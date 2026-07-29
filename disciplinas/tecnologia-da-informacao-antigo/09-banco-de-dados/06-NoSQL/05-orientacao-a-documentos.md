# Anotações

# NoSQL ORIENTADO A DOCUMENTOS E REVISÃO GERAL DOS TIPOS

## 1. Modelo Orientado a Documentos

### 1.1 Definição e Propósito

- **Especialidade:** Projetado para armazenar e consultar **dados semiestruturados**.
- **Formatos Suportados:** ***JSON*** (JavaScript Object Notation), ***BSON*** (Binary JSON - específico do MongoDB), ***XML*** (eXtensible Markup Language), ***HTML***, ***YAML***.
- **Contexto de Criação:** Surgiu da necessidade de manipular rapidamente grandes volumes de dados vindos da internet (troca de informações entre sistemas, APIs, notas fiscais eletrônicas), onde o modelo relacional impunha muitas "travas" de estrutura.

> ### 1.1.1 Estrutura Interna do Documento
- **Visão Lógica:** Uma base de dados contém uma coleção de documentos. Cada documento é um registro (equivalente a uma linha no SQL).
- **Visão Física:** Internamente, os documentos são organizados como uma **lista de pares Chave-Valor**.
- **Característica de Desempenho:** **Não existe informação sobre um documento fora do próprio documento.** Isso evita *joins* (junções) com outras tabelas, trazendo velocidade.
    - *Exemplo:* Em uma tabela de `Cliente` SQL, o endereço está em outra tabela. No NoSQL de Documento, o endereço está **dentro** do documento do Cliente.

### 1.2 Características Técnicas (Schema-less e Indexação)

- ***Schema-less* (Ausência de Esquema):** Não exige definição prévia de estrutura (tabelas, colunas). Cada documento pode ter seu próprio conjunto de campos.
- **Indexação:**
    - **Mito (Cespe/2016):** É **ERRADO** afirmar que a inexistência de um esquema impossibilita a definição de **índices**.
    - **Realidade:** Bancos orientados a documentos **permitem sim a criação de índices** para acelerar as consultas, mesmo sem um esquema fixo. O índice é uma estrutura auxiliar de ordenação que agiliza a busca.

### 1.3 Casos de Uso

- **Aplicativos *Mobile* e *E-Commerce*:** Armazenamento rápido de perfis de usuário, catálogos de produtos e carrinhos de compras (todas as informações do produto em um único documento).
- **Internet das Coisas (*IoT*):** Dispositivos geram dados em formato JSON/XML.
- ***Analytics* em Tempo Real:** Coleta e processamento de dados *streaming*.
- **Blogs e CMS (Sistemas de Gerenciamento de Conteúdo):** Postagens são naturalmente documentos (título, autor, texto, data).

### 1.4 Atomicidade em Transações (AOCP/2021)

- **Regra Geral:** Em bancos NoSQL baseados em documentos, as transações são **atômicas em nível de documento** (operações em um único JSON/XML são "tudo ou nada").
- **Exceção (Destaque):** Existem produtos como o **RavenDB** que suportam transações com **múltiplas operações** e múltiplos documentos.

## 2. Revisão Consolidada dos 4 Tipos de NoSQL (Matriz de Classificação)

### 2.1 Tabela de Correlação (SGBD x Modelo)

| SGBD NoSQL | MODELO ESTRUTURAL | CARACTERÍSTICA PRINCIPAL |
| :--- | :--- | :--- |
| **Redis** | **Chave-Valor** | Estrutura mais simples (Tabela Hash). *In-memory*. |
| **Cassandra** | **Orientado a Colunas** | Família de colunas; foco em *Big Data* e *Analytics*. |
| **MongoDB** | **Orientado a Documentos** | Armazena JSON/BSON; muito popular na web. |
| **Neo4j** | **Orientado a Grafos** | Nós e Arestas; foco em relacionamentos complexos. |

### 2.2 Questão de Correlação (UFMT/2015 - Adaptada)

