# Aula 02 — AWS Well-Architected

**Módulo** · 01 — Fundamentos de Arquitetura de Solução  
**Tema** · 05 — AWS Well-Architected Framework  
**Origem** · Anotações da aula. O checklist, o estudo de caso e as perguntas de revisão são complementos autorais.

## Objetivo

Usar os seis pilares do AWS Well-Architected Framework para revisar um workload, identificar lacunas e fundamentar decisões sobre sua evolução.

## Framework como checklist arquitetural

O AWS Well-Architected é uma referência de arquitetura e operação. Ele organiza boas práticas em perguntas e princípios que ajudam a examinar como um workload foi desenhado e como se comporta em produção. A revisão retoma o workload da Aula 01, considerando aplicação, dados, integrações, operação e requisitos de negócio no mesmo escopo.

O formato de checklist torna critérios de qualidade observáveis. Uma resposta sobre recuperação, por exemplo, ganha substância quando a equipe consegue explicar o cenário de falha, o comportamento esperado e o que já foi verificado. Revisar o workload por pilar ajuda a revelar pontos cegos que um teste funcional, por si só, deixaria passar. A mesma decisão pode beneficiar um pilar e impor um custo ou uma restrição em outro.

## Aplicabilidade além da AWS

A AWS documenta práticas para workloads na sua nuvem. O raciocínio da aula é transferível para OCI, Azure, Google Cloud e ambientes on-premises. Perguntas sobre recuperação, controle de acesso ou uso de capacidade continuam pertinentes. As evidências e os mecanismos para atendê-las dependem dos serviços disponíveis e das responsabilidades operacionais em cada ambiente.

## Os seis pilares

### Excelência operacional

Avalia se a equipe consegue acompanhar, manter e evoluir o workload com controle. O desenho precisa dar condições para perceber degradações, diagnosticar problemas e ajustar a solução ao longo do tempo. Uma arquitetura difícil de operar aumenta retrabalho, prolonga incidentes e reduz a previsibilidade das mudanças.

### Segurança

Torna proteção, acesso e controle critérios explícitos da revisão. Isso envolve verificar quem pode executar cada operação, como dados e componentes são protegidos e quais controles sustentam essas decisões. A revisão ajuda a detectar lacunas enquanto ainda há espaço para ajustar a arquitetura.

### Confiabilidade

Examina como o workload continua entregando o comportamento esperado diante de falhas, mudanças de carga ou eventos inesperados. A análise trata de resistência a falhas, recuperação e continuidade dentro dos limites aceitáveis para o negócio. Esses limites dão sentido a decisões sobre o que precisa continuar disponível e o que pode ser recuperado depois.

### Eficiência de performance

Avalia a adequação entre demanda, capacidade e recursos escolhidos. Uma solução precisa responder dentro dos objetivos do workload nos perfis de carga relevantes. A revisão também considera como as escolhas técnicas se comportam quando o volume ou o padrão de uso muda e onde há capacidade desperdiçada.

### Otimização de custos

Examina se o workload entrega valor com uso eficiente dos recursos financeiros. Na nuvem, dimensionamento, retenção, transferência e processamento podem gerar cobrança recorrente. Avaliar essas escolhas junto aos requisitos ajuda a encontrar superdimensionamento, desperdício e oportunidades de melhorar o custo da operação.

### Sustentabilidade

Considera os impactos do consumo de recursos ao longo do ciclo de vida do workload. A revisão procura oportunidades de reduzir capacidade ociosa, processamento e armazenamento desnecessários, respeitando as necessidades do serviço. Essa perspectiva amplia a análise de eficiência para incluir o impacto do uso de recursos.

## Uso prático do framework

A revisão percorre perguntas e princípios de cada pilar para identificar onde o workload está bem sustentado e onde há riscos ou respostas incompletas. Seu resultado depende da aplicação ao contexto concreto da solução. A documentação completa da AWS detalha as práticas e permite aprofundar a análise para além dos tópicos introdutórios da aula.

## Checklist arquitetural

*Complemento autoral para aplicar os conceitos da aula.*

Antes da revisão, registre o fluxo avaliado, suas dependências e as expectativas de negócio. Para cada item, anote a evidência disponível, a lacuna encontrada e o próximo passo. Quando a evidência estiver pendente, registre como obtê-la.

