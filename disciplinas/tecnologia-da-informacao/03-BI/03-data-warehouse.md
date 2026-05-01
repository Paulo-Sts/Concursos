# Anotações

# BUSINESS INTELLIGENCE – DATA WAREHOUSE (DW)

## 1. Definição e Propósito do Data Warehouse

### 1.1 O que é um Data Warehouse (DW)

- **Definição:** Repositório centralizado e integrado de **dados estruturados**, projetado para suportar a **análise e a geração de relatórios**, fornecendo uma visão consolidada e histórica.
- **Propósito Fundamental:** Proporcionar um ambiente que permita realizar a **análise dos negócios** com base nos dados armazenados, visando **embasar e agilizar tomadas de decisão** nos níveis **gerencial e estratégico**.
- **Contexto no BI:** O DW é o "coração" da arquitetura de BI. Ele transforma dados operacionais em informação voltada à decisão estratégica.

### 1.2 DW vs. Banco de Dados Transacional (OLTP)

| CARACTERÍSTICA | DATA WAREHOUSE (DW) | BANCO TRANSACIONAL (OLTP) |
| :--- | :--- | :--- |
| **Orientação** | Orientado a **assuntos** de análise (ex: vendas, impostos). | Orientado a **aplicações**/processos de negócio (ex: cadastro de cliente, pedido). |
| **Nível de Uso** | Níveis **gerencial e estratégico** (tomada de decisão). | Nível **operacional** (transações do dia a dia). |
| **Dados** | Armazena dados **sumarizados** e históricos. | Armazena dados **detalhados** e atuais. |
| **Volatilidade** | **Não volátil** (dados são estáveis, apenas leitura). | **Volátil** (os dados sofrem constantes alterações, inserções e exclusões). |
| **Variabilidade no Tempo** | **Variável no tempo** (mantém um histórico de longos períodos). | Reflete o estado atual do negócio. |

## 2. Características Fundamentais do DW (as 4 Características)

### 2.1 As Quatro Características Essenciais

- **Orientado a Assuntos (*Subject-Oriented*):** Os dados são organizados pelos principais assuntos de análise do negócio (ex: vendas, finanças, clientes), e não pelos processos operacionais.
- **Integrado (*Integrated*):** Os dados de múltiplas fontes (sistemas transacionais, planilhas, fontes externas) são padronizados, limpos e integrados em um formato comum e consistente.
- **Não Volátil (*Non-Volatile*):** Após os dados serem inseridos no DW, eles **não podem ser alterados** pelos usuários. O acesso é focado em **consultas e leitura**, não em modificações da informação histórica.
- **Variável no Tempo (*Time-Variant*):** O DW mantém um **histórico de dados** por longos períodos (muito maiores que os sistemas transacionais), permitindo análises de séries temporais e evolução de valores.

> ### 2.1.1 Questão FCC/SEFAZ-BA (2019)
- Devido à **não volatilidade**, os dados no DW não podem ser alterados, não havendo necessidade de bloqueio por concorrência de usuários ao seu acesso.

## 3. Funcionamento e Utilização

### 3.1 Processo de Construção e Uso

- **Construção:** O DW é construído a partir de **fontes de dados internas e externas** à organização por meio do processo de ETL (Extração, Transformação e Carga).
- **Modelagem:** Os dados são organizados em um **modelo dimensional** (tabelas Fato e Dimensão).
- **Análise:** Os usuários podem executar consultas *ad hoc*, criar relatórios, aplicar técnicas estatísticas e de mineração de dados para obter *insights* e detectar tendências de longo prazo.
- **Independência de Fonte:** O DW é capaz de fornecer um **modelo de dados comum** para diferentes áreas de interesse, independentemente da fonte de dados original, resolvendo problemas de padronização.

## 4. Análise de Questões de Concurso

### 4.1 Definição e Características (Cespe/FUB/2022)

