# Anotações (Continuação - NumPy XVII)

## 65. Diferenças Discretas (`np.diff`) em Arrays 2D e Parâmetro `axis`

### 65.1 Comportamento padrão (`axis=1` – diferença por linha)

- Para arrays 2D, `np.diff(arrei)` (sem `axis`) aplica a diferença discreta **ao longo das linhas** (eixo 1 – colunas).
- O resultado tem o mesmo número de linhas, mas cada linha perde um elemento (N elementos → N-1 diferenças por linha).

**Exemplo:**
```python
arrei = np.array([[18, 2, 17, 4],
                  [2, 3, 15, 1]])
print(np.diff(arrei))
# [[-16, 15, -13],
#  [ 1, 12, -14]]
# Cálculo: linha0: 2-18=-16, 17-2=15, 4-17=-13
#          linha1: 3-2=1, 15-3=12, 1-15=-14
```

### 65.2 `axis=0` – diferença entre linhas (coluna a coluna)

- `np.diff(arrei, axis=0)` calcula a diferença **entre elementos de mesma coluna** em linhas consecutivas.
- O resultado perde uma linha (para um array com `n` linhas, o resultado tem `n-1` linhas).

**Exemplo:**
```python
arrei = np.array([[18, 2, 17, 4],
                  [4, 3, 15, 1]])
print(np.diff(arrei, axis=0))
# [[-14, 1, -2, -3]]
# Cálculo: col0: 4-18=-14; col1: 3-2=1; col2: 15-17=-2; col3: 1-4=-3
```

### 65.3 Combinação de `n` (profundidade) com array 2D

- O parâmetro `n` aplica a diferença discreta **recursivamente** em cada linha separadamente (para o padrão `axis=1`), mantendo a estrutura bidimensional.

**Exemplo com `n=2`:**
```python
arrei = np.array([[18, 2, 17, 4], [2, 3, 15, 1]])
print(np.diff(arrei, n=2))
# [[31, -28],
#  [11, -26]]
```

| NÍVEL | LINHA 0 | LINHA 1 |
| --- | --- | --- |
| Original | [18,2,17,4] | [2,3,15,1] |
| `n=1` | [-16, 15, -13] | [1, 12, -14] |
| `n=2` | [31, -28] | [11, -26] |

> ### 65.3.1 Equivalência de eixos
> - `np.diff(arrei)` é equivalente a `np.diff(arrei, axis=1)` (diferença por linha).
> - `np.diff(arrei, axis=0)` calcula diferença **por coluna** (entre linhas).

## 66. Reforço sobre Somatórios

### 66.1 Diferença entre `np.add()` e `np.sum()` (consolidação)

| FUNÇÃO | COMO PASSAR OS ARRAYS | COMPORTAMENTO | RESULTADO |
| --- | --- | --- | --- |
| `np.add(a, b)` | Diretamente como argumentos (`a, b`) | Soma elemento a elemento | Array com mesma forma |
| `np.sum([a, b])` | Dentro de uma lista ou tupla (`[a, b]`) | Soma total de todos os elementos | Escalar |
| `np.sum([a, b], axis=0)` | Lista + `axis=0` | Soma elemento a elemento (como `add`) | Array com mesma forma |
| `np.sum([a, b], axis=1)` | Lista + `axis=1` | Soma os elementos de cada array individualmente (total por array) | Array 1D com um elemento por array |

**Exemplo (arrays 1D):**
```python
a = np.array([18, 2, 17, 4])
b = np.array([2, 7, 5, 11])
print(np.add(a, b))           # [20, 9, 22, 15]
print(np.sum([a, b]))         # 66
print(np.sum([a, b], axis=0)) # [20, 9, 22, 15]
print(np.sum([a, b], axis=1)) # [41, 25]  (18+2+17+4=41; 2+7+5+11=25)
```

### 66.2 Método `.sum()` em arrays 1D – cuidado com `axis`

- Para arrays **1D**, `array.sum(axis=0)` **não gera erro** – simplesmente soma todos os elementos (único eixo existente).
- `array.sum(axis=1)` gera erro porque não há eixo 1.

