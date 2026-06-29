# Anotações – PostgreSQL – Tabelas (CREATE, DROP, ALTER)

## 1. PostgreSQL – Modelo Relacional com Características OO

- O PostgreSQL é um **SGBD relacional** com características de banco de dados **objeto-relacional**.
- **Atenção:** se a questão perguntar se o PostgreSQL é relacional, a resposta é **sim**. Se perguntar se é objeto-relacional, também é **verdadeiro**.
- As principais características de orientação a objetos incluem:
  - Tipos de dados como **`serial`** (auto incremento, semelhante ao `IDENTITY` do SQL Server ou `AUTO_INCREMENT` do MySQL).
  - Suporte a **herança** de tabelas (embora menos usado).
  - Tipos definidos pelo usuário (ex.: `point` para coordenadas geográficas).

## 2. Estrutura de Tabelas no PostgreSQL

### 2.1 Conceitos fundamentais

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Tabela (Relação)** | Estrutura principal de armazenamento. Composta por linhas e colunas. |
| **Linha (Tupla/Registro)** | Instância de uma tabela. Representa um registro completo. |
| **Coluna (Atributo)** | Define um campo da tabela com um tipo específico. |
| **Chave Primária (PK)** | Identifica unicamente cada registro. Não se repete e não pode ser nula. |
| **Chave Estrangeira (FK)** | Referencia a chave primária de outra tabela. Mantém a integridade referencial. |

### 2.2 Esquemas (Schemas)

- Objetos podem ser agrupados em **schemas** (subdivisões dentro de uma database).
- O esquema padrão do PostgreSQL é o **`public`**.
- Schemas permitem organizar objetos e controlar permissões de forma mais granular.

## 3. Comandos DDL para Tabelas

### 3.1 `CREATE TABLE`

**Sintaxe básica:**

```sql
CREATE TABLE nome_tabela (
    coluna1 tipo [restrições],
    coluna2 tipo [restrições],
    ...
);
```

**Exemplo 1 – Tabela "clima":**

```sql
CREATE TABLE clima (
    cidade varchar(80),
    temp_min int,      -- temperatura mínima
    temp_max int,      -- temperatura máxima
    prpc real,         -- precipitação
    dia date
);
```

**Exemplo 2 – Tabela "cidades" com tipo geográfico `point`:**

```sql
CREATE TABLE cidades (
    nome varchar(80),
    localizacao point   -- tipo para coordenadas geográficas
);
```

### 3.2 `DROP TABLE`

```sql
DROP TABLE nome_tabela;
```

- Remove a tabela e **todos os seus dados**.
- Se houver referências (FK), o comando pode falhar a menos que seja usado `CASCADE`.

### 3.3 `ALTER TABLE` – Modificações em tabelas

#### 3.3.1 Adicionar coluna (`ADD COLUMN`)

```sql
ALTER TABLE nome_tabela ADD COLUMN nome_coluna tipo;
```

**Exemplo:**

```sql
ALTER TABLE clima ADD COLUMN umidade real;
```

#### 3.3.2 Remover coluna (`DROP COLUMN`)

```sql
ALTER TABLE nome_tabela DROP COLUMN nome_coluna;
```

**Com `CASCADE` (remove também referências):**

```sql
ALTER TABLE nome_tabela DROP COLUMN nome_coluna CASCADE;
```

> ### 3.3.2.1 O que é `CASCADE`?
> - Se uma coluna é referenciada por uma chave estrangeira em outra tabela, o PostgreSQL **impede** a remoção silenciosa.
> - Com `CASCADE`, todas as dependências (FK, views, etc.) são removidas junto com a coluna.
> - **Cuidado:** pode apagar mais dados do que o pretendido. Não é uma boa prática usar `CASCADE` indiscriminadamente.

#### 3.3.3 Alterar valor padrão de coluna (`SET DEFAULT` / `DROP DEFAULT`)

```sql
-- Definir valor padrão
ALTER TABLE nome_tabela ALTER COLUMN nome_coluna SET DEFAULT 10;

-- Remover valor padrão
ALTER TABLE nome_tabela ALTER COLUMN nome_coluna DROP DEFAULT;
```

