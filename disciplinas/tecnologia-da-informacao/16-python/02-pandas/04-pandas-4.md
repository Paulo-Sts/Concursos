# Anotações – Python para Análise de Dados/IA – Pandas IV (Leitura de Arquivos e Métodos Essenciais)

## 1. Métodos de Visualização de DataFrame

### 1.1 `head(n)` – primeiras linhas

- **`df.head()`** retorna as **primeiras 5 linhas** (padrão).
- `df.head(2)` retorna as 2 primeiras linhas.
- Útil para verificar rapidamente a estrutura e os dados iniciais.

### 1.2 `tail(n)` – últimas linhas

- **`df.tail()`** retorna as **últimas 5 linhas** (padrão).
- `df.tail(3)` retorna as 3 últimas linhas.
- Útil para verificar o final do conjunto de dados.

> ### 1.2.1 Dica de prova (FGV/2025)
> - Para visualizar **as últimas 5 linhas** de um DataFrame, o comando correto é **`print(df.tail())`** (sem necessidade de passar `5`, pois é o padrão).
> - `df.head()` mostra as primeiras linhas; `df.bottom()` e `df.display()` não existem no Pandas.

### 1.3 `describe()` – resumo estatístico

- Retorna **medidas estatísticas** das **colunas numéricas** (int, float).
- As estatísticas incluem: `count`, `mean`, `std`, `min`, `25%`, `50%` (mediana), `75%`, `max`.
- **Não** se aplica a colunas de texto (object).

> ### 1.3.1 Reconhecimento em prova
> - Se o enunciado mostrar uma saída com `count`, `mean`, `std`, `min`, percentis e `max`, a função utilizada foi **`describe()`**.
> - Confirme com a pergunta: "O método DataFrame.describe() tem como função retornar **medidas estatísticas das colunas do dataframe**".

### 1.4 `info()` – informações gerais

- Mostra: classe, número de entradas, contagem de valores **não nulos**, tipo de cada coluna, uso de memória.
- Confunde-se às vezes com `describe()`, mas `info()` não apresenta estatísticas (média, desvio etc.).

### 1.5 `shape` – dimensão do DataFrame

- Atributo que retorna uma tupla `(linhas, colunas)`.
- Exemplo: `(4, 3)` significa 4 linhas e 3 colunas.

### 1.6 `df.T` – transposição

- Troca linhas por colunas (transposição). Não é um método comum de visualização inicial, mas aparece em provas.

## 2. Leitura de Arquivos com Pandas

### 2.1 Funções de leitura (principais)

| FUNÇÃO | FORMATO | DESCRIÇÃO |
| --- | --- | --- |
| `pd.read_csv()` | CSV (comma-separated values) | Arquivos separados por vírgula, ponto e vírgula ou outro delimitador. |
| `pd.read_json()` | JSON | Dados estruturados em formato JSON. |
| `pd.read_xml()` | XML | Dados estruturados em XML. |
| `pd.read_sql()` | SQL / Banco de dados | Requer uma consulta SQL e uma conexão com o banco. |
| `pd.read_excel()` | Excel (.xlsx, .xls) | Planilhas Excel. |
| `pd.read_parquet()` | Parquet | Formato colunar usado em Big Data, Data Lakes. |
| `pd.read_pickle()` | Pickle | Objetos Python serializados. |
| `pd.read_table()` | TXT / tabular | Arquivos de texto organizados em formato tabular. |
| `pd.read_html()` | HTML | Tabelas existentes em páginas HTML. |

> ### 2.1.1 Observação
> - `pd.read_sql()` recebe **dois parâmetros principais**: a consulta SQL (`SELECT ...`) e a conexão com o banco de dados.
> - As demais funções geralmente recebem apenas o caminho do arquivo (string).

### 2.2 Exemplo de leitura de CSV

```python
import pandas as pd

df = pd.read_csv('data.csv')   # arquivo separado por vírgula (padrão)
print(df.head())               # 5 primeiras linhas
print(df.tail())               # 5 últimas linhas
print(df.to_string())          # exibe todo o DataFrame (sem truncamento)
```

- **`df.to_string()`** retorna uma representação em string de todo o DataFrame, útil para visualização completa quando há muitas linhas.

### 2.3 Parâmetros de leitura de arquivos

