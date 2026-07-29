# Anotações – Classificação de Modelos (Matriz de Confusão e Métricas)

## 1. Matriz de Confusão

### 1.1 Conceito

- A **matriz de confusão** é uma ferramenta que estabelece a relação entre as **previsões realizadas pelo modelo** e os **valores reais** do conjunto de testes.
- Permite avaliar o desempenho de um modelo de **classificação** com base na frequência de acertos e erros.
- É a base para o cálculo da maioria das métricas de avaliação de classificadores.

### 1.2 Estrutura da Matriz de Confusão (classificação binária)

| | **REAL POSITIVO** | **REAL NEGATIVO** |
| --- | --- | --- |
| **PREVISTO POSITIVO** | Verdadeiro Positivo (VP) | Falso Positivo (FP) |
| **PREVISTO NEGATIVO** | Falso Negativo (FN) | Verdadeiro Negativo (VN) |

### 1.3 Definições

| TERMO | SIGNIFICADO |
| --- | --- |
| **Verdadeiro Positivo (VP)** | O modelo previu positivo e o valor real é positivo (acerto). |
| **Verdadeiro Negativo (VN)** | O modelo previu negativo e o valor real é negativo (acerto). |
| **Falso Positivo (FP)** | O modelo previu positivo, mas o valor real é negativo (erro tipo I). |
| **Falso Negativo (FN)** | O modelo previu negativo, mas o valor real é positivo (erro tipo II). |

> ### 1.3.1 Exemplo prático (detecção de fraudes)
> - **Classe positiva:** fraude.
> - **Classe negativa:** normal.
> - **FP:** o modelo alerta fraude, mas a transação é normal (falso alarme).
> - **FN:** o modelo não alerta fraude, mas a transação é fraudulenta (erro crítico).

## 2. Métricas de Avaliação

### 2.1 Acurácia (Accuracy)

- Mede o **total de instâncias classificadas corretamente** em relação ao total de instâncias.

```
Acurácia = (VP + VN) / (VP + VN + FP + FN)
```

> ### 2.1.1 Exemplo
> - Conjunto de teste com 1.000 dados.
> - VP = 490, VN = 450, FP = 50, FN = 10.
> - Acurácia = (490 + 450) / 1000 = 940 / 1000 = **94%**.

### 2.2 Precisão (Precision)

- Mede a **proporção de instâncias classificadas como positivas que são realmente positivas**.
- Quanto maior, **menos falsos positivos** o modelo terá.

```
Precisão = VP / (VP + FP)
```

> ### 2.2.1 Exemplo
> - VP = 80, FP = 20.
> - Precisão = 80 / (80 + 20) = 80 / 100 = **80%**.

### 2.3 Sensibilidade (Recall / Revocação)

- Mede a **proporção de instâncias positivas que foram corretamente identificadas**.
- Quanto maior, **menos falsos negativos** o modelo terá.

```
Sensibilidade (Recall) = VP / (VP + FN)
```

### 2.4 F1-Score

- **Média harmônica** entre precisão e sensibilidade.
- Útil quando se deseja equilibrar as duas métricas.

```
F1 = 2 × (Precisão × Recall) / (Precisão + Recall)
```

### 2.5 Especificidade

- Mede a **proporção de instâncias negativas corretamente identificadas**.

```
Especificidade = VN / (VN + FP)
```

## 3. Interpretação das Métricas

| MÉTRICA | FOCO | PENALIZA |
| --- | --- | --- |
| **Acurácia** | Acertos gerais | Nenhum (pode ser enganosa em classes desbalanceadas) |
| **Precisão** | Evitar falsos positivos | FP |
| **Recall (Sensibilidade)** | Evitar falsos negativos | FN |
| **F1-Score** | Equilíbrio entre precisão e recall | Ambos FP e FN |
| **Especificidade** | Evitar falsos positivos (foco na classe negativa) | FP |

