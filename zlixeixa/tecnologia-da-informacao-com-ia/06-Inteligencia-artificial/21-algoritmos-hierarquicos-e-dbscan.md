# Algoritmos Hieráquicos e DBSCAN

## 1. Algoritmos Hierárquicos
- Os algoritmos hierárquicos constroem uma hierarquia de grupos, representada graficamente por um dendrograma.
- Existem duas abordagens principais para execução: aglomerativa (bottom-up) e divisiva (top-down).

### 1.1 Abordagem Aglomerativa (Bottom-Up)
- O processo inicia com cada dado como um grupo individual.
- Os grupos são unidos progressivamente com base em sua similaridade, formando grupos de níveis superiores.
- O processo continua até que todos os dados estejam em um único grupo ou até que o número desejado de clusters (K) seja alcançado.
- Exemplo: Seis grupos individuais são formados inicialmente; dois se unem em um grupo de segundo nível; outros se unem sucessivamente até completar a estrutura hierárquica.

### 1.2 Abordagem Divisiva (Top-Down)
- O processo inicia com todos os dados em um único grupo.
- Esse grupo é dividido sucessivamente em subgrupos menores.
- O processo continua até que cada dado esteja em seu próprio cluster individual ou até que o número desejado de clusters (K) seja alcançado.

### 1.3 Dendrograma
- O dendrograma é uma representação gráfica em forma de árvore que organiza os grupos gerados pelos algoritmos hierárquicos.
- Ele exibe a hierarquia de uniões (bottom-up) ou divisões (top-down) realizadas durante o processo.
- O dendrograma pode ser seccionado em diferentes níveis para definir o número de clusters desejado, conforme a necessidade do usuário.

> [!TIP] DICAS: 
> - Em algoritmos aglomerativos, primeiro cada objeto é classificado em um grupo e, em seguida, os grupos são combinados com base em proximidade até restar um único cluster.
> - Em algoritmos divisivos, todos os pontos iniciam como um grupo único e são subdivididos até que uma regra de parada seja satisfeita.
> - Nos algoritmos hierárquicos, é possível criar uma estrutura hierárquica de acordo com a proximidade entre os indivíduos, resultando em uma árvore binária.

> [!CAUTION] OBSERVAÇÃO: 
> - Nos algoritmos hierárquicos, não há exigência de especificação prévia do número de clusters, diferentemente do K-Means, no qual esse valor deve ser definido pelo usuário.
> - A principal característica que distingue algoritmos hierárquicos do K-Means é a construção do dendrograma, que permite visualizar a hierarquia de agrupamentos.

## 2. DBSCAN
- O DBSCAN (Density-Based Spatial Clustering of Applications with Noise) é um algoritmo de agrupamento baseado em densidade.
- O algoritmo identifica regiões do espaço onde há alta concentração de pontos e forma clusters nessas regiões.
- Pontos que não pertencem a nenhum cluster são classificados como ruído ou outliers, tornando o algoritmo robusto a dados atípicos.

### 2.1 Parâmetros do DBSCAN
- O DBSCAN utiliza dois parâmetros principais:
  - Epsilon (ε): Distância máxima entre dois pontos para que sejam considerados como pertencentes ao mesmo cluster.
  - MinPts (Número Mínimo de Pontos): Quantidade mínima de pontos necessária para formar um cluster.

### 2.2 Efeitos dos Parâmetros
- O parâmetro Epsilon (ε):
  - Valores pequenos para ε impedem a formação de clusters, transformando cada ponto em um grupo isolado.
  - Valores grandes para ε permitem que pontos de grupos distintos sejam reunidos no mesmo cluster, eliminando a existência de ruído.
- O parâmetro MinPts:
  - Valores altos para MinPts deixam muitos pontos de fora dos clusters (mais ruído).
  - Valores baixos para MinPts geram mais clusters.

### 2.3 Comparação com K-Means
| CARACTERÍSTICA | DBSCAN | K-MEANS |
|----------------|--------|---------|
| Definição de número de clusters | Não exige definição prévia de K | Exige definição prévia do número de clusters (K) |
| Robustez a outliers | Robustez elevada (outliers são classificados como ruído) | Sensível a outliers (distorcem o centróide) |
| Parâmetros principais | Epsilon (ε) e número mínimo de pontos (MinPts) | Número de clusters (K) e inicialização dos centróides |
| Funcionamento | Agrupa dados por densidade local | Agrupa dados por distância ao centróide |

### 2.4 Mecanismo de Funcionamento
- O DBSCAN cria clusters formados por dados próximos entre si, de acordo com a distância definida por ε.
- Dados que não se encaixam em nenhum cluster são considerados ruído ou outliers.
- O algoritmo não exige um número pré-definido de clusters, apenas a especificação dos parâmetros ε e MinPts.
- A lógica consiste em identificar grupos cuja distância máxima interna é determinada pelo parâmetro ε, simulando a densidade dos dados.

> [!TIP] DICAS: 
> - O DBSCAN é a escolha ideal para conjuntos de dados com outliers, pois os isola automaticamente como ruído.
> - O K-Means é mais apropriado para dados com distribuição esférica e sem muitos outliers, pois a presença de pontos atípicos distorce o centróide.

> [!CAUTION] OBSERVAÇÃO: 
> - No DBSCAN, a definição de ε e MinPts é crítica para o resultado do agrupamento: distâncias muito pequenas ou mínimos muito altos podem inviabilizar a formação de clusters relevantes.
> - Diferentemente do K-Means, no DBSCAN não há centroides; os clusters são definidos unicamente pela densidade local dos pontos.