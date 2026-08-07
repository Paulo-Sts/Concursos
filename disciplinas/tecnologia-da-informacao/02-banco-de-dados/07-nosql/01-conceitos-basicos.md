# NoSQL

## 1. Contexto Histórico e Motivação
- O banco de dados é o local destinado ao armazenamento de dados consumidos por outros sistemas.
- Exemplo contextual: Nos anos 1990, uma locadora de carros usaria um SGBD (Sistema Gerenciador de Banco de Dados) com tabelas relacionadas (carros, clientes, locação), caracterizando o modelo relacional.
- Com a expansão da internet e o surgimento de arquivos multimídia (imagem e som), os bancos de dados relacionais apresentavam baixa performance.
- Para resolver esse problema, surgiram os bancos de dados não relacionais (NoSQL). Exemplo: O Facebook criou o Cassandra, um NoSQL focado em Big Data.

## 2. NoSQL: Definição e Conceitos
- NoSQL significa Not Only SQL (Não Somente SQL).
- Pode ser utilizado para fazer consultas em SQL.
- Bancos de dados distribuídos não relacionais:
  - Os dados estão armazenados em diversos servidores ao redor do mundo, não restritos a um computador local;
  - Os dados são replicados em diversos nós da rede;
  - São não relacionais por não utilizarem tabelas inter-relacionadas.

### 2.1 Aspectos para Identificar se é Relacional ou não Relacional
- Volume de dados;
- Velocidade;
- Velocidade de criação dos dados.

### 2.2 Características Adicionais dos NoSQL
- Trabalham com Big Data;
- Não possuem modelo de dados fixo. Diferente do modelo relacional, no Big Data é possível guardar um dado sem que a tabela tenha sido criada anteriormente;
- Não são orientados a objeto. A orientação a objeto é um paradigma de programação que cria objetos em vez de visualizar dados simples.

## 3. Características do NoSQL
- Aceitam SQL: É possível realizar consultas SQL dentro do banco não relacional;
- Trabalham primariamente com dados não estruturados e semiestruturados:
  - Dado estruturado: estrutura fixa e rígida;
  - Dado não estruturado: dados que não podem ser organizados, como vídeos, imagens, textos e livros;
  - Dado semiestruturado: uso de tags de marcação para delimitar, como XML e HTML.
- Aceitam diversos tipos de modelo de dados, incluindo schema-less;
- Dados distribuídos globalmente;
- Escalabilidade horizontal: a capacidade do banco de dados é aumentada com a adição de mais computadores na rede.
  - Escalabilidade é o poder de aumentar a capacidade de armazenamento, memória e processamento de maneira rápida e invisível para o usuário.
  - No modelo relacional, a escalabilidade é vertical: para aumentar a capacidade, é necessário instalar mais recursos (HD, RAM, CPU) na máquina.

## 4. Vantagens do NoSQL
- Rapidez de acesso;
- Disponibilidade dos dados: tolerância à partição, os dados replicados permitem a recuperação mesmo com falhas em nós;
- Escalabilidade: instalação em clusters com processamento distribuído. Um cluster é um conjunto de computadores que armazenam e processam dados em paralelo;
- Replicação de dados: protege contra ataques ou falhas físicas (ex.: incêndio), garantindo recuperação pelos demais nós. Isso resulta em zero downtime;
- Flexibilidade: tanto nos modelos de dados quanto no armazenamento de vários tipos de dados;
- Facilidade para os programadores.

## 5. Quando usar NoSQL?
- Quando os dados mudam constantemente;
- Para armazenar dados semiestruturados e não estruturados;
- Em desenvolvimento ágil: solução para modelos de desenvolvimento pesados e detalhados, comum em softwares com versões atualizadas constantemente;
- Em Big Data e análise de dados: excelente para ciência de dados e inteligência artificial;
- Quando não há requisitos rígidos de consistência e integridade;
- Em arquiteturas escaláveis;
- Em micro-serviços e real-time streaming;
- Na Internet das Coisas (IoT): dispositivos como celulares, carros e geladeiras produzem dados que precisam ser armazenados.

> [!TIP] DICAS:
> - Use NoSQL para situações que exigem alta disponibilidade, escalabilidade horizontal e lidam com grandes volumes de dados variados.
> - A flexibilidade e a velocidade são os grandes atrativos para projetos ágeis.

## 6. O que o NoSQL não Possui
- Esquemas/modelos de dados pré-definidos e estáveis;
- Operações ACID (Atomicity, Consistency, Isolation, Durability). Essas operações são típicas de bancos relacionais e garantem a confiabilidade das transações;
- Normalização: as tabelas são estanques, não há necessidade de normalização;
- Imunidade a SQL Injection: a injeção de SQL é uma estratégia de invasão que insere consultas SQL em campos inadequados. O NoSQL, apesar de aceitar SQL, não oferece a mesma proteção nativa;
- Menor variedade de possibilidades de consultas;
- Padronização de dados, modelos e esquemas.

