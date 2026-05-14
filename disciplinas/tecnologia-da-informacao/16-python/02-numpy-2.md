# Anotações (Continuação - NumPy II)

## 7. Arrays por Dimensão (0D, 1D, 2D, 3D)

### 7.1 Array 0D (Escalar)

- Criado ao passar um valor **solto** (sem colchetes ou parênteses) para `np.array()`.

```python
import numpy as np
arrei = np.array(15)
print(arrei.ndim)   # 0
print(arrei.shape)  # ()
print(arrei.size)   # 1
```

> ### 7.1.1 Observação do professor
> - **`ndim = 0`** indica zero dimensões. O array armazena um único valor escalar.
> - A ausência de delimitadores (`[ ]` ou `( )`) é a chave para identificar um array 0D.

### 7.2 Array 1D (Unidimensional)

- Criado com **um par de colchetes** envolvendo os elementos.

```python
arrei = np.array([1, 2, 3, 4, 5])
print(arrei.ndim)   # 1
print(arrei.shape)  # (5,)
print(arrei.size)   # 5
```

- **Shape:** `(5,)` → 5 elementos na única dimensão; o valor após a vírgula fica em branco (ou zero).

> ### 7.2.1 Lembrete do professor
> - `type(arrei)` sempre retorna `<class 'numpy.ndarray'>`. Use **`dtype`** para saber o tipo dos elementos.

### 7.3 Array 2D (Bidimensional)

- Criado com **dois pares de colchetes** (um delimitando cada linha).

```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
print(arrei.ndim)   # 2
print(arrei.shape)  # (2, 4)
print(arrei.size)   # 8 (total de elementos: 2×4)
```

- **Shape `(2, 4)`:** primeira dimensão = 2 linhas; segunda dimensão = 4 colunas.
- **Total de elementos** = multiplicação dos valores do *shape* (2 × 4 = 8).

> ### 7.3.1 Pegadinha da banca
> - O atributo **`size`** retorna a **quantidade total** de elementos (soma de todas as dimensões), não apenas a primeira dimensão.
> - O **`shape`** só apresenta a segunda informação (valor após a vírgula) quando o array tem 2 ou mais dimensões. Em arrays 2D, o segundo número indica quantos elementos há em cada linha/coluna.

### 7.4 Array 3D (Tridimensional)

- Criado com **três pares de colchetes** aninhados.

```python
arrei = np.array([[[1, 2, 3], [4, 5, 6]], [[15, 17, 19], [21, 22, 23]]])
print(arrei.ndim)   # 3
print(arrei.shape)  # (2, 2, 3)
print(arrei.size)   # 12 (2×2×3)
```

- **Shape `(2, 2, 3)`:** 
  - 1ª dimensão: 2 blocos principais.
  - 2ª dimensão: cada bloco tem 2 linhas.
  - 3ª dimensão: cada linha tem 3 colunas.

## 8. Tipos de Dados no NumPy

### 8.1 Tipos nativos do Python (revisão)

| TIPO PYTHON | EXEMPLO |
| --- | --- |
| Inteiro (`int`) | `x = 15` |
| Ponto flutuante (`float`) | `y = 1.84` |
| Complexo (`complex`) | `z = 15 + 7j` |
| Booleano (`bool`) | `x = True` |
| Texto (`str`) | `x = "Python"` |

### 8.2 Tipos adicionais do NumPy (representados por um caractere)

| CARACTERE | SIGNIFICADO | DESCRIÇÃO |
| --- | --- | --- |
| `i` | Inteiro (integer) | Ex.: `int32`, `int64` |
| `f` | Ponto flutuante (float) | Ex.: `float32`, `float64` |
| `c` | Complexo (complex) | Números complexos |
| `b` | Booleano (boolean) | `True` / `False` |
| `S` | String (byte string) | String de bytes |
| `U` | String Unicode | Ex.: `<U6` (string de até 6 caracteres) |
| `m` | Timedelta | Diferença entre datas/horas |
| `M` | Datetime | Data e hora |
| `O` | Objeto (object) | Qualquer objeto Python |
| `V` | Void | Bloco fixo de memória para outro tipo |

> ### 8.2.1 Importante
> - O **`dtype`** de um array com strings geralmente aparece como **`<U6`** (Unicode, 6 caracteres no exemplo do professor) ou similar.
> - O símbolo `<` indica *little-endian* (arquitetura comum).

## 9. Criação de Arrays com Tipo Definido (parâmetro `dtype`)

### 9.1 Convertendo tipos explicitamente

```python
import numpy as np

# Criar array de inteiros, mas forçar tipo string
arrei = np.array([10, 12, 14], dtype='U')
print(arrei.dtype)  # <U2 (Unicode de até 2 caracteres)
print(arrei)        # ['10' '12' '14']

# Criar array de strings, mas forçar tipo inteiro
arrei2 = np.array(['10', '12', '14'], dtype='i')
print(arrei2.dtype) # int32
print(arrei2)       # [10 12 14]
```

> ### 9.1.1 Atenção (Exemplo 2 do professor)
> - Se um elemento **não puder ser convertido** para o tipo especificado, ocorre erro `ValueError`.
> ```python
> arrei = np.array(['a', '12', '14'], dtype='i')
> # ValueError: invalid literal for int() with base 10: 'a'
> ```

### 9.2 *Structured dtype* (dtype estruturado)

- Permite criar arrays com **campos nomeados** de diferentes tipos (como uma tabela).

```python
# Exemplo 3: tuplas com campos x e y
arrei = np.array([(1, 2), (3, 4), (5, 6)], dtype=[('x', 'i4'), ('y', 'i4')])
print(arrei.dtype)   # [('x', '<i4'), ('y', '<i4')]
print(arrei['x'])    # [1 3 5]
print(arrei['y'])    # [2 4 6]
```

```python
# Exemplo 4: dados estruturados (id, nome, salario)
linguagens = [(15, 'Java', 18125.35), (19, 'Python', 23535.5)]
arrei = np.array(linguagens, dtype=[('id', 'i4'), ('nome', 'U10'), ('salario', 'f4')])
print(arrei['id'])       # [15 19]
print(arrei['nome'])     # ['Java' 'Python']
print(arrei['salario'])  # [18125.35 23535.5]
```

> ### 9.2.1 Características do structured dtype
> - O array permanece **homogêneo** (todos os elementos seguem a mesma estrutura).
> - Acesso aos campos por nome (ex.: `arrei['nome']`).
> - Útil para representar registros ou linhas de tabela.

## 10. Questão de Concurso Comentada

### 10.1 (FUNDATEC/2022/AGERGS/TÉCNICO SUPERIOR ENGENHEIRO DE DADOS)

**Código apresentado:**

```python
import numpy as np
series = [[23,45,12,679], [14,48,69,38]]
new_series = np.array(series)
print(new_series.ndim)
print(new_series.shape)
```

**Pergunta:** Qual é a saída correta?

**Alternativas:**
a) 2 (2, 4)  
b) 2 (4, 2)  
c) 4 (2)  
d) 2 (4)  
e) 4 (2,4)

**Gabarito:** **a) 2 (2, 4)**

**Comentário:**  
- O array `new_series` é bidimensional (2 dimensões) porque a lista `series` possui duas listas internas (`ndim = 2`).  
- `shape` retorna `(2, 4)`: 2 linhas e 4 colunas (total de 8 elementos).  

> ### 10.1.1 Verificação
> ```python
> print(new_series.size)   # 8
> print(new_series.dtype)  # int64
> ```

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 | a |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy II" (professor Rogério Araújo, Gran Concursos).*