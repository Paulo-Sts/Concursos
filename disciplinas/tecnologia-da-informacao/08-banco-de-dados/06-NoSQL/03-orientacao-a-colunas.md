# Anotações

# NoSQL ORIENTADO A COLUNAS E CHAVE-VALOR

## 1. Modelo Orientado a Colunas (Wide Column Store)

### 1.1 Conceito e Estrutura

- **Definição:** Armazena os dados como uma coleção de colunas conhecida como **Família de Colunas** (*Column Family*).
- **Flexibilidade de Linhas:** As linhas **não precisam** ter as mesmas colunas (cada linha pode ter um conjunto diferente de atributos).
- **Tratamento Independente:** Cada coluna é tratada (consultada, lida, agregada) separadamente.
- **Estrutura Física:** As colunas e suas subcolunas ficam separadas em grandes blocos de armazenamento.
- **Comparação com SQL:**
    - **SQL:** Para dados complexos (ex: endereço com subatributos), seria necessário criar uma tabela separada e relacionar via chave estrangeira.
    - **NoSQL Colunar:** Utiliza-se uma **única tabela** onde as colunas são subdivididas (Ex: Coluna `Endereço` contendo `Rua`, `Cidade`, `CEP` como propriedades internas).

> ### 1.1.1 Contexto de Aplicação (Ciência de Dados)
- **Motivação:** Em *Machine Learning*, trabalha-se com *DataFrames* (tabelas com muitos atributos). Bancos orientados a colunas são otimizados para transformações de dados em colunas específicas (Ex: converter coluna numérica em categórica) sem a complexidade de código do SQL tradicional.

### 1.2 Casos de Uso

- **BI** (*Business Intelligence*).
- ***Analytics***.
- **Processamento de *Big Data***.

### 1.3 Apache Cassandra (O Principal SGBD Colunar)

- **Origem:** *Open-source* criado originalmente pelo **Facebook**.
- **Modelo de Dados:** Utiliza pares de **Chave-Valor** e **Tabelas**.
- **Estrutura de Linhas:** As linhas de uma tabela (ou família de colunas) podem conter uma quantidade **variável** de colunas.
- **Linguagem:** Utiliza a ***Cassandra Query Language*** (CQL).
- **Interface:** O *shell* para executar CQL é o **`cqlsh`**.

#### 1.3.1 Estrutura Lógica (Keyspace e Tabela)

| CONCEITO CASSANDRA | EQUIVALENTE NO SQL RELACIONAL |
| :--- | :--- |
| **Keyspace** | **Esquema/Banco de Dados** (*Database/Schema*) |
| **Tabela** | **Tabela** (*Table*) |

- **Keyspace:** Contém opções que são aplicadas em todas as tabelas contidas nele.
- **Comandos de Gerenciamento de Keyspace:**
    - **Criar:** `CREATE KEYSPACE nome_keyspace;`
    - **Selecionar:** `USE nome_keyspace;`
    - **Alterar:** `ALTER KEYSPACE nome_keyspace;`
    - **Apagar:** `DROP KEYSPACE nome_keyspace;`

#### 1.3.2 CQL (Cassandra Query Language) - Comandos Essenciais

- **Criação de Tipos Personalizados (UDT):**
    - Permite criar **Tipos Definidos pelo Usuário** (*User-Defined Types*).
    - **Sintaxe Correta (AOCP/2020):** `CREATE TYPE endereco (rua text, cidade text, num int, complemento text);`
- **Manipulação de Dados (DML):**
    - **Inserir:** `INSERT INTO usuarios ...`
    - **Selecionar:** `SELECT nome, ocupacao FROM users WHERE user_id = 199;` (É possível usar `WHERE`, funções de agregação como `COUNT(*)` e formatação de saída como `JSON`).
    - **Atualizar:** `UPDATE ... SET ... WHERE ...`
    - **Apagar:** `DELETE ... FROM ... WHERE ...`