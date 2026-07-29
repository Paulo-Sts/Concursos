# Anotações (Continuação - NumPy IV)

## 14. Conversão de Tipo com `astype()` (Complemento)

### 14.1 Método `astype(tipo)`

- O método **`astype()`** cria uma **cópia** do array original com os elementos convertidos para o tipo especificado.
- O **array original permanece inalterado**.

### 14.2 Exemplo 1 – Inteiro para Unicode (string)

```python
arrei = np.array([10, 12, 14])
novo_arrei = arrei.astype('U')
print(arrei.dtype)      # int64
print(novo_arrei.dtype) # <U21
print(novo_arrei)       # ['10' '12' '14']
```

### 14.3 Exemplo 2 – *Float* para Inteiro

```python
arrei = np.array([1.1, 2.1, 3.1])
novo_arrei = arrei.astype('i')
print(arrei.dtype)      # float64
print(novo_arrei.dtype) # int32
print(novo_arrei)       # [1 2 3]  → truncamento, não arredondamento
```

> ### 14.3.1 Conversão de *float* para inteiro
> - As casas decimais são **descartadas** (truncamento), não há arredondamento.

### 14.4 Exemplo 3 – Inteiro para Booleano

```python
arrei = np.array([1, 0, 3])
novo_arrei = arrei.astype(bool)
print(arrei.dtype)      # int64
print(novo_arrei)       # [ True False True]
print(novo_arrei.dtype) # bool
```

- **Regra de conversão para bool:**
  - `0` (zero) → `False`
  - **Qualquer valor diferente de zero** → `True`

> ### 14.4.1 Dica de prova
> - Questões costumam cobrar que o array original **não é modificado** e que `astype` retorna um **novo array**.

## 15. Acesso a Elementos – Indexação (Indexing)

### 15.1 Princípios gerais

- Em Python (e linguagens derivadas de C), a indexação começa em **0**.
- O primeiro elemento tem índice `0`, o segundo `1`, e assim sucessivamente.
- Índices válidos: de `0` até `tamanho_do_array - 1`.

### 15.2 Indexação negativa

| ÍNDICE NEGATIVO | SIGNIFICADO |
| --- | --- |
| `-1` | Último elemento |
| `-2` | Penúltimo elemento |
| `-3` | Antepenúltimo elemento |
| ... | ... |

> ### 15.2.1 Comparação com outras linguagens
> - **Python, Java, C:** indexação começa em `0`.
> - **Linguagem R:** indexação começa em `1`.

### 15.3 Exemplos unidimensionais

```python
arrei = np.array([10, 12, 14])
print(arrei[0])   # 10
print(arrei[1])   # 12
print(arrei[2])   # 14
print(arrei[1] + arrei[2])  # 26
```

```python
arrei = np.array(["Python", "Java", "PHP", "C"])
print(arrei[-1])   # C
print(arrei[-2])   # PHP
print(arrei[-3])   # Java
print(arrei[-4])   # Python
print(arrei[-1] + arrei[-2])  # CPHP (concatenação)
```

### 15.4 Indexação em arrays multidimensionais (2D)

- **Sintaxes equivalentes:**
  - `array[linha, coluna]` (um par de colchetes com vírgula)
  - `array[linha][coluna]` (dois pares de colchetes)

**Exemplo com array 2×4:**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
```

| ACESSO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0, 0]` ou `arrei[0][0]` | `1` | 1ª linha, 1ª coluna |
| `arrei[0, 3]` ou `arrei[0][3]` | `4` | 1ª linha, 4ª coluna |
| `arrei[1, 2]` ou `arrei[1][2]` | `17` | 2ª linha, 3ª coluna |
| `arrei[1, 1]` ou `arrei[1][1]` | `16` | 2ª linha, 2ª coluna |

**Indexação negativa em 2D:**
| ACESSO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[-1, -3]` | `16` | última linha, 3ª coluna a partir do fim (16) |
| `arrei[-1, -4]` | `15` | última linha, 4ª coluna a partir do fim (15) |
| `arrei[-2, -2]` | `3` | penúltima linha, penúltima coluna (3) |

> ### 15.4.1 Atenção
> - Em arrays 2D, o **primeiro índice** refere-se à **linha** (dimensão externa), o **segundo índice** refere-se à **coluna** (dimensão interna).
> - Índices negativos funcionam em **ambas as dimensões** independentemente.

## 16. Questão de Concurso Comentada

### 16.1 (INSTITUTO ACESSO/2024/CÂMARA DE MANAUS – AM)

**Código:**
```python
my_array = np.array([[4, 5], [6, 1]])
print(my_array[0][1])
```

**Estrutura do array:**
```
Linha 0 (índice 0): [4, 5]
Linha 1 (índice 1): [6, 1]
```

**Análise:**
- `my_array[0]` → retorna a primeira linha: `[4, 5]`
- `my_array[0][1]` → dentro da primeira linha, acessa o elemento de índice 1 (segunda posição): **5**

**Sintaxe equivalente:** `my_array[0, 1]`

**Gabarito:** **e) 5**.

> ### 16.1.1 Demonstração adicional (indexação negativa)
> ```python
> print(my_array[-1][-2])  # 6 (última linha, penúltimo elemento)
> print(my_array[-2][-1])  # 5 (primeira linha, último elemento)
> ```

## 17. Fatiamento (Slicing) em Arrays 1D

### 17.1 Sintaxe

```python
array[início:fim:passo]
```

| PARÂMETRO | DESCRIÇÃO | OBSERVAÇÃO |
| --- | --- | --- |
| `início` | Índice onde começa (incluído) | Opcional. Padrão: `0` |
| `fim` | Índice onde **para** (não incluído) | Opcional. Padrão: `tamanho_do_array` |
| `passo` | Incremento entre elementos | Opcional. Padrão: `1` |

> ### 17.1.1 Regra fundamental
> - O elemento no índice **fim não é incluído** no resultado.

### 17.2 Exemplos com array 1D

```python
arrei = np.array(["Python", "Java", "PHP", "C"])
# Índices:         0        1       2     3
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0:3]` | `['Python', 'Java', 'PHP']` | índices 0, 1, 2 (fim=3 não incluso) |
| `arrei[:]` | `['Python', 'Java', 'PHP', 'C']` | todos os elementos (início=0, fim=4 padrão) |
| `arrei[:4]` | `['Python', 'Java', 'PHP', 'C']` | início=0 padrão, fim=4 (não incluso, mas é o fim) |
| `arrei[0:]` | `['Python', 'Java', 'PHP', 'C']` | início=0, fim padrão (tamanho) |
| `arrei[:2]` | `['Python', 'Java']` | início=0 padrão, fim=2 (índices 0 e 1) |

> ### 17.2.1 Observação importante
> - O fatiamento **não modifica o array original** – retorna um **novo array** (cópia dos elementos selecionados).
> - Quando início e fim são omitidos (`[:]`), o resultado é uma cópia de todo o array.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (INSTITUTO ACESSO/2024) | e |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy IV" (professor Rogério Araújo, Gran Concursos).*