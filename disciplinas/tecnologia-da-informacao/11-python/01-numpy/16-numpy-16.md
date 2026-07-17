# Anotações (Continuação - NumPy XVI)

## 61. Método `.sum()` do Array vs. Função `np.sum()`

### 61.1 Sintaxe e comportamento

- O **método** `array.sum()` aplica-se diretamente a um array NumPy e retorna a soma dos elementos.
- A **função** `np.sum()` pode receber um array ou uma lista/tupla de arrays.
- Ambos aceitam o parâmetro `axis` para especificar o eixo de soma.

**Exemplo 1 – método `sum()` em array 1D:**
```python
arrei = np.array([18, 2, 17, 4])
print(arrei.sum())        # 41 (soma total)
print(arrei.sum(axis=0))  # 41 (mesmo resultado, pois só há um eixo)
# print(arrei.sum(axis=1))  # ERRO: array 1D não tem eixo 1
```

> ### 61.1.1 Atenção
> - Em arrays **1D**, `axis=0` refere-se ao único eixo existente. `axis=1` não existe e gera erro.
> - O resultado de `sum()` sem `axis` ou com `axis=0` em um array 1D é o mesmo: a soma de todos os elementos.

### 61.2 Método `sum()` em arrays 2D

**Array base:**
```python
arrei = np.array([[18, 2, 17, 4], [2, 3, 15, 1]])  # shape (2,4)
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei.sum()` | `62` | Soma de todos os elementos (18+2+17+4+2+3+15+1) |
| `arrei.sum(axis=0)` | `[20, 5, 32, 5]` | Soma de cada coluna (18+2, 2+3, 17+15, 4+1) |
| `arrei.sum(axis=1)` | `[41, 21]` | Soma de cada linha (18+2+17+4=41; 2+3+15+1=21) |

> ### 61.2.1 Relação entre `np.sum()` e método `sum()`
> - `np.sum(arrei)` ≡ `arrei.sum()`
> - `np.sum(arrei, axis=0)` ≡ `arrei.sum(axis=0)`
> - Para múltiplos arrays, `np.sum([a1, a2], axis=0)` soma elemento a elemento – não há equivalente direto como método de um único array.

## 62. Somatório Acumulado – `np.cumsum()`

### 62.1 Conceito

- `np.cumsum(array)` (ou `array.cumsum()`) retorna um array onde cada elemento é a **soma acumulada** (*prefix sum*) dos elementos do array original.
- O primeiro elemento permanece igual; cada elemento seguinte é a soma de todos os elementos anteriores (inclusive o atual).

**Exemplo 1D:**
```python
arrei = np.array([18, 2, 17, 4])
print(np.cumsum(arrei))   # [18, 20, 37, 41]
# Cálculo: 18; 18+2=20; 20+17=37; 37+4=41
```

### 62.2 `cumsum` em arrays 2D (achatamento)

- Quando aplicado a um array multidimensional sem especificar `axis`, `cumsum` achata o array e retorna o acumulado em 1D.

**Exemplo com array 2×2:**
```python
data = np.array([[1, 2], [3, 4], [5, 6]])
print(data.cumsum())   # [1, 3, 6, 10, 15, 21]
# Ordem de achatamento: C-order (linha por linha) → 1,2,3,4,5,6
# Acumulado: 1; 1+2=3; 3+3=6; 6+4=10; 10+5=15; 15+6=21
```

> ### 62.2.1 Comportamento
> - O array de saída tem o **mesmo número de elementos** que o array original (diferente de `sum`, que reduz).
> - O último elemento do `cumsum` é igual ao `sum` total.

## 63. Diferenças Discretas – `np.diff()`

### 63.1 Conceito fundamental

- `np.diff(array)` calcula a **diferença discreta** entre elementos consecutivos.
- Para cada par de elementos `(a[i], a[i+1])`, retorna `a[i+1] - a[i]`.
- O resultado tem **um elemento a menos** que o array original (para `n=1`).

**Exemplo básico:**
```python
arrei = np.array([18, 2, 17, 4])
print(np.diff(arrei))   # [-16, 15, -13]
# Cálculo: 2-18 = -16; 17-2 = 15; 4-17 = -13
```

### 63.2 Parâmetro `n` – múltiplas rodadas de diferença

- O parâmetro `n` (opcional) especifica quantas vezes a operação de diferença é aplicada **recursivamente**.
- A cada rodada, o tamanho do array diminui em 1.

**Exemplo com `n=2`:**
```python
arrei = np.array([18, 2, 17, 4])
print(np.diff(arrei, n=2))   # [31, -28]
```
- 1ª rodada: `[-16, 15, -13]`
- 2ª rodada (sobre o resultado): `15 - (-16) = 31`; `-13 - 15 = -28`

**Exemplo com `n=3`:**
```python
print(np.diff(arrei, n=3))   # [-59]
```
- 1ª rodada: `[-16, 15, -13]`
- 2ª rodada: `[31, -28]`
- 3ª rodada: `-28 - 31 = -59`

> ### 63.2.1 Relação com tamanho do array
> - Se o array original tem `N` elementos, `np.diff(arr, n=k)` retorna um array com `N - k` elementos (para `k ≤ N-1`).
> - Se `k = N-1`, o resultado é um array de um único elemento.

## 64. Questão de Concurso Comentada

### 64.1 (INSTITUTO CONSULPLAN/TJ-RO/ANALISTA JUDICIÁRIO/MATEMÁTICO/2025)

**Código:**
```python
import numpy as np
data = np.array([[1, 2], [3, 4], [5, 6]])
result = data.sum(axis=0)
```

**O que o comando `data.sum(axis=0)` faz?**

**Alternativas:**
a) Soma todos os seus elementos.  
b) Soma os elementos de cada linha.  
c) Soma os elementos de cada coluna.  
d) Retorna a soma acumulada de todos os seus elementos.  
e) Retorna a soma dos elementos ao longo da sua diagonal principal.

**Gabarito: c) Soma os elementos de cada coluna.**

**Análise:**
- O array `data` tem shape `(3,2)`:
  ```
  [[1, 2],
   [3, 4],
   [5, 6]]
  ```
- `axis=0` refere-se ao primeiro eixo (linhas). Somar ao longo do eixo 0 significa **somar os elementos de cada coluna** (verticalmente).
- Resultado: `[1+3+5, 2+4+6] = [9, 12]`.

**Distinção dos conceitos:**
- `data.sum()` (sem axis) → soma todos os elementos (21) – alternativa **a**.
- `data.sum(axis=1)` → soma cada linha `[3, 7, 11]` – alternativa **b**.
- `data.cumsum()` → soma acumulada `[1, 3, 6, 10, 15, 21]` – alternativa **d**.
- Diagonal principal (elementos `[1, 4]` ou `[1,4]`? Não é o caso) – alternativa **e** não se aplica.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (INSTITUTO CONSULPLAN/TJ-RO/2025) | c |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XVI" (professor Rogério Araújo, Gran Concursos).*