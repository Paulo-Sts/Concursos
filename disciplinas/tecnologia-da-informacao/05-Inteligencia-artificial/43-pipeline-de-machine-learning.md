# Pipeline de Machine Learning

## 1. Introdução
- Processo estruturado que organiza todas as etapas necessárias para desenvolver e otimizar um modelo de aprendizado de máquina.
- O pipeline é composto por etapas interligadas que conduzem à criação de um sistema de inteligência artificial funcional.
- Etapas principais: entrada/coleta dos dados, limpeza, pré-processamento, treinamento do modelo e implantação.
- O modelo tende a perder qualidade com o tempo, exigindo monitoramento constante para avaliar se está produzindo mais acertos do que erros.

> [!CAUTION] OBSERVAÇÃO:
> - Embora haja interpretações diferentes sobre a inclusão da limpeza no pré-processamento, o pipeline geralmente contempla: limpeza, pré-processamento como um todo, treinamento do modelo e implantação.
> - A construção de um modelo envolve a criação de um pipeline que começa pela entrada ou coleta dos dados.

## 2. Coleta de Dados
- Etapa inicial do pipeline, essencial para compreender quais dados estão disponíveis.
- Em projetos de data mining, o primeiro passo é o entendimento do negócio, identificando o problema que precisa ser resolvido.
- Após essa etapa, segue-se para o entendimento dos dados, analisando e conhecendo as informações disponíveis na organização.
- Somente após essa análise inicial é possível avançar para a etapa de preparação dos dados.

### 2.1 Identificação de Fontes de Dados
- Fontes de Big Data.
- Planilhas da área de negócio.
- Bancos de dados armazenando dados relacionados aos processos.

### 2.2 Identificação dos Tipos de Dados
- Dados estruturados (formato de tabela).
- Dados não estruturados.
- A classificação influencia diretamente o tipo de processo de Machine Learning que será aplicado.

### 2.3 Métodos de Coleta de Dados
- Coleta manual.
- Coleta automática.
- Web Scraping: acesso a páginas da internet para baixar conteúdos.
- API: obtenção de dados diretamente de fontes externas.
- Logs de sistemas.
- Sensores (IoT - Internet das Coisas): geram grandes volumes de dados.
- Formulários online: dados enviados diretamente para o pipeline.
- Data Lakes e Data Warehouses: repositórios que armazenam diversas bases de dados.

### 2.4 Qualidade dos Dados
- Análise preliminar para avaliar a qualidade.
- Verificação da presença de dados faltantes.
- Verificação de outliers.
- Aplicação de estatísticas descritivas.
- Análise exploratória para determinar se os dados disponíveis são adequados.

> [!TIP] DICAS:
> - Para web scraping, as bibliotecas mais conhecidas em Python são BeautifulSoup e Scrapy.
> - A API do Twitter permite a obtenção de dados diretamente da rede social.

### 2.5 Tecnologias de Coleta
- APIs: Conectar a fontes de dados externas (e.g., Twitter API, Google APIs).
- Web Scraping: Extrair dados de sites usando BeautifulSoup, Scrapy.
- Bancos de Dados: Acessar dados em MySQL, PostgreSQL, MongoDB.
- Armazenamento em Nuvem: AWS S3, Google Cloud Storage, Azure Blob Storage.

## 3. Exploração de Dados
- Etapa essencial para obter uma compreensão mais aprofundada dos dados coletados.
- Identificação de colunas ou variáveis relevantes para o problema a ser resolvido.
- Durante o processo de análise, pode-se decidir não utilizar uma coluna, especialmente se contiver grande quantidade de dados faltantes.

> [!CAUTION] OBSERVAÇÃO:
> - A exploração de dados precede o pré-processamento.
> - Nessa fase, identifica-se quais dados têm potencial para ser incluídos no conjunto final.
> - Normalmente, a exploração de dados não faz parte do pipeline, pois é realizada uma única vez, mas pode ser necessário revisitar essa etapa ao longo do tempo.

### 3.1 Atividades da Exploração de Dados

#### 3.1.1 Sumarização Estatística
- Entender a distribuição dos dados presentes nos diferentes conjuntos.
- Identificar o que pode ser levado para a próxima etapa (preparação dos dados).

#### 3.1.2 Detecção de Outliers
- Utilização de boxplot para identificar dados além dos limites inferiores e superiores.
- Os outliers recebem uma flag para serem tratados na etapa de preparação.

#### 3.1.3 Análise de Distribuições
- Identificação de padrões nas variáveis.
- Descobrir se uma variável segue distribuição normal ou apresenta concentração de dados.
- Cada tipo de distribuição requer tratamento específico durante a preparação dos dados.