| PARÂMETRO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| `filepath_or_buffer` (primeiro argumento) | Caminho do arquivo (obrigatório). | `'dados.csv'` |
| `sep` ou `delimiter` | Separador/delimitador de campos. Padrão é vírgula (`,`). | `sep=';'` |
| `encoding` | Codificação dos caracteres. | `encoding='utf-8'`, `encoding='latin1'` |
| `header` | Linha usada como cabeçalho das colunas (padrão é 0 – primeira linha). | `header=0`, `header=None` |
| `names` | Lista de nomes para as colunas (usado quando não há cabeçalho). | `names=['matricula','nome','idade']` |
| `usecols` | Selecionar colunas específicas. | `usecols=[0,2]` ou `usecols=['nome','idade']` |
| `nrows` | Número de linhas a ler. | `nrows=100` |
| `dtype` | Definir tipo de dados para colunas. | `dtype={'idade': int, 'salario': float}` |
| `parse_dates` | Converter colunas para tipo data/hora. | `parse_dates=['data_nascimento']` |
| `na_values` | Valores a serem interpretados como NaN (nulo). | `na_values=['', '?', 'N/A']` |

**Exemplo prático (arquivo com separador `;` e codificação UTF-8):**

```python
df = pd.read_csv('vendas.csv', sep=';', encoding='utf-8')
```

> ### 2.3.1 Atenção (pegadinha)
> - Se o arquivo estiver separado por **ponto e vírgula (`;`)** e você usar o separador padrão (vírgula), o Pandas **não separará as colunas corretamente**, podendo gerar apenas uma coluna.
> - Verifique sempre o separador real do arquivo antes de usar `pd.read_csv()`.

## 3. Questões de Concurso Comentadas

### 3.1 (FGV/2025/MPU – ANALISTA)

**Código:**
```python
import pandas as pd
processo = {"id_processo": [1,2,3,4,5,6], "valor_causa": [10,20,30,40,50,60]}
df = pd.DataFrame(processo)
```

**Pergunta:** Para visualizar as últimas 5 linhas do DataFrame, deve-se usar:

**Alternativas:** a) `print(df.head())`; b) `print(df.tail())`; c) `print(df.info(5))`; d) `print(df.bottom(5))`; e) `print(df.display(5))`.

**Gabarito:** **b) `print(df.tail())`**.

**Comentário:** `tail()` sem argumento retorna as últimas 5 linhas. `head()` retorna as primeiras. `bottom()` e `display()` não existem. `info()` não aceita `5` como argumento.

### 3.2 (CESPE/CEBRASPE/2025/FUNPRESP-EXE – ANALISTA)

**Item:** "A biblioteca Pandas utiliza o DataFrame, uma estrutura bidimensional em que diversos métodos podem ser aplicados e que serve de base para outras estruturas."

**Gabarito:** **Certo**.

**Comentário:** O DataFrame é bidimensional (linhas e colunas) e é a estrutura central do Pandas. Outras estruturas (como Series) são unidimensionais.

### 3.3 (CESPE/CEBRASPE/2025/EMBRAPA – ANALISTA)

**Código:**
```python
mydataset = { 'carro': ["BMW", "Volvo", "Ford"], 'passagens': [3, 7, 2] }
myvar = pd.DataFrame(mydataset)
print(myvar)
```

**Item:** "Ao executar o referido trecho de código pandas, será exibido um DataFrame com as colunas carro e passagens com os respectivos valores e índices automaticamente gerados."

**Gabarito:** **Certo**.

**Comentário:** O DataFrame é criado a partir de um dicionário; as chaves viram colunas, as listas viram dados. Índices numéricos (0,1,2) são gerados automaticamente.

### 3.4 (VUNESP/2024/UNESP – ANALISTA DE INFORMÁTICA)

**Item:** O método `DataFrame.describe()` tem como função retornar:

**Alternativa correta:** **e) medidas estatísticas das colunas do dataframe**.

**Comentário:** As demais alternativas correspondem a outras funções: correlação (`df.corr()`), dados inválidos (`df.isnull().sum()`), gráficos (requer Matplotlib).

### 3.5 (INSTITUTO ACESSO/2024/CÂMARA DE MANAUS – ANALISTA DE SEGURANÇA)

**Imagem (saída com `count`, `mean`, `min`, `max`, percentis)**: Comando que gerou a saída → **c) `df.describe()`**.

### 3.6 (CESPE/CEBRASPE/2023/TC-DF – AUDITOR)

**Item:** "Os métodos `head()` e `tail()` são usados para visualizar, respectivamente, as primeiras e as últimas posições de um objeto Pandas."

**Gabarito:** **Certo**.

### 3.7 (CESPE/CEBRASPE/2023/TC-DF – AUDITOR)

