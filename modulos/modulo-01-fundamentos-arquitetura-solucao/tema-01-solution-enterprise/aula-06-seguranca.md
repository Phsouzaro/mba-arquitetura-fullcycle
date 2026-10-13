# Aula 06 — Segurança

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** Solution Enterprise  
**Status:** Documentada

## Objetivo

Compreender segurança como característica estrutural de sistemas enterprise, envolvendo dados, operação, identidade, permissões, redes e governança.

## Segurança em sistemas enterprise

A proteção precisa abranger usuários, colaboradores, executivos, terceiros e sistemas integrados. Senhas e criptografia são importantes, mas não substituem processos organizacionais, responsabilidades e controles operacionais.

## Ameaças internas e externas

Riscos podem vir de agentes externos ou de acessos internos excessivos, erros humanos e integrações mal configuradas. A arquitetura deve estabelecer quem pode acessar cada recurso, em quais condições e com qual rastreabilidade.

## Autenticação e autorização

- **Autenticação:** confirmar a identidade de quem solicita acesso.
- **Autorização:** verificar quais ações e recursos essa identidade pode utilizar.

Uma pessoa autenticada não deve receber automaticamente permissão para todas as operações.

## Três categorias de fatores de autenticação

| Categoria | Exemplo |
| --- | --- |
| Algo que você sabe | Senha ou PIN |
| Algo que você tem | Chave física ou aplicativo autenticador |
| Algo que você é | Impressão digital ou reconhecimento facial |

A autenticação multifator combina categorias diferentes. Duas senhas, por exemplo, não equivalem a dois fatores distintos.

## Controles proporcionais ao risco

Operações críticas podem requerer autenticação adicional, revisão de permissões, segregação de funções, aprovações independentes e registros de auditoria. A escolha dos controles deve considerar o impacto da ação e o contexto do negócio.

## Governança e segurança

A governança conecta pessoas, processos e tecnologia. Políticas de acesso, revisão periódica de privilégios, responsabilidades claras e resposta a incidentes ajudam a sustentar controles técnicos.

## Exemplo complementar — pagamento corporativo

Em um cenário hipotético, um funcionário solicita um pagamento de alto valor. O sistema verifica sua permissão para solicitar, exige aprovação de uma segunda pessoa autorizada e registra a operação para auditoria. O desenho evita depender apenas da autenticação inicial.

> Exemplo autoral de aplicação dos conceitos, não exercício oficial do curso.

## Princípios complementares

- **Menor privilégio:** conceder somente os acessos necessários.
- **Defesa em profundidade:** utilizar controles complementares.
- **Segurança por padrão:** restringir acessos até que sejam autorizados.
- **Rastreabilidade:** registrar ações relevantes de modo adequado à operação.

## Perguntas de revisão

1. Por que criptografia e senha não resolvem sozinhas a segurança enterprise?
2. Qual a diferença entre autenticação e autorização?
3. Por que duas senhas não constituem autenticação multifator?
4. Como a governança contribui para reduzir riscos internos?
5. Quando é justificável exigir uma verificação adicional?

## Síntese

> Segurança enterprise depende da integração entre controles técnicos, processos e governança, com proteção proporcional à criticidade de cada operação.

## Conexões

- [Aula 03 — Ecossistema Enterprise](./aula-03-ecossistema-enterprise.md)
- [Aula 05 — Disponibilidade](./aula-05-disponibilidade.md)
