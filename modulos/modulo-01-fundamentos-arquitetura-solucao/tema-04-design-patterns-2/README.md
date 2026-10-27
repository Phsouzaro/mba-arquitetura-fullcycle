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

## Aprendizados registrados

- Configuration permite atualizar parâmetros operacionais em runtime quando os componentes suportam recarga segura.
- Externalizar configuração não significa automaticamente permitir refresh dinâmico.
- Mudanças exigem validação, autorização, auditoria, propagação e tratamento especial para credenciais.
- Secret Management protege e governa credenciais por meio de cofre, identidade de workload, menor privilégio, rotação e auditoria.
- Circuit Breaker limita falhas em cascata com estados fechado, aberto e meio aberto, protegendo o chamador de dependências degradadas.
- Sequencing coordena emissão de identificadores quando necessário, mas deve ser comparado a sequences de banco, UUIDs e geradores distribuídos conforme os requisitos.
- API Gateway centraliza roteamento e políticas na borda, incluindo autenticação, rastreabilidade e controle de tráfego, sem substituir a autorização de domínio.

As próximas aulas serão documentadas conforme os resumos forem compartilhados.
