# Anotações

# Coleta, Tratamento, Armazenamento, Integração e Recuperação de Dados

## 1.1 Ciclo de Vida dos Dados

O ciclo de vida dos dados no contexto de ciência de dados abrange as seguintes etapas:

1. **Coleta** – obtenção de informações de diversas fontes.
2. **Tratamento** – preparação e limpeza dos dados para análise.
3. **Armazenamento** – guarda dos dados em sistemas apropriados.
4. **Integração** – unificação de informações de diferentes fontes.
5. **Recuperação** – extração das informações dos sistemas de armazenamento.

## 1.2 Coleta de Dados

### 1.2.1 Fontes de Dados

| TIPO | DESCRIÇÃO | EXEMPLOS |
|------|-----------|----------|
| **Fontes Primárias** | Dados coletados diretamente | Entrevistas, formulários, sensores IoT |
| **Fontes Secundárias** | Dados previamente coletados e organizados | Bancos de dados públicos, redes sociais, registros administrativos |

### 1.2.2 Estratégias de Coleta
- **Formulários online.**
- **APIs** (*Application Programming Interfaces*).
- **Web Scraping** – extração de dados de páginas web usando bibliotecas em Python.
- **Sistemas de TI e IoT** – sensores e dispositivos conectados geram dados em tempo real.

### 1.2.3 Desafios da Coleta
- **Qualidade dos dados:** inconsistências, erros de digitação, dados desatualizados.
- **Privacidade:** LGPD – necessidade de consentimento para uso de dados pessoais.
- **Variedade:** dados estruturados, semiestruturados e não estruturados.
- **Volume:** grandes massas de dados (*Big Data*).
- **Segurança:** evitar vazamentos, perda de integridade, garantir confiabilidade.

> [!CAUTION] OBSERVAÇÃO
> **Exemplo prático:** A Meta (Facebook/WhatsApp) interrompeu o uso de dados pessoais de brasileiros para treinar IA devido à **falta de consentimento**, caracterizando prática ilegal.

## 1.3 Tratamento de Dados

### 1.3.1 Etapas do Tratamento

**1. Limpeza de Dados (*Data Cleaning*):**
- Corrigir erros.
- Remover duplicidades (deduplicação).
- Tratar valores atípicos (*outliers*).
- Preencher dados ausentes.
- **Validação:** verificar conformidade e precisão das informações.

> [!TIP] DICAS
> - Algoritmos como **árvore de decisão** não lidam com dados incompletos – é necessário tratar ou excluir dados ausentes.
> - A **validação de dados** pode utilizar ferramentas como análises descritivas para identificar inconsistências.

**2. Transformação de Dados:**
- **Mudança de tipo de dado:** numérico → categórico (ex.: altura → "baixo/médio/alto") ou categórico → numérico.
- ***One-Hot Encoding:*** converte variáveis categóricas em variáveis binárias numéricas (cria uma coluna para cada categoria).
- **Mudança de escala:** normalização ou padronização para redes neurais.
- **Geração de hierarquias de conceitos:** organização de dados em estruturas hierárquicas (ontologias).
- **Agrupamento de dados:** transformação de variáveis numéricas em categorias (ex.: clusterização).
- **Redução de dimensionalidade:** redução do número de atributos (ex.: Análise de Componentes Principais – ACP/PCA).
- **Mascaramento/Anonimização:** ocultação de informações sensíveis (LGPD).

**3. Rotulagem:**
- Identificação de palavras-chave ou categorias gramaticais em textos.
- Importante para **Processamento de Linguagem Natural (PLN)**.

### 1.3.2 ETL – Extract, Transform, Load

| ETAPA | DESCRIÇÃO |
|-------|-----------|
| **Extração** | Obtenção de dados de diversas fontes para uma área intermediária |
| **Transformação** | Tratamento, limpeza, validação, deduplicação e ajustes dos dados |
| **Carga** | Carregamento dos dados tratados no destino final (banco, Data Warehouse) |

> [!CAUTION] OBSERVAÇÃO
> **A validação e a deduplicação ocorrem na fase de TRANSFORMAÇÃO, não na de CARGA.**

