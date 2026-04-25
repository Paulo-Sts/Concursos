# Anotações

# NoSQL ORIENTADO A COLUNAS E CHAVE-VALOR

## 2. Modelo Orientado a Chave-Valor

### 2.1 Conceito e Estrutura

- **Definição:** Cada item do banco de dados é armazenado como um **par** composto por uma **Chave** (*Key*) única e um **Valor** (*Value*).
- **Simplicidade:** Funcionalmente, é como uma **tabela com duas colunas** (Chave, Valor) ou uma grande **Tabela Hash**.
- ***Schema-less:*** Não exige esquema pré-definido.
- **Conteúdo do Valor:** Pode ser de qualquer tipo (número, texto, imagem, documento, JSON).

### 2.2 Casos de Uso

- Acelerar a *performance* de aplicativos com **cache**.
- Armazenar **dados pessoais** de usuários e preferências.
- Gerenciar **sessões** em jogos *online*.
- **Dicionários e coleções.**

> ### 2.2.1 Consistência no Modelo Chave-Valor
- **Garantia Restrita (AOCP/2021):** O conceito de consistência é aplicável **apenas às operações em uma única chave** (obtenção, gravação ou exclusão).
- **Fundamento:** Como as operações são atômicas por chave, a garantia de que o dado retornado é o correto se limita ao escopo daquela chave específica.

### 2.3 Questões Comuns de Prova (Pegadinhas)

- **Erro Comum 1 (Cespe/2013):** Afirmar que **todos** os bancos NoSQL implementam a tecnologia **Chave-Valor**.
    - **Fundamento:** **ERRADO**. Existem 4 tipos principais: Chave-Valor, Documento, Colunar e Grafos.
- **Erro Comum 2 (Cespe/2022):** Afirmar que a chave no modelo Chave-Valor é "multidimensional" e composta por "nome de tabela + linha-coluna + timestamp".
    - **Fundamento:** **ERRADO**. A chave é um identificador simples (ex: CPF, ID de sessão), e o valor é o conteúdo associado. A descrição da questão remete a estruturas mais complexas (como o BigTable/Colunar).

## 3. Quadro Sinótico de Comandos (Cassandra)

| COMANDO | FINALIDADE | EXEMPLO |
| :--- | :--- | :--- |
| **CREATE KEYSPACE** | Cria um *keyspace* (equivalente ao BD/Schema). | `CREATE KEYSPACE IF NOT EXISTS minha_app WITH REPLICATION = {...};` |
| **USE** | Define o *keyspace* ativo para as próximas operações. | `USE minha_app;` |
| **CREATE TYPE** | Cria um tipo de dados personalizado (*UDT*). | `CREATE TYPE endereco (rua text, cidade text, num int);` |
| **CREATE TABLE** | Cria uma tabela (Família de Colunas). | `CREATE TABLE usuarios (id UUID PRIMARY KEY, nome text, end endereco);` |
| **SELECT** | Recupera dados. | `SELECT JSON nome, ocupacao FROM users WHERE id = 199;` |

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (AOCP 2020) | **C** (Keyspace) | Keyspace no Cassandra = Esquema no Relacional. |
| **2** (AOCP 2020) | **E** | Sintaxe correta para UDT: `CREATE TYPE`. |
| **3** (FEPESE 2017) | **C** (cqlsh) | Shell nativo do Cassandra. |
| **4** (ESAF 2015) | **E** | Cassandra é NoSQL, criado pelo Facebook, baseado em chave. |
| **5** (Cespe 2013) | **E** | Nem todo NoSQL é Chave-Valor (ex: Grafos, Documentos). |
| **6** (Cespe 2022) | **E** | Chave-Valor é simples (chave única, não multidimensional). |
| **7** (AOCP 2021) | **C** | Consistência garantida apenas por operação em chave única. |
| **8** (Cespe 2022) | **C** | Chave-Valor é considerado uma *Tabela Hash* simples via API. |