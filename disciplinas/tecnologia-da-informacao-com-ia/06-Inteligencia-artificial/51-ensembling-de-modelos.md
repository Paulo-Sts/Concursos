# Ensembling de Modelos

## 1. Conceito Fundamental de Ensembling
- O ensembling consiste na combinação de vários modelos para criar um modelo final.
- A lógica central é combinar diferentes abordagens para melhorar a precisão das previsões.
- Modelos diferentes possuem pontos fortes e fracos distintos, e seus erros podem ser complementares.
- A estratégia eficaz é combinar vários modelos distintos, variando o conjunto de treinamento para cada um, treiná-los separadamente e, posteriormente, combinar as classificações por meio de votação.
- Quando vários modelos emitem previsões, a decisão final é tomada com base na maioria.
- Exemplo: se cinco modelos afirmam que um exemplo pertence à classe A e três afirmam que pertence à classe B, a classificação final será da classe A.

### 1.1 Exemplo Prático de Ensembling
- Considera-se um conjunto de dados dividido em seis partes.
- Cada parte é utilizada para treinar um modelo diferente: árvore de decisão, KNN, rede neural (multilayer perceptron), Naive Bayes, regressão logística e SVM.
- Ao apresentar um novo exemplo, a árvore de decisão, o KNN, a rede neural e o Naive Bayes classificam como classe A, enquanto a regressão logística e o SVM indicam classe B.
- A maioria dos modelos apontou classe A, e essa será a classificação final.
- Possível explicação: a rede neural e o SVM podem ter sofrido overfitting, enquanto os demais modelos não.
- Ao combinar as previsões de diferentes modelos, os erros podem ser neutralizados.

> [!TIP] DICAS:
> - O ensembling é uma técnica frequentemente utilizada por especialistas em aprendizado de máquina para melhorar a precisão das previsões.
> - A votação por maioria é o método mais comum de combinação para problemas de classificação.

## 2. Bagging (Bootstrap Aggregating)
- O bagging foi um dos primeiros algoritmos historicamente utilizados para realizar a mistura de modelos.
- Consiste em duas etapas: Bootstrap e Aggregation.
- O processo conjunto é conhecido no campo da ciência de dados como BAG.

### 2.1 Etapa de Bootstrap
- Gera vários subconjuntos de dados de treinamento a partir do conjunto de dados original.
- Utiliza bootstrap sampling (amostragem com reposição).
- A amostragem com reposição permite que um mesmo elemento seja escolhido mais de uma vez.
- Exemplo: em um conjunto de treinamento composto por cinco dados distintos, ao criar um conjunto de Bootstrap com três elementos, realiza-se o sorteio de três dados entre os cinco, com possibilidade de repetição. Se o elemento "C" for sorteado na primeira rodada, ele permanece disponível para os sorteios seguintes.
- Os elementos que não foram escolhidos para o subconjunto de treinamento formam o Out-of-Bag Dataset, utilizado para testes.

### 2.2 Etapa de Aggregation
- Para cada subconjunto de dados, um modelo é treinado independentemente.
- Na fase de predição, as previsões de todos os modelos são combinadas.
- Problemas de classificação: votação por maioria.
- Problemas de regressão: média dos valores previstos.
- Exemplo de regressão: para previsão do valor do aluguel, um modelo prevê R$ 1.800, outro prevê R$ 900, um terceiro prevê R$ 1.900, outro R$ 2.000, outro R$ 1.500 e outro R$ 1.800. O valor final será a média de todas as previsões.

### 2.3 Exemplo Clássico: Random Forest
- O Random Forest utiliza várias árvores de decisão.
- Constrói diversos subconjuntos de dados para gerar árvores de decisão distintas.
- Embora cada subconjunto utilize o mesmo algoritmo (árvore de decisão), diferentes resultados são gerados.
- Cada árvore é gerada a partir de um subconjunto de dados.
- Posteriormente, realiza-se a agregação dos resultados por votação.

> [!CAUTION] OBSERVAÇÃO:
> - O bagging gera vários modelos simultaneamente, cada um a partir de um subconjunto de dados.
> - O foco do bagging é a redução da variância, não do viés.
> - O bagging não treina modelos em sequência; todos os modelos são treinados de forma independente.

