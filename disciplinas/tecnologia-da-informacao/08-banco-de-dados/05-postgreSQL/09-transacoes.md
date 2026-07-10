# Anotações – PostgreSQL – Transações e Procedimentos Armazenados

## 1. Transações – Conceito ACID

| PROPRIEDADE | DESCRIÇÃO |
| --- | --- |
| **Atomicidade** | A transação é executada por completo ou não é executada (tudo ou nada). |
| **Consistência** | A transação leva o banco de um estado consistente a outro estado consistente. |
| **Isolamento** | Transações concorrentes não interferem umas nas outras. |
| **Durabilidade** | Após o `COMMIT`, as alterações são permanentes, mesmo em caso de falha. |

> ### 1.1 `BEGIN`, `COMMIT` e `ROLLBACK`

```sql
BEGIN;
UPDATE contas SET saldo = saldo - 100.00 WHERE nome = 'Alice';
-- ... outras operações ...
COMMIT;  -- confirma as alterações
-- ou
ROLLBACK;  -- desfaz todas as alterações desde o BEGIN
```

- O PostgreSQL trata **cada instrução SQL** como uma transação implícita (com `BEGIN` e `COMMIT` automáticos).
- Se uma instrução falhar, a transação implícita é revertida (`ROLLBACK`).

## 2. `SAVEPOINT` e `ROLLBACK TO`

- Permite **reverter parcialmente** uma transação, mantendo as alterações anteriores.
- Útil para operações complexas onde se deseja descartar apenas parte da transação.

```sql
BEGIN;
UPDATE contas SET saldo = saldo - 100.00 WHERE nome = 'Alice';
SAVEPOINT my_savepoint;
UPDATE contas SET saldo = saldo + 100.00 WHERE nome = 'Bob';  -- erro (nome errado)
ROLLBACK TO my_savepoint;  -- desfaz apenas o update do Bob
UPDATE contas SET saldo = saldo + 100.00 WHERE nome = 'Wally'; -- corrige
COMMIT;
```

- Após `ROLLBACK TO`, o `SAVEPOINT` permanece ativo para novos `ROLLBACK TO`.

## 3. Procedimentos Armazenados (Stored Procedures)

No PostgreSQL existem três tipos:

| TIPO | DESCRIÇÃO |
| --- | --- |
| **Funções em SQL** | Não possuem variáveis ou estruturas de controle (`IF`, `FOR`). Apenas comandos SQL (`SELECT`, `INSERT`, `UPDATE`, `DELETE`). |
| **Funções em Linguagens Procedurais** | Utilizam variáveis e estruturas de controle. **PL/pgSQL** é a mais comum. |
| **Funções Externas** | Desenvolvidas em linguagens externas (C++, Python) e carregadas como bibliotecas compartilhadas. |

### 3.1 PL/pgSQL

- Linguagem procedural carregável, semelhante à **PL/SQL do Oracle**.
- Funções em PL/pgSQL podem:
  - Aceitar tipos escalares, arrays, tipos compostos (`record`).
  - Retornar `SETOF` (conjunto de linhas), `void`, tipos polimórficos.
  - Ser usadas com `RETURNS TABLE` para retornar várias colunas.

### 3.2 `CREATE FUNCTION` – Sintaxe básica

```sql
CREATE OR REPLACE FUNCTION nome_funcao(param1 tipo, param2 tipo)
RETURNS tipo_retorno AS $$
    -- corpo da função (SQL ou PL/pgSQL)
$$ LANGUAGE 'SQL';
```

**Exemplo (SQL):**

```sql
CREATE FUNCTION total_pedidos() RETURNS INTEGER AS $$
    SELECT COUNT(*) FROM pedidos;
$$ LANGUAGE 'SQL';
```

**Exemplo com `SETOF` (retorna conjunto):**

```sql
CREATE FUNCTION quem_deve() RETURNS SETOF INTEGER AS $$
    SELECT clientes.id
    FROM clientes
    INNER JOIN contas ON clientes.id = contas.fkcliente
    INNER JOIN movimentos ON contas.id = movimentos.fkconta
    GROUP BY clientes.id
    HAVING SUM(movimentos.credito - movimentos.debito) < 0;
$$ LANGUAGE 'SQL';
```

- `SETOF` indica que a função retorna **um conjunto** (várias linhas), não um único valor.

### 3.3 `CREATE PROCEDURE` (PostgreSQL 11+)

- **Procedures** foram introduzidas no PostgreSQL 11.
- **Diferença principal:** `PROCEDURE` permite **controle de transações** (`COMMIT` e `ROLLBACK`) dentro do corpo.
- `FUNCTION` **não** permite controle de transações internas.

```sql
CREATE OR REPLACE PROCEDURE nome_procedure(INOUT p1 integer)
LANGUAGE 'plpgsql' AS $$
BEGIN
    RAISE NOTICE 'Valor recebido: %', p1;
    -- ... operações ...
END;
$$;
```

**Execução:** `CALL nome_procedure(10);`

### 3.4 `FUNCTION` vs. `PROCEDURE`

| CARACTERÍSTICA | FUNCTION | PROCEDURE |
| --- | --- | --- |
| **Retorno** | Obrigatório (`RETURNS`) | Não tem retorno (ou `void`) |
| **Controle de transação** | **Não** permite `COMMIT`/`ROLLBACK` | **Permite** `COMMIT`/`ROLLBACK` |
| **Uso** | Consultas e cálculos | Operações administrativas e migrações |
| **Versão PostgreSQL** | Disponível desde o início | PostgreSQL 11+ |
| **Migração Oracle** | Limitada | Facilita a migração |

> ### 3.4.1 Modos de parâmetro
> - **`IN`** – parâmetro de entrada (padrão).
> - **`OUT`** – parâmetro de saída (retorna valor).
> - **`INOUT`** – entrada e saída (passa valor e retorna outro).

## 4. Tabela `pg_proc`

- Armazena todas as **functions** criadas no PostgreSQL.
- Não armazena `PROCEDURE` – essas são armazenadas em `pg_proc` também? Na verdade, no PostgreSQL, procedures são armazenadas em `pg_proc` também, mas com `prokind = 'p'`.

## 5. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| `BEGIN` / `COMMIT` / `ROLLBACK` | Controle básico de transações. |
| `SAVEPOINT` | Ponto de restauração parcial dentro de uma transação. |
| `ROLLBACK TO` | Reverte apenas até o `SAVEPOINT`. |
| `FUNCTION` | Retorna valor; não permite controle de transações. |
| `PROCEDURE` | Não retorna valor (ou `void`); permite controle de transações (PostgreSQL 11+). |
| `PL/pgSQL` | Linguagem procedural nativa do PostgreSQL. |
| `SETOF` | Indica que a função retorna um conjunto de linhas. |
| `RAISE NOTICE` | Exibe mensagem no console (depuração). |
| `CALL` | Comando para executar uma `PROCEDURE`. |

---

*Material complementar à aula "PostgreSQL – Transações e Procedimentos Armazenados" (professor Washington Henrique Almeida, Gran Concursos).*