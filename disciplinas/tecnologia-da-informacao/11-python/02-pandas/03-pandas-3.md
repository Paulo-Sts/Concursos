# Anotações – Python para Análise de Dados/IA – Pandas III (DataFrame: Atributos, Operações e Métodos)

## 1. Revisão: DataFrame como Estrutura Heterogênea

- Um **DataFrame** é uma estrutura bidimensional composta por **colunas** (cada coluna é uma **Series**) e **linhas**.
- Cada coluna (Series) é homogênea (todos os elementos do mesmo tipo – ex.: string, int, float).
- O **DataFrame como um todo é heterogêneo**, pois colunas diferentes podem ter tipos diferentes.
- O DataFrame é baseado em arrays do NumPy, mas oferece **indexação rotulada** (por nome de linha e coluna).

> ### 1.1 Comparação com NumPy
> - NumPy array: estrutura homogênea, índices numéricos apenas.
> - DataFrame: heterogêneo, índices e colunas nomeados, construído sobre Series (que são arrays NumPy com rótulos).

## 2. Atributos Importantes do DataFrame

| ATRIBUTO | DESCRIÇÃO | EXEMPLO DE SAÍDA |
| --- | --- | --- |
| `df.shape` | Tupla `(linhas, colunas)` | `(4, 3)` → 4 linhas, 3 colunas |
| `df.columns` | Nomes das colunas (índice das colunas) | `Index(['Produto', 'Preço', 'Quantidade'], dtype='object')` |
| `df.index` | Rótulos das linhas (índice das linhas) | `Index(['P1', 'P2', 'P3', 'P4'], dtype='object')` |
| `df.dtypes` | Tipo de cada coluna (plural) | `Produto      object`<br>`Preço       float64`<br>`Quantidade    int64` |

> ### 2.1 Atenção: `dtype` vs `dtypes`
> - No **NumPy** (array único): `array.dtype` (singular).
> - No **Pandas** (DataFrame com várias colunas): `df.dtypes` (plural) retorna uma Series com o tipo de cada coluna.
> - Para uma **Series** (coluna individual): `series.dtype` (singular).

## 3. Principais Operações com DataFrame

### 3.1 Selecionar uma coluna inteira

```python
df['Preço']          # retorna uma Series
df.Preço             # notação equivalente (se o nome da coluna não tiver espaços)
```

### 3.2 Filtrar linhas com base em condição

```python
df[df['Preço'] > 20]   # retorna apenas as linhas onde Preço > 20
```

- A condição `df['Preço'] > 20` gera uma Series booleana.
- O DataFrame resultante mantém todas as colunas, apenas com as linhas que atendem à condição.

### 3.3 Adicionar nova coluna

```python
df['País'] = 'Brasil'    # adiciona uma coluna constante
```

### 3.4 Remover coluna

```python
df.drop('cidade', axis=1, inplace=True)
# axis=1: coluna; axis=0: linha.
```

## 4. Métodos Essenciais do DataFrame

### 4.1 `describe()` – Resumo estatístico

- Aplica-se apenas a **colunas numéricas** (int, float).
- Retorna um DataFrame com as seguintes estatísticas:

| ESTATÍSTICA | DESCRIÇÃO |
| --- | --- |
| `count` | Número de elementos não nulos |
| `mean` | Média |
| `std` | Desvio padrão |
| `min` | Valor mínimo |
| `25%` | Primeiro quartil (percentil 25) |
| `50%` | Mediana (segundo quartil) |
| `75%` | Terceiro quartil (percentil 75) |
| `max` | Valor máximo |

> ### 4.1.1 Exemplo com duas colunas numéricas
> ```python
> print(df.describe())
> # Saída: duas colunas (Preço, Quantidade) com as 8 estatísticas acima.
> ```

### 4.2 `head(n)` – Amostra das primeiras linhas

- `df.head()` → **5 primeiras** linhas (padrão).
- `df.head(10)` → 10 primeiras linhas.

### 4.3 `tail(n)` – Amostra das últimas linhas

- `df.tail()` → **5 últimas** linhas.
- `df.tail(2)` → 2 últimas linhas.

## 5. Indexação: `iloc` vs `loc`

| MÉTODO | BASE | DESCRIÇÃO |
| --- | --- | --- |
| `df.iloc[linha, coluna]` | Posição (inteiro) | Acesso por índice numérico (como array). |
| `df.loc[linha, coluna]` | Rótulo (nome) | Acesso por rótulo do índice/coluna. |

