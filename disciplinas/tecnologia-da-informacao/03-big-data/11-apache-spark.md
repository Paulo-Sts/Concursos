# Apache Spark

## 1. Definição e Características Gerais
- O Spark é um framework para computação distribuída e processamento de dados em larga escala.
- É um sistema de código aberto, escrito em Scala.
- Não funciona sozinho, pois não é um sistema de armazenamento de dados.
- Oferece paralelismo de dados e tolerância a falhas, permitindo a recuperação até a etapa anterior da falha.
- Provê API de alto nível em Java, Scala, Python e R.
- A vantagem do Spark é sua capacidade de realizar muitas operações de forma automatizada pela utilização eficiente da memória.

## 2. Módulos do Spark

### 2.1 Spark Core
- É o módulo principal do Spark.
- Trabalha com as APIs nas diferentes linguagens.

### 2.2 Spark SQL
- Destinado ao processamento de dados estruturados.
- Capaz de retirar dados de bases estruturadas e relacionais.
- Funciona de maneira similar ao Hive, que converte códigos SQL para Map Reduce Java.

### 2.3 MLlib (Machine Learning Library)
- Biblioteca para aprendizado de máquina.
- Inclui funcionalidades para redes neurais, trabalhos com datasets, arquitetura de dados e processamento em tempo real.
- Funciona de forma parecida aos pacotes do R ou ao numpy e scikit-learn do Python.

### 2.4 GraphX
- Destinado ao processamento de grafos.
- Os dados são divididos em quatro tipos de estruturas: documentos, colunas, grafos e chave-valor.
- Grafos são estruturas interligadas por nós e vértices (arestas).
- Exemplo: sistemas de mapeamento geográfico como Waze e Google Maps, onde cada ponto de referência é um nó e cada rua é uma aresta.

### 2.5 Spark Streaming
- Módulo para processamento de dados em tempo real.
- Apresenta escalabilidade, tolerância a falhas e possibilidade de integração entre processos batch e em tempo real.

### 2.6 Outros Módulos
- SparkR: processamento de dados com a linguagem R.
- PySpark: processamento de dados com Python.
- Panda API: para trabalhos com a biblioteca Panda (dataframes e datasets em Python).
- BlinkDB: realiza consultas em SQL com amostragem, permitindo consultas de fragmentos da base para compreensão geral do conteúdo.

### Tabela de Módulos
| MÓDULO | FUNÇÃO PRINCIPAL |
|--------|------------------|
| Spark Core | Módulo principal do framework |
| Spark SQL | Processamento de dados estruturados e consultas SQL/HQL |
| MLlib | Aprendizado de máquina e redes neurais |
| GraphX | Processamento de grafos |
| Spark Streaming | Processamento em tempo real |
| SparkR | Processamento com linguagem R |
| PySpark | Processamento com Python |
| BlinkDB | Consultas SQL com amostragem |

> [!CAUTION] OBSERVAÇÃO: 
> - O Spark não possui sistema gerenciador de arquivos próprio, dependendo de outras plataformas para isso, como o Hadoop.
> - O Spark Streaming é uma extensão do Spark voltada para processamento em tempo real.

## 3. Arquitetura do Spark

### 3.1 Driver Program
- É a aplicação principal.
- Recebe as chamadas e as interpreta, enviando-as ao gerenciador de cluster.

### 3.2 Cluster Manager
- Administra as máquinas nos clusters.
- Gerencia os recursos disponíveis.

### 3.3 Workers
- Executam as tarefas enviadas pelo Driver Program.
- São as máquinas que realizam o processamento efetivo dos dados.

### 3.4 SparkContext
- Tenta identificar o contexto, recebendo as chamadas do Driver e interpretando-as.
- Envia as chamadas ao gerenciador de cluster.

> [!TIP] DICAS: 
> - A arquitetura do Spark é baseada em clusters interligados, com o Driver Program como aplicação principal.

## 4. Resilient Distributed Datasets (RDD)