- [ ] **Excelência operacional.** A equipe detecta degradações e sabe como agir durante incidentes e mudanças? Verifique alertas, responsáveis e procedimentos operacionais.
- [ ] **Segurança.** As permissões e a proteção dos dados acompanham os riscos do fluxo? Revise os acessos, a proteção de segredos e os registros de operações sensíveis.
- [ ] **Confiabilidade.** O workload mantém ou recupera as funções críticas dentro dos limites acordados? Confira testes de indisponibilidade e restauração.
- [ ] **Eficiência de performance.** A capacidade atende aos perfis de carga esperados? Compare resultados de testes de carga, latência e utilização de recursos.
- [ ] **Otimização de custos.** Os gastos acompanham o valor entregue e a demanda? Relacione custos recorrentes ao volume processado e identifique recursos superdimensionados.
- [ ] **Sustentabilidade.** Há consumo evitável ao longo da operação? Verifique períodos de ociosidade, retenção de dados e processamento repetido.

Consolide os achados em ações com responsável, prioridade e critério de validação. Registre os trade-offs que justificam a ordem escolhida e revise os resultados após mudanças relevantes.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral que retoma o exemplo conceitual da Aula 01.*

Considere uma API de reservas com banco relacional, fila de eventos e processador assíncrono de notificações. Neste cenário hipotético, confirmar a reserva é a operação crítica. A notificação pode atrasar, desde que a reserva confirmada permaneça consultável e os eventos pendentes sejam processados quando o serviço de notificação voltar.

| Pilar | Pergunta aplicada | Evidência a buscar |
| --- | --- | --- |
| Excelência operacional | A equipe distingue falhas na confirmação de atrasos nas notificações? | Alertas separados para erros da API e idade das mensagens, com procedimentos para cada incidente. |
| Segurança | Um cliente consegue consultar ou cancelar somente as reservas autorizadas? | Testes de acesso entre contas e revisão das permissões da API e do processador. |
| Confiabilidade | Uma falha do processador afeta reservas já confirmadas? | Teste de indisponibilidade, retomada da fila e reprocessamento sem duplicar a notificação. Teste também a restauração do banco. |
| Eficiência de performance | A API sustenta o pico sem saturar o banco? | Teste de carga com latência p95, taxa de erro e uso de conexões, medidos junto ao tempo de processamento da fila. |
| Otimização de custos | Qual é o custo por reserva confirmada e como ele varia com o volume? | Gastos atribuídos ao fluxo divididos pelo número de confirmações no mesmo período, com análise dos componentes de maior custo. |
| Sustentabilidade | Os processadores ficam ociosos por longos períodos ou refazem trabalho? | Medidas de utilização e de reprocessamento ao longo do dia, como indicadores de consumo evitável. |

Se o teste mostrar que o atraso na fila permanece dentro do limite acordado, a equipe pode reduzir a capacidade ociosa do processamento assíncrono. Essa escolha pode favorecer custos e sustentabilidade, mas também pode aumentar o tempo de recuperação após um pico. A decisão deve registrar o atraso tolerado e validar, em teste, quanto tempo a fila leva para voltar ao normal. Se o teste revelar risco de perda de reservas confirmadas, a recuperação dos dados ganha prioridade por afetar diretamente o fluxo crítico.

## Perguntas de revisão

*Complemento autoral para estudo.*

1. Como o formato de checklist transforma uma preocupação arquitetural em um critério verificável?
2. Que partes do raciocínio Well-Architected são transferíveis para outro provedor ou para um ambiente on-premises? O que precisa ser adaptado?
3. Que evidências diferenciariam uma solução funcional de um workload com excelência operacional?
4. Como verificar se as decisões de acesso e proteção de dados atendem ao pilar de segurança?
5. No serviço de reservas, que testes distinguem a confiabilidade da confirmação da confiabilidade das notificações?
6. Que medidas usaria para avaliar a eficiência de performance sob carga variável?
7. Como a redução da capacidade ociosa pode afetar custos, sustentabilidade e tempo de recuperação?
8. Como transformar uma lacuna identificada na revisão em uma ação verificável?

## Links relacionados

- [Aula 01 — Arquitetura de Solução para Cloud](./aula-01-arquitetura-de-solucao-para-cloud.md)
- [Índice do Tema 05](./README.md)
- [Documentação oficial do AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS Well-Architected Tool](https://aws.amazon.com/well-architected-tool/)
