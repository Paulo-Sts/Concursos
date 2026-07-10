# Anotações – Regressão Logística

## 1. Conceito e Propósito

- **Regressão Logística** é um algoritmo de **classificação**, apesar do nome "regressão".
- **Classificação binária:** prevê se uma instância pertence a uma classe (1) ou a outra (0).
- Também pode ser usada para **classificação multiclasse** (one-vs-rest): uma regressão logística para cada classe.

> ### 1.1 Como funciona
> - Utiliza a **função sigmoide (logística)** para mapear qualquer valor de entrada para um valor **entre 0 e 1**.
> - A saída é interpretada como a **probabilidade** de a instância pertencer à classe positiva.

## 2. A Função Sigmoide

- A função sigmoide tem formato de **"S"**.
- **Fórmula:**

```
P(y=1) = 1 / (1 + e^(-z))
```

onde `z` é uma combinação linear das variáveis de entrada (`z = β₀ + β₁x₁ + β₂x₂ + ...`).

- **Saída:** sempre entre 0 e 1.
- **Interpretação:**
  - Próximo de 1 → classe positiva (1).
  - Próximo de 0 → classe negativa (0).
  - Valores intermediários → probabilidade.

> ### 2.1 Características
> - Modelo **paramétrico** (usa uma função conhecida – a sigmoide).
> - **Não linear** – a relação entre as variáveis e a saída não é linear.
> - A curva pode ser mais ou menos íngreme dependendo dos coeficientes.

## 3. Regressão Logística vs. Regressão Linear

| CARACTERÍSTICA | REGRESSÃO LOGÍSTICA | REGRESSÃO LINEAR |
| --- | --- | --- |
| **Tipo de problema** | Classificação (binária ou multiclasse) | Regressão (prever número) |
| **Variável dependente** | Categórica (0 ou 1) | Contínua (número) |
| **Função utilizada** | Sigmoide (logística) | Reta (linear) |
| **Saída** | Entre 0 e 1 | Qualquer valor real |
| **Tipo de modelo** | Não linear | Linear |

> ### 3.1 Atenção (pegadinha)
> - **Regressão logística** não é regressão – é **classificação**.
> - A banca pode tentar confundir: "regressão logística prevê valores numéricos" → **ERRADO**.

## 4. Aplicações Típicas

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Detecção de fraudes** | Prever se uma transação é fraudulenta ou não. |
| **Diagnóstico médico** | Prever se um paciente tem uma doença (sim/não). |
| **Aprovação de crédito** | Prever se um cliente irá inadimplir. |
| **Marketing** | Prever se um cliente vai comprar ou não. |
| **Probabilidade de decisão judicial** | Prever se uma decisão será favorável ou desfavorável. |

## 5. Overfitting e Regularização

- A regressão logística **pode sofrer overfitting**.
- **Solução:** técnicas de **regularização** (ex.: L1, L2) para reduzir a complexidade do modelo e melhorar a generalização.

## 6. Questões de Concurso Comentadas

### 6.1 (FCC/2023/TRT-15 – Analista)

**Item:** "Prever a probabilidade de uma decisão judicial ser favorável ou desfavorável."

**Gabarito: b) a técnica de Logistic Regression.**

**Comentário:** Problema de classificação binária → regressão logística.

### 6.2 (FGV/2023/PGM-NITERÓI – Analista)

**Item:** "Algoritmo que atribui, necessariamente, um valor no intervalo numérico de 0 a 1 para cada entrada."

**Gabarito: c) Regressão Logística.**

**Comentário:** A função sigmoide da regressão logística sempre produz saída entre 0 e 1.

### 6.3 (CESPE/CEBRASPE/SERPRO/2023 – Analista)

**Item:** "A regressão logística utiliza variáveis independentes categóricas para prever uma variável lógica ou booleana."

**Gabarito: Errado (E).**

**Comentário:** As variáveis independentes são **numéricas** (ou podem ser codificadas, mas a entrada é numérica).

### 6.4 (CESPE/CEBRASPE/PF/2025 – Perito)

**Item:** "O algoritmo de minimização da função custo da regressão logística não é imune ao overfitting, que pode ser mitigado por meio de técnica de regularização."

**Gabarito: Certo (C).**

**Comentário:** A regressão logística pode sofrer overfitting e a regularização é uma solução.

### 6.5 (CESPE/CEBRASPE/INSA/2025 – Tecnologista)

**Item:** "A regressão logística pode ser usada para prever variáveis dependentes contínuas."

**Gabarito: Errado (E).**

**Comentário:** A regressão logística prevê **variáveis categóricas binárias**, não contínuas.

### 6.6 (CESPE/CEBRASPE/EMBRAPA/2025 – Analista)

**Item:** "Os algoritmos de regressão logística são utilizados para prever valores numéricos e baseiam-se em uma relação linear entre valores diferentes."

**Gabarito: Errado (E).**

**Comentário:** Regressão logística prevê **classes (0/1)** e é **não linear**.

### 6.7 (CESPE/CEBRASPE/CAGEPA/2024 – Analista)

**Item:** "Instituição financeira utilizando Big Data para prever fraudes nas suas transações – técnica recomendada:"

**Gabarito: b) a regressão logística.**

**Comentário:** Detecção de fraudes é um problema de **classificação binária** → regressão logística.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FCC/TRT-15/2023) | b |
| 02 (FGV/PGM-NITERÓI/2023) | c |
| 03 (CESPE/SERPRO/2023) | E |
| 04 (CESPE/PF/2025) | C |
| 05 (CESPE/INSA/2025) | E |
| 06 (CESPE/EMBRAPA/2025) | E |
| 07 (CESPE/CAGEPA/2024) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Regressão Logística** | Algoritmo de **classificação binária** (apesar do nome). |
| **Função Sigmoide** | `1/(1+e^(-z))` – saída entre 0 e 1. |
| **Saída** | Probabilidade de pertencer à classe positiva. |
| **Tipo de modelo** | Paramétrico, não linear. |
| **Comparação com Regressão Linear** | RL: classificação, saída 0/1. Regressão Linear: prever números. |
| **Overfitting** | Pode ocorrer – regularização mitiga. |
| **Extensão para multiclasse** | One-vs-rest (uma regressão por classe). |

---

*Material complementar à aula "Regressão Logística" (professor Vitor Kessler/Gran Concursos).*