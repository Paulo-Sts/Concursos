# Anotações – Python para Análise de Dados/IA – Pandas II (Series e DataFrame)

## 1. Revisão: Pandas e suas Estruturas

- Pandas é uma biblioteca Python de código aberto para **análise e manipulação de dados**, amplamente utilizada em mineração de dados, ciência de dados e machine learning.
- Permite leitura de dados de diversas fontes: CSV, Excel, JSON, XML, bancos de dados SQL (via consultas `SELECT`).
- Suas principais estruturas são:
  - **Series** – unidimensional (uma coluna).
  - **DataFrame** – bidimensional (tabela com linhas e colunas).

> ### 1.1 Relação com NumPy
> - O Pandas é **construído sobre o NumPy**.
> - Cada **Series** é baseada em um array NumPy (portanto, homogênea internamente).
> - O **DataFrame** é uma coleção de Series (colunas) que podem ser de tipos diferentes → estrutura **heterogênea**.

## 2. Series – Estrutura Unidimensional

### 2.1 Definição e características

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Unidimensionalidade** | Contém apenas uma coluna de dados. |
| **Indexação** | Cada valor possui um rótulo (índice), que pode ser numérico (padrão) ou textual (personalizado). |
| **Tipo único de dado** | Cada série armazena dados de um único tipo (ex.: `int64`, `string`, `float64`). |
| **Operações vetorizadas** | Permite cálculos rápidos (soma, média, filtragem) diretamente sobre a coluna. |
| **Base** | Assentada em arrays do NumPy, herdando a homogeneidade por coluna. |

### 2.2 Criação de Series

#### 2.2.1 A partir de uma lista (índices padrão)

```python
import pandas as pd

linguagens = ["Python", "Java", "PHP", "C"]
series = pd.Series(linguagens)
print(series)
```

**Resultado:**
```
0    Python
1      Java
2       PHP
3         C
dtype: object
```

- Os índices padrão são numéricos, começando em **0**.

#### 2.2.2 A partir de uma lista com índices personalizados (parâmetro `index`)

```python
series = pd.Series(
    linguagens,
    index=["l1", "l2", "l3", "l4"]
)
print(series["l2"])   # Java
```

- A quantidade de índices deve ser **igual** à quantidade de valores.
- O acesso pode ser feito pelo rótulo personalizado.

#### 2.2.3 A partir de um dicionário (chave = índice, valor = dado)

```python
dados = {
    'Segunda': 120,
    'Terça': 340,
    'Quarta': 560,
    'Quinta': 430,
    'Sexta': 210
}
vendas = pd.Series(dados)
```

- As **chaves** do dicionário tornam-se os **índices** da Series.
- Os **valores** tornam-se os **dados**.

### 2.3 Acesso e filtragem

```python
print(vendas['Quarta'])            # 560
print(vendas[vendas > 300])        # retorna apenas os valores > 300
```

- Filtragem direta sobre a Series: `series[condição]` retorna uma nova Series com os elementos que atendem à condição.

### 2.4 Métodos estatísticos e agregadores

| MÉTODO | DESCRIÇÃO |
| --- | --- |
| `series.mean()` | Média |
| `series.sum()` | Soma total |
| `series.min()` | Valor mínimo |
| `series.max()` | Valor máximo |
| `series.std()` | Desvio padrão |

**Exemplo:**
```python
print(vendas.mean())   # 332.0
print(vendas.sum())    # 1660
```

### 2.5 Método `info()` – informações gerais

```python
print(vendas.info())
```

**Saída típica:**
```
<class 'pandas.core.series.Series'>
Index: 5 entries, Segunda to Sexta
Series name: None
Non-Null Count  Dtype
5 non-null      int64
dtypes: int64(1)
memory usage: 80.0+ bytes
```

- Mostra: classe, número de entradas, contagem de valores **não nulos**, tipo de dado, uso de memória.

### 2.6 Método `describe()` – resumo estatístico

```python
print(vendas.describe())
```

**Saída:**
```
count     5.000000
mean    332.000000
std     174.269906
min     120.000000
25%     210.000000
50%     340.000000
75%     430.000000
max     560.000000
dtype: float64
```

O método `describe()` gera automaticamente:

| ESTATÍSTICA | DESCRIÇÃO |
| --- | --- |
| `count` | Número de elementos não nulos |
| `mean` | Média aritmética |
| `std` | Desvio padrão |
| `min` | Valor mínimo |
| `25%` | Primeiro quartil (percentil 25) |
| `50%` | Mediana (percentil 50) |
| `75%` | Terceiro quartil (percentil 75) |
| `max` | Valor máximo |

