# Anotações

# BUSINESS INTELLIGENCE – ETL II (ELT E DATA LAKE)

## 1. Conceito de ELT (Extração, Carga e Transformação)

### 1.1 Definição e Diferença Fundamental

- **ELT** é a sigla para **Extração, Carga e Transformação** (*Extract, Load, Transform*).
- É uma alternativa mais recente ao ETL, que surgiu como um complemento.
- **Diferença Fundamental:** No ELT, a **ordem das etapas é invertida**. A **carga** dos dados brutos no repositório de destino (como um *Data Lake*) ocorre **antes da transformação**. A transformação é feita diretamente no ambiente de destino, sob demanda.

### 1.2 Benefícios do ELT

- **Foco em Grandes Bases:** Mais adequado para *Big Data* e dados semiestruturados/não estruturados.
- **Redução do Tempo de Carga:** Tempos menores de carregamento e de transformação, resultando em menor custo de manutenção.
- **Disponibilidade dos Dados:** Os dados brutos ficam disponíveis de forma mais rápida.
- **Flexibilidade:** O esquema é "lido" no momento da análise (*schema-on-read*), permitindo múltiplas interpretações dos dados brutos.
- **Adaptado a Data Lakes:** Ideal para este tipo de repositório.

### 1.3 Desvantagens do ELT

- *Pipelines* com menos maturidade.
- Menos profissionais habilitados.
- Análises podem ser mais demoradas e menos estáveis em comparação com dados pré-modelados.

## 2. Data Lake

### 2.1 Definição e Características

- **Data Lake** é um tipo de **repositório de armazenamento** que guarda **grandes volumes de dados** em seu formato bruto (não refinado).
- Diferentemente do DW, não exige um esquema ou modelo de dados predefinido para armazenar os dados.
- Aplica-se o conceito de ***Schema-on-Read*** (Esquema na Leitura): os dados são armazenados sem um esquema fixo, e a estrutura é aplicada apenas no momento da consulta/análise.
- Utiliza dados de fontes variadas, incluindo dados não relacionais e relacionais.

### 2.2 Data Lake vs. Data Warehouse (DW)

| CARACTERÍSTICA | DATA WAREHOUSE (DW) | DATA LAKE (DL) |
| :--- | :--- | :--- |
| **Dados** | Altamente selecionados e refinados (versão central da verdade). | Brutos, em formato nativo, podendo ser estruturados, semi ou não-estruturados. |
| **Esquema** | *Schema-on-Write* (Esquema gravado no momento da carga). | ***Schema-on-Read*** (Esquema aplicado na análise). |
| **Propósito** | Responder a perguntas de negócio específicas e análises de BI. | Exploração de dados, *Data Science*, *Machine Learning*. |
| **Fontes de Dados** | Principalmente dados relacionais e estruturados. | IoT, mídias sociais, aplicações móveis, logs. |

## 3. Análise de Questões de Concurso

### 3.1 Vantagens do ELT sobre ETL (CESPE/SEFAZ-CE/2021)

- **Enunciado:** Vantagens do ELT sobre ETL.
- **Gabarito:** **Certo.** Tempos menores de carregamento e transformação e menor custo de manutenção são benefícios reais do ELT.

### 3.2 Definição de Data Lake (FUNDATEC/BRDE/2023)

- **Enunciado:** Associar características a DW ou DL.
- **Gabarito:** **D) DL – DW – DL – DW.**
    - "Esquema de leitura": **DL**.
    - "Versão central da verdade": **DW**.
    - "Dados de IoT, mídia social": **DL**.
    - "Relatórios em lote e visualizações rápidas": **DW**.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/MC) | **E** | ETL não é mais rápido que o ELT para grandes volumes. |
| **2** (CESPE/BNB) | **E** | Data Lake não exige dados refinados previamente. |
| **3** (CESPE/MC) | **E** | Data Lake não armazena sob um esquema comum unificado. |
| **4** (CESPE/SEFAZ-CE) | **C** | ELT = tempos menores de carga e transformação, menor custo. |
| **5** (FUNDATEC/BRDE) | **D** | DL -> Esquema de Leitura e Dados de IoT; DW -> Versão da Verdade e Relatórios. |