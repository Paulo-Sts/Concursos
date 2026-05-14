# Anotações (Continuação - NumPy VIII)

## 31. *Fancy Indexing* Avançado em Arrays 2D – Combinação de Listas

### 31.1 Seleção de linhas inteiras com lista de índices (revisão)

```python
arrei = np.array([[1, 2, 3, 4],
                  [15, 16, 17, 18],
                  [21, 22, 23, 24]])

print(arrei[[0, 2]])   # [[1,2,3,4], [21,22,23,24]]
```

- `arrei[[0, 2]]` seleciona as **linhas 0 e 2** (completas) → array 2D.

### 31.2 Combinação de duas listas de índices (pareamento)

**Sintaxe:** `arrei[[lista_linhas], [lista_colunas]]`

```python
print(arrei[[0, 2], [1, 3]])   # [2, 24]
```

**Lógica:** as duas listas são combinadas **elemento a elemento** (como um *zip*):

- Par (0,1) → linha 0, coluna 1 → valor **2**
- Par (2,3) → linha 2, coluna 3 → valor **24**

> ### 31.2.1 Distinção fundamental (pegadinha)
> - `arrei[[0, 2], [1, 3]]` → **dois elementos** (combinação pareada).
> - `arrei[[0, 2]][:, [1, 3]]` → **submatriz 2×2** (todas as combinações entre linhas {0,2} e colunas {1,3}).
> - As bancas adoram confundir essas duas formas.

### 31.3 Filtro com condição em array 2D (achatamento)

```python
print(arrei[arrei > 15])   # [16, 17, 18, 21, 22, 23, 24]
```

- A condição `arrei > 15` gera uma máscara booleana da mesma forma que o array.
- A indexação com máscara booleana retorna os elementos **em um array 1D achatado** (todos os elementos que satisfazem a condição, independentemente da posição original).

> ### 31.3.1 Comportamento
> - Em arrays multidimensionais, a indexação booleana **achata** o resultado para 1D.
> - Para manter a estrutura 2D, seria necessário usar `np.where` ou combinações de *fancy indexing*.

## 32. Filtrando Arrays com Máscaras (Revisão Sistemática)

### 32.1 Máscara booleana fornecida explicitamente

**Exemplo 1 (1D):**
```python
arrei1 = np.array([1, 2, 3, 4, 5])
condicoes = [True, False, True, True, False]
arrei2 = arrei1[condicoes]   # [1, 3, 4]
```

- A lista de booleanos deve ter o **mesmo comprimento** do array (ou da dimensão).

**Exemplo 2 (2D com máscara 2D):**
```python
arrei1 = np.array([[1, 2, 4, 5], [15, 16, 17, 18]])
condicoes = [[True, False, True, False], [True, False, True, True]]
arrei2 = arrei1[condicoes]   # [1, 4, 15, 17, 18] → resultado 1D
```

> ### 32.2.1 Importante
> - A máscara booleana, quando aplicada a um array multidimensional, **achata** o resultado para 1D.
> - Para obter um subarray 2D, deve-se usar fatiamento ou *fancy indexing* estruturado.

### 32.3 Filtro com condição relacional direta

**Exemplo 3 (pares):**
```python
arrei1 = np.array([1, 2, 3, 4, 5, 6])
print(arrei1[arrei1 % 2 == 0])   # [2, 4, 6]
```

**Exemplo 4 (valores maiores ou iguais a 17):**
```python
arrei2 = np.array([[1, 2, 4, 5], [15, 16, 17, 18]])
print(arrei2[arrei2 >= 17])   # [17, 18] → achatado
```

**Exemplo 5 (ímpares em 2D):**
```python
print(arrei2[arrei2 % 2 != 0])   # [1, 5, 15, 17]
```

## 33. Questão de Concurso Comentada

### 33.1 (CESGRANRIO/2021/BANCO DO BRASIL/AGENTE DE TECNOLOGIA)

**Código:**
```python
import numpy as np
a = np.array([[1,2,3],[4,5,6],[7,8,9]])
print(a[a>5])
```

**Alternativa correta:** e) `[6 7 8 9]`

**Análise:**
- `a` é um array 3×3.
- `a > 5` gera máscara booleana: `[[F,F,F], [F,F,T], [T,T,T]]`.
- A indexação com máscara retorna todos os elementos onde a condição é `True` **em um array 1D achatado**.
- Elementos maiores que 5: 6, 7, 8, 9.

