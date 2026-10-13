# Aula 01 — Introdução

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** Solution Architecture  
**Status:** Resumo documentado  
**Fonte:** Síntese fornecida pelo estudante, reorganizada e complementada com exemplos autorais.

## Objetivo

Compreender a arquitetura de soluções como uma disciplina de tomada de decisão que conecta necessidades de negócio, restrições técnicas e consequências operacionais.

## 1. O que é arquitetura de soluções?

Arquitetura de soluções é a prática de definir **como componentes, tecnologias, integrações e processos devem trabalhar juntos** para resolver um problema de negócio dentro de restrições reais.

O arquiteto de soluções não pergunta apenas *“como implementar?”*, mas também:

- **Por quê?** Qual resultado de negócio se deseja alcançar?
- **Para quem?** Quem utiliza e opera a solução?
- **Sob quais restrições?** Quais limites de orçamento, prazo, segurança e equipe existem?
- **Com quais consequências?** Como a decisão impacta manutenção, disponibilidade e evolução?

Uma arquitetura bem-sucedida não precisa ser a mais sofisticada: precisa ser **adequada ao contexto**.

## 2. Conceitos antes de ferramentas

Frameworks, provedores de nuvem e linguagens evoluem. Conceitos como acoplamento, coesão, separação de responsabilidades, consistência e tolerância a falhas ajudam a avaliar alternativas independentemente da stack.

**Exemplo:** antes de adotar microsserviços, avalie os limites dos domínios, a necessidade de implantação independente e a capacidade da equipe de operar um sistema distribuído.

## 3. Pensar como arquiteto

O pensamento arquitetural amplia a análise para além da tarefa imediata. É necessário identificar dependências, requisitos não funcionais e trade-offs.

| Foco local | Visão arquitetural |
| --- | --- |
| Implementar um endpoint | Entender contrato, segurança, volume e consumidores |
| Escolher um banco conhecido | Avaliar padrões de acesso, consistência, custo e operação |
| Entregar uma funcionalidade rapidamente | Considerar prazo **e** custo de evolução e manutenção |
| Adotar uma tecnologia nova | Justificar benefícios frente à complexidade adicional |

## 4. Evitar decisões imediatistas

A alternativa mais rápida no curto prazo pode gerar custos futuros; por outro lado, projetar para uma escala hipotética pode introduzir complexidade desnecessária.

Boas decisões explicitam hipóteses e priorizam necessidades verificáveis, em vez de modismos ou preferências pessoais.

## 5. Custos, restrições e visão sistêmica

Uma solução deve considerar, entre outros fatores:

- **Negócio:** objetivos, prazo, orçamento e impacto esperado.
- **Técnica:** integrações existentes, requisitos de desempenho e segurança.
- **Operação:** observabilidade, implantação, suporte e recuperação de falhas.
- **Pessoas:** conhecimento da equipe, disponibilidade e curva de aprendizado.

A otimização isolada de um componente pode prejudicar o sistema completo.

## 6. Maturidade profissional

A evolução de uma pessoa desenvolvedora inclui passar de **executar escolhas** para **comparar, justificar e acompanhar escolhas**. Esse raciocínio agrega valor mesmo sem o cargo formal de arquiteto.

## Exemplo prático complementar (autoral)

**Cenário hipotético:** uma pequena loja precisa registrar vendas e controlar estoque, inclusive quando a internet está indisponível.

| Alternativa | Benefício | Trade-off |
| --- | --- | --- |
| Aplicação local com banco local | Operação independente da internet | Exige estratégia de backup e manutenção local |
| Aplicação inteiramente na nuvem | Centralização e acesso remoto | Depende de conectividade para operar |
| Operação local com sincronização | Continuidade local e consolidação remota | Exige tratamento de conflitos e falhas de sincronização |

**Raciocínio arquitetural:** primeiro levantar quantidade de terminais, tolerância à indisponibilidade, orçamento, requisitos fiscais e necessidades de sincronização. Só depois selecionar tecnologias e topologia.

> Este exemplo é um exercício ilustrativo acrescentado à documentação, não uma atividade atribuída ao curso.

## Checklist para decisões futuras

- [ ] O problema e o resultado esperado estão claros?
- [ ] Requisitos funcionais e não funcionais foram identificados?
- [ ] Restrições de custo, prazo, equipe e operação foram levantadas?
- [ ] Existem alternativas comparadas por critérios explícitos?
- [ ] Os trade-offs e riscos foram documentados?
- [ ] Há uma forma de validar a decisão após a implementação?

## Perguntas de revisão

1. Por que uma arquitetura tecnicamente elegante pode ser inadequada ao negócio?
2. Qual é a diferença entre escolher uma ferramenta e justificar uma solução?
3. Como uma decisão local pode afetar negativamente o sistema como um todo?

## Síntese

> Arquitetura de soluções não é escolher a tecnologia mais moderna; é compor uma solução justificável, sustentável e alinhada às necessidades reais.

## Próximos passos

Registrar as demais aulas do tema **Solution Architecture**, preservando os títulos e a sequência do curso.
