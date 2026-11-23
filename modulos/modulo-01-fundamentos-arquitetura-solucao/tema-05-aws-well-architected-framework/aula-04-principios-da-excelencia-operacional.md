# Aula 04 — Princípios da Excelência Operacional

**Módulo** · 01 — Fundamentos de Arquitetura de Solução  
**Tema** · 05 — AWS Well-Architected Framework  
**Origem** · Transcrição fornecida. As notas técnicas, o exemplo aplicado, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Entender como operações como código, mudanças pequenas, revisão de procedimentos e preparação para falhas ajudam a manter e evoluir um workload. A aula retoma a observabilidade da Aula 03 e orienta o estudo de práticas que arquitetos e desenvolvedores precisam reconhecer no dia a dia.

## Execute operações como código

A aula apresenta infraestrutura como código (*Infrastructure as Code*, ou IaC) como uma forma de provisionar ambientes de maneira automatizada. Em um fluxo manual de *ClickOps*, alguém entra no painel do provedor, escolhe a configuração de um cluster Kubernetes e cria os recursos clicando. Com IaC, a configuração passa a ser descrita em arquivos que uma ferramenta pode aplicar de forma repetível. A mesma abordagem ajuda a preparar os recursos necessários para executar aplicações.

O AWS CloudFormation é o exemplo da aula para ambientes AWS. O Terraform, da HashiCorp, aparece como alternativa que trabalha com diferentes provedores de nuvem e com Kubernetes. Entender o fluxo ajuda o desenvolvedor a colaborar com a operação e a reconhecer quais dependências precisam ser preparadas para implantar ou recuperar a aplicação.

Se uma zona de disponibilidade ficar indisponível, a equipe pode reaplicar definições de infraestrutura em outra zona prevista no plano de recuperação. O ganho é ter uma descrição reaproveitável do ambiente e reduzir a dependência de decisões manuais durante o incidente.

> **Nota técnica autoral.** IaC configura recursos. A recuperação de dados, segredos, tráfego e dependências precisa estar contemplada e testada no plano de recuperação. O framework atual da AWS trata operações como código no princípio de automatizar com segurança e abrange também configurações e procedimentos operacionais.

## Faça mudanças frequentes, pequenas e reversíveis

Divida mudanças grandes em etapas que possam ser implantadas e verificadas individualmente. Criar um bucket, mudar configurações e lançar várias funcionalidades em uma única entrega dificulta descobrir qual alteração causou a falha. Também torna mais difícil desfazer só a parte que apresentou problema.

Mudanças de escopo reduzido facilitam associar um desvio a uma alteração específica e retornar a um estado conhecido. Para cada etapa, a equipe precisa saber o que observar após a implantação e como reagir se o comportamento sair do esperado.

> **Nota técnica autoral.** Reverter uma versão da aplicação pode exigir compatibilidade com dados já gravados, alterações de esquema e configurações em uso. Verifique essas dependências ao planejar a sequência de mudanças.

## Refine os procedimentos de operação com frequência

Procedimentos operacionais fazem parte do trabalho diário e devem evoluir conforme a equipe os executa. Se uma tarefa manual se repete, observe onde ela consome tempo ou favorece erros. Simplifique as etapas, esclareça instruções ambíguas e automatize o que puder ser repetido com segurança.

Quando uma execução falha, examine as condições e o processo que orientou a pessoa que realizou a tarefa. Uma instrução incompleta, uma verificação ausente ou uma etapa difícil de reproduzir podem afetar qualquer operador. Atualize o procedimento com o que a equipe aprendeu e confira seu funcionamento na próxima execução.

## Antecipe falhas

A aula propõe perguntas diretas sobre situações plausíveis. O que a equipe faz se a zona de disponibilidade onde a aplicação roda ficar indisponível? Como recupera a operação se um cluster Kubernetes for comprometido? As respostas precisam ser preparadas e praticadas com frequência, para que a equipe chegue ao incidente sabendo quem decide, o que executar e como validar a recuperação.

A prática também revela dependências que podem faltar no plano. O objetivo é entrar em um incidente com passos já exercitados e condições claras para recuperar o serviço dentro dos limites do negócio.

## Aprenda com as falhas

Depois de uma falha ou indisponibilidade, investigue o que ocorreu, quais condições contribuíram e o que precisa mudar para reduzir o risco de repetição. Registre o aprendizado em um relatório que explique a causa quando conhecida, as ações tomadas e as melhorias que a equipe vai implementar.

Converta as descobertas em instruções operacionais que possam ser usadas no próximo incidente. O relatório preserva o contexto da falha. O procedimento define o que fazer quando determinada condição for observada. Documentos curtos e acionáveis ajudam a consolidar o aprendizado no processo cotidiano.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral que retoma o workload das aulas anteriores.*

A equipe precisa mudar a configuração de implantação do serviço de reservas e testar sua recuperação em outra zona de disponibilidade.

1. **Versionar o ambiente.** Registre as definições de infraestrutura e valide em um ambiente de teste se a configuração pode ser reaplicada.
2. **Separar as mudanças.** Publique primeiro os ajustes de infraestrutura e verifique a saúde do serviço. Entregue a nova versão da aplicação em uma etapa seguinte, com critérios de reversão definidos.
3. **Exercitar a recuperação.** Simule a indisponibilidade da zona em um ambiente controlado. Verifique se o tráfego chega à implantação disponível, se o serviço acessa os dados necessários e se uma reserva pode ser confirmada e consultada.
4. **Melhorar o procedimento.** Se a simulação revelar que o redirecionamento depende de uma etapa manual pouco clara, documente o achado, atribua a correção e repita o exercício para verificar o resultado.

## Checklist operacional

*Complemento autoral para revisar os princípios da aula.*

- [ ] As definições do ambiente estão versionadas e o provisionamento foi verificado?
- [ ] Cada mudança tem escopo, critério de sucesso e plano de reversão ou recuperação?
- [ ] Os procedimentos usados no dia a dia são revisados quando a equipe encontra erros ou etapas repetitivas?
- [ ] O plano de recuperação foi exercitado e inclui a validação do fluxo de negócio?
- [ ] Cada incidente gera ações de melhoria que a equipe consegue acompanhar e verificar?

## Perguntas de revisão

*Complemento autoral para estudo.*

1. Que diferenças práticas existem entre provisionar um cluster pelo painel e aplicar uma definição de infraestrutura como código?
2. Quais dependências precisam entrar no plano para recuperar o serviço em outra zona?
3. Como dividir uma entrega que inclui criação de infraestrutura, configuração e lançamento de uma funcionalidade?
4. Como avaliar se uma falha recorrente tem relação com o procedimento operacional?
5. O que deve aparecer no relatório de incidente e o que deve virar instrução de operação?

## Links relacionados

- [Aula 03 — Excelência Operacional](./aula-03-excelencia-operacional.md)
- [Aula 02 — AWS Well-Architected](./aula-02-aws-well-architected.md)
- [Índice do Tema 05](./README.md)
- [Princípios de design da excelência operacional — AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/ops-design-principles.html)
