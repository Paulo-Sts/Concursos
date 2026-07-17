# Anotações – PostgreSQL – Chaves (Primary Keys, Foreign Keys, Sequences)

## 1. Chave Primária (Primary Key)

### 1.1 Definição

- Uma **chave primária** identifica **unicamente** cada linha de uma tabela.
- Características:
  - **Única** – não pode haver dois registros com o mesmo valor.
  - **Não nula** – não pode ser `NULL`.
- Pode ser composta por **uma ou mais colunas**.

### 1.2 Sintaxe – coluna única

```sql
CREATE TABLE produtos (
    produto_nr integer UNIQUE NOT NULL,
    nome text,
    preco numeric
);
```

> ### 1.2.1 Não recomendado
> - Usar `UNIQUE NOT NULL` manualmente não é a melhor prática.
> - O `PRIMARY KEY` já garante unicidade e não nulidade, além de facilitar a integridade referencial.

### 1.3 Sintaxe – chave primária explícita

```sql
CREATE TABLE produtos (
    produto_nr integer PRIMARY KEY,
    nome text,
    preco numeric
);
```

### 1.4 Chave primária composta (várias colunas)

```sql
CREATE TABLE exemplo (
    a integer,
    b integer,
    c integer,
    PRIMARY KEY (a, c)
);
```

## 2. `SERIAL` e `BIGSERIAL` – Auto Incremento

- `SERIAL` e `BIGSERIAL` **não são tipos de dados verdadeiros**.
- São **notações abreviadas** que criam uma **sequence** e definem o valor padrão para a coluna.
- `SERIAL` → 4 bytes (inteiro, até 2.147.483.647).
- `BIGSERIAL` → 8 bytes (inteiro grande).

### 2.1 Exemplo

```sql
CREATE TABLE produtos (
    produto_nr SERIAL PRIMARY KEY,
    nome text,
    preco numeric
);
```

- O PostgreSQL cria automaticamente uma **sequence** para a coluna `produto_nr`.
- Ao inserir um novo registro, o próximo valor da sequence é usado.

> ### 2.1.1 Comparação com outros SGBDs
> - **MySQL:** `AUTO_INCREMENT`.
> - **SQL Server:** `IDENTITY`.
> - **PostgreSQL:** `SERIAL` / `BIGSERIAL`.

## 3. `SEQUENCE` – Sequência Personalizada

- Em casos específicos, o padrão incremental do `SERIAL` pode não atender.
- É possível criar uma **sequence personalizada**.

### 3.1 Criar uma `SEQUENCE`

```sql
CREATE SEQUENCE produtos_sequence
START 2
INCREMENT 2;
```

- A sequence começa em **2** e é incrementada de **2 em 2**.
- Valores gerados: 2, 4, 6, 8, ...

### 3.2 Usar a sequence em um `INSERT`

```sql
INSERT INTO produtos (produto_nr, nome, preco)
VALUES (nextval('produtos_sequence'), 'Arroz', 5.00);
```

- `nextval('nome_da_sequence')` obtém o próximo valor da sequence.

## 4. Chave Estrangeira (Foreign Key)

### 4.1 Definição

- Uma **chave estrangeira** garante que os valores em uma coluna (ou grupo de colunas) correspondam a valores existentes em outra tabela.
- Mantém a **integridade referencial** entre duas tabelas relacionadas.

### 4.2 Sintaxe básica

```sql
CREATE TABLE pedidos (
    pedido_nr integer PRIMARY KEY,
    produto_nr integer REFERENCES produtos (produto_nr),
    quantidade integer
);
```

- `produto_nr` na tabela `pedidos` deve existir na coluna `produto_nr` da tabela `produtos`.
- O valor pode ser `NULL` (se não houver produto associado).

### 4.3 Sintaxe reduzida

```sql
CREATE TABLE pedidos (
    pedido_nr integer PRIMARY KEY,
    produto_nr integer REFERENCES produtos,
    quantidade integer
);
```

