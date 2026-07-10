# Anotações – PostgreSQL – DML (INSERT, UPDATE, DELETE, SELECT)

## 1. INSERT – Inserindo Dados

### 1.1 Sintaxe básica (ordem das colunas implícita)

```sql
INSERT INTO clima VALUES ('Brasilia', 14, 32, 0.10, '2019-11-16');
```

- **Atenção:** os valores devem ser passados **na ordem exata** em que as colunas foram definidas na tabela.
- Valores numéricos: **sem aspas**.
- Valores texto, data, etc.: **entre aspas simples** (`'`).

### 1.2 Sintaxe com listagem explícita de colunas (recomendada)

```sql
INSERT INTO clima (cidade, temp_min, temp_max, prcp, dia)
VALUES ('Brasilia', 14, 32, 0.10, '2019-11-16');
```

- Permite **omitir colunas** (se forem opcionais ou tiverem valor padrão).
- Permite **alterar a ordem** dos campos.
- **Boa prática:** sempre listar as colunas para evitar erros se a estrutura da tabela for alterada.

### 1.3 Tipo geográfico (`point`)

```sql
INSERT INTO cidades VALUES ('Brasilia', '(-15.7801, -47.9292)');
```

### 1.4 Múltiplas linhas em um único `INSERT`

```sql
INSERT INTO clima (cidade, temp_min, temp_max, dia)
VALUES
    ('São Paulo', 9, 27, '2019-11-16'),
    ('Rio de Janeiro', 15, 33, '2019-11-16'),
    ('Belo Horizonte', 14, 29, '2019-11-16');
```

### 1.5 `INSERT` com `SELECT` (inserir resultado de uma consulta)

```sql
INSERT INTO clima (cidade)
SELECT nome FROM cidades;
```

- Insere na tabela `clima` os nomes das cidades da tabela `cidades`.

## 2. UPDATE – Atualizando Dados

### 2.1 Sintaxe

```sql
UPDATE clima
SET temp_max = temp_max - 2,
    temp_min = temp_min - 2
WHERE cidade = 'Brasilia';
```

### 2.2 Cuidados importantes

| SITUAÇÃO | RESULTADO |
| --- | --- |
| `UPDATE` **com** `WHERE` | Atualiza apenas as linhas que atendem à condição. |
| `UPDATE` **sem** `WHERE` | Atualiza **todas** as linhas da tabela. |

> ### 2.2.1 Exemplo perigoso
> ```sql
> UPDATE clima SET temp_max = temp_max - 2;
> ```
> - Isso reduziria a temperatura máxima de **todos** os registros – geralmente indesejado.

## 3. DELETE – Removendo Dados

### 3.1 Sintaxe

```sql
DELETE FROM clima WHERE cidade = 'Brasilia';
```

### 3.2 Cuidados importantes

| SITUAÇÃO | RESULTADO |
| --- | --- |
| `DELETE` **com** `WHERE` | Remove apenas as linhas que atendem à condição. |
| `DELETE` **sem** `WHERE` | Remove **todas** as linhas da tabela. |

> ### 3.2.1 Exemplo perigoso
> ```sql
> DELETE FROM clima;
> ```
> - Remove **todos** os registros da tabela (deixa-a vazia).

## 4. SELECT – Consultando Dados

### 4.1 Selecionar todas as colunas (`*`)

```sql
SELECT * FROM clima;
```

- `*` é uma abreviação para **todas as colunas**.
- **Não recomendado** para consultas otimizadas: prefira listar as colunas necessárias.

### 4.2 Selecionar colunas específicas (projeção)

```sql
SELECT cidade, temp_min, temp_max, prcp, dia FROM clima;
```

### 4.3 `WHERE` – Filtrar linhas (seleção)

```sql
SELECT * FROM clima WHERE cidade = 'Brasilia';
```

- A cláusula `WHERE` contém uma expressão booleana.
- Apenas as linhas onde a condição é **verdadeira** são retornadas.

### 4.4 `ORDER BY` – Ordenar resultados

```sql
SELECT * FROM clima ORDER BY cidade;
```

- Padrão: ordem **crescente (ASC)**.
- Para decrescente: `ORDER BY cidade DESC`.

### 4.5 `DISTINCT` – Eliminar duplicatas

```sql
SELECT DISTINCT cidade FROM clima ORDER BY cidade;
```

- Remove cidades repetidas da consulta.

## 5. Resumo dos Comandos DML no PostgreSQL

| COMANDO | FUNÇÃO | CUIDADO |
| --- | --- | --- |
| `INSERT INTO ... VALUES` | Inserir uma ou mais linhas. | Sempre liste as colunas explicitamente. |
| `UPDATE ... SET ... WHERE` | Atualizar linhas. | Sem `WHERE`, atualiza **todas** as linhas. |
| `DELETE FROM ... WHERE` | Remover linhas. | Sem `WHERE`, remove **todas** as linhas. |
| `SELECT ... FROM ... WHERE` | Consultar dados. | Prefira colunas específicas em vez de `*`. |

## 6. Álgebra Relacional x SQL

| OPERAÇÃO NA ÁLGEBRA | COMANDO SQL CORRESPONDENTE |
| --- | --- |
| **Seleção** (filtrar linhas) | `SELECT * FROM tabela WHERE condição` |
| **Projeção** (filtrar colunas) | `SELECT coluna1, coluna2 FROM tabela` |

## 7. Questão de Concurso Comentada

### 7.1 (COMPERVE/UFRN/2018 – Analista de TI)

**Item:** "Para selecionar os nomes dos alunos por ordem alfabética crescente, deve-se executar no PostgreSQL o seguinte comando SQL:"

**Alternativas:**
- a) `SELECT NOME FROM aluno ORDER BY nome DESC`
- b) `SELECT NOME FROM aluno ORDER BY nome ASC`
- c) `SELECT NOME FROM aluno SORTED BY nome DESC`
- d) `SELECT NOME FROM aluno SORTED BY nome ASC`

**Gabarito: b) `SELECT NOME FROM aluno ORDER BY nome ASC`**.

**Comentário:**
- A ordem **crescente** (ascendente) é obtida com `ASC` (ou omitindo, pois é o padrão).
- `DESC` é ordem decrescente.
- O comando de ordenação é `ORDER BY` (não `SORTED BY`).

---

## Síntese para Revisão Rápida

| COMANDO | EXEMPLO |
| --- | --- |
| `INSERT` (com colunas) | `INSERT INTO clima (cidade, temp_min) VALUES ('SP', 10);` |
| `INSERT` (múltiplas linhas) | `INSERT INTO t (c1, c2) VALUES (1, 'A'), (2, 'B');` |
| `INSERT ... SELECT` | `INSERT INTO t1 SELECT c1 FROM t2;` |
| `UPDATE` | `UPDATE t SET col = valor WHERE condicao;` |
| `DELETE` | `DELETE FROM t WHERE condicao;` |
| `SELECT *` | `SELECT * FROM t;` |
| `SELECT colunas` | `SELECT nome, idade FROM alunos;` |
| `SELECT ... WHERE` | `SELECT * FROM t WHERE idade > 18;` |
| `SELECT ... ORDER BY` | `SELECT * FROM t ORDER BY nome ASC;` |
| `SELECT DISTINCT` | `SELECT DISTINCT cidade FROM t;` |

---

*Material complementar à aula "PostgreSQL – DML" (professor Washington Henrique Almeida, Gran Concursos).*