### 4.1 Definição e Características
- RDDs são a unidade fundamental de dados no Spark.
- Abstraem um conjunto de objetos distribuídos no cluster.
- Funcionam em modo leitura: não podem ser apagados e, para manipular dados, é necessário criar uma cópia.
- São imutáveis, ou seja, não podem ser alterados após criados.
- São resilientes: tolerantes a falhas, com possibilidade de retornar à etapa anterior do processamento caso o cluster seja danificado.
- São distribuídos: armazenamento na memória por todo o cluster.
- Trabalham no processamento da memória RAM e memória Cache (partes superiores da pirâmide de dados).
- Os RDDs podem armazenar qualquer tipo de elemento, como tipos primitivos (inteiros, caracteres, booleanos), sequências (strings, listas, arrays, tuples) e objetos Scala ou Java.

### 4.2 Armazenamento dos RDDs
- O Spark não possui sistema próprio de armazenamento.
- Os RDDs são armazenados em sistemas auxiliares, podendo ser:
  - Em sistemas de arquivo tradicionais.
  - No HDFS (Hadoop Distributed File System).
  - Em bancos de dados NoSQL, como Cassandra e HBase.

### 4.3 Operações em RDDs
- As operações em RDDs dividem-se em dois tipos principais: transformações e ações.

#### 4.3.1 Transformações
- Criam um novo RDD a partir de um existente.
- São "lazy": não calculam seus resultados imediatamente, apenas lembram as transformações aplicadas.
- Exemplos:
  - map(function): cria um novo RDD processando a função em cada registro do RDD.
  - filter(function): cria um novo RDD incluindo ou excluindo cada elemento de acordo com uma função booleana.
  - flatMap(function): similar ao map, mas retorna mais itens ao invés de apenas um.
  - distinct(): retorna um novo dataset contendo os valores distintos do RDD original.

#### 4.3.2 Ações
- Retornam um valor ao Driver Program após executar uma computação no conjunto de dados.
- Não há criação de novo RDD durante ações.
- Exemplos:
  - count(): retorna o número de elementos dentro do RDD.
  - take(n): retorna um array com os primeiros n elementos do RDD.
  - collect(): retorna um array com todos os elementos do RDD.
  - saveAsTextFile(file): salva o RDD em arquivo no HD.

> [!CAUTION] OBSERVAÇÃO: 
> - Durante as operações de ação não há criação de RDD, enquanto nas transformações há criação de um novo RDD.
> - As transformações no Spark são lazy, ou seja, só são computadas quando uma ação é executada.

## 5. Gráfico Acíclico Direcionado (DAG)
- Agenda tarefas e orquestra os trabalhadores.
- Rastreia as tarefas e garante tolerância a falhas.
- Os RDDs suportam tolerância a falhas por meio do conceito de linhagem (lineage), que guarda todo o histórico de processamento.

## 6. DataFrames e Datasets

### 6.1 DataFrames
- São tabelas estruturadas usadas em problemas de Aprendizado de Máquina.
- O dataframe é um tipo de dado de programação com colunas que atuam de forma autônoma.

### 6.2 Datasets
- São conjuntos de dados provenientes das fontes.
- São imutáveis.
- São fortemente tipados, ou seja, os tipos das colunas estão bem definidos.

> [!TIP] DICAS: 
> - RDDs, DataFrames e Datasets são as principais abstrações para programação paralela no Spark.
> - RDDs são coleções de objetos de só leitura particionados em um conjunto de máquinas.

### Tabela de Operações RDD
| TIPO | OPERAÇÃO | DESCRIÇÃO |
|------|----------|-----------|
| Transformação | map(function) | Cria novo RDD aplicando função em cada elemento |
| Transformação | filter(function) | Cria novo RDD filtrando elementos |
| Transformação | flatMap(function) | Similar ao map, mas retorna mais itens |
| Transformação | distinct() | Retorna RDD com valores distintos |
| Ação | count() | Retorna número de elementos |
| Ação | take(n) | Retorna array com primeiros n elementos |
| Ação | collect() | Retorna array com todos os elementos |
| Ação | saveAsTextFile(file) | Salva RDD em arquivo |

### 6.3 Variáveis Compartilhadas
- O Spark oferece suporte a dois tipos restritos de variáveis compartilhadas:
  - Broadcast: constantes.
  - Accumulators: variáveis específicas para trabalhar com contagem.