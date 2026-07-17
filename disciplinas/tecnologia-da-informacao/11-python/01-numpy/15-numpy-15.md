# Anotações (Continuação - NumPy XV)

## 58. Operações Aritméticas – Elemento a Elemento (*Element-wise*)

### 58.1 Princípio

- Os operadores aritméticos (`+`, `-`, `*`, `/`, `%`, `**`) e suas respectivas funções no NumPy (`np.add`, `np.subtract`, `np.multiply`, `np.divide`, `np.mod`, `np.power`) atuam **elemento a elemento**.
- Os arrays devem ter **shapes compatíveis** (mesmo shape ou compatíveis por *broadcasting*).
- O resultado é um **novo array** com a mesma forma (ou forma compatível).

### 58.2 Operadores e funções equivalentes (consolidação)

| OPERAÇÃO | OPERADOR | FUNÇÃO EQUIVALENTE |
| --- | --- | --- |
| Soma | `a + b` | `np.add(a, b)` |
| Subtração | `a - b` | `np.subtract(a, b)` |
| Multiplicação | `a * b` | `np.multiply(a, b)` |
| Divisão | `a / b` | `np.divide(a, b)` |
| Resto da divisão (módulo) | `a % b` | `np.mod(a, b)` (ou `np.remainder(a, b)`) |
| Potência | `a ** b` | `np.power(a, b)` |

### 58.3 Exemplos práticos

**Exemplo 1 – arrays 1D:**
```python
arrei1 = np.array([18, 2, 17, 4])
arrei2 = np.array([2, 7, 5, 11])

print(arrei1 + arrei2)   # [20, 9, 22, 15]
print(arrei1 - arrei2)   # [16, -5, 12, -7]
print(arrei1 * arrei2)   # [36, 14, 85, 44]
print(arrei1 / arrei2)   # [9.0, 0.2857, 3.4, 0.3636]
print(arrei1 % arrei2)   # [0, 2, 2, 4]
print(arrei1 ** arrei2)  # [324, 128, 1419857, 4194304]
```

**Exemplo 2 – broadcasting (array 2D × 1D):**
```python
arrei1 = np.array([[18, 2, 17, 4]])   # shape (1,4)
arrei2 = np.array([2, 7, 5, 11])      # shape (4,)
# broadcasting: arrei2 é tratado como (1,4)
print(np.add(arrei1, arrei2))         # [20, 9, 22, 15]
```

**Exemplo 3 – arrays 2D com shapes compatíveis:**
```python
arrei1 = np.array([[18, 2, 17, 4], [6, 3, 15, 1]])   # shape (2,4)
arrei2 = np.array([[2, 7, 5, 11], [12, 4, 7, 8]])     # shape (2,4)
print(arrei1 + arrei2)   # [[20,9,22,15], [18,7,22,9]]
```

> ### 58.3.1 Atenção
> - As operações aritméticas **não modificam os arrays originais** – retornam um novo array.
> - Para arrays multidimensionais, a operação ocorre **entre elementos de mesma posição** em cada dimensão.

### 58.4 Funções adicionais relacionadas à divisão

| FUNÇÃO | RETORNO | DESCRIÇÃO |
| --- | --- | --- |
| `np.remainder(a, b)` | Resto da divisão | Equivalente a `a % b` e `np.mod(a, b)` |
| `np.divmod(a, b)` | Tupla `(quociente, resto)` | Retorna dois arrays: quociente (divisão inteira) e resto |

**Exemplo:**
```python
arrei1 = np.array([18, 2, 17, 4])
arrei2 = np.array([2, 7, 5, 11])

print(np.remainder(arrei1, arrei2))   # [0, 2, 2, 4]
print(np.divmod(arrei1, arrei2))      # (array([9,0,3,0]), array([0,2,2,4]))
```

> ### 58.4.1 Interpretação do `divmod`
> - A primeira parte da tupla é o **quociente da divisão inteira** (floor division).
> - A segunda parte é o **resto** (módulo).
> - No exemplo: `18 // 2 = 9`, `18 % 2 = 0`; `2 // 7 = 0`, `2 % 7 = 2`; etc.

### 58.5 Valor absoluto

```python
arrei = np.array([-1, -2, 3, 4])
print(np.absolute(arrei))   # [1, 2, 3, 4]
```

