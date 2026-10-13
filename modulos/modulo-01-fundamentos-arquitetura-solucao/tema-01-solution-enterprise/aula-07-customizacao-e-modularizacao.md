# Aula 07 — Customização e Modularização

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** Solution Enterprise  
**Origem:** Resumo do estudante, reorganizado com exemplos autorais.

## Objetivo
Entender como equilibrar padronização, customização e modularização para preservar diferenciais competitivos.

## Customização e vantagem competitiva
Customizar é adaptar o software às particularidades da organização. Certos processos representam vantagem competitiva; obrigar a empresa a abandoná-los para seguir um produto padrão pode prejudicar sua estratégia. Outros processos podem ser padronizados para reduzir custos.

## ERP, CRM e análise de aderência
ERPs e CRMs aceleram a implantação, mas podem não atender todos os processos. Uma análise de aderência identifica o que já funciona e o que exige configuração, integração, extensão ou mudança de processo.

## Modularização
Separar responsabilidades por áreas ou domínios permite que vendas, operações e finanças evoluam suas regras sem perder a integração corporativa. Modularização **não exige microsserviços**: um monólito modular pode atender bem ao contexto.

## Custos e trade-offs

| Abordagem | Benefício | Limitação |
| --- | --- | --- |
| Produto padrão | Menor esforço inicial | Menos flexibilidade |
| Configuração nativa | Customização suportada | Limites da plataforma |
| Extensão por API | Preserva o núcleo | Integrações e manutenção |
| Alteração profunda | Grande liberdade | Custo e dificuldade de atualização |

A decisão deve considerar custo total de propriedade, e não apenas aquisição.

## SaaS e BI
SaaS combina processos-base compartilhados com personalização por configurações, automações, integrações e painéis. BI integrado ao CRM permite adaptar indicadores e análises sem necessariamente modificar o núcleo do produto. A aproximação entre Salesforce e Tableau ilustra esse movimento. A atualização em tempo real depende da integração e da arquitetura adotadas.

## No-code e low-code
Essas plataformas permitem que áreas de negócio resolvam necessidades locais sem depender exclusivamente de longas filas de desenvolvimento. O ganho de agilidade precisa ser acompanhado por governança: responsáveis definidos, permissões, qualidade de dados, integração e manutenção.

## Exemplo complementar
Uma unidade de negócio cria uma aplicação interna de solicitação de materiais. A interface e os fluxos locais são adaptados, enquanto compras, identidade e auditoria permanecem integrados aos serviços corporativos.

> Exemplo autoral, não atividade oficial do curso.

## Checklist
- [ ] O processo é diferencial competitivo?
- [ ] A configuração padrão atende à necessidade?
- [ ] É possível estender por APIs?
- [ ] Os módulos possuem responsabilidades claras?
- [ ] Custos de atualização e manutenção foram avaliados?
- [ ] Soluções locais têm responsáveis e governança?

## Perguntas de revisão
1. Quando a padronização pode prejudicar o negócio?
2. Por que modularização não implica microsserviços?
3. Como BI permite customização informacional?
4. Quais riscos surgem com aplicações low-code sem governança?

## Síntese
> Padronizar o que é comum e adaptar o que diferencia o negócio, com modularização e governança.

## Conexões
- [Aula 02 — Software Enterprise](./aula-02-software-enterprise.md)
- [Aula 03 — Ecossistema Enterprise](./aula-03-ecossistema-enterprise.md)
- [Aula 06 — Segurança](./aula-06-seguranca.md)