```python
arrei = np.array([18, 2, 17, 4])
print(arrei.sum())      # 41
print(arrei.sum(axis=0)) # 41  (não erro!)
# print(arrei.sum(axis=1)) # IndexError: axis 1 is out of bounds
```

> ### 66.2.1 Observação do professor
> - Em arrays 1D, o eixo 0 é o único eixo; `axis=0` realiza a soma de todos os elementos (equivalente a `sum()` sem eixo).
> - O erro só ocorre para `axis` maior ou igual ao número de dimensões.

## 67. Produtos: `np.prod()` e `np.cumprod()`

### 67.1 `np.prod()` – Produto de elementos

- `np.prod(array)` retorna o **produto de todos os elementos** do array (análogo a `sum` para multiplicação).
- Também disponível como método `array.prod()`.
- Aceita `axis` para reduzir ao longo de um eixo.

**Exemplo 1D:**
```python
arrei = np.array([1, 2, 3, 4])
print(np.prod(arrei))   # 24 (1×2×3×4)
print(arrei.prod())     # 24
```

**Exemplo 2D:**
```python
arrei = np.array([[1, 2, 3, 4],
                  [5, 6, 7, 8]])
print(np.prod(arrei))           # 40320 (1×2×...×8)
print(np.prod(arrei, axis=0))   # [5, 12, 21, 32] (multiplicação por coluna)
print(np.prod(arrei, axis=1))   # [24, 1680] (multiplicação por linha)
```

| OPERAÇÃO | RESULTADO | CÁLCULO |
| --- | --- | --- |
| `prod(axis=0)` | `[5, 12, 21, 32]` | 1×5, 2×6, 3×7, 4×8 |
| `prod(axis=1)` | `[24, 1680]` | 1×2×3×4=24; 5×6×7×8=1680 |

### 67.2 `np.prod()` com múltiplos arrays

- Passa-se uma **lista ou tupla** de arrays como primeiro argumento.
- Usa-se `axis` para controlar a direção:
  - `axis=0`: multiplica elemento a elemento (arrays devem ter mesma forma).
  - `axis=1`: multiplica cada array individualmente (total por array).

```python
a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])
print(np.prod((a, b), axis=0))   # [5, 12, 21, 32] (elemento a elemento)
print(np.prod([a, b], axis=1))   # [24, 1680] (1×2×3×4 e 5×6×7×8)
```

### 67.3 `np.cumprod()` – Produto acumulado

- Retorna o **produto acumulado** (prefix product) – análogo ao `cumsum` para multiplicação.
- O primeiro elemento permanece; cada elemento seguinte é o produto de todos os anteriores (incluindo o atual).
- Para arrays 1D, retorna um array do mesmo tamanho.

**Exemplo 1D:**
```python
arrei = np.array([1, 2, 3, 4])
print(np.cumprod(arrei))   # [1, 2, 6, 24]
# Cálculo: 1; 1×2=2; 2×3=6; 6×4=24
```

**Exemplo 2D (achatamento padrão):**
```python
arrei2 = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(np.cumprod(arrei2))   # [1, 2, 6, 24, 120, 720, 5040, 40320]
# (1; 1×2=2; 2×3=6; 6×4=24; 24×5=120; ...)
```

> ### 67.3.1 Observação
> - O último elemento de `cumprod` é igual ao `prod` total.
> - `cumprod` pode receber `axis` para calcular acumulado ao longo de um eixo específico (ex.: `axis=0` para colunas, `axis=1` para linhas). O professor não detalhou no material, mas é extensão natural.

## 68. Tabela Comparativa – Operações de Agregação

| FUNÇÃO | AGREGADA (REDUZ) | ACUMULADA (MESMO TAMANHO) |
| --- | --- | --- |
| Soma | `np.sum()` / `array.sum()` | `np.cumsum()` |
| Produto | `np.prod()` / `array.prod()` | `np.cumprod()` |
| Diferença | `np.diff()` (reduz tamanho em 1 por rodada) | Não se aplica |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XVII" (professor Rogério Araújo, Gran Concursos).*