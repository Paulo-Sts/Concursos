# Anotações – Banco de Dados – Linguagem SQL

## 1. Introdução ao SQL

### 1.1 O que é SQL?

- **SQL** (*Structured Query Language*) – linguagem de consulta estruturada.
- Implementa as operações da **álgebra relacional** de forma amigável.
- Linguagem para acesso e manipulação de bancos de dados **relacionais**.
- **Padronizada pela ANSI** (*American National Standards Institute*).

> ### 1.1.1 NoSQL
> - **NoSQL** inicialmente significava "não relacional" – com o tempo, passou a significar **"Not Only SQL"** (não apenas SQL).
> - Bancos relacionais e SQL permanecem fundamentais devido à base matemática sólida (consistência, normalização).

### 1.2 Evolução do SQL

| VERSÃO | ANO | CARACTERÍSTICAS |
| --- | --- | --- |
| SEQUEL | 1970 | Nome original (*Structured English Query Language*), desenvolvido pela IBM (System R). |
| SQL-86 / SQL1 | 1986 | Primeira padronização pela ISO e ANSI. |
| SQL92 / SQL2 | 1992 | Revisão e expansão do padrão. |
| SQL:1999 / SQL3 | 1999 | Características de BDOO (bancos de dados orientados a objetos). Novos tipos (CLOB), predicados, tipos abstratos. |
| SQL:2003, 2006, 2008, 2011, 2016 | – | Atualizações contínuas. |

## 2. Divisão dos Comandos SQL

### 2.1 Classificação principal (mais aceita)

| CATEGORIA | SIGLA | FUNÇÃO | COMANDOS PRINCIPAIS |
| --- | --- | --- | --- |
| **Linguagem de Definição de Dados** | DDL | Definir a estrutura do banco (esquema, tabelas, índices). | `CREATE`, `DROP`, `ALTER`, `RENAME` (às vezes) |
| **Linguagem de Manipulação de Dados** | DML | Manipular os dados (CRUD). | `INSERT`, `UPDATE`, `DELETE`, `SELECT` |
| **Linguagem de Controle de Dados** | DCL | Controlar permissões e segurança. | `GRANT`, `REVOKE` |
| **Linguagem de Controle de Transações** | DTL / TCL | Controlar transações. | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

> ### 2.1.1 Observação sobre DQL
> - Algumas bancas (ex.: FGV) utilizam a classificação **DQL** (*Data Query Language*) para agrupar apenas o comando `SELECT`.
> - O professor considera essa classificação **desnecessária** e pouco usual na prática.

## 3. DDL – Data Definition Language

### 3.1 Comandos principais

| COMANDO | FUNÇÃO |
| --- | --- |
| `CREATE TABLE` | Criar uma nova tabela (relação). |
| `DROP TABLE` | Remover uma tabela e seus dados. |
| `ALTER TABLE` | Adicionar, remover ou modificar colunas/restrições. |

### 3.2 `CREATE TABLE` – Exemplo

```sql
CREATE TABLE empregado (
    cod_empregado CHAR(9) PRIMARY KEY NOT NULL,
    nome VARCHAR(15) NOT NULL,
    data_nasc DATE,
    cod_departamento INT DEFAULT 0 NOT NULL,
    cod_supervisor CHAR(9),
    CONSTRAINT EP_departamento FOREIGN KEY (cod_departamento)
        REFERENCES departamento(cod_departamento)
        ON DELETE CASCADE
);
```

| ELEMENTO | EXPLICAÇÃO |
| --- | --- |
| `CHAR(9)` | Tipo fixo – sempre ocupa 9 caracteres (preenche com espaços). |
| `VARCHAR(15)` | Tipo variável – ocupa apenas os caracteres usados. |
| `DEFAULT 0` | Valor padrão (insere 0 se não for informado). |
| `NOT NULL` | O campo não pode ficar vazio (ausência de valor). |
| `PRIMARY KEY` | Chave primária da tabela. |
| `FOREIGN KEY` / `REFERENCES` | Chave estrangeira que referencia outra tabela. |
| `ON DELETE CASCADE` | Ao excluir o departamento, exclui também os empregados vinculados. |

> ### 3.2.1 `CHAR` vs `VARCHAR`
> - **`CHAR(n)`**: tamanho **fixo** – ocupa sempre `n` caracteres, preenchendo com espaços.
> - **`VARCHAR(n)`**: tamanho **variável** – ocupa apenas a quantidade usada.
> - Espaço vazio (`' '`) **é um valor** (diferente de `NULL`). O `NULL` representa ausência de valor.

### 3.3 `ALTER TABLE` – Exemplos

```sql
-- Adicionar uma nova coluna
ALTER TABLE Produto ADD Marca VARCHAR(30);

-- Definir valor padrão para uma coluna
ALTER TABLE Produto ALTER COLUMN Preco SET DEFAULT 0;

-- Remover uma coluna
ALTER TABLE Produto DROP COLUMN Preco;
```

### 3.4 `DROP TABLE`

