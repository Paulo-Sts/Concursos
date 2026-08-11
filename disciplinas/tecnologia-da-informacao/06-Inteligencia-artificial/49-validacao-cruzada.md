# Validação Cruzada (Cross-validation)

## 1. Conceito Fundamental
- Técnica utilizada para avaliar modelos de aprendizado de máquina, especialmente em problemas de classificação.
- Os conjuntos de treinamento e teste devem ser uma partição disjunta do conjunto de dados.
- Permite estimar a precisão preditiva do modelo a partir de uma amostra de dados não utilizada anteriormente.

## 2. K-Fold Cross-Validation
- Método que divide o dataset em k partes (folds) de tamanhos aproximadamente iguais.
- Para cada iteração, uma das partes é destinada para testes e as outras k-1 partes são utilizadas para treinamento.
- Processo repetido k vezes, alternando a parte utilizada como teste.
- Ao final, calcula-se a média das métricas de desempenho de cada iteração para obter a performance final.

### 2.1 Passos do K-Fold
- Dividir o conjunto de dados em k partes.
- Para cada parte (fold), treinar o modelo com k-1 partes e avaliar a performance no fold restante.
- Calcular a média das métricas de desempenho de cada iteração.
- Repetir o processo para cada uma das k partes do conjunto de dados.

### 2.2 Escolha do Valor de k

| VALOR DE K | CARACTERÍSTICAS |
|------------|-----------------|
| k = 2 ou 3 | Benefício para recursos computacionais limitados ou avaliação mais rápida; reduz o número de ciclos de treinamento; fornece estimativa razoável do desempenho |
| k = 5 ou 10 | Escolhas mais populares; proporcionam bom equilíbrio entre eficiência computacional e estimativa de desempenho |
| k = 20 | Pode proporcionar avaliação mais detalhada; aumenta a carga computacional; pode resultar em maior variação se subconjuntos forem muito pequenos |

### 2.3 Vantagens do K-Fold
- Oferece equilíbrio entre precisão e eficiência computacional.
- Menos viés comparado à simples divisão treino/teste (hold-out).
- Usa todo o conjunto de dados para validação e treinamento.

### 2.4 Desvantagens do K-Fold
- Pode ser computacionalmente mais caro que uma simples divisão treino/teste.

> [!TIP] DICAS:
> - Quanto mais recursos computacionais são utilizados e mais ajustados os parâmetros do modelo para o conjunto de dados, melhor será o resultado.
> - O treinamento do modelo ocorre com k-1 partes, e o erro é avaliado utilizando a parte que sobra.

## 3. Hold-Out
- Método simples de avaliação onde os dados são divididos uma única vez.
- Separar 20% dos dados para avaliação e treinar com 80% dos dados (proporções comuns).
- Processo realizado apenas uma vez.

## 4. Overfitting (Sobreajuste)
- Fenômeno que ocorre quando o modelo é excessivamente complexo, aprendendo não apenas o padrão do conjunto de treinamento, mas também os ruídos e dados mal identificados.
- O modelo de baixa complexidade não é a causa do overfitting (pelo contrário, modelos de alta complexidade tendem a sofrer mais com esse problema).
- Pode ser causado por dados de treinamento com grande quantidade de informações irrelevantes.

### 4.1 Detecção e Mitigação
- A validação cruzada k-fold é um dos métodos utilizados para detectar a ocorrência de overfitting.
- Durante o treinamento, o erro do modelo no conjunto de treinamento diminui, mas quando o erro do conjunto de teste começa a aumentar, indica overfitting.
- O treinamento deve ser interrompido quando o erro do conjunto de validação começa a subir.
- Busca-se o mínimo global da função de erro projetada com o conjunto de validação, em vez de maximizar o desempenho.

## 5. Leave-One-Out Cross-Validation (LOOCV)
- Variação do k-fold onde k é igual ao número total de linhas ou registros do dataset.
- Cada exemplo é usado como conjunto de testes exatamente uma vez, enquanto os demais formam o conjunto de treinamento.

### 5.1 Passos do LOOCV
- Para cada observação, treinar o modelo usando todas as outras observações e validar no dado deixado de fora.
- Repetir o processo até que todas as observações tenham sido usadas como dado de validação uma vez.

### 5.2 Variação Leave-p-Out
- Modelo é treinado com todos os dados, exceto "p" registros.
- Os "p" registros são usados como conjunto de testes.

### 5.3 Vantagens do LOOCV
- Usa todo o conjunto de dados tanto para treinamento quanto para validação.
- Muito eficiente para conjuntos de dados pequenos.

### 5.4 Desvantagens do LOOCV
- Extremamente caro computacionalmente para grandes conjuntos de dados.
- Pode ser mais sensível a outliers.
- Geralmente aplicado em algoritmos como regressão linear, não sendo recomendado para algoritmos custosos como redes neurais profundas.

> [!CAUTION] OBSERVAÇÃO:
> - A diferença entre k-fold cross-validation e Leave-One-Out não é o valor de K, mas sim o fato de que no LOOCV, K é igual ao número total de registros.

## 6. Bootstrap
- Técnica de reamostragem onde se amostra o conjunto de dados com substituição.

### 6.1 Passos do Bootstrap
- Amostrar o conjunto de dados com substituição para criar subconjuntos de treinamento.
- Treinar o modelo nesses subconjuntos e validar nos dados que não foram selecionados (out-of-bag).
- Repetir o processo várias vezes e calcular a média do desempenho.

### 6.2 Vantagens do Bootstrap
- Excelente para conjuntos de dados pequenos.

### 6.3 Desvantagens do Bootstrap
- Pode reduzir a variabilidade do modelo.
- O conjunto de dados de teste pode ser menor do que em abordagens de validação cruzada tradicionais.

## 7. Tratamento de Dados Faltantes
- Métodos para tratar atributos não preenchidos na base de dados:
  - Média da coluna.
  - Interpolação de vizinhas mais próximas.
  - Moda da coluna.
  - Vizinhas mais próximas (KNN).
  - Valor aleatório.

## 8. Divisão Estratificada
- Técnica onde cada subconjunto (fold) do conjunto de dados mantém a mesma proporção de classes presentes no conjunto original.
- Recomendada especialmente quando o valor de k é igual a 10.