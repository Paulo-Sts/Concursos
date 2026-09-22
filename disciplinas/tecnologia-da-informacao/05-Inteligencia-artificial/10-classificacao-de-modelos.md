# Classificação de Modelos

## 1. Avaliação de Modelos de Classificação
- A disciplina aborda o aprofundamento em aprendizado de máquina, tratando dos tipos de aprendizado e dos problemas que surgem no treinamento.
- O próximo passo consiste em avaliar o modelo antes de disponibilizá-lo no mercado para determinar se o desempenho é satisfatório.
- A avaliação pode ser apresentada nos editais como avaliação de modelos de classificação ou de modelos de regressão.
- O foco do estudo atual é a avaliação de modelos de classificação, que é mais recorrente em questões de prova.

## 2. Matriz de Confusão
- A matriz de confusão é um instrumento que estabelece a relação entre as previsões realizadas pela máquina e os dados reais do conjunto de testes.
- A lógica consiste em comparar o valor predito com o valor real; se corresponderem, o modelo acertou, caso contrário, houve erro.
- O treinamento é efetuado com o conjunto de treinamento, enquanto a qualidade do modelo é verificada utilizando o conjunto de teste.
- Na matriz, os valores previstos são dispostos em uma dimensão e os valores reais na outra.

### 2.1 Categorias da Matriz
- A lógica pode ser estruturada utilizando as categorias positiva e negativa em lugar de classes específicas.
- Exemplo: na detecção de fraudes, a classe positiva corresponde à ocorrência de fraude e a classe negativa à ausência desta.
- Os quatro quadrantes fundamentais da matriz são:
  - Verdadeiro positivo: quando a máquina acerta a previsão da classe positiva;
  - Falso negativo: quando erra a previsão da classe positiva ⟶ representa uma falha crítica em sistemas sensíveis como diagnósticos médicos;
  - Falso positivo: quando classifica como positiva uma observação que é negativa;
  - Verdadeiro negativo: quando acerta a classificação da classe negativa.

| VALOR PREVISTO | REAL POSITIVO | REAL NEGATIVO |
|---|---|---|
| Predito positivo | Verdadeiro positivo | Falso positivo |
| Predito negativo | Falso negativo | Verdadeiro negativo |

## 3. Métricas de Classificação
- A maioria das métricas utilizadas para avaliação da qualidade de um classificador em aprendizado de máquina é obtida por meio da matriz de confusão.

### 3.1 Acurácia
- Mede o total de instâncias classificadas corretamente em relação ao total de instâncias no conjunto de testes.
- Corresponde ao percentual de acertos totais do modelo.
- O cálculo envolve a soma dos verdadeiros positivos e verdadeiros negativos dividida pelo total de dados presentes na matriz.
- Fórmula: (VP + VN) / (VP + VN + FP + FN).

### 3.2 Precisão
- Mede a proporção de instâncias classificadas como positivas que são realmente positivas no conjunto de testes.
- Quanto maior a precisão, menos falsos positivos o modelo apresentará.
- A precisão alcança o valor máximo de um caso não exista nenhum falso positivo; quanto mais erros deste tipo, menor a precisão.
- Fórmula: VP / (VP + FP).

> [!TIP] DICAS: 
> - Para identificar rapidamente os acertos do classificador em uma matriz, observe os valores que compõem a diagonal principal (verdadeiros positivos e verdadeiros negativos).

> [!CAUTION] OBSERVAÇÃO: 
> - Embora o Cespe historicamente não exigisse muitos cálculos, surgiram questões em 2025 que cobram a aplicação direta das fórmulas de acurácia e precisão.
> - Em matrizes de confusão multiclasse (para k classes), a soma de todos os elementos da matriz é exatamente o número total de objetos testados (n).
> - A taxa de acerto (acurácia) em contextos multiclasse é dada pela razão entre a soma da diagonal principal e a soma de todos os elementos da matriz.