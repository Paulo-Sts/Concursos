# Anotações

# INGESTÃO DE DADOS E PIPELINE

## 1. Ingestão de Dados

### 1.1 Conceito e Fontes

- **Definição:** Processo de **coletar e importar dados** de diversas fontes para um sistema de armazenamento ou processamento (Data Lake, Data Warehouse, etc.).
- **Objetivo:** Garantir que os dados de múltiplas origens estejam **centralizados e disponíveis** para análise.
- **Fontes Comuns:** Bancos de dados (SQL, NoSQL), APIs, arquivos (CSV, XML, JSON), *streams* de eventos (ex: **Apache Kafka**), sistemas corporativos (ERP, CRM), sensores IoT.

### 1.2 Tipos de Ingestão

| CARACTERÍSTICA | INGESTÃO EM LOTE (*BATCH*) | INGESTÃO EM *STREAMING* (TEMPO REAL) |
| :--- | :--- | :--- |
| **Funcionamento** | Dados são acumulados e processados em **grandes blocos** e intervalos programados. | Dados são processados **continuamente e incrementalmente** à medida que são gerados. |
| **Vantagem Principal** | Otimiza recursos (processamento fora do horário de pico). | **Baixa latência**; ideal para decisões em tempo real. |
| **Desvantagem Principal** | Dados não ficam disponíveis imediatamente (latência alta). | Exige infraestrutura robusta e especializada. |
| **Exemplo de Uso** | Análises históricas, atualização diária de vendas em um DW. | Monitoramento de tráfego, transações financeiras, sensores IoT. |
| **Ferramentas Típicas** | Apache Sqoop, Talend. | **Apache Kafka**, Apache Flume, AWS Kinesis. |

## 2. Pipeline de Dados

### 2.1 Conceito e Componentes

- **Definição:** Conjunto organizado e automatizado de **etapas e processos** que conduzem os dados desde a sua coleta (ingestão) até o consumo final. É a "linha de produção" dos dados.
- **Componentes Essenciais:**
    1.  **Ingestão de Dados:** Captura dos dados brutos das fontes (em lote ou *streaming*).
    2.  **Armazenamento Bruto:** Depósito inicial no formato original (ex: Data Lake, HDFS, S3).
    3.  **Processamento e Transformação:** Limpeza, padronização, enriquecimento e aplicação de regras de negócio. Pode usar ferramentas como **Apache Spark**.
    4.  **Armazenamento Estruturado:** Dados prontos vão para repositórios otimizados para consulta (ex: DWs como Snowflake, BigQuery).
    5.  **Consumo e Visualização:** Dashboards, relatórios e modelos de ML (ex: Tableau, Power BI).
    6.  **Orquestração e Automação:** Coordena a ordem de execução das tarefas (ex: **Apache Airflow**).
    7.  **Monitoramento e Governança:** Rastreia desempenho, qualidade e segurança (conformidade com LGPD).

### 2.2 Tipos de Pipeline

- ***Batch Pipeline***: Processa grandes blocos em intervalos programados.
- ***Streaming Pipeline***: Processa eventos em tempo real, com baixa latência.
- ***Lambda Architecture***: Combina processamento em lote e em *streaming*.
- ***Kappa Architecture***: Foca apenas em *pipelines* de *streaming* unificados.

## 3. Análise de Questões de Concurso

### 3.1 Conceitos de Ingestão (FGV/TJ-RR/2024)

- **Enunciado:** Avaliar afirmativas sobre ingestão em lote e em tempo real.
- **Gabarito:** **C) III, apenas.**
- **Análise:**
    - **I (Errada):** A ingestão **em lote** é que se dá de forma programada, não contínua.
    - **II (Errada):** A ingestão **em tempo real** é que processa continuamente, e não em massa e blocos.
    - **III (Certa):** Em ambos os métodos é comum que haja transformação e validação para garantir precisão e consistência.

### 3.2 Aplicação de Ingestão em Tempo Real (CESGRANRIO/IPEA/2024)

- **Enunciado:** Exemplo em que a ingestão em lote **NÃO** é vantajosa.
- **Gabarito:** **D) monitoramento e gerenciamento de tráfego urbano ou de fenômenos climáticos.**
- **Análise:** Para análises históricas e relatórios, o lote é suficiente. Para cenários que exigem resposta imediata a eventos que estão acontecendo agora (tráfego, clima), a ingestão em tempo real é mandatória.

### 3.3 Definição de Pipeline (CESPE/ANATEL/2024)

- **Enunciado:** "Pipelines de dados apresentam uma única estrutura para o recebimento dos dados originados de uma fonte não confiável."
- **Gabarito:** **ERRADO**.
- **Análise:** O pipeline não é uma estrutura única e simples; é um conjunto complexo de múltiplas etapas interligadas (ingestão, transformação, armazenamento, etc.).

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (QUADRIX/CFBIO) | **C** | A camada de ingestão coleta e carrega dados para o Data Lake. |
| **02** (CESPE/MPE-GO) | **C** | Ingestão deve ser escalável, rápida, confiável e segura. |
| **03** (FGV/TJ-RR) | **C** | Apenas III correta: transformação e validação são comuns em ambos os métodos. |
| **04** (QUADRIX/NOVACAP) | **C** | Ingestão é a fase de coleta de dados de diversas fontes. |
| **05** (CESGRANRIO/IPEA) | **B** | *Streaming* = dados capturados e processados continuamente. |
| **06** (FGV/TCE-PA) | **D** | V, V, F, F. (Ingestão incremental de streaming aumenta o tráfego). |
| **07** (CESGRANRIO/IPEA) | **D** | Monitoramento de tráfego e clima exigem tempo real (não lote). |
| **08** (CESPE/ANATEL) | **E** | Pipeline não é uma estrutura única simples. |
| **09** (CESPE/SEPLAG-CE) | **C** | Pipeline refina e limpa dados brutos para facilitar o uso. |
| **10** (CESPE/TRF-6) | **C** | Na ingestão, dados são coletados e transportados para armazenamento centralizado. |