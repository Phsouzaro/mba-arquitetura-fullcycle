# Aula 01 — Design Patterns: Visão Geral

**Módulo:** 01 — Fundamentos de Arquitetura de Solução  
**Tema:** 03 — Design Patterns  
**Origem:** Resumo do estudante, com exemplos e complementos autorais identificados.

## Objetivo de aprendizagem

Reconhecer **design patterns** como soluções nomeadas e recorrentes para problemas de projeto, compreender seu valor como vocabulário compartilhado e avaliar sua adoção por contexto, benefícios e trade-offs.

## 1. O que são design patterns?

**Design patterns** são descrições reutilizáveis de soluções para problemas que se repetem em determinados contextos de desenvolvimento de software. Não são trechos de código prontos, bibliotecas nem regras universais.

O nome do padrão ajuda a comunicar **intenção, estrutura, consequências e condições de uso** sem redescrever a ideia inteira a cada conversa.

> Conhecer um pattern é conhecer uma alternativa e suas consequências — não uma obrigação de aplicá-lo.

## 2. Por que começar com uma visão panorâmica?

Antes de aprofundar implementações, vale aprender a reconhecer famílias de problemas e opções existentes. Isso amplia o repertório para:

- Identificar problemas semelhantes aos já resolvidos em outros sistemas;
- Discutir decisões com linguagem técnica compartilhada;
- Comparar alternativas antes de implementar;
- Reconhecer custos e limites dos padrões;
- Evitar soluções improvisadas quando existe uma abordagem bem compreendida.

O panorama não substitui estudo de implementação, testes e avaliação no contexto real.

## 3. Pattern não é receita fixa

A adequação de um padrão depende de fatores como **domínio, escala, restrições, equipe, manutenção, operação e evolução esperada**.

Aplicar um pattern apenas porque é conhecido pode introduzir abstrações e indireções desnecessárias. Por outro lado, deixar de usá-lo em um problema recorrente pode gerar acoplamento e duplicação de decisões.

### Perguntas antes de escolher

1. Qual problema concreto precisamos resolver?
2. O problema realmente se repete ou exige flexibilidade?
3. Que benefício mensurável ou observável esperamos?
4. Que complexidade adicional o padrão introduz?
5. Existe uma solução mais simples suficiente?
6. Como saberemos se a decisão continua adequada?

## 4. Vocabulário técnico compartilhado

Nomes como **Strategy**, **Adapter** e **Observer** ajudam equipes a discutir ideias conhecidas. Entretanto, usar o nome de um pattern não dispensa explicar **como ele foi aplicado** e quais decisões específicas foram tomadas.

Exemplo: dizer “vamos usar Strategy” comunica a intenção de trocar comportamentos por composição, mas não responde sozinho como instâncias serão selecionadas, testadas ou configuradas.

## 5. Panorama de categorias — complemento autoral

Na classificação clássica dos padrões GoF (*Gang of Four*), há três grandes famílias:

| Categoria | Preocupação principal | Exemplos |
| --- | --- | --- |
| **Criacionais** | Como objetos são criados | Factory Method, Abstract Factory, Builder |
| **Estruturais** | Como objetos e estruturas se compõem | Adapter, Decorator, Facade |
| **Comportamentais** | Como responsabilidades e comportamentos interagem | Strategy, Observer, Command |

Essas categorias se referem principalmente a **padrões de design orientados a objetos**. Existem também padrões em outros níveis, como padrões arquiteturais e de integração, que não devem ser confundidos automaticamente com a classificação GoF.

## 6. Exemplo em Java: Strategy — complemento autoral

**Problema:** a plataforma de ingressos precisa calcular taxas de serviço de maneiras diferentes conforme o tipo de evento. Uma sequência crescente de condicionais pode dificultar a extensão e os testes.

Uma alternativa é representar a regra variável por uma interface:

