# Anotações

# DATA LAKE

## 1. Conceito e Definição

### 1.1 O que é um Data Lake

- **Definição:** Um **repositório centralizado** que permite armazenar **grandes volumes de dados** em seu **formato bruto (raw data)** e original, sem a necessidade de pré-processamento ou estruturação.
- **Tipos de Dados Suportados:** Aceita dados **estruturados** (tabelas), **semiestruturados** (JSON, XML, logs) e **não estruturados** (vídeos, áudios, imagens, texto livre).

### 1.2 Data Lake vs. Data Warehouse

A principal diferença entre os dois repositórios reside na abordagem do esquema de dados.

| CARACTERÍSTICA | DATA LAKE | DATA WAREHOUSE (DW) |
| :--- | :--- | :--- |
| **Tipo de Esquema** | ***Schema-on-Read*** (Esquema na Leitura). A estrutura é aplicada apenas no momento da análise. | ***Schema-on-Write*** (Esquema na Escrita). Os dados são estruturados e transformados antes de serem carregados. |
| **Formato dos Dados** | Armazena dados **brutos** e não processados. | Armazena dados **processados, limpos e estruturados**. |
| **Tipo de Análise** | Suporte para Big Data Analytics, ML, IA e exploração de dados. | Análises gerenciais, dashboards de BI e consultas OLAP. |
| **Flexibilidade** | **Alta**. Adaptável a diferentes tipos de análise. | **Baixa/Média**. Otimizado para análises predefinidas. |

## 2. Características, Arquitetura e Desafios

### 2.1 Principais Características

- **Armazenamento de Qualquer Tipo de Dado:** Aceita formatos estruturados, semiestruturados e não estruturados em sua forma nativa.
- **Escalabilidade:** Geralmente horizontal, crescendo conforme a demanda, principalmente em ambientes de nuvem.
- **Baixo Custo de Armazenamento:** Uso de hardware *commodity* ou serviços de nuvem com pagamento por uso.
- **Flexibilidade:** Não exige um esquema pré-definido para a ingestão de dados.

### 2.2 Arquitetura e Funcionamento

1.  **Ingestão:** Os dados são coletados de múltiplas fontes (sensores, sistemas corporativos, APIs) e enviados ao Data Lake, seja em **lote (*batch*)** ou em ***streaming*** (tempo real).
2.  **Armazenamento:** Os dados permanecem em seu formato bruto até que sejam necessários.
3.  **Processamento:** A limpeza, transformação e estruturação (*schema-on-read*) ocorrem quando os dados são lidos para uma análise específica.
4.  **Consumo:** Cientistas e analistas de dados acessam os dados já processados (ex: *datasets*) para criar modelos de *Machine Learning*, relatórios e análises exploratórias.

### 2.3 Tecnologias Utilizadas

- ***On-Premises* (Local):** Frequentemente utiliza o **HDFS** (*Hadoop Distributed File System*).
- **Nuvem:** Serviços como **Amazon S3**, **Azure Data Lake Storage** e **Google Cloud Storage**.

### 2.4 Desafios e Riscos

- **Governança de Dados:** Sem controle e um catálogo de dados adequado, o Data Lake pode se tornar um “***Data Swamp***” (pântano de dados), um depósito caótico e inútil.
- **Segurança:** Necessidade de políticas de acesso, criptografia e auditoria.
- **Qualidade da Informação:** Dados brutos podem conter inconsistências ou redundâncias.

## 3. Análise de Questões de Concurso

### 3.1 Características do Data Lake (CONSULPAM/CONAB/2025)

- **Enunciado:** Traz características inerentes ao Data Lake.
- **Gabarito:** **A) Apenas I e III.**
- **Análise:**
    - **I. Suporta tipos de dados estruturados, semiestruturados e não estruturados:** **Correto.**
    - **II. Custo de armazenamento elevado:** **Incorreto.** O custo é geralmente mais baixo.
    - **III. Os dados são interpretados no momento da leitura:** **Correto.** É o conceito de *schema-on-read*.
    - **IV. Apresenta flexibilidade baixa/moderada:** **Incorreto.** A flexibilidade é alta.

### 3.2 Coexistência de Modelos (CESPE/TRF-6/2025)

- **Enunciado:** "Os data lakes [...] eliminam completamente a necessidade de data warehouses em ambientes de Big Data."
- **Gabarito:** **ERRADO.**
- **Análise:** Data Lakes e Data Warehouses têm propósitos diferentes e **podem coexistir** em uma mesma organização, complementando-se.

### 3.3 Suporte a Dados Semiestruturados (CESPE/MPE-CE/2025)

- **Enunciado:** "Embora os data lakes possam armazenar dados estruturados [...], eles não oferecem suporte para dados semiestruturados e não estruturados."
- **Gabarito:** **ERRADO.**
- **Análise:** Uma das características principais do Data Lake é exatamente oferecer suporte a **todos** esses tipos de dados.

### 3.4 Necessidade de Governança (CESPE/ANATEL/2024)

- **Enunciado:** "Em um data lake, os dados são depositados em estado bruto, sem terem passado por qualquer análise e mesmo sem terem uma governança."
- **Gabarito:** **CERTO**. (Em relação ao depósito em estado bruto). Porém, a ausência de governança transforma o repositório em um *Data Swamp*.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CONSULPAM/CONAB) | **A** | Data Lake suporta vários tipos de dados e interpreta na leitura (schema-on-read). |
| **02** (CONSULPLAN/TJ-R) | **A** | Todas as definições sobre tipos de dados e Data Lake estão corretas. |
| **03** (CESPE/TRF-6) | **E** | Data Lake não elimina a necessidade de um Data Warehouse. |
| **04** (CESPE/MPE-CE) | **E** | Data Lake oferece suporte a dados semi e não estruturados. |
| **05** (CESPE/TRT-10) | **C** | Característica do Data Lake: armazenar diferentes tipos de dados sem esquema prévio. |
| **06** (QUADRIX/CFP) | **E** | Data Lake é flexível, não possui estrutura rigidamente definida. |
| **07** (QUADRIX/CFP) | **C** | Suporta dados estruturados e não estruturados em sua forma original. |
| **08** (FGV/DATAPREV) | **D** | Vantagem de usar IA/ML com DL é a liberdade de usar dados brutos para análises precisas. |
| **09** (CESPE/TCE-AC) | **E** | Aplicações de Data Lake podem ser abrigadas na mesma plataforma. |
| **10** (CESPE/ANATEL) | **C** | Dados brutos sem governança viram um Data Swamp. |
| **11** (CESPE/SEBRAE) | **D** | Todos os itens (I, II e III) estão certos. |
| **12** (CESPE/MPO) | **C** | Data Lake não oferece visão multidimensional; isso é função do DW. |
| **13** (QUADRIX/NOVACAP) | **C** | Definição correta de Data Lake. |
| **14** (FGV/CVM) | **B** | Repositório para dados no formato original = Data Lake. |
| **15** (QUADRIX/COREN-PR) | **E** | Data Lake não utiliza exclusivamente armazenamento em nuvem. |
| **16** (CESPE/TSE) | **E** | Data Lake não requer que os dados sejam estruturados antes. |
| **17** (FUNDATEC/SIMAE) | **E** | Definição de Data Lake como repositório centralizado de dados em forma original. |
| **18** (IMPARH/Fortaleza) | **D** | Somente a afirmação II (schema-on-read) está correta. |
| **19** (CESPE/MPE-TO) | **E** | Formatos citados são não estruturados; Data Lake armazena ambos os tipos. |