# Anotações – Classificação de Modelos II (Métricas e Curva ROC)

## 1. Métricas de Classificação (Revisão com Fórmulas)

| MÉTRICA | FÓRMULA | O QUE MEDE | QUANDO USAR |
| --- | --- | --- | --- |
| **Acurácia** | `(VP + VN) / Total` | Percentual de acertos gerais. | Classes balanceadas. |
| **Precisão** | `VP / (VP + FP)` | Proporção de positivos previstos que realmente são positivos. | Quando FP é crítico (ex.: spam). |
| **Sensibilidade (Recall)** | `VP / (VP + FN)` | Proporção de positivos reais que foram corretamente identificados. | Quando FN é crítico (ex.: fraudes, doenças). |
| **Especificidade** | `VN / (VN + FP)` | Proporção de negativos reais corretamente identificados. | Recall da classe negativa. |
| **F1-Score** | `2 × (P × R) / (P + R)` | Média harmônica entre precisão e recall. | Classes desbalanceadas. |

> ### 1.1 Interpretação
> - **Sensibilidade (Recall):** mede a capacidade do modelo de **encontrar todos os casos positivos reais**.
> - **Especificidade:** mede a capacidade do modelo de **encontrar todos os casos negativos reais**.
> - **Precisão:** mede a capacidade do modelo de **não gerar falsos alarmes** (FP).

## 2. Acurácia em Classes Desbalanceadas (pegadinha!)

- A acurácia pode ser **enganosa** quando as classes são desbalanceadas.
- **Exemplo:** 98% de dados da classe A, 2% da classe B.
  - Um modelo que classifica **tudo como A** tem acurácia de 98%, mas **não aprendeu a classe B**.
  - Nesse caso, a métrica mais adequada é a **sensibilidade (recall)**, que mede quantos casos positivos (classe B) foram detectados.

## 3. Curva ROC (Receiver Operating Characteristic)

### 3.1 Conceito

- Representação gráfica do desempenho de um **classificador binário** em **diferentes limiares de decisão**.
- **Eixos:**
  - **Eixo X:** Taxa de Falsos Positivos (TFP) = `FP / (FP + VN)`
  - **Eixo Y:** Taxa de Verdadeiros Positivos (TVP) = `VP / (VP + FN)` = Sensibilidade (Recall)

### 3.2 Interpretação da Curva ROC

| POSIÇÃO DA CURVA | SIGNIFICADO |
| --- | --- |
| **Canto superior esquerdo** | Melhor desempenho (TVP alta, TFP baixa). |
| **Diagonal (y = x)** | Desempenho aleatório (classificador não aprendeu nada). |
| **Canto inferior direito** | Pior desempenho. |

> ### 3.2.1 Classificador ideal
> - **TVP = 1** (todos os positivos detectados – sem FN).
> - **TFP = 0** (sem falsos positivos).
> - A curva ideal vai direto ao **canto superior esquerdo**.

### 3.3 AUC (Área Sob a Curva)

- **AUC** (*Area Under the Curve*) é a área sob a curva ROC.
- **Interpretação:**
  - AUC = 1 → classificador perfeito.
  - AUC = 0.5 → classificador aleatório (sem poder discriminatório).
  - AUC → 0 → classificador inverso (pior que aleatório).
- **Quanto mais próximo de 1, melhor** o desempenho do modelo.

> ### 3.3.1 AUC não é paramétrico!
> - O cálculo da AUC **não assume** que os dados seguem uma distribuição específica (ex.: normal).
> - É uma métrica **não paramétrica**.

## 4. Matriz de Confusão vs. Curva ROC

| MATRIZ DE CONFUSÃO | CURVA ROC |
| --- | --- |
| Refere-se a um **único limiar de decisão**. | Refere-se a **vários limiares** de decisão. |
| Permite calcular: acurácia, precisão, recall, F1-score. | Permite calcular a **AUC** (área sob a curva). |
| **Não** permite calcular AUC. | Permite calcular AUC. |

> ### 4.1 Observação
> - Com a matriz de confusão, é possível calcular o **F1-score**, mas **não a AUC**.
> - A AUC é calculada a partir da curva ROC, que requer múltiplos limiares.

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/SEFAZ-SE/2025)

**Item:** "Proporção de exemplos positivos corretamente identificados em relação ao total de exemplos positivos existentes."

**Gabarito: b) revocação (recall).**

**Comentário:** A definição corresponde exatamente ao recall: `VP / (VP + FN)`.

### 5.2 (CESPE/CEBRASPE/EMBRAPA/2025)

**Item:** "Para avaliar o desempenho de um classificador em problemas de classificação com classes significativamente desbalanceadas, a métrica acurácia é a mais adequada."

**Gabarito: Errado (E).**

**Comentário:** A acurácia é enganosa em classes desbalanceadas. A métrica mais adequada é a **sensibilidade (recall)**.

### 5.3 (CESGRANRIO/IPEA/2024)

**Item:** Precisão = 80%, Recall = 70%. Calcular o F1-Score.

```
F1 = 2 × (0,8 × 0,7) / (0,8 + 0,7) = 2 × 0,56 / 1,5 = 1,12 / 1,5 = 0,7466 → 74,66%
```

**Gabarito: d) 74%.**

### 5.4 (CESPE/CEBRASPE/EMBRAPA/2025)

