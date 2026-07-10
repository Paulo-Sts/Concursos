# Anotações – Regressão Linear

## 1. Conceito de Regressão Linear

- A **Regressão Linear** é um algoritmo de aprendizado de máquina **supervisionado** usado para resolver problemas de **regressão** (previsão de valores numéricos contínuos).
- **Objetivo:** modelar a relação entre uma **variável dependente (Y)** e uma ou mais **variáveis independentes (X)**.
- **Regressão linear simples:** apenas uma variável independente (`y = ax + b`).
- **Regressão linear múltipla:** duas ou mais variáveis independentes (`y = a₁x₁ + a₂x₂ + ... + b`).

> ### 1.1 Exemplo
> - **Entrada (X):** idade do paciente.
> - **Saída (Y):** pressão arterial.
> - O algoritmo encontra a reta que melhor se ajusta aos dados, minimizando o erro entre os valores previstos e os reais.

## 2. Regressão Linear vs. Regressão Logística (comparação)

| CARACTERÍSTICA | REGRESSÃO LINEAR | REGRESSÃO LOGÍSTICA |
| --- | --- | --- |
| **Tipo de problema** | Regressão (prever números) | Classificação (prever categorias) |
| **Variável dependente (Y)** | **Numérica / Contínua** (ex.: preço, temperatura) | **Categórica / Binária** (ex.: 0 ou 1, spam ou normal) |
| **Saída** | Qualquer valor real (de -∞ a +∞) | Valor entre 0 e 1 (probabilidade) |
| **Função utilizada** | Função linear (`y = ax + b`) | Função sigmoide (logística) |
| **Objetivo** | Minimizar o erro quadrático (distância dos pontos à reta) | Maximizar a probabilidade de classificação correta |

> ### 2.1 Diferença fundamental
> - A principal diferença entre as duas regressões é o **tipo de variável que elas preveem**: numérica (regressão linear) vs. categórica (regressão logística).

## 3. Métrica de Avaliação – R² (Coeficiente de Determinação)

- O **R²** mede o quão bem a variável independente (X) explica a variável dependente (Y).
- **Interpretação:** quanto mais próximo de **1**, melhor é o ajuste do modelo (maior correlação).
- **Exemplo:** R² = 0,85 → 85% da variação de Y é explicada por X.

## 4. Características da Regressão Linear

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Tipo de aprendizado** | Supervisionado |
| **Tipo de problema** | Regressão (previsão de números) |
| **Variáveis de entrada (X)** | Numéricas (contínuas ou discretas) |
| **Variável de saída (Y)** | Numérica / Contínua |
| **Função** | Linear (ou polinomial, se transformada) |
| **Objetivo** | Minimizar o erro entre os valores previstos e os reais |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/BDMG/2025 – Analista)

**Item:** "Os algoritmos supervisionados de ML do tipo regressão linear são capazes de prever uma variável dependente contínua usando determinado conjunto de variáveis independentes."

**Gabarito: Certo (C).**

**Comentário:** A definição está correta: regressão linear prevê uma variável dependente **contínua (numérica)** a partir de variáveis independentes.

### 5.2 (FGV/PREFEITURA DE MACAÉ/2024 – Analista)

**Item:** "Técnica mais apropriada para lidar com um problema de regressão no qual o objetivo é prever um valor numérico contínuo."

**Gabarito: a) A Regressão Linear.**

**Comentário:** As demais alternativas são algoritmos de classificação ou não supervisionados.

### 5.3 (CESPE/CEBRASPE/STJ/2024 – Analista)

**Item:** "A regressão linear do aprendizado de máquina busca estabelecer uma relação entre as variáveis de entrada de um algoritmo."

**Gabarito: Errado (E).**

**Comentário:** A regressão linear busca estabelecer uma relação entre as variáveis **independentes (entrada)** e a **variável dependente (saída numérica)** – não apenas entre variáveis de entrada.

### 5.4 (CESPE/CEBRASPE/MPE-RO/2023 – Analista Programador)

**Item:** "Algoritmo que mostra ou preve a relação entre duas variáveis" (figura com reta ajustada).

**Gabarito: c) regressão linear.**

**Comentário:** A figura com reta ajustada aos dados indica regressão linear.

### 5.5 (CESPE/CEBRASPE/ANTT/2024 – Especialista)

**Item:** "A regressão logística, assim como a regressão linear, pode ser usada para estimar o relacionamento entre uma variável dependente e uma ou mais variáveis independentes."

**Gabarito: Certo (C).**

**Comentário:** Ambas modelam a relação entre X e Y. A diferença está no **tipo de Y**:
- Regressão linear → Y numérico.
- Regressão logística → Y categórico.

### 5.6 (FGV/AGSUS/2025 – Analista)

**Afirmativas:**

- I – Ambas modelam relação entre variáveis dependentes e independentes; a diferença é o tipo de variável prevista. **(V)**
- II – A regressão linear minimiza discrepâncias ajustando uma probabilidade, com saída entre 0 e 1. **(F)** – isso é regressão logística.
- III – Ambas requerem tamanho de amostra adequado. **(V)** – válido para ambas.

**Gabarito: d) I e III, apenas.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/BDMG/2025) | C |
| 02 (FGV/MACAÉ/2024) | a |
| 03 (CESPE/STJ/2024) | E |
| 04 (CESPE/MPE-RO/2023) | c |
| 05 (CESPE/ANTT/2024) | C |
| 06 (FGV/AGSUS/2025) | d |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Regressão Linear** | Algoritmo supervisionado para prever valores numéricos contínuos. |
| **Variável independente (X)** | Entrada (preditores). |
| **Variável dependente (Y)** | Saída numérica (o que se quer prever). |
| **Regressão linear simples** | Uma única variável X. |
| **Regressão linear múltipla** | Duas ou mais variáveis X. |
| **R²** | Mede a qualidade do ajuste (quanto mais próximo de 1, melhor). |
| **Diferença para Regressão Logística** | Regressão linear: Y numérico. Regressão logística: Y categórico. |

---

*Material complementar à aula "Regressão Linear" (professor Vitor Kessler/Gran Concursos).*