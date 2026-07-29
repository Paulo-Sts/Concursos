# Anotações (Continuação - NumPy XIV)

## 56. Ordenação de Elementos em Arrays

### 56.1 Método `.sort()` – ordenação *in-place*

- O método `array.sort()` ordena os elementos **diretamente no array original** (modifica o array, não retorna uma cópia).
- A ordenação padrão é **crescente** (alfabética para strings, numérica para números).
- Para arrays multidimensionais, `sort()` ordena **ao longo do último eixo** (padrão `axis=-1`), ou seja, **cada linha é ordenada individualmente**.

**Exemplo 1 (1D – strings e números):**
```python
arrei1 = np.array(["Python", "Java", "PHP", "C"])
arrei1.sort()
print(arrei1)   # ['C' 'Java' 'PHP' 'Python']

arrei2 = np.array([100, 50, 65, 82, 23])
arrei2.sort()
print(arrei2)   # [23 50 65 82 100]
```

**Exemplo 2 (2D – ordenação padrão por linha – axis=1):**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
arrei.sort()   # equivalente a sort(axis=1)
print(arrei)
# [[ 2  4 17 18]
#  [ 1  3 15 16]]
```

> ### 56.1.1 Comportamento para 2D sem especificar eixo
> - O método `sort()` sem parâmetros em um array 2D ordena **cada linha individualmente** (eixo 1), não o array inteiro como uma sequência única.

### 56.2 Parâmetro `axis` no método `sort()`

- **`axis=0`**: ordena ao longo das linhas (ou seja, ordena **cada coluna** individualmente, de cima para baixo).
- **`axis=1`**: ordena ao longo das colunas (cada linha individualmente).

**Exemplo 3 – ordenação por coluna (`axis=0`):**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
arrei.sort(axis=0)
print(arrei)
# [[16  2 15  1]   ← menores valores de cada coluna na primeira linha
#  [18  3 17  4]]  ← maiores valores de cada coluna na segunda linha
```

**Exemplo 4 – efeito cumulativo (ordenar primeiro por coluna, depois por linha):**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
arrei.sort(axis=0)   # ordena por coluna
arrei.sort(axis=1)   # depois ordena cada linha resultante
print(arrei)
# [[ 1  2 15 16]
#  [ 3  4 17 18]]
```

> ### 56.2.1 Entendendo o Exemplo 4
> 1. Após `sort(axis=0)`, o array torna-se:
>    `[[16, 2, 15, 1], [18, 3, 17, 4]]`
> 2. Após `sort(axis=1)`, cada linha é ordenada internamente:
>    - Linha 0: `[1, 2, 15, 16]`
>    - Linha 1: `[3, 4, 17, 18]`

### 56.3 Ordenação decrescente

- O método `sort()` **não possui parâmetro para ordem decrescente**.
- Estratégia: ordenar de forma crescente e depois **inverter o array** com fatiamento `[::-1]`.

**Exemplo:**
```python
arrei2 = np.array([100, 50, 65, 82, 23])
arrei2.sort()                # [23 50 65 82 100]
decrescente = arrei2[::-1]   # [100 82 65 50 23]
print(decrescente)
```

### 56.4 `np.sort()` – retornando uma cópia ordenada

- A função `np.sort(array)` retorna um **novo array ordenado** (cópia), **sem modificar o array original**.
- Diferente do método `.sort()`, que altera o array original.

**Exemplo 1 (1D):**
```python
arrei1 = np.array(["Python", "Java", "PHP", "C"])
print(np.sort(arrei1))   # ['C' 'Java' 'PHP' 'Python']
print(arrei1)            # original permanece ['Python' 'Java' 'PHP' 'C']
```

**Exemplo 2 (2D – ordenação por linha – padrão `axis=-1`):**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
copia_ordenada = np.sort(arrei)   # axis=1 por padrão
print(copia_ordenada)
# [[ 2  4 17 18]
#  [ 1  3 15 16]]
print(arrei)   # original inalterado
```

**Exemplo 3 – ordenação por coluna com `np.sort` e `axis=0`:**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
copia_coluna = np.sort(arrei, axis=0)
print(copia_coluna)
# [[16  2 15  1]
#  [18  3 17  4]]
```

**Exemplo 4 – encadeamento de ordenações com `np.sort` (cópias sucessivas):**
```python
arrei = np.array([[18, 2, 17, 4], [16, 3, 15, 1]])
resultado = np.sort(np.sort(arrei, axis=0), axis=1)
print(resultado)
# [[ 1  2 15 16]
#  [ 3  4 17 18]]
```
- O `np.sort` interno ordena por coluna (axis=0) → retorna uma cópia.
- O `np.sort` externo ordena cada linha (axis=1) dessa cópia → resultado final.

> ### 56.4.1 Comparação: `.sort()` vs `np.sort()`
> | MÉTODO/FUNÇÃO | MODIFICA O ORIGINAL? | RETORNO | USO TÍPICO |
> | --- | --- | --- | --- |
> | `array.sort()` | **Sim** (in-place) | `None` (altera o próprio array) | Quando não há necessidade de preservar o original |
> | `np.sort(array)` | **Não** | Novo array ordenado | Quando se quer manter o original inalterado |

## 57. Operações Aritméticas em NumPy

### 57.1 Princípio fundamental

- Operadores aritméticos (+, -, *, /, %, **) em arrays NumPy atuam **elemento a elemento** (*element-wise*).
- Os arrays devem ter **shapes compatíveis** (mesmo shape ou compatíveis por *broadcasting*).

### 57.2 Operadores e funções equivalentes

| OPERAÇÃO | OPERADOR | FUNÇÃO EQUIVALENTE |
| --- | --- | --- |
| Soma | `a + b` | `np.add(a, b)` |
| Subtração | `a - b` | `np.subtract(a, b)` |
| Multiplicação | `a * b` | `np.multiply(a, b)` |
| Divisão | `a / b` | `np.divide(a, b)` |
| Resto da divisão (módulo) | `a % b` | `np.mod(a, b)` |
| Potência | `a ** b` | `np.power(a, b)` |

**Exemplo (conceitual):**
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
print(a + b)   # [5, 7, 9]
print(a * b)   # [4, 10, 18]
print(a ** 2)  # [1, 4, 9]
```

> ### 57.2.1 Observação do professor
> - Não há questões sobre ordenação e operações aritméticas neste momento, mas o professor ressalta que as bancas têm gradualmente aumentado a cobrança desses tópicos, por serem relativamente novos em concursos.
> - Operações aritméticas elemento a elemento são **fundamentais** para análise de dados e serão utilizadas em conjunto com outras bibliotecas (ex.: Pandas).

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XIV" (professor Rogério Araújo, Gran Concursos).*