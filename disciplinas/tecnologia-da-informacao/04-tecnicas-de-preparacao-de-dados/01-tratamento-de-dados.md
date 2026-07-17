# Anotações

# TRATAMENTO DE DADOS – NORMALIZAÇÃO NUMÉRICA

## 1. Conceitos Fundamentais

### 1.1 Por que Normalizar?

- **Motivação Central:** Algoritmos de *Machine Learning* (ML) e mineração de dados são sensíveis à escala das variáveis. Atributos com magnitudes maiores podem dominar o aprendizado, gerando distorções.
- **Objetivo:** Alterar a escala dos atributos numéricos para que fiquem em uma mesma magnitude, evitando que um atributo tenha peso indevido sobre os outros.
- **Diferenças de Terminologia:** O conceito pode aparecer como "normalização", "padronização", "transformação de dados" ou "pré-processamento de dados".

### 1.2 Principais Técnicas

| TÉCNICA | FÓRMULA | OBJETIVO | CARACTERÍSTICAS |
| :--- | :--- | :--- | :--- |
| **Normalização (Min-Max)** | `(X - Xmin) / (Xmax - Xmin)` | Transformar todos os valores para uma escala linear entre **0 e 1**. | É o tipo mais comum de normalização linear. Ideal para dados sem muitos *outliers* e com escalas diferentes. |
| **Padronização (Z-Score)** | `(X - μ) / σ` | Transformar os dados para que tenham uma **média 0** e **desvio padrão 1**. | Não restringe os valores a um intervalo fixo. É mais **robusta à presença de outliers**, pois os toma como referência para o desvio padrão. |
| **Redimensionamento** | Operações com constantes. | Converter uma unidade de medida para outra. | Exemplo: Transformar uma temperatura de Celsius para Fahrenheit. |

## 2. Detalhamento das Técnicas

### 2.1 Padronização (Z-Score)

- **Função:** Centralizar os dados e redimensioná-los conforme o desvio padrão.
- **Componentes:**
    - **μ (mu):** A média aritmética da coluna.
    - **σ (sigma):** O desvio padrão da coluna (medida de dispersão).
- **Resultado:** Os valores resultantes (z-scores) representam quantos desvios padrão um valor está afastado da média.

### 2.2 Normalização Min-Max

- **Função:** Comprimir todos os valores para dentro do intervalo fechado [0, 1].
- **Componentes:**
    - **Xmin:** O menor valor presente no atributo.
    - **Xmax:** O maior valor presente no atributo.
- **Resultado:** O menor valor original torna-se 0, o maior torna-se 1, e todos os outros são interpolados linearmente neste intervalo.

## 3. Análise de Questões de Concurso

### 3.1 Identificação de Técnica pelo Resultado (FGV/CGE-PB/2024)

- **Enunciado:** O auditor precisa tratar dados para garantir que as variáveis tenham uma distribuição normal, com **média igual a zero e desvio padrão igual a um**. Leva em consideração a presença de *outliers*.
- **Gabarito:** **D) padronização (standardization Z-Score)**.
- **Análise:**
    - **Média 0 e Desvio Padrão 1:** Esta é a assinatura da padronização Z-Score.
    - **Presença de Outliers:** O Z-Score é a técnica mais indicada, pois usa o desvio padrão, que é uma métrica estatística robusta para lidar com a variabilidade dos dados (inclusive valores extremos).

### 3.2 Identificação de Técnica pela Fórmula (CESGRANRIO/TRANSPETRO/2018)

- **Enunciado:** Técnica que gera `(vi - μ) / σ`.
- **Gabarito:** **E) Z-Score**.
- **Análise:** A fórmula apresentada define a técnica de Z-Score.

### 3.3 Aplicação em Colunas Categóricas (FGV/SMF-RJ/2023)

- **Enunciado:** Pré-processamento em um conjunto de dados.
- **Gabarito:** **D) normalização das colunas do tipo continua “Idade, Ganho_capital...”.**
- **Análise:**
    - A normalização/padronização **só se aplica a dados numéricos (contínuos)**.
    - Não se normalizam dados categóricos (texto/classes).
    - Não se calcula média de dados categóricos.
    - Discretização é a transformação de dado numérico em categórico, não o contrário.
    - *Outlier* é um conceito de dados numéricos.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESGRANRIO/TRANSPETRO) | **E** | A fórmula `(vi - μ) / σ` define o **Z-Score**. |
| **02** (CESGRANRIO/IPEA) | **A** | Para escalas diferentes, a normalização **Min-Max** (entre 0 e 1) é adequada. |
| **03** (CESPE/ANP) | **C** | Normalização linear entre 0 e 1 é a **Min-Max**. |
| **04** (FGV/CGE-PB) | **D** | Média 0 e Desvio Padrão 1 + Robusto a outliers = **Padronização (Z-Score)**. |
| **05** (FGV/SMF-RJ) | **D** | Normalização aplica-se a colunas **contínuas** (numéricas). |