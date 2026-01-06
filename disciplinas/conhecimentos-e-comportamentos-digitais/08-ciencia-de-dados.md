# Ciência de Dados

## 1. Conceito e Objetivo
- Campo interdisciplinar que utiliza métodos científicos, processos, algoritmos e sistemas para extrair conhecimento e insights a partir de dados.
- Objetivo Final:
  - Extrair informações que proporcionem vantagem competitiva e agreguem valor à organização.
  - Gerencia o ciclo de vida dos dados, da coleta ao descarte, com foco na extração de conhecimento.
- Pirâmide do Conhecimento (Dados → Informação → Conhecimento)
  - Dado: Valor isolado (ex: número 37,5).
  - Informação: Dado contextualizado (ex: 37,5°C é a temperatura de uma criança).
  - Conhecimento: Interpretação que permite conclusões (ex: 37,5°C indica febre).

## 2. Processo da Ciência de Dados (Etapas Principais)

#### 2.1 Coleta de Dados
- Acesso e ingestão de dados de diversas fontes.
- Fontes: Bancos de dados (relacionais/não relacionais), arquivos, sensores (IoT), APIs, Web Scraping, pesquisas, questionários.
- Dificuldades: Qualidade dos dados, escalabilidade (Big Data), privacidade (LGPD, LAI).

#### 2.2 Preparação dos Dados
- Refinamento para criar um *dataset* estruturado.
- Atividades:
  - Eliminação de dados duplicados.
  - Tratamento de valores ausentes (exclusão ou preenchimento com média/regressão).
  - Correção de erros de formatos e padronização (ex: moedas diferentes).
  - Tratamento de *outliers* (ex: transformação logarítmica).
  - Transformação de variáveis (categóricas para numéricas ou vice-versa).
  - Seleção de características relevantes.
  - Validação dos dados.

#### 2.3 Análise Exploratória de Dados (AED)
- Compreensão dos dados por meio de visualização e estatística.
- Técnicas:
  - Visualização: Gráficos de barras, histogramas, boxplots, scatter plots.
  - Estatística Descritiva: Medidas de tendência central (média, mediana, moda) e dispersão (desvio padrão, variância).
  - Correlação entre variáveis.
  - Técnicas Multivariadas: Análise de Componentes Principais (PCA), Análise de Clusters.

#### 2.4 Modelagem de Dados
- Aplicação de algoritmos para extrair conhecimento.
- Tipos de Análise:
  - Descritiva: Compreender a base de dados e agrupar dados (clusterização).
  - Preditiva: Usar dados históricos para prever eventos futuros.
  - Prescritiva: Propor soluções para problemas específicos.
  - Diagnóstica: Identificar a causa raiz de um problema.

#### 2.5 Validação de Modelos
- Verificar se o modelo aprendeu corretamente.
- Técnicas de Validação:
  - Holdout: Divisão em conjuntos de treino (ex: 70%) e teste (ex: 30%).
  - Validação Cruzada: K-Fold (divide dados em K subconjuntos), Leave-One-Out.
  - Bootstrap.
- Métricas de Avaliação:
  - Classificação: Acurácia, Precisão, Recall, F1-Score, AUC-ROC.
  - Regressão: Erro Quadrático Médio (MSE), Erro Absoluto Médio (MAE), Coeficiente de Determinação (R²).
  - Clusterização: Coeficiente de Silhueta, Índice Davies-Bouldin.

#### 2.6 Implantação de Modelos
- Integração com sistemas existentes.
- Automação de processos (do fluxo de coleta ao resultado).
- Criação de interfaces (ex: web) para acesso.
- Monitoramento e atualizações contínuas.

## 3. Tipos de Aprendizado de Máquina (Usados na Modelagem)

#### 3.1 Aprendizado Supervisionado
- O modelo é treinado com dados históricos que possuem rótulos (respostas conhecidas).
- Tarefas:
  - Classificação: Prever uma categoria (ex: fraude/não fraude, tumor maligno/benigno).
  - Regressão: Prever um valor numérico contínuo (ex: valor de um empréstimo).

#### 3.2 Aprendizado Não Supervisionado
- Não há rótulos pré-definidos. O modelo encontra padrões nos dados.
- Tarefas:
  - Clusterização: Agrupar dados similares (ex: algoritmo K-Means).
  - Redução de Dimensionalidade: Simplificar o conjunto de dados removendo atributos irrelevantes (ex: PCA).

#### 3.3 Aprendizado por Reforço
- Um agente inteligente interage com um ambiente.
- Recebe recompensas ou punições com base em suas ações.
- Objetivo: Aprender a maximizar as recompensas ao longo do tempo (ex: robô explorando um ambiente).

## 4. Pontos Relevantes para Concursos

#### 4.1 Caráter Multidisciplinar
- Envolve conhecimentos de computação, matemática aplicada, inteligência artificial, estatística e otimização.

#### 4.2 Foco em Problemas Complexos
- Utiliza grandes conjuntos de dados (Big Data) como núcleo de operação.

#### 4.3 Paralelização
- Principal motivador: Reduzir o tempo de processamento, permitindo que tarefas ocorram simultaneamente.

#### 4.4 Aplicações Práticas
- Previsão do tempo, espalhamento de doenças (usando modelos como Cadeias de Markov), detecção de fraudes, segmentação de clientes.