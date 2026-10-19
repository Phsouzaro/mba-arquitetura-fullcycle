# Aula 16 — Risco vs. Documentação

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** 02 — Solution Architecture  
**Origem:** Resumo do estudante, com exemplos e complementos autorais identificados.  
**Situação:** Aula final do Tema 02.

## Objetivo

Entender por que a documentação arquitetural deve ser **proporcional aos riscos e à criticidade** de cada solução, escolhendo representações e registros que reduzam incertezas sem gerar burocracia desnecessária.

## 1. O princípio: documentar para reduzir risco

A documentação arquitetural não é um fim em si mesma. Ela deve ajudar pessoas a:

- Entender decisões e premissas importantes;
- Identificar dependências e possíveis pontos de falha;
- Revisar escolhas antes que erros se tornem caros;
- Compartilhar conhecimento entre equipes;
- Operar, manter e evoluir a solução com segurança.

**Ideia central:** documentar o suficiente para reduzir riscos relevantes — e não produzir todos os artefatos possíveis por hábito.

Pouca documentação em sistemas críticos deixa decisões importantes implícitas. Documentação excessiva em sistemas simples pode consumir mais tempo de produção, leitura e manutenção do que o risco justifica.

## 2. Proporcionalidade entre risco e formalização

A necessidade de formalização aumenta conforme fatores como:

| Fator | Pergunta arquitetural |
| --- | --- |
| Impacto da falha | Qual prejuízo operacional, financeiro, humano ou reputacional pode ocorrer? |
| Complexidade | Quantos componentes e comportamentos precisam ser compreendidos? |
| Integrações | Quantos sistemas externos e contratos precisam funcionar juntos? |
| Mudanças | Qual a chance de alterações provocarem efeitos colaterais? |
| Recuperação | Quão difícil é detectar, corrigir e reverter uma falha? |
| Requisitos regulatórios | Quais evidências e controles são obrigatórios? |
| Dependência de conhecimento | O que acontece se pessoas-chave deixarem a equipe? |

O nível de documentação deve considerar **impacto, probabilidade, detectabilidade, incerteza e obrigações aplicáveis**, sem presumir que um único escore substitua análise profissional.

## 3. Exemplo: CRUD de uma padaria

**Cenário da aula:** um CRUD simples, com poucas regras, usuários e integrações, tende a demandar menos formalização.

Documentação possivelmente suficiente:

- README com objetivo, requisitos e instruções de execução;
- Modelo de dados simples, se houver ambiguidade;
- Registro breve de decisões não óbvias;
- Orientações de backup e recuperação, se os dados forem importantes.

Não há razão automática para criar um conjunto extenso de views, relatórios e aprovações.

**Ressalva:** o rótulo “CRUD” não garante baixo risco. Se o sistema sustenta vendas, estoque crítico ou dados pessoais, o impacto real deve ser reavaliado.

## 4. Exemplo: transferência bancária

**Cenário da aula:** uma solução de transferência bancária pode envolver sistemas legados, mensageria, múltiplas plataformas internas, integração com infraestrutura financeira e exigências regulatórias.

Uma falha pode causar inconsistência de saldos, movimentação duplicada, indisponibilidade, perdas financeiras e impactos regulatórios ou reputacionais.

Documentação relevante pode incluir:

- Fluxos de ponta a ponta e estados da transação;
- Contratos de integração e responsabilidades;
- Tratamento de timeout, retry, idempotência e reconciliação;
- Modelo de consistência e recuperação;
- Controles de segurança e trilhas de auditoria;
- Deployment, dependências, observabilidade e resposta a incidentes;
- Decisões arquiteturais (ADRs), premissas e trade-offs;
- Evidências de revisão, testes e requisitos regulatórios aplicáveis.

**Nuance:** nem toda transferência bancária se integra diretamente ao Banco Central; as dependências e obrigações variam conforme o arranjo, a instituição e o sistema. Kafka, mainframe e microservices são exemplos possíveis, não requisitos universais.

## 5. Matriz ilustrativa de risco e documentação

**Complemento autoral — ferramenta de discussão, não regra normativa:**

| Impacto | Incerteza / complexidade baixa | Incerteza / complexidade alta |
| --- | --- | --- |
| Baixo | Documentação enxuta e instruções essenciais | Registrar interfaces, premissas e decisões de maior dúvida |
| Alto | Formalizar controles críticos, fluxos de falha e recuperação | Views direcionadas, contratos, ADRs, revisões independentes e planos operacionais |

A matriz ajuda a **priorizar conversas**, não a dispensar controles obrigatórios. Um risco raro com impacto extremo pode justificar documentação rigorosa.

## 6. Viewpoints como instrumentos de controle de risco

As [Views e Viewpoints](./aula-14-views-e-viewpoints.md) e o [modelo 4+1](./aula-15-modelo-4-mais-1.md) oferecem maneiras de inspecionar riscos diferentes:

