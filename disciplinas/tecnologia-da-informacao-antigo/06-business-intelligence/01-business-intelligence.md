# Anotações

# BUSINESS INTELLIGENCE (BI) – INTRODUÇÃO E CONCEITOS

## 1. Definição e Propósito do BI

### 1.1 O que é Business Intelligence (BI)

- **Definição:** Business Intelligence é um **conjunto de processos, tecnologias e ferramentas** que auxiliam as organizações a obter **insights significativos** a partir de seus dados, permitindo a **tomada de decisões baseada em informações**.
- **Propósito Central:** Transformar dados brutos em informações, depois em decisões e, por fim, em ações.
- **Aplicação:** Utilizado em diversas áreas e setores, incluindo vendas, marketing, finanças, recursos humanos, operações e logística.

### 1.2 Evolução e Contexto

- O BI vai além de consultas simples em bancos de dados (SQL) ou bases transacionais (OLTP) isoladas.
- O fluxo clássico de informações é: dados de fontes diversas (OLTP) -> extraídos, transformados e carregados (ETL) para um **Data Warehouse (DW)** -> onde são analisados e navegados (OLAP) -> para gerar dashboards e relatórios.
- O BI tem se integrado cada vez mais com tecnologias como ***Big Data***, ***Analytics* Avançada**, **Inteligência Artificial** e ***Machine Learning*** para extrair conhecimento.

## 2. Componentes e Arquitetura do BI

### 2.1 Elementos Essenciais

- **Coleta de Dados:** Extração de dados de fontes heterogêneas (bancos internos, sistemas de gestão, planilhas, APIs externas, mídias sociais).
- **Organização e Armazenamento:**
    - Os dados são preparados em uma ***Staging Area***.
    - São armazenados de forma organizada e modelada (geralmente em um modelo dimensional) em um **Data Warehouse (DW)** ou em um **Data Mart**.
- **Análise:** Aplicação de técnicas estatísticas, modelagem de dados e algoritmos de mineração para identificar padrões, tendências e correlações.
- **Visualização:** Criação de **dashboards interativos**, relatórios personalizados e gráficos para facilitar a compreensão e interpretação dos resultados pelos tomadores de decisão.

### 2.2 Características do Sistema de BI

- **Acesso Interativo:** Fornece aos gestores e analistas a capacidade de **interagir e manipular** dados para realizar análises, não sendo um sistema de acesso passivo (somente leitura).
- **Orientado ao Nível Gerencial:** É uma ferramenta voltada primariamente para a alta e média gerência, apoiando a definição de estratégias e a solução de problemas.
- **Base para Decisões:** Substitui decisões baseadas em intuição ou "sentimento" por decisões baseadas em padrões e fatos.

## 3. Objetivos e Desafios do BI

### 3.1 Principais Objetivos

- Permitir acesso interativo e manipulação de dados para análise.
- Ajudar a empresa a criar conhecimento e converter decisões em ações.
- Oferecer suporte à tomada de decisões no ambiente de negócios.

### 3.2 Desafios Comuns na Implementação (Questão FUNDATEC/2022)

Os seguintes pontos representam desafios reais na construção de uma solução de BI:
    - Integração de dados de diferentes fontes.
    - Qualidade dos dados.
    - Criação de uma cultura organizacional baseada em dados (*Data-driven culture*).
    - Falta de conhecimento técnico em ferramentas de BI.

## 4. Análise de Questões de Concurso

### 4.1 Conjunto de Ferramentas e Definição (AOCP/2018)

- **Questão 2:** O BI estrutura os dados do negócio com base na definição primária do recurso de software? **Não.** BI é um conceito e conjunto de processos, não um definidor do negócio em si.
- **Questão 3:** BI é um conjunto de técnicas, métodos e ferramentas utilizado para a tomada de decisões por parte da alta gerência da empresa? **Sim.**

### 4.2 BI vs. Data Warehouse (IADES/2018)

- BI é o **mesmo** que Data Warehouse? **Não.**
    - BI é o **processo** (coleta, tratamento, análise).
    - Data Warehouse é o **local** (armazém de dados) onde os dados são guardados para o BI. São conceitos complementares, mas não sinônimos.

### 4.3 Acesso Interativo (QUADRIX/2022)

- O principal objetivo da BI é possibilitar acesso **não interativo** (somente leitura) a dados? **ERRADO.**
- O objetivo é fornecer acesso **interativo**, permitindo a manipulação e análise dos dados.

## 5. Definições Importantes de Provas

- **Cespe (CGM de João Pessoa/2018):** Business intelligence pode ser definido como um processo inteligente de coleta, organização, análise, compartilhamento e monitoração de dados que, depois de processados, geram informações para o suporte e para a tomada de decisões no ambiente de negócios.
- **Cesgranrio (Banco do Brasil/2021):** Os sistemas de BI são utilizados por gestores para exploração de dados sumarizados para compreensão e inspiração na solução de problemas.

## 6. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/PETROBRAS/2022) | **C** | Dados -> Informações -> Decisões -> Ações. |
| **2** (AOCP/PRODEB/2018) | **D** | BI possibilita a descoberta de padrões sem tendenciosidade intuitiva. |
| **3** (AOCP/PRODEB/2018) | **A** | Conjunto de técnicas para tomada de decisão da alta gerência. |
| **4** (CESGRANRIO/BB/2021) | **A** | Exploração de dados sumarizados pelos gestores. |
| **5** (CESPE/SEFAZ-CE/2021) | **C** | Permite acesso interativo e manipulação para análise. |
| **6** (CESPE/JP/2018) | **C** | Processo inteligente de coleta, organização, análise... |
| **7** (IADES/APEX/2018) | **D** | Processo de recolhimento e tratamento de informações. |
| **8** (CESPE/APEX/2021) | **A** | Acessos interativos e transformação em informações, decisões e ações. |
| **9** (CESPE/PGE-RJ/2022) | **C** | Ajuda a criar conhecimento e converter decisões em ação. |
| **10** (FUNDATEC/AGERGS/2022) | **A** | Todos os itens são desafios (Integração, Qualidade, Cultura, Conhecimento). |
| **11** (QUADRIX/CFO-DF/2022) | **C** | Combina arquiteturas, ferramentas, bases de dados... |
| **12** (QUADRIX/CFO-DF/2022) | **E** | BI = acesso **interativo**, não "não interativo". |