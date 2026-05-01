# Anotações

# BUSINESS INTELLIGENCE – ETL (EXTRAÇÃO, TRANSFORMAÇÃO E CARGA)

## 1. Definição e Propósito do ETL

- **ETL** é a sigla para **Extração, Transformação e Carga** (*Extract, Transform, Load*).
- É o processo fundamental para integrar dados de fontes heterogêneas, limpá-los, padronizá-los e carregá-los em um **Data Warehouse (DW)** ou **Data Mart**.
- O ETL é a "espinha dorsal" que alimenta o ambiente analítico, movendo dados do mundo operacional (OLTP) para o mundo de suporte à decisão (DW).

## 2. As Três Etapas do Processo ETL

### 2.1 Extração (*Extract*)

- **Objetivo:** Obter e ler os dados de diversas fontes de origem.
- **Fontes de Dados Comuns:**
    - Bancos de dados relacionais (OLTP).
    - Arquivos CSV, planilhas Excel.
    - APIs.
    - Sistemas ERP/CRM.
    - Logs, sistemas legados e fontes externas.
- **Mecanismo de Extração:**
    - **Carga Completa:** Todos os dados da fonte são extraídos (comum na primeira carga).
    - **Carga Incremental (Gradual):** Apenas os dados novos ou modificados desde a última extração são carregados.

### 2.2 Transformação (*Transform*)

- **Objetivo:** Realizar a limpeza, padronização e adequação dos dados às regras de negócio.
- **Local:** Esta etapa é realizada na ***Staging Area*** (Área de Estágio/Palco), uma área intermediária e temporária.
- **Principais Ações de Transformação:**
    - **Limpeza de Dados (*Data Cleansing*):** Tratar ruídos, dados duplicados, erros de formatação, valores ausentes (incompletude) e *outliers*.
    - **Padronização e Formatação:** Padronizar medidas, formatos e normalizar dados para uma mesma escala.
    - **Tradução de Valores Codificados:** Converter códigos (ex: 1=M, 2=F) para os formatos do DW.
    - **Enriquecimento de Dados:** Buscar dados em outras fontes para complementar informações.
    - **Geração de Chaves Substitutas (*Surrogate Keys*):** Criar chaves primárias artificiais para as tabelas do DW.
    - **Transformações de Dados:** Realizar agregações, cálculos de campos derivados e conversões de tipos de dados.
- **Observação:** A transformação é, geralmente, a etapa **mais complexa e demorada** do ETL.

### 2.3 Carga (*Load*)

- **Objetivo:** Inserir os dados transformados no repositório de destino final.
- **Destino:** Data Warehouse (DW) ou Data Mart.
- **Mecanismo:** Pode ser feita em lote (*batch*) ou, em cenários modernos, em tempo real.
- **Ações Finais:** Após a carga, podem ocorrer processos de validação, indexação e otimização dos dados no DW.

## 3. Análise de Questões de Concurso

### 3.1 O que é ETL (CESPE/MPE-AP/2021)

- **Enunciado:** "Tecnologias que recuperam dados de muitas fontes, limpando-os e carregando-os em data warehouse..."
- **Gabarito:** **B) ETL (Extract, Transform and Load).**
- **Análise:** Esta é a descrição funcional do processo ETL.

### 3.2 Complexidade do ETL (CESPE/MPC-SC/2022)

- **Enunciado:** "o ETL é considerado uma das fases mais simples, pois se resume à seleção dos dados..."
- **Gabarito:** **ERRADO**.
- **Análise:** O ETL é uma fase complexa, que vai muito além da seleção, envolvendo um profundo trabalho de limpeza, descoberta e transformação.

### 3.3 Local da Transformação (FCC/AL-MS/2016 e outros)

- **Enunciado:** Onde os dados são transformados?
- **Gabarito:** Na **Staging Area** (Área de Estágio).
- **Análise:** É a área de processamento intermediário entre as fontes e o DW, onde os dados são "estacionados" para serem trabalhados.

### 3.4 Natureza Sequencial do ETL (AOCP/MJSP/2020)

- **Enunciado:** "As ferramentas de ETL modernas são capazes de fazer a extração e a carga dos dados de forma simultânea".
- **Gabarito:** **ERRADO**.
- **Análise:** A sigla E-T-L indica um processo lógico e sequencial, não simultâneo.

### 3.5 Atribuição de Responsabilidades (Cespe/BANESE/2021)

- **Enunciado:** "ETL é um tipo de data integration com capacidades analíticas sofisticadas que permite que os dados sejam analisados...".
- **Gabarito:** **ERRADO**.
- **Análise:** A análise dos dados é feita por ferramentas de **OLAP e BI**, não pelo ETL. A função do ETL é preparar os dados, não analisá-los.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (FCC/TRT-14) | **D** | Processo para carregar o DW = ETL. |
| **2** (FCC/AL-AP) | **E** | Integrar bancos heterogêneos = ETL. |
| **3** (FCC/SÃO LUÍS) | **C** | Extrair de fontes heterogêneas para o DW = ETL. |
| **4** (CESPE/TJ-PA) | **D** | Extração e transformação em DW = ETL. |
| **5** (CESPE/MPE-AP) | **B** | Recuperar, limpar e carregar = ETL. |
| **6** (FCC/SANASA) | **C** | O retângulo entre as fontes e o DW = ETL. |
| **7** (FGV/ALERJ) | **A** | Ler, transformar e carregar = ETL. |
| **8** (CESPE/BANESE) | **E** | ETL não realiza análise de dados. |
| **9** (CESPE/TCE-RJ) | **E** | ETL não faz análise multidimensional. |
| **10** (CESPE/MPC-SC) | **E** | ETL não é uma fase simples. |
| **11** (AOCP/MJSP) | **C** | ETL extrai, limpa e carrega. |
| **12** (FUNDATEC/SPGG) | **B** | Etapa de obtenção de dados OLTP = Extração. |
| **13** (FCC/DPE-AM) | **B** | Transformação adequa os valores ao modelo do DW. |
| **14** (FCC/TERESINA) | **E** | Carga periódica pode ter intervalo de 24h. |
| **15** (CESGRANRIO/TRANSPETRO) | **B** | Área de transferência e transformação = Staging Area. |
| **16** (VUNESP/CAMPINAS) | **C** | Área intermediária do ETL = Staging. |
| **17** (CESPE/PGE-RJ) | **E** | OLTP é fonte, não staging. |
| **18** (CESPE/PETROBRAS) | **C** | Staging area é usada para processamento no ETL. |
| **19** (CESGRANRIO/TRANSPETRO) | **C** | Staging armazena dados para o processo. |
| **20** (FCC/AL-MS) | **E** | I = Staging; II = DW. |
| **21** (CESPE/PETROBRAS) | **E** | Dado incompleto = faltante, não fora do domínio. |
| **22** (**ANULADA**) | **A** | Todos os itens são tarefas de preparação. |
| **23** (FCC/TRE-SP) | **A** | Tradução e chaves substitutas = Transformação. |
| **24** (CESPE/SEFAZ-RS) | **C** | Definir regras para formatação adequada dos dados. |