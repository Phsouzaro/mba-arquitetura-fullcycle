# Aula 02 — Perfil da Função

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** 02 — Solution Architecture  
**Status:** Documentada  
**Origem:** Resumo do estudante, reorganizado e complementado com exemplos autorais.

## Objetivo de aprendizagem

Entender as competências e responsabilidades da pessoa arquiteta de solução, combinando conhecimento do domínio de negócio, experiência tecnológica e leitura do contexto organizacional.

## 1. O perfil da função

A pessoa arquiteta de solução conecta objetivos de negócio, requisitos técnicos e capacidade de execução da organização. Seu trabalho não consiste em escolher a tecnologia mais moderna, mas em propor uma solução **viável, coerente e sustentável** para um contexto específico.

Três eixos orientam sua atuação:

| Eixo | Pergunta principal | Exemplo |
| --- | --- | --- |
| Domínio de negócio | Qual problema precisamos resolver? | Entender regras contábeis e fechamento financeiro |
| Repertório tecnológico | Quais alternativas atendem aos requisitos? | Comparar APIs, filas, bancos e modelos de hospedagem |
| Contexto organizacional | O que a empresa consegue implantar e operar? | Considerar orçamento, equipe, legado e prazos |

## 2. Por que raramente é uma função de entrada?

A arquitetura de solução costuma exigir experiência acumulada em implementação, manutenção, incidentes, integrações e decisões com trade-offs reais.

Isso não significa que apenas pessoas com determinado título ou número fixo de anos possam contribuir com arquitetura. Significa que **a responsabilidade por decisões amplas normalmente exige repertório prático e capacidade de antecipar consequências**.

## 3. Domínio de negócio

Domínio é compreender como a organização trabalha, quais regras são centrais e quais problemas têm impacto real.

**Exemplo:** em sistemas contábeis, conhecer apenas APIs e bancos de dados não basta. É necessário entender processos de conciliação, fechamento, integrações com outros sistemas e exigências de auditoria.

Sem esse conhecimento, uma solução pode estar tecnicamente correta e ainda resolver o problema errado.

## 4. Repertório tecnológico aplicado

Conhecer diferentes tecnologias ajuda a comparar alternativas sem ficar preso à stack preferida.

Uma pessoa arquiteta precisa reconhecer:
- Capacidades e limites das plataformas;
- Custos de desenvolvimento e operação;
- Integração com sistemas existentes;
- Riscos de manutenção e evolução;
- Conhecimento disponível na equipe.

O objetivo não é dominar profundamente todas as ferramentas, mas **saber avaliar opções, consultar especialistas e justificar decisões**.

## 5. Domínio e tecnologia precisam caminhar juntos

**Domínio sem tecnologia:** pode produzir uma proposta que atende à operação, mas não é implementável.

**Tecnologia sem domínio:** pode gerar um desenho sofisticado que ignora regras, riscos e prioridades de negócio.

A arquitetura conecta esses conhecimentos e transforma requisitos em decisões concretas.

## 6. Contexto organizacional e restrições

Decisões arquiteturais dependem de orçamento, maturidade, competências da equipe, legado, cultura, prazos e exigências operacionais.

Uma solução distribuída em múltiplos serviços pode ser adequada para uma empresa com equipe especializada, mas excessivamente complexa para outra organização com poucos profissionais e infraestrutura limitada.

## 7. Custos e operação

A escolha arquitetural deve considerar **custo total de propriedade (TCO)**: implantação, infraestrutura, observabilidade, suporte, treinamento, manutenção e evolução.

Também importa avaliar a capacidade de resposta a incidentes e a dependência de fornecedores. Uma alternativa tecnicamente superior em um critério pode ser pior no conjunto.

## 8. Exemplo complementar — escolher uma arquitetura viável

**Cenário hipotético:** uma empresa de médio porte precisa modernizar um sistema interno, mas possui uma equipe pequena e orçamento limitado.

| Alternativa | Vantagem | Desafio |
| --- | --- | --- |
| Microsserviços em plataforma cloud gerenciada | Evolução independente de serviços | Maior complexidade operacional e custos recorrentes |
| Monólito modular com deploy automatizado | Fronteiras claras e operação mais simples | Exige disciplina para preservar os módulos |

**Possível decisão:** iniciar com monólito modular e contratos bem definidos, monitorando indicadores que justifiquem futuras separações. A escolha não é universal; depende de requisitos de escala, disponibilidade e organização.

> Exemplo autoral para ilustrar trade-offs, não atividade oficial do MBA.

## 9. Complexidade enterprise

Em empresas grandes, múltiplas unidades, tecnologias heterogêneas e integrações tornam as decisões interdependentes. A pessoa arquiteta precisa negociar restrições e comunicar impactos a equipes técnicas e stakeholders.

**Complemento:** habilidades de comunicação, facilitação de decisões e registro de justificativas são importantes porque arquitetura é também trabalho colaborativo.

## Checklist de atuação

- [ ] Entendi o problema e as regras do domínio?
- [ ] Identifiquei stakeholders e restrições reais?
- [ ] Comparei mais de uma alternativa?
- [ ] Considerei custos de implantação e operação?
- [ ] Avaliei competências e maturidade da equipe?
- [ ] Registrei trade-offs e riscos?
- [ ] Consegui explicar a decisão em linguagem de negócio e técnica?

## Perguntas de revisão

1. Por que experiência prática costuma ser importante para a função?
2. O que pode acontecer quando uma decisão considera apenas tecnologia?
3. Como o conhecimento de domínio muda uma arquitetura contábil?
4. Por que uma solução sofisticada pode ser inadequada ao orçamento e à equipe?
5. Quais competências além das técnicas ajudam a sustentar decisões arquiteturais?

## Síntese

> A pessoa arquiteta de solução não escolhe apenas como construir: ela avalia o que faz sentido construir, com quais tecnologias e dentro de quais limites organizacionais.

## Conexões

- [Aula 01 — O que é arquitetura de solução?](./aula-01-o-que-e-arquitetura-de-solucao.md)
- [Tema 01 — Solution Enterprise](../tema-01-solution-enterprise/README.md)
