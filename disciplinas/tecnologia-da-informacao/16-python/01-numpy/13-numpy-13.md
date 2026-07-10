# Anotações (Continuação - NumPy XIII)

## 52. Empilhamento Horizontal com `np.hstack()`

### 52.1 Conceito e equivalência

- `np.hstack()` realiza o **empilhamento horizontal** (lado a lado), aumentando o número de colunas.
- **Mantém o número de dimensões** dos arrays originais (diferente do `np.stack()`, que cria nova dimensão).

**Equivalência fundamental:**
- `np.hstack((a, b))` ≡ `np.concatenate((a, b), axis=1)` (para arrays com mesma dimensionalidade compatível).

### 52.2 Exemplo prático

```python
arrei1 = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])  # shape (2,4)
nova_coluna = np.array([[21], [22]])                 # shape (2,1)

# Usando hstack
arrei2 = np.hstack((arrei1, nova_coluna))

# Usando concatenate com axis=1 (equivalente)
arrei3 = np.concatenate((arrei1, nova_coluna), axis=1)

print(arrei2)
# [[1 2 3 4 21]
#  [15 16 17 18 22]]
```

- `arrei1` (2×4) + `nova_coluna` (2×1) → resultado shape **(2,5)**.
- A operação **não cria nova dimensão**; apenas aumenta o tamanho do eixo 1 (colunas).

> ### 52.2.1 Relação entre `vstack`, `hstack` e `concatenate`
> - `np.vstack((a, b))` ≡ `np.concatenate((a, b), axis=0)` (empilha linhas).
> - `np.hstack((a, b))` ≡ `np.concatenate((a, b), axis=1)` (empilha colunas).
> - Ambas **mantêm** o número de dimensões, diferentemente de `np.stack()`.

> ### 52.2.2 Atenção (pegadinha comum)
> - Apesar de conter a palavra *stack* no nome, **`vstack` e `hstack` NÃO criam nova dimensão** – comportam-se como `concatenate` com eixo específico.
> - O método que **cria nova dimensão** é `np.stack()` (sem o prefixo `v` ou `h`).

## 53. Alteração de Elementos em Arrays

### 53.1 Modificação por índice direto

- É possível alterar elementos de um array atribuindo novos valores a posições específicas.
- A modificação ocorre **diretamente no array original** (diferente de `append`/`insert`, que criam cópias).

**Exemplo 1D:**
```python
arrei = np.array(["Python", "Java", "PHP", "C"])
arrei[1] = "C#"    # altera o índice 1
# Resultado: ['Python', 'C#', 'PHP', 'C']
```

**Exemplo 2D:**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
arrei[1][2] = 30   # linha 1, coluna 2 → 17 vira 30
# ou arrei[1, 2] = 30 (notação com vírgula)
# Resultado: [[1,2,3,4], [15,16,30,18]]
```

### 53.2 Modificação por fatiamento (atribuição múltipla)

- É possível alterar **vários elementos simultaneamente** usando fatiamento.
- O valor atribuído pode ser um escalar (atribui o mesmo valor a todos os elementos selecionados) ou um array de dimensões compatíveis.

**Exemplo 1 – alterar uma fatia de linha:**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
arrei[0, 1:3] = 30   # linha 0, colunas 1 a 2 (índices 1 e 2)
# Resultado: [[1, 30, 30, 4], [15, 16, 17, 18]]
```

