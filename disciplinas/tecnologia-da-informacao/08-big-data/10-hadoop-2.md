# Hadoop 2

## 1. Mapreduce
- É um modelo de programação e um framework do Hadoop usado para processar grandes volumes de dados de forma distribuída e paralela.
- Foi inspirado no modelo criado pelo Google e adaptado para o ecossistema Hadoop.
- Divide o processamento em duas fases principais: Map e Reduce.

### 1.1 Funcionamento
- Map (Mapeamento):
  - Entrada: conjunto de pares (chave, valor).
  - Função: processar os dados de entrada, filtrando, transformando e gerando novos pares (chave, valor) intermediários.
  - Os dados resultantes são particionados por chave para serem processados na fase seguinte.
- Shuffle & Sort (Baralhamento e Ordenação):
  - Intermediário entre Map e Reduce.
  - Reagrupa todos os valores com a mesma chave e ordena os dados para serem enviados aos nós que executarão o Reduce.
- Reduce (Redução):
  - Entrada: cada chave com a lista de valores associados.
  - Função: agregar, resumir ou combinar esses valores, gerando o resultado final.

### 1.2 Exemplo prático: contagem de palavras
- Imagine que queremos contar quantas vezes cada palavra aparece em um conjunto de documentos:
  - Map: lê o texto e para cada palavra gera (palavra, 1).
  - Shuffle & Sort: agrupa todas as ocorrências da mesma palavra.
  - Reduce: soma os valores para cada palavra, resultando em (palavra, total).

> [!TIP] DICAS: 
> - Map: divide e distribui os dados para processamento.
> - Reduce: agrega e combina os resultados processados, produzindo a saída final.

> [!CAUTION] OBSERVAÇÃO: 
> - O MapReduce do Hadoop é um modelo amplamente utilizado para processamento de grandes volumes de dados, porém é voltado para processamento em lotes, não para baixa latência ou tempo real.

## 2. Ecossistema Hadoop
- É um conjunto de ferramentas, frameworks e bibliotecas que trabalham em conjunto para armazenar, processar, gerenciar e analisar grandes volumes de dados.
- É modular, onde cada componente cuida de uma parte do fluxo de dados: armazenamento, processamento, ingestão, análise, visualização e orquestração.

### 2.1 Componentes Centrais
- HDFS (Hadoop Distributed File System):
  - Sistema de arquivos distribuído e tolerante a falhas.
  - Armazena dados em blocos replicados em diferentes nós.
- YARN (Yet Another Resource Negotiator):
  - Gerenciador de recursos e agendador de tarefas.
  - Controla quais nós executam quais processos.
- MapReduce:
  - Modelo de programação e processamento distribuído.
  - Executa tarefas em lote, dividindo o processamento em fases Map e Reduce.

> [!CAUTION] OBSERVAÇÃO: 
> - O YARN não é um sistema de arquivos distribuídos, mas sim um gerenciador de recursos e agendador de tarefas.

### 2.2 Ferramentas de Processamento
- Apache Spark: processamento em memória, mais rápido que o MapReduce; suporta batch e streaming.
- Apache Tez: motor de execução otimizado para consultas interativas, usado pelo Hive.
- Apache Flink: processamento de dados em streaming de baixa latência.

### 2.3 Ferramentas de Ingestão de Dados
- Apache Sqoop: importa/exporta dados entre Hadoop e bancos de dados relacionais.
- Apache Flume: coleta e movimenta grandes volumes de dados de log.
- Apache Kafka: plataforma de streaming para ingestão em tempo real.
- Apache NiFi: ingestão, roteamento e transformação de dados com interface gráfica.

> [!TIP] DICAS: 
> - O Apache Kafka é uma plataforma de código aberto usada para lidar com grandes volumes de dados de streaming em tempo real, porém não possui suporte nativo a machine learning.

### 2.4 Ferramentas de Armazenamento e Consulta
- Apache Hive: linguagem de consulta similar ao SQL (HiveQL), converte para MapReduce/Spark.
- Apache HBase: banco de dados NoSQL baseado em colunas, sobre o HDFS.
- Apache Impala: consultas SQL interativas de baixa latência.
- Apache Kudu: combina recursos de banco transacional e analítico.

### 2.5 Ferramentas de Análise e Ml
- Apache Mahout: algoritmos de aprendizado de máquina escaláveis.
- MLlib (Spark): biblioteca de machine learning do Spark.

### 2.6 Ferramentas de Orquestração e Workflow
- Apache Oozie: gerencia e agenda tarefas Hadoop.
- Apache Airflow: orquestração de workflows complexos.

> [!TIP] DICAS: 
> - O sistema de agendamento de WorkFlow para gerenciar os jobs de computação distribuída do MapReduce é o Oozie.

### 2.7 Ferramentas de Monitoramento
- Ambari: instalação, configuração e monitoramento de clusters Hadoop.
- Zookeeper: coordenação e sincronização de serviços distribuídos.

### 2.8 Módulos do Apache Hadoop
- O Apache Hadoop apresenta quatro módulos principais:
  - HDFS: sistema de arquivos distribuídos.
  - YARN: plataforma de gerenciamento de clusters e recursos.
  - MapReduce: modelo de computação paralela e processamento distribuído.
  - Hadoop Common: bibliotecas e utilitários comuns.

> [!TIP] DICAS: 
> - Os módulos YARN e MapReduce oferecem, respectivamente, plataforma de gerenciamento de clusters e processamento paralelo/distribuído.