### 1.3.3 Ferramentas de Tratamento
- **Python** – biblioteca *pandas* (estrutura DataFrame).
- **R** – amplamente utilizado para análises estatísticas avançadas.
- **Ferramentas de ETL:** Talend, Apache Nifi.

## 1.4 Armazenamento de Dados

### 1.4.1 Tipos de Repositórios

| TIPO | DESCRIÇÃO | EXEMPLOS |
|------|-----------|----------|
| **Bancos de Dados Relacionais** | Dados estruturados em tabelas | PostgreSQL, Oracle, SQL Server |
| **Bancos NoSQL** | Dados não estruturados/semiestruturados | Cassandra, DynamoDB, MongoDB |
| **Data Lake** | Repositório não estruturado; armazena grandes volumes sem pré-processamento | Amazon S3, Hadoop HDFS |
| **Data Warehouse** | Estrutura dimensional (tabelas fato e dimensão); dados remodelados para análise | Modelo dimensional |
| **Data Mart** | Versão segmentada do Data Warehouse, focada em um domínio específico | — |
| **ODS (Operational Data Store)** | Armazenamento operacional consolidado, sem características dimensionais; dados atualizados em tempo real | — |

> [!TIP] DICAS
> - **Data Warehouse e Data Mart** → estruturas **dimensionais** para análises.
> - **ODS** → dados operacionais consolidados, **sem características dimensionais**.
> - **Data Lake** → dados brutos/não estruturados, sem pré-processamento.

## 1.5 Integração de Dados

- Combinação de dados de **diferentes fontes** para gerar uma **visão unificada**.
- Pode ser realizada por:
  - **ETL tradicional:** Extração → Transformação → Carga.
  - **ELT:** Extração → Carga → Transformação (comum em Big Data).
- Objetivo: combinar fontes com dados conflitantes, gerando informações coerentes.

## 1.6 Recuperação de Dados

- Extração de informações dos sistemas de armazenamento.
- Formas de recuperação:
  - **Consultas SQL.**
  - **APIs.**
  - **Ferramentas de BI:** Tableau, Power BI, Google Data Studio.

## 1.7 Tabela Resumo – Ciclo de Vida dos Dados

| ETAPA | DESCRIÇÃO | DESAFIOS |
|-------|-----------|----------|
| **Coleta** | Obtenção de dados de fontes primárias/secundárias | Qualidade, privacidade, variedade, volume, segurança |
| **Tratamento** | Limpeza, transformação, validação, deduplicação | Dados ausentes, outliers, inconsistências |
| **Armazenamento** | Guarda em repositórios adequados | Escalabilidade, segurança, acesso |
| **Integração** | Unificação de dados de múltiplas fontes | Dados conflitantes, padronização |
| **Recuperação** | Extração eficiente dos dados | Performance, ferramentas adequadas |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2024/MPO/ANALISTA DE PLANEJAMENTO E ORÇAMENTO/GESTÃO DE DADOS ORÇAMENTÁRIOS)

Acerca de dados abertos, bem como de processos de coleta, tratamento, armazenamento, integração e recuperação de dados, julgue o item que se segue.

Na fase de carregamento de um processo ETL (extract transform load), são realizadas a deduplicação e a validação dos dados.

**Gabarito:** E (Errado) - A validação e a deduplicação ocorrem na fase de **transformação**, não na de carga.

## Questão 02
(CESPE/CEBRASPE/2024/MPO/ANALISTA DE PLANEJAMENTO E ORÇAMENTO/GESTÃO DE DADOS ORÇAMENTÁRIOS)

Acerca de dados abertos, bem como de processos de coleta, tratamento, armazenamento, integração e recuperação de dados, julgue o item que se segue.

Data warehouse e data mart dizem respeito às estruturas dimensionais de dados, remodeladas com o objetivo de prover análises diferenciais, ao passo que o OSD (operational data store) está relacionado ao armazenamento e tratamento de dados, de forma também consolidada, porém sem as características dimensionais.

**Gabarito:** C (Correto)

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | C |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*