# Anotações (Continuação - NumPy III)

## 11. Arrays Estruturados (Structured Arrays)

### 11.1 Conceito fundamental

- Um array estruturado (ou *structured array*) é um **array NDArray** em que **cada elemento** é composto por **múltiplos campos** (compartimentos), cada qual com seu próprio tipo de dados.
- Diferentemente de um array multidimensional (2D, 3D), aqui os campos **não representam novas dimensões** – eles são partes indivisíveis de cada elemento.

> ### 11.1.1 Distinção crucial (professor)
> - **Array 2D:** `shape = (2, 4)` → 2 linhas e 4 colunas (total 8 elementos independentes).
> - **Array estruturado com 2 elementos, cada um com 3 campos:** `ndim = 1`, `shape = (2,)` → apenas 2 elementos (cada elemento contém 3 informações agrupadas).
> - **Não confundir:** campos internos não geram dimensão extra.

### 11.2 Criação com `dtype` estruturado (revisão e aprofundamento)

**Sintaxe geral:**
```python
np.array(lista_de_tuplas, dtype=[('nome_campo1', 'tipo1'), ('nome_campo2', 'tipo2'), ...])
```

**Exemplo 4 (professor):**
```python
import numpy as np
linguagens = [(15, 'Java', 18125.35), (19, 'Python', 23535.5)]
arrei = np.array(linguagens, dtype=[('id', 'i4'), ('nome', 'U10'), ('salario', 'f4')])
```

**Atributos do array resultante:**
- `arrei.size` → `2` (dois elementos)
- `arrei.ndim` → `1` (uma única dimensão)
- `arrei.shape` → `(2,)` (segundo valor em branco)
- `arrei.dtype` → `[('id', '<i4'), ('nome', '<U10'), ('salario', '<f4')]`

> ### 11.2.1 Acesso aos campos
> - `arrei['id']` → retorna um array com todos os valores do campo `id`: `[15 19]`
> - `arrei['nome']` → `['Java' 'Python']`
> - `arrei['salario']` → `[18125.35 23535.5]`
> - `arrei[0]` → retorna o primeiro elemento completo: `(15, 'Java', 18125.35)`

## 12. Questões de Concurso Comentadas

### 12.1 (FGV/2024/INPE/TECNOLOGISTA PLENO)

**Código base:**
```python
import numpy as np
x = np.array([('Morango', 25, 18.3), ('Abacate', 37, 2.5)], 
             dtype=[('nome', 'U10'), ('codigo', 'i4'), ('valor', 'f4')])
```

**Afirmativas:**

| ITEM | COMANDO | RESULTADO ESPERADO | CORREÇÃO |
| --- | --- | --- | --- |
| I | `x[0]` | `('Morango', 25, 18.3)` | **Correto** – índice 0 acessa o primeiro elemento. |
| II | `x[x['codigo']>30]['valor']` | `2.5` | **Incorreto** – retorna `[2.5]` (lista/array de um elemento), não o valor solto `2.5`. |
| III | `x['nome'][:] = 'Laranja'` | altera apenas o último elemento | **Incorreto** – o fatiamento `[:]` seleciona **todos** os elementos, alterando o campo `nome` de **ambos** para `'Laranja'`. Para alterar só o último, seria `x['nome'][1] = 'Laranja'`. |

**Gabarito:** **a) I, apenas**.

> ### 12.1.1 Observação sobre o item II
> - A diferença entre `2.5` (valor solto) e `[2.5]` (array com um elemento) é **cobrada em provas**.
> - *Boolean indexing* (`x['codigo']>30`) retorna um array filtrado; ao acessar `['valor']`, obtém-se outro array (ainda que unitário).

### 12.2 (CESPE/CEBRASPE/2023/DATAPREV)

**Código apresentado:**
```python
import numpy as np
a = np.array([(1, 2), (3, 4), (5, 6)], dtype=[('x', 'i4'), ('y', 'i4')])
print(a)
print(a.shape)
```

**O enunciado afirmava que o resultado seria:**
```
[[1 2]
 [3 4]
 [5 6]
 ['x','i4']
 ['y','i4']]
(3, 2)
```

**Análise:**

- Na realidade, `print(a)` exibe: `[(1, 2) (3, 4) (5, 6)]`
- `a.dtype` exibe: `[('x', '<i4'), ('y', '<i4')]` – **não** é impresso pelo código dado.
- `a.shape` é `(3,)` – **não** `(3,2)`.

> ### 12.2.1 Por que shape é (3,) e não (3,2)?
> - O array tem **3 elementos**. Cada elemento é uma **tupla (x,y)** que forma um registro, **não** uma subdivisão dimensional.
> - Se fosse um array 2D verdadeiro (lista de listas, não lista de tuplas com dtype estruturado), o shape seria `(3,2)`.
> - **Erro da questão:** tanto a representação do array quanto o `shape` estão incorretos.

**Gabarito:** **E** (errado).

## 13. Conversão de Tipo de um Array Existente – `astype()`

### 13.1 Sintaxe e comportamento

- O método `astype(tipo)` cria uma **cópia** do array original, convertendo os elementos para o novo tipo especificado.
- O **array original permanece inalterado**.

### 13.2 Exemplo 1 – inteiro para string (Unicode)

```python
arrei = np.array([10, 12, 14])
novo_arrei = arrei.astype('U')
print(arrei.dtype)      # int64
print(novo_arrei.dtype) # <U21 (Unicode)
print(novo_arrei)       # ['10' '12' '14']
```

### 13.3 Exemplo 2 – *float* para inteiro

```python
arrei = np.array([1.1, 2.1, 3.1])
novo_arrei = arrei.astype('i')
print(arrei.dtype)      # float64
print(novo_arrei.dtype) # int32
print(novo_arrei)       # [1 2 3] (truncamento, não arredondamento)
```

> ### 13.3.1 Atenção
> - A conversão de `float` para `int` **trunca** a parte decimal (não arredonda).
> - `astype` é comumente cobrado em questões que verificam se o aluno sabe que o original não é modificado.

## GABARITO DAS QUESTÕES DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/2024) | a |
| 02 (CESPE/2023) | E |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy III" (professor Rogério Araújo, Gran Concursos).*