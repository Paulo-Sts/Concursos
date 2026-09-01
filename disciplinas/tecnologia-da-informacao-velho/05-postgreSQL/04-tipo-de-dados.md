# Anotações – PostgreSQL – Tipos de Dados

## 1. Visão Geral

O PostgreSQL suporta:
- Todos os **tipos padrão do SQL**.
- Tipos de **utilidade geral**.
- Um **rico conjunto de tipos geométricos**.
- Tipos modernos como **JSON, XML, UUID, arrays e intervalos**.

> ### 1.1 Origem da diversidade de tipos
> - O PostgreSQL foi criado para ser um **concorrente open-source do Oracle**.
> - Por isso, possui uma grande variedade de tipos de dados.

## 2. Tipos Numéricos

| TIPO | TAMANHO | DESCRIÇÃO | FAIXA |
| --- | --- | --- | --- |
| `smallint` | 2 bytes | Inteiro pequeno | -32.768 a +32.767 |
| `integer` (int) | 4 bytes | Inteiro padrão | -2.147.483.648 a +2.147.483.647 |
| `bigint` | 8 bytes | Inteiro grande | -9.223.372.036.854.775.808 a +9.223.372.036.854.775.807 |
| `decimal` | Variável | Precisão definida pelo usuário (exata) | Até 131.072 dígitos antes da vírgula; até 16.383 depois |
| `numeric` | Variável | Mesmo que `decimal` | Mesma faixa |
| `real` | 4 bytes | Precisão variável (inexata) | 6 casas decimais de precisão |
| `double precision` | 8 bytes | Precisão variável (inexata) | 15 casas decimais de precisão |
| `serial` | 4 bytes | Auto incremento (inteiro) | 1 a 2.147.483.647 |
| `bigserial` | 8 bytes | Auto incremento grande | 1 a 9.223.372.036.854.775.807 |

> ### 2.1 Diferenças importantes
> - `decimal` e `numeric` são **exatos** (precisão definida pelo usuário).
> - `real` e `double precision` são **inexatos** (precisão variável – apropriados para cálculos científicos).
> - `serial` e `bigserial` são **auto incremento** (criam uma *sequence* internamente).

## 3. Tipos Monetários

| TIPO | TAMANHO | DESCRIÇÃO | FAIXA |
| --- | --- | --- | --- |
| `money` | 8 bytes | Valor monetário com precisão fixa | -92.233.720.368.547.758,08 a +92.233.720.368.547.758,07 |

- A precisão fracionária é definida pela configuração `lc_monetary` (ex.: R$ 1.000,00).
- O padrão é o **dólar**, mas pode ser alterado para **real** ou outra moeda.

## 4. Tipos para Caracteres (Strings)

| TIPO | DESCRIÇÃO | TAMANHO |
| --- | --- | --- |
| `character varying(n)` / `varchar(n)` | Tamanho **variável** com limite | Até `n` caracteres |
| `character(n)` / `char(n)` | Tamanho **fixo** (preenchido com espaços) | Exatamente `n` caracteres |
| `text` | Tamanho **ilimitado** (não padrão SQL) | Qualquer tamanho |

> ### 4.1 Comparação
> - `varchar(n)` ocupa apenas o espaço usado (variável).
> - `char(n)` ocupa sempre `n` caracteres (espaços em branco também ocupam memória).
> - `text` é específico do PostgreSQL (não faz parte do padrão SQL).

### 4.2 Tipos internos (`name` e `"char"`)

| TIPO | TAMANHO | DESCRIÇÃO |
| --- | --- | --- |
| `name` | 64 bytes (63 caracteres + terminador) | Armazenamento de identificadores nos catálogos internos. |
| `"char"` (com aspas) | 1 byte (8 bits) | Tipo interno de um único byte. Difere de `char(1)` (que usa 2 bytes). |

## 5. Tipos Binários (`bytea`)

| TIPO | TAMANHO | DESCRIÇÃO |
| --- | --- | --- |
| `bytea` | 1 ou 4 bytes + string binária real | String binária de tamanho variável (*raw bytes*). |

- Apropriado para armazenar **bytes brutos** (dados binários).
- Suporta dois formatos externos:
  - **`hex`**: codifica cada byte como dois dígitos hexadecimais (mais rápido e compatível com aplicações externas).
  - **`escape`**: formato tradicional do PostgreSQL (representação ASCII).

## 6. Tipos de Data e Hora

| TIPO | TAMANHO | DESCRIÇÃO |
| --- | --- | --- |
| `date` | 4 bytes | Data (sem hora) |
| `time [ (p) ] [ without time zone ]` | 8 bytes | Hora do dia (sem data) |
| `time [ (p) ] with time zone` | 12 bytes | Hora com fuso horário |
| `timestamp [ (p) ] [ without time zone ]` | 8 bytes | Data e hora (sem fuso) |
| `timestamp [ (p) ] with time zone` | 8 bytes | Data e hora com fuso |
| `interval [ fields ] [ (p) ]` | 16 bytes | Intervalo de tempo |

