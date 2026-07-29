# Anotações

# BUSINESS INTELLIGENCE – COMPONENTES DA ARQUITETURA

## 1. Arquitetura Geral de um Sistema de BI

### 1.1 Componentes Essenciais do Fluxo de BI

- **Fontes de Dados (Origem):** Sistemas de origem (OLTP), planilhas, APIs, dados externos. É o ambiente operacional que alimenta o BI.
- **ETL (Extração, Transformação e Carga):** Camada responsável por extrair dados das fontes, transformá-los (limpeza, padronização, integração) e carregá-los no repositório analítico.
- ***Data Warehouse* (DW) / *Data Mart***: Repositório central de dados analíticos, modelados de forma dimensional (tabelas Fato e Dimensão). Considerado o "coração" do BI.
- **Ferramentas de Análise e Relatórios:** Conjunto de tecnologias para manipular, minerar e analisar os dados. Isso inclui a **Análise de Negócio (*Business Analytics*)** e ferramentas OLAP.
- **Interface do Usuário (Visualização):** Camada de apresentação (dashboards, portais, relatórios) que fornece capacidade visual interativa para os tomadores de decisão. Inclui também o **BPM (*Business Performance Management*)** para monitorar indicadores.

### 1.2 Detalhamento dos Componentes

- ***Data Warehouse***: Repositório de dados granulares e integrados.
- ***Business Analytics* (Análise de Negócio):** Coleção de ferramentas para manipular, minerar e analisar os dados no DW.
- ***Business Performance Management* (BPM):** Monitora e analisa indicadores de desempenho.
- **Interface do Usuário:** Fornece capacidade visual (dashboard, portal, cockpit) para os tomadores de decisão.

## 2. Análise de Questões de Concurso

### 2.1 Componentes da Arquitetura de BI (FGV/SEFAZ-AM/2022)

- **Enunciado:** Assinale a opção que apresenta os principais componentes da arquitetura de um sistema de BI.
- **Gabarito Oficial:** **D) Data warehouse, análise de negócio, business process management e interfaces do usuário.**
- **Análise:** Segundo a literatura que a banca se baseou, o DW, a Análise de Negócio, o BPM e as interfaces de usuário são os componentes principais da arquitetura.

### 2.2 Análise de Negócio (CESPE/MPE-AP/2021)

- **Enunciado:** Em um sistema de BI, a coleção de ferramentas utilizada como componente para manipular, minerar e analisar os dados no DW denomina-se:
- **Gabarito:** **C) Análise de Negócio (*Business Analytics*).**
- **Análise:** É a definição precisa do componente responsável por essa função analítica.

### 2.3 Componentes de um Data Warehouse (FGV/CGE-SC/2023)

- **Enunciado:** Avalie se os componentes de um Data Warehouse se incluem: I- Sistemas de origem; II- Infraestrutura de ETL; III- Data Warehouse; IV- Aplicações de Front-end.
- **Gabarito:** **E) I, II, III e IV.**
- **Análise:** O ambiente de Data Warehousing, que suporta o BI, é composto por todos esses quatro elementos principais.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (FGV/SEFAZ-AM/2022) | **D** | DW, Análise de Negócio, BPM e Interface do Usuário. |
| **2** (CESPE/MPE-AP/2021) | **C** | Ferramentas para manipular/minerar dados = Análise de Negócio. |
| **3** (VUNESP/MPE-SP/2016) | **C** | DW é o "coração" do BI. |
| **4** (FGV/CGE-SC/2023) | **E** | Todos são componentes de um DW. |