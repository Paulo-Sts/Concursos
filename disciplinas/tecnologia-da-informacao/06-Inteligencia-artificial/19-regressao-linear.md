# Regressão Linear

## 1. Contexto da Machine Learning
- A Inteligência Artificial (IA) engloba a área de Machine Learning (ML), que é o foco do estudo.
- O aprendizado em Machine Learning é dividido em três tipos principais:
  - Aprendizado por reforço;
  - Aprendizado não supervisionado;
  - Aprendizado supervisionado.

### 1.1 Aprendizado Supervisionado
- Este é o tipo de aprendizado onde os dados de treinamento possuem tanto a entrada (variável independente) quanto a saída (variável dependente) rotulada.
- O objetivo é aprender um mapeamento que permita prever a saída para novas entradas.
- Subdivide-se em duas grandes categorias de algoritmos:
  - Algoritmos de Classificação: Preveem uma saída categórica (classe discreta).
  - Algoritmos de Regressão: Preveem uma saída numérica contínua.

#### 1.1.1 Principais Algoritmos de Classificação e Regressão
- Redes neurais artificiais;
- Árvore de decisão;
- Random Forest;
- KNN;
- SVM.

#### 1.1.2 Principais Algoritmos de Classificação
- Naïve Bayes;
- Regressão logística.

#### 1.1.3 Principais Algoritmos de Regressão
- Regressão linear.

> [!OBSERVAÇÃO]
> - É possível utilizar qualquer tipo de função para modelar os dados, como uma polinomial (ex.: x² + 2), desde que a função escolhida seja capaz de explicar adequadamente a base de dados.

## 2. Conceito de Regressão Linear
- A regressão linear é um algoritmo estatístico utilizado em machine learning para resolver problemas de regressão.
- Seu objetivo principal é modelar a relação entre uma ou mais variáveis independentes (de entrada) e uma variável dependente (de saída).
- A variável de entrada é chamada de variável independente, pois define a variável de saída.
- A variável de saída é chamada de variável dependente, pois seu valor depende da entrada.
- Os dados são plotados em um gráfico n-dimensional, onde cada variável independente representa uma dimensão.

### 2.1 Tipos de Regressão Linear
- Regressão linear simples: Quando existe apenas uma variável independente.
- Regressão linear múltipla: Quando existem duas ou mais variáveis independentes.

### 2.2 Métrica de Avaliação (R²)
- O R² é uma métrica fundamental para avaliar a qualidade do modelo de regressão.
- Ele mede o quão bem a variável independente explica a variabilidade da variável dependente.
- Quanto mais próximo de 1, maior a correlação e melhor o ajuste do modelo.

## 3. Características Fundamentais da Regressão Linear
- A variável dependente (Y) é sempre uma variável numérica contínua.
- A variável independente (X) é uma variável numérica.
- O algoritmo busca minimizar as discrepâncias entre os valores previstos e os valores reais de Y (minimização do erro).

## 4. Comparação entre Regressão Linear e Regressão Logística
- Ambos os modelos buscam estimar o relacionamento entre uma variável dependente e uma ou mais variáveis independentes.
- A principal diferença reside no tipo de variável dependente que cada um é capaz de prever.

### 4.1 Regressão Linear vs. Regressão Logística
- Regressão Linear: Utilizada para prever uma variável dependente contínua (não limitada).
- Regressão Logística: Utilizada para prever uma variável dependente categórica (normalmente binária, como 0 ou 1). A saída não é uma probabilidade contínua entre 0 e 1, e sim a classe prevista.

### Exemplo de Base de Dados
- A tabela a seguir ilustra um dataset de treinamento com m=11 dados, onde a idade é a variável de entrada (x) e a pressão arterial é a variável de saída (y).

| IDADE (X) | PRESSÃO ARTERIAL (Y) |
|-----------|-----------------------|
| 15        | 2132                  |
| 25        | 9143                  |
| 36        | 7153                  |
| 73        | 1625                  |
| 64        | 1546                  |
| 74        | 1687                  |
| 54        | 1378                  |
| 61        | 1499                  |
| 65        | 1591                  |
| 46        | 1281                  |
| 72        | 166                   |

> [!TIP] DICAS: 
> - Guarde que a regressão linear é o algoritmo "padrão" para problemas onde o objetivo é prever um valor numérico (ex.: preço de um imóvel, temperatura, pressão arterial).