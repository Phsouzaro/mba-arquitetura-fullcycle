# Aula 01 — Introdução

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema / submódulo:** Solution Enterprise  
**Status:** Documentada  
**Origem:** Síntese autoral baseada no resumo de estudo enviado pelo aluno, com exemplos complementares identificados.

## Objetivo de aprendizagem

Entender o papel da arquitetura de soluções na conexão entre necessidades de negócio, decisões técnicas, restrições e sustentabilidade operacional.

## 1. Arquitetura de soluções

Arquitetura de soluções é a disciplina de pensar e estruturar uma solução de software considerando o **problema completo**, e não apenas o código. A escolha de tecnologias precisa responder a objetivos de negócio e às condições reais de implementação e operação.

Perguntas essenciais:
- Que problema estamos resolvendo e qual resultado esperamos?
- Quais são os requisitos funcionais e não funcionais?
- Quais restrições de orçamento, prazo, equipe e infraestrutura existem?
- Como a solução será mantida, monitorada e evoluída?

## 2. Conceitos antes de técnicas

Frameworks e ferramentas mudam; princípios como **coesão, acoplamento, separação de responsabilidades e trade-offs** permitem avaliar alternativas de forma mais consistente.

**Aplicação:** antes de escolher uma stack, identificar quais capacidades a solução realmente exige. Uma tecnologia familiar pode ser mais adequada que uma novidade, dependendo do contexto.

## 3. Pensar como arquiteto de solução

O pensamento arquitetural amplia o foco da tarefa para dependências, efeitos colaterais e consequências ao longo do tempo.

| Perspectiva limitada | Perspectiva arquitetural |
| --- | --- |
| Como implementar a funcionalidade? | Que problema ela resolve e como afeta o sistema? |
| Qual tecnologia é mais moderna? | Qual alternativa atende melhor às restrições? |
| Como entregar mais rápido? | Como equilibrar prazo, custo, qualidade e evolução? |

## 4. Limites da visão imediatista

Priorizar apenas velocidade ou novidade tecnológica pode aumentar complexidade, custos operacionais e dificuldades de manutenção. Por outro lado, excesso de planejamento e abstrações também pode ser prejudicial.

O objetivo é tomar decisões **proporcionais ao problema**, registrando as premissas e riscos.

## 5. Custos, restrições e visão geral

Uma solução tecnicamente elegante pode não ser viável economicamente ou operacionalmente. É preciso avaliar:

- **Negócio:** orçamento, prazo, impacto e prioridades.
- **Técnica:** integrações, performance, segurança e disponibilidade.
- **Operação:** monitoramento, suporte, backups e recuperação.
- **Pessoas:** experiência e capacidade de manutenção da equipe.

Uma melhoria isolada em um componente pode introduzir problemas para o conjunto.

## 6. Maturidade profissional

A maturidade arquitetural aparece quando deixamos de apenas implementar decisões e passamos a **avaliar alternativas, justificar escolhas e acompanhar suas consequências**. Essa habilidade é valiosa mesmo para quem não exerce formalmente o cargo de arquiteto.

## Exemplo complementar — cenário hipotético

Uma loja precisa de um sistema de vendas que continue operando durante quedas de internet.

| Alternativa | Benefício | Restrição / trade-off |
| --- | --- | --- |
| Sistema local | Continua operando sem internet | Exige backups e manutenção local |
| Sistema em nuvem | Facilita centralização e acesso remoto | Dependência de conectividade |
| Sistema local com sincronização | Combina continuidade local e consolidação remota | Mais complexidade e possíveis conflitos de dados |

**Conclusão do exemplo:** a decisão não deve começar pela tecnologia. Primeiro é necessário levantar quantidade de terminais, orçamento, requisitos de disponibilidade, integrações e regras de sincronização.

> Exemplo elaborado como complemento didático; não representa um exercício oficial do MBA.

## Checklist de revisão

- [ ] Consigo explicar o problema de negócio sem mencionar tecnologias?
- [ ] Sei diferenciar requisitos de restrições?
- [ ] Consigo comparar ao menos duas alternativas e seus trade-offs?
- [ ] Considerei custos operacionais e manutenção?
- [ ] Sei justificar a escolha para pessoas técnicas e não técnicas?

## Perguntas para fixação

1. Por que a solução tecnicamente mais elegante pode não ser a mais adequada?
2. O que diferencia pensamento arquitetural de implementação imediata?
3. Como restrições de negócio afetam decisões técnicas?

## Síntese

> Pensar como arquiteto de soluções é conectar objetivos, restrições, decisões e consequências para construir sistemas adequados ao contexto.
