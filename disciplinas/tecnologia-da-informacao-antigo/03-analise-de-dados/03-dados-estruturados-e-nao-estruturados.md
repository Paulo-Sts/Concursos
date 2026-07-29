# Anotações

# Dados Estruturados e Não Estruturados

## 1.1 Dados Estruturados

### 1.1.1 Características
- **Formato definido** = rigidez de formato.
- **Facilidade de análise** – os dados são facilmente consultáveis.
- **Integração simples** entre diferentes fontes de dados estruturados.

### 1.1.2 Exemplos Comuns
- Bancos de dados relacionais.
- Planilhas Excel.

### 1.1.3 Ferramentas de Análise
- **SGBD Relacionais (RDBMS):** MySQL, PostgreSQL, Oracle, SQL Server.
- **Ferramentas de BI:** Tableau, Power BI, QlikView.
  - Nestas ferramentas, selecionam-se diversas fontes de dados (normalmente estruturadas); elas são integradas por meio de **ETL** (Extração, Transformação e Carga); colocadas no modelo dimensional (Tabela Fato e Tabela de Dimensões); armazenadas em um **Data Warehouse**; e, por meio de operações **OLAP**, organizadas para tomada de decisão gerencial.
- **ETL Tools:** Talend, Apache Nifi.
  - Trabalham com diversas bases de dados, extraindo-as de produção para uma área intermediária onde são realizadas as transformações, criadas as tabelas finais que farão parte do destino e, então, carregadas no destino (ex.: Data Warehouse).

> [!TIP] DICAS
> - Ao se falar em **BI tradicional**, há uma relação com dados estruturados.
> - São exceções os casos em que os examinadores citam **"BI modernos"**, que também trabalham com dados não estruturados.

## 1.2 Dados Não Estruturados

### 1.2.1 Características
- **Formato livre** – sem estrutura pré-definida.
- **Diversidade** de tipos e formatos.
- **Análise complexa** – o dado é binário; para extrair informações, é necessária intervenção humana ou de **Inteligência Artificial**.

> [!CAUTION] OBSERVAÇÃO
> **Dados não estruturados exigem processamentos mais sofisticados para extração de informações** – estão diretamente relacionados ao conceito de **Big Data**.

### 1.2.2 Exemplos Comuns
- Arquivos de texto.
- E-mails.
- Imagens.
- Vídeos.
- Arquivos de áudio.
- Documentos PDF.
- Postagens em redes sociais.

### 1.2.3 Ferramentas de Análise
- **Sistemas de Armazenamento:** Hadoop HDFS, Amazon S3, Google Cloud Storage.
- **Bancos de Dados NoSQL:** Cassandra, Amazon DynamoDB, Neo4j.
- **Ferramentas de Análise de Texto:** Apache Lucene, Elasticsearch, Solr.
- **Ferramentas de NLP (Processamento de Linguagem Natural):** NLTK, SpaCy, TensorFlow, BERT.
- **Processamento de Imagens e Vídeos:** OpenCV, TensorFlow, PyTorch.

> [!TIP] DICAS
> - Para analisar dados não estruturados, é necessário montar um modelo de **inteligência artificial**, que passa por um processo de treinamento e validação, utilizando bibliotecas como as de Python, resultando em uma **rede neural artificial treinada**.
> - **A pesquisa de dados não estruturados é feita por meio de algoritmos complexos de aprendizado de máquina.**

## 1.3 Dados Semiestruturados

- Estão entre os dados estruturados e não estruturados.
- Têm um formato **não tabular**, mas apresentam um **mínimo de estrutura**.
- Exemplo: **XML** (possui tags que organizam os dados hierarquicamente).

## 1.4 Tabela Comparativa – Estruturados x Não Estruturados

| ASPECTO | ESTRUTURADOS | NÃO ESTRUTURADOS |
|---------|--------------|------------------|
| **Formato** | Definido/rígido | Livre |
| **Análise** | Fácil (consultas SQL) | Complexa (IA/ML) |
| **Integração** | Simples | Desafiadora |
| **Exemplos** | BD relacionais, planilhas | Textos, imagens, vídeos, áudios, redes sociais |
| **Ferramentas** | RDBMS, BI, ETL | NoSQL, NLP, IA, armazenamento distribuído |

> [!TIP] DICAS
> - **Se o dado cabe em uma tabela, é estruturado. Se não cabe em uma tabela, é dado não estruturado.**
> - **Banco de dados** está relacionado a dados **estruturados** (especialmente os relacionais).
> - **Flexibilidade** se relaciona a dados **não estruturados**.

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2021/SERPRO/ANALISTA/ESPECIALIZAÇÃO: CIÊNCIA DE DADOS)

Julgue o item subsequente relativo a conceitos de ingestão de dados estruturados, semiestruturados, não estruturados e em streaming.