| Risco a esclarecer | Representação útil |
| --- | --- |
| Responsabilidades confusas | View lógica / contexto |
| Timeout e operações duplicadas | View de processo / sequência |
| Dependências difíceis de manter | View de desenvolvimento |
| Ponto único de falha | View física / deployment |
| Falta de entendimento sobre decisões | ADRs e registro de premissas |
| Exposição indevida de dados | Fluxo de dados e análise de segurança |

**Não é necessário produzir todas as views em todo projeto.** A seleção depende das perguntas dos stakeholders e dos riscos que precisam ser esclarecidos.

## 7. Double check e revisão de decisões

Em soluções críticas, documentar cria condições para **revisão independente**.

Uma revisão efetiva deve permitir que outras pessoas:

1. Entendam o problema e os critérios de sucesso;
2. Identifiquem premissas e restrições;
3. Inspecionem fluxos normais e de exceção;
4. Questionem trade-offs e pontos únicos de falha;
5. Verifiquem responsáveis por decisões e controles;
6. Registrem pendências, riscos aceitos e próximos passos.

A documentação **não substitui** testes, monitoramento, governança ou validações exigidas; ela torna essas atividades mais claras e auditáveis.

## 8. O custo de documentar também entra na decisão

Produzir um documento custa tempo. Mantê-lo atualizado também.

**Complemento autoral — avaliação simples:**

```text
Valor esperado da documentação
≈ risco relevante reduzido + ganho de comunicação e manutenção
  − custo de criação, revisão e atualização
```

Essa expressão é **qualitativa**, não uma fórmula financeira universal.

Uma view desatualizada pode ser pior do que um registro curto e confiável. A documentação precisa ter propósito, público e responsável por manutenção.

A análise também se conecta ao [TCO](./aula-05-iniciando-com-tco.md): documentação é investimento e custo de ciclo de vida, não apenas uma atividade inicial.

## 9. Aplicação prática: documentação mínima orientada a riscos

**Roteiro complementar autoral:**

1. Identificar o objetivo e o escopo da solução;
2. Listar os riscos e as incertezas mais importantes;
3. Associar cada risco a uma pergunta que precisa ser respondida;
4. Escolher o menor artefato capaz de responder com clareza;
5. Validar com stakeholders e especialistas relevantes;
6. Registrar decisões, responsáveis e riscos residuais;
7. Revisar os artefatos quando decisões e riscos mudarem.

### Exemplo de registro de decisão documental

| Risco | Artefato escolhido | Quem valida | Motivo |
| --- | --- | --- | --- |
| Pagamento duplicado | Diagrama de sequência + contrato de idempotência | Engenharia e operações | Explicitar estados e reprocessamento |
| Indisponibilidade do banco | Diagrama de deployment + plano de recuperação | Plataforma e negócio | Identificar falhas e expectativas de recuperação |
| Ambiguidade de status | Glossário e contrato de API | Domínio e times integrados | Evitar inconsistência semântica |

## 10. Checklist arquitetural

- [ ] Identifiquei o impacto real de uma falha?
- [ ] Avaliei complexidade, integrações e dependências?
- [ ] Conheço obrigações regulatórias e controles exigidos?
- [ ] Cada artefato responde a uma pergunta ou risco concreto?
- [ ] Registrei premissas e decisões difíceis de reverter?
- [ ] Os fluxos críticos incluem cenários de falha?
- [ ] As pessoas certas conseguem revisar a solução?
- [ ] A documentação tem responsáveis e plano de atualização?
- [ ] Evitei formalização sem benefício proporcional?
- [ ] Registrei riscos residuais e validações pendentes?

## Perguntas de revisão

1. Por que documentação excessiva também pode representar um problema?
2. Quais fatores tornam uma solução mais crítica?
3. Quando um CRUD aparentemente simples pode exigir documentação adicional?
4. Quais views ajudariam a investigar uma transferência bancária com risco de duplicidade?
5. Como o double check reduz dependência de conhecimento tácito?
6. Por que documentação não substitui testes e controles operacionais?
7. Como decidir qual artefato arquitetural produzir primeiro?

## Síntese

> **Documentar bem não é documentar tudo. É produzir evidência suficiente para compreender, revisar e controlar os riscos relevantes da solução.**

## Encerramento do Tema 02 — Solution Architecture

Este tema percorreu a definição da arquitetura de solução, o perfil e as habilidades da função, princípios de design, TCO, relação com Enterprise Architecture, níveis de análise, visão e escopo, domínio e linguagem, Lei de Conway, views/viewpoints e modelo 4+1.

A lição de encerramento conecta esses conceitos: **as decisões e os artefatos arquiteturais devem ser proporcionais ao contexto e aos riscos reais do negócio**.

## Conexões

- [Aula 04 — Princípios para Arquitetar uma Solução](./aula-04-principios-para-arquitetar-uma-solucao.md)
- [Aula 05 — Iniciando com TCO](./aula-05-iniciando-com-tco.md)
- [Aula 10 — Nível 0: Escopo](./aula-10-nivel-0-escopo.md)
- [Aula 14 — Views e Viewpoints](./aula-14-views-e-viewpoints.md)
- [Aula 15 — Modelo 4+1](./aula-15-modelo-4-mais-1.md)