#### 3.1.4 Identificação de Padrões e Correlações
- Identificação preliminar de padrões e correlações.
- Identificar atributos com forte correlação com a variável alvo ou classe.
- Atributos com alta correlação ajudam a explicar a variável alvo, sendo úteis para o modelo.

### 3.2 Tecnologias de Exploração de Dados
- Pandas: Manipulação de dados, estatísticas descritivas, sumarização (df.describe(), df.info()).
- Seaborn: Visualização de distribuições e correlações com gráficos como pairplots e heatmaps.
- Matplotlib: Criação de gráficos básicos como histogramas e scatter plots.
- Plotly: Visualizações interativas e gráficas 3D para análise exploratória.
- Sweetviz: Geração automática de relatórios exploratórios com gráficos e insights.
- Pandas Profiling: Relatórios detalhados de análise exploratória automática.
- Tableau: Dashboards interativos para análise visual de dados complexos.
- Power BI: Visualização de dados interativa com foco empresarial.

> [!TIP] DICAS:
> - Ao explorar a base de dados com Pandas em Python, use Data Profile para obter visão geral e estatísticas descritivas.
> - Para colunas categóricas, é possível visualizar a distribuição das categorias (exemplo: 90% dos dados pertencem à classe A e 10% à classe B).

## 4. Pré-Processamento dos Dados
- Também chamado de preparação ou transformação de dados (ETL - Extração, Transformação e Carga, ou LT - Load and Transform).
- Nessa fase, são realizadas diversas atividades para melhorar a qualidade do conjunto de dados, preparando-os para a modelagem.

### 4.1 Limpeza de Dados

#### 4.1.1 Tratamento de Valores Ausentes
- Técnicas para lidar com dados faltantes (imputação, remoção, etc.).

#### 4.1.2 Remoção de Duplicatas
- Eliminação de registros duplicados no conjunto de dados.

#### 4.1.3 Tratamento de Outliers
- Dados fora da curva podem ser problemáticos, especialmente para algoritmos de aprendizagem.
- Em casos onde o ponto está isolado, a melhor abordagem é descartá-lo durante o pré-processamento.

> [!CAUTION] OBSERVAÇÃO:
> - Outliers tendem a prejudicar o desempenho do modelo.
> - Exemplo: em uma regressão linear, um outlier distorce a linha de regressão, que precisa ser ajustada para se aproximar desse ponto fora da curva.

### 4.2 Transformação de Dados

#### 4.2.1 Normalização
- Ajusta a média para 0 e o desvio padrão para 1.
- Transforma distribuições muito dispersas em distribuições com formato de sino perfeito.
- Transforma variáveis numéricas em distribuições iguais para todos os dados.
- Benefício: dados numéricos inseridos no modelo possuem distribuição semelhante, com mesmo formato e intervalo de valores.

> [!CAUTION] OBSERVAÇÃO:
> - A normalização não está relacionada à remoção de duplicidade dos dados relacionais.
> - Valores muito altos podem ser interpretados como mais importantes, quando não são, devido à natureza da variável.
> - Exemplo: salário (até 50 mil) comparado com idade (até 100 anos) - uma pessoa que ganha mil reais seria considerada mais relevante que uma com idade de 30 anos.

#### 4.2.2 Padronização
- Coloca todos os dados na mesma escala.
- Exemplo: idade (0 a 100) e salário (0 a 50 mil) passam a variar de 0 a 1 após a padronização.

#### 4.2.3 Transformação de Variáveis Categóricas

##### 4.2.3.1 One-Hot Encoding
- Transforma variável categórica em variáveis binárias.
- Cria colunas com dados binários (0 ou 1).
- Exemplo: atributo "nível de escolaridade" (superior, médio, fundamental) é transformado em três colunas.

| SUPERIOR | MÉDIO | FUNDAMENTAL |
|----------|-------|-------------|
| 1        | 0     | 0           |
| 0        | 1     | 0           |
| 0        | 0     | 1           |

> [!TIP] DICAS:
> - One-hot encoding é o método mais adequado para variáveis categóricas não ordinais (sem ordem clara).
> - Muitos modelos só trabalham com dados numéricos, por isso a transformação é necessária.

##### 4.2.3.2 Label Encoding
- Substitui a categoria por valores numéricos.
- Exemplo: nível superior = 2, nível médio = 1, nível fundamental = 0.

| NÍVEL DE ESCOLARIDADE | VALOR NUMÉRICO |
|-----------------------|----------------|
| Superior              | 2              |
| Médio                 | 1              |
| Fundamental           | 0              |

