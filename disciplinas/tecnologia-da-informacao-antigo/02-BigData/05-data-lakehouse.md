# Anotações – Data Lakehouse

## 1. O Dilema Histórico dos Dados

### 1.1 Data Warehouse (Armazém de Dados)

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Confiabilidade** | Dados estruturados, organizados, históricos. |
| **Alto desempenho** | Otimizado para consultas analíticas (OLAP). |
| **Governança rígida** | Controle rigoroso de acesso, estrutura e esquema. |
| **Custo elevado** | Consequência da governança e desempenho. |

### 1.2 Data Lake (Lago de Dados)

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Flexibilidade** | Dados de diversos formatos; mantém o esquema original. |
| **Dados brutos** | Armazena dados sem transformação prévia. |
| **Baixo custo** | Armazenamento em objetos (ex.: S3, Azure Blob). |
| **Caos (Data Swamp)** | Perda de governança – dados tornam-se um "pântano". |

> ### 1.3 A falha da arquitetura clássica
> - Empresas precisavam manter **dois sistemas separados**: Data Lake e Data Warehouse.
> - **Problemas:**
>   - Silos de dados.
>   - Pipelines complexos para transformar dados.
>   - Duplicidade de dados.
>   - Manutenção de duas pilhas tecnológicas.
>   - Gargalos de engenharia.

## 2. Data Lakehouse – A Unificação

### 2.1 Conceito

- **Data Lakehouse** é uma **arquitetura híbrida** que une:
  - **Baixo custo e flexibilidade** do Data Lake.
  - **Confiabilidade, ACID e desempenho** do Data Warehouse.
- **Objetivo:** eliminar a divisão entre dados analíticos (BI) e ciência de dados, unificando todas as cargas de trabalho em uma única plataforma.

### 2.2 A Fórmula

```
Data Lake + ACID + Metadados + Performance = Lakehouse
```

- **Armazenamento:** objetos (S3, Azure Blob, Google Cloud) – baixo custo e escala.
- **Transações ACID:** garantem confiabilidade (Atomicidade, Consistência, Isolamento, Durabilidade).
- **Metadados:** permitem governança e performance.
- **Performance:** de um Data Warehouse.

### 2.3 Camadas do Data Lakehouse

| CAMADA | DESCRIÇÃO |
| --- | --- |
| **1. Armazenamento (dados brutos)** | Dados em formatos abertos (Parquet, ORC, Avro). |
| **2. Tabelas transacionais** | Camada intermediária que garante ACID. Utiliza **table formats** abertos (Delta Lake, Apache Iceberg, Apache Hudi). |
| **3. Processamento** | SQL, Apache Spark, machine learning. |
| **4. Consumo** | Painéis, BI, APIs. |

> ### 2.3.1 Table Formats (formatos de tabela)
> - **Delta Lake** (Databricks): desempenho e integração com Apache Spark.
> - **Apache Iceberg** (Netflix): grandes volumes, compatível com múltiplos motores.
> - **Apache Hudi** (Uber): usado para pipelines de dados.

## 3. Comparativo Arquitetural

| CRITÉRIO | DATA LAKE | DATA WAREHOUSE | LAKEHOUSE |
| --- | --- | --- | --- |
| **Dados Brutos** | ✅ Sim | ❌ Não | ✅ Sim |
| **ACID** | ❌ Não | ✅ Sim | ✅ Sim |
| **BI Corporativo** | Limitado | Excelente | Excelente |
| **ML / IA** | Excelente | Limitado | Excelente |
| **Custo** | Baixo | Alto | Moderado |
| **Flexibilidade** | Alta | Baixa | Alta |

## 4. Vantagens Estratégicas do Data Lakehouse

| VANTAGEM | DESCRIÇÃO |
| --- | --- |
| **Governança unificada** | Único repositório para segurança e compliance (ex.: LGPD). |
| **Redução de custos** | Elimina pipelines complexos e duplicidade de dados. |
| **Dados em tempo real** | Não depende de ETL tradicional – pipelines em tempo real. |
| **Suporte híbrido** | BI e ciência de dados na mesma base. |
| **Auditoria e compliance** | Rastreabilidade e histórico de dados (time travel). |
| **Grandes volumes** | Adequado para dados estruturados e semiestruturados. |

> ### 4.1 Time Travel
> - Capacidade de **consultar versões passadas** dos dados.
> - Permite rollback e auditoria histórica.

## 5. Quando Adotar o Data Lakehouse?

- Quando a organização trabalha com **BI e IA simultaneamente**.
- Quando há **grandes volumes de dados** estruturados e semiestruturados.
- Quando se deseja **reduzir custos** e **simplificar a arquitetura** de dados.
- **Exemplos de uso:**
  - Analytics Governamental.
  - Monitoramento de Dados.
  - Plataformas Corporativas (dados centralizados).

## 6. Questão de Concurso Comentada

### 6.1 (FGV/2024/TCE-PA – Auditor)

**Item:** "Com relação ao conceito de Data Lakehouse e sua arquitetura, assinale a afirmativa correta."

**Análise das alternativas:**
- a) É anterior ao Data Warehouse? **(F)** – é posterior e unifica Data Lake e Warehouse.
- b) Armazena dados brutos não processados? **(F)** – isso é Data Lake; o Lakehouse também armazena, mas com camada transacional.
- c) Sem suporte a transações ACID? **(F)** – suporta ACID na camada de tabelas transacionais.
- d) Armazenamento em objetos + atualizações incrementais, exclusões, histórico e rollback? **(V)**
- e) Dificuldade de trocar dados entre ferramentas? **(F)** – usa formatos abertos (Parquet, ORC, Avro), facilitando interoperabilidade.

**Gabarito: d.**

---

## GABARITO DA QUESTÃO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/TCE-PA/2024) | d |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Data Lake** | Armazena dados brutos, flexível, baixo custo, mas sem ACID. |
| **Data Warehouse** | Dados estruturados, alta performance, governança rígida, alto custo. |
| **Data Lakehouse** | Unificação: baixo custo + ACID + performance + flexibilidade. |
| **Table Formats** | Delta Lake, Iceberg, Hudi – habilitam ACID sobre Data Lake. |
| **Time Travel** | Consulta a versões passadas dos dados. |
| **Camadas** | Armazenamento bruto → Tabelas transacionais → Processamento → Consumo. |

---

*Material complementar à aula "Data Lakehouse" (professor Vitor Kessler/Gran Concursos).*