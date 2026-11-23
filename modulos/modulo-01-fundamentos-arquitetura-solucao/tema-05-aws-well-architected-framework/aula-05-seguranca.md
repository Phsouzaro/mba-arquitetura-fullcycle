# Aula 05 — Segurança

**Módulo** · 01 — Fundamentos de Arquitetura de Solução  
**Tema** · 05 — AWS Well-Architected Framework  
**Origem** · Anotações fornecidas. O exemplo aplicado, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Entender como decisões sobre identidade, rede, dados e resposta a incidentes limitam o impacto de falhas e de acessos indevidos em um workload.

## Identidade forte e menor privilégio

Autenticação verifica quem está fazendo a solicitação. Autorização determina quais ações essa identidade pode executar, sobre quais recursos e em quais condições. Em cloud, cada pessoa ou sistema deve receber permissões compatíveis com sua responsabilidade. O menor privilégio é uma decisão arquitetural porque o escopo de uma identidade também delimita o que pode ser afetado se sua credencial for comprometida.

### Roles, grupos e usuário root

Roles e grupos ajudam a organizar acessos por função em organizações com muitas pessoas, equipes e sistemas. Grupos organizam permissões de usuários conforme suas responsabilidades. Roles representam identidades que pessoas ou serviços autorizados podem assumir conforme a tarefa. Essa organização facilita revisar acessos e reduz concessões individuais amplas.

Reserve o usuário root da conta AWS para tarefas que exigem esse acesso. Na rotina, administradores usam identidades próprias e recorrem a permissões elevadas em situações controladas. A autenticação multifator reforça a verificação da identidade em acessos humanos privilegiados.

### Acessos internos também exigem controle

Uma pessoa, aplicação ou integração interna pode ter permissões excessivas ou usar um acesso fora do contexto previsto. A rede interna, por si só, não estabelece a identidade de quem faz uma chamada nem a legitimidade da operação. Aplique autenticação, autorização e restrições de acesso também dentro da organização e entre componentes do workload.

## Rastreabilidade e auditoria

A telemetria discutida na Aula 03 também serve à segurança. Uma exclusão de bucket, uma tentativa de acesso negada, uma alteração de configuração ou a queda de um servidor deve deixar evidências proporcionais ao evento. A equipe precisa correlacionar horário, origem, recurso afetado e resultado. Quando houver uma ação atribuível a uma identidade, registre quem a executou.

A investigação pode combinar registros de auditoria com logs da aplicação e sinais de infraestrutura. Essa correlação ajuda a distinguir erro operacional, acesso indevido e falhas sem causa de segurança identificada.

## Defesa em camadas e exposição mínima

Defesa em camadas distribui controles por identidade, autenticação, rede, pontos de entrada e componentes sensíveis. Por exemplo, a autenticação da aplicação controla quem usa suas funções. O isolamento do banco limita quem consegue estabelecer uma conexão com ele. Uma falha no primeiro controle ainda deixa outras barreiras no caminho.

Uma arquitetura pode receber tráfego externo por um balanceador público com regras restritivas e manter aplicação e banco em subnets privadas. O balanceador encaminha somente o tráfego previsto para a aplicação, e o banco aceita conexões pelos caminhos internos autorizados. A revisão deve examinar tanto as rotas quanto as regras de acesso, pois a decisão de colocar um recurso em uma subnet privada descreve apenas parte do seu isolamento.

## Proteção de dados em trânsito

Dados em trânsito circulam entre clientes, aplicações, serviços e bancos. TLS protege a confidencialidade e a integridade da comunicação e, na configuração usual de HTTPS, permite ao cliente verificar a identidade do servidor. Essa proteção se aplica às conexões externas e aos fluxos internos que transportam dados ou credenciais.

### mTLS entre workloads

No TLS mútuo, ou mTLS, cliente e servidor apresentam certificados e validam a identidade um do outro. Em chamadas entre serviços, isso reduz o risco de aceitar um componente que se apresenta como outro. A autorização continua definindo quais operações o serviço autenticado pode realizar.

Uma service mesh pode ajudar a aplicar mTLS entre workloads e operacionalizar a emissão, distribuição e renovação de certificados. A equipe ainda precisa definir quais identidades e fluxos são permitidos e verificar se as políticas correspondem à arquitetura.