> [!CAUTION] OBSERVAÇÃO:
> - Label encoding é usado especialmente para variáveis categóricas ordinais (que têm ordem definida).
> - Exemplo: ensino fundamental é inferior ao ensino superior, portanto 0 para fundamental e 2 para superior.

#### 4.2.4 Transformação Logarítmica
- Transforma um dado normal em um dado exponencial.
- Ajuda a reduzir a distância entre os outliers e os outros dados.

### 4.3 Redução de Dimensionalidade
- Dataset é composto por colunas (atributos, filtros, características ou dimensões) e linhas.
- Reduzir a dimensionalidade significa diminuir o número de colunas no dataset.
- Objetivo: simplificar o dataset, tornando-o mais compacto.
- Benefícios: processamento dos dados mais ágil, treinamento mais rápido.
- São descartadas colunas não relevantes para o problema.

> [!TIP] DICAS:
> - PCA (Análise de Componentes Principais) gera novas variáveis capazes de explicar a variação dos dados.
> - Se tinha 100 variáveis, pode-se ter apenas 5 que explicam a variação da mesma forma que as 100 originais.

#### 4.3.1 Seleção de Características
- Processo de escolher um subconjunto das variáveis existentes.
- Exemplo: de 50 variáveis, selecionar apenas 20.

#### 4.3.2 Extração de Características
- Cria novas variáveis (componentes principais) diferentes do conjunto de dados original.
- Exemplo: PCA cria 10 componentes principais completamente diferentes dos dados originais.
- Muitas vezes se confunde com a engenharia de características.

### 4.4 Feature Engineering (Engenharia de Características)
- Consiste em criar novas variáveis (colunas) ou transformar as existentes.
- Exemplo: em uma tabela com produto e valor da venda, calcular a média do valor de venda de cada produto.
- A média do valor do produto pode ser mais relevante para o contexto do projeto do que manter os dados com vendas isoladas.

### 4.5 Balanceamento de Classes
- O balanceamento se refere às classes (rótulos), que é aquilo que a máquina irá aprender.
- Problema: conjunto de dados com desbalanceamento nas classes.

> [!CAUTION] OBSERVAÇÃO:
> - Exemplo: detecção de transações fraudulentas em cartões de crédito.
> - Conjunto de dados pode conter 1 milhão de transações normais e apenas 50 transações fraudulentas.
> - O objetivo é identificar as transações fraudulentas, mas uma classe aparece muito mais vezes que a outra.

#### 4.5.1 Soluções para Desbalanceamento
- Criar cópias da classe minoritária.
- Descartar parte dos dados da classe majoritária.
- Existem várias abordagens para tratar o desbalanceamento, aplicadas no pré-processamento.

### 4.6 Codificação de Variáveis Textuais
- Leva ao campo do Processamento de Linguagem Natural (PLN).
- Diversas tarefas realizadas com dados textuais para reduzir o tamanho do conjunto de dados.
- Em um dataset de PLN, cada coluna representa uma palavra (especialmente em modelos como bag of words).
- Quanto menos palavras incluídas, mais rápido será o processamento e o treinamento.
- Necessário descartar palavras irrelevantes.

#### 4.6.1 Tokenização
- Separar o texto em tokens (unidades).

#### 4.6.2 Remoção de Stopwords
- Remover palavras desnecessárias (exemplo: de, do, da, dos, a, o, uma).

#### 4.6.3 TF-IDF (Term Frequency-Inverse Document Frequency)
- A frequência das palavras é calculada e utilizada no conjunto de dados.
- Substitui as palavras em si ou suas quantidades originais.

#### 4.6.4 Word Embeddings
- Processo que mapeia palavras para um espaço n-dimensional.
- Palavras semelhantes ficam próximas entre si, enquanto palavras sem relação permanecem distantes.
- Cria um espaço vetorial onde cada palavra é representada por um vetor numérico.
- Em vez de trabalhar diretamente com o texto original, utiliza-se o vetor numérico para representar o conteúdo.
- Otimiza o processamento pela máquina.

> [!TIP] DICAS:
> - Word Embedding é especialmente útil para otimizar o processamento de textos pela máquina.
> - O vetor numérico descreve a posição da palavra no espaço de alta dimensão.

### 4.7 Tecnologias de Pré-Processamento
- Pandas, NumPy: Manipulação e limpeza de dados.
- Dask e Apache Spark: Processamento de grandes volumes de dados de forma distribuída.

> [!CAUTION] OBSERVAÇÃO:
> - Questões de concurso (CESPE/CEBRASPE) frequentemente abordam o uso de tecnologias específicas no pipeline de Machine Learning.