- `p` é um valor de precisão opcional (número de dígitos fracionários nos segundos).
- O PostgreSQL é **muito flexível** na entrada de datas e horas.

> ### 6.1 Formatos de data
> - Formato **recomendado**: `YYYY-MM-DD` (ISO 8601) – ex.: `1999-01-08`.
> - O formato padrão nos EUA é **MM/DD/YYYY**; no Brasil, **DD/MM/YYYY**.
> - O PostgreSQL aceita múltiplos formatos, mas o **formato ISO** é o mais seguro.

## 7. Tipo Booleano (`boolean`)

| TIPO | TAMANHO | DESCRIÇÃO |
| --- | --- | --- |
| `boolean` | 1 byte | Verdadeiro, falso ou desconhecido (NULL) |

**Valores aceitos para `true`:** `true`, `yes`, `on`, `1`  
**Valores aceitos para `false`:** `false`, `no`, `off`, `0`

- A saída padrão do PostgreSQL para booleano é **`t`** ou **`f`**.

> ### 7.1 Terceiro estado
> - Além de `true` e `false`, o booleano pode ser **`NULL`** (desconhecido).

## 8. Tipos Geométricos

| TIPO | TAMANHO | DESCRIÇÃO |
| --- | --- | --- |
| `point` | 16 bytes | Ponto no plano `(x, y)` |
| `line` | 32 bytes | Linha infinita `{A, B, C}` |
| `lseg` | 32 bytes | Segmento de linha finito |
| `box` | 32 bytes | Retângulo (caixa) |
| `path` (fechado) | 16 + 16n bytes | Caminho fechado (semelhante a polígono) |
| `path` (aberto) | 16 + 16n bytes | Caminho aberto |
| `polygon` | 40 + 16n bytes | Polígono |
| `circle` | 24 bytes | Círculo `<centro, raio>` |

- O PostgreSQL oferece funções e operadores para operações geométricas:
  - Escala, translação, rotação, interseção, etc.

## 9. Tipos de Dados (visão geral – menos cobrados)

| CATEGORIA | TIPOS |
| --- | --- |
| **Enumerados** | `enum` |
| **Geométricos** | `point`, `line`, `lseg`, `box`, `path`, `polygon`, `circle` |
| **Endereço de rede** | `inet`, `cidr`, `macaddr` |
| **Sequência de bits** | `bit`, `bit varying` |
| **Pesquisa de texto** | `tsvector`, `tsquery` |
| **UUID** | `uuid` |
| **XML** | `xml` |
| **JSON** | `json`, `jsonb` |
| **Matrizes** | `array` (ex.: `int[]`) |
| **Compostos** | Tipos definidos pelo usuário |
| **Intervalo** | `int4range`, `int8range`, `tsrange`, etc. |
| **Domínio** | `domain` (restrição sobre tipo base) |
| **Identificador de objeto** | `oid` |
| **pg_Isn** | Números ISBN, ISSN, etc. |
| **Pseudo-tipos** | `record`, `void`, `any` |

## 10. Destaques para Provas (O que mais cai)

| TIPO | POR QUE É COBRADO |
| --- | --- |
| `serial` / `bigserial` | Auto incremento (muito usado em concursos). |
| `varchar(n)` / `char(n)` | Diferença entre tamanho fixo e variável. |
| `text` | Específico do PostgreSQL (não padrão SQL). |
| `numeric` / `decimal` | Precisão exata definida pelo usuário. |
| `money` | Formatação monetária (lc_monetary). |
| `timestamp` | Data e hora (com ou sem fuso). |
| `boolean` | Valores aceitos para `true`/`false`. |
| `json` / `jsonb` | Suporte a dados JSON (crescente em provas). |

## 11. Síntese para Revisão Rápida

| TIPO | CATEGORIA | CARACTERÍSTICA PRINCIPAL |
| --- | --- | --- |
| `integer` | Numérico | 4 bytes, inteiro padrão. |
| `bigint` | Numérico | 8 bytes, inteiro grande. |
| `serial` | Numérico | Auto incremento (inteiro). |
| `numeric` | Numérico | Precisão exata definida pelo usuário. |
| `money` | Monetário | Valor com precisão fixa (formato local). |
| `varchar(n)` | Caractere | Tamanho variável com limite. |
| `char(n)` | Caractere | Tamanho fixo (preenchido com espaços). |
| `text` | Caractere | Tamanho ilimitado (não padrão SQL). |
| `bytea` | Binário | Dados binários (raw bytes). |
| `date` | Data/Hora | Data (sem hora). |
| `timestamp` | Data/Hora | Data e hora (com ou sem fuso). |
| `boolean` | Booleano | `true`, `false` ou `NULL`. |
| `json` / `jsonb` | JSON | Armazenamento de dados JSON. |
| `point` | Geométrico | Coordenada `(x, y)`. |

---

*Material complementar à aula "PostgreSQL – Tipos de Dados" (professor Washington Henrique Almeida, Gran Concursos).*