# Anotações

# BUSINESS INTELLIGENCE E SISTEMAS DE SUPORTE À DECISÃO (SSD)

## 1. Revisão do Fluxo de Business Intelligence (BI)

- **BI** é o conjunto de processos, tecnologias e ferramentas que auxiliam as organizações a obter *insights* significativos a partir de seus dados, permitindo a tomada de decisões baseada em informações.
- O fluxo se inicia nas **fontes de dados**, que são extraídas, transformadas (em um modelo dimensional na *staging area*) e **carregadas** em um *Data Warehouse* (DW) ou *Data Mart*.
- Sobre esses repositórios, atuam as **operações OLAP** que alimentam os **Sistemas de Suporte à Decisão (SSD)** e *dashboards*, que fornecem a visualização e interatividade para o usuário final.
- O BI incorpora tecnologias como *Big Data*, *Analytics*, Inteligência Artificial e *Machine Learning*.

## 2. Sistemas de Suporte à Decisão (SSD / DSS)

### 2.1 Definição e Propósito

- **Sistemas de Suporte à Decisão (SSD)** são ferramentas tecnológicas e conceituais projetadas para **auxiliar** os tomadores de decisão.
- **Função:** Combinam **dados e modelos analíticos sofisticados** para fornecer informações relevantes, análises e interfaces amigáveis (como *dashboards* interativos).
- **Objetivo:** Melhorar a qualidade das decisões, aumentar a eficiência do processo decisório e reduzir a incerteza e o risco.

### 2.2 Tipos de Problemas Atendidos

- **Problemas Estruturados:** São rotineiros e repetitivos, com definição clara, processos estabelecidos e soluções previamente conhecidas. **Não necessitam de SSD**.
- **Problemas Não Estruturados:** São únicos, complexos, subjetivos e com informações incertas. A tomada de decisão exige julgamento humano, intuição e criatividade. **Este é o foco do SSD**, que busca fornecer evidências para apoiar, mas não substituir, o julgamento humano.

### 2.3 Características e Aplicações dos SSD

- Os SSD são aplicados nos níveis **gerencial e estratégico** da organização.
- Utilizam dados **internos** (da própria empresa) e **externos** (do mercado) para análises.
- **Não automatizam** completamente a decisão; eles dão **suporte** e exigem a participação do usuário.
- São sistemas **interativos** e permitem a fácil execução de **análises de sensibilidade** (estudo do impacto que mudanças em uma parte do modelo causam no resultado).
- Têm aplicações nas mais diversificadas áreas, não se limitando ao comércio eletrônico.

## 3. Análise de Questões de Concurso

### 3.1 Nível de Atuação do BI e DW (CESGRANRIO/ELETRONUCLEAR/2022)

- **Enunciado:** Em que níveis organizacionais as ferramentas de BI que utilizam um DW são adequadas?
- **Gabarito:** **C) Níveis gerencial e estratégico.**
- **Análise:** O DW provê dados sumarizados para apoiar a gestão e o planejamento de alto nível, não o chão de operação.

### 3.2 Tomada de Decisão e Julgamento Humano (CESPE/CODEVASF/2021)

- **Enunciado:** "Os sistemas de suporte à decisão são programados para substituir os tomadores de decisão..."
- **Gabarito:** **ERRADO.**
- **Análise:** Os SSD são feitos para **auxiliar**, não substituir. Eles são especialmente úteis para decisões de alto nível (não estruturadas), que exigem julgamento humano.

### 3.3 Informações Analíticas (FGV/CGE-SC/2023)

- **Enunciado:** Assinale a opção que apresenta apenas exemplos de **informações analíticas**.
- **Gabarito:** **B) Estatísticas de vendas por estado/Tendências no mercado de seguros.**
- **Análise:** "Informação analítica" é um dado consolidado, sumarizado ou projetado, que gera *insight*. Um "ingresso de cinema", "venda de remédio" ou "bilhete de passagem" são informações **transacionais** (registro de um evento).

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/PGE-RJ) | **C** | BI transforma dados em conhecimento para decisão e ação. |
| **2** (CESPE/TELEBRAS) | **C** | Ferramentas de BI: coleta, análise, visualização, decisão. |
| **3** (CESGRANRIO/ELETRONUCLEAR) | **D** | DW = Orientado, Integrado, Variável no tempo, Não Volátil. |
| **4** (CESGRANRIO/ELETRONUCLEAR) | **C** | DW e BI atuam nos níveis **gerencial e estratégico**. |
| **5** (CESPE/BANESE) | **E** | As consultas no DW não são processadas nos provedores originais. |
| **6** (CESGRANRIO/ELETRONUCLEAR) | **A** | OLAP organiza, consolida e permite acesso para tomada de decisão. |
| **7** (QUADRIX/CFO-DF) | **E** | Objetivo da BI é possibilitar acesso **interativo**. |
| **8** (CESGRANRIO/BB) | **C** | DW deve ter dados resumidos e adequadamente modelados. |
| **9** (QUADRIX/CRM-MG) | **A** | SSDs combinam dados e modelos analíticos sofisticados. |
| **10** (CESPE/CODEVASF) | **E** | SSDs **auxiliam**, não substituem, e são ideais para decisões de alto nível. |
| **11** (CESGRANRIO/TRANSPETRO) | **C** | SSD deve permitir a fácil execução das **análises de sensibilidade**. |
| **12** (CESGRANRIO/TRANSPETRO) | **D** | Tecnologias relacionadas ao propósito do SSD: Servidores OLAP, Data Marts. |
| **13** (CESGRANRIO/BB) | **D** | SSD no nível estratégico usa dados internos e **externos**. |
| **14** (CESPE/PETROBRAS) | **E** | SSD dá suporte a decisões **não estruturadas**, não estruturadas. |
| **15** (QUADRIX/CFO-DF) | **C** | DSS usam modelos para resolver problemas **não estruturados**. |
| **16** (CESGRANRIO/BB) | **E** | Tratar problemas não recorrentes com base em heurísticas. |
| **17** (QUADRIX/CRECI-MS) | **E** | SSD **requer a participação** do usuário. |
| **18** (FCC/SANASA) | **E** | "Específicos" na imagem = Data Marts. |
| **19** (QUADRIX/CRECI-MS) | **E** | SSD é **interativo**. |
| **20** (QUADRIX/CRECI-MS) | **E** | Aplicações de SSD estão em **todas** as áreas. |
| **21** (CESPE/TJ-AM) | **C** | Árvore de decisão usa predição baseada em eventos passados. |
| **22** (QUADRIX/CRECI-MS) | **C** | Análise de sensibilidade é extremamente valiosa no SSD. |
| **23** (FGV/CGE-SC) | **B** | Estatísticas e tendências são informações analíticas. |
| **24** (CESPE/PGE-RJ) | **E** | Um data lake por si só não é um sistema de suporte à decisão. |
| **25** (CESGRANRIO/TRANSPETRO) | **D** | Maximizar lucro com base em dados de DW = SSD. |