- **Enunciado:** "Diferentemente dos bancos de dados transacionais, os data warehouses caracterizam-se pela volatilidade..."
- **Análise:** **ERRADO.** A volatilidade é uma característica dos bancos transacionais, não do DW. O DW é **não volátil**.

### 4.2 Armazenamento (CESGRANRIO/2018)

- **Enunciado:** "Um Data Warehouse é recomendado para armazenar dados:"
- **Gabarito:** **b. sumarizados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.**
- **Análise:** O DW lida com dados sumarizados (agregados) e históricos, não com o detalhe transacional.

### 4.3 Níveis Organizacionais (CESGRANRIO/2022)

- **Enunciado:** "Em que níveis organizacionais as ferramentas de BI, que utilizam dados organizados em um DW, são adequadas?"
- **Gabarito:** **c. Níveis gerencial e estratégico.**
- **Análise:** O DW contém dados sumarizados e históricos, ideais para a gestão de processos (gerencial) e o planejamento (estratégico).

### 4.4 DW e BI (CESPE/PGE-RJ/2022)

- **Enunciado:** "Data warehouse [...] não pode ser utilizado como repositório de dados em uma arquitetura de BI."
- **Análise:** **ERRADO.** O DW é o repositório **central** da arquitetura de BI.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (FCC/SEFAZ-BA) | **B** | DW = Não volátil (consultável, mas não alterável). |
| **2** (CESPE/IPHAN) | **E** | DW **é** um banco de dados. |
| **3** (CESGRANRIO/TRANSPETRO) | **C** | DW é construído a partir de fontes internas e externas. |
| **4** (CESPE/PETROBRAS) | **C** | DW fornece armazenamento para análise e decisão. |
| **5** (CESPE/FUB) | **E** | DW é **não volátil**. Transacional é volátil. |
| **6** (CESPE/TJ-AM) | **E** | Principal dispositivo de armazenamento != DW. |
| **7** (AOCP/PRODEB) | **C** | DW otimizado para recuperação de dados, não processamento transacional. |
| **8** (CESPE/APEX) | **D** | DW detecta tendências de longo prazo, não mostra status atual. |
| **9** (CESPE/PG-DF) | **C** | DW fornece modelo de dados comum independente da fonte. |
| **10** (CESPE/BANESE) | **E** | DW = decisão estratégica; consultas não são no provedor original. |
| **11** (CESGRANRIO/ELETRONUCLEAR) | **C** | DW = Níveis gerencial e estratégico. |
| **12** (CESPE/SEFAZ-CE) | **C** | DW = não volátil (não alterável) e variável no tempo (histórico). |
| **13** (CESPE/TCE-PA) | **E** | DW é um repositório de dados **não volátil**. |
| **14** (CESPE/STJ) | **C** | Finalidade: identificação de indicadores e evolução de valores. |
| **15** (CESGRANRIO/BANCO AMAZÔNIA) | **B** | DW armazena dados sumarizados de toda a empresa. |
| **16** (CESPE/EBSERH) | **C** | DW dá apoio a análises com grande volume de dados históricos. |
| **17** (FCC/DPE-AM) | **C** | DW proporciona ambiente para análise dos negócios. |
| **18** (FGV/COMPESA) | **A** | I. Visa facilitar a tomada de decisão. |
| **19** (CESPE/PGE-RJ) | **E** | DW é o repositório central de uma arquitetura de BI. |
| **20** (CESPE/PGE-RJ) | **E** | DW **pode** usar técnicas estatísticas e de aprendizagem. |
| **21** (CESGRANRIO/ELETRONUCLEAR) | **D** | DW = Orientado, Integrado, Variável no tempo e Não volátil. |
| **22** (FUNDATEC/AGERGS) | **C** | DW = Orientado por assunto, Integrado, Não volátil, Variável no tempo. |
| **23** (FGV/CGE-SC) | **A** | Transacional -> orientado a aplicação. DW -> orientado a assunto. |