| TIPO | PROPRIEDADE / DESCRIÇÃO |
| :--- | :--- |
| **2) Documento** | O conteúdo do dado é organizado em codificações semelhantes à YAML/JSON/XML. |
| **3) Grafo** | Tem enfoque principal no relacionamento entre os dados, com valores armazenados em nós e suas ligações. |
| **1) Chave-Valor** | Para cada identificador único tem-se associado um valor que pode ser de qualquer tipo. |
| **4) Coluna** | Organizado em tabelas com foco nos campos das tuplas (colunas independentes). |

## 3. Análise de Questões Específicas (Pegadinhas e Destaques)

### 3.1 Erro Comum: Limitação de Formatos (Cespe/2022)

- **Afirmativa:** "Com exceção do XML, os documentos armazenados são JSON e BSON."
- **Análise:** **ERRADO**. O XML **É** um dos formatos clássicos de dados semiestruturados suportados por bancos orientados a documentos. A exceção está incorreta.

### 3.2 Erro Comum: Tabelas Hash Distribuídas (Cespe/2015)

- **Afirmativa:** "Banco de dados NoSQL orientado a documentos armazena objetos indexados por chaves utilizando tabelas de hash distribuídas."
- **Análise:** **ERRADO**. Embora **internamente** um documento seja um conjunto de pares chave-valor, o banco em si não é uma **tabela hash distribuída** (esta definição se aplica melhor ao modelo **Chave-Valor** puro, como o DynamoDB).

### 3.3 Erro Comum: Formato de Linhas e Colunas (FCC/2018)

- **Afirmativa:** Identificar quais NoSQL modelam dados no formato de linhas e colunas.
- **Análise:**
    - **Orientado a Colunas:** Sim (explicitamente usa este formato).
    - **Chave-Valor:** Pode ser visualizado como uma tabela de 2 colunas.
    - **Documento:** Pode ser visualizado como coleções de colunas (chaves).
    - **Grafos:** **NÃO** podem ser enxergados como linha/coluna (são nós e arestas).
- **Resposta:** Apenas Grafos **NÃO** usa esta modelagem visual.

## 4. Gabarito das Questões de Documentos e Revisão

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (Cespe 2014) | **C** | Orientado a documentos é apropriado para dados semiestruturados. |
| **2** (Cespe 2022) | **E** | XML também é suportado. |
| **3** (Cespe 2016) | **E** | Ausência de esquema **não** impossibilita índices. |
| **4** (AOCP 2021) | **C** | Transações atômicas em nível de documento; RavenDB é exceção. |
| **5** (Cespe 2015) | **E** | Documento contém pares chave-valor; banco não é tabela hash distribuída. |
| **6** (Cespe 2021) | **E** | Não utilizam expressões regulares como método padrão de busca. |
| **7** (AOCP 2019) | **A** | Categorias: Chave-valor, Documentos, Grafos (e Colunas). |
| **8** (AOCP 2018) | **E** | Cassandra (Coluna), Neo4j (Grafo), MongoDB (Documento), Redis (Chave-Valor). |
| **9** (IDECAN 2022) | **E** | Redis (*in-memory* Chave-Valor) e Neo4j (Grafo). |
| **10** (UFMT 2015) | **A** | Sequência: 2 (Doc), 3 (Grafo), 1 (Chave), 4 (Coluna). |
| **11** (FCC 2018) | **B** | Chave-Valor e Documentos **podem** ser visualizados como linha/coluna; Grafos não. |
| **12** (FUNDATEC 2020) | **B** | Cassandra (2), MongoDB (3), Redis (1). |

## 5. Mapa Mental dos SGBDs NoSQL (Para Memorização)

- **Chave-Valor** -> **Redis** (mais famoso), DynamoDB.
- **Documentos** -> **MongoDB** (mais famoso), CouchDB, RavenDB.
- **Grafos** -> **Neo4j** (mais famoso).
- **Colunar** -> **Cassandra** (mais famoso), HBase.