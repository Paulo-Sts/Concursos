# Anotações – PostgreSQL – PL/pgSQL (Linguagem Procedural)

## 1. Estrutura de um Bloco PL/pgSQL

A linguagem **PL/pgSQL** é estruturada em **blocos**. A estrutura básica de um bloco é:

```sql
[ <<rótulo>> ]
[ DECLARE
    declarações ]
BEGIN
    instruções
END [ rótulo ];
```

> ### 1.1 Regras importantes
> - Todas as declarações e instruções dentro do bloco devem terminar com **ponto e vírgula (`;`)**.
> - O `END` final que conclui o corpo da função **não requer** ponto e vírgula (embora seja permitido em sub-blocos).
> - Palavras-chave e identificadores **não diferenciam maiúsculas de minúsculas** (case-insensitive), a menos que estejam entre **aspas duplas**.

### 1.2 Comentários

| TIPO | SINTAXE | DESCRIÇÃO |
| --- | --- | --- |
| **Comentário de linha** | `--` | Comentário até o final da linha. |
| **Comentário de bloco** | `/* ... */` | Comentário de múltiplas linhas. Não podem ser aninhados. |

### 1.3 Exemplo de função PL/pgSQL

```sql
CREATE FUNCTION sum(int[]) RETURNS int8 AS $$
DECLARE
    s int8 := 0;
    x int;
BEGIN
    FOREACH x IN ARRAY $1 LOOP
        s := s + x;
    END LOOP;
    RETURN s;
END;
$$ LANGUAGE plpgsql;
```

- `$$` é usado como delimitador de string (evita conflito com aspas simples).

> ### 1.4 `BEGIN`/`END` no PL/pgSQL
> - **Não** são comandos de transação.
> - Servem apenas para **agrupamento lógico** de instruções e delimitação de escopo de variáveis.
> - Transações são controladas pelo comando externo (`BEGIN`/`COMMIT` do SQL, não pelo bloco PL/pgSQL).

## 2. Declaração de Variáveis

### 2.1 Sintaxe básica

```sql
nome_variavel tipo [ CONSTANT ] [ NOT NULL ] [ { DEFAULT | := } valor_inicial ];
```

- Se `DEFAULT` não for fornecido, a variável é inicializada com **`NULL`**.
- `CONSTANT` impede que a variável seja alterada.
- `NOT NULL` exige um valor padrão não nulo.

**Exemplos:**

```sql
quantidade integer DEFAULT 32;
url varchar := 'http://meu-site.com';
id_usuario CONSTANT integer := 10;
```

### 2.2 Atribuição

```sql
variavel := expressao;
```

- **Atenção:** PL/pgSQL usa `:=` para atribuição (não `=`).

### 2.3 `%TYPE` – Cópia de tipo de coluna

- Declara uma variável com o mesmo tipo de uma coluna de tabela.
- **Boa prática:** evita problemas se o tipo da coluna for alterado.

```sql
id_usuario usuarios.id_usuario%TYPE;
```

### 2.4 `%ROWTYPE` – Variável linha (registro)

- Declara uma variável que pode armazenar uma **linha inteira** de uma tabela.
- Os campos são acessados com notação de ponto (`variavel.campo`).

```sql
registro usuarios%ROWTYPE;
```

## 3. Estruturas de Controle

### 3.1 `FOR` – Laço com intervalo de inteiros

- A variável do laço é **declarada automaticamente** como `integer`.
- Existe apenas dentro do laço.

```sql
FOR i IN 1..10 LOOP
    RAISE NOTICE 'i é %', i;
END LOOP;
```

- Com `REVERSE`, a iteração vai do valor superior para o inferior:

```sql
FOR i IN REVERSE 10..1 LOOP
    -- processamento
END LOOP;
```

## 4. Parâmetros de Função e Aliases

### 4.1 Referência numérica (`$1`, `$2`, ...)

- Os parâmetros podem ser referenciados por `$1`, `$2`, etc.

### 4.2 Alias (nome explícito)

**Método 1 – nome no `CREATE FUNCTION` (preferido):**

```sql
CREATE FUNCTION taxa_de_venda(subtotal real) RETURNS real AS $$
BEGIN
    RETURN subtotal * 0.06;
END;
$$ LANGUAGE plpgsql;
```

**Método 2 – `ALIAS FOR` (versões antigas):**

```sql
CREATE FUNCTION taxa_de_venda(real) RETURNS real AS $$
DECLARE
    subtotal ALIAS FOR $1;
BEGIN
    RETURN subtotal * 0.06;
END;
$$ LANGUAGE plpgsql;
```

## 5. `GET DIAGNOSTICS` e `FOUND`

### 5.1 `GET DIAGNOSTICS`

- Obtém informações sobre o efeito do último comando SQL.

```sql
GET DIAGNOSTICS variavel = item;
```

### 5.2 `FOUND`

- Variável booleana que indica se o último comando SQL afetou alguma linha.
- Inicializada como `false` em cada chamada de função.
- É **local** à função (mudanças afetam apenas a função corrente).

## 6. Cursores

- Cursores permitem ler os resultados de uma consulta **linha por linha**.
- Útil para evitar o uso excessivo de memória com grandes conjuntos de dados.
- O tipo de dados para cursores é **`refcursor`**.

### 6.1 Declaração de cursor

```sql
DECLARE
    curs1 refcursor;
    curs2 CURSOR FOR SELECT * FROM tenk1;
    curs3 CURSOR (chave integer) IS
        SELECT * FROM tenk1 WHERE unico1 = chave;
```

## 7. `RAISE` – Mensagens e Erros

### 7.1 Sintaxe

```sql
RAISE [ nível ] 'formato' [, variavel [, ...] ];
```

### 7.2 Níveis disponíveis

| NÍVEL | DESCRIÇÃO |
| --- | --- |
| `DEBUG` | Mensagem de depuração. |
| `LOG` | Mensagem registrada no log do servidor. |
| `INFO` | Informação geral. |
| `NOTICE` | Aviso informativo. |
| `WARNING` | Aviso de potencial problema. |
| `EXCEPTION` | **Erro** – interrompe a transação corrente. |

### 7.3 Exemplos

```sql
RAISE NOTICE 'Chamando cs_create_job(%)', v_job_id;

RAISE EXCEPTION 'ID inexistente --> %', id_usuario;
```

- O `%` na string de formato é substituído pelo valor da variável.
- `%%` produz um `%` literal.

## 8. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Bloco PL/pgSQL** | `[DECLARE] BEGIN ... END;` |
| `:=` | Atribuição de valor. |
| `%TYPE` | Declara variável com o tipo de uma coluna. |
| `%ROWTYPE` | Declara variável para armazenar uma linha inteira. |
| `FOR i IN 1..10 LOOP` | Laço com intervalo de inteiros. |
| `$1`, `$2` | Referência a parâmetros por posição. |
| `ALIAS FOR` | Cria alias para parâmetro. |
| `FOUND` | Booleano – indica se último comando afetou linhas. |
| `refcursor` | Tipo para cursores. |
| `RAISE NOTICE` | Exibe mensagem informativa. |
| `RAISE EXCEPTION` | Gera erro e interrompe transação. |

---

*Material complementar à aula "PostgreSQL – PL/pgSQL" (professor Washington Henrique Almeida, Gran Concursos).*