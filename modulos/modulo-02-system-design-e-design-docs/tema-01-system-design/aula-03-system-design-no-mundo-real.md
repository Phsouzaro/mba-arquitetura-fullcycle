# Aula 03 — System Design no mundo real

**Módulo** · 02 — System Design e Design Docs  
**Tema** · 01 — System Design  
**Origem** · Anotações fornecidas. O exemplo aplicado, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Usar o processo de System Design para estruturar, documentar e defender uma proposta de arquitetura diante de clientes, equipes técnicas e áreas comerciais.

## System Design como ferramenta de trabalho

As etapas discutidas nas aulas anteriores ajudam a organizar uma proposta antes de levá-la a uma reunião. A equipe explicita o problema, os requisitos que orientam o desenho, as premissas e as alternativas consideradas. Com esse material, as pessoas envolvidas conseguem avaliar a mesma proposta a partir de responsabilidades diferentes.

O cliente pode querer entender o benefício esperado e os limites da entrega. O time técnico precisa examinar interfaces, dependências e consequências para a operação. A área comercial precisa entender o que está incluído na proposta e quais condições afetam custo, prazo e compromissos. Uma apresentação pode mudar de nível de detalhe conforme o público e preservar a mesma justificativa para a decisão.

## Como tornar a complexidade compreensível

Sistemas reais acumulam dependências, restrições e impactos cruzados. Uma apresentação estruturada começa pelo problema e pelas restrições que mudam a decisão. Em seguida, descreve o fluxo principal, as dependências relevantes e as alternativas. Essa ordem permite que cada pessoa identifique a parte que precisa avaliar e entenda como ela afeta o restante do sistema.

## Formalização antes da implementação

Escrever e especificar uma solução obriga a verificar se as decisões fazem sentido em conjunto. Ao formalizar uma integração, por exemplo, surgem perguntas sobre quem fornece os dados, quando precisam estar disponíveis e como o fluxo se comporta diante de uma falha. Essas perguntas permitem refinar a proposta antes de assumir compromissos de implementação.

A aula compara esse exercício ao TDD. Escrever primeiro um teste leva a explicitar o comportamento esperado antes do código. Formalizar a arquitetura produz um efeito semelhante ao expor lacunas, permitir crítica e amadurecer decisões antes da implementação. A segurança ao defender a proposta vem do raciocínio que pode ser examinado.

## Artefatos que sustentam a proposta

System Design produz artefatos complementares. Um diagrama ajuda a visualizar componentes, relações e fluxos. A especificação registra comportamentos esperados, interfaces e limites. As estimativas deixam visíveis os números e as premissas usadas na análise. A documentação das decisões registra alternativas, justificativas e consequências.

Juntos, esses registros permitem revisar a proposta sem depender da presença de quem a elaborou. Também dão credibilidade à conversa com o cliente. Se uma estimativa embasa o prazo ou o custo, o leitor consegue verificar de onde ela veio e em que circunstâncias precisa ser revista.

## Uso comercial e justificativa dos trade-offs

Uma proposta comercialmente defensável liga benefícios e limites a decisões que a equipe consegue explicar. Se o desenho inclui Apache Kafka, a conversa precisa mostrar qual requisito motivou a escolha, quais alternativas foram consideradas e que custo operacional a solução introduz. O cliente consegue avaliar o benefício esperado, a equipe técnica consegue examinar as consequências e a área comercial consegue apresentar o escopo com clareza.

Uma justificativa útil registra o contexto em que a alternativa faz sentido. Se as premissas mudarem, o registro permite saber se a escolha continua adequada.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral.*

A equipe precisa confirmar reservas e enviar notificações em segundo plano. O cliente aceita que as notificações cheguem depois da confirmação. O escopo inicial prevê um único consumidor dos eventos.

| Alternativa | Benefício para o cenário | Custo ou consequência |
| --- | --- | --- |
| Fila para o processador de notificações | Permite tratar notificações de forma assíncrona e reprocessar entregas com falha conforme a política da fila. | A equipe precisa tratar duplicidades e acompanhar o acúmulo de mensagens. |
| Log de eventos com Apache Kafka | Permite que consumidores independentes leiam eventos e que o histórico retido seja reprocessado. | Exige decisões sobre retenção, partições e operação dos consumidores, além do custo da plataforma. |

Com um único consumidor e sem requisito de reprocessar um histórico compartilhado, a fila é uma proposta inicial defensável. O desenho pode mostrar a confirmação e o envio assíncrono. A especificação registra o atraso aceitável para a notificação. O registro de decisão explica por que o escopo atual favorece a fila e em que condições a equipe revisitaria a escolha, como a entrada de consumidores independentes com necessidade de releitura do histórico.

Na apresentação, o cliente pode avaliar o atraso aceitável, a equipe técnica pode revisar a entrega dos eventos e a área comercial pode explicar o escopo coberto pela proposta.

## Checklist da proposta

*Complemento autoral.*

- [ ] O problema, o escopo e as restrições relevantes estão explícitos?
- [ ] O diagrama, a especificação e as estimativas descrevem a mesma proposta?
- [ ] Os números essenciais têm premissas registradas?
- [ ] As alternativas foram comparadas por benefícios, custos e consequências?
- [ ] Cada público consegue avaliar os compromissos que afetam sua decisão?

## Perguntas de revisão

*Complemento autoral.*

1. Por que uma estrutura explícita ajuda a apresentar um sistema com muitas dependências?
2. Como a analogia com TDD explica o valor de formalizar a solução antes da implementação?
3. Que informações precisam acompanhar o diagrama para sustentar a proposta?
4. Como apresentar a mesma arquitetura para o cliente, a equipe técnica e a área comercial?
5. Que mudança no cenário de reservas justificaria reavaliar a escolha da fila?

## Links relacionados

- [Aula 01 — Entendendo os principais conceitos](./aula-01-entendendo-os-principais-conceitos.md)
- [Aula 02 — System Design nas big techs](./aula-02-system-design-nas-big-techs.md)
- [Índice do Tema 01 — System Design](./README.md)
- [Índice do Módulo 02](../README.md)
