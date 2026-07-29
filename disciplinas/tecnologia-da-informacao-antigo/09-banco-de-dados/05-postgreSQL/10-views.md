# Anotações – PostgreSQL – Views e Gatilhos (Triggers)

## 1. Views (Visualizações)

### 1.1 Conceito

- Uma **view** é uma **consulta armazenada** que seleciona dados de uma ou mais tabelas.
- **Sintaxe:** `CREATE VIEW myview AS SELECT * FROM mytab;`
- Do ponto de vista lógico, uma view é uma **relação** (como uma tabela), mas os dados não são armazenados fisicamente – são derivados das tabelas base.

### 1.2 Utilidade das Views

| FUNÇÃO | DESCRIÇÃO |
| --- | --- |
| **Segurança** | Limitar o acesso a colunas ou linhas específicas. |
| **Simplificação** | Encapsular consultas complexas (ex.: `JOIN`s com múltiplas tabelas). |
| **Isolamento** | Mudanças na estrutura da tabela não afetam as aplicações se as views forem mantidas. |
| **Reutilização** | A view pode ser usada em qualquer lugar onde uma tabela possa ser usada. |

### 1.3 Views e Regras

- As views são implementadas no PostgreSQL usando o **sistema de regras** (`ON SELECT`).
- As regras `ON SELECT` são aplicadas a todas as consultas como a **última etapa**.
- O sistema de regras permite combinar:
  - As tabelas a serem varridas.
  - Os relacionamentos entre tabelas.
  - As qualificações da view e da consulta original em uma **única árvore de consulta**.

> ### 1.3.1 Inserção via View
> - É tecnicamente possível usar `INSERT`, `UPDATE` ou `DELETE` em uma view (se ela for **atualizável**).
> - **Não é recomendado** fazer inserções via view – prefira operar diretamente nas tabelas base.

## 2. Triggers (Gatilhos)

### 2.1 Conceito

- Um **trigger** é uma função que é executada **automaticamente** quando ocorre um evento específico em uma tabela, view ou tabela estrangeira.
- **Eventos:** `INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`.

### 2.2 Sintaxe básica

```sql
CREATE TRIGGER nome_trigger
{BEFORE | AFTER | INSTEAD OF} {INSERT | UPDATE | DELETE | TRUNCATE}
ON nome_tabela
[FOR EACH ROW | FOR EACH STATEMENT]
EXECUTE FUNCTION nome_funcao();
```

### 2.3 Quando o trigger é executado

| MOMENTO | DESCRIÇÃO |
| --- | --- |
| **BEFORE** | Antes da tentativa de operação na linha. |
| **AFTER** | Após a conclusão da operação. |
| **INSTEAD OF** | Em vez da operação (apenas para views e `FOR EACH ROW`). |

### 2.4 Nível de execução

| NÍVEL | DESCRIÇÃO |
| --- | --- |
| **FOR EACH ROW** | Executado **uma vez para cada linha** modificada pela operação. |
| **FOR EACH STATEMENT** | Executado **uma vez por operação**, independentemente do número de linhas afetadas. |

### 2.5 Tabela de combinações (PostgreSQL)

| MOMENTO | EVENTO | ROW-LEVEL (nível de linha) | STATEMENT-LEVEL (nível de comando) |
| --- | --- | --- | --- |
| **BEFORE** | INSERT/UPDATE/DELETE | Tabelas e tabelas estrangeiras | Tabelas, views e tabelas estrangeiras |
| **BEFORE** | TRUNCATE | — | Tabelas |
| **AFTER** | INSERT/UPDATE/DELETE | Tabelas e tabelas estrangeiras | Tabelas, views e tabelas estrangeiras |
| **AFTER** | TRUNCATE | — | Tabelas |
| **INSTEAD OF** | INSERT/UPDATE/DELETE | **Views** | — |

> ### 2.5.1 Observações
> - `INSTEAD OF` **só pode ser usado** em **views** e **exige** `FOR EACH ROW`.
> - `BEFORE` e `AFTER` em views devem ser `FOR EACH STATEMENT`.
> - **`TRUNCATE`** não tem versão `BEFORE` com `FOR EACH ROW`.

### 2.6 Exemplos

**1. Trigger executado antes de um UPDATE:**

```sql
CREATE TRIGGER name_trigger
BEFORE UPDATE ON name_table
FOR EACH ROW
EXECUTE FUNCTION name_function();
```

**2. Trigger `INSTEAD OF` para uma view:**

```sql
CREATE TRIGGER view_insert
INSTEAD OF INSERT ON my_view
FOR EACH ROW
EXECUTE FUNCTION view_insert_row();
```

## 3. Variáveis Especiais em Triggers (PL/pgSQL)

- Quando uma função que retorna `TRIGGER` é executada, o PostgreSQL cria variáveis especiais na memória.

| VARIÁVEL | DESCRIÇÃO |
| --- | --- |
| `TG_OP` | Identifica a operação que disparou o trigger. Valores: `INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`. |
| `NEW` | Contém os novos valores (para `INSERT` e `UPDATE`). |
| `OLD` | Contém os valores antigos (para `UPDATE` e `DELETE`). |
| `TG_TABLE_NAME` | Nome da tabela que disparou o trigger. |
| `TG_WHEN` | `BEFORE`, `AFTER` ou `INSTEAD OF`. |

> ### 3.1 Questão CESPE
> - A variável **`TG_OP`** permite identificar a operação que está sendo executada (`INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`). A afirmação está **Certa**.

## 4. Funções – `IMMUTABLE` e `RETURNS NULL ON NULL INPUT`

### 4.1 `IMMUTABLE`

- Indica que a função **não modifica o banco de dados**.
- Sempre retorna o **mesmo resultado** para os mesmos argumentos.
- Não realiza consultas ao banco nem usa informações externas à lista de argumentos.

### 4.2 `RETURNS NULL ON NULL INPUT`

- Se algum argumento for `NULL`, a função retorna `NULL` imediatamente, sem executar o corpo.

**Exemplo (função `add`):**

```sql
CREATE FUNCTION add(integer, integer)
RETURNS integer AS 'select $1 + $2;'
LANGUAGE SQL
IMMUTABLE
RETURNS NULL ON NULL INPUT;
```

- A função soma dois inteiros, é `IMMUTABLE` (não altera o BD) e retorna `NULL` se algum argumento for `NULL`.

## 5. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **View** | Consulta armazenada (tabela virtual). |
| **Trigger** | Função executada automaticamente em eventos (`INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`). |
| **BEFORE** | Dispara antes da operação. |
| **AFTER** | Dispara após a operação. |
| **INSTEAD OF** | Dispara em vez da operação (apenas views). |
| **FOR EACH ROW** | Executa uma vez por linha modificada. |
| **FOR EACH STATEMENT** | Executa uma vez por operação. |
| **TG_OP** | Variável que identifica a operação (`INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`). |
| **IMMUTABLE** | Função não modifica o BD e é determinística. |

---

*Material complementar à aula "PostgreSQL – Views e Gatilhos" (professor Washington Henrique Almeida, Gran Concursos).*