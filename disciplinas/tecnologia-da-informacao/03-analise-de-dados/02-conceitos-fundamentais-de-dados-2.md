# Anotações

# Conceitos Fundamentais de Dados II – Formatos de Arquivos

## 1.1 Formatos Comuns de Arquivos de Dados

### 1.1.1 TXT (Texto Puro)
- Contém dados em formato de texto simples, sem estruturação formal além de quebras de linha.
- É fácil de abrir, mas **não é eficiente** para grandes volumes de dados ou metadados.
- Caracteres especiais: `\t` (tabulação), `\n` (nova linha) etc.

### 1.1.2 CSV (Comma-Separated Values)
- Armazena dados tabulares em texto simples, onde os valores são separados por **vírgulas** (ou outro delimitador).
- Amplamente utilizado por sua **simplicidade e compatibilidade** com muitos sistemas.
- **Não lida bem** com dados complexos ou hierárquicos (ex.: dados geográficos, estruturas aninhadas, arrays).
- Formato **em linha** – lê a linha inteira, mesmo que apenas algumas colunas sejam necessárias.

### 1.1.3 XLSX (Excel)
- Formato **binário** utilizado pelo Microsoft Excel para armazenar planilhas.
- Permite **formatação rica**, uso de **fórmulas** e **macros**.
- Mais **difícil de manipular** em sistemas automatizados por ser um formato proprietário e mais complexo.
- Requer bibliotecas específicas para leitura (diferente do CSV, que pode ser lido diretamente por ser texto).

### 1.1.4 XML (Extensible Markup Language)
- Usado para armazenar dados de forma **estruturada e hierárquica**.
- Utiliza **marcações (tags)** para indicar informações (ex.: `<título>...</título>`).
- Amplamente utilizado para **intercâmbio de dados** entre sistemas.
- Pode ser **verboso** e difícil de manipular em grandes volumes.
- É classificado como **dado semiestruturado**.

### 1.1.5 JSON (JavaScript Object Notation)
- Formato **leve e legível** para humanos.
- Comumente usado em **APIs** para troca de dados entre sistemas.
- Suporta **estruturas hierárquicas** (pares chave-valor dentro de chaves `{}`).
- Mais **eficiente que XML** em muitos casos.
- É classificado como **dado semiestruturado**.

> [!TIP] DICAS
> - **CSV** → dados **estruturados** (formato tabular/linha).
> - **XML e JSON** → dados **semiestruturados** (hierárquicos, com tags ou chaves).
> - **XLSX** → formato **binário** (mais complexo, proprietário).

## 1.2 Apache Parquet

### 1.2.1 Visão Geral
- Formato de armazenamento de dados **open-source**, **colunar**.
- Otimizado para **leitura e escrita eficiente** em grandes volumes de dados.
- Usado em **ambientes de Big Data** e sistemas analíticos distribuídos:
  - Apache Hadoop
  - Apache Spark
  - Amazon S3
- Também pode ser usado em sistemas locais.

### 1.2.2 Formato Colunar x Formato em Linha

| ASPECTO | FORMATO EM LINHA (CSV) | FORMATO COLUNAR (PARQUET) |
|---------|------------------------|---------------------------|
| **Organização** | Linha por linha | Coluna por coluna |
| **Leitura seletiva** | Não – lê a linha inteira | Sim – acessa apenas colunas específicas |
| **Desempenho** | Lento para grandes volumes | Rápido para grandes volumes |
| **Uso típico** | Planilhas, dados pequenos | Big Data, análise distribuída |

### 1.2.3 Tipos de Dados Suportados pelo Parquet

| TIPO | DESCRIÇÃO |
|------|-----------|
| **BOOLEAN** | Booleano de 1 bit (verdadeiro/falso) |
| **INT32** | Inteiro com sinal de 32 bits |
| **INT64** | Inteiro com sinal de 64 bits |
| **INT96** | Inteiro com sinal de 96 bits (para timestamps) |
| **FLOAT** | Ponto flutuante de 32 bits (IEEE) |
| **DOUBLE** | Ponto flutuante de 64 bits (IEEE) |
| **BYTE_ARRAY** | Arrays de bytes de comprimento arbitrário |
| **FIXED_LEN_BYTE_ARRAY** | Arrays de bytes de comprimento fixo |

### 1.2.4 Metadados do Parquet

**Metadados Globais (Arquivo):**
- Versão do arquivo.
- Esquema de dados (estrutura das colunas, tipos de dados, estruturas aninhadas).
- Número total de linhas.
- Informações sobre compressão (Snappy, Gzip, Brotli).
- Informações sobre as colunas (nomes, tipos, estatísticas).

**Metadados de Bloco:**
- Intervalos de linhas que o bloco cobre.
- Estatísticas: valor mínimo e máximo de cada coluna, contagem de valores nulos.
- Tamanho do bloco em bytes.
- O arquivo é dividido em **blocos** (sharding) – cada bloco é processado e armazenado de forma independente por um nó do cluster.

**Metadados de Coluna:**
- Nome da coluna.
- Tipo de dado.
- Estatísticas: valor mínimo, máximo, contagem de nulos.
- Codificação (ex.: Delta Encoding, Run Length Encoding).
- Compressão (pode variar por coluna).

### 1.2.5 Vantagens do Parquet
- **Leitura seletiva:** operações realizadas em subconjunto de colunas sem carregar o arquivo inteiro na memória.
- **Alta compactação:** dados compactados, reduzindo tamanho do arquivo.
- **Otimizado para Big Data:** ideal para sistemas distribuídos.
- **Não é relacional:** não possui modelo com múltiplas tabelas e chaves; formato não normalizado.

> [!CAUTION] OBSERVAÇÃO
> **O Parquet NÃO é um formato de dados estruturados no sentido tradicional.** É um formato colunar otimizado para Big Data, amplamente utilizado em ciência de dados e inteligência artificial para armazenamento de datasets.

## 1.3 Tabela Comparativa – Formatos de Arquivos

| CARACTERÍSTICA | CSV | JSON | PARQUET |
|----------------|-----|------|---------|
| **Estrutura** | Linha (tabular) | Hierárquica (chave-valor) | Colunar |
| **Compactação** | Nenhuma (grande) | Opcional | Alta |
| **Leitura seletiva** | Não | Não | Sim (colunas) |
| **Suporte a Big Data** | Limitado | Limitado | Otimizado |
| **Tipos de dados** | Básicos | Simples e complexos | Simples e complexos |
| **Desempenho de leitura** | Lento | Médio | Rápido |
| **Classificação** | Estruturado | Semiestruturado | Colunar (Big Data) |

> [!TIP] DICAS
> - **CSV:** formato em linha, leitura lenta, sem compressão.
> - **JSON/XML:** semiestruturados, hierárquicos, médio desempenho.
> - **Parquet:** formato colunar, alta compressão, leitura seletiva, otimizado para Big Data.

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2023/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/PERFIL: ENGENHEIRO DE DADOS)

A respeito de dados estruturados e não estruturados, julgue o item seguinte. Arquivos .xml, .csv e .json são exemplos de dados estruturados.

**Gabarito:** E (Errado) - **XML e JSON** são dados **semiestruturados**; **CSV** é estruturado.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*