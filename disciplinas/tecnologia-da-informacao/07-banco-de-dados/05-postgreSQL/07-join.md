# Anotações – PostgreSQL – JOIN, GROUP BY e HAVING

## 1. JOIN – Conceito Geral

- **JOIN** é uma operação da **álgebra relacional** que combina dados de duas ou mais tabelas.
- A operação consiste basicamente em:
  1. **Produto cartesiano** entre as tabelas.
  2. **Seleção** das linhas que satisfazem a condição de junção.

### 1.1 Sintaxe básica (junção implícita)

```sql
SELECT *
FROM clima, cidades
WHERE clima.cidade = cidades.nome;
```

- Sem a condição `WHERE`, ocorre um **produto cartesiano** (cada linha de uma tabela combinada com cada linha da outra).

### 1.2 Boa prática: qualificar colunas

```sql
SELECT clima.cidade,
       clima.temp_min,
       clima.temp_max,
       clima.prcp,
       clima.dia,
       cidades.localizacao
FROM clima, cidades
WHERE cidades.nome = clima.cidade;
```

- **Qualificar** colunas com o nome da tabela (ou alias) evita ambiguidades.

## 2. Tipos de JOIN

| TIPO | DESCRIÇÃO | RESULTADO |
| --- | --- | --- |
| **INNER JOIN** | Retorna apenas linhas com correspondência em ambas as tabelas. | Interseção. |
| **LEFT OUTER JOIN** | Retorna todas as linhas da tabela esquerda + correspondências da direita. | Tabela esquerda + interseção. |
| **RIGHT OUTER JOIN** | Retorna todas as linhas da tabela direita + correspondências da esquerda. | Tabela direita + interseção. |
| **FULL OUTER JOIN** | Retorna todas as linhas de ambas as tabelas. | União. |
| **CROSS JOIN** | Produto cartesiano: todas as combinações entre linhas. | T1 × T2. |

### 2.1 INNER JOIN (padrão)

```sql
SELECT *
FROM t1
INNER JOIN t2 ON t1.num = t2.num;
```

- A palavra `INNER` é **opcional**.
- Retorna apenas linhas onde a condição `ON` é satisfeita.

### 2.2 LEFT OUTER JOIN

```sql
SELECT *
FROM t1
LEFT JOIN t2 ON t1.num = t2.num;
```

- Retorna **todas** as linhas de `t1`.
- Para linhas de `t1` sem correspondência em `t2`, as colunas de `t2` ficam com `NULL`.

### 2.3 RIGHT OUTER JOIN

```sql
SELECT *
FROM t1
RIGHT JOIN t2 ON t1.num = t2.num;
```

- Retorna **todas** as linhas de `t2`.
- Para linhas de `t2` sem correspondência em `t1`, as colunas de `t1` ficam com `NULL`.

### 2.4 FULL OUTER JOIN

```sql
SELECT *
FROM t1
FULL JOIN t2 ON t1.num = t2.num;
```

- Retorna **todas** as linhas de ambas as tabelas.
- Onde não há correspondência, os campos da tabela oposta ficam com `NULL`.

### 2.5 CROSS JOIN (produto cartesiano)

```sql
SELECT *
FROM t1
CROSS JOIN t2;
```

- Combina **cada linha** de `t1` com **cada linha** de `t2`.
- **Cuidado:** pode gerar um número muito grande de linhas.

## 3. Resumo Comparativo (com exemplos)

Considere as tabelas `t1` e `t2`:

**t1:**

| num | nome |
| --- | --- |
| 1 | a |
| 2 | b |
| 3 | c |

**t2:**

| num | valor |
| --- | --- |
| 1 | xxx |
| 3 | yyy |
| 4 | zzz |

| TIPO DE JOIN | RESULTADO (num) |
| --- | --- |
| `INNER JOIN` | 1, 3 |
| `LEFT JOIN` | 1, 3 (todos de t1; 2 vem com NULL) |
| `RIGHT JOIN` | 1, 3, 4 (todos de t2; 4 vem com NULL à esquerda) |
| `FULL JOIN` | 1, 2, 3, 4 (todos de ambas) |
| `CROSS JOIN` | 1×1, 1×2, 2×1, 2×2, ... (todas as combinações) |

## 4. GROUP BY – Agrupamento de Dados

- Usado para agrupar linhas que têm os **mesmos valores** em colunas especificadas.
- Geralmente combinado com **funções de agregação** (`COUNT`, `SUM`, `AVG`, `MAX`, `MIN`).

### 4.1 Sintaxe

```sql
SELECT coluna, COUNT(*)
FROM tabela
GROUP BY coluna;
```

### 4.2 Exemplo

**Tabela vendas:**

| produto | categoria | valor |
| --- | --- | --- |
| A | eletrônicos | 100 |
| B | eletrônicos | 200 |
| C | livros | 50 |

**Consulta:**

```sql
SELECT categoria, SUM(valor) AS total
FROM vendas
GROUP BY categoria;
```

**Resultado:**

| categoria | total |
| --- | --- |
| eletrônicos | 300 |
| livros | 50 |

## 5. HAVING – Filtrando Grupos

- `HAVING` é usado para filtrar **grupos** após o `GROUP BY` (similar ao `WHERE`, mas para grupos).
- `WHERE` filtra **linhas** antes do agrupamento; `HAVING` filtra **grupos** depois do agrupamento.

### 5.1 Sintaxe

```sql
SELECT coluna, COUNT(*)
FROM tabela
GROUP BY coluna
HAVING condição_sobre_grupo;
```

### 5.2 Exemplo

```sql
SELECT categoria, SUM(valor) AS total
FROM vendas
GROUP BY categoria
HAVING SUM(valor) > 100;
```

**Resultado:** apenas categorias com soma maior que 100.

### 5.3 Comparação: `WHERE` vs. `HAVING`

| WHERE | HAVING |
| --- | --- |
| Filtra **linhas** | Filtra **grupos** |
| Antes do `GROUP BY` | Depois do `GROUP BY` |
| Não usa funções de agregação | Usa funções de agregação |

## 6. Exemplo Completo (`GROUP BY` + `HAVING`)

```sql
SELECT x, SUM(y) AS total
FROM tabela
WHERE x < 'c'           -- filtra linhas antes do agrupamento
GROUP BY x
HAVING SUM(y) > 3;      -- filtra grupos com soma > 3
```

- A cláusula `WHERE` elimina linhas com `x >= 'c'`.
- O `GROUP BY` agrupa por `x`.
- O `HAVING` mantém apenas grupos com `SUM(y) > 3`.

## 7. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **INNER JOIN** | Apenas correspondências em ambas as tabelas. |
| **LEFT JOIN** | Todas as linhas da tabela esquerda + correspondências. |
| **RIGHT JOIN** | Todas as linhas da tabela direita + correspondências. |
| **FULL JOIN** | Todas as linhas de ambas as tabelas. |
| **CROSS JOIN** | Produto cartesiano (todas as combinações). |
| **GROUP BY** | Agrupa linhas com valores iguais. |
| **HAVING** | Filtra grupos após `GROUP BY`. |
| **WHERE** | Filtra linhas antes do `GROUP BY`. |

---

*Material complementar à aula "PostgreSQL – JOIN, GROUP BY e HAVING" (professor Washington Henrique Almeida, Gran Concursos).*