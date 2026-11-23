# Aula 03 — Excelência Operacional

**Módulo** · 01 — Fundamentos de Arquitetura de Solução  
**Tema** · 05 — AWS Well-Architected Framework  
**Origem** · Anotações da aula. O exemplo aplicado, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Entender como a equipe usa sinais de produção para acompanhar o workload, diagnosticar desvios e verificar se mudanças melhoram a operação.

## Operação como atividade contínua

O deploy coloca uma versão em execução. A partir daí, a equipe precisa sustentar a entrega de valor enquanto desenvolve funcionalidades, corrige incidentes e responde a mudanças de carga e de dependências. A excelência operacional aparece na capacidade de perceber desvios, avaliar seus efeitos e agir antes que o problema se amplie e afete o negócio.

A metáfora dos pratos girando ilustra o desafio apresentado na aula. Vários componentes operam simultaneamente, e cada sinal de instabilidade pede atenção. A melhoria contínua transforma esses sinais em ajustes da aplicação e dos procedimentos operacionais. A equipe observa o comportamento, corrige o que causa atrito e mede de novo para verificar se a mudança trouxe o efeito desejado. Esse ciclo preserva a qualidade do workload à medida que ele evolui.

## Observabilidade

Observabilidade é a capacidade de inferir o estado interno de um sistema a partir dos sinais que ele emite. Em um workload distribuído, uma falha percebida na API pode começar em outro serviço, no banco ou em uma integração. A equipe usa a telemetria para descobrir onde o comportamento mudou, quando isso ocorreu e em quais condições.

### Métricas

Métricas são medições numéricas acompanhadas ao longo do tempo. Latência, taxa de erro, volume processado por unidade de tempo e consumo de recursos ajudam a identificar tendências, saturação e regressões. Painéis e alertas permitem acompanhar a saúde do workload, e séries históricas ajudam a comparar o comportamento antes e depois de uma mudança em condições de carga semelhantes.

### Logs

Logs registram eventos discretos gerados pela aplicação ou pela infraestrutura. Eles preservam detalhes de execução, como quando ocorreu uma falha, qual componente a registrou e em que contexto. Esses detalhes ajudam a reconstruir eventos, investigar falhas específicas e apoiar a auditoria operacional. Métricas mostram a extensão de um problema, enquanto logs ajudam a examinar ocorrências concretas.

### Application Performance Monitoring (APM)

APM acompanha o desempenho da aplicação durante a execução. Ele associa transações a chamadas de dependências e tempos de processamento para localizar gargalos e falhas percebidas no uso real. Uma API pode continuar respondendo enquanto uma operação demora cada vez mais. O APM ajuda a descobrir em qual etapa o tempo foi gasto e a direcionar a investigação.

### Rastreabilidade

Rastreabilidade permite acompanhar uma requisição ou um fluxo através de serviços e integrações. Em uma operação distribuída, ela ajuda a identificar onde surgiu a falha, em qual etapa a latência aumentou e por quais dependências o efeito se propagou. Um trace distribuído é uma forma de reconstruir esse caminho e examinar a duração de cada etapa instrumentada.

### Monitores de uptime

Monitores de uptime verificam periodicamente, do ponto de vista externo, se o serviço está acessível e responde como esperado. Um alerta sinaliza que a verificação falhou ou degradou e dá início à investigação. O alcance do sinal depende do caminho exercitado pelo monitor. As métricas, os logs e os traces ajudam a investigar a causa e a delimitar os fluxos afetados.

## Operação orientada por dados

Uma decisão operacional começa com uma pergunta sobre o workload. A equipe precisa saber, por exemplo, se houve degradação, quem foi afetado e como o serviço se comportou após uma correção. Para responder, combina os sinais disponíveis, formula uma hipótese, toma uma ação e mede seu efeito. Custos, segurança e capacidade de infraestrutura também influenciam a operação. Os dados de produção mostram como essas decisões se refletem na entrega do serviço ao longo do tempo.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral que retoma o workload das aulas anteriores.*

Após um deploy, o monitor externo continua indicando que a API está acessível. Ao mesmo tempo, o painel mostra aumento da latência p95 na confirmação de reservas. O monitor comprova que a verificação configurada responde. A métrica mostra degradação em um fluxo específico.

1. **Dimensionar o impacto.** Compare a latência, a taxa de erro e o volume de confirmações antes e depois do deploy. Verifique se a degradação coincide com mudança de versão ou com um pico de carga.
2. **Localizar o atraso.** Abra no APM alguns traces de reservas lentas e examine as etapas da transação. Neste cenário, a maior parte do tempo aparece na obtenção de uma conexão com o banco.
3. **Verificar a hipótese.** Cruze os traces com as métricas de uso do pool de conexões e com os logs de espera ou timeout. Confira se a nova versão alterou o tempo durante o qual cada confirmação mantém uma conexão ocupada.
4. **Corrigir e medir.** Se houver impacto e o rollback for seguro, reverta a versão para mitigar o incidente. Compare novamente latência, erros e espera por conexões sob carga semelhante. Use os resultados para corrigir a mudança e ajustar os alertas do fluxo de confirmação.

## Checklist operacional

*Complemento autoral para revisar um fluxo crítico.*

- [ ] Identificar o comportamento esperado do fluxo e os desvios que afetam o negócio.
- [ ] Acompanhar latência, taxa de erro, volume e sinais de saturação.
- [ ] Registrar nos logs o contexto necessário para investigar uma ocorrência.
- [ ] Usar APM e rastreabilidade para localizar atrasos e falhas entre componentes.
- [ ] Verificar externamente a disponibilidade e entender quais caminhos o monitor cobre.
- [ ] Registrar o efeito das intervenções e atualizar os procedimentos com base no que foi observado.

## Perguntas de revisão

*Complemento autoral para estudo.*

1. Por que a excelência operacional precisa ser avaliada após o deploy e ao longo de toda a operação?
2. Que sinais permitem distinguir uma regressão de performance de uma indisponibilidade?
3. Como métricas e logs se complementam na investigação de um incidente?
4. O que APM e rastreabilidade permitem verificar quando uma transação atravessa vários serviços?
5. Como o monitor de uptime pode indicar disponibilidade enquanto confirmações de reservas estão lentas?
6. Que evidências mostrariam que uma correção melhorou a operação em condições comparáveis?

## Links relacionados

- [Aula 01 — Arquitetura de Solução para Cloud](./aula-01-arquitetura-de-solucao-para-cloud.md)
- [Aula 02 — AWS Well-Architected](./aula-02-aws-well-architected.md)
- [Índice do Tema 05](./README.md)
- [Pilar de Excelência Operacional — AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/operational-excellence.html)
