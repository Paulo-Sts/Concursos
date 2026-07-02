# Anotações – Regras de Associação

## 1. Conceito de Regras de Associação

- **Regras de Associação** são uma técnica de **aprendizado de máquina não supervisionado**.
- **Objetivo:** descobrir **relações frequentes** entre itens em grandes bases de dados.
- **Aplicação clássica:** análise de cesta de compras (*market basket analysis*) – identificar produtos que são frequentemente comprados juntos.

> ### 1.1 Exemplo clássico (Walmart, anos 90)
> - Base de dados de vendas: cada linha representa uma venda.
> - O algoritmo identifica padrões como: "quem compra **fraldas** também compra **cerveja**" (regra de associação).

## 2. Estrutura de uma Regra de Associação

- **Formato:** `A → B` (lê-se: "A implica B" ou "se A, então B").
- **A:** **antecedente** (o item/condição que precede).
- **B:** **consequente** (o item que é associado).
- **A e B** são subconjuntos **disjuntos** (não compartilham itens).

## 3. Métricas para Avaliação de Regras

| MÉTRICA | DESCRIÇÃO | FÓRMULA |
| --- | --- | --- |
| **Suporte (Support)** | Frequência com que a regra aparece no dataset. | `Suporte(A→B) = freq(A∪B) / N` |
| **Confiança (Confidence)** | Probabilidade de B ocorrer dado que A ocorreu. | `Confiança(A→B) = Suporte(A∪B) / Suporte(A)` |
| **Lift (Elevação)** | Mede se a ocorrência de A aumenta a probabilidade de B. | `Lift = Suporte(A∪B) / (Suporte(A) × Suporte(B))` |

> ### 3.1 Interpretação do Lift
> - **Lift > 1:** associação positiva – A e B ocorrem juntos com mais frequência do que o esperado.
> - **Lift = 1:** independência – A e B são independentes.
> - **Lift < 1:** associação negativa – A e B tendem a não ocorrer juntos.

## 4. Principais Algoritmos

| ALGORITMO | DESCRIÇÃO |
| --- | --- |
| **Apriori** | O mais clássico. Gera regras iterativamente, eliminando combinações com suporte abaixo de um limite mínimo. |
| **Eclat** | Utiliza uma estrutura baseada em conjuntos de transações (mais eficiente que Apriori em alguns casos). |
| **FP-Growth** | Constrói uma árvore de padrões frequentes (*Frequent Pattern Tree*) – mais rápido que Apriori. |
| **Partition** | Divide o dataset em partições para processamento paralelo. |

> ### 4.1 Apriori – lógica
> - Gera **itemsets** (combinações de itens) de tamanho 1, 2, 3, etc.
> - Mantém apenas aqueles com suporte ≥ suporte mínimo.
> - Combina itemsets frequentes para gerar os de tamanho superior.

## 5. Aplicações Típicas

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Análise de cesta de compras** | Identificar produtos frequentemente comprados juntos (ex.: pão e manteiga). |
| **Sistemas de recomendação** | Sugerir produtos com base em compras anteriores ("quem comprou X também comprou Y"). |
| **Segmentação de clientes** | Identificar padrões de consumo por perfil. |
| **Bioinformática** | Descobrir associações entre genes ou proteínas. |
| **Saúde pública** | Identificar correlações entre sintomas e doenças. |

## 6. Regras de Associação vs. Árvore de Decisão

| REGRAS DE ASSOCIAÇÃO | ÁRVORE DE DECISÃO |
| --- | --- |
| Não supervisionado | Supervisionado |
| Descobre **muitas regras** com diferentes conclusões. | Constrói uma **única estrutura** hierárquica de decisões. |
| Regras do tipo `A → B`. | Regras do tipo "se condição, então classe". |

> ### 6.1 Atenção (pegadinha)
> - A afirmação "os algoritmos de regras de associação constroem regras com apenas uma única conclusão" está **errada**.
> - Regras de associação **geram muitas regras**, cada uma com uma conclusão diferente.

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/CEBRASPE/ANTT/2024 – Especialista)

**Item:** "Os algoritmos de regras de associação constroem regras com apenas uma única conclusão, ao contrário dos algoritmos de árvore de decisão, que tentam localizar muitas regras."

**Gabarito: Errado (E).**

**Comentário:** É o **contrário**: regras de associação geram **muitas regras**; árvores de decisão geram uma estrutura hierárquica.

### 7.2 (INSTITUTO AOCP/MJ/2020 – Cientista de Dados)

**Item:** "Nome do processo de extração dessas regras de um determinado conjunto de dados."

**Gabarito: e) Mineração de regras de associação (ARM).**

### 7.3 (CESPE/CEBRASPE/TCE-RJ/2021 – Analista)

**Item:** "As regras de associação adotadas em mineração de dados buscam padrões frequentes entre conjuntos de dados e podem ser úteis para caracterizar, por exemplo, hábitos de consumo de clientes."

**Gabarito: Certo (C).**

**Comentário:** A descrição está correta – regras de associação são usadas para identificar padrões de consumo.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/ANTT/2024) | E |
| 02 (INSTITUTO AOCP/2020) | e |
| 03 (CESPE/TCE-RJ/2021) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Regras de Associação** | Técnica não supervisionada para descobrir relações frequentes entre itens. |
| **Formato** | `A → B` (antecedente → consequente). |
| **Suporte** | Frequência da regra no dataset. |
| **Confiança** | Probabilidade de B dado A. |
| **Lift** | Mede se A aumenta a probabilidade de B (lift > 1 = associação positiva). |
| **Algoritmo mais famoso** | Apriori. |
| **Aplicação clássica** | Análise de cesta de compras. |
| **Diferença para Árvore de Decisão** | Regras de associação geram muitas regras; árvore de decisão é uma estrutura hierárquica. |

---

*Material complementar à aula "Regras de Associação" (professor Vitor Kessler/Gran Concursos).*