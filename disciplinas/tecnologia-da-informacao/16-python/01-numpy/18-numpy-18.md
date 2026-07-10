# Anotações (Continuação - NumPy XVIII)

## 69. Produto Acumulado – `np.cumprod()`

### 69.1 Conceito fundamental

- `np.cumprod(array)` retorna o **produto acumulado** (*prefix product*) dos elementos, análogo ao `cumsum` para multiplicação.
- O primeiro elemento permanece inalterado; cada elemento seguinte é o produto de todos os elementos anteriores (incluindo o atual).
- Para arrays **multidimensionais**, sem especificar `axis`, o array é **achatado** (C-order) antes do cálculo.

**Exemplo 1D:**
```python
arrei1 = np.array([1, 2, 3, 4])
print(np.cumprod(arrei1))   # [1, 2, 6, 24]
# Cálculo: 1; 1×2=2; 2×3=6; 6×4=24
print(arrei1.cumprod())     # mesmo resultado
```

**Exemplo 2D (achatamento):**
```python
arrei2 = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])
print(np.cumprod(arrei2))
# [1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800, 39916800, 479001600]
```
- A ordem de achatamento: linha 0 (1,2,3,4), linha 1 (5,6,7,8), linha 2 (9,10,11,12).
- O último elemento é o produto total (12!? não, é 1×2×...×12 = 479001600).

> ### 69.1.1 Observação
> - O último elemento de `cumprod` é sempre igual a `np.prod` total.
> - A cada etapa, multiplica-se o valor atual pelo produto acumulado anterior.

### 69.2 Parâmetro `axis` em `cumprod`

- **`axis=0`**: produto acumulado **por coluna** (vertical). O resultado tem a mesma forma que o array original; cada coluna acumula de cima para baixo.
- **`axis=1`**: produto acumulado **por linha** (horizontal). Cada linha acumula da esquerda para a direita.

**Exemplo com array 3×4:**
```python
arrei = np.array([[1, 2, 3, 4],
                  [5, 6, 7, 8],
                  [9, 10, 11, 12]])

# axis=0 (colunas)
print(np.cumprod(arrei, axis=0))
# [[1, 2, 3, 4],
#  [5, 12, 21, 32],
#  [45, 120, 231, 384]]
# Cálculo: col0: 1; 1×5=5; 5×9=45; col1: 2; 2×6=12; 12×10=120; ...

# axis=1 (linhas)
print(np.cumprod(arrei, axis=1))
# [[1, 2, 6, 24],
#  [5, 30, 210, 1680],
#  [9, 90, 990, 11880]]
```

> ### 69.2.1 Regra prática
> - `axis=0` → acumula verticalmente (cada coluna independente).
> - `axis=1` → acumula horizontalmente (cada linha independente).

### 69.3 `cumprod` com múltiplos arrays

- Pode-se passar uma **lista ou tupla** de arrays para `np.cumprod`, utilizando `axis` para definir a direção do acúmulo.
- Os arrays são tratados como linhas de uma matriz empilhada.

```python
a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])
c = np.array([9, 10, 11, 12])

# axis=0: acumula verticalmente (primeiro a, depois a×b, depois a×b×c)
print(np.cumprod((a, b, c), axis=0))
# [[1, 2, 3, 4],
#  [5, 12, 21, 32],
#  [45, 120, 231, 384]]

# axis=1: acumula horizontalmente (cada array internamente)
print(np.cumprod([a, b, c], axis=1))
# [[1, 2, 6, 24],
#  [5, 30, 210, 1680],
#  [9, 90, 990, 11880]]
```

| PARÂMETRO | COMPORTAMENTO |
| --- | --- |
| `axis=0` | Multiplica acumulativamente entre os arrays (primeiro array, depois array1 × array2, etc.) |
| `axis=1` | Calcula o produto acumulado dentro de cada array individual (horizontal) |

## 70. *Broadcasting* – Operações entre Arrays de Diferentes Dimensões

### 70.1 Conceito

- ***Broadcasting*** é o mecanismo do NumPy que permite realizar operações matemáticas **elemento a elemento** entre arrays de **formas diferentes**, ajustando automaticamente as dimensões sem a necessidade de copiar ou replicar dados manualmente.
- O NumPy "estica" os arrays menores para que tenham a mesma forma do maior, desde que as regras de compatibilidade sejam atendidas.

