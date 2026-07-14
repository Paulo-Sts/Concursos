# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO – ÁLGEBRA RELACIONAL

## 1. ÁLGEBRA RELACIONAL - CONCEITOS FUNDAMENTAIS

- A Álgebra Relacional constitui um conjunto básico de operações do modelo relacional.

- As operações da álgebra relacional permitem ao usuário especificar solicitações básicas de recuperação de tuplas.

- O resultado de uma recuperação é uma **nova relação**, que pode ser formada a partir de uma ou mais relações (operações em cascata).

- Uma sequência de operações em álgebra relacional forma uma **expressão**, cujo resultado também será uma relação.

> ### 1.1 Relação com SQL
> - O banco de dados transforma o SQL em álgebra relacional como técnica de otimização de desempenho.
> - A álgebra relacional é um conjunto de operações sobre relações, sendo gerada dessas operações uma relação de saída.

### 1.2 Classificação dos Operadores

- **Operadores Unários:** aplicados a uma única relação (ex.: SELEÇÃO, PROJEÇÃO, RENAME).

- **Operadores Binários:** aplicados a duas relações (ex.: UNIÃO, INTERSEÇÃO, DIFERENÇA, PRODUTO CARTESIANO, JUNÇÃO, DIVISÃO).

### 1.3 Divisão dos Operadores em Grupos

| Grupo | Operadores |
|-------|------------|
| Operações da Teoria Matemática dos Conjuntos | UNIÃO (U), INTERSEÇÃO (∩), DIFERENÇA (–), PRODUTO CARTESIANO (X) |
| Operações específicas para Bancos de Dados Relacionais | SELEÇÃO (σ), PROJEÇÃO (π), JUNÇÃO (⋈), DIVISÃO (÷) |

## 2. OPERADOR SELECT (σ) - SELEÇÃO

- Utilizado para selecionar um subconjunto de tuplas de uma relação que satisfaça a uma condição de seleção.

- É um operador **unário** (aplicado a uma única relação).

- Representação: **σ <condição de seleção> (R)**

- Uma condição de seleção é uma expressão booleana, podendo estar associada aos operadores booleanos **E (AND)** , **OU (OR)** e **NÃO (NOT)** .

### 2.1 Características da SELEÇÃO

- O operador SELECT (σ) é **comutativo** (a ordem não importa):

  **σ <condição1> (σ <condição2> (R)) = σ <condição2> (σ <condição1> (R))**

- O **grau** (número de colunas) da relação resultante é o **mesmo grau** de R.

- O **número de tuplas** na relação resultante é **sempre menor ou igual** ao número de tuplas de R.

### 2.2 Exemplos de SELEÇÃO

**Tabela PRODUTOS:**

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Café | Mercearia | R$ 8,99 | KG |
| Açúcar | Mercearia | R$ 10,20 | 5 KG |
| Sabão em Pó | Limpeza | R$ 9,90 | KG |
| Vinho | Bebida | R$ 59,90 | 750 ML |
| Refrigerante | Bebida | R$ 7,90 | 2 L |

**Exemplo 1:** Listar os produtos da categoria Bebida.

**σ categoria = "bebida" (PRODUTOS)**

Resultado:

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Vinho | Bebida | R$ 59,90 | 750 ML |
| Refrigerante | Bebida | R$ 7,90 | 2 L |

**Exemplo 2:** Listar os produtos da categoria Bebida com preço maior que R$ 10 (uso de "and").

**σ categoria = "bebida" and preço > 10 (PRODUTOS)**

Resultado:

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Vinho | Bebida | R$ 59,90 | 750 ML |

> ### 2.3 Correspondência com SQL
> - O comando **WHERE** do SQL corresponde à operação de **SELEÇÃO** (SELECT) da álgebra relacional, e NÃO à projeção.

## 3. OPERADOR PROJECT (π) - PROJEÇÃO

- Seleciona determinadas colunas da relação R, descartando outras.