**Exemplo (índices personalizados):**

```python
df = pd.DataFrame(produtos, index=['P1', 'P2', 'P3', 'P4'])
print(df.loc['P5'])   # acessa a linha com rótulo P5
print(df.iloc[4])     # acessa a quinta linha (índice numérico 4)
```

> ### 5.1 Quando usar cada um
> - **`iloc`** → quando se conhece a posição (ex.: primeira linha, terceira coluna).
> - **`loc`** → quando se usa rótulos (ex.: linha "P5", coluna "Preço").

## 6. Exemplos Práticos (Códigos dos Slides)

### 6.1 Exemplo 2: DataFrame com índice personalizado

```python
produtos = {
    'Produto': ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'],
    'Preço': [10.5, 20.0, 15.0, 30.0, 25.5, 22.0, 18.0, 40.0],
    'Quantidade': [5, 3, 8, 2, 6, 7, 4, 10]
}
df = pd.DataFrame(produtos, index=['P1','P2','P3','P4','P5','P6','P7','P8'])
print(df.loc['P5'])   # linha com rótulo P5 → Produto E, Preço 25.5, Quantidade 6
```

### 6.2 Exemplo 4: Filtragem condicional

```python
print(df[df['Preço'] > 20])
# Retorna linhas com índices 3, 4, 5, 7 (Produtos D, E, F, H)
```

### 6.3 Exemplo 5: `describe()` em DataFrame com duas colunas numéricas

```python
print(df.describe())
# Saída (valores fictícios):
#          Preço   Quantidade
# count  8.000000     8.000000
# mean  22.625000     5.625000
# std    9.245655     2.669270
# min   10.500000     2.000000
# 25%   17.250000     3.750000
# 50%   21.000000     5.500000   ← mediana da Quantidade (média entre 5 e 6)
# 75%   26.625000     7.250000
# max   40.000000    10.000000
```

- O cálculo da mediana para quantidade par de elementos: média dos dois centrais (5 e 6 → 5.5).

### 6.4 Exemplo 6: `head()` e `tail()`

```python
print(df.head())      # 5 primeiras linhas (índices 0 a 4)
print(df.tail(2))     # 2 últimas linhas (índices 6 e 7)
```

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/CEBRASPE/2026/TCE-RN – AUDITOR)

**Item:** "No ecossistema Python, a biblioteca Pandas oferece a estrutura DataFrame, projetada para manipulação eficiente de dados tabulares bidimensionais com eixos rotulados para linhas e colunas."

**Gabarito:** **Certo**.

**Comentário:** O DataFrame é bidimensional, com índices para linhas e nomes para colunas, permitindo acesso por rótulo (`loc`) ou posição (`iloc`).

### 7.2 (FUVEST/2025/USP – ESPECIALISTA EM LABORATÓRIO/INFORMÁTICA BIOLÓGICA)

**Alternativa correta:** **b) O Pandas oferece estruturas como DataFrames, permitindo manipular grandes conjuntos de dados biológicos de maneira eficiente, enquanto o NumPy fornece operações vetorizadas para cálculos matemáticos otimizados.**

**Comentário:** As demais alternativas contêm erros: (a) Pandas é eficiente para grandes volumes; (c) NumPy não substitui Pandas (são complementares); (d) Pandas não dispensa métodos estatísticos adicionais; (e) ambas são usadas em diversas áreas, não só bioinformática.

### 7.3 (FUVEST/2025/USP – ANALISTA DE SISTEMAS)

**Código:**
```python
import pandas as pd
dados = {
    'Nome': ['Ivo', 'Iza', 'Ney', 'Ana'],
    'Idade': [28, 34, 23, 21],
    'Salario': [3000, 4000, 1500, 2000]
}
df = pd.DataFrame(dados)
t_idade = df['Idade'].dtype
print(f'O tipo da coluna Idade é: {t_idade}')
```

**Saída correta:** **a) O tipo da coluna "Idade" é: int64**.

**Comentário:** A coluna "Idade" contém valores inteiros, e o Pandas infere o tipo como `int64`. `df['Idade'].dtype` retorna o tipo da Series.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2026) | C |
| 02 (FUVEST/2025 – Bioinformática) | b |
| 03 (FUVEST/2025 – Analista) | a |

---

*Material complementar à aula "Python para Análise de Dados/IA – Pandas III" (professor Rogério Araújo, Gran Concursos).*