- `np.absolute()` (ou `np.abs()`) retorna o valor absoluto de cada elemento.

## 59. Somatórios em Arrays

### 59.1 Diferenciação entre `np.add()` e `np.sum()`

| FUNÇÃO | COMPORTAMENTO | RESULTADO | EXEMPLO (2 arrays 1D de 4 elementos) |
| --- | --- | --- | --- |
| `np.add(a, b)` | Soma **elemento a elemento** | Array da mesma forma | `[20, 9, 22, 15]` |
| `np.sum([a, b])` | Soma **todos os elementos** de todos os arrays | Escalar (agregação total) | `66` (18+2+17+4+2+7+5+11) |
| `np.sum([a, b], axis=0)` | Soma ao longo do eixo 0 (colunas/vertical) | Array 1D com soma de cada posição | `[20, 9, 22, 15]` |
| `np.sum([a, b], axis=1)` | Soma ao longo do eixo 1 (linhas) | Array 1D com soma de cada array individual | `[41, 25]` |

**Exemplo completo:**
```python
arrei1 = np.array([18, 2, 17, 4])
arrei2 = np.array([2, 7, 5, 11])

print(np.add(arrei1, arrei2))           # [20 9 22 15]
print(np.sum([arrei1, arrei2]))         # 66
print(np.sum([arrei1, arrei2], axis=0)) # [20 9 22 15]
print(np.sum([arrei1, arrei2], axis=1)) # [41 25]
```

> ### 59.1.1 Explicação do `axis` no `np.sum`
> - Quando se passa uma **lista de arrays** para `np.sum()`, o NumPy primeiro os empilha como se fossem um array 2D (linhas = arrays individuais, colunas = posições dos elementos).
> - `axis=0`: soma **cada coluna** → resultado tem o mesmo número de elementos que cada array original.
> - `axis=1`: soma **cada linha** (cada array individual) → resultado tem um elemento por array original (total de cada array).
> - Sem `axis`: soma todos os elementos de todos os arrays (escalar).

### 59.2 `np.cumsum()` – somatório acumulado (mencionado na aula)

- Retorna um array onde cada elemento é a **soma acumulada** (prefix sum) dos elementos do array original.

**Exemplo conceitual:**
```python
arrei = np.array([1, 2, 3, 4])
print(np.cumsum(arrei))   # [1, 3, 6, 10]
```

- Para arrays multidimensionais, é possível especificar o `axis` para o somatório acumulado ao longo de um eixo.

> ### 59.2.1 Utilidade
> - `cumsum` é útil para cálculos de somas parciais, como evolução de saldos, juros acumulados, etc.

## 60. Questão de Concurso Comentada

### 60.1 (CESGRANRIO/2021/BANCO DO BRASIL/AGENTE DE TECNOLOGIA)

**Código:**
```python
import numpy as np
valorAplicado = np.array([5000, 6000, 7000, 8000])
taxaJuros = np.array([1, 2, 3, 4])
resultado = valorAplicado * taxaJuros
```

**O que será exibido?**

**Alternativas:**
a) 70000  
b) 260000  
c) [5000 12000 21000 32000]  
d) matriz 4×4 com produtos (broadcasting errado)  
e) matriz 4×4 com produtos (outra ordem)

**Gabarito: c) [5000 12000 21000 32000]**

**Análise:**
- Ambos os arrays são **1D** e têm o mesmo tamanho (4 elementos).
- O operador `*` realiza multiplicação **elemento a elemento**.
- Cálculo:
  - 5000 × 1 = 5000
  - 6000 × 2 = 12000
  - 7000 × 3 = 21000
  - 8000 × 4 = 32000
- O resultado é um array 1D com esses 4 valores.

> ### 60.1.1 Distração das alternativas
> - As alternativas d) e e) sugerem matrizes 4×4 (produto externo ou *broadcasting* mal interpretado), que seria o resultado se um dos arrays fosse 2D com formato (4,1) e o outro (1,4), mas não é o caso.
> - O item a) (70000) seria a soma de todos os elementos do resultado.
> - O item b) (260000) seria a soma de todos os elementos do resultado original? Não corresponde.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/2021/BB) | c |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XV" (professor Rogério Araújo, Gran Concursos).*