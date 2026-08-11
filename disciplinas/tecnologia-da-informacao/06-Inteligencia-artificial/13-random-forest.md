# Random Forest

## 1. Definição e Conceito Fundamental
- Random Forest (floresta randômica ou floresta aleatória) é um ensemble de múltiplas árvores de decisão treinadas de forma ligeiramente diferente.
- O termo "ensemble" significa um conjunto de modelos de IA utilizados para realizar tarefas de classificação ou regressão.
- Funcionamento básico do ensemble:
  - Constrói-se diversos modelos (ex: 10 árvores);
  - Realiza-se uma votação entre os resultados;
  - A classe que obtiver mais votos prevalece.
- Exemplo prático de ensemble:
  - Seis modelos indicam classe A e quatro indicam classe B;
  - O resultado final é classe A (voto majoritário).

## 2. Mecânica de Funcionamento da Random Forest

### 2.1 Processo de Treinamento
- Cada árvore de decisão é treinada com um subconjunto de dados obtido por amostragem com reposição (bootstrap).
- Amostragem com reposição significa que, ao retirar um dado para compor o subconjunto, faz-se uma cópia e o dado original retorna ao conjunto de treinamento.
- Esse processo gera conjuntos de treinamento ligeiramente distintos para cada árvore.
- São utilizadas centenas ou até milhares de árvores de decisão na composição da floresta.

### 2.2 Processo de Predição (Classificação)
- Um novo dado é processado por todas as árvores de decisão da floresta.
- Cada árvore gera um resultado (uma classe).
- Realiza-se uma votação entre os resultados.
- A classe com maior número de votos é a previsão final da Random Forest.

### 2.3 Processo de Predição (Regressão)
- Cada árvore gera um valor numérico como resultado.
- Calcula-se a média de todos os valores produzidos pelas árvores.
- Essa média é a previsão final da Random Forest.

> [!TIP] DICAS:
> - A Random Forest pode ser utilizada tanto para classificação quanto para regressão, pois as árvores de decisão são aplicáveis a ambos os propósitos.
> - A principal justificativa para o uso da Random Forest é a redução do risco de overfitting.

## 3. Características e Comparações com Árvore de Decisão

### 3.1 Interpretabilidade
- Árvore de decisão única: possui alta interpretabilidade, permitindo explicar com clareza a origem de cada decisão.
- Random Forest: perde a interpretabilidade, pois torna-se inviável explicar individualmente cada uma das centenas de árvores.

### 3.2 Custo Computacional
- Árvore de decisão: modelo mais leve computacionalmente.
- Random Forest: modelo mais pesado, pois envolve centenas ou milhares de árvores.

### 3.3 Risco de Overfitting
- Árvore de decisão única: pode tornar-se excessivamente especializada no conjunto de treinamento, decorando padrões.
- Random Forest: mesmo que algumas árvores incorram em overfitting, a maioria não o fará, e o resultado agregado permite uma decisão mais robusta.
- Consequência: Random Forest apresenta redução de variância.

> [!CAUTION] OBSERVAÇÃO:
> - A Random Forest é apresentada como não interpretável, de alto custo computacional e de baixa variância.
> - Diferentemente da árvore de decisão, a Random Forest não tem sensibilidade a outliers e não apresenta tendência a overfitting.

### 3.4 Importância das Variáveis
- A Random Forest não atribui a mesma importância para todas as variáveis ao fazer as predições.
- Em um dataset com diversas colunas, cada árvore de decisão tende a selecionar apenas alguns atributos para realizar suas divisões.
- A floresta como um todo pode fornecer métricas de importância relativa de cada recurso.

> [!CAUTION] OBSERVAÇÃO:
> - As Random Forests fornecem métricas de importância dos recursos, mas não utilizam pontuações de distância euclidiana para esse fim.
> - A importância é calculada com base em critérios como o índice de Gini ou redução de impureza.

## 4. Esclarecimentos sobre Terminologia e Conceitos

### 4.1 Mineração de Dados
- Mineração de dados é o processo voltado à extração de informações de bases de dados.
- A Random Forest permite a realização de mineração de dados por meio da criação de estruturas de aprendizagem.
- A Random Forest utiliza múltiplas árvores de decisão, e não uma única árvore.

### 4.2 Aprendizado Supervisionado
- A Random Forest é um algoritmo de aprendizado supervisionado.
- O aprendizado supervisionado trabalha com um conjunto de observações para produzir predições em função de variáveis independentes contínuas e/ou binárias.

### 4.3 Expressões Equivalentes
- "Random Forests" (plural) é uma variação aceitável do termo.
- "Árvores aleatórias" é uma tradução possível para Random Forest.

> [!TIP] DICAS:
> - A banca CESPE/CEBRASPE costuma cobrar a definição de Random Forest como um método de aprendizado de conjunto que combina várias árvores de decisão.
> - É comum a cobrança de que a Random Forest pode ser usada tanto para regressão quanto para classificação.