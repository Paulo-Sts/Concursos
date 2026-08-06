# Data Lakehouse

## 1. O Dilema Histórico dos Dados

### 1.1 Data Warehouse
- Bases de dados estruturadas, organizadas e históricas.
- Características:
  - Confiabilidade;
  - Alto desempenho para consultas analíticas (OLAP);
  - Governança rígida (controle de acesso, estrutura e esquema dos dados).
- Consequência: custo elevado.

### 1.2 Data Lake
- Ambiente flexível que aceita dados dos mais diversos formatos.
- Características:
  - Mantém o esquema original dos dados;
  - Dados brutos;
  - Baixo custo.
- Problema: tende a se transformar em um Data Swamp (pântano de dados) devido à perda de governança.
- Historicamente, as empresas precisavam manter dois sistemas separados, sacrificando qualidade em nome da flexibilidade.

### 1.3 A Falha da Arquitetura Clássica
- Necessidade de manter silos de dados separados.
- Processos e pipelines complexos para transformar dados do Data Lake e armazená-los no Data Warehouse.
- Duplicidade de dados nos dois ambientes de armazenamento.
- No Data Lake, a qualidade dos dados não era boa.
- Manutenção de duas pilhas tecnológicas, criando gargalos de engenharia.
- Os dados mudavam ao longo do tempo sem controle adequado.

> [!TIP] DICAS:
> - Data Warehouse = estruturado, confiável, com governança, mas caro.
> - Data Lake = flexível, dados brutos, barato, mas bagunçado (Data Swamp).

## 2. A Unificação: Data Lakehouse

### 2.1 Conceito
- Arquitetura híbrida que elimina a divisão entre ambientes analíticos e de ciência de dados.
- Única plataforma na qual se pode fazer BI, processamento analítico, ingerir dados de Big Data e praticar ciência de dados.
- Objetivo: unificar todas as cargas de trabalho em uma única plataforma, evitando duplicações.

### 2.2 A Fórmula da Nova Arquitetura
- Armazenamento de objetos (ex.: Amazon S3, Azure Blob, Google Cloud) igual ao Data Lake.
- Baixo custo e escala do Data Lake.
- Garantia de transações ACID e metadados que asseguram confiabilidade e performance do Data Warehouse.
- Resultado: desempenho de armazém com economia de lago de dados.

## 3. Arquitetura do Data Lakehouse

### 3.1 Camadas da Arquitetura
- O Data Lakehouse se organiza em quatro camadas:

#### 3.1.1 Camada de Armazenamento (Dados Brutos)
- Armazenamento dos dados em sua forma original.

#### 3.1.2 Camada Intermediária (Tabelas Transacionais)
- Tabelas que garantem o Data Warehouse do Data Lake.
- Utilizam table formats (formatos abertos de tabela):
  - Delta Lake (Databricks): desempenho e integração profunda com Apache Spark;
  - Apache Iceberg (Netflix): grandes volumes e compatibilidade com múltiplos motores;
  - Apache Hudi (Uber): utilizado para grandes volumes de dados.
- São formatos de código aberto que permitem transações confiáveis sobre o Data Lake.

#### 3.1.3 Camada de Processamento
- Processamento de dados por SQL ou utilizando Spark.
- Inclui camadas de machine learning.

#### 3.1.4 Camada de Consumo
- Painéis (dashboards), BI e APIs.

### 3.2 Funcionalidades Habilitadas
- Transações ACID quando necessário: atomicidade, consistência, isolamento e durabilidade.
- Leituras e escritas confiáveis; não há corrupção de dados.
- Enforcement (endurecimento/melhoria) do esquema nas tabelas intermediárias; não há dados sujos ou mal formatados transitando entre tabelas.
- Time Travel: capacidade de consultar versões passadas dos dados.
- Separação entre computação e armazenamento.

> [!CAUTION] OBSERVAÇÃO:
> - O professor sinalizou que detalhes específicos de implementação "não são cobrados".

## 4. Comparativo Arquitetural
| CRITÉRIO | DATA LAKE | DATA WAREHOUSE | LAKEHOUSE |
|----------|-----------|----------------|-----------|
| Dados brutos | Sim | Não | Sim |
| ACID | Não | Sim | Sim |
| BI corporativo | Limitado | Excelente | Excelente |
| ML / IA | Excelente | Limitado | Excelente |
| Custo | Baixo | Alto | Moderado |
| Flexibilidade | Alta | Baixa | Alta |

### 4.1 Análise do Comparativo
- Dados brutos: mantidos no Data Lake e no Lakehouse (camada de armazenamento); não no Data Warehouse.
- ACID: não garantida no Data Lake; garantida no Data Warehouse e no Lakehouse (camada de tabelas transacionais).
- BI corporativo: complexo no Data Lake; presente no Lakehouse (camada de consumo) e no Data Warehouse.
- Machine Learning/IA: executado no Data Lake e no Lakehouse; praticamente não executado no Data Warehouse (apenas extração com data mining).
- Custo: moderado no Lakehouse (não tão barato quanto o Data Lake, nem tão caro quanto o Data Warehouse).
- Flexibilidade: alta no Data Lake e no Lakehouse (formatos abertos como Parquet, ORC, Avro na camada de armazenamento); baixa no Data Warehouse.

## 5. Vantagens Estratégicas do Data Lakehouse

### 5.1 Governança Unificada
- Única base, único repositório para garantir segurança e conformidade (ex.: LGPD).
- Preocupação com um único repositório, não com dois distintos.

### 5.2 Redução de Custos
- Eliminação de pipelines complexos.
- Não há cópia de dados em dois ambientes diferentes de armazenamento.

### 5.3 Dados em Tempo Real
- Não é necessário rodar ETL do Data Warehouse.
- Possibilidade de fazer pipelines em tempo real.

### 5.4 Suporte Híbrido
- Possibilidade de realizar tanto trabalhos de BI quanto de ciência de dados na mesma base.

### 5.5 Auditoria e Compliance
- Requisitos de rastreabilidade mais organizados.
- Histórico de dados da camada de armazenamento até a camada de tabelas.

### 5.6 Cenários de Adoção
- Quando a organização trabalha com BI e IA simultaneamente.
- Quando se roda SQL para montar um Data Warehouse e, ao mesmo tempo, se faz machine learning.
- Para grandes volumes de dados estruturados e semiestruturados.
- Exemplos de aplicação: Analytics Governamental, Monitoramento de Dados, Plataformas Corporativas.