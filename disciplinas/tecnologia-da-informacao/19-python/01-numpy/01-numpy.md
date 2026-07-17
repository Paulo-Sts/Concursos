# Anotações

# Python para Análise de Dados/IA - NumPy

## 1. Contextualização e Importância

### 1.1 Análise de Dados e IA em Concursos

- A análise de dados e a inteligência artificial são temas amplamente cobrados em concursos públicos, especialmente diante da transformação digital e da necessidade de automatização de tarefas e tomada de decisões baseada em dados.
- Concursos recentes, inclusive fora da área de TI (ex.: áreas fiscais para cargos gerais), têm exigido esses conteúdos de forma significativa desde 2020/2021.
- A linguagem Python, por meio de bibliotecas especializadas (**NumPy**, **Pandas**, **Matplotlib**, etc.), é a principal ferramenta programática para esses fins.

### 1.2 Bibliotecas mais cobradas

- **NumPy** e **Pandas** são as duas bibliotecas mais exigidas em provas.
- NumPy é a base para outras bibliotecas (Pandas, SciPy, etc.).

> ### 1.2.1 Diferenciação de bibliotecas (conforme questão CESPE/2025)
> - **Manipulação e análise de dados:** NumPy, Pandas, SciPy, Statsmodels.
> - **Visualização de dados:** Matplotlib, Seaborn, Plotly (gráficos e plots interativos).

## 2. Fundamentos do NumPy

### 2.1 Definição

- **NumPy** = *Numerical Python*.
- Principal biblioteca de computação numérica em Python.
- Pacote fundamental para computação científica, servindo de base para Pandas e SciPy.

### 2.2 NDArray – Objeto Central

- **NDArray** = *N-dimensional array* (array de N dimensões).
- É um objeto que representa um array **multidimensional**, **homogêneo** e de **tamanho fixo**.

#### 2.2.1 Características principais

- **Multidimensional:** pode possuir uma ou mais dimensões.
- **Homogêneo:** todos os elementos devem ser do mesmo tipo (semelhante aos arrays do Java).
- **Tamanho fixo:** após criado com determinado número de elementos, não é possível alterar seu tamanho.
- **Desempenho superior:** pode ser até **50 vezes mais rápido** que as listas tradicionais do Python para armazenamento e processamento de dados numéricos.
- **Container numérico** projetado para cálculo rápido e manipulação eficiente de dados multidimensionais.

> ### 2.2.2 Comparação com listas do Python
> - **Listas tradicionais:** permitem elementos de tipos diferentes (heterogêneas) e tamanho variável.
> - **NDArray:** exige tipo único e tamanho fixo, mas oferece muito maior eficiência para dados numéricos.

## 3. Atributos do NDArray

### 3.1 `dtype`

- Retorna o tipo dos elementos armazenados no array (ex.: `int64`, `<U6` para strings *Unicode*).
- **Atenção:** a função `type()` do Python retorna sempre `<class 'numpy.ndarray'>` – **não** serve para identificar o tipo dos elementos. Use sempre o atributo ***dtype***.

### 3.2 `size`

- Quantidade total de elementos presentes no array.

### 3.3 `ndim`

- Número de dimensões do array (ex.: `1` para unidimensional, `2` para bidimensional).

### 3.4 `shape`

- Tupla que informa a quantidade de elementos em cada dimensão.
- **Exemplos:** `(3,)` para array unidimensional com 3 elementos; `(2,3)` para matriz bidimensional com 2 linhas e 3 colunas.
- Em arrays unidimensionais, o segundo valor da tupla fica em branco (ex.: `(4,)`).

## 4. Criação de Arrays

### 4.1 Usando listas

```python
import numpy as np
arr = np.array([10, 12, 14])
```

- A lista é passada como parâmetro entre colchetes `[ ]`.

### 4.2 Usando tuplas

```python
import numpy as np
arr = np.array(("Python", "Java", "PHP", "C"))
```

- A tupla é passada entre parênteses `( )`.
- A tupla é imutável (não pode ser modificada após criada), mas pode ser usada como parâmetro para `np.array()`.

> ### 4.2.1 Observação do Professor sobre `type()` vs `dtype`
> - **`type(arr)`** → sempre retorna `<class 'numpy.ndarray'>`.
> - **`arr.dtype`** → retorna o tipo real dos elementos (ex.: `int64`, `<U6`).

## 5. Exemplos Práticos Sintetizados

| ATRIBUTO | EXEMPLO 1 (inteiros) | EXEMPLO 2 (strings) |
| --- | --- | --- |
| Código | `np.array([10, 12, 14])` | `np.array(["Python", "Java", "PHP", "C"])` |
| Saída | `[10 12 14]` | `['Python' 'Java' 'PHP' 'C']` |
| `type()` | `<class 'numpy.ndarray'>` | `<class 'numpy.ndarray'>` |
| `dtype` | `int64` | `<U6` (Unicode) |
| `size` | `3` | `4` |
| `ndim` | `1` | `1` |
| `shape` | `(3,)` | `(4,)` |

## 6. Questões de Concurso (comentadas)

### 6.1 (CESPE/CEBRASPE/2025/BDMG)

**Item:** As bibliotecas NumPy, Pandas, SciPy e Statsmodels são frequentemente usadas para manipulação e análise de dados em Python, enquanto Matplotlib, Seaborn e Plotly são amplamente utilizadas para visualização de dados.

**Gabarito:** **Certo**.

**Comentário:** O item distingue corretamente as bibliotecas de manipulação/análise das de visualização.

### 6.2 (AVANÇA/SP/2025/UNITAU)

**Pergunta:** Qual biblioteca é amplamente usada para manipulação de arrays e matrizes em Python?

**Alternativas:** a) pandas; b) numpy; c) scikit-learn; d) seaborn; e) matplotlib.

**Gabarito:** **b) numpy**.

**Comentário:** NumPy é específica para arrays/matrizes; Pandas para *data frames*; Matplotlib para visualização.

### 6.3 (AMEOSC/2025/PREFEITURA DE MONDAÍ)

**Afirmativa:** Python, com sua sintaxe clara e vasto ecossistema de bibliotecas, é amplamente utilizada em desenvolvimento web (Django, Flask), ciência de dados (NumPy, Pandas) e automação de tarefas.

**Gabarito:** **Verdadeiro**.

### 6.4 (QUADRIX/2024/IBICT)

**Item:** Pandas é uma biblioteca de código aberto destinada a realizar operações em arrays multidimensionais na linguagem de programação Java.

**Gabarito:** **Errado**.

**Comentário:** Pandas utiliza NumPy internamente, mas a biblioteca principal para arrays multidimensionais é **NumPy**, e ambas são da linguagem **Python**, não Java.

### 6.5 (FUNDATEC/2024/IF SUL)

**Descrição:** Biblioteca de código aberto da linguagem Python que fornece funcionalidades para computação numérica (matrizes multidimensionais), sendo dependência do OpenCV com Python.

**Gabarito:** **d) NumPy**.

### 6.6 (FGV/2024/PREFEITURA DE CUIABÁ)

**Afirmativa:** A biblioteca NumPy é baseada na manipulação de estruturas de dados multidimensionais nas quais todos os elementos possuem o mesmo tipo.

**Gabarito:** **Verdadeiro** (corresponde à característica de homogeneidade do NDArray).

## GABARITO GERAL

| QUESTÃO | GABARITO |
| --- | --- |
| 01 | C |
| 02 | b |
| 03 | C |
| 04 | E |
| 05 | d |
| 06 | C |

---

*Material elaborado com base na aula do professor Rogério Araújo (Gran Concursos).*