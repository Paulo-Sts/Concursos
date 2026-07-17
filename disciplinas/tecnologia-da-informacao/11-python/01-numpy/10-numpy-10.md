# Anotações (Continuação - NumPy X)

## 41. Visualizações (*Views*) e Cópias – Aprofundamento

### 41.1 Conceitos fundamentais

| CONCEITO | MÉTODO | COMPARTILHA MEMÓRIA? | ALTERAÇÕES REFLETEM? |
| --- | --- | --- | --- |
| **Cópia** (*deep copy*) | `.copy()` | Não | Independentes (não afetam o original) |
| **Visualização** (*view* / *shallow copy*) | `.view()` | Sim | Alterações em um refletem no outro |
| **Referência direta** | atribuição simples (`y = arrei`) | Sim (mesmo objeto) | Refletem (é o mesmo objeto) |

> ### 41.1.1 Distinção entre view e referência direta
> - **Referência direta (`y = arrei`):** `y` é **o mesmo objeto** que `arrei`. Compartilham o mesmo identificador (`id`). Qualquer alteração em um é automaticamente uma alteração no outro.
> - ***View* (`x = arrei.view()`):** `x` é um **objeto diferente** (tem `id` próprio), mas aponta para o **mesmo buffer de dados** que `arrei`. Alterações nos dados são refletidas, mas os objetos são distintos.

### 41.2 Exemplo prático com `.view()`

```python
import numpy as np
arrei = np.array([1, 2, 3, 4])
x = arrei.view()      # view: objeto diferente, mesmo buffer
y = arrei             # referência direta: mesmo objeto
arrei[0] = 15

print(arrei)   # [15, 2, 3, 4]
print(x)       # [15, 2, 3, 4] → reflete a alteração
print(y)       # [15, 2, 3, 4] → reflete a alteração

print(id(arrei))   # ex.: 23037606493616
print(id(x))       # ex.: 23037606490256 → diferente do original
print(id(y))       # ex.: 23037606493616 → igual ao original
```

> ### 41.2.1 Interpretação
> - `x` (view) tem `id` diferente, mas os dados são compartilhados.
> - `y` (referência direta) tem o **mesmo `id`** que `arrei` – é o mesmo objeto.
> - **Vantagem da view:** mais eficiente em memória para grandes conjuntos, pois não duplica os dados.

### 41.3 Atributo `.base`

- Indica se um array é proprietário dos seus dados ou apenas uma visualização.
- **Retorna:**
  - `None` → o array é **proprietário** dos dados (array original, cópia independente ou referência direta ao original).
  - **Referência ao array original** → o array é uma **view** (ou view de view), não proprietário.

**Exemplo:**
```python
arrei = np.array([1, 2, 3, 4])
a = arrei.copy()   # cópia independente
b = arrei          # referência direta
c = arrei.view()   # view
d = b.view()       # view de uma referência (que aponta para original)

print(arrei.base)   # None (original)
print(a.base)       # None (cópia independente)
print(b.base)       # None (referência direta ao original)
print(c.base)       # [1 2 3 4] → array original (não None)
print(d.base)       # [1 2 3 4] → array original (não None)
```

| TIPO DE ARRAY | `.base` RETORNA |
| --- | --- |
| Array original | `None` |
| Cópia (`.copy()`) | `None` |
| Referência direta (`y = arrei`) | `None` |
| View (`.view()`) | Array original (não `None`) |
| View de view | Array original (não `None`) |

> ### 41.3.1 Regra prática
> - Se `.base` for `None` → o array **é dono** dos seus dados (pode ser original, cópia ou referência direta).
> - Se `.base` não for `None` → o array é uma **view** e compartilha dados com o array retornado.

## 42. Atributo `shape` – Revisão com Novos Exemplos

- `shape` retorna uma **tupla de inteiros** com o tamanho de cada eixo (dimensão).
- `ndim` é o número de elementos da tupla `shape` (número de dimensões).

**Exemplos comparativos:**

| CÓDIGO | `ndim` | `shape` | EXPLICAÇÃO |
| --- | --- | --- | --- |
| `np.array([10, 12, 14])` | 1 | `(3,)` | 1D com 3 elementos |
| `np.array(["Python", "Java", "PHP", "C"])` | 1 | `(4,)` | 1D com 4 elementos |
| `np.array([[1,2,3,4], [15,16,17,18]])` | 2 | `(2, 4)` | 2 linhas × 4 colunas |

## 43. Parâmetro `ndmin` na Criação de Arrays

- **`ndmin`** (parâmetro de `np.array()`) define o **número mínimo de dimensões** do array criado.
- O NumPy **adiciona dimensões extras** (com tamanho 1) no início da tupla `shape` para atender ao mínimo solicitado.
- **Não confundir com `ndim`:** `ndim` é um atributo que informa quantas dimensões o array **tem**; `ndmin` é um parâmetro de criação que **força** uma quantidade mínima.

**Exemplo com lista de 15 elementos:**
```python
lista = [3, 49, 14, 89, 29, 52, 41, 98, 74, 73, 82, 29, 76, 98, 38]
arrei1 = np.array(lista)                # sem ndmin
print(arrei1.ndim, arrei1.shape)       # 1 (15,)

arrei2 = np.array(lista, ndmin=3)      # força no mínimo 3 dimensões
print(arrei2.ndim, arrei2.shape)       # 3 (1, 1, 15)
```

