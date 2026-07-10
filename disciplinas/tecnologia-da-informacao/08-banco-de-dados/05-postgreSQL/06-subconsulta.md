# Anotações – PostgreSQL – Subconsulta (Subquery)

## 1. Operador de Concatenação (`||`)

- O operador `||` é usado para **concatenar** duas strings no PostgreSQL.
- É uma funcionalidade **exclusiva** do PostgreSQL (embora exista em outros SGBDs também).

### 1.1 Exemplos

```sql
SELECT text 'abc' || 'def' AS "texto e desconhecido";
```

**Resultado:** `abcdef`

- Quando o primeiro argumento é do tipo `text`, o analisador assume que o segundo também deve ser `text`.

```sql
SELECT 'abc' || 'def' AS "desconhecido";
```

**Resultado:** `abcdef`

- O operador `||` exige que os operandos sejam **strings** (caracteres), portanto devem estar entre aspas simples (`'`).

## 2. Subconsultas (Subqueries)

### 2.1 Definição

- Uma **subconsulta** (ou *subquery*) é uma consulta SQL aninhada dentro de outra consulta.
- Pode ser usada com:
  - `SELECT`
  - `INSERT`
  - `UPDATE`
  - `DELETE`

### 2.2 Terminologia

| TERMO | SIGNIFICADO |
| --- | --- |
| **Subquery (inner query)** | A consulta interna (dentro dos parênteses). |
| **Outer query** | A consulta externa que contém a subconsulta. |

### 2.3 Exemplo básico

```sql
SELECT film_id, title, rental_rate
FROM film
WHERE rental_rate > (
    SELECT AVG(rental_rate) FROM film
);
```

- A subconsulta interna calcula a **média** de `rental_rate` de todos os filmes.
- A consulta externa retorna apenas os filmes com `rental_rate` **maior que a média**.

### 2.4 Subconsulta com filtro adicional

```sql
SELECT film_id, title, rental_rate
FROM film
WHERE rental_rate > (
    SELECT AVG(rental_rate)
    FROM film
    WHERE category = 'Ação'
);
```

- A subconsulta calcula a média apenas dos filmes da categoria **Ação**.
- A consulta externa retorna filmes com `rental_rate` maior que essa média.

## 3. Subconsultas em outros comandos

### 3.1 `UPDATE` com subconsulta

```sql
UPDATE film
SET rental_rate = rental_rate * 1.1
WHERE film_id IN (
    SELECT film_id FROM film_category WHERE category_id = 5
);
```

- Atualiza o preço de filmes que pertencem a uma categoria específica.

### 3.2 `DELETE` com subconsulta

```sql
DELETE FROM film
WHERE film_id IN (
    SELECT film_id FROM film_category WHERE category_id = 5
);
```

- Remove filmes que pertencem a uma categoria específica.

### 3.3 `INSERT` com subconsulta

```sql
INSERT INTO film (title, rental_rate)
SELECT title, rental_rate
FROM old_films
WHERE rental_rate > 5;
```

- Insere na tabela `film` o resultado da consulta em `old_films`.

## 4. Comparação: Subconsulta vs. `JOIN`

| CRITÉRIO | SUBCONSULTA | JOIN |
| --- | --- | --- |
| **Uso típico** | Quando se quer comparar com um valor agregado (ex.: média). | Quando se quer combinar dados de duas tabelas. |
| **Performance** | Pode ser mais pesada se houver muitos níveis. | Geralmente mais eficiente para junções complexas. |
| **Níveis** | Pode ter vários níveis de aninhamento (2–4 níveis são comuns). | Não há aninhamento. |

> ### 4.1 Dica do professor
> - **Não existe um limite máximo** para níveis de subconsulta.
> - Porém, cada nível adiciona **processamento extra**.
> - Em bancos comerciais, **2 níveis** são comuns; **3 ou 4** são raros.

## 5. Boas Práticas

| BOA PRÁTICA | MOTIVO |
| --- | --- |
| **Prefira `JOIN`** quando possível | Geralmente mais eficiente. |
| **Use subconsulta** para valores agregados | Ex.: média, máximo, mínimo. |
| **Evite múltiplos níveis** | Aumenta a complexidade e o custo de processamento. |
| **Teste com dados reais** | O desempenho pode variar conforme o volume de dados. |

## 6. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| `||` | Operador de concatenação (exclusivo do PostgreSQL para strings). |
| **Subquery** | Consulta aninhada dentro de outra consulta. |
| **Inner query** | A consulta interna (executada primeiro). |
| **Outer query** | A consulta externa (usa o resultado da inner). |
| **Usos** | `SELECT`, `INSERT`, `UPDATE`, `DELETE`. |
| **Níveis** | Não há limite, mas recomenda-se evitar muitos níveis. |

---

*Material complementar à aula "PostgreSQL – Subconsulta" (professor Washington Henrique Almeida, Gran Concursos).*