- O `SET DEFAULT` afeta apenas **novas inserções** – dados existentes não são alterados.
- `DROP DEFAULT` equivale a definir o padrão como `NULL`.

#### 3.3.4 Alterar tipo de coluna (`TYPE`)

```sql
ALTER TABLE nome_tabela ALTER COLUMN nome_coluna TYPE novo_tipo;
```

**Exemplo (convertendo para decimal com precisão):**

```sql
ALTER TABLE clima ALTER COLUMN temp_max TYPE numeric(10,2);
```

- A conversão é **implícita**: só funciona se todos os valores existentes forem compatíveis com o novo tipo.
- Exemplo: uma coluna `varchar` com letras **não pode** ser convertida para `int`.

#### 3.3.5 Renomear coluna

```sql
ALTER TABLE nome_tabela RENAME COLUMN nome_antigo TO nome_novo;
```

**Exemplo:**

```sql
ALTER TABLE clima RENAME COLUMN prpc TO precipitacao;
```

#### 3.3.6 Renomear tabela

```sql
ALTER TABLE nome_tabela RENAME TO novo_nome;
```

**Exemplo:**

```sql
ALTER TABLE clima RENAME TO dados_climaticos;
```

## 4. Resumo dos Comandos ALTER TABLE

| AÇÃO | COMANDO |
| --- | --- |
| Adicionar coluna | `ALTER TABLE t ADD COLUMN c tipo;` |
| Remover coluna | `ALTER TABLE t DROP COLUMN c;` |
| Remover coluna com cascata | `ALTER TABLE t DROP COLUMN c CASCADE;` |
| Definir valor padrão | `ALTER TABLE t ALTER COLUMN c SET DEFAULT valor;` |
| Remover valor padrão | `ALTER TABLE t ALTER COLUMN c DROP DEFAULT;` |
| Alterar tipo de coluna | `ALTER TABLE t ALTER COLUMN c TYPE novo_tipo;` |
| Renomear coluna | `ALTER TABLE t RENAME COLUMN c_antigo TO c_novo;` |
| Renomear tabela | `ALTER TABLE t_antigo RENAME TO t_novo;` |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/2019/TJ-AM – Assistente Judiciário)

**Item:** "Um SGBD trata do acesso ao banco e pode ser executado independentemente pelo Oracle, MySQL ou PostgreSQL; no entanto, cada SGBD utiliza DML e DDL específicas."

**Gabarito: Certo (C).**

**Comentário:**
- Cada SGBD tem sua própria **versão do SQL** (comandos e tipos específicos).
- Embora sigam o padrão ANSI SQL, há diferenças entre eles (ex.: PL/SQL no Oracle, T-SQL no SQL Server, PL/pgSQL no PostgreSQL).

### 5.2 (CS-UFG/2019/IF Goiano – Técnico de TI)

**Item:** "Especificamente, o PostgreSQL:"

**Alternativa correta:** **b) oferece os tipos de dados JSON e XML.**

**Análise:**
- a) Incorreto – PostgreSQL permite índices em texto e números.
- b) **Correto** – PostgreSQL suporta JSON e XML.
- c) Incorreto – PostgreSQL foi criado nos anos 1990 (mais de uma década).
- d) Incorreto – PostgreSQL é compatível com nuvem (cloud computing).

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2019) | C |
| 02 (CS-UFG/2019) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Tipo do PostgreSQL** | Relacional + Objeto-relacional. |
| **CREATE TABLE** | Cria tabela com colunas e tipos. |
| **DROP TABLE** | Remove tabela e dados. |
| **ALTER TABLE ADD COLUMN** | Adiciona coluna. |
| **ALTER TABLE DROP COLUMN** | Remove coluna (com ou sem `CASCADE`). |
| **ALTER TABLE ALTER COLUMN** | Altera tipo ou valor padrão. |
| **ALTER TABLE RENAME** | Renomeia coluna ou tabela. |
| **CASCADE** | Remove dependências (FK, views) junto com a coluna/tabela. |
| **Suporte a JSON/XML** | Sim, o PostgreSQL oferece esses tipos. |

---

*Material complementar à aula "PostgreSQL – Tabelas" (professor Washington Henrique Almeida, Gran Concursos).*