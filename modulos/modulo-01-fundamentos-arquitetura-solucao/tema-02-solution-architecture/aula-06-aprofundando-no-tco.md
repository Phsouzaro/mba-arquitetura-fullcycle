# Aula 06 — Aprofundando no TCO

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** 02 — Solution Architecture  
**Origem:** Resumo do estudante, reorganizado com exemplos e aprofundamentos autorais.

## Objetivo

Aprofundar a avaliação do **Total Cost of Ownership (TCO)** considerando comprar ou construir, dependências externas, contingência, operação e custo de desativação.

## 1. Comprar ou construir: Buy vs. Build

A decisão entre contratar uma solução pronta e desenvolver internamente depende de custo total, tempo de entrega, diferenciação competitiva, riscos e capacidade operacional.

| Critério | Comprar | Construir |
| --- | --- | --- |
| Tempo inicial | Pode acelerar a adoção | Exige desenvolvimento |
| Personalização | Limitada por produto e contrato | Maior controle sobre regras |
| Dependência | Fornecedor, licenças e APIs | Equipe, stack e conhecimento interno |
| Evolução | Depende do roadmap contratado | Depende da capacidade da organização |
| Custo | Aquisição, integração e operação | Desenvolvimento, manutenção e operação |

**Pergunta central:** a capacidade faz parte do *core business* e diferencia a empresa? Se não, vale investigar soluções existentes antes de reconstruí-la.

Comprar não elimina integração, configuração, migração, segurança nem suporte.

## 2. Dependência de terceiros como custo

Serviços externos fazem parte da experiência do usuário, mesmo quando estão fora do controle da equipe.

**Exemplos do resumo:** gateway de pagamento e integrações com a SEFAZ. Latência ou indisponibilidade podem impedir vendas, faturamento ou outras operações críticas.

Custos associados:
- Monitorar disponibilidade e tempo de resposta;
- Investigar incidentes e acionar fornecedores;
- Implementar timeouts, retentativas e tratamento de falhas;
- Preparar processos alternativos quando permitidos;
- Lidar com impacto de negócio durante interrupções.

A existência de um terceiro não transfere integralmente a responsabilidade pela continuidade do processo.

## 3. Contingência custa antes da falha

Contingência é preparar caminhos alternativos para falhas previsíveis: rotas secundárias, fallback, operação manual, recuperação e suporte especializado.

Seu TCO inclui **desenho, implementação, testes periódicos e manutenção**, além do custo de acionamento.

> Complemento: nem todo fallback é seguro ou legalmente permitido. Em operações fiscais e financeiras, a alternativa precisa respeitar regras de negócio e exigências regulatórias.

## 4. Categorias de custo no ciclo de vida

| Categoria | O que contempla |
| --- | --- |
| **Aquisição** | Licenças, assinaturas, contratação e capacidade externa |
| **Implementação** | Integração, parametrização, migração, testes e treinamento |
| **Manutenção** | Correções, atualizações e adaptações para manter o software utilizável |
| **Operação** | Infraestrutura, execução contínua, monitoramento, suporte operacional e resposta a incidentes |
| **Contingência** | Preparação e sustentação de alternativas para falhas |
| **Inativação** | Migração de saída, retenção de dados, contratos e desligamento seguro |

As categorias devem ser definidas sem dupla contagem: por exemplo, o suporte pode ser classificado em manutenção ou operação conforme sua finalidade e a convenção financeira adotada.

## 5. Infraestrutura e observabilidade

Servidores, ambientes, rede, armazenamento, logs, métricas, traces e pessoas responsáveis pela operação geram custos recorrentes.

A observabilidade permite identificar degradação e investigar falhas. Seu custo deve ser dimensionado pelo risco e criticidade, incluindo retenção de telemetria, processamento e licenciamento.

## 6. Sofisticação técnica versus viabilidade

Uma solução mais precisa ou escalável não é automaticamente a melhor escolha se seu benefício incremental não justificar o custo.

**Exemplo conceitual do resumo:** modelos de recomendação de streaming podem ter diferentes níveis de precisão e consumo computacional. A decisão precisa comparar melhoria real de resultado com custo adicional, não apenas métricas técnicas isoladas.

## 7. Inativação: o custo de saída

Retirar um CRM de produção pode exigir:
1. Inventariar dados, integrações e usuários;
2. Exportar e validar informações;
3. Migrar processos para a solução substituta;
4. Atender obrigações de retenção e privacidade;
5. Encerrar licenças e contratos;
6. Desativar infraestrutura e acessos com segurança.

Contratos de longo prazo e recursos reservados podem continuar gerando despesas após a desativação. Esse risco deve entrar na análise desde a aquisição.

## 8. Simulação complementar — custo de contingência e saída

**Cenário inteiramente hipotético:** uma empresa avalia uma solução contratada por três anos.

| Item | Valor estimado |
| --- | ---: |
| Aquisição e implantação | R$ 60.000 |
| Operação e manutenção (36 × R$ 5.000) | R$ 180.000 |
| Preparação e testes de contingência | R$ 24.000 |
| Migração e inativação ao final | R$ 36.000 |
| **TCO estimado em 3 anos** | **R$ 300.000** |

**Fórmula simplificada:** TCO = aquisição + implementação + manutenção + operação + contingência + inativação.

> Exemplo autoral ilustrativo. Valores fictícios, sem inflação, impostos, desconto a valor presente ou custos de incidentes não previstos.

## 9. Como estruturar uma avaliação econômica

1. Definir horizonte temporal e premissas;
2. Listar alternativas viáveis de compra e construção;
3. Identificar custos iniciais e recorrentes;
4. Mapear terceiros críticos e contingências;
5. Estimar custos de evolução e operação;
6. Planejar migração e desligamento;
7. Comparar custos com benefícios e riscos;
8. Registrar incertezas e revisar estimativas ao longo do projeto.

## Checklist de revisão

- [ ] A solução é parte do diferencial competitivo?
- [ ] Comprar e construir foram comparados no mesmo horizonte?
- [ ] Integração com terceiros e riscos de indisponibilidade foram considerados?
- [ ] Contingências possuem custos de implantação e teste?
- [ ] Manutenção e operação foram diferenciadas?
- [ ] Observabilidade e suporte estão no orçamento?
- [ ] Existe plano e estimativa para migração e inativação?
- [ ] Contratos, retenção de dados e compromissos financeiros foram avaliados?

## Perguntas de fixação

1. Quando comprar uma solução pode ser melhor do que construí-la?
2. Por que dependências externas aumentam o TCO?
3. Qual a diferença entre custo de manutenção e custo de operação?
4. Como o custo de contingência altera a escolha arquitetural?
5. Por que o melhor desempenho técnico nem sempre gera o melhor resultado econômico?
6. Quanto custaria desativar a solução atual sem perder dados nem interromper processos essenciais?

## Síntese

> TCO completo considera toda a jornada: adquirir, implementar, operar, manter, proteger contra falhas, evoluir e, finalmente, retirar a solução de uso com segurança.

## Conexões

- [Aula 05 — Iniciando com TCO](./aula-05-iniciando-com-tco.md)
- [Aula 04 — Princípios para Arquitetar uma Solução](./aula-04-principios-para-arquitetar-uma-solucao.md)
- [Tema 01 — Disponibilidade](../tema-01-solution-enterprise/aula-05-disponibilidade.md)
- [Tema 01 — Observabilidade](../tema-01-solution-enterprise/aula-09-observabilidade.md)
