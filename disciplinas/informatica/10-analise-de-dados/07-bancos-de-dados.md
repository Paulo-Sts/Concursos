# Bancos de Dados

## 1. Conceitos Básicos
- **Banco de Dados (BD):** Conjunto de dados armazenados de forma estruturada e organizada, que tratam de um mesmo assunto.
- **Sistema Gerenciador de Banco de Dados (SGBD):** Conjunto de softwares responsáveis pelo gerenciamento de um ou mais bancos de dados. Controla acesso, definição, manipulação e transações.

#### Principais SGBDs relacionais
- Oracle
- SQL Server
- DB2 (IBM)
- MySQL (livre)
- PostgreSQL (livre)
- MariaDB (livre)
- SQLite (livre)
- Microsoft Access (simples, não corporativo)

#### SGBDs NoSQL
- MongoDB (documentos)
- Redis (chave-valor)
- Cassandra (colunas)
- Neo4j (grafos)

## 2. Componentes de um BD
- **Tabelas:** Estruturas básicas de armazenamento (também chamadas de relações).
- **Linhas/Registros/Tuplas:** Instâncias de dados.
- **Colunas/Campos/Atributos:** Propriedades que caracterizam um registro.
- **Chaves:**
  - **Primária (PK):** Identifica unicamente cada registro.
  - **Estrangeira (FK):** Referencia a PK de outra tabela.
  - **Surrogada:** Chave numérica autoincremental.
- **Índices:** Aceleram buscas.
- **Restrições (Constraints):** Regras que garantem integridade (ex.: NOT NULL, UNIQUE, CHECK).
- **Gatilhos (Triggers):** Procedimentos automáticos disparados por eventos.
- **Visões (Views):** Consultas armazenadas que criam tabelas virtuais.

## 3. Modelagem de Dados

#### Níveis de modelagem
- **Conceitual:** Abstrato, independente de tecnologia (MER/DER).
- **Lógico:** Estruturas de armazenamento, dependente da tecnologia.
- **Físico:** Implementação no SGBD (DDL, índices, restrições).

#### Elementos do DER
- **Entidades:** Fortes (independentes), fracas (dependentes), associativas.
- **Atributos:** Simples, composto, derivado, multivalorado, chave.
- **Relacionamentos:** Associações entre entidades.
  - Cardinalidade: 1:1, 1:N, N:N.
  - Restrições: Estrutural, participação (total/parcial).

## 4. SQL (Structured Query Language)

#### Tipos de Linguagem
- **DDL (Data Definition Language):** CREATE, ALTER, DROP, TRUNCATE.
- **DML (Data Manipulation Language):** SELECT, INSERT, UPDATE, DELETE.
- **DCL (Data Control Language):** GRANT, REVOKE.
- **DTL (Data Transaction Language):** COMMIT, ROLLBACK, SAVEPOINT.

#### Exemplo de SELECT
```sql
SELECT coluna1, coluna2
FROM tabela
WHERE condição
ORDER BY coluna ASC/DESC;
```

#### Transações e ACID
- **Atomicidade:** Tudo ou nada.
- **Consistência:** Dados válidos antes e depois.
- **Isolamento:** Transações não interferem entre si.
- **Durabilidade:** Alterações persistem após commit.

## 5. Bancos de dados NoSQL

#### Características
- Não relacionais.
- Escaláveis, de alta performance e flexíveis.
- Ideais para Big Data.
- Priorizam performance em detrimento da integridade.

#### Tipos
- **Chave-Valor:** Ex.: Redis.
- **Documentos:** Ex.: MongoDB.
- **Colunas:** Ex.: Cassandra.
- **Grafos:** Ex.: Neo4j.

#### Observações
- Esquema flexível (não rígido).
- Dados semiestruturados ou não estruturados.
- Distribuídos em clusters.

## 6. Integridade e Segurança
- **Integridade Referencial:** Garante consistência entre tabelas relacionadas.
- **Views:** Restringem acesso a dados sensíveis.
- **Permissões:** Controladas via DCL (GRANT, REVOKE).