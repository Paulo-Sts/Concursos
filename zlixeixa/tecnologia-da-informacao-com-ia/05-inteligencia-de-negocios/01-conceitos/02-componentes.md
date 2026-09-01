# Componentes

## 1. Componentes do Business Intelligence

### 1.1 Definição Geral
- Business Intelligence (BI) é um conjunto de processos, arquiteturas e ferramentas que transformam dados brutos em informações significativas e úteis para a tomada de decisão.

### 1.2 Principais Componentes
- Fontes de dados: dão origem ao BI.
- ETL (Extração, Transformação e Carga): pega os dados da fonte de dados e os insere no Data Mart.
- Data Warehouse/Data Mart: repositório de dados a serem analisados para auxiliar na tomada de decisão.
- Modelagem de dados dimensional: os dados guardados no DW terão um formato de tabela fato e várias tabelas dimensão.
  - O fato é o tema principal do negócio (exemplo: a venda).
  - As dimensões descrevem o fato (exemplo: a venda).
- Ferramentas de análise e relatórios: navegam pelos dados na modelagem dimensional e transformam-nos em informação.
- Consultas e análises.
- Visualização de dados: pode ser em gráficos, em um painel etc.
- Distribuição e compartilhamento.
- Segurança e acesso.
- Governança de dados.

> [!TIP] DICAS: 
> - O ETL é responsável por pegar os dados da fonte e jogar no Data Mart.
> - A modelagem dimensional utiliza tabelas fato e tabelas dimensão.
> - O fato é o tema principal do negócio.

## 2. Componentes da Arquitetura de BI

### 2.1 Data Warehouse
- Data warehouse (DW) com seus dados-fonte utilizados para a análise de negócios.
- É considerado o "coração" de informações da fábrica.
- Contém dados granulares integrados.

### 2.2 Análise de Negócio
- Business analytics: coleção de ferramentas para manipular e analisar os dados no data warehouse.
- Inclui data mining.

### 2.3 Business Performance Management
- BPM para monitorar e analisar indicadores de desempenho.

### 2.4 Interface de Usuário
- Fornece uma capacidade visual para os dados solicitados pelos tomadores de decisão.
- Exemplos: dashboard, cockpit ou portal.

### 2.5 Componentes do Data Warehouse
- Sistemas de origem.
- Infraestrutura de ETL (Extraction-transformation-load).
- Data Warehouse.
- Aplicações de Front-end para o usuário final.

| COMPONENTE | FUNÇÃO |
|------------|--------|
| Fontes de dados | Ambientes operacionais com aplicativos de gestão, onde consumidores e fornecedores interagem com sistemas administrativos |
| ETL | Extrai dados dos aplicativos de gestão e insere diretamente no data warehouse |
| Data Warehouse | Banco de dados central, contém dados granulares integrados, "coração" da fábrica de informações |
| Plataforma de BI | Conjunto de ferramentas que disponibiliza dados para consulta e processamento pelo usuário |

> [!CAUTION] OBSERVAÇÃO: 
> - Os principais componentes da arquitetura de um sistema de BI são: data warehouse, análise de negócio, business process management e interfaces do usuário.
> - Em sistemas de BI, a coleção de ferramentas para manipular e analisar dados no DW denomina-se Análise de Negócio, não OLAP, BPM, Dashboard ou Processamento de Transações.
> - O ETL insere os dados diretamente no DW, não no banco de dados comum.
> - A estrutura geral do BI demanda que todos os componentes sejam delineados de forma lógica.