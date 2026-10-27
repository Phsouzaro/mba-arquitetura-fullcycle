# Tema 03 — Design Patterns

**Módulo:** [01 — Fundamentos de Arquitetura de Solução](../README.md)  
**Situação:** Em andamento

## Aulas documentadas

| Aula | Título | Link |
| --- | --- | --- |
| 01 | Design Patterns: Visão Geral | [Ler documentação](./aula-01-design-patterns-visao-geral.md) |
| 02 | N-Tier e N-Layered Architecture | [Ler documentação](./aula-02-n-tier-e-n-layered-architecture.md) |
| 03 | Multi-Tenant Architecture | [Ler documentação](./aula-03-multi-tenant-architecture.md) |
| 04 | Stateless vs. Stateful Architecture | [Ler documentação](./aula-04-stateless-vs-stateful-architecture.md) |
| 05 | Serverless Architecture | [Ler documentação](./aula-05-serverless-architecture.md) |
| 06 | Microservices Architecture | [Ler documentação](./aula-06-microservices-architecture.md) |
| 07 | CQRS — Command Query Responsibility Segregation | [Ler documentação](./aula-07-cqrs.md) |
| 08 | Entendendo Cache | [Ler documentação](./aula-08-entendendo-cache.md) |
| 09 | Invalidando Cache | [Ler documentação](./aula-09-invalidando-cache.md) |

## Aprendizados registrados

- Design patterns são soluções nomeadas para problemas recorrentes, não receitas universais.
- Conhecer padrões amplia o repertório e o vocabulário compartilhado de engenharia.
- A escolha de um padrão deve considerar contexto, benefícios, custos e trade-offs.
- Design patterns, padrões arquiteturais e padrões de integração operam em níveis diferentes e podem se relacionar.
- Layers separam responsabilidades lógicas, enquanto tiers separam unidades de implantação; closed e open layering representam regras distintas de dependência.
- Multi-tenancy compartilha recursos entre organizações, exigindo identificação autorizada e segregação de dados por banco, tabela ou chave, inclusive em estratégias híbridas.
- Aplicações stateless externalizam sessões, arquivos e logs para que instâncias sejam substituíveis, favorecendo elasticidade.
- Serverless combina execução e serviços gerenciados sob demanda, com trade-offs de custo, cold start, observabilidade e dependência do provedor.
- Microserviços favorecem ownership e deploy independente por domínio, mas exigem resiliência distribuída, consistência, CI/CD e observabilidade.
- CQRS separa modelos e fluxos de escrita e leitura, podendo usar projeções e persistências distintas quando a complexidade se justifica.
- Cache-aside reaproveita leituras, reduz latência e carga na origem, exigindo política de expiração e invalidação.
- Invalidação por TTL, eviction por LRU/MRU/LFU e sincronização por write-through/write-back resolvem problemas distintos de cache.

As próximas aulas serão documentadas conforme os resumos forem compartilhados.