**Item:** "A métrica sensibilidade, também chamada de recall, afere a capacidade do modelo de encontrar todos os incêndios reais."

**Gabarito: Certo (C).**

### 5.5 (FGV/CGE-PB/2024)

**Item:** "Métrica que avalia o equilíbrio entre precisão e sensibilidade (recall)."

**Gabarito: b) F1-score.**

### 5.6 (CESGRANRIO/BNDES/2024) – Matriz de confusão

**Matriz:** VP=45, FP=10, FN=5, VN=40.

```
Precisão = 45/(45+10) = 45/55 = 0,818 → 0,82
Recall = 45/(45+5) = 45/50 = 0,90
```

**Gabarito: b) 0,82 e 0,90.**

### 5.7 (FGV/RECEITA FEDERAL/2023)

**Itens:**

- I – Sensibilidade (recall) é a métrica mais importante para minimizar FN. **(V)**
- II – Precisão não é a mais importante nesse caso. **(F)**
- III – Minimizar FN geralmente aumenta FP. **(V)**
- IV – Treinamento mais longo pode causar overfitting. **(F)**

**Gabarito: a) I e III, apenas.**

### 5.8 (FGV/CÂMARA DOS DEPUTADOS/2023)

**Item:** VP=80, FN=20 → Recall = 80/(80+20) = 0,80.

**Gabarito: d) 0,80.**

### 5.9 (FGV/TCE-PA/2024)

**Item:** Precisão=90%, Recall=75% → F1 = 2 × 0,9 × 0,75 / (0,9+0,75) = 1,35/1,65 = 0,8182 → 81,82%.

**Gabarito: b) 81,82%.**

### 5.10 (FGV/INPE/2024)

**Item:** "Proporção de verdadeiros positivos em relação ao total de amostras positivas."

**Gabarito: c) Recall.**

### 5.11 (FGV/TCE-RR/2025)

**Item:** VP=90, FP=60 → Precisão = 90/(90+60) = 90/150 = 0,6.

**Gabarito: b) uma precisão de 0,6.**

### 5.12 (FCC/TRT-18/2023)

**Item:** Acurácia = (600+900)/(600+900+400+100) = 1500/2000 = 0,75 = 75%.

**Gabarito: e) acurácia... é de 75%.**

### 5.13 (FGV/TCE-ES/2023)

**Item:** Matriz de confusão permite calcular F1-score, mas **não AUC** (que requer curva ROC).

**Gabarito: d) o F1-score do modelo, mas não a sua AUC.**

### 5.14 (FGV/FHEMIG/2023)

**Item:** Curva ROC – maior poder discriminatório = curva que mais se aproxima do canto superior esquerdo.

**Gabarito: a) A.**

### 5.15 (CESPE/CEBRASPE/STJ/2024)

**Item:** "O método não paramétrico para calcular a AUC assume distribuição normal."

**Gabarito: Errado (E).**

**Comentário:** AUC é uma métrica **não paramétrica** – não assume distribuição.

### 5.16 (CESPE/CEBRASPE/ANATEL/2024)

**Item:** "Quanto mais próxima a curva ROC estiver do canto superior direito, melhor."

**Gabarito: Errado (E).**

**Comentário:** O ponto ideal é o **canto superior esquerdo** (alta TVP, baixa TFP).

### 5.17 (CESPE/CEBRASPE/PF/2025)

**Item:** "Quanto mais a AUC se aproxima de 1, melhor é o desempenho."

**Gabarito: Certo (C).**

### 5.18 (CESPE/CEBRASPE/TRT-10/2025)

**Item:** "Curva A (AUC=0,91) é a melhor – quanto maior a AUC, melhor."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/SEFAZ-SE/2025) | b |
| 02 (CESPE/EMBRAPA/2025) | E |
| 03 (CESGRANRIO/IPEA/2024) | d |
| 04 (CESPE/EMBRAPA/2025) | C |
| 05 (FGV/CGE-PB/2024) | b |
| 06 (CESGRANRIO/BNDES/2024) | b |
| 07 (FGV/RECEITA/2023) | a |
| 08 (FGV/CÂMARA/2023) | d |
| 09 (FGV/TCE-PA/2024) | b |
| 10 (FGV/INPE/2024) | c |
| 11 (FGV/TCE-RR/2025) | b |
| 12 (FCC/TRT-18/2023) | e |
| 13 (FGV/TCE-ES/2023) | d |
| 14 (FGV/FHEMIG/2023) | a |
| 15 (CESPE/STJ/2024) | E |
| 16 (CESPE/ANATEL/2024) | E |
| 17 (CESPE/PF/2025) | C |
| 18 (CESPE/TRT-10/2025) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Recall (Sensibilidade)** | `VP/(VP+FN)` – prioriza encontrar todos os positivos. |
| **Precisão** | `VP/(VP+FP)` – prioriza evitar falsos positivos. |
| **F1-Score** | Média harmônica entre precisão e recall. |
| **Acurácia** | `(VP+VN)/Total` – pode ser enganosa em classes desbalanceadas. |
| **Curva ROC** | TVP vs. TFP para diferentes limiares. |
| **AUC** | Área sob a curva ROC – quanto maior, melhor. |
| **AUC = 0.5** | Classificador aleatório. |
| **AUC = 1** | Classificador perfeito. |

---

*Material complementar à aula "Classificação de Modelos II" (professor Vitor Kessler/Gran Concursos).*