- É um operador **unário** (aplicado a uma única relação).

- Representação: **π <lista de atributos> (R)**

> ### 3.1 ATENÇÃO: Remoção de Duplicatas
> - O operador PROJECT **remove tuplas duplicadas** quando os atributos projetados não pertencem à chave da relação R.
> - Esta é uma característica bastante cobrada em provas.

### 3.2 Características da PROJEÇÃO

- O **grau** (número de colunas) da relação resultante é igual ao **número de atributos existentes na lista**.

- O **número de tuplas** na relação resultante é **sempre menor ou igual** ao número de tuplas da relação R.

- A operação de projeção **NÃO é comutativa** (a ordem faz diferença):

  **π <list1> (π <list2> (R)) = π <list> (R)** — desde que list1 seja subconjunto de list2

### 3.3 Exemplos de PROJEÇÃO

**Exemplo 1:** Listar o nome e o preço de todos os produtos.

**π nome, preço (PRODUTOS)**

| NOME | PREÇO |
|------|-------|
| Café | R$ 8,99 |
| Açúcar | R$ 10,20 |
| Sabão em Pó | R$ 9,90 |
| Vinho | R$ 59,90 |
| Refrigerante | R$ 7,90 |

**Exemplo 2:** Listar as categorias de produtos.

**π categoria (PRODUTOS)**

| CATEGORIA |
|-----------|
| Mercearia |
| Limpeza |
| Bebida |

> ### 3.4 Comparação com SELEÇÃO
> - A SELEÇÃO atua sobre **linhas** (tuplas).
> - A PROJEÇÃO atua sobre **colunas** (atributos).
> - A SELEÇÃO mantém o grau (número de colunas).
> - A PROJEÇÃO reduz o grau.

### 3.5 Correspondência com SQL

- O comando **SELECT campo FROM tabela** (sem WHERE) corresponde a uma operação de **PROJEÇÃO** da álgebra relacional.

## 4. OPERADOR RENAME (ρ) - RENOMEAR

- Utilizado para renomear relações ou atributos.

- Representação:

  - **ρ <NovoNome> (Relação)**

  - **ρ <novoAtributo/atributoOriginal> (Relação)**

- É um operador **unário**.

### 4.1 Atribuição

- É possível agrupar operações e criar relações de resultado intermediário (atribuição).

- **Exemplo:**

  **BEBIDAS ← σ categoria = 'bebida' (PRODUTOS)**

- Em seguida, aplica-se a projeção:

  **π nome, preço (BEBIDAS)**

## 5. OPERADORES BINÁRIOS (TEORIA DOS CONJUNTOS)

### 5.1 UNIÃO (U)

- Produz uma relação que inclui todas as tuplas em R1 e R2, ou tanto R1 quanto R2.

- **Requisito:** R1 e R2 precisam ser **compatíveis na união** (mesmo número de atributos e domínios compatíveis).

### 5.2 INTERSEÇÃO (∩)

- Produz uma relação que inclui todas as tuplas em R1 e R2.

- **Requisito:** R1 e R2 precisam ser compatíveis na união.

### 5.3 DIFERENÇA (–)

- Produz uma relação que inclui todas as tuplas em R1 que não estão em R2.

- **Requisito:** R1 e R2 precisam ser compatíveis na união.

### 5.4 PRODUTO CARTESIANO (X)

- Produz uma relação que tem os atributos de R1 e R2 e inclui como tuplas todas as possíveis combinações de tuplas de R1 e R2.

- Não exige compatibilidade de esquemas.

- Pode gerar um grande número de tuplas (combinações).

## 6. OPERADORES DE JUNÇÃO

### 6.1 JUNÇÃO THETA (θ)

- Produz todas as combinações de tuplas de R1 e R2 que satisfazem a condição de junção.

- Utiliza o produto cartesiano como base, cruzando operações de forma combinatória.

- Representação: **R1 ⋈ <condição> R2**

