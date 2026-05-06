# Anotações

# HADOOP – CONCEITOS, MAPREDUCE E ECOSSISTEMA

## 1. Apache Hadoop

### 1.1 Definição e Propósito

- ***Framework open source*** projetado para **armazenar e processar grandes volumes de dados de forma distribuída e escalável** em *clusters* de computadores.
- **Objetivo:** Lidar com os desafios de Big Data, dividindo carga de dados e processamento entre vários nós.
- **Características Principais:**
    - **Escalabilidade Horizontal:** Adiciona mais máquinas para aumentar a capacidade.
    - **Tolerância a Falhas:** Dados replicados em múltiplos nós.
    - **Baixo Custo:** Utiliza *hardware commodity* e *software* livre.
    - **Flexibilidade:** Suporta múltiplos tipos de dados.
- **Desvantagens:** Alta latência (processamento em lote, não tempo real), curva de aprendizado alta, configuração complexa.

### 1.2 HDFS (*Hadoop Distributed File System*)

- **Função:** Sistema de arquivos distribuído do Hadoop, responsável pelo **armazenamento** dos dados.
- **Arquitetura Mestre-Escravo:**
    - ***NameNode* (Mestre):** Gerencia os **metadados** (nomes de arquivos, diretórios, localização dos blocos). Não armazena dados reais.
    - ***DataNodes* (Escravos):** Armazenam efetivamente os **blocos de dados** e executam leitura/escrita.
- **Funcionamento:**
    - Arquivos são divididos em **blocos** (padrão 128/256 MB).
    - Cada bloco é **replicado** (padrão 3 cópias) em diferentes *DataNodes*, garantindo **alta disponibilidade e tolerância a falhas**.
    - Otimizado para acesso sequencial e processamento em **lote**.

## 2. MapReduce

### 2.1 Conceito e Fases

- **Definição:** Modelo de programação e *framework* para **processar grandes volumes de dados de forma distribuída e paralela** no Hadoop. É baseado no processamento em **disco**.
- **Fases do Processo:**
    1.  **Map (Mapeamento):**
        - **Entrada:** Um conjunto de dados (pares chave-valor).
        - **Função:** Processa, filtra e transforma os dados, dividindo o problema maior em subproblemas e gerando **pares chave-valor intermediários**.
    2.  **Shuffle & Sort (Baralhamento e Ordenação):**
        - Fase intermediária automática.
        - Agrupa e ordena todos os valores intermediários associados a uma mesma chave, preparando para o *Reduce*.
    3.  **Reduce (Redução):**
        - **Entrada:** Uma chave e sua lista de valores associados.
        - **Função:** Agrega, resume ou combina os valores, gerando o **resultado final**.

### 2.2 Características do MapReduce

- **Processamento em Lote (*Batch*):** Projetado para demandas de alta latência em grandes volumes, **NÃO** atende a cenários de baixa latência ou tempo real.
- **Paralelismo:** As fases *Map* e *Reduce* são executadas em paralelo nos diferentes nós do *cluster*.
- **Entrada e Saída:** Trabalha com arquivos armazenados no HDFS. A saída final é tipicamente menor que a entrada, pois agrega os dados.

## 3. Ecossistema Hadoop

### 3.1 Componentes e Ferramentas

| CATEGORIA | FERRAMENTA | FUNÇÃO PRINCIPAL |
| :--- | :--- | :--- |
| **Núcleo** | **HDFS** | Armazenamento distribuído. |
| **Núcleo** | **YARN** (*Yet Another Resource Negotiator*) | **Gerenciador de recursos e agendador de tarefas** do cluster. Não é um sistema de arquivos. |
| **Processamento** | **MapReduce** | Processamento em lote baseado em disco. |
| **Processamento** | **Apache Spark** | Processamento em **memória**, mais rápido, suporta lote e *streaming*. |
| **Processamento** | Apache Flink | Processamento *streaming* de baixa latência. |
| **Ingestão** | **Apache Sqoop** | Transfere dados entre **Hadoop e bancos relacionais** (baseado em lotes). |
| **Ingestão** | **Apache Kafka** | Plataforma de *streaming* para **ingestão em tempo real** (mensageria). |
| **Ingestão** | Apache Flume | Coleta e movimenta grandes volumes de dados de log. |
| **Consulta** | **Apache Hive** | *Data Warehouse* para consultas SQL-like (HiveQL) sobre Hadoop. |
| **Armazenamento** | **Apache HBase** | Banco de dados NoSQL orientado a colunas sobre o HDFS. |
| **Orquestração** | **Apache Oozie** | Agendador de *workflows* para gerenciar *jobs* MapReduce. |
| **Orquestração** | **Apache Airflow** | Orquestração de *pipelines* complexos. |
| **ML** | Apache Mahout, **MLlib** | Bibliotecas de *Machine Learning* escaláveis. |
| **Coordenação** | **Zookeeper** | Coordenação e sincronização de serviços distribuídos. |

