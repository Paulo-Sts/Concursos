# Banco da Dados NoSQL

## 1. Banco de Dados e Contexto Histórico

- O banco de dados é o local destinado ao armazenamento de dados que serão consumidos por outros sistemas.
- Nos anos 1990, sistemas de locadoras utilizavam o **Sistema Gerenciador de Banco de Dados (SGBD)** com tabelas relacionadas entre si, caracterizando o **banco de dados relacional**.
- Com a expansão da internet e a necessidade de armazenar imagens e sons (redes sociais), os bancos relacionais apresentaram problemas de *performance*.
- A solução foi a criação de bancos de dados não relacionais, denominados **NoSQL**, projetados para trabalhar com grandes bases de dados (*Big Data*). Exemplo citado: **Cassandra**, criado pelo Facebook.

> ### 1.1 Aspectos para Classificação da Base de Dados
- Para determinar se uma base é relacional ou não relacional, verifica-se:
- Volume de dados;
- Velocidade;
- Velocidade de criação dos dados.

## 2. Definição e Características do NoSQL

### 2.1 Definição (Conceitos Fundamentais)

- **NoSQL** significa ***Not Only SQL*** (Não Somente SQL). É um equívoco comum achar que significa "Não SQL".
- **Aceitação de SQL:** É possível utilizar bancos NoSQL para fazer consultas em SQL (*SQL-Like*).
- **Bancos de dados distribuídos não relacionais:**
    - Os dados estão armazenados em diversos servidores e locais do mundo, sem restrição a um computador local.
    - Os dados são **replicados** em diversos nós da rede.
    - **Não relacional:** Não envolve o uso de tabelas com relações rígidas entre si.
- **Big Data:** Trabalham especificamente com grandes volumes de dados.
- **Modelo de Dados Flexível:** Não possuem modelo de dados fixo (*schema-less*).
    - Em bancos relacionais, a arquitetura de tabelas e relacionamentos deve ser pré-definida.
    - No NoSQL, é possível guardar um dado em uma "tabela" sem que ela tenha sido formalmente criada antes, o que aumenta a performance para *Big Data*.
- **Paradigma:** Não são orientados a objeto (paradigma de programação).

### 2.2 Características Técnicas

- **Tipos de Dados:** Trabalham primariamente com dados **não estruturados** e **semiestruturados**.
    - **Dado Estruturado:** Estrutura fixa e rígida (Ex: Tabela Relacional).
    - **Dado Não Estruturado:** Impossível organizar rigidamente (Ex: Vídeo, textos longos).
    - **Dado Semiestruturado:** Uso de *tags* de marcação (Ex: XML, HTML).
- **Escalabilidade:**
    - **Horizontal:** A capacidade do banco de dados é aumentada adicionando-se mais computadores à rede (*cluster*).
    - **Vertical (Modelo Relacional):** Aumenta-se a capacidade do servidor instalando mais HD, RAM ou CPU na mesma máquina.

### 2.3 Vantagens Específicas

- **Rapidez de acesso** e **Disponibilidade dos dados** (Tolerância à partição; capacidade de recuperação via replicação de nós).
- ***Zero Downtime:*** Proteção contra falhas ou desastres em um nó, pois os demais mantêm o sistema ativo.
- **Flexibilidade:** Tanto nos modelos de dados quanto no armazenamento de variados tipos de conteúdo.
- **Observação do Professor:** "Os programadores gostam".

### 2.4 Quando Utilizar (Casos de Uso)

- Dados que mudam constantemente.
- Armazenamento de dados semi e não estruturados.
- **Desenvolvimento ágil** (ciclos rápidos de atualização de *software*).
- ***Big Data*** e análise de dados (Ciência de Dados e Inteligência Artificial).
- **Sem requisitos rígidos de consistência e integridade** imediata.
- Arquiteturas escaláveis, **micro-serviços**, *real-time streaming*.
- **Internet das Coisas (*IoT*):** Dispositivos como carros e geladeiras que geram fluxo constante de dados.

## 3. Limitações e Ausências no NoSQL (O que NÃO tem)

- **Esquemas/modelos de dados pré-definidos e estáveis** (característica, não defeito).
- **Operações ACID** (não garantem Atomicidade, Consistência, Isolamento, Durabilidade no sentido estrito do SQL relacional).
- **Normalização:** As "tabelas" são estanques, sem o rigor de normalização relacional.
- **Imunidade a SQL Injection:** Não são imunes; *SQL Injection* continua sendo uma estratégia de invasão que consiste em inserir consultas maliciosas em campos de entrada.
- **Menor variedade de possibilidades de consultas** complexas.
- **Padronização** (dados, modelos, esquemas).

