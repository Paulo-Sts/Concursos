# Tipos de Aprendizado de Máquina 3

## 1. Outros Tipos de Aprendizado
- Aprendizado semissupervisionado ⟶ ocorre quando o conjunto de dados está parcialmente rotulado, possuindo normalmente poucos dados com rótulos e muitos dados sem rótulos.
- A lógica consiste em economizar tempo e custo com rotulagem humana, utilizando a parte rotulada para treinar uma IA inicial que prevê os rótulos dos dados restantes; posteriormente, treina-se uma nova solução com a base completa.
- Aprendizado de transferência ⟶ utiliza um modelo já treinado em uma tarefa genérica para auxiliar em uma tarefa específica e relacionada.
- Exemplo: treinar uma IA generativa de forma genérica com dados globais e depois especializá-la com dados internos de uma instituição específica para torná-la perita em determinado assunto.
- Aprendizado online ⟶ o modelo é treinado em tempo real conforme novos dados são recebidos, permitindo atualizações constantes.
- É essencial para lidar com o drift, situação em que os padrões dos dados variam ao longo do tempo, como na detecção de fraudes onde o comportamento fraudulento evolui.

## 2. Aprendizado Profundo e Técnicas Avançadas
- Aprendizado profundo ou deep learning ⟶ consiste no uso de redes neurais artificiais com muitas camadas de neurônios para analisar dados complexos.
- Exemplos incluem o GPT (Generative Pre-trained Transformer) e redes neurais convolucionais para identificação de padrões em imagens.
- Diferencia-se do machine learning tradicional, que utiliza algoritmos como árvores de decisão e k-nearest neighbors.
- Aprendizado auto-supervisionado ⟶ o modelo gera seus próprios rótulos automaticamente a partir dos dados de entrada, como ocorre no pre-training de IAs generativas que preveem a próxima palavra em uma sequência.
- Aprendizado de adversidade ⟶ o modelo é treinado para enfrentar competidores que tentam enganar o sistema ou prejudicar sua precisão.
- Exemplo das GANs (Generative Adversarial Networks), onde uma rede criadora compete com uma rede discriminadora até que as imagens geradas sejam indistinguíveis das reais.

## 3. Mapeamento de Tarefas e Algoritmos
- O aprendizado de máquina divide-se em supervisionado (rotulado), não supervisionado (sem rótulo) e por reforço (agente interagindo com ambiente).
- As tarefas do aprendizado supervisionado são classificação (alvo categórico) e regressão (alvo numérico).
- As tarefas do aprendizado não supervisionado são agrupamento, regras de associação e redução de dimensionalidade.

| TIPO DE APRENDIZADO | TAREFA | ALGORITMOS EXEMPLOS |
|---|---|---|
| Supervisionado | Classificação | Naive bayes, regressão logística, árvores de decisão, random forest, knn, svm |
| Supervisionado | Regressão | Regressão linear, redes neurais, árvores de decisão, random forest, knn, svm |
| Não Supervisionado | Agrupamento | K-means (k-médias), algoritmos hierárquicos, dbscan |
| Não Supervisionado | Regras de associação | A priori |
| Não Supervisionado | Redução de dimensionalidade | Pca (análise de componentes principais) |

### 3.1 Detalhes dos Algoritmos Supervisionados
- Naive Bayes: baseado em probabilidade condicional e utilizado apenas para problemas de classificação.
- Regressão Logística: utiliza a função sigmoide para realizar classificação binária, retornando percentuais de probabilidade.
- Regressão Linear: prevê um valor numérico através de uma reta que explica a relação entre variáveis independentes e dependentes.
- Algoritmos versáteis: redes neurais, árvores de decisão, floresta randômica (Random Forest), KNN e SVM podem resolver tanto classificação quanto regressão.

### 3.2 Detalhes dos Algoritmos Não Supervisionados
- K-means: algoritmo particional de agrupamento, considerado o mais importante da categoria.
- DBSCAN: algoritmo de agrupamento baseado em densidade.
- PCA: método mais famoso para redução de dimensionalidade, atuando normalmente na fase de pré-processamento.
- A Priori: algoritmo mais conhecido para descoberta de regras de associação e vendas casadas.

> [!CAUTION] OBSERVAÇÃO: 
> - O aprendizado por reforço tem baixa incidência em concursos e geralmente aparece apenas em provas específicas de ciência de dados.

> [!CAUTION] OBSERVAÇÃO: 
> - No aprendizado supervisionado, os algoritmos obrigatoriamente partem de um modelo de conhecimento no formato (entrada, saída desejada).

> [!TIP] DICAS: 
> - O aprendizado não supervisionado é essencial para extrair conhecimento oculto quando não há saídas conhecidas ou rótulos disponíveis.