### 70.2 Regras de compatibilidade

Dois arrays são compatíveis para *broadcasting* quando:
1. Eles têm o mesmo número de dimensões, **ou** uma das dimensões é 1.
2. Para cada dimensão (começando da última para a primeira), os tamanhos são iguais ou um deles é 1.

> ### 70.2.1 Exemplos de sucesso

**Exemplo 1 – Escalar + array 2D:**
```python
a = np.array([[1, 2, 3], [4, 5, 6]])   # shape (2,3)
b = 10                                  # escalar (tratado como (1,1))
print(a + b)   # [[11,12,13], [14,15,16]]
# 10 é transmitido para todas as posições
```

**Exemplo 2 – Array 1D + array 2D (linha compatível):**
```python
a = np.array([[1, 2, 3], [4, 5, 6]])   # shape (2,3)
b = np.array([10, 20, 30])             # shape (3,)
print(a + b)   # [[11,22,33], [14,25,36]]
# b é transmitido para cada linha (linha0 + b, linha1 + b)
```

> ### 70.2.2 Exemplo de erro (incompatibilidade)

```python
a = np.array([[1, 2, 3], [4, 5, 6]])   # shape (2,3)
b = np.array([10, 20])                 # shape (2,)
# Tentativa: (2,3) vs (2,) → falha porque a última dimensão de a é 3, b tem tamanho 2 (não são iguais e nenhum é 1)
# ValueError: operands could not be broadcast together with shapes (2,3) (2,)
```

- Para funcionar, `b` deveria ter shape `(2,1)` (duas linhas, uma coluna) ou `(3,)` (como no exemplo anterior) ou `(1,3)`.

> ### 70.2.3 Dica de prova (Questão CESPE/2023)
> - O item **"A biblioteca numpy permite realizar operações matemáticas entre arrays de diferentes dimensões usando o mecanismo de broadcast"** está **CERTO**. É uma afirmação verdadeira e frequentemente cobrada.

## 71. Funções Estatísticas no NumPy

### 71.1 Principais funções e métodos

| FUNÇÃO | DESCRIÇÃO | MÉTODO EQUIVALENTE |
| --- | --- | --- |
| `np.mean(array)` | Média aritmética | `array.mean()` |
| `np.median(array)` | Mediana (valor central) | – (não tem método direto) |
| `np.var(array)` | Variância | `array.var()` |
| `np.std(array)` | Desvio padrão | `array.std()` |
| `np.percentile(array, q)` | Percentil `q` (0 a 100) | – |

### 71.2 Média (`mean`)

- Soma de todos os elementos dividida pelo número de elementos.
- Aceita `axis` para cálculo por linha ou coluna.

**Exemplo:**
```python
velocidades = np.array([99, 86, 87, 88, 111, 86, 103, 87, 94, 78, 77, 85, 86])
print(np.mean(velocidades))   # 89.769...
print(velocidades.mean())     # mesmo resultado
```

**Com `axis`:**
```python
arrei = np.array([[18,2,17,4], [2,3,15,1], [9,2,10,5]])
print(arrei.mean(axis=0))   # [9.67, 2.33, 14.0, 3.33] (média por coluna)
print(arrei.mean(axis=1))   # [10.25, 5.25, 6.5] (média por linha)
```

### 71.3 Mediana (`median`)

- Valor que separa a metade superior da metade inferior dos dados.
- Para conjunto com número **ímpar** de elementos: elemento central após ordenação.
- Para número **par**: média dos dois elementos centrais.

**Exemplo 1D:**
```python
velocidades = np.array([99, 86, 87, 88, 111, 86, 103, 87, 94, 78, 77, 85, 86])
print(np.sort(velocidades))   # [77,78,85,86,86,86,87,87,88,94,99,103,111]
print(np.median(velocidades)) # 87.0 (elemento central, posição 7)
```