## 4. Resumo – Métricas (fórmulas)

| MÉTRICA | FÓRMULA |
| --- | --- |
| Acurácia | `(VP + VN) / (VP + VN + FP + FN)` |
| Precisão | `VP / (VP + FP)` |
| Recall (Sensibilidade) | `VP / (VP + FN)` |
| F1-Score | `2 × (Precisão × Recall) / (Precisão + Recall)` |
| Especificidade | `VN / (VN + FP)` |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador)

**Item:** "A maioria das métricas utilizadas para avaliação da qualidade de um classificador em aprendizado de máquina é obtida por meio da matriz de confusão."

**Gabarito: Certo (C).**

### 5.2 (CESPE/CEBRASPE/2023/SERPRO – Analista)

**Item:** "A matriz de confusão permite avaliar o desempenho de um modelo de classificação a partir da frequência de erros e acertos."

**Gabarito: Certo (C).**

### 5.3 (CESPE/CEBRASPE/2025/EMBRAPA – Matriz de confusão com cálculo)

**Matriz:**

| | Real Positivo | Real Negativo |
| --- | --- | --- |
| Predito Positivo | VP = 80 | FP = 20 |
| Predito Negativo | FN = 10 | VN = 90 |

**Cálculo da acurácia:**

```
Acurácia = (VP + VN) / Total = (80 + 90) / (80 + 90 + 20 + 10) = 170 / 200 = 85%
```

**Gabarito: Certo (C).**

### 5.4 (CESPE/CEBRASPE/2025/EMBRAPA – Definição de acurácia)

**Item:** "A acurácia de um modelo classificador mede a taxa de previsões corretas, em relação ao total de previsões positivas."

**Gabarito: Errado (E).**

**Comentário:** A acurácia mede as previsões corretas em relação ao **total de previsões** (não apenas as positivas).

### 5.5 (CESGRANRIO/2024/IPEA – Cálculo de acurácia)

**Matriz (linhas = resposta correta, colunas = previsão):**

| | Opinião | Não Opinião |
| --- | --- | --- |
| Opinião | 440 | 60 |
| Não Opinião | 20 | 480 |

- Diagonal principal (acertos): 440 + 480 = 920.
- Total: 1000.
- Acurácia: 920 / 1000 = **92%**.

**Gabarito: e) 92%.**

### 5.6 (FGV/2024/PREFEITURA DE CUIABÁ – Matriz de confusão multiclasse)

**Afirmativas:**

- I – A soma de todos os elementos da matriz é igual a `n` (total de objetos testados). **(V)**
- II – A taxa de acerto (acurácia) é a razão entre a soma da diagonal principal e a soma de todos os elementos. **(V)**
- III – A precisão para a classe `i` é a razão entre o elemento da diagonal na linha `i` e a soma de todos os elementos da coluna `i`. **(F)** – depende da organização da matriz (pode ser recall dependendo do arranjo).

**Gabarito: c) I e II, apenas.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/EMBRAPA/2025) | C |
| 02 (CESPE/SERPRO/2023) | C |
| 03 (CESPE/EMBRAPA/2025 – cálculo) | C |
| 04 (CESPE/EMBRAPA/2025 – definição) | E |
| 05 (CESGRANRIO/IPEA/2024) | e |
| 06 (FGV/CUIABÁ/2024) | c |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Matriz de Confusão** | Tabela que compara previsões com valores reais. |
| **VP** | Acertou positivo. |
| **VN** | Acertou negativo. |
| **FP** | Errou positivo (falso alarme). |
| **FN** | Errou negativo (falha crítica). |
| **Acurácia** | `(VP+VN)/Total` |
| **Precisão** | `VP/(VP+FP)` |
| **Recall** | `VP/(VP+FN)` |
| **F1-Score** | Média harmônica entre precisão e recall. |

---

*Material complementar à aula "Classificação de Modelos" (professor Vitor Kessler/Gran Concursos).*