## 3. Boosting
- No boosting, os modelos são construídos sequencialmente.
- Cada novo modelo tenta corrigir os erros cometidos pelos modelos anteriores.
- As amostras mal classificadas recebem maior peso a cada iteração, incentivando o próximo modelo a focar nesses exemplos difíceis.
- Inicialmente, cria-se um subconjunto de dados e treina-se um weak learner (modelo fraco), frequentemente uma árvore de decisão.
- Após o treinamento, identificam-se as previsões erradas.
- Esses erros são ponderados, e os exemplos incorretos são incluídos no próximo subconjunto de dados para o treinamento do próximo modelo.
- Ao final, calcula-se a média de todas as previsões, considerando todos os modelos, sendo que os modelos mais recentes terão maior peso.

### 3.1 AdaBoost (Adaptive Boosting)
- Constrói um conjunto de modelos simples (geralmente árvores de decisão rasas, chamadas de stumps) de forma sequencial.
- Árvores de decisão rasas são aquelas com pequena profundidade, que resultam em decisões binárias, dividindo os dados de forma simples, geralmente até o segundo nível.
- A cada iteração, as amostras mal classificadas ganham um peso maior, e o próximo modelo foca em corrigi-las.
- No final, as previsões dos modelos são combinadas ponderadamente.
- O AdaBoost foca em exemplos classificados erroneamente.

> [!TIP] DICAS:
> - Stumps são árvores de decisão com profundidade limitada, geralmente até o segundo nível.
> - O AdaBoost é considerado o modelo tradicional de boosting.

### 3.2 Gradient Boosting
- Ajusta as previsões dos modelos subsequentes, minimizando os resíduos (erros) do modelo anterior.
- A cada nova etapa, o modelo tenta ajustar os erros residuais deixados pelos modelos anteriores.
- A diferença fundamental entre o AdaBoost e o Gradient Boosting é que, no Gradient Boosting, a cada modelo gerado, o erro é minimizado sequencialmente utilizando o método de Gradiente Descendente.
- O Gradient Boosting minimiza o erro ao longo das etapas, ajustando os erros residuais deixados pelos modelos anteriores.
- No Gradient Boosting, a preocupação é com os erros do modelo anterior, ou seja, com o resíduo, que corresponde à diferença entre o valor esperado e o valor previsto.

### 3.3 XGBoost (Extreme Gradient Boosting)
- Implementação otimizada do Gradient Boosting.
- Baseado em árvores de decisão.
- Principais características:
  - Regularização nos modelos gerados;
  - Validação cruzada interna (em vez de simples subconjuntos, envolve a troca do conjunto de teste e a criação de K subconjuntos);
  - Paralelização de cálculos, tornando o processo mais rápido;
  - Melhor uso de memória;
  - Interpretação de importância dos atributos;
  - Lida com dados ausentes de maneira mais eficiente.
- Amplamente reconhecido por ter conquistado diversas competições de machine learning.

> [!TIP] DICAS:
> - Embora o modelo XGBoost em si não seja facilmente interpretável, a atribuição de importância a cada atributo permite entender melhor a origem da decisão tomada.
> - O XGBoost cresce as árvores verticalmente (em profundidade).

### 3.4 LightGBM (Light Gradient Boosting Machine)
- Criado pela Microsoft.
- Variante do Gradient Boosting mais rápida e escalável.
- Utiliza Leaf-wise growth para construir árvores de decisão.
- As árvores crescem horizontalmente (verticalmente no XGBoost e no Gradient Boosting original).
- Diferencia-se dos outros modelos de boosting pelo crescimento horizontal das árvores.

### 3.5 CatBoost
- Lida com variáveis categóricas de forma eficiente, sem necessidade de transformação explícita (como one-hot encoding).
- Utiliza Oblivious Trees (árvores simétricas).
- Enquanto o XGBoost e o LightGBM normalmente geram árvores assimétricas, o CatBoost constrói árvores simétricas.
- O CatBoost também trabalha com variáveis categóricas.

> [!CAUTION] OBSERVAÇÃO:
> - No XGBoost e no Gradient Boosting, as árvores crescem verticalmente (em profundidade).
> - No LightGBM, as árvores crescem horizontalmente (Leaf-wise growth).
> - No CatBoost, as árvores são simétricas (Oblivious Trees).

### 3.6 Comparação entre os Modelos de Boosting
| ALGORITMO | CARACTERÍSTICA PRINCIPAL | CRESCIMENTO DA ÁRVORE |
|-----------|--------------------------|----------------------|
| AdaBoost | Foca em exemplos classificados erroneamente | Vertical |
| Gradient Boosting | Minimiza resíduos (erros) do modelo anterior | Vertical |
| XGBoost | Implementação otimizada do Gradient Boosting com regularização | Vertical |
| LightGBM | Versão rápida e escalável do Gradient Boosting | Horizontal (Leaf-wise) |
| CatBoost | Lida com variáveis categóricas e utiliza árvores simétricas | Simétrico (Oblivious Trees) |

