# Anotações (Continuação - NumPy XI)

## 46. Adicionando Elementos em Arrays

### 46.1 Princípio fundamental

O **NDArray** possui **tamanho fixo**. Portanto, não é possível adicionar elementos diretamente ao array original. Qualquer operação de adição resulta na **criação de um novo array**, derivado do original, com o elemento incluído. O array original permanece inalterado.

### 46.2 `np.append(array, elemento)`

- Adiciona um **único elemento** no **final** do array.
- Retorna um **novo array** com o elemento acrescentado.

```python
import numpy as np
arrei1 = np.array([1, 2, 3, 4, 5])
arrei2 = np.append(arrei1, 6)
print(arrei1)   # [1 2 3 4 5] → inalterado
print(arrei2)   # [1 2 3 4 5 6]
```

### 46.3 `np.insert(array, índice, elemento)`

- Insere um elemento em uma **posição específica** (índice).
- Os elementos posteriores são **deslocados** para a direita.
- Retorna um **novo array**.

```python
arrei3 = np.insert(arrei1, 1, 15)   # insere 15 no índice 1
print(arrei3)   # [1 15 2 3 4 5]
```

> ### 46.3.1 Atenção
> - O **índice** segue a indexação padrão Python (começa em 0).
> - Tanto `append` quanto `insert` **não modificam o array original** – retornam uma **cópia** com a alteração.

## 47. Concatenando Arrays

### 47.1 Visão geral dos métodos

| MÉTODO | COMPORTAMENTO | MANTÉM Nº DE DIMENSÕES? | CRIA NOVA DIMENSÃO? |
| --- | --- | --- | --- |
| `np.concatenate()` | Junta arrays ao longo de um eixo existente | Sim | Não |
| `np.stack()` | Empilha arrays criando um novo eixo | Não (aumenta em 1) | Sim |
| `np.vstack()`, `np.hstack()`, `np.dstack()` | Atalhos semânticos para empilhamentos vertical, horizontal e em profundidade | Depende | Depende |

> ### 47.1.1 Regra geral
> - `concatenate` **preserva** o número de dimensões.
> - `stack` **aumenta** o número de dimensões em 1.
> - Os arrays concatenados devem ter **o mesmo número de dimensões** e serem compatíveis em `shape` em todos os eixos, exceto no eixo da concatenação.

### 47.2 `np.concatenate((a1, a2, ...), axis=0)`

#### 47.2.1 Com arrays 1D (unidimensionais)

```python
arrei1 = np.array([1, 2, 3, 4])
arrei2 = np.array([15, 16, 17, 18])
arrei3 = np.concatenate((arrei1, arrei2))
print(arrei3)   # [1 2 3 4 15 16 17 18] → ainda 1D
```

- O resultado é um único array 1D com todos os elementos em sequência.

#### 47.2.2 Com arrays 2D (bidimensionais) – axis padrão (0)

```python
arrei1 = np.array([[1, 2, 3, 4]])        # shape (1, 4)
arrei2 = np.array([[15, 16, 17, 18]])   # shape (1, 4)
arrei3 = np.concatenate((arrei1, arrei2))
print(arrei3)   # [[1 2 3 4]
                #  [15 16 17 18]]  → shape (2, 4)
```

- A concatenação ocorre **empilhando linhas** (aumenta o eixo 0).
- O resultado permanece 2D.

#### 47.2.3 Com arrays 2D de diferentes tamanhos no eixo 0

```python
arrei1 = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])  # shape (2, 4)
arrei2 = np.array([[21, 22, 23, 24]])                 # shape (1, 4)
arrei3 = np.concatenate((arrei1, arrei2))
print(arrei3)   # [[1 2 3 4]
                #  [15 16 17 18]
                #  [21 22 23 24]] → shape (3, 4)
```

### 47.3 Parâmetro `axis` em `concatenate`

- **`axis=0` (padrão):** concatena ao longo da primeira dimensão (empilha linhas em arrays 2D; aumenta o tamanho do eixo 0).
- **`axis=1`:** concatena ao longo da segunda dimensão (empilha colunas em arrays 2D; aumenta o tamanho do eixo 1).

**Exemplo com `axis=1` (concatenação por colunas):**

```python
arrei1 = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])   # shape (2, 4)
nova_coluna = np.array([[21], [22]])                  # shape (2, 1)
arrei3 = np.concatenate((arrei1, nova_coluna), axis=1)
print(arrei3)   # [[1 2 3 4 21]
                #  [15 16 17 18 22]] → shape (2, 5)
```

> ### 47.3.1 Condições para concatenar
> - Todos os arrays devem ter **o mesmo número de dimensões**.
> - Os `shape` devem ser **idênticos em todos os eixos, exceto no eixo de concatenação**.
> - Exemplo: para `axis=1`, o número de **linhas** (eixo 0) deve ser igual em todos os arrays.

### 47.4 Equivalência entre `concatenate` com `axis=0` e omissão do eixo

- `np.concatenate((a, b))` é equivalente a `np.concatenate((a, b), axis=0)`.
- O comportamento padrão é sempre concatenar no primeiro eixo (eixo 0).

### 47.5 Diferenciação importante para arrays 1D vs. 2D

| SITUAÇÃO | `concatenate` | RESULTADO |
| --- | --- | --- |
| Arrays 1D | `np.concatenate((a, b))` | Array 1D maior (elementos em sequência) |
| Arrays 2D com `axis=0` | `np.concatenate((a, b), axis=0)` | Mais **linhas** (aumenta eixo 0) |
| Arrays 2D com `axis=1` | `np.concatenate((a, b), axis=1)` | Mais **colunas** (aumenta eixo 1) |

> ### 47.5.1 Pegadinha comum
> - Se você tem arrays 2D com `shape (2,4)` e tenta concatenar com um array `shape (2,)` (1D), ocorrerá erro. É necessário primeiro transformar o array 1D em 2D (ex.: `array.reshape(2,1)` ou `array[:, np.newaxis]`) para compatibilizar as dimensões.

### 47.6 Outros métodos de empilhamento (visão geral)

Embora o foco da aula seja `concatenate`, o professor menciona:

| MÉTODO | DESCRIÇÃO |
| --- | --- |
| `np.vstack((a, b))` | Empilha verticalmente (linhas) – equivalente a `concatenate` com `axis=0` para arrays 2D |
| `np.hstack((a, b))` | Empilha horizontalmente (colunas) – equivalente a `concatenate` com `axis=1` para arrays 2D |
| `np.dstack((a, b))` | Empilha em profundidade (terceira dimensão) – aumenta `ndim` |
| `np.stack((a, b), axis=n)` | Cria uma **nova dimensão** no eixo especificado (aumenta `ndim` em 1) |

> ### 47.6.1 Nota
> - `stack` difere fundamentalmente de `concatenate` porque **aumenta o número de dimensões**. Por exemplo, empilhar dois arrays 1D com `stack` resulta em um array 2D.
> - As bancas podem cobrar a diferença entre `concatenate` (preserva dimensões) e `stack` (cria nova dimensão).

## 48. Resumo – Comportamento do `concatenate` por tipo de array

| TIPO DOS ARRAYS | EIXO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- | --- |
| 1D e 1D | axis=0 (padrão) | 1D mais longo | Elementos em sequência |
| 2D e 2D (compatible shapes) | axis=0 | 2D com mais linhas | Empilhamento vertical |
| 2D e 2D (compatible shapes) | axis=1 | 2D com mais colunas | Empilhamento horizontal |
| 2D e (array 1D mal formatado) | qualquer | Erro | Dimensões incompatíveis |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XI" (professor Rogério Araújo, Gran Concursos).*