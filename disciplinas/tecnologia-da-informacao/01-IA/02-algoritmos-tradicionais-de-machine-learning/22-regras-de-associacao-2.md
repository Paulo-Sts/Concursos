# Anotações – Regras de Associação II (Métricas e Algoritmo Apriori)

## 1. Métricas para Avaliação de Regras de Associação

### 1.1 Suporte (Support)

- **Definição:** proporção de transações no dataset que contêm **todos os itens** da regra (antecedente + consequente).
- **Fórmula:**
```
Suporte(A → B) = |A ∪ B| / |D|
```
Onde:
- `|A ∪ B|` = número de transações que contêm A e B juntos.
- `|D|` = número total de transações no dataset.

> ### 1.1.1 Exemplo
> - 4 vendas: A, AB, ABC, AB.
> - Regra `A → B`: A∪B aparece em 3 transações. Suporte = 3/4 = **75%**.

### 1.2 Confiança (Confidence)

- **Definição:** proporção de vezes que o consequente aparece **dado que o antecedente** aparece.
- **Fórmula:**
```
Confiança(A → B) = Suporte(A ∪ B) / Suporte(A)
```

> ### 1.2.1 Exemplo
> - A aparece 4 vezes, B aparece 3 vezes (sempre com A).
> - Confiança = 3/4 = **75%**.

### 1.3 Lift (Elevação)

- **Definição:** mede se a ocorrência de A **aumenta** a probabilidade de B.
- **Fórmula:**
```
Lift(A → B) = Confiança(A → B) / Suporte(B)
```

| VALOR DO LIFT | INTERPRETAÇÃO |
| --- | --- |
| **> 1** | Correlação positiva – A aumenta a probabilidade de B. |
| **= 1** | A e B são independentes. |
| **< 1** | Correlação negativa – A diminui a probabilidade de B. |

## 2. Algoritmo Apriori

### 2.1 Conceito

- O **Apriori** é o algoritmo mais famoso para extração de regras de associação.
- Utiliza **limiares de suporte** e **confiança** para selecionar regras relevantes.

### 2.2 Funcionamento (passo a passo)

#### Fase 1 – Geração de Itemsets Frequentes (busca em largura)

1. **Itemsets de tamanho 1:** conta a frequência de cada item individual.
2. **Filtro:** mantém apenas os itens com suporte ≥ suporte mínimo.
3. **Itemsets de tamanho 2:** combina os itens frequentes em pares.
4. **Filtro:** mantém apenas os pares com suporte ≥ suporte mínimo.
5. O processo se repete para itemsets de tamanho 3, 4, etc.

**Regra:** um itemset só pode ser frequente se **todos os seus subconjuntos** também forem frequentes (propriedade *Apriori*).

#### Fase 2 – Geração de Regras de Associação

1. Para cada itemset frequente, gera-se todas as regras possíveis (ex.: `A→C`, `C→A`).
2. Calcula-se a confiança de cada regra.
3. Mantêm-se apenas as regras com confiança ≥ confiança mínima.

### 2.3 Exemplo prático

**Dataset (8 transações):**
```
T1: A, B, C
T2: A, C
T3: A, D
T4: B, C
T5: A, C, D
T6: B, D
T7: C, D
T8: A, B, C
```

**Suporte mínimo = 3/8 (aparecer em pelo menos 3 transações)**

**Itemset de tamanho 1 (frequência):**
- A: 5 (passa)
- B: 4 (passa)
- C: 6 (passa)
- D: 4 (passa)

**Itemset de tamanho 2 (frequência):**
- A,B: 2 (eliminado)
- A,C: 4 (passa)
- A,D: 2 (eliminado)
- B,C: 3 (passa)
- B,D: 2 (eliminado)
- C,D: 3 (passa)

**Itemsets selecionados:** {A,C}, {B,C}, {C,D}

**Geração de regras (confiança mínima = 70%):**
- `A → C`: Suporte(A,C)/Suporte(A) = 4/5 = 80% **(passa)**
- `C → A`: Suporte(A,C)/Suporte(C) = 4/6 = 67% **(eliminado)**
- `B → C`: 3/4 = 75% (passa)
- `C → B`: 3/6 = 50% (eliminado)

## 3. Propriedade Apriori

- **Princípio:** se um itemset é **infrequente**, todos os seus supersets também serão infrequentes.
- Permite **podar** o espaço de busca, tornando o algoritmo eficiente.

## 4. Questões de Concurso Comentadas

### 4.1 (CESPE/CTI/2024 – Tecnologista)

**Item:** "O objetivo das regras de associação é encontrar todos os conjuntos de itens que possuem confiança mínima com máximo de dados observados."

**Gabarito: Errado (E).**

**Comentário:** Regras de associação usam **suporte** e **confiança**; a confiança não depende da quantidade total de dados observados.

### 4.2 (CESGRANRIO/PETROBRAS/2018 – Analista)

**Item:** Qual regra possui confiança mínima de 80% e suporte mínimo de 30%?

**Gabarito: b) café, pão → manteiga.**

**Comentário:** A regra aparece em 3 das 10 transações (suporte 30%) e, quando café e pão aparecem, manteiga também aparece (confiança 100%).

### 4.3 (FGV/TJDFT/2022 – Analista)

**Item:** "Se um cliente compra Cacau, a probabilidade de ele comprar Chia é de 50%." – Suporte = 50%, Confiança = 66,7%.

**Gabarito: c) regra de associação.**

**Comentário:** A descrição corresponde exatamente ao conceito de regra de associação (`Cacau → Chia`).

### 4.4 (CESPE/TCE-RJ/2021 – Analista)

**Item:** "O fator de suporte e o fator de confiança são dois índices utilizados para definir o grau de certeza de uma regra de associação."

**Gabarito: Certo (C).**

### 4.5 (FGV/SEMSA/2022 – Analista)

**Item:** "Algoritmo usado na extração de regras de associação."

**Gabarito: a) Apriori.**

### 4.6 (CESPE/CTI/2024 – Tecnologista)

**Item:** "O algoritmo Apriori emprega busca em profundidade e gera conjuntos de itens candidatos de k elementos a partir de conjuntos de itens de k–1 elementos."

**Gabarito: Certo (C).**

**Comentário:** A descrição está correta – Apriori gera itemsets de tamanho k a partir de itemsets de tamanho k-1.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/CTI/2024) | E |
| 02 (CESGRANRIO/2018) | b |
| 03 (FGV/TJDFT/2022) | c |
| 04 (CESPE/TCE-RJ/2021) | C |
| 05 (FGV/SEMSA/2022) | a |
| 06 (CESPE/CTI/2024) | C |

---

## Síntese para Revisão Rápida

| MÉTRICA | FÓRMULA | INTERPRETAÇÃO |
| --- | --- | --- |
| **Suporte** | `freq(A∪B)/N` | Frequência da regra no dataset. |
| **Confiança** | `Suporte(A∪B)/Suporte(A)` | Probabilidade de B dado A. |
| **Lift** | `Confiança/Suporte(B)` | > 1 = correlação positiva; = 1 = independentes; < 1 = correlação negativa. |
| **Apriori** | Algoritmo | Gera itemsets frequentes (suporte) → regras (confiança). |

---

*Material complementar à aula "Regras de Associação II" (professor Vitor Kessler/Gran Concursos).*