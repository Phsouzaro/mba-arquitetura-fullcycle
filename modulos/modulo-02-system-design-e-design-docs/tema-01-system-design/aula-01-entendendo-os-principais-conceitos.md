# Aula 01 — Entendendo os principais conceitos

**Módulo** · 02 — System Design e Design Docs  
**Tema** · 01 — System Design  
**Origem** · Anotações fornecidas. O exemplo aplicado, o checklist e as perguntas de revisão são complementos autorais.

## Objetivo

Entender System Design como um processo de decisão. A partir de requisitos e restrições, o trabalho é selecionar o que importa, estimar ordens de grandeza e comparar alternativas pelos seus efeitos imediatos e ao longo do tempo.

## System Design como processo

System Design é o processo de definir a arquitetura, os componentes, os módulos, as interfaces e os dados de um sistema para atender a requisitos específicos. O diagrama registra parte do resultado. Ele ganha valor quando permite explicar como o problema foi interpretado, por que certas escolhas foram feitas e quais condições sustentam a proposta.

## Arquitetura intencional

Comece pelo problema que o sistema precisa resolver e pelas condições nas quais ele precisa operar. A decisão de incluir um balanceador, por exemplo, depende de necessidades como distribuir tráfego entre instâncias. Cada componente deve atender a uma necessidade identificável. Essa relação permite revisar o desenho se as restrições mudarem ou se uma alternativa resolver o mesmo problema com menor custo operacional.

## Aproximações úteis

Estimativas iniciais servem para orientar a discussão sob incerteza. Ordens de grandeza e intervalos ajudam a descobrir se uma alternativa merece análise mais detalhada. Registre as premissas e refine o cálculo quando uma diferença plausível puder mudar a decisão. Essa abordagem será útil ao estimar requisitos, capacidade e custos nas próximas etapas.

## Foco nas decisões que importam

Dê prioridade às restrições que mudam o desenho, aos efeitos de escala e às escolhas caras de reverter. Uma análise inicial pode ser suficiente para alinhar os envolvidos quando deixa claras as decisões tomadas, as premissas e as questões que ainda precisam ser verificadas.

## Exploração e comparação de soluções

Um problema pode admitir várias soluções tecnicamente válidas. Planejar mais de uma opção ajuda a separar familiaridade de adequação e amplia o repertório para problemas futuros. Compare as opções sob os mesmos requisitos e restrições para entender qual atende melhor ao negócio naquele momento.

Se uma aplicação precisa responder rapidamente, um cache em memória pode reduzir a latência e acrescentar custo. Compare a diferença de desempenho com uma abordagem mais simples e pergunte se o ganho muda a experiência do usuário ou atende a um objetivo que a opção mais barata deixa de cumprir. A decisão depende desse efeito prático e das condições em que ele foi medido.

## Consequências ao longo do tempo

Avalie como as escolhas afetam custo, operação e crescimento depois da entrega inicial. Uma taxa diária de armazenamento pode parecer pequena e se tornar relevante quando acumulada por cinco anos. Projeções ajudam a identificar quando uma decisão deve ser revista e quais mudanças serão difíceis se o volume crescer.

## Exemplo aplicado ao serviço de reservas

*Complemento autoral.*

O serviço precisa exibir a disponibilidade com latência p95 de até 250 ms. O fluxo de confirmação consulta a fonte transacional para validar a disponibilidade no momento da reserva. Para a consulta, a equipe considera dois caminhos.

| Alternativa | Benefício | Consequência |
| --- | --- | --- |
| Consultar o banco diretamente | Menos componentes e dados atualizados na leitura | O aumento de consultas pode elevar a latência e competir com as confirmações pela capacidade do banco. |
| Consultar um cache em memória | Leituras repetidas podem responder mais rápido e reduzir a carga no banco | A equipe assume custo de infraestrutura e precisa lidar com expiração, dados desatualizados e consultas que não encontram o dado no cache. |

Se um teste representativo medir p95 de 200 ms com leitura direta e 90 ms com cache, ambas as opções atendem à meta hipotética. A leitura direta pode ser a escolha inicial, desde que a equipe verifique se existe margem para o crescimento esperado. Se o aumento de tráfego aproximar o serviço do limite, reavalie o cache com base na taxa de acertos, no custo e na tolerância a dados desatualizados.

O armazenamento também merece uma estimativa. Se o sistema retiver cerca de 2 GB novos por dia durante cinco anos, o volume bruto chega a aproximadamente 3,65 TB, assumindo 365 dias por ano e taxa constante. Esse cálculo exclui índices, réplicas e backups. A ordem de grandeza já orienta a discussão sobre retenção e custo, e a equipe pode refinar a estimativa se essas premissas afetarem a decisão.

## Checklist de System Design

*Complemento autoral.*

- [ ] Defini o problema, os requisitos relevantes e as restrições que mudam o desenho?
- [ ] Consigo explicar por que cada componente está presente?
- [ ] Registrei as premissas das estimativas e sei quais exigem validação?
- [ ] Comparei alternativas pelos mesmos critérios de desempenho, custo e operação?
- [ ] Avaliei o crescimento e identifiquei quando a decisão deve ser revista?

## Perguntas de revisão

*Complemento autoral.*

1. Que parte do trabalho de System Design acontece antes de desenhar o diagrama?
2. Em que situação uma estimativa aproximada é suficiente? Quando vale refiná-la?
3. Quais decisões merecem ser discutidas primeiro em uma revisão de arquitetura?
4. Que evidências justificariam introduzir um cache no exemplo de reservas?
5. Como a retenção de dados por cinco anos pode afetar uma escolha que parece adequada hoje?

## Links relacionados

- [Índice do Tema 01](./README.md)
- [Índice do Módulo 02](../README.md)
- [Aula 01 do Tema 05 — Arquitetura de Solução para Cloud](../../modulo-01-fundamentos-arquitetura-solucao/tema-05-aws-well-architected-framework/aula-01-arquitetura-de-solucao-para-cloud.md)
- [Aula 02 do Tema 05 — AWS Well-Architected](../../modulo-01-fundamentos-arquitetura-solucao/tema-05-aws-well-architected-framework/aula-02-aws-well-architected.md)