> ### 33.1.1 Por que não é `[[6],[7,8,9]]` ou algo 2D?
> - Indexação booleana em NumPy **sempre retorna uma cópia 1D** quando aplicada diretamente com máscara da mesma forma do array.
> - Para manter a dimensionalidade, seriam necessárias operações como `np.where` ou *fancy indexing* mais elaborado.

## 34. Método `np.where()` – Duas Sintaxes

### 34.1 Sintaxe 1: `np.where(condição)`

- Retorna os **índices** onde a condição é verdadeira.
- Retorna uma **tupla de arrays** (um array por dimensão).

**Exemplo 1D:**
```python
arrei1 = np.array([1, 2, 3, 4, 5, 4, 4])
print(np.where(arrei1 == 4))   # (array([3, 5, 6]),)
```

**Exemplo 2D:**
```python
arrei2 = np.array([[1, 2, 4, 5], [15, 4, 17, 4]])
print(np.where(arrei2 == 4))
# (array([0, 1, 1]), array([2, 1, 3]))
```

Interpretação:
- Primeiro array da tupla: índices das **linhas**.
- Segundo array: índices das **colunas**.
- Pares: (0,2), (1,1), (1,3) → posições onde valor = 4.

**Exemplo com condição (pares):**
```python
print(np.where(arrei1 % 2 == 0))   # índices dos números pares
```

**Exemplo com condição (ímpares em 2D):**
```python
print(np.where(arrei2 % 2 != 0))   # índices dos ímpares
```

> ### 34.1.1 Utilidade
> - `np.where(condição)` é usado para **localizar posições**, não para extrair os valores diretamente (embora se possa usar os índices para indexar o array original).

### 34.2 Sintaxe 2: `np.where(condição, valor_se_verdadeiro, valor_se_falso)`

- Funciona como um **operador ternário vetorizado**.
- Retorna um **novo array** da mesma forma que o array de entrada.

**Exemplo 1 – aprovação/reprovação:**
```python
notas = np.array([4.5, 6.0, 7.2, 5.9])
resultado = np.where(notas >= 6, "Aprovado", "Reprovado")
# ['Reprovado' 'Aprovado' 'Aprovado' 'Reprovado']
```

**Exemplo 2 – substituir valores negativos por zero:**
```python
arrei = np.array([10, -3, 5, -1, 0])
arrei1 = np.where(arrei < 0, 0, arrei)
# [10, 0, 5, 0, 0]
```

**Exemplo 3 – reajuste salarial condicional:**
```python
salarios = np.array([2000, 3200, 2800, 5000])
ajustados = np.where(salarios >= 3000, salarios * 1.10, salarios)
# [2000., 3520., 2800., 5500.]
```

| PARÂMETRO | SIGNIFICADO |
| --- | --- |
| `condição` | Expressão booleana (pode ser comparação com escalar ou outro array) |
| `valor_se_verdadeiro` | Valor (ou array) atribuído onde condição é `True` |
| `valor_se_falso` | Valor (ou array) atribuído onde condição é `False` |

> ### 34.2.1 Atenção
> - `valor_se_verdadeiro` e `valor_se_falso` podem ser **escalares**, **arrays da mesma forma** ou **expressões**.
> - O resultado tem a mesma forma que o array da condição.

## 35. Operador `in` – Verificação de Pertinência

- Funciona de forma semelhante às listas Python.
- Retorna `True` se o elemento estiver presente no array; `False` caso contrário.

**Exemplo:**
```python
arrei = np.array(["Python", "Java", "PHP", "C"])
print("Python" in arrei)   # True
print("C#" in arrei)       # False
print("Python" not in arrei)  # False
print("C#" not in arrei)      # True
```

> ### 35.1 Observação
> - O operador `in` verifica **elementos inteiros**, não substrings. `"Py" in arrei` retornaria `False` (não há elemento exatamente igual a `"Py"`).

## 36. Iteração com `for`

- Arrays NumPy são **iteráveis**: um loop `for` percorre os elementos na ordem em que aparecem (em 1D) ou as **linhas** (em 2D).

**Exemplo 1D:**
```python
for i in arrei:
    print(i)
```

**Saída (para array de strings):** cada string em uma linha.

> ### 36.1 Comportamento em 2D
> - Para um array 2D, `for linha in arrei:` itera sobre as **linhas** (cada linha é um array 1D).
> - Para iterar sobre elementos individuais, pode-se usar `.flat` ou loops aninhados.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/2021/BB) | e |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy VIII" (professor Rogério Araújo, Gran Concursos).*