# Anotações

# BIG DATA – INTRODUÇÃO E CONCEITOS

## 1. Definição e Propósito do Big Data

### 1.1 O que é Big Data

- **Definição:** Conjunto de **métodos, tecnologias e processos** voltados para lidar com dados massivos, que se caracterizam por grande **volume**, alta **velocidade** e grande **variedade**.
- **Diferencial:** São dados que as **ferramentas tradicionais** de processamento **não conseguem gerenciar** de forma eficiente. O Big Data não se refere apenas ao dado em si, mas a toda uma arquitetura de coleta, armazenamento e processamento.
- **Objetivo Principal:** **Extrair valor e gerar conhecimento** a partir de dados (estruturados ou não) para embasar decisões estratégicas e criar **vantagens competitivas**.

## 2. Contexto e Infraestrutura

### 2.1 Origem e Evolução

- Surgiu com a explosão de dados da internet, redes sociais, dispositivos móveis e sensores (IoT).
- Impulsionado pelo avanço de tecnologias de **armazenamento e processamento distribuído** (ex: Hadoop, Spark), bancos NoSQL e computação em nuvem.

### 2.2 Conceitos de Infraestrutura

- **Computação Distribuída (*Cluster*):** Em vez de um único computador, utiliza-se um grupo de computadores interligados que trabalham juntos, dividindo os dados e o processamento.
- **Escalabilidade Horizontal:** Capacidade de aumentar o poder computacional **adicionando mais máquinas** ao *cluster*. É o modelo fundamental do Big Data.
- **Escalabilidade Vertical:** Aumentar a capacidade de uma **única máquina** (adicionando mais RAM, CPU, HD). É o modelo tradicional.

## 3. Tecnologias e Modelos de Processamento

### 3.1 Principais Tecnologias

- **Armazenamento e Processamento Distribuído:** **Apache Hadoop**, **Apache Spark**.
- **Bancos NoSQL:** MongoDB, Cassandra, HBase (flexíveis e distribuídos).
- **Ingestão de Dados:** Apache Kafka, Flume.
- **Análise e Visualização:** Tableau, Power BI, Kibana.

### 3.2 Modelos de Processamento

- **Processamento em Lote (*Batch Processing*):** Grandes volumes de dados são processados em intervalos definidos (ex: uma vez por dia).
- **Processamento em *Streaming* (Fluxo Contínuo):** Os dados são processados de forma contínua e incremental, assim que chegam. Ideal para dados em tempo real.

## 4. Características Técnicas (Além dos 3 Vs)

- **Processamento Distribuído:** Dados armazenados e processados em múltiplos nós/servidores.
- **Escalabilidade Horizontal:** Adição de novos servidores para aumentar capacidade.
- **Alta Disponibilidade:** Arquiteturas tolerantes a falhas, com replicação e recuperação automática.
- **Baixa Latência em Streaming:** Análise de dados contínuos com baixa demora.
- **Capacidade de Integração:** Conexão com múltiplas fontes (APIs, sensores, logs, redes sociais).
- **Flexibilidade de Modelagem:** Uso de modelos não relacionais (NoSQL) com esquemas flexíveis (*schema-on-read*).
- **Segurança e Governança:** Controle de acesso, criptografia e conformidade legal (LGPD).

## 5. Análise de Questões de Concurso

### 5.1 Diferencial Competitivo (IBFC/TRF-5/2024)

- **Enunciado:** Um dos principais objetivos do uso de big data nas empresas.
- **Gabarito:** **B) Aumentar a eficiência e alcançar resultados que proporcionem um diferencial competitivo.**
- **Análise:** O foco não é apenas armazenar, e sim **gerar valor** e vantagem no mercado.

### 5.2 Infraestrutura Necessária (FGV/TJ-MS/2024)

- **Enunciado:** Para implementar bancos de dados massivos (Big Data), é necessário:
- **Gabarito:** **D) infraestrutura computacional escalável.**
- **Análise:** O Big Data prescinde de uma infraestrutura que possa crescer horizontalmente para lidar com o volume e a velocidade crescentes. Esquema pré-definido e dados apenas estruturados são conceitos de bancos relacionais tradicionais.

### 5.3 Capacidades da Solução (FGV/CVM/2024)

- **Enunciado:** As soluções de Big Data para análise de dados devem ter a capacidade de:
- **Gabarito:** **A) processar dados heterogêneos, de alto volume e alta velocidade, utilizando estruturas computacionais aprimoradas para a automação de processos e tomadas de decisão.**
- **Análise:** A alternativa descreve precisamente o tratamento dos 3 Vs (Volume, Velocidade, Variedade) com o objetivo de gerar valor para a decisão.

## 6. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESPE/FUNPRESP-EXE) | **C** | Grandes volumes revelam padrões valiosos para análises preditivas. |
| **02** (CESPE/TRF-6) | **C** | Visualizações permitem rápida identificação de padrões. |
| **03** (CESPE/INSA) | **C** | Big data é usado para mapear comportamento de consumidores. |
| **04** (IBFC/TRF-5) | **D** | Dados de transações de aplicativos financeiros contribuem para Big Data. |
| **05** (IBFC/TRF-5) | **B** | Objetivo principal é aumentar a eficiência e proporcionar diferencial competitivo. |
| **06** (IVIN/S. Domingos) | **D** | O conjunto de técnicas para analisar grande quantidade de dados é o Big Data. |
| **07** (INST. ACCESS/CEASA-ES) | **D** | Beneficia a organização melhorando a personalização do atendimento. |
| **08** (FGV/CVM) | **A** | Processar dados heterogêneos, de alto volume e alta velocidade. |
| **09** (FGV/TJ-MS) | **D** | É necessária infraestrutura computacional escalável. |
| **10** (INST. ACCESS/INT) | **A** | Texto descreve o conceito de Big Data. |
| **11** (CESPE/CTI) | **C** | Big Data são dados que softwares tradicionais não conseguem gerenciar. |