### 6.2 EQUIJUNÇÃO

- Produz todas as combinações de tuplas de R1 e R2 que satisfazem uma condição de junção **apenas com comparações de igualdade**.

- É um caso especial da JUNÇÃO THETA onde a condição usa apenas o operador "=".

### 6.3 JUNÇÃO NATURAL (*)

- Mesmo conceito da EQUIJUNÇÃO, com a diferença que os **atributos de junção de R1 não são incluídos na relação resultante**.

- Se os atributos de junção tiverem os mesmos nomes, eles nem precisam ser especificados.

- Representação: **R1 * R2** (quando os atributos de junção têm os mesmos nomes)

## 7. OPERADOR DIVISÃO (÷)

- Produz uma relação R[X] que inclui todas as tuplas f[X] em R1(Z) que aparecerem em R1 em combinação com toda tupla de R2(Y), onde Z = X U Y.

- Representação: **R1 (Z) ÷ R2 (Y)**

## 8. RESUMO DOS OPERADORES

| Elemento | Significado | Tipo |
|----------|-------------|------|
| ← (atribuição) | Armazena o resultado de uma operação numa variável | - |
| σ (seleção) | Filtra linhas com base em uma condição | Unário |
| π (projeção) | Seleciona colunas específicas | Unário |
| ρ (rename) | Renomeia relação ou atributos | Unário |
| U (união) | Combina tuplas de duas relações | Binário |
| ∩ (interseção) | Tuplas comuns a duas relações | Binário |
| – (diferença) | Tuplas em uma relação mas não na outra | Binário |
| X (produto cartesiano) | Combina todas as tuplas de duas relações | Binário |
| ⋈ (junção) | Combina tuplas com base em condição | Binário |
| ÷ (divisão) | Tuplas que se combinam com todas as de outra relação | Binário |

## 9. QUESTÕES COMENTADAS

### Questão 01 (CESPE/ABIN/2018)

**O comando SQL `select campo from tabela` corresponde a uma operação de projeção da álgebra relacional.**

**Gabarito: C** (correto para o cenário apresentado — sem WHERE, apenas seleção de colunas específicas)

### Questão 02 (CESPE/FUB/2018)

**O comando WHERE do SQL corresponde à operação de projeção da álgebra relacional.**

**Gabarito: E** (WHERE corresponde à SELEÇÃO, não à PROJEÇÃO)

> ### Atenção
> - **SELECT (SQL) + WHERE** → SELEÇÃO na álgebra
> - **SELECT (SQL) sem WHERE** → PROJEÇÃO na álgebra

### Questão 03 (CESPE/FUB/2018)

**Álgebra relacional é um conjunto de operações sobre relações, sendo gerada dessas operações uma relação de saída.**

**Gabarito: C**

### Questão 04 (CESGRANRIO/PETROBRAS/2023)

**Dentre os operadores listados, o único NÃO binário é:**
- a) divisão (binário)
- b) projeção (unário) ✓
- c) junção natural (binário)
- d) junção externa esquerda (binário)
- e) produto cartesiano (binário)

**Gabarito: b**

### Questão 05 (FGV/PGM/NITÉROI/2023)

**Consulta SQL: `SELECT a.X, b.Y FROM T1 a, T2 b WHERE a.R = b.S`**

Operações necessárias:
- `T1 a, T2 b` → **PRODUTO CARTESIANO**
- `SELECT a.X, b.Y` → **PROJEÇÃO** (seleciona colunas específicas)
- `WHERE a.R = b.S` → **SELEÇÃO** (filtra linhas)

**Gabarito: d** (Produto, Projeção, Seleção)

## 10. LINGUAGENS FORMAIS PARA O MODELO DE DADOS RELACIONAL

- **Álgebra relacional:** operações, operações unárias e binárias.

- **Cálculos relacionais:** baseados no cálculo de predicado.

- Algumas consultas não podem ser declaradas com as operações básicas da álgebra relacional.