**Item:** "A classe `pandas.Series()` é usada para criar e manipular matrizes coluna, enquanto a classe `pandas.DataFrame()` é usada para criar e manipular matrizes multidimensionais."

**Gabarito:** **Errado**.

**Comentário:** A classe `DataFrame` é usada para estruturas **bidimensionais** (linhas e colunas), não "multidimensionais" (que seria um array 3D+). O termo "matrizes coluna" para Series está correto, mas a parte sobre DataFrame está imprecisa.

### 3.8 (CESPE/CEBRASPE/2023/DATAPREV – INTELIGÊNCIA)

**Item:** "A biblioteca Pandas apresenta os dados em uma estrutura de DataFrame, composta por linhas e colunas."

**Gabarito:** **Certo**.

### 3.9 (CESPE/CEBRASPE/2023/DATAPREV – INTELIGÊNCIA)

**Item:** "O método `describe()` da biblioteca Pandas retorna as linhas superiores e inferiores do DataFrame."

**Gabarito:** **Errado**.

**Comentário:** `describe()` retorna estatísticas; `head()` e `tail()` retornam linhas.

### 3.10 (CESPE/CEBRASPE/2023/DATAPREV – ENGENHARIA CIVIL)

**Item:** "A biblioteca Pandas permite a manipulação de data frames em Python."

**Gabarito:** **Certo**.

### 3.11 (CESPE/CEBRASPE/2023/DATAPREV – ENGENHARIA ELÉTRICA)

**Item:** "A leitura de arquivos .xml não requer a instalação da biblioteca Pandas."

**Gabarito:** **Certo**.

**Comentário:** É possível ler XML com outras bibliotecas (ex.: `xml.etree.ElementTree`), mas para usar `pd.read_xml()` é necessário ter o Pandas instalado. A afirmação é tecnicamente verdadeira: **não requer** Pandas (pode ser feito sem ele), embora o Pandas ofereça uma função para isso.

### 3.12 (CESPE/CEBRASPE/2023/DATAPREV – ENGENHARIA CIVIL)

**Item:** "Python só permite a leitura e a escrita de arquivos .csv e .xlsx por meio da biblioteca Pandas."

**Gabarito:** **Errado**.

**Comentário:** Python tem funções nativas para ler/escrever CSV (`csv` module) e bibliotecas como `openpyxl` para Excel. Pandas é uma das formas, não a única.

## 4. Síntese para Revisão Rápida

| MÉTODO/ATRIBUTO | DESCRIÇÃO | RETORNO |
| --- | --- | --- |
| `df.head(n=5)` | Primeiras `n` linhas | DataFrame |
| `df.tail(n=5)` | Últimas `n` linhas | DataFrame |
| `df.describe()` | Estatísticas das colunas numéricas | DataFrame |
| `df.info()` | Informações gerais (tipos, não nulos, memória) | None (imprime) |
| `df.shape` | Dimensão `(linhas, colunas)` | Tupla |
| `df.dtypes` | Tipos de cada coluna | Series |
| `df.to_string()` | Representação textual completa | String |
| `pd.read_csv('arquivo.csv', sep=';')` | Lê CSV com separador personalizado | DataFrame |

> ### 4.1 Dicas de prova
> - **Últimas 5 linhas** → `df.tail()` (não precisa argumento).
> - **Resumo estatístico** → `df.describe()`.
> - **Separador ponto e vírgula** → `sep=';'` em `read_csv`.
> - `head()` e `tail()` são os métodos corretos para visualizar partes do DataFrame; não existem `bottom()` ou `display()`.

## GABARITO DAS QUESTÕES DO ARQUIVO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/2025) | b |
| 02 (CESPE/2025 – FUNPRESP) | C |
| 03 (CESPE/2025 – EMBRAPA) | C |
| 04 (VUNESP/2024) | e |
| 05 (INSTITUTO ACESSO/2024) | c |
| 06 (CESPE/2023 – TC-DF) | C |
| 07 (CESPE/2023 – TC-DF) | E |
| 08 (CESPE/2023 – DATAPREV/Inteligência) | C |
| 09 (CESPE/2023 – DATAPREV/Inteligência) | E |
| 10 (CESPE/2023 – DATAPREV/Eng. Civil) | C |
| 11 (CESPE/2023 – DATAPREV/Eng. Elétrica) | C |
| 12 (CESPE/2023 – DATAPREV/Eng. Civil) | E |

---

*Material complementar à aula "Python para Análise de Dados/IA – Pandas IV" (professor Rogério Araújo, Gran Concursos).*