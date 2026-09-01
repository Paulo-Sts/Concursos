# K-Means

## 1. Aprendizado Não Supervisionado
- É o aprendizado de máquina que não possui rótulo nos dados.
- O objetivo é extrair padrões e informações úteis a partir de dados não classificados previamente.
- Trata-se de uma análise descritiva, não preditiva.
- As três tarefas básicas do aprendizado não supervisionado incluem o agrupamento/clusterização, sendo o K-means o principal algoritmo dessa categoria.

> [!CAUTION] OBSERVAÇÃO:
> - A classe, alvo, target ou variável dependente sempre se referem ao rótulo. Isso é fundamental para separar o que é supervisionado do que não é.

## 2. Conceito do K-Means
- É um algoritmo de agrupamento (clusterização) que organiza dados semelhantes em um mesmo grupo e dados distintos em grupos diferentes.
- O parâmetro K representa a quantidade de vizinhos mais próximos, ou seja, o número de grupos que será formado.
- O cientista de dados define o valor de K antes da execução do algoritmo.

### 2.1 Funcionamento do Algoritmo
- Os dados são plotados em um espaço n-dimensional.
- Centroides são criados aleatoriamente no espaço n-dimensional, de acordo com o valor de K.
- Cada ponto (dado) é associado ao centroide mais próximo, formando grupos iniciais.
- O processo é iterativo: os centroides são movidos para o centro (média) do grupo formado.
- As ligações entre pontos e centroides são apagadas e refeitas a cada iteração.
- O algoritmo converge quando os centroides param de se mover.

> [!TIP] DICAS:
> - Uma boa inicialização dos centroides faz com que o K-means crie grupos melhores.
> - Por isso, o algoritmo é frequentemente executado várias vezes para encontrar os grupos que fazem sentido.
> - Todo agrupamento possui uma etapa posterior de análise e interpretação para saber o que os grupos representam.

## 3. Características do K-Means
- É um algoritmo não supervisionado.
- É utilizado para agrupamento de dados não rotulados.
- É do tipo particional, pois particiona o espaço n-dimensional nos grupos definidos.
- A similaridade intragrupo é avaliada considerando o valor médio dos objetos em um grupo, que representa o centroide.
- Os centroides não são selecionados a partir de dados reais; são iniciados de forma aleatória e recalculados como a média dos pontos do grupo.

> [!CAUTION] OBSERVAÇÃO:
> - K-means não é um algoritmo hierárquico, mas sim particional.
> - K-means e K-NN são algoritmos diferentes. O K-NN é supervisionado, enquanto o K-means é não supervisionado.

## 4. Comparação com Outros Algoritmos de Agrupamento
| TIPO | CARACTERÍSTICA |
|------|----------------|
| Particional | Particiona o espaço n-dimensional em grupos. Exemplo: K-means. |
| Hierárquico | Contém uma hierarquia de grupos, representada por dendrogramas. |
| Baseado em densidade | Locais com muitos dados próximos são centros dos grupos. Exemplo: Density Based. |
| Baseado em grade | Divide o espaço n-dimensional em grades, e cada quadrante forma um grupo. |
| Baseado em grafo | Cria um grafo que é separado em grupos. |

## 5. Aprendizado Supervisionado x Não Supervisionado

### 5.1 Aprendizado Supervisionado
- Possui rótulo nos dados.
- Divide-se em:
  - Algoritmos de classificação: SVM, Árvore de Decisão, Random Forest, KNN, Naive Bayes, Regressão Logística, Redes Neurais (LSTM, RNN, CNN).
  - Algoritmos de regressão: Regressão Linear, Regressão Logística, SVM, Redes Neurais, Árvore de Decisão.
- É utilizado para previsão de resultados futuros (análise preditiva).

### 5.2 Aprendizado Não Supervisionado
- Não possui rótulo nos dados.
- É utilizado para análise descritiva.
- Algoritmos principais: K-means (agrupamento), PCA (redução de dimensionalidade).

> [!CAUTION] OBSERVAÇÃO:
> - SVM é supervisionado, não não supervisionado.
> - Regressão Logística é supervisionada, para classificação.
> - Árvore de Decisão é supervisionada.
> - PCA é não supervisionado, mas serve para redução de dimensionalidade, não para agrupamento.
> - ARIMA é um método estatístico para séries temporais, não para agrupamento.

## 6. Conceitos e Definições Importantes
- Centroide: ponto que representa o centro de um grupo, calculado como a média dos objetos do grupo.
- K: número de grupos a serem formados, definido previamente pelo cientista de dados.
- Clusterização particional: divide o conjunto de dados em K grupos de forma não hierárquica.
- Convergência: momento em que os centroides param de se mover, indicando que o algoritmo encontrou uma solução estável.

> [!TIP] DICAS:
> - Questões de concurso costumam cobrar a diferença entre algoritmos supervisionados e não supervisionados.
> - É comum a tentativa de confundir K-means com K-NN.
> - Fique atento: K-means é não supervisionado e não é hierárquico.
> - A inicialização aleatória dos centroides pode afetar o resultado final, sendo recomendada a execução múltiplas vezes.