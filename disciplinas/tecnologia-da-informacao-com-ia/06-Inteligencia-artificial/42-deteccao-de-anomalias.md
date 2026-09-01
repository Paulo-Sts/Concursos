# Detecção de Anomalias

## 1. Introdução à Detecção de Anomalias
- A detecção de anomalias consiste na identificação de padrões, comportamentos ou eventos que não se enquadram no comportamento normal esperado dos dados.
- As anomalias podem ser definidas como:
  - Outlier: ponto fora da curva, valor que salta aos olhos e se difere dos demais atributos esperados em uma transação normal;
  - Dado que se desvia significativamente dos outros dados observados;
  - Problemas, oportunidades ou eventos inesperados em diversos domínios.
- Anomalias resultantes de ações maliciosas normalmente tentam se camuflar em meio ao comportamento normal, tornando a separação mais difícil.
- Principais aplicações da detecção de anomalias:
  - Detecção de fraudes;
  - Segurança cibernética;
  - Manutenção preditiva;
  - Monitoramento de saúde;
  - Monitoramento de mídias sociais.

## 2. Tipos de Anomalias

### 2.1 Anomalias Não Intencionais
- São pontos de dados que se desviam da norma devido a erros ou ruído no processo de coleta de dados.
- Os erros podem ser sistemáticos ou aleatórios, originados por problemas como sensores defeituosos ou erro humano durante a entrada de dados.
- Anomalias não intencionais podem distorcer o conjunto de dados, dificultando a obtenção de insights precisos.

### 2.2 Anomalias Pontuais (Point Anomalies)
- Um único ponto de dado é considerado anômalo em relação ao restante dos dados.
- Exemplo: transação de valor extremamente alto em uma conta bancária que geralmente tem transações de valores menores.

### 2.3 Anomalias Contextuais (Contextual Anomalies)
- Um ponto de dado é considerado anômalo em um contexto específico, mas pode ser normal em outro.
- Exemplo: aumento repentino na temperatura de um equipamento pode ser normal durante o verão, mas anômalo no inverno.

### 2.4 Anomalias Coletivas (Collective Anomalies)
- Um conjunto de pontos de dados é anômalo em conjunto, mesmo que os pontos individualmente não sejam anômalos.
- Exemplo: padrão de login em uma conta a partir de várias localizações diferentes em um curto espaço de tempo.

## 3. Métodos de Detecção de Anomalias

### 3.1 Métodos Baseados em Visualização

#### 3.1.1 Gráficos de Dispersão (Scatter Plots)
- Mostram a relação entre duas variáveis numéricas.
- Os pontos mais distantes são considerados outliers.

#### 3.1.2 Box Plots (Diagramas de Caixa)
- Apresentam um conjunto de dados através de cinco medidas, permitindo a realização de diversas observações em uma única análise.
- As cinco medidas são: mínimo, primeiro quartil (Q1), mediana, terceiro quartil (Q3) e máximo.

#### 3.1.3 Gráficos de Séries Temporais (Time Series Plots)
- Apresentam uma representação visual de dados que mostra como os valores variam ao longo do tempo.
- O ponto mais distante da curva é considerado um outlier.

#### 3.1.4 Histogramas
- Gráfico de barras que representa a frequência com que um conjunto de dados contínuos ocorre.
- A barra mais distante das demais representa um outlier.

#### 3.1.5 Mapas de Calor
- Funciona de forma semelhante ao scatter plot.
- Os pontos mais distantes são outliers.
- Quando os dados não se misturam com nenhum outro grupo, geralmente refere-se a um outlier.

### 3.2 Métodos Baseados em Estatísticas

#### 3.2.1 Distribuição Univariada
- Baseia-se na distribuição dos dados para detectar anomalias que estão muito afastadas da média ou da mediana.
- Pontos que estão além de um certo número de desvios padrão são considerados anomalias.

### 3.3 Modelos Paramétricos
- Utilizam distribuições estatísticas conhecidas, como a distribuição normal, para definir regiões de normalidade e identificar outliers.

### 3.4 Métodos Baseados em Aprendizado de Máquina

#### 3.4.1 Supervisionado
- Requer um conjunto de dados rotulados, em que exemplos de anomalias são conhecidos.
- Modelos como árvores de decisão, SVMs e redes neurais podem ser treinados para classificar novos dados como normais ou anômalos.

#### 3.4.2 Não Supervisionado
- Utilizado quando os dados rotulados não estão disponíveis.
- Algoritmos como clustering (K-means, DBSCAN) e autoencoders são populares para detectar anomalias em dados não rotulados.

> [!CAUTION] OBSERVAÇÃO: 
> - O autoencoder é utilizado para zipar informações, ou seja, remover ruídos (informações), que são as anomalias.
> - O DBSCAN procura pontos de densidade; onde há muitos pontos é o centro do grupo. Quem não está próximo do centro do grupo é considerado um outlier.

### 3.5 Métodos Baseados em Proximidade

#### 3.5.1 K-Nearest Neighbors (KNN)
- Identifica anomalias com base na distância de um ponto de dado em relação a seus vizinhos mais próximos.
- Pontos que estão distantes dos demais são considerados anômalos.

### 3.6 Métodos de Densidade

#### 3.6.1 Local Outlier Factor (LOF)
- Mede a densidade local dos dados.
- Identifica como anômalos os pontos que têm densidade significativamente menor do que seus vizinhos.

### 3.7 Métodos Baseados em Modelos Probabilísticos

#### 3.7.1 Modelos de Mistura de Gaussianas (GMM)
- Assumem que os dados podem ser modelados como uma combinação de várias distribuições gaussianas.
- Detectam anomalias como pontos que têm baixa probabilidade em relação ao modelo.

### 3.8 Modelos de Séries Temporais
- Para dados sequenciais, como detecção de anomalias em dados de sensores.
- Modelos como ARIMA ou LSTM podem ser usados para prever valores futuros e identificar anomalias baseadas em desvios dessas previsões.

> [!TIP] DICAS: 
> - A métrica de acurácia não é utilizada para detecção de anomalias, pois ela verifica somente quanto o modelo acerta, não sendo adequada para conjuntos de dados desbalanceados.
> - A métrica F1 é uma das mais indicadas para avaliação em detecção de anomalias, pois equilibra precisão e sensibilidade.
> - Em problemas de detecção de anomalias, o custo do falso negativo (não detectar uma anomalia) é normalmente muito maior do que o custo do falso positivo (identificar um objeto normal como anômalo).
> - A detecção de anomalias é um caso particular de problema de classificação binária, onde a quantidade de objetos da classe alvo (anomalia) é muito inferior à quantidade de objetos da classe normal.