- Na ausência de uma lista de colunas, o PostgreSQL usa a **chave primária** da tabela referenciada.

## 5. `ON DELETE` e `ON UPDATE` – Comportamento em Cascata

| OPÇÃO | COMPORTAMENTO |
| --- | --- |
| `RESTRICT` | **Impede** a exclusão ou atualização de uma linha referenciada. (Padrão). |
| `CASCADE` | Exclui ou atualiza **automaticamente** as linhas que referenciam a linha alterada. |
| `SET NULL` | Define a chave estrangeira como `NULL` quando a linha referenciada é excluída. |
| `SET DEFAULT` | Define a chave estrangeira com o valor padrão. |
| `NO ACTION` | Similar a `RESTRICT` (a verificação é feita após a operação). |

### 5.1 Exemplo com `RESTRICT` e `CASCADE`

```sql
CREATE TABLE itens_pedidos (
    produto_nr integer REFERENCES produtos ON DELETE RESTRICT,
    pedido_nr integer REFERENCES pedidos ON DELETE CASCADE,
    quantidade integer,
    PRIMARY KEY (produto_nr, pedido_nr)
);
```

- **`ON DELETE RESTRICT`:** não permite excluir um produto que tenha pedidos associados.
- **`ON DELETE CASCADE`:** se um pedido for excluído, todos os itens desse pedido são excluídos automaticamente.

### 5.2 `ON UPDATE`

- Análogo ao `ON DELETE`, mas aplicado quando a coluna referenciada é **atualizada**.
- Exemplo: `ON UPDATE CASCADE` atualiza automaticamente as chaves estrangeiras quando a chave primária é alterada.

## 6. Questão de Concurso Comentada

### 6.1 (COMPERVE/UFRN/2018 – Analista de TI)

**Item:** "Para se criar a tabela ALUNO em um banco de dados PostgreSQL, o comando SQL que deve ser executado é:"

**Alternativas:**

a) `CREATE TABLE ALUNO (id SERIAL, nome VARCHAR(250), idade INT, matrícula VARCHAR(10), primary key(id))`

b) `CREATE TABLE ALUNO (id AUTO_INCREMENT, nome VARCHAR(250), idade INT, matrícula VARCHAR(10), primary key(id))`

c) `CREATE TABLE ALUNO (id AUTO_INCREMENT, nome STRING, idade INT, matrícula STRING, primary key(id))`

d) `CREATE TABLE ALUNO (id SERIAL, nome STRING, idade INT, matrícula STRING, primary key(id))`

**Gabarito: a) `CREATE TABLE ALUNO (id SERIAL, nome VARCHAR(250), idade INT, matrícula VARCHAR(10), primary key(id))`**

**Comentário:**
- No PostgreSQL, o auto incremento é feito com **`SERIAL`** (não `AUTO_INCREMENT`, que é do MySQL).
- O tipo para strings no PostgreSQL é **`VARCHAR(n)`** ou `TEXT` (não `STRING`).

## GABARITO DA QUESTÃO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (COMPERVE/UFRN/2018) | a |

---

## Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| `PRIMARY KEY` | Identifica unicamente cada linha. Única e não nula. |
| `SERIAL` | Auto incremento (inteiro) – cria uma sequence internamente. |
| `BIGSERIAL` | Auto incremento (inteiro grande). |
| `SEQUENCE` | Gerador de números personalizado. |
| `FOREIGN KEY` | Referência a uma chave primária de outra tabela. |
| `REFERENCES` | Define a chave estrangeira. |
| `ON DELETE RESTRICT` | Impede exclusão da linha referenciada. |
| `ON DELETE CASCADE` | Exclui automaticamente as linhas que referenciam. |
| `ON UPDATE CASCADE` | Atualiza automaticamente as chaves estrangeiras. |

---

*Material complementar à aula "PostgreSQL – Chaves" (professor Washington Henrique Almeida, Gran Concursos).*