> [!CAUTION] OBSERVAÇÃO:
> - A ausência de ACID e de normalização torna o NoSQL menos adequado para sistemas que exigem consistência rigorosa e transações confiáveis.

## 7. ACID (Atomicidade, Consistência, Isolamento e Durabilidade)
- Atomicidade: as transações são indivisíveis, não sendo possível fazer atualizações em momentos distintos;
- Consistência: as regras de integridade devem ser respeitadas (ex.: validação de dígitos de CPF);
- Isolamento: transações em paralelo não interferem umas nas outras;
- Durabilidade: as transações devem persistir no banco de dados.

## 8. Comparativo: NoSQL x Bases Relacionais
| CARACTERÍSTICA          | NOSQL                                                                   | BASES RELACIONAIS                                                       |
|-------------------------|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Linguagem               | SQL e linguagens SQL-Like                                               | SQL                                                                     |
| Esquemas                | Registros podem ser criados sem esquemas pré-definidos                  | Pré-definidos e rígidos (cada campo deve ser detalhado)                 |
| Escalabilidade          | Vertical: uma máquina precisará de mais RAM, CPU e HD                   | Horizontal: são adicionadas máquinas                                    |
| Big Data                | Suportado                                                               | Escalabilidade vertical dificulta                                       |
| Propriedades            | CAP ou BASE                                                             | ACID (Atomicity, Consistency, Isolation, Durability)                    |
| Tipos de dados          | Estruturados, semi e não estruturados                                   | Estruturados                                                            |
| Queries complexas       | Não                                                                     | Sim                                                                     |

## 9. Teorema CAP (Teorema de Brewer)
- É impossível que o armazenamento de dados distribuído forneça simultaneamente mais de duas das três garantias seguintes:
  - Consistência: os clientes veem os mesmos dados em um instante de tempo. Os dados gravados em um nó devem ser distribuídos para outro nó para que a transação seja finalizada;
  - Disponibilidade (availability): cada pedido recebe uma resposta (sem erro);
  - Partição tolerante a falhas: o cluster deve continuar a funcionar mesmo com uma ou mais falhas de comunicação entre os nós.

## 10. BASE (Basically Available, Soft State with Eventual Consistency)
- Valoriza a disponibilidade sobre a consistência;
- Basically Available: operações de escrita e leitura estão disponíveis, mas sem consistência automática (a atualização dos nós pode levar algum tempo);
- Soft State: o estado dos dados não é garantido sem consistência;
- Eventual Consistency: alterações em um banco de dados não são propagadas de forma imediata.

> [!TIP] DICAS:
> - O Teorema CAP e o BASE são fundamentais para entender as escolhas arquiteturais de sistemas distribuídos. Lembre-se: em NoSQL, muitas vezes se abre mão da consistência imediata em favor da disponibilidade e da tolerância a falhas.

## 11. Tipos de NoSQL

### 11.1 Chave-Valor
- Banco de dados que armazena pares de chave e valor.
- Exemplos: Redis (o mais famoso), DynamoDB, Riak, Tokyo Cabinet/Tyrant, Voldemort, Memcached, Scalaris, Amazon SimpleDB e Oracle BDB.

### 11.2 Documentos
- Armazena dados em formato de documentos (ex.: JSON, BSON).
- Exemplos: MongoDB (o mais famoso), Elasticsearch, DocumentDB, CouchDB, CouchBase, RavenDB, OrientDB, IBM Cloudant, CrateDB, BaseX e Lotus Notes.

### 11.3 Grafos (Graph)
- Estrutura de nós ligados por arestas, representando relacionamentos complexos (ex.: João é amigo de Maria, que é amiga de José).
- Exemplos: Neo4j (o mais famoso), Neptune, HyperGraphDB, Infinite Graph, JanusGraph, InfoGrid, Titan e FlockDB.

### 11.4 Colunar
- Tabelas com colunas independentes entre si.
- Exemplos: Cassandra (o mais famoso), HBASE, Bigtable e Hypertable.

## 12. Não são Exemplos de NoSQL
- Microsoft SQL Server;
- PostgreSQL;
- MySQL;
- Oracle;
- Firebird;
- Microsoft Access;
- IBM DB2.

> [!CAUTION] OBSERVAÇÃO:
> - Embora alguns bancos NoSQL aceitem SQL, a lista acima se refere a bancos de dados relacionais tradicionais. Não confunda: aceitar SQL não torna um banco relacional; a arquitetura e a forma de armazenamento são determinantes.