## Proteção de dados em repouso

Bancos, buckets e outros repositórios persistentes guardam dados mesmo quando nenhuma operação está em andamento. A criptografia em repouso protege o conteúdo armazenado diante de determinados acessos indevidos ao meio ou ao volume. Políticas de acesso, controle de chaves e isolamento restringem quem pode alcançar e consultar os dados. Esses controles também precisam alcançar cópias e backups conforme sua sensibilidade.

### Restrição de acesso a dados de produção

Reproduzir um erro em teste pode parecer motivo para copiar um banco de produção. O caso apresentado na aula, de um banco de clientes enviado por engano, mostra como a própria circulação de uma cópia amplia o impacto possível de um erro humano. O acesso ao dado real deve ser excepcional, justificado e restrito às pessoas e ao contexto autorizados. Dados sintéticos ou versões devidamente desidentificadas podem atender a testes que exigem apenas reproduzir o comportamento da aplicação.

## Preparação e resposta a incidentes

Antes de um incidente, defina como detectar desvios, conter o impacto, investigar e recuperar o workload. A equipe precisa saber quem pode isolar um ambiente, revogar acessos ou coordenar a recriação de componentes em condições controladas. A investigação usa os registros disponíveis para identificar alcance e causas e orientar a recuperação.

Após a contenção e a restauração do serviço, registre o que ocorreu e transforme os achados em mudanças verificáveis nas políticas, nos controles e nos procedimentos operacionais. Essa etapa retoma o aprendizado com falhas discutido na Aula 04.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral.*

A API recebe conexões HTTPS por um balanceador. A aplicação e o banco operam em subnets privadas. A API pode consultar e gravar reservas, enquanto o processador de notificações recebe apenas as permissões necessárias para consumir os eventos e enviar mensagens. Se a API chama outro serviço interno, mTLS pode verificar a identidade dos dois lados e uma política de autorização pode limitar as operações permitidas.

Se a auditoria indicar uma exportação de reservas fora do procedimento esperado, a equipe correlaciona a identidade, o horário, o recurso e a operação para entender o alcance. O procedimento de resposta indica quem pode restringir a sessão, preservar os registros e confirmar se o fluxo de reservas continua operando em segurança. A revisão posterior verifica se a permissão de exportar estava limitada às funções que realmente precisavam dela.

## Checklist arquitetural

*Complemento autoral.*

- [ ] Cada identidade tem permissões vinculadas à sua função, com acesso privilegiado controlado?
- [ ] As operações relevantes deixam evidências que permitem reconstruir o que ocorreu?
- [ ] Pontos de entrada públicos são explícitos e componentes internos têm caminhos de acesso restritos?
- [ ] Os fluxos sensíveis usam TLS, com autenticação mútua quando exigida entre workloads?
- [ ] Dados persistentes e cópias têm criptografia e controles de acesso compatíveis com sua sensibilidade?
- [ ] A equipe praticou como conter, investigar e recuperar o workload?

## Perguntas de revisão

*Complemento autoral.*

1. Como autenticação, autorização e menor privilégio limitam riscos diferentes?
2. Por que o usuário root deve ficar fora da rotina e como roles ajudam a organizar acessos?
3. Quais evidências ajudam a investigar uma exclusão de bucket ou uma alteração de configuração?
4. Como um balanceador público e subnets privadas contribuem para a defesa em camadas?
5. O que mTLS acrescenta à comunicação entre serviços e quais decisões ficam a cargo da autorização?
6. Como restringir dados de produção sem inviabilizar a investigação de falhas?
7. Que medidas precisam ser planejadas antes e acompanhadas depois de um incidente?

## Links relacionados

- [Aula 02 — AWS Well-Architected](./aula-02-aws-well-architected.md)
- [Aula 03 — Excelência Operacional](./aula-03-excelencia-operacional.md)
- [Aula 04 — Princípios da Excelência Operacional](./aula-04-principios-da-excelencia-operacional.md)
- [Índice do Tema 05](./README.md)
- [Princípios de design do pilar de Segurança — AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/sec-design.html)
