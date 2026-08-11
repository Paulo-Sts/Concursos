# Avaliação dos Modelos de Regressão

## 1. Introdução aos Modelos de Regressão
- Os valores de um modelo de regressão não são exatos, mas aproximados, existindo uma margem de erro aceitável.
- As métricas de avaliação permitem calcular essa margem de erro e mensurar o desempenho do modelo.
- Em um modelo de regressão linear, como peso x altura, as variáveis possuem correlação entre si e a regressão gera uma reta que explica a previsão de uma variável com base na outra.

## 2. Mean Squared Error (MSE) – Erro Médio Quadrático

### 2.1 Definição e Fórmula
- O MSE calcula a média dos quadrados das diferenças entre os valores reais e os valores previstos pelo modelo.
- Fórmula: MSE = (1/n) * Σ (yi - ŷi)² , onde:
  - n = número de observações;
  - yi = valor real;
  - ŷi = valor previsto pelo modelo.

### 2.2 Características do MSE
- Eleva os erros ao quadrado, penalizando erros maiores de forma mais intensa.
- É sensível a outliers, pois valores com grandes erros têm impacto significativo no resultado.
- Quanto menor o MSE, melhor o desempenho do modelo.
- O MSE corresponde ao somatório dos resíduos elevados ao quadrado, dividido pela quantidade de itens (média dos quadrados dos erros).

### 2.3 Exemplo de Cálculo
- Para calcular o MSE, pega-se os resíduos (diferença entre o valor real e o valor apurado), eleva-os ao quadrado, soma-os e divide pela quantidade de observações.

## 3. Root Mean Squared Error (RMSE) – Raiz do Erro Médio Quadrático

### 3.1 Definição e Fórmula
- O RMSE é a raiz quadrada do MSE.
- Fórmula: RMSE = √(MSE)

### 3.2 Características do RMSE
- Retorna o erro na mesma unidade dos dados originais, facilitando a interpretação.
- Quanto menor o RMSE, melhor o modelo.
- Exemplo: se MSE = 0,238, então RMSE = √0,238 ≈ 0,488.

> [!TIP] DICAS:
> - O RMSE é mais intuitivo que o MSE porque sua unidade é a mesma da variável alvo, permitindo avaliar a magnitude do erro de forma mais direta.

## 4. Mean Absolute Error (MAE) – Erro Médio Absoluto

### 4.1 Definição e Fórmula
- O MAE calcula a média das diferenças absolutas entre os valores reais e os previstos, sem elevar os erros ao quadrado.
- Fórmula: MAE = (1/n) * Σ |yi - ŷi|

### 4.2 Características do MAE
- Não eleva os erros ao quadrado, tornando-se mais robusto a outliers.
- Quanto menor o MAE, melhor o modelo.

> [!CAUTION] OBSERVAÇÃO:
> - O MAE é menos sensível a outliers que o MSE, sendo preferível quando há valores extremos que poderiam distorcer a avaliação.

### 4.3 Exemplo de Cálculo
- Dados da tabela:

| VALORES PREVISTOS | VALORES REAIS |
|-------------------|---------------|
| 5,0               | 5,2           |
| 5,5               | 5,2           |
| 4,5               | 5,0           |
| 4,0               | 3,8           |
| 4,8               | 4,5           |

- Cálculo dos resíduos em valor absoluto:
  - |5,2 - 5,0| = 0,2;
  - |5,2 - 5,5| = 0,3;
  - |5,0 - 4,5| = 0,5;
  - |3,8 - 4,0| = 0,2;
  - |4,5 - 4,8| = 0,3.
- Soma dos resíduos: 0,2 + 0,3 + 0,5 + 0,2 + 0,3 = 1,5.
- MAE = 1,5 / 5 = 0,3.

## 5. R² (Coeficiente de Determinação)

### 5.1 Definição e Fórmula
- Mede a proporção da variabilidade dos dados de saída que é explicada pelo modelo.
- Fórmula: R² = 1 - [ Σ (yi - ŷi)² ] / [ Σ (yi - ȳ)² ] , onde ȳ = média dos valores reais.

### 5.2 Interpretação do R²
- R² = 1: o modelo explica 100% da variabilidade dos dados.
- R² = 0: o modelo não explica nenhuma variabilidade.
- Quanto mais valores da base de dados o modelo conseguir explicar, maior será o R².
- O R² não penaliza a complexidade do modelo, o que pode levar a overfitting.

## 6. R² Ajustado

### 6.1 Definição e Fórmula
- O R² ajustado corrige o R² considerando o número de preditores (variáveis independentes) no modelo.
- Fórmula: R²_ajustado = 1 - (1 - R²) * (n - 1) / (n - p - 1) , onde:
  - n = número de observações;
  - p = número de preditores.

### 6.2 Características do R² Ajustado
- Penaliza a inclusão de variáveis desnecessárias.
- Quanto mais preditores houver, maior o denominador e, consequentemente, menor o valor do R² ajustado.
- Se uma variável não estiver realmente melhorando o modelo, o R² ajustado pode diminuir.

> [!CAUTION] OBSERVAÇÃO:
> - O R² ajustado é preferível ao R² em modelos com múltiplas variáveis, pois evita que variáveis irrelevantes sejam mantidas apenas por aumentarem artificialmente o R².

## 7. Relação Entre SQR, SQE e SQT
- SQT (Soma de Quadrados Total) = Σ (yi - ȳ)².
- SQR (Soma de Quadrados da Regressão) = Σ (ŷi - ȳ)².
- SQE (Soma de Quadrados dos Erros) = Σ (yi - ŷi)².
- A relação entre elas é: SQT = SQR + SQE.
- O coeficiente de determinação pode ser expresso como: R² = SQR / SQT = 1 - (SQE / SQT).
- Quando R² = 1, temos SQR = SQT e SQE = 0, indicando que o modelo explica perfeitamente os dados.

## 8. Propriedades do R²
- O R² está sempre entre 0 e 1, independentemente da força da correlação entre as variáveis.
- Ao aumentar o número de variáveis independentes, o R² pode aumentar ou permanecer igual, mas nunca decresce.
- O R² indica a porcentagem da variação total que é explicada pela regressão.
- Não mede se uma variável causa ou não a outra, apenas a força da relação explicativa.

> [!CAUTION] OBSERVAÇÃO:
> - Embora algumas bancas considerem que o R² nunca decresce ao adicionar variáveis, é possível discordar, pois o conjunto de resíduos muda completamente e o R² pode tanto aumentar quanto diminuir.