```sql
DROP TABLE Produto;
```

- Remove a tabela e **todos os seus dados** (irreversível).

## 4. DML – Data Manipulation Language

### 4.1 Comandos principais

| COMANDO | FUNÇÃO |
| --- | --- |
| `INSERT` | Inserir novos registros. |
| `UPDATE` | Atualizar registros existentes. |
| `DELETE` | Excluir registros. |
| `SELECT` | Consultar (selecionar) dados. |

## 5. SELECT – Sintaxe Básica

```sql
SELECT [DISTINCT] colunas
FROM tabela
WHERE condição
ORDER BY coluna [ASC|DESC];
```

### 5.1 `SELECT *` vs. `SELECT colunas`

- `SELECT *` – retorna **todas** as colunas da tabela.
- `SELECT coluna1, coluna2` – retorna **apenas** as colunas especificadas (projeção na álgebra relacional).

## 6. Operadores no `WHERE`

### 6.1 Operadores Relacionais

| OPERADOR | SIGNIFICADO | EXEMPLO |
| --- | --- | --- |
| `=` | Igual | `WHERE codigo = 10` |
| `<` | Menor que | `WHERE qtd < 5` |
| `<=` | Menor ou igual | `WHERE preco <= 50` |
| `>` | Maior que | `WHERE preco > 500` |
| `>=` | Maior ou igual | `WHERE preco >= 500` |
| `<>` ou `!=` | Diferente | `WHERE codigo <> 2` |

### 6.2 Operadores Lógicos

| OPERADOR | SIGNIFICADO | EXEMPLO |
| --- | --- | --- |
| `AND` | E (ambas condições verdadeiras) | `WHERE marca = 'LG' AND preco > 1500` |
| `OR` | OU (pelo menos uma verdadeira) | `WHERE qtd < 5 OR qtd > 100` |
| `NOT` | Negação | `WHERE preco IS NOT NULL` |

### 6.3 Operadores Especiais

| OPERADOR | SIGNIFICADO | EXEMPLO |
| --- | --- | --- |
| `IS NULL` / `IS NOT NULL` | Testa se o valor é nulo ou não nulo | `WHERE preco IS NULL` |
| `BETWEEN ... AND ...` | Intervalo (inclusivo) | `WHERE preco BETWEEN 10 AND 100` |
| `LIKE` | Padrão para strings (coringa) | `WHERE nome LIKE 'A%'` (começa com A) |
| `IN` | Comparação com um conjunto | `WHERE codigo IN (2, 5, 15, 29)` |
| `DISTINCT` | Elimina duplicidades (usado com `SELECT`) | `SELECT DISTINCT categoria FROM produto` |

> ### 6.3.1 `LIKE` – coringas mais comuns
> - `%` – zero ou mais caracteres.
> - `_` – exatamente um caractere.
> - Exemplo: `'A%'` → começa com "A"; `'%s'` → termina com "s".

## 7. Comparação entre Tipos de Dados (CHAR vs. VARCHAR)

| TIPO | TAMANHO | OCUPAÇÃO | USO RECOMENDADO |
| --- | --- | --- | --- |
| `CHAR(n)` | Fixo | Sempre `n` caracteres (com espaços). | Dados com tamanho fixo (ex.: CPF, UF, sigla). |
| `VARCHAR(n)` | Variável | Apenas os caracteres usados. | Nomes, descrições, endereços. |

> ### 7.1 `NULL` vs. espaço em branco (`''`)
> - **`NULL`**: ausência de valor – não ocupa espaço.
> - **Espaço (`' '` ou `''`)**: é um valor – ocupa espaço e é diferente de `NULL`.

## 8. Esquema (Schema)

- Um **esquema** é definido por um **nome** e inclui um **identificador de autorização** (usuário dono do esquema).
- Exemplo: `CREATE SCHEMA PF AUTHORIZATION agente_silva;`
- O esquema contém: tabelas, restrições, visões (*views*), domínios, etc.

## 9. Sintetização para Revisão

| COMANDO | CLASSIFICAÇÃO | FUNÇÃO |
| --- | --- | --- |
| `CREATE` | DDL | Criar estruturas (tabela, esquema, view). |
| `ALTER` | DDL | Modificar estruturas. |
| `DROP` | DDL | Remover estruturas. |
| `SELECT` | DML (ou DQL) | Consultar dados. |
| `INSERT` | DML | Inserir dados. |
| `UPDATE` | DML | Atualizar dados. |
| `DELETE` | DML | Excluir dados. |
| `GRANT` | DCL | Conceder permissões. |
| `REVOKE` | DCL | Remover permissões. |
| `COMMIT` | DTL / TCL | Confirmar transação. |
| `ROLLBACK` | DTL / TCL | Desfazer transação. |
| `SAVEPOINT` | DTL / TCL | Criar ponto de restauração. |

---

*Material complementar à aula "Banco de Dados – Linguagem SQL" (professor Washington Henrique Almeida, Gran Concursos).*