```java
import java.math.BigDecimal;

interface PoliticaTaxa {
    BigDecimal calcular(BigDecimal valor);
}

final class TaxaFixa implements PoliticaTaxa {
    public BigDecimal calcular(BigDecimal valor) {
        return new BigDecimal("5.00");
    }
}

final class TaxaPercentual implements PoliticaTaxa {
    public BigDecimal calcular(BigDecimal valor) {
        return valor.multiply(new BigDecimal("0.10"));
    }
}

final class CalculadoraPreco {
    private final PoliticaTaxa politica;

    CalculadoraPreco(PoliticaTaxa politica) {
        this.politica = politica;
    }

    BigDecimal total(BigDecimal valor) {
        return valor.add(politica.calcular(valor));
    }
}
```

**Benefício:** diferentes políticas podem ser testadas e substituídas sem alterar a classe que calcula o total.

**Trade-off:** mais tipos, indireção e decisões de configuração. Para uma regra única e estável, essa abstração pode não se justificar.

**Nota:** valores e regras são ilustrativos; em sistemas financeiros reais, regras de arredondamento e precisão precisam ser definidas.

## 7. Repertório arquitetural e decisão

Ao crescer, sistemas apresentam desafios de separação de responsabilidades, comunicação, escalabilidade, consistência e operação.

Nem todo desafio exige um design pattern GoF. Em alguns casos, a decisão envolve **padrões arquiteturais** (por exemplo, arquitetura em camadas) ou **padrões de integração** (por exemplo, Publish–Subscribe). É importante identificar **em que nível o problema ocorre** antes de escolher a solução.

### Linha cinzenta entre arquitetura de solução e arquitetura de software

A arquitetura de solução considera a organização ampla da solução e sua aderência ao negócio; a arquitetura de software costuma aprofundar estruturas internas, componentes e código.

Essas responsabilidades podem se sobrepor. Um padrão que parece local pode afetar desempenho, contratos, extensibilidade e decisões mais amplas. O critério é **impacto e contexto**, não uma fronteira rígida entre cargos.

## 8. Comparando trade-offs — complemento autoral

| Alternativa | Possível benefício | Possível custo |
| --- | --- | --- |
| Strategy | Troca de regras sem alterar o consumidor | Interfaces e objetos adicionais |
| Adapter | Isola incompatibilidades de interface | Camada extra de tradução |
| Observer | Desacopla emissores de observadores | Fluxo de execução menos explícito |
| Solução direta, sem pattern formal | Menor complexidade inicial | Pode ficar rígida quando a variação cresce |

A melhor opção não é a mais sofisticada: é a que resolve o problema com **complexidade proporcional**.

## 9. Relação com aulas anteriores

- [Princípios para Arquitetar uma Solução](../tema-02-solution-architecture/aula-04-principios-para-arquitetar-uma-solucao.md): patterns ajudam a aplicar princípios, mas não substituem análise.
- [Lei de Conway](../tema-02-solution-architecture/aula-13-lei-de-conway.md): escolhas de organização e comunicação também influenciam a arquitetura.
- [Risco vs. Documentação](../tema-02-solution-architecture/aula-16-risco-vs-documentacao.md): formalizar a decisão sobre um pattern deve ser proporcional ao risco.

## 10. Checklist

- [ ] Identifiquei o problema antes de selecionar o pattern?
- [ ] Entendo o propósito e as consequências da alternativa?
- [ ] Sei distinguir pattern de biblioteca ou implementação pronta?
- [ ] Avaliei uma solução mais simples?
- [ ] Considerei testabilidade, manutenção e evolução?
- [ ] Expliquei por que o padrão é adequado neste contexto?

## Perguntas de revisão

1. O que torna uma solução um design pattern?
2. Por que patterns são úteis como vocabulário compartilhado?
3. Qual é o risco de aplicar um padrão sem necessidade real?
4. Quais são as três categorias clássicas dos padrões GoF?
5. Que benefício e que custo o Strategy traz ao exemplo de taxas?
6. Como diferenciar um design pattern de um padrão arquitetural?
7. Por que o mesmo pattern pode interessar à arquitetura de solução e à arquitetura de software?

## Síntese

> **Design patterns são ferramentas de repertório e comunicação.** Seu valor está em reconhecer problemas recorrentes e selecionar soluções conhecidas com consciência dos benefícios, limites e trade-offs.