- O total de elementos (`.size`) permanece **15**.
- O `shape` `(1, 1, 15)` significa: 1 elemento na 1ª dimensão, 1 na 2ª, 15 na 3ª.

**Exemplo com lista já 2D:**
```python
lista = [[3, 49, 14, 89, 29],
         [52, 41, 98, 74, 73],
         [82, 29, 76, 98, 38]]
arrei1 = np.array(lista)                # shape (3, 5), ndim=2
arrei2 = np.array(lista, ndmin=3)       # shape (1, 3, 5), ndim=3
```

> ### 43.1 Observação
> - `ndmin` adiciona dimensões **à esquerda** (no início da tupla `shape`).
> - É útil para padronizar dimensionalidade em operações que exigem arrays com determinado número de eixos.

## 44. Método `reshape()`

### 44.1 Conceito

- **`reshape()`** altera a **forma** (dimensões) de um array **sem modificar os dados** subjacentes.
- O número total de elementos **deve permanecer o mesmo** (produto dos novos valores de `shape` deve ser igual a `.size`).
- Pode ser chamado como:
  - **Método do array:** `array.reshape(novas_dimensoes)`
  - **Função do NumPy:** `np.reshape(array, novas_dimensoes)`

### 44.2 Exemplo 1 – 1D para 2D

```python
lista = [3, 49, 14, 89, 29, 52, 41, 98, 74, 73, 82, 29, 76, 98, 38]  # 15 elementos
arrei1 = np.array(lista)                     # shape (15,)
arrei2 = arrei1.reshape(3, 5)               # shape (3, 5) – 3 linhas × 5 colunas
print(arrei2.shape)  # (3, 5)
print(arrei2.size)   # 15 (inalterado)
```

### 44.3 Exemplo 2 – 1D para 3D (12 elementos)

```python
lista = [3, 49, 14, 89, 29, 52, 41, 98, 74, 73, 82, 29]  # 12 elementos
arrei1 = np.array(lista)                     # shape (12,)
arrei2 = arrei1.reshape(2, 3, 2)             # shape (2, 3, 2)
# 2 blocos × 3 linhas por bloco × 2 colunas = 12 elementos
print(arrei2)
# [[[ 3 49]
#   [14 89]
#   [29 52]]
#  [[41 98]
#   [74 73]
#   [82 29]]]
```

### 44.4 Sintaxes equivalentes

```python
y = x.reshape(4, 5)          # método do array
y = np.reshape(x, (4, 5))    # função do NumPy (forma como tupla)
```

> ### 44.4.1 Atenção
> - Em `np.reshape()`, as novas dimensões devem ser passadas como uma **tupla** (parênteses).
> - Em `array.reshape()`, pode-se passar os valores separados por vírgula (`reshape(4,5)`) ou uma tupla (`reshape((4,5))`).

## 45. Questões de Concurso Comentadas

### 45.1 (FGV/2024/CVM/ANALISTA CVM – PERFIL 7/CIÊNCIA DE DADOS)

**Código:**
```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
newarr = arr.reshape(2, 3, 2)
print(newarr)
```

**Alternativa correta:** **c)** `[[[1 2] [3 4] [5 6]] [[7 8] [9 10] [11 12]]]`

**Análise:**
- Array original tem 12 elementos.
- `reshape(2, 3, 2)` → 2 blocos × 3 linhas por bloco × 2 colunas.
- A ordem de preenchimento é **linha a linha** (C-order), respeitando a sequência dos elementos originais.
- O primeiro bloco recebe os primeiros 6 elementos (1 a 6) organizados em 3 linhas de 2 colunas.
- O segundo bloco recebe os 6 elementos restantes (7 a 12).

### 45.2 (CESGRANRIO/2024/IPEA/TÉCNICO DE PLANEJAMENTO E PESQUISA/CIÊNCIA DE DADOS)

**Enunciado:** Um vetor unidimensional de tamanho 20 (chamado `vetor`) deseja ser transformado em uma matriz de 4 linhas e 5 colunas, criada linha a linha. Qual expressão utilizar?

**Alternativas:**
a) `np.split(vetor, 4)`  
b) `vetor.reshape(5, 4)`  
c) `np.reshape(vetor, (4, 5))`  
d) `vetor.transpose(4, 5)`  
e) `np.array(vetor, shape=(4, 5))`

**Gabarito:** **c) `np.reshape(vetor, (4, 5))`** (ou `vetor.reshape(4, 5)`)

**Análise:**
- A alternativa **b** está incorreta porque `reshape(5, 4)` produziria 5 linhas e 4 colunas (inverte a ordem).
- `np.split(vetor, 4)` divide o vetor em 4 sub-arrays, mas retorna uma **lista de arrays**, não uma matriz única 4×5.
- `transpose` é uma operação de transposição, não de redimensionamento.
- `np.array(vetor, shape=(4,5))` tem sintaxe inválida – `shape` não é parâmetro direto de `np.array()`.

**Demonstração:**
```python
x = np.arange(1, 21)                # [1...20]
y = x.reshape(4, 5)                 # matriz 4×5
# ou
y = np.reshape(x, (4, 5))           # mesmo resultado
```

## GABARITO DAS QUESTÕES DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/2024/CVM) | c |
| 02 (CESGRANRIO/2024/IPEA) | c |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy X" (professor Rogério Araújo, Gran Concursos).*