**Exemplo 2 – alterar submatriz (interseção de linhas e colunas):**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18], [21, 22, 23, 24]])
arrei[0:2, 1:3] = 45   # linhas 0 e 1, colunas 1 e 2
# Resultado: [[1,45,45,4], [15,45,45,18], [21,22,23,24]]
```

> ### 53.2.1 Funcionamento
> - O fatiamento seleciona uma região (pode ser contígua ou com passo).
> - O valor atribuído é **transmitido** (*broadcast*) para todos os elementos da região selecionada.
> - A modificação é **in-place** (altera o array original).

## 54. Método `np.arange()`

### 54.1 Conceito e sintaxe

- `np.arange()` é similar à função embutida `range()` do Python, mas retorna um **array NumPy** (1D).
- **Parâmetros:** `np.arange([início,] fim [, passo])`
  - `início` (opcional): valor inicial (padrão = 0).
  - `fim` (obrigatório): valor de parada (não incluso).
  - `passo` (opcional): incremento (padrão = 1).

### 54.2 Exemplos de sequências crescentes

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `np.arange(5)` | `[0, 1, 2, 3, 4]` | início=0 padrão, fim=5, passo=1 |
| `np.arange(3, 6)` | `[3, 4, 5]` | início=3, fim=6, passo=1 |
| `np.arange(3, 10, 2)` | `[3, 5, 7, 9]` | início=3, fim=10, passo=2 |
| `np.arange(0, 1, 0.2)` | `[0.0, 0.2, 0.4, 0.6, 0.8]` | passo float; não atinge o fim |

### 54.3 Sequências decrescentes (passo negativo)

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `np.arange(10, 3, -1)` | `[10, 9, 8, 7, 6, 5, 4]` | início=10, fim=3 (não incluso), passo=-1 |
| `np.arange(-1, -15, -2)` | `[-1, -3, -5, -7, -9, -11, -13]` | início=-1, fim=-15, passo=-2 |

### 54.4 Condições para array não vazio

A relação entre `início`, `fim` e `passo` deve ser **lógica** para que a sequência progrida do início em direção ao fim.

| CONDIÇÃO | PASSO NECESSÁRIO | RESULTADO SE PASSO INVERSO |
| --- | --- | --- |
| `início < fim` | **Positivo** | Array vazio (ex.: `np.arange(3, 6, -1)` → `[]`) |
| `início > fim` | **Negativo** | Array vazio (ex.: `np.arange(-15, -1, -2)` → `[]`) |

> ### 54.4.1 Regra prática
> - Para gerar uma sequência válida, o passo deve **apontar do início em direção ao fim**.
> - Se o passo "empurrar" para longe do fim, o resultado é um array **vazio**.

## 55. Questão de Concurso Comentada

### 55.1 (FGV/2024/EPE/ANALISTA DE PESQUISA ENERGÉTICA)

**Código:**
```python
import numpy as np
x = np.arange(1, 30, 2).reshape(3, 5)
y = x[[1, 2]]
y[0, :] = 0
z = x[0, 2]
```

**Assinale o valor que `z` recebe na linha `<5>`:**
a) 0  
b) 5  
c) array([[0,0,0,0,0]])  
d) array([[11,13,15], [21,23,25]])  
e) array([[1,3,5], [11,13,15]])

**Gabarito: b) 5**

### 55.2 Análise passo a passo

**Passo 1 – criação de `x`:**
```python
x = np.arange(1, 30, 2).reshape(3, 5)
```
- `np.arange(1, 30, 2)` → elementos ímpares de 1 a 29:  
  `[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]` (15 elementos).
- `.reshape(3, 5)` → reorganiza em 3 linhas × 5 colunas:

```
[[ 1,  3,  5,  7,  9],
 [11, 13, 15, 17, 19],
 [21, 23, 25, 27, 29]]
```

**Passo 2 – criação de `y` (fancy indexing):**
```python
y = x[[1, 2]]
```
- `x[[1, 2]]` seleciona as **linhas de índice 1 e 2**.
- **Importante:** fancy indexing com lista de índices retorna uma **cópia** (não uma view).
- `y` torna-se:
```
[[11, 13, 15, 17, 19],
 [21, 23, 25, 27, 29]]
```

**Passo 3 – modificação de `y`:**
```python
y[0, :] = 0
```
- Altera **todos os elementos da primeira linha de `y`** (índice 0) para 0.
- `y` passa a ser:
```
[[ 0,  0,  0,  0,  0],
 [21, 23, 25, 27, 29]]
```
- Como `y` é uma **cópia** (não uma view), **`x` permanece inalterado**.

**Passo 4 – atribuição a `z`:**
```python
z = x[0, 2]
```
- Acessa o elemento na **linha 0, coluna 2** do array original `x`.
- `x[0, 2]` = **5** (pois `x` não foi modificado).

> ### 55.2.1 Conceito-chave da questão
> - **Fancy indexing com lista** (`x[[1,2]]`) **retorna uma cópia**, não uma view.
> - Modificações em `y` **não afetam** `x`.
> - Portanto, `x[0,2]` continua sendo o valor original `5`, não `0`.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/2024/EPE) | b |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XIII" (professor Rogério Araújo, Gran Concursos).*