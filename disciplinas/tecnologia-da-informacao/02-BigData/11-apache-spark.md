# Anotações

# APACHE SPARK

## 1. Conceito e Propósito do Apache Spark

- **Definição:** *Framework* de código aberto para **computação distribuída e processamento de dados em larga escala** em *clusters* de computadores.
- **Característica Principal:** Utilização intensiva da **memória RAM** para processamento, o que o torna muito mais rápido que o modelo baseado em disco (MapReduce).
- **Linguagem de Desenvolvimento:** Escrito em **Scala**.
- **APIs de Alto Nível:** Suporta programação em **Java, Scala, Python e R**.
- **Observação:** O Spark **não possui sistema gerenciador de arquivos próprio**. Ele depende de sistemas de armazenamento como HDFS, Cassandra, HBase ou sistemas de arquivos tradicionais para persistir os dados.

## 2. Principais Módulos do Spark

| MÓDULO | FUNÇÃO PRINCIPAL |
| :--- | :--- |
| **Spark Core** | Módulo principal, motor de processamento distribuído. |
| **Spark SQL** | Processamento de dados **estruturados** via consultas SQL/HiveQL. |
| **Spark Streaming** | Processamento de dados em **tempo real** (*streaming*). |
| **MLlib** | Biblioteca de **Aprendizado de Máquina** (*Machine Learning*). |
| **GraphX** | Processamento de **grafos** em paralelo. |
| **SparkR / PySpark** | APIs para processamento com as linguagens **R** e **Python**, respectivamente. |

## 3. RDD (*Resilient Distributed Dataset*)

- **Definição:** É a **principal abstração** do modelo de programação do Spark. Representa uma coleção imutável e particionada de objetos distribuídos ao longo do *cluster*, que pode ser processada em paralelo.
- **Características Fundamentais:**
    - **Imutável:** Uma vez criado, não pode ser modificado. Para processá-lo, é gerado um novo RDD.
    - ***Resiliente* (Tolerante a Falhas):** Em caso de falha em uma partição, o RDD pode ser **reconstruído** a partir de sua **linhagem (*lineage*)**. A linhagem registra todas as transformações que o originaram.
    - **Distribuído:** Seus dados são particionados e armazenados em memória (ou discos) nos vários nós do *cluster*.
    - **Suporte a Tipos:** Pode armazenar tipos primitivos, sequências, objetos Scala/Java ou tipos mistos.
- **Operações sobre RDDs:**
    - **Transformações:** Operações *lazy* (preguiçosas) que **criam um novo RDD** a partir de um existente. Não executam imediatamente, apenas registram a operação na linhagem (ex: `map`, `filter`, `flatMap`, `distinct`).
    - **Ações:** Operações que **retornam um valor** ao *Driver Program* ou gravam em armazenamento. Disparam a execução de todas as transformações anteriores (ex: `count`, `collect`, `take`, `saveAsTextFile`, `reduce`).

## 4. Análise de Questões de Concurso

### 4.1 Spark vs. Hadoop (INSTITUTO AOCP/MJSP/2020)

- **Enunciado:** Tecnologia com suporte ao processamento em tempo real de Big Data.
- **Gabarito:** **D) Spark.**
- **Análise:** O Hadoop (com MapReduce) é para processamento em lote (*batch*). O Spark (com Spark Streaming) é a tecnologia que suporta processamento em tempo real.

### 4.2 Gerenciamento de Arquivos (IADES/ADASA/2022)

- **Enunciado:** "[O Apache Spark] Não possui um sistema gerenciador de arquivos próprio, dependendo de outras plataformas para isso, como o Hadoop."
- **Gabarito:** Alternativa correta (Letra E).
- **Análise:** Esta é uma característica distintiva importante do Spark. Ele foca no processamento em memória e delega o armazenamento a outros sistemas, sendo o HDFS do Hadoop o mais comum.

### 4.3 Abstrações de Programação (FGV/SEFAZ-MG/2023)

- **Enunciado:** "Spark provê três principais abstrações para a programação paralela: RDDs, operações paralelas, e operações de comunicação."
- **Gabarito:** **Incorreta (Item B)**.
- **Análise:** Esta foi a exceção. A principal abstração do Spark é o **RDD**. As operações sobre RDDs existem, mas a assertiva listava-as como as três principais abstrações do modelo, o que não é preciso.

### 4.4 Operações de Transformação (FUNDATEC/AGERGS/2022)

- **Enunciado:** São exemplos de operações de transformação, EXCETO:
- **Gabarito:** **D) Joinstep.**
- **Análise:** `map`, `filter` e `flatMap` são todas transformações válidas no Spark. `Joinstep` é o termo que não corresponde a uma operação Spark real.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (AOCP/MJSP/2020) | **D** | Spark = processamento em tempo real. |
| **2** (FUNDATEC/AGERGS/2022) | **A** | Todas as assertivas sobre Spark estão corretas. |
| **3** (CESPE/SEFAZ-AL) | **E** | Spark foi escrito em Scala, não em Fortran. |
| **4** (IADES/ADASA/2022) | **E** | Spark não possui sistema de arquivos próprio. |
| **5** (FUNDATEC/AGERGS/2022) | **A** | Todas as assertivas sobre módulos do Spark estão corretas. |
| **6** (FGV/SEFAZ-MG/2023) | **B** | A principal abstração do Spark é o RDD, não as três listadas. |
| **7** (FUNDATEC/AGERGS/2022) | **E** | RDDs podem armazenar qualquer tipo de elemento. |
| **8** (FGV/SEFAZ-MG/2023) | **E** | Transformações são preguiçosas (lazy) e só computadas quando uma ação é chamada, mas a alternativa E continha uma imprecisão na forma como descreveu o gatilho. |
| **9** (FUNDATEC/AGERGS/2022) | **D** | `Joinstep` não é uma operação de transformação do Spark. |