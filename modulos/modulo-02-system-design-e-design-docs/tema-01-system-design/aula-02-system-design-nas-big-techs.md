# Aula 02 — System Design nas big techs

**Módulo** · 02 — System Design e Design Docs  
**Tema** · 01 — System Design  
**Origem** · Anotações fornecidas. O exemplo, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Entender como um problema aberto de System Design permite avaliar raciocínio técnico, comunicação e capacidade de revisar decisões sob incerteza.

## System Design como instrumento de avaliação

Em entrevistas de System Design, um problema aberto permite observar o processo discutido na Aula 01. O entrevistador acompanha como a pessoa esclarece o problema, explicita hipóteses e chega a uma proposta que consegue defender. A arquitetura final faz parte da avaliação. Sua justificativa mostra se a pessoa entendeu as restrições e consegue ajustar a proposta quando recebe novas informações.

### Justificativa e profundidade técnica

Uma estimativa é útil quando a pessoa consegue explicar sua origem, suas premissas e o efeito que ela tem sobre a decisão. O mesmo vale para cada componente citado. Ao propor um cache, por exemplo, abre-se espaço para discutir que dados seriam armazenados, quando poderiam ficar desatualizados e como o sistema responderia se o cache estivesse indisponível. Assim, a conversa revela tanto a capacidade de estruturar o problema quanto a profundidade técnica para sustentar as escolhas.

## Técnica de raciocínio sob pressão

Uma sequência de trabalho reduz a dispersão. Comece esclarecendo o problema, organize os requisitos e restrições, estime o que pode mudar o desenho e compare alternativas antes de aprofundar componentes. Se surgir uma informação nova, retome a premissa afetada e ajuste a proposta. Um método dá à conversa um ponto de retorno quando há interrupções ou questionamentos.

### Perguntas que alteram o desenho

Perguntar faz parte da solução. Use as perguntas para esclarecer quais fluxos são essenciais, quais restrições são obrigatórias e o que fica fora do escopo. Em um sistema de reservas, perguntar se a tela de disponibilidade pode exibir dados alguns segundos atrasados ajuda a decidir se o cache cabe no fluxo de consulta. A resposta pode ser diferente para a confirmação da reserva, que altera o estado do sistema.

### Aproximação e dedução

Com dados incompletos, simplifique o problema o suficiente para avançar. Declare as premissas, mostre o cálculo e explicite a incerteza que pode modificar a decisão. Uma ordem de grandeza pode indicar se vale discutir capacidade de pico, mesmo quando o volume exato ainda é desconhecido. Refine a estimativa quando uma faixa plausível incluir cenários que exigem escolhas diferentes.

## Comunicação e reação a questionamentos

Torne o raciocínio verificável. Diga o que foi confirmado, o que é hipótese e o que falta investigar. Se uma questão fugir do seu conhecimento, explicite a dúvida e explique que evidência buscaria para avaliá-la.

Sob pressão, uma pergunta difícil pode indicar que falta esclarecer um requisito ou que a solução precisa mudar. Retome a cadeia de raciocínio, identifique a premissa contestada e explique o que muda caso ela seja falsa. A postura técnica aparece na capacidade de ouvir, revisar e continuar a análise com clareza.

## Valor além da entrevista

O mesmo processo ajuda equipes a discutir arquitetura no trabalho. Perguntas reduzem divergências de interpretação, estimativas tornam a conversa concreta e justificativas permitem revisar decisões quando o contexto muda. Explicitar as condições de uma escolha facilita tanto a colaboração durante o desenho quanto a revisão posterior.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral.*

Em um exercício, a pessoa recebe o enunciado “Desenhe um sistema que permita consultar disponibilidade e confirmar reservas”.

1. **Esclareça o escopo.** Pergunte se uma consulta pode mostrar disponibilidade desatualizada e se duas pessoas podem tentar reservar o mesmo item ao mesmo tempo.
2. **Faça uma aproximação.** Se houver 600 mil consultas por dia, são cerca de 7 consultas por segundo em média. Assumindo um pico de 10 vezes a média, use cerca de 70 por segundo como hipótese inicial. Confirme se há eventos com tráfego mais concentrado, pois eles podem invalidar essa hipótese.
3. **Justifique a proposta.** Comece avaliando se o banco consegue atender às consultas e às confirmações sob a carga estimada. Considere cache para consultas se os testes apontarem necessidade e houver tolerância a dados desatualizados. Na confirmação, valide e atualize a disponibilidade na mesma operação atômica da fonte transacional para evitar duas confirmações do mesmo item.
4. **Revise diante de um questionamento.** Se o entrevistador informar que quase todo o tráfego chega em poucos minutos após a abertura de vendas, refaça a estimativa para essa janela e verifique separadamente a carga de leitura e a concorrência nas confirmações. Explique quais decisões precisam ser reavaliadas.

## Checklist para a discussão

*Complemento autoral.*

- [ ] Esclareci o escopo e os requisitos que podem mudar o desenho?
- [ ] Explicitei as hipóteses e mostrei como cheguei às estimativas?
- [ ] Consigo justificar os componentes citados e explicar seus trade-offs?
- [ ] Consigo revisar a proposta quando uma premissa muda?
- [ ] Identifiquei o que ainda preciso validar?

## Perguntas de revisão

*Complemento autoral.*

1. O que uma entrevista pode revelar sobre duas pessoas que chegam ao mesmo desenho por caminhos diferentes?
2. Quando vale refinar uma estimativa inicial?
3. Que perguntas mudam a arquitetura do serviço de reservas?
4. Como responder quando uma hipótese é contestada e faltam dados para decidir?
5. Como essa técnica ajuda uma equipe em uma revisão de arquitetura?

## Links relacionados

- [Aula 01 — Entendendo os principais conceitos](./aula-01-entendendo-os-principais-conceitos.md)
- [Índice do Tema 01 — System Design](./README.md)
- [Índice do Módulo 02](../README.md)
