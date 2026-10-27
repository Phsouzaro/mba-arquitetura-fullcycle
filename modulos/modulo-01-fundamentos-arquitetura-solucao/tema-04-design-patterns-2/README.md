# Tema 04 — Design Pattern (2)

**Módulo:** [01 — Fundamentos de Arquitetura de Solução](../README.md)  
**Situação:** Em andamento

## Aulas documentadas

| Aula | Título | Link |
| --- | --- | --- |
| 01 | Configuration | [Ler documentação](./aula-01-configuration.md) |
| 02 | Secret Management | [Ler documentação](./aula-02-secret-management.md) |
| 03 | Circuit Breaker | [Ler documentação](./aula-03-circuit-breaker.md) |
| 04 | Sequencing | [Ler documentação](./aula-04-sequencing.md) |
| 05 | API Gateway | [Ler documentação](./aula-05-api-gateway.md) |
| 06 | Arquitetura Baseada em Eventos | [Ler documentação](./aula-06-arquitetura-baseada-em-eventos.md) |
| 07 | Publish/Subscribe (Pub/Sub) | [Ler documentação](./aula-07-pub-sub.md) |
| 08 | Sidecar | [Ler documentação](./aula-08-sidecar.md) |
| 09 | Service Mesh | [Ler documentação](./aula-09-service-mesh.md) |

## Aprendizados registrados

- Configuration permite atualizar parâmetros operacionais em runtime quando os componentes suportam recarga segura.
- Externalizar configuração não significa automaticamente permitir refresh dinâmico.
- Mudanças exigem validação, autorização, auditoria, propagação e tratamento especial para credenciais.
- Secret Management protege e governa credenciais por meio de cofre, identidade de workload, menor privilégio, rotação e auditoria.
- Circuit Breaker limita falhas em cascata com estados fechado, aberto e meio aberto, protegendo o chamador de dependências degradadas.
- Sequencing coordena emissão de identificadores quando necessário, mas deve ser comparado a sequences de banco, UUIDs e geradores distribuídos conforme os requisitos.
- API Gateway centraliza roteamento e políticas na borda, incluindo autenticação, rastreabilidade e controle de tráfego, sem substituir a autorização de domínio.
- Arquitetura baseada em eventos desacopla produtores e consumidores, com notificações, transferência de estado, Event Sourcing, coreografia, orquestração e Sagas.
- Pub/Sub distribui eventos a consumidores independentes via tópicos, com atenção a consumer groups, particionamento, idempotência e garantias de entrega.
- Sidecar extrai capacidades transversais para componentes adjacentes à aplicação, incluindo logs, mTLS, controle de tráfego e configuração.
- Service Mesh coordena políticas de comunicação, segurança e observabilidade entre serviços por meio de data plane e control plane.

As próximas aulas serão documentadas conforme os resumos forem compartilhados.
