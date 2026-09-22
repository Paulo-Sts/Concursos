# Otimização de Hiperparâmetros

## 1. Conceitos Fundamentais
- Existem dois tipos de parâmetros em modelos de machine learning.
- Hiperparâmetros:
  - Controlam o processo de aprendizagem do modelo;
  - Não são ajustados diretamente pelo algoritmo durante o treinamento;
  - A otimização manual é um processo lento e complexo.
- Parâmetros normais:
  - São ajustados durante o processo de treinamento;
  - Exemplo: os pesos em uma rede neural.

> [!CAUTION] OBSERVAÇÃO: 
> - Os hiperparâmetros são definidos antes do início do treinamento, diferentemente dos parâmetros do modelo, que são aprendidos durante o treino.

## 2. Hiperparâmetros por Algoritmo

### 2.1 K-Nearest Neighbors (KNN)
- n_neighbors: número de vizinhos a serem considerados.
- p: parâmetro da métrica de distância (p=1: Manhattan; p=2: Euclidiana).

### 2.2 Support Vector Machines (SVM)
- C: parâmetro de regularização (valores maiores evitam underfitting).
- kernel: função do kernel (linear, poly, rbf, sigmoid).
- gamma: parâmetro para kernels não lineares (controla o alcance de influência de um ponto de treinamento).
- degree: grau do polinômio (se kernel for poly).

### 2.3 Decision Trees
- max_depth: profundidade máxima da árvore.
- min_samples_split: número mínimo de amostras exigido para dividir um nó.
- min_samples_leaf: número mínimo de amostras em um nó folha.
- criterion: função de avaliação de divisão (gini ou entropy).

### 2.4 Redes Neurais (MLP)
- hidden_layer_sizes: número de neurônios nas camadas ocultas.
- activation: função de ativação (relu, tanh, logistic).
- solver: algoritmo para otimização de pesos (adam, sgd, lbfgs).
- learning_rate: taxa de aprendizado (constant, adaptive, invscaling).

## 3. Métodos de Busca

### 3.1 Grid Search
- Técnica exaustiva de busca.
- Todas as combinações possíveis de hiperparâmetros em um "grid" são testadas.
- O espaço de busca é definido pelo usuário.
- Vantagem: garante que todas as combinações serão testadas, aumentando as chances de encontrar a melhor configuração.
- Desvantagem: muito custoso em tempo e recursos computacionais, especialmente em espaços grandes.

Exemplo em Python:
```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier

param_grid = {'n_estimators': [50, 100, 200], 'max_depth': [10, 20, 30]}
grid_search = GridSearchCV(estimator=RandomForestClassifier(), param_grid=param_grid)
grid_search.fit(X_train, y_train)
```

> [!TIP] DICAS: 
> - No exemplo acima, o sistema rodará 9 modelos diferentes (3x3).
> - O espaço de busca é limitado pela quantidade de valores colocada pelo usuário no grid.

### 3.2 Random Search
- Amostra aleatoriamente combinações de hiperparâmetros a partir de um espaço de busca definido pelo usuário.
- O número de modelos a serem gerados é definido previamente.
- Vantagem: mais eficiente que o Grid Search em espaços de alta dimensionalidade, pois não testa todas as combinações e ainda assim pode encontrar boas soluções.
- Desvantagem: pode não explorar tão bem o espaço de busca quanto o Grid Search.

> [!TIP] DICAS: 
> - A principal diferença entre Grid Search e Random Search é que o Grid Search é exaustivo (testa todas as combinações), enquanto o Random Search testa apenas uma amostra aleatória do espaço de busca.

### 3.3 Otimização Bayesiana
- Constrói um modelo probabilístico da função de perda em relação aos hiperparâmetros.
- Trata o ajuste de hiperparâmetros como um problema de regressão.
- Aprende a relação entre o valor do parâmetro e o desempenho do modelo.
- Processo iterativo:
  - Determina o ponto de avaliação futura com base no resultado obtido na interação passada.
- Ferramentas: Hyperopt, Optuna, Scikit-Optimize.

> [!CAUTION] OBSERVAÇÃO: 
> - A otimização bayesiana se utiliza do conceito de probabilidade para encontrar o valor de entrada de uma função que possa retornar o menor valor de saída possível.
> - O número de iterações de pesquisa pode ser reduzido a partir da escolha dos valores de entrada, levando em consideração os resultados anteriores.

### 3.4 Algoritmos Genéticos
- Uma única combinação de valores de hiperparâmetros é um indivíduo (ex: {n_estimators: 100, max_depth: 20}).
- São geradas populações de indivíduos.
- Uso de uma função de aptidão (ex: avaliar a acurácia de um modelo de classificação).
- Indivíduos com melhor aptidão reproduzem.
- Processo roda por algumas iterações.

### 3.5 Hyperband
- Usa uma técnica adaptativa para explorar e "exploitar" diferentes configurações de hiperparâmetros.
- Combina a eficiência do Random Search com um mecanismo de "early stopping".
- Interrompe configurações que não parecem promissoras.
- Aloca mais recursos para configurações promissoras.

## 4. AutoTuning e AutoML

### 4.1 AutoTuning
- Abordagem automatizada para o ajuste e a otimização de hiperparâmetros de modelos de machine learning de forma contínua e adaptativa.
- Otimiza dinamicamente os hiperparâmetros durante a execução do modelo.
- Uso em modelos em produção.
- Ferramentas: Ray Tune, Optuna, Keras Tuner.

> [!CAUTION] OBSERVAÇÃO: 
> - AutoTuning é a capacidade de se ter uma ferramenta de otimização de hiperparâmetros a ser rodada em produção.

### 4.2 AutoML (Automated Machine Learning)
- Processo de automatizar diversas etapas no desenvolvimento de modelos de machine learning.
- Tarefas automatizadas: pré-processamento de dados, seleção de features, escolha do modelo e otimização de hiperparâmetros.
- Utiliza técnicas de otimização como Grid Search, Random Search e algoritmos de otimização avançados (ex: Bayesian Optimization ou Hyperband).
- O processo de ajuste de hiperparâmetros no AutoML é contínuo.

> [!CAUTION] OBSERVAÇÃO: 
> - O AutoML integra o processo de seleção de modelos e otimização de hiperparâmetros, automatizando grande parte do pipeline de machine learning.