## 4. Análise de Questões de Concurso

### 4.1 Função do Reduce (IV-UFG/Rio Branco/2024)

- **Enunciado:** Qual a principal função do componente “Reduce” no modelo MapReduce?
- **Gabarito:** **C) Agregar os resultados produzidos pelos mappers, realizando operações de síntese como somatória, contagem ou ordenação.**
- **Análise:** Esta é a definição precisa da fase *Reduce*. O *Map* divide/processa, o *Reduce* agrega.

### 4.2 YARN (CESPE/ANATEL/2024)

- **Enunciado:** "O YARN (Yet Another Resource Negotiator) é um sistema de arquivos distribuídos que faz parte do framework Hadoop."
- **Gabarito:** **ERRADO.**
- **Análise:** O YARN é o **gerenciador de recursos e agendador de tarefas**, não um sistema de arquivos. O sistema de arquivos distribuído é o **HDFS**.

### 4.3 Apache Sqoop vs. Kafka (FGV/TCE-RR/2025)

- **Enunciado:** Associar descrições: transferência de dados entre bancos relacionais e Hadoop; *streaming* de dados em tempo real.
- **Gabarito:** **E) 2 – 2 – 1 – 1.**
    - **(2) Apache Sqoop**: Transferência em lotes entre Hadoop e BD Relacionais.
    - **(1) Apache Kafka**: Plataforma de *streaming* para ingestão em tempo real.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/DATAPREV) | **B** | Hadoop = arquitetura distribuída HDFS + MapReduce. |
| **02** (FCPC/UFC) | **A** | Hadoop implementa o modelo MapReduce. |
| **03** (CETAP/BANPARÁ) | **E** | Modelo de programação para processamento distribuído em disco = MapReduce. |
| **04** (CESPE/TRF-6) | **E** | MapReduce é para alta latência (lote), não baixa latência. |
| **05** (CESPE/CTI) | **C** | MapReduce usa o HDFS para armazenar dados de entrada e saída. |
| **06** (CESPE/TRF-6) | **C** | MapReduce divide em Map e Reduce usando processamento paralelo. |
| **07** (CESPE/TRF-6) | **E** | MapReduce não é eficiente para baixa latência/tempo real. |
| **08** (FGV/TJ-RR) | **D** | Dividir, processar e combinar em paralelo = MapReduce. |
| **09** (FGV/TCE-PA) | **B** | Descrição do padrão de transformação em lote = Hadoop MapReduce. |
| **10** (FIOCRUZ) | **E** | Todas as afirmativas (HDFS, NoSQL, MapReduce) são verdadeiras. |
| **11** (UFG/Rio Branco) | **C** | Função do Reduce é agregar os resultados dos mappers. |
| **12** (CESGRANRIO/IPEA) | **A** | MapReduce = solução simplificada de processamento paralelo. |
| **13** (CESPE/ANATEL) | **E** | A saída do Reduce é agregada, não mantém a mesma quantidade de dados. |
| **14** (CETAP/BANPARÁ) | **A** | Apache Kafka é plataforma de streaming sem suporte nativo de ML. |
| **15** (FGV/TCE-RR) | **E** | Apache Sqoop (2) = BD Relacionais; Apache Kafka (1) = streaming. |
| **16** (CESPE/ANATEL) | **E** | YARN é gerenciador de recursos, não sistema de arquivos. |
| **17** (CS-UFG/TJ-AC) | **B** | Agendador de Workflow no Hadoop = Oozie. |
| **18** (UFG/Rio Branco) | **D** | YARN = gerenc. de clusters; MapReduce = processamento paralelo/distribuído. |