## 4. Stacking (Stacked Generalization)
- Diferentes modelos são combinados de forma hierárquica.
- Primeiramente, são gerados modelos que produzem saídas (ex.: 1,2; 1,3; 1,4).
- Em seguida, um modelo adicional (metamodelo) é criado para receber essas saídas e fornecer a classificação final.
- Usa um meta-modelo (ou modelo de nível superior) para aprender a combinar as previsões dos modelos de base.
- Diversos modelos são treinados em um conjunto de dados, e suas previsões são usadas como inputs para um modelo meta que faz a previsão final.
- O modelo meta pode ser uma regressão linear, uma árvore de decisão, ou até mesmo uma rede neural.
- A principal diferença em relação ao bagging: no bagging os modelos geram classificações individuais e há uma votação entre eles; no stacking os modelos são combinados de maneira hierárquica.

> [!TIP] DICAS:
> - O stacking é menos comum em provas, mas é importante entender o conceito hierárquico.
> - O metamodelo aprende a melhor forma de combinar as previsões dos modelos base.

## 5. Resumo das Principais Técnicas de Ensembling
| TÉCNICA | CARACTERÍSTICA PRINCIPAL | MÉTODO DE COMBINAÇÃO | REDUÇÃO DE ERRO |
|---------|--------------------------|---------------------|-----------------|
| Bagging | Modelos treinados em paralelo com subconjuntos de dados | Votação (classificação) ou média (regressão) | Reduz variância |
| Boosting | Modelos treinados em sequência, corrigindo erros anteriores | Média ponderada (pesos maiores para modelos recentes) | Reduz viés |
| Stacking | Modelos combinados hierarquicamente com metamodelo | Metamodelo aprende a combinar previsões | Reduz viés e variância |

> [!CAUTION] OBSERVAÇÃO:
> - O bagging tem como foco a redução da variância, não do viés.
> - O boosting tem como foco a redução do viés.
> - No bagging, os modelos são treinados em paralelo (simultaneamente).
> - No boosting, os modelos são treinados em sequência.
> - No stacking, os modelos são combinados hierarquicamente.

## 6. Conceitos Importantes

### 6.1 Classificação x Clustering x Regressão
- Algoritmos de classificação: usam cálculos preditivos para atribuir dados a categorias predefinidas.
- Algoritmos de clustering: dividem os dados em vários grupos determinando o nível de similaridade entre os pontos de dados.
- Algoritmos de regressão linear: mostram ou preveem a relação entre duas variáveis ou dois fatores ajustando uma linha reta contínua aos dados.
- Algoritmos de gradient boosting: produzem um modelo de previsão que agrupa modelos de previsão fracos por meio de um processo de ensembling que aprimora o desempenho geral do modelo.

### 6.2 Weak Learners (Modelos Fracos)
- São modelos simples, frequentemente árvores de decisão rasas.
- São combinados para construir um modelo mais forte.
- No boosting, os weak learners são treinados sequencialmente para corrigir erros dos modelos anteriores.

### 6.3 Poda (Pruning)
- Técnica utilizada para contornar a complexidade de um modelo em relação à plataforma de execução.
- Visa simplificar um modelo complexo substituindo uma sub-árvore por uma folha.
- O objetivo da poda é reduzir a profundidade da árvore, tornando-a menos complexa.
- Realizada por meio de um algoritmo de regularização.

### 6.4 Out-of-Bag Dataset
- Conjunto de elementos que não foram selecionados para o subconjunto de treinamento no processo de Bootstrap.
- Utilizado para testes e validação do modelo.

### 6.5 Amostragem com Reposição (Bootstrap Sampling)
- Consiste em selecionar elementos de um conjunto de dados, permitindo que um mesmo elemento seja escolhido mais de uma vez.
- Alguns elementos podem ser repetidos, enquanto outros não são selecionados.
- Os elementos não selecionados formam o Out-of-Bag Dataset.

> [!TIP] DICAS:
> - A poda é uma técnica de regularização que reduz o overfitting.
> - A poda simplifica o modelo e reduz seu tamanho, sendo útil quando o modelo possui requisitos computacionais além da capacidade da plataforma de execução.
> - A poda substitui uma sub-árvore complexa por uma folha associada a uma classe específica.