> ### 2.6.1 Cálculo de percentis com poucos elementos (ex.: 3 elementos)
> - Valores ordenados: `[10, 23, 78]`
> - `min = 10`, `max = 78`, `50% (mediana) = 23`
> - **25%** = média entre o primeiro e o segundo: `(10+23)/2 = 16,5`
> - **75%** = média entre o segundo e o terceiro: `(23+78)/2 = 50,5`

## 3. DataFrame – Estrutura Bidimensional

### 3.1 Definição

- **DataFrame** é a principal estrutura do Pandas para análise de dados.
- **Bidimensional** – organizado em **linhas e colunas**.
- Cada **coluna** é uma **Series**.
- Diferente do NumPy (estrutura homogênea), o DataFrame é **heterogêneo**: colunas podem ter tipos diferentes (ex.: string, int, float).

### 3.2 Características

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Estrutura bidimensional** | Tabela com linhas e colunas |
| **Linhas e colunas rotuladas** | Índices (linhas) e nomes (colunas) podem ser personalizados |
| **Colunas heterogêneas** | Cada coluna tem seu próprio tipo de dado (ex.: nomes → string, idades → int) |
| **Indexação flexível** | Acesso por posição (`iloc`) ou por rótulo (`loc`) |
| **Operações vetorizadas** | Suporte a cálculos rápidos e estatísticas por coluna/linha |
| **Integração com fontes de dados** | Pode ser criado a partir de listas, dicionários, arrays, CSV, Excel, SQL, Parquet etc. |

### 3.3 Criação de um DataFrame (revisão)

A partir de um dicionário (chaves = nomes das colunas, valores = listas com os dados):

```python
import pandas as pd

notas_alunos = {
    "Nome": ["Ana", "Bruno", "Carlos"],
    "Idade": [22, 25, 21],
    "Curso": ["Python", "Java", "Python"],
    "Nota": [8.5, 7.0, 9.2]
}
df = pd.DataFrame(notas_alunos)
print(df)
```

**Resultado:**
```
    Nome  Idade   Curso  Nota
0    Ana     22  Python   8.5
1  Bruno     25    Java   7.0
2  Carlos   21  Python   9.2
```

- Os índices das linhas são criados automaticamente a partir de 0 (caso não sejam especificados).

## 4. Questões de Concurso Comentadas

### 4.1 (CESPE/CEBRASPE/2023/DATAPREV – ANALISTA)

**Item:** "O Pandas é uma das bibliotecas de Python que é utilizada para trabalhar com análise de dados e é utilizada em mineração de dados, por exemplo, por oferecer uma série de funções que permitem a leitura e manipulação de dados."

**Gabarito:** **Certo**.

**Comentário:** O Pandas permite leitura (CSV, Excel, SQL), limpeza, transformação e preparação de dados para mineração e visualização.

### 4.2 (UFMT/2021/UFMT – TÉCNICO DE TI)

**Afirmativas:**
- I – Possui bibliotecas como pandas e numpy. **(Verdadeiro)**
- II – Disponibiliza documentação na Internet. **(Verdadeiro)**
- III – É uma linguagem de baixo nível. **(Falso – Python é de alto nível)**

**Gabarito:** **b) I e II, apenas**.

### 4.3 (CESPE/CEBRASPE/2023/DATAPREV – INTELIGÊNCIA DA INFORMAÇÃO)

**Código:**
```python
import pandas as pd
a = [10, 78, 23]
myvar = pd.Series(a, index=["x", "y", "z"])
print(myvar.describe())
```

**A questão apresentava um resultado falso (count = 4, mean = 38 etc.).**

**Análise do erro:**
- A série tem **3 elementos** → `count` deveria ser `3`, não `4`.
- `min` correto é `10` (não `38`).
- `std` correto é aproximadamente `36,09` (não `6,07`).
- Os percentis corretos para 3 elementos são:
  - `25% = 16,5`
  - `50% = 23`
  - `75% = 50,5`

> ### 4.3.1 Dica de prova
> - O **primeiro campo** a ser verificado em uma questão que apresenta um `describe()` é o **`count`**. Se estiver diferente do número real de elementos, o item já está **incorreto**.
> - Verifique também `min` e `max` (valores extremos) – são fáceis de conferir.

**Gabarito:** **Errado (E)**.

---

## GABARITO DAS QUESTÕES DO ARQUIVO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2023 – Dataprev) | C |
| 02 (UFMT/2021) | b |
| 03 (CESPE/2023 – Dataprev/Inteligência) | E |

---

*Material complementar à aula "Python para Análise de Dados/IA – Pandas II" (professor Rogério Araújo, Gran Concursos).*