# Aula 05 — Iniciando com TCO

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** 02 — Solution Architecture  
**Origem:** Resumo do estudante, com aprofundamentos e exemplos autorais identificados.

## Objetivo

Entender o **Total Cost of Ownership (TCO)** como critério arquitetural para avaliar viabilidade econômica, comparar alternativas e justificar decisões ao longo do ciclo de vida da solução.

## 1. O que é TCO?

**TCO** representa o custo total de possuir, operar e evoluir uma solução durante um horizonte definido. Não se limita ao investimento de desenvolvimento: inclui infraestrutura, operação, manutenção, suporte, licenças, segurança, atualizações e mudanças futuras.

Uma arquitetura pode cumprir todos os requisitos técnicos e ainda ser inviável se seu custo recorrente superar a capacidade financeira ou o valor que entrega.

## 2. O erro de considerar apenas o desenvolvimento

Avaliar apenas o preço de construção ignora despesas que continuam depois do go-live.

| Etapa | Custos a investigar |
| --- | --- |
| Construção | Análise, implementação, testes, integração e migração |
| Implantação | Infraestrutura inicial, treinamento e transição |
| Operação | Cloud, rede, licenças, monitoramento, suporte e equipe |
| Evolução | Correções, melhorias, atualização de dependências |
| Encerramento | Migração, desativação e retenção obrigatória de dados |

O horizonte de **cinco anos** é útil para comparar cenários, mas deve ser ajustado ao tipo de solução e à estratégia da empresa.

## 3. Negócio, solução e infraestrutura

Separar três camadas ajuda a explicar a origem dos custos:

- **Negócio:** processos, casos de uso, criticidade e valor esperado.
- **Solução técnica:** componentes, integrações, contratos e complexidade de manutenção.
- **Infraestrutura:** hospedagem, armazenamento, processamento, rede e ferramentas operacionais.

A separação melhora a rastreabilidade entre requisitos, decisões e despesas, mas alguns custos atravessam mais de uma camada.

## 4. A pessoa arquiteta e a área comercial

Em propostas enterprise, a pessoa arquiteta pode apoiar a equipe comercial com uma visão tecnicamente defensável:

1. Esclarecer o problema e os requisitos.
2. Explicar alternativas arquiteturais.
3. Estimar custos e premissas.
4. Mostrar riscos, limitações e benefícios.
5. Sustentar a recomendação diante dos stakeholders.

A responsabilidade pela aprovação financeira costuma ser compartilhada com negócio, financeiro e gestão, e não exclusivamente da arquitetura.

## 5. TCO e aprovação executiva

Uma proposta executiva deve responder:

- **Quanto custa implantar?**
- **Quanto custa manter por mês ou ano?**
- **Quais fatores podem aumentar o custo?**
- **Qual valor de negócio é esperado?**
- **Quais alternativas foram consideradas?**

**Complemento:** TCO mede custos; **ROI** e análise de benefícios ajudam a discutir retorno. Não são a mesma métrica.

## 6. Simulação didática de cinco anos

**Cenário hipotético:** duas opções atendem aos requisitos mínimos de uma integração.

| Categoria | Opção A: solução simples | Opção B: plataforma complexa |
| --- | ---: | ---: |
| Implantação inicial | R$ 80.000 | R$ 120.000 |
| Operação e manutenção mensal | R$ 4.000 | R$ 10.000 |
| Custo recorrente em 60 meses | R$ 240.000 | R$ 600.000 |
| **TCO em 5 anos** | **R$ 320.000** | **R$ 720.000** |

**Fórmula simplificada:** TCO = implantação + (custo mensal × número de meses) + demais custos previstos.

A diferença é de **R$ 400.000** em cinco anos. A opção B só se justifica se entregar benefícios, reduzir riscos ou atender requisitos que compensem essa diferença.

> Valores inteiramente fictícios e sem desconto a valor presente, inflação, impostos ou variação de demanda. Não representam preços reais de fornecedores nem atividade oficial do MBA.

## 7. Hype tecnológico: o exemplo do Kafka

O resumo da aula apresenta um caso em que **Apache Kafka** foi sugerido para comunicação entre áreas, mas sua operação consumiria **50% do orçamento de manutenção do projeto**.

O problema não é Kafka: trata-se de uma tecnologia útil quando existem requisitos adequados de streaming, escala e distribuição de eventos. O problema é adotá-la sem demonstrar por que alternativas mais simples não atenderiam.

Antes de decidir, investigar:
- Quantos produtores e consumidores existem?
- Qual volume de eventos e qual latência são necessários?
- É preciso retenção e reprocessamento?
- Uma API, fila ou integração em lote resolveria?
- Quem operará e monitorará a plataforma?
- Qual é o custo recorrente comparado ao orçamento?

## 8. Viés técnico e responsabilidade futura

Preferências por ferramentas conhecidas ou populares podem distorcer decisões. A recomendação arquitetural precisa partir de requisitos, alternativas e evidências.

**Boa prática complementar:** registrar em uma ADR a decisão, as opções descartadas, as premissas de custo, os riscos e as condições para revisitar a escolha.

## 9. Checklist de TCO

- [ ] O horizonte de análise está definido?
- [ ] Separei custos iniciais, recorrentes e de evolução?
- [ ] Considerei licenças, suporte, observabilidade e equipe?
- [ ] Registrei premissas e incertezas das estimativas?
- [ ] Comparei alternativas tecnicamente viáveis?
- [ ] Relacionei o custo ao valor de negócio esperado?
- [ ] Avaliei dependência de fornecedores e riscos operacionais?
- [ ] A recomendação pode ser explicada a gestores não técnicos?

## Perguntas de revisão

1. Por que o custo inicial não representa o TCO?
2. Como a separação entre negócio, solução e infraestrutura ajuda a estimar custos?
3. Qual a diferença entre TCO e ROI?
4. Em quais condições Kafka pode justificar um custo operacional elevado?
5. Como evitar viés tecnológico na escolha de uma arquitetura?
6. Quais premissas precisam acompanhar uma projeção de cinco anos?

## Síntese

> Uma arquitetura sustentável não é apenas a que funciona tecnicamente, mas a que entrega valor dentro de um custo total que a organização consegue justificar e manter.

## Conexões

- [Aula 02 — Perfil da Função](./aula-02-perfil-da-funcao.md): contexto organizacional e custos.
- [Aula 03 — Soft Skills](./aula-03-soft-skills.md): comunicação executiva e negociação.
- [Aula 04 — Princípios para Arquitetar uma Solução](./aula-04-principios-para-arquitetar-uma-solucao.md): objetivos de negócio e trade-offs.
- [Tema 01 — Aula 08, Integração](../tema-01-solution-enterprise/aula-08-integracao.md): tecnologias e padrões de integração.
