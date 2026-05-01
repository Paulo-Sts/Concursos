# Anotações

# BUSINESS INTELLIGENCE – DATA MART E OLAP

## 1. Data Mart

### 1.1 Definição e Propósito

- **Data Mart** é um **subconjunto** de um Data Warehouse.
- Representa uma **visão específica e segmentada** dos dados para atender às necessidades de uma **área de negócio** ou departamento específico (ex: Data Mart de Vendas, Data Mart de Finanças).
- Contém informações focadas em um determinado assunto, não normalizadas, e são indexados para suportar pesquisas.

### 1.2 Abordagens para Criação

- ***Top-Down* (De cima para baixo):** Os Data Marts são derivados diretamente do Data Warehouse central.
- ***Bottom-Up* (De baixo para cima):** Os Data Marts são criados separadamente e, depois, integrados em um Data Warehouse central.

### 1.3 Benefícios

- Foco em necessidades específicas de um departamento.
- Melhor desempenho nas consultas.
- Autonomia para as equipes de negócio.
- Flexibilidade.

## 2. OLAP (Processamento Analítico Online)

### 2.1 Definição e Propósito

- **OLAP (*Online Analytical Processing*)** é uma abordagem e tecnologia usada para a **análise interativa de dados multidimensionais**.
- **Função Central:** É a ferramenta para acesso à informação do Data Warehouse, que permite explorar dados de diversas perspectivas, extraindo e analisando informações para suportar a tomada de decisões empresariais.
- **Características:** Trabalha sobre **histórico de dados**, não sobre dados em tempo real. É uma **interface com o usuário** e não uma forma de armazenamento. Disponibiliza relatórios de forma dinâmica.

### 2.2 Variações de Armazenamento OLAP

| TIPO | SIGLA | CARACTERÍSTICA PRINCIPAL |
| :--- | :--- | :--- |
| **OLAP Multidimensional** | **MOLAP** | Armazena dados em um cubo multidimensional pré-computado. Consultas mais rápidas. |
| **OLAP Relacional** | **ROLAP** | Cria visões multidimensionais a partir de um banco de dados relacional existente. Mais escalável. |
| **OLAP Híbrido** | **HOLAP** | Combina MOLAP (para agregações) e ROLAP (para dados detalhados). |
| **OLAP Web** | **WOLAP** | Ferramentas OLAP baseadas em ambiente web. |
| ***Desktop* OLAP** | **DOLAP** | Dados são acessados e analisados localmente no computador do usuário. |

## 3. Análise de Questões de Concurso

### 3.1 Data Mart (AOCP/SUSIPE/2018)

- **Enunciado:** Definição de Data Mart.
- **Gabarito:** **e. "subconjunto de dados referentes a uma área específica, não normalizados e indexados para suportar pesquisas."**
- **Análise:** É a definição que captura a natureza departamental e a estrutura voltada para análise.

### 3.2 OLAP vs. OLTP (CESPE/PETROBRAS/2022)

- **Enunciado:** "OLAP é uma técnica de análise de dados que tem o propósito de desempenhar funções empresariais cotidianas."
- **Gabarito:** **ERRADO**.
- **Análise:** A técnica voltada para desempenhar funções empresariais cotidianas (transações do dia a dia) é o **OLTP**, não o OLAP.

### 3.3 Variações do OLAP (CESPE/TCE-PA/2016)

- **Enunciado:** "MOLAP é um método utilizado para apresentar, fisicamente e em formato relacional, os dados em formato OLAP."
- **Gabarito:** **ERRADO**.
- **Análise:** O método que apresenta os dados em formato relacional é o **ROLAP**. O MOLAP os apresenta em cubos multidimensionais.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (AOCP/EBSERH) | **B** | Subdivisão do DW para um departamento = Data Mart. |
| **2** (AOCP/SUSIPE) | **E** | Subconjunto de dados não normalizados e indexados. |
| **3** (FCC/SANASA) | **E** | Cilindros específicos na imagem = Data Mart. |
| **4** (AOCP/CASAN) | **A** | Projeto de DW que começa pequeno = Data Mart. |
| **5** (AOCP/EMPREL) | **C** | Ferramenta para acesso à informação do DW = OLAP. |
| **6** (CESGRANRIO/ELETRONUCLEAR) | **A** | OLAP organiza, consolida e permite acesso a dados. |
| **7** (AOCP/MJSP) | **D** | Programa para explorar dados = Processamento analítico on-line (OLAP). |
| **8** (CESPE/PETROBRAS) | **E** | Funções cotidianas = OLTP, não OLAP. |
| **9** (AOCP/CASAN) | **B** | Ferramenta para explorar DW = OLAP. |
| **10** (AOCP/UFPB) | **A** | OLAP: histórico, análise, relatórios dinâmicos. |
| **11** (FUNDATEC/IPE) | **A** | DW, OLAP e Data Marts. |
| **12** (FGV/TRT-13) | **E** | 1-A (BI), 2-B (DW), 3-C (OLAP). |
| **13** (CESPE/PGE-RJ) | **E** | MOLAP sobre BDR existente = é o ROLAP. |
| **14** (CESPE/TCE-SC) | **C** | ROLAP = visões multidimensionais de um BDR. |
| **15** (AOCP/UFOB) | **C** | HOLAP = híbrido (parte relacional, parte multidimensional). |
| **16** (CESPE/TCE-PA) | **E** | MOLAP em formato relacional = é o ROLAP. |
| **17** (CESGRANRIO/LIQUIGÁS) | **D** | ROLAP (relacional) e MOLAP (multidimensional). |