# Redução de Dimensionalidade

## 1. Definição e Contexto
- Processo de diminuir a quantidade de colunas (atributos) de um dataset para acelerar o processamento e melhorar o desempenho do algoritmo.
- Quanto menor o volume de dados, melhor o desempenho do modelo.
- Geralmente, é uma etapa de pré-processamento, onde colunas desnecessárias são removidas antes da construção final do dataset.

## 2. Maldição da Dimensionalidade
- Conceito que descreve a degradação do desempenho do modelo à medida que o número de colunas (características) aumenta excessivamente.
- O gráfico presente no material demonstra a relação entre a acurácia do modelo e a quantidade de colunas.
- Inicialmente, a adição de colunas melhora o desempenho (ganho de informação), mas chega a um ponto em que a adição de variáveis, mesmo que relevantes, provoca a degeneração do modelo (overfitting ou ruído).
- O ponto ideal é representado pela linha tracejada no gráfico, que indica a quantidade ótima de colunas; após esse ponto, o excesso de informação torna-se prejudicial.

> [!TIP] DICAS: 
> - A Maldição da Dimensionalidade é o principal problema que a redução de dimensionalidade visa corrigir. A ideia é que "menos é mais" após um certo ponto.
> - O gráfico é uma curva em formato de sino (ou parábola), mostrando a acurácia no eixo Y e o número de colunas no eixo X.

## 3. Tipos de Redução de Dimensionalidade
- Existem duas abordagens principais para realizar a redução de dimensionalidade: a seleção de atributos e a extração de atributos.

### 3.1 Seleção de Atributos
- Consiste em selecionar os atributos mais relevantes e descartar os que não agregam valor ao modelo.
- Exemplo: Wrapping (ou Feature Selection por busca). Funciona adicionando uma nova coluna ao modelo e testando se a acurácia melhora. Se melhorar, a coluna é mantida; se não, é descartada. O processo é iterativo (expansão do dataset enquanto houver ganho de acurácia).

### 3.2 Extração de Atributos
- Consiste em criar novos atributos a partir da combinação dos atributos originais. Não descarta atributos, mas os transforma.
- Exemplo: Análise de Componentes Principais (PCA), que é o principal algoritmo cobrado em concursos para esse tema.

> [!TIP] DICAS: 
> - A principal diferença entre seleção e extração é: seleção descarta (filtra) atributos, enquanto extração cria novos atributos (combinações).
> - A seleção mantém o significado original dos atributos; a extração cria novos significados (componentes principais).

## 4. PCA (Análise de Componentes Principais)
- Técnica de extração de características (feature extraction) usada para redução de dimensionalidade.
- Funciona combinando as variáveis originais em um novo conjunto de variáveis chamadas "componentes principais".
- Os componentes principais são ordenados de acordo com a quantidade de variância que eles explicam nos dados originais. O primeiro componente principal é o que explica a maior parte da variância.

> [!TIP] DICAS: 
> - A seleção dos componentes principais é realizada com base na variância explicada por cada componente. Só se mantêm os componentes que, juntos, explicam uma porcentagem alta da variância total (ex: 95%).
> - PCA é uma técnica de aprendizado não supervisionado, pois independe de rótulos para extrair componentes de maior variância.

### 4.1 Características e Requisitos do PCA
- Normalização: Para utilizar o PCA de forma adequada, é essencial normalizar os dados.
- Se as variáveis não estiverem na mesma escala, aquelas com maior variância terão maior impacto, distorcendo o resultado da PCA.
- A PCA transforma variáveis correlacionadas em componentes principais não correlacionados (ortogonais).
- Preserva a máxima variabilidade dos dados originais no menor número possível de dimensões.

> [!TIP] DICAS: 
> - A normalização antes do PCA é uma pegadinha clássica em provas. A questão costuma afirmar que não é necessário, mas é fundamental.
> - PCA não é usado para prever novas observações. A previsão é feita por análise preditiva (regressão, por exemplo).
> - Uma das principais utilidades do PCA é facilitar a exploração e visualização dos dados, reduzindo a dimensionalidade para 2 ou 3 dimensões.

### 4.2 Outras Técnicas de Redução de Dimensionalidade
- Além do PCA, a Análise de Componentes Independentes (ICA) é outra técnica de extração de atributos usada para redução de dimensionalidade.
- A ICA busca separar sinais ou fontes que sejam estatisticamente independentes, sendo uma alternativa ao PCA em certos cenários.

> [!TIP] DICAS: 
> - Enquanto o PCA busca componentes com máxima variância, a ICA busca componentes com máxima independência estatística.