## 4. Análise Comparativa: NoSQL x Bases Relacionais

| CARACTERÍSTICA | NOSQL | BASES RELACIONAIS |
| :--- | :--- | :--- |
| **Linguagem** | SQL e linguagens *SQL-Like* | SQL |
| **Esquemas** | Registros podem ser criados sem esquemas pré-definidos | Pré-definidos e rígidos (detalhamento obrigatório) |
| **Escalabilidade** | **Horizontal** (adição de máquinas) | **Vertical** (mais RAM, CPU, HD na mesma máquina) |
| ***Big Data*** | Suportado nativamente | Escalabilidade vertical dificulta o uso |
| **Propriedades** | **CAP** ou **BASE** | **ACID** (Atomicity, Consistency, Isolation, Durability) |
| **Tipos de Dados** | Estruturados, Semi e Não estruturados | Estruturados (predominantemente) |
| ***Queries* Complexas** | Não | Sim |

## 5. Teoremas e Propriedades Fundamentais

### 5.1 Teorema CAP (Teorema de Brewer)

- É impossível que o armazenamento de dados distribuído forneça simultaneamente mais de duas das três garantias seguintes:
    1.  **Consistência (*Consistency*):** Todos os clientes veem os mesmos dados no mesmo instante. A gravação em um nó deve ser replicada para finalizar a transação.
    2.  **Disponibilidade (*Availability*):** Cada pedido recebe uma resposta (sem erro), mesmo que o dado não esteja 100% atualizado.
    3.  **Tolerância a Partição (*Partition Tolerance*):** O *cluster* continua funcionando mesmo com falhas de comunicação entre os nós.

### 5.2 Propriedade BASE

- **BASE** é a sigla para ***Basically Available, Soft State with Eventual Consistency***.
- **Valoriza a Disponibilidade sobre a Consistência.**
- **Basically Available (Basicamente Disponível):** Operações de escrita e leitura estão disponíveis, mas sem consistência automática imediata (a atualização entre nós pode levar um tempo).
- **Soft State (Estado Suave):** O estado dos dados não é garantido sem a devida consistência eventual.
- **Eventual Consistency (Consistência Eventual):** As alterações não são propagadas de forma imediata, mas o sistema garante que em algum momento futuro todos os nós estarão consistentes.

> ### 5.2.1 Comparativo de Propriedades (ACID x BASE)
- **ACID:** Atomicidade, Consistência, Isolamento, Durabilidade.
    - **Atomicidade:** Transações são indivisíveis (tudo ou nada).
    - **Consistência:** Regras de integridade devem ser respeitadas (Ex: dígitos do CPF).
    - **Isolamento:** Transações em paralelo não interferem umas nas outras.
    - **Durabilidade:** Transações confirmadas devem persistir.
- **BASE:** Voltado para disponibilidade em sistemas distribuídos, tolerando atrasos na consistência.

## 6. Tipos de Bancos NoSQL e Exemplos

### 6.1 Chave-Valor
- **Modelo:** Estrutura simples de par "chave" e "valor".
- **Exemplos (Destacado):** **Redis** (o mais famoso), DynamoDB, Riak, Voldemort, Memcached, Amazon SimpleDB, Oracle BDB.

### 6.2 Documentos
- **Modelo:** Armazena documentos (JSON, XML, BSON) auto-contidos.
- **Exemplos (Destacado):** **MongoDB** (o mais famoso), Elasticsearch, CouchDB, CouchBase, RavenDB, OrientDB.

### 6.3 Grafos (*Graph*)
- **Modelo:** Nós ligados por arestas para representar relacionamentos complexos (Ex: "João é amigo de Maria, que é amiga de José").
- **Exemplos (Destacado):** **Neo4j** (o mais famoso), Neptune, JanusGraph, Titan, FlockDB.

### 6.4 Colunar (*Wide Column*)
- **Modelo:** Tabelas onde as colunas são independentes entre si, otimizadas para consultas em grandes volumes de dados.
- **Exemplos (Destacado):** **Cassandra** (o mais famoso), HBASE, Bigtable, Hypertable.

## 7. Exemplos NÃO Classificados como NoSQL

- Os seguintes sistemas são **SGBDs Relacionais** (SQL) e **NÃO** são exemplos de NoSQL:
    - Microsoft SQL Server;
    - PostgreSQL;
    - MySQL;
    - Oracle;
    - Firebird;
    - Microsoft Access;
    - IBM DB2.