Os dados não estruturados constam de bancos de dados relacionais que são eminentemente pesquisáveis tanto por meio de consultas realizadas por humanos quanto por meio daquelas realizadas por algoritmos que usam tipos de dados e nomes de campos, como alfabéticos ou numéricos, moeda ou data.

**Gabarito:** E (Errado) - Essas características correspondem a dados **estruturados**. A pesquisa de dados não estruturados é feita por algoritmos complexos de aprendizado de máquina.

## Questão 02
(CESPE/CEBRASPE/2022/TCE-RJ/ANALISTA DE CONTROLE EXTERNO)

Julgue o item a seguir, referente à informação e a dados, estruturados e não estruturados.

No contexto de Big Data, os dados em formato de textos longos, de vídeos ou de imagens são considerados dados estruturados, quando armazenados em um campo de um banco de dados relacional.

**Gabarito:** E (Errado) - O simples armazenamento em um campo de banco de dados relacional **não** torna os dados estruturados – eles permanecem não estruturados.

## Questão 03
(INSTITUTO CONSULPLAN/MPE MG/ANALISTA/TECNOLOGIA DA INFORMAÇÃO/GESTÃO DE PROJETOS DE TI/2023)

Dado é a representação utilizada para gerar uma informação. Um dado pode ser estruturado ou não estruturado. Em relação às diferenças entre dados estruturados e dados não estruturados, marque V para as afirmativas verdadeiras e F para as falsas.

( ) Em dados estruturados, dados de um mesmo registro possuem relação entre eles.
( ) Textos, documentos, banco de dados, redes sociais, imagens, vídeos e áudios são exemplos de dados não estruturados.
( ) Dados estruturados permitem que tipos de dados diferentes das estruturas preestabelecidas sejam carregados.
( ) Em dados estruturados, atributos e campos são definidos por um esquema.

A sequência está correta em

a) F, V, V, F.
b) V, V, V, V.
c) V, F, F, V.
d) F, F, F, F.

**Gabarito:** c

## Questão 04
(CESPE/CEBRASPE/SEPLAN RR/ANALISTA DE PLANEJAMENTO E ORÇAMENTO APO/ÁREA TECNOLOGIA DA INFORMAÇÃO/2023)

Com base nos conceitos de dados estruturados e não estruturados, de análise exploratória de dados e de dados abertos, julgue os itens seguintes. Dados de redes sociais são exemplos de dados não estruturados.

**Gabarito:** C (Correto)

## Questão 05
(FUNDATEC/BRDES/ANALISTA/CIÊNCIA DE DADOS/2023)

Assinale a alternativa que contém um exemplo de dados não estruturados.

a) Dados extraídos de uma rede social de um banco podem ser classificadas em polaridades como positivas ou negativas, ou agrupadas por similaridade de assunto.
b) Um sistema bancário armazena dados sobre seus clientes, sobre suas respectivas contas bancárias e sobre as transações executadas sobre tais contas.
c) Funcionários de um departamento de recursos humanos observam os candidatos a uma vaga de emprego e fazem anotações sobre as suas atitudes durante a realização de atividades de um processo de seleção.
d) Uma empresa deseja lançar um novo produto e, para isso, realiza pesquisas sobre sua aceitação com um conjunto específico de pessoas que representa o público-alvo.
e) Uma corrida de Fórmula 1 na qual se medem os tempos que cada piloto gasta para chegar em diferentes trechos de um circuito.

**Gabarito:** a

## Questão 06
(CESPE/CEBRASPE/DPE RO/ANALISTA DA DEFENSORIA PÚBLICA/REDES E COMUNICAÇÃO DE DADOS/2022)

As fontes de dados não estruturados incluem

a) a planilha eletrônica.
b) a rede social.
c) a linguagem de programação.
d) o arquivo XML.
e) o banco de dados.

**Gabarito:** b

## Questão 07
(IBADE/SES MG/ESPECIALISTA EM POLÍTICAS E GESTÃO DA SAÚDE/TI/2022)

Os dados constantes em uma planilha eletrônica, organizados em linhas e colunas, são chamados dados:

a) alinhados.
b) estruturados.
c) indexados.
d) relacionados.
e) descriminados.

**Gabarito:** b

## Questão 08
(CONSULPLAN/MPE PA/ANALISTA DE SISTEMAS/SUPORTE À REDE DE COMPUTADORES/2022)

Dados são um conjunto de fatos em estado bruto que podem ser utilizados para tomadas de decisão. Os dados podem ser divididos entre estruturados e não estruturados. Sobre os dados estruturados, assinale a afirmativa correta.

a) Mensagens de e-mail são dados estruturados.
b) Dados estruturados são organizados em linhas e colunas.
c) Dados estruturados são armazenados em arquivos no formato "TXT".
d) Mecanismos de busca possuem dificuldade para pesquisar dados estruturados.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | E |
| 03 | c |
| 04 | C |
| 05 | a |
| 06 | b |
| 07 | b |
| 08 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*