**Exemplo 2D (com `axis`):**
```python
arrei = np.array([[18,2,17,4], [2,3,15,1], [9,2,10,5]])
print(np.median(arrei, axis=0))   # [9., 2., 15., 4.] (mediana por coluna)
print(np.median(arrei, axis=1))   # [10.5, 2.5, 7.] (mediana por linha)
```

> ### 71.3.1 Mediana total vs. por eixo
> - Sem `axis`: mediana de **todos os elementos achatados**.
> - `axis=0`: mediana de cada coluna.
> - `axis=1`: mediana de cada linha.

### 71.4 Variância (`var`) e Desvio Padrão (`std`)

- **Variância**: média dos quadrados dos desvios em relação à média. Mede a dispersão dos dados.
- **Desvio padrão**: raiz quadrada da variância. Está na mesma unidade dos dados originais.

```python
idades = np.array([5,31,43,48,50,41,7,11,15,39,80,82,32,2,8,6,25,36,27,61,31])
print(np.var(idades))   # 514.331...
print(np.std(idades))   # 22.678... (sqrt da variância)
```

### 71.5 Percentil (`percentile`)

- Valor abaixo do qual uma determinada porcentagem dos dados se encontra.
- `np.percentile(array, q)` onde `q` é o percentual (0 a 100).
- **Percentil 50** é equivalente à **mediana**.

```python
print(np.percentile(idades, 25))   # 11.0
print(np.percentile(idades, 50))   # 31.0 (igual à mediana)
print(np.percentile(idades, 75))   # 43.0
```

## 72. Questões de Concurso Comentadas

### 72.1 (CESPE/CEBRASPE/2023/DATAPREV) – *Broadcasting*

**Item:** A biblioteca numpy permite realizar operações matemáticas entre arrays de diferentes dimensões usando o mecanismo de broadcast.

**Gabarito: Certo**.

**Comentário:** Afirmação correta. *Broadcasting* é um recurso fundamental do NumPy para operações entre arrays de formas diferentes.

### 72.2 (CESPE/CEBRASPE/2023/DATAPREV) – Métodos estatísticos

**Item:** Se um conjunto de dados for armazenado em um array numpy, então, por meio dos seus métodos pré-definidos, será possível obter dados de resumo estatístico desse conjunto de dados.

**Gabarito: Certo**.

**Comentário:** Métodos como `mean()`, `var()`, `std()` etc. estão disponíveis em arrays NumPy para análise estatística.

### 72.3 (CESPE/CEBRASPE/2021/BANESE) – Mediana com `axis=0`

**Código:**
```python
y = numpy.array([[1, 2], [2, 2], [3, 3]])
numpy.median(y, axis=0)
```

**Item afirma que o código retorna as medianas das colunas: {1,2,3} e {2,2,3}.**

**Cálculo:**
- Coluna 0: valores [1,2,3] → mediana = 2.
- Coluna 1: valores [2,2,3] → mediana = 2.
- Resultado: `[2., 2.]`

**Gabarito: Certo** (embora a descrição das medianas como "primeira coluna {1,2,3} e segunda {2,2,3}" esteja confusa, o resultado é `[2,2]`, e a afirmativa foi considerada verdadeira pela banca).

### 72.4 (CESPE/CEBRASPE/2022/TRT 8ª REGIÃO) – Métodos corretos

**Análise das alternativas:**

| ALTERNATIVA | AFIRMAÇÃO | CORREÇÃO |
| --- | --- | --- |
| a) | `deviation()` encontra o desvio padrão | **Errado** – o método é `std()` |
| b) | `percentile()` encontra o percentil | **Correto** – `np.percentile()` |
| c) | `half()` calcula a média | **Errado** – o método é `mean()` |
| d) | `mean()` encontra a mediana | **Errado** – `mean()` é média; mediana é `median()` |
| e) | `type()` retorna o tipo de dados do array | **Errado** – usa-se `dtype`, não `type()` (que retorna `numpy.ndarray`) |

**Gabarito: b**.

## GABARITO DAS QUESTÕES DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2023/DATAPREV – broadcast) | C |
| 02 (CESPE/2023/DATAPREV – estatísticas) | C |
| 03 (CESPE/2021/BANESE) | C |
| 04 (CESPE/2022/TRT 8ª) | b |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XVIII" (professor Rogério Araújo, Gran Concursos).*