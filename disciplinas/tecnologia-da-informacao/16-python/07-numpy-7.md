# Anotações (Continuação - NumPy VI – Fancy Indexing e Distinções Avançadas)

## 27. Distinção Avançada: Fatiamento com Vírgula vs. Colchetes Sequenciais (Retomada)

### 27.1 Regra de ouro (ênfase do professor)

| COMEÇA COM | COMPARAÇÃO ENTRE NOTAÇÕES | RESULTADO |
| --- | --- | --- |
| **Índice** (ex.: `arrei[1]`) | `arrei[1, 2]` vs `arrei[1][2]` | **Equivalentes** (mesmo resultado) |
| **Índice + fatiamento** (ex.: `arrei[1, 1:2]` vs `arrei[1][1:2]`) | **Equivalentes** (mesmo resultado) |
| **Fatiamento** (ex.: `arrei[0:2]`) | `arrei[0:2, 1]` vs `arrei[0:2][1]` | **Diferentes** (resultados distintos) |
| **Fatiamento + fatiamento** (ex.: `arrei[0:2, 1:3]` vs `arrei[0:2][1:3]`) | **Diferentes** (resultados distintos) |

> ### 27.1.1 Justificativa
> - Quando se começa com **índice** (valor único, não fatiamento), o resultado é um array de **menor dimensionalidade** (ex.: uma linha, um escalar). Sobre esse resultado, qualquer operação posterior (índice ou fatiamento) produz o mesmo efeito independentemente do uso de vírgula ou colchetes separados.
> - Quando se começa com **fatiamento** (ex.: `0:2`), o resultado mantém a dimensionalidade original (ou subconjunto dela). A aplicação de vírgula atua **simultaneamente** no eixo 1 (colunas), enquanto colchetes separados aplicam um **novo fatiamento sobre o subarray já fatiado** – que pode atuar novamente no eixo 0 (linhas) se não houver vírgula.

### 27.2 Exemplos comparativos (consolidados)

**Array base:**
```python
arrei = np.array([[1, 2, 3, 4],
                  [15, 16, 17, 18],
                  [21, 22, 23, 24]])
```

| CASO | NOTAÇÃO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- | --- |
| Índice + índice | `arrei[1, 2]` | `17` | Simultâneo: linha 1, coluna 2 |
| Índice + índice (sequencial) | `arrei[1][2]` | `17` | Sequencial: linha 1 → depois coluna 2 → **equivalente** |
| Índice + fatiamento | `arrei[1, 1:2]` | `[16]` | Linha 1, colunas 1 a 2 exclusive → array 1D de 1 elemento |
| Índice + fatiamento (sequencial) | `arrei[1][1:2]` | `[16]` | Sequencial: linha 1 → depois fatiamento nas colunas → **equivalente** |
| Fatiamento + índice | `arrei[0:2, 1]` | `[2, 16]` | Linhas 0 e 1, coluna 1 |
| Fatiamento + índice (sequencial) | `arrei[0:2][1]` | `[15, 16, 17, 18]` | Sequencial: linhas 0 e 1 → depois índice 1 (segunda linha do subarray) → **diferente** |
| Fatiamento + fatiamento | `arrei[0:2, 1:3]` | `[[2,3], [16,17]]` | Submatriz 2×2 (linhas 0-1, colunas 1-2) |
| Fatiamento + fatiamento (sequencial) | `arrei[0:2][1:2]` | `[[15,16,17,18]]` | Sequencial: linhas 0 e 1 → depois fatiamento [1:2] (linha 1 apenas) → **diferente** |

> ### 27.2.1 Padrão identificado
> - **Sempre que o primeiro operador for um índice (número inteiro único), as duas formas são equivalentes.**
> - **Sempre que o primeiro operador for um fatiamento (`início:fim` ou `:`), as formas diferem.**

## 28. *Fancy Indexing* (Indexação Avançada)

### 28.1 Conceito

- *Fancy indexing* permite selecionar **posições não contíguas**, **repetir elementos**, ou especificar **ordens arbitrárias** de índices usando **listas** ou **arrays de índices** dentro dos colchetes.
- Também permite o uso de **máscaras booleanas** (arrays de `True`/`False`) para filtrar elementos.

### 28.2 *Fancy indexing* com lista de índices (array 1D)

**Array base:**
```python
arrei = np.array([1, 2, 3, 4, 5, 6, 7, 8])
# índices: 0  1  2  3  4  5  6  7
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0]` | `1` | Índice simples (já conhecido) |
| `arrei[2], arrei[5]` | `3 6` | Acesso separado (não é fancy) |
| `arrei[[0, 2, 5]]` | `[1, 3, 6]` | Lista de índices → fancy indexing |
| `arrei[[7, 0, 3]]` | `[8, 1, 4]` | Ordem arbitrária (7,0,3) |
| `arrei[[1, 1, 1, 4]]` | `[2, 2, 2, 5]` | Índices repetidos permitidos |
| `arrei[range(7, -1, -1)]` | `[8,7,6,5,4,3,2,1]` | `range` gera lista [7,6,5,4,3,2,1,0] → array invertido |

> ### 28.2.1 Vantagem
> - Em uma única operação, seleciona-se múltiplos elementos **não adjacentes** e em **qualquer ordem**, sem necessidade de loops ou concatenações.

### 28.3 *Fancy indexing* com máscara booleana (filtro)

```python
arrei = np.array([1, 2, 3, 4, 5, 6, 7, 8])
mascara = np.array([True, False, True, False, False, True, False, True])
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[mascara]` | `[1, 3, 6, 8]` | Retorna apenas elementos onde a máscara é `True` |
| `arrei[arrei > 4]` | `[5, 6, 7, 8]` | Condição relacional gera máscara booleana automaticamente |
| `arrei[(arrei % 2 == 0) & (arrei > 3)]` | `[4, 6, 8]` | Combinação de condições com `&` (AND). **Atenção:** usar `&` (bitwise) e parênteses, não `and`. |

> ### 28.3.1 Operadores em máscaras booleanas do NumPy
> - **`&`** (AND bitwise) para combinar condições.
> - **`|`** (OR bitwise) para alternativas.
> - **`~`** (NOT) para negação.
> - **Não usar** `and`, `or`, `not` do Python com arrays NumPy (causam `ValueError`).

## 29. *Fancy indexing* em Arrays 2D

### 29.1 Seleção de linhas inteiras por lista de índices

```python
arrei = np.array([[1, 2, 3, 4],
                  [15, 16, 17, 18],
                  [21, 22, 23, 24]])
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[[0, 2]]` | `[[1,2,3,4], [21,22,23,24]]` | Seleciona as linhas 0 e 2 (pula a linha 1) |
| `arrei[[0, 2], 1:3]` | `[[2,3], [22,23]]` | Linhas 0 e 2, e para cada linha, colunas 1 a 3 exclusive (colunas 1 e 2) |

> ### 29.1.1 Cuidado com a diferença
> - `arrei[0, 2]` → **escalar** (linha 0, coluna 2) = `3`.
> - `arrei[[0, 2]]` → **array 2D** com duas linhas (linhas 0 e 2 completas).
> - A presença dos **colchetes internos** (lista) muda completamente a interpretação: de indexação simples para *fancy indexing*.

### 29.2 Combinação de *fancy indexing* com fatiamento

```python
# Linhas 0 e 2 (fancy), colunas 1 a 3 exclusive (fatiamento)
print(arrei[[0, 2], 1:3])   # [[2,3], [22,23]]
```

- A notação mantém a vírgula separando linhas (lista) e colunas (fatiamento).
- O resultado é uma submatriz 2×2.

### 29.3 Equivalências e diferenças (reforço)

| EXPRESSÃO | RESULTADO | TIPO |
| --- | --- | --- |
| `arrei[0][2]` | `3` | índice + índice |
| `arrei[0, 2]` | `3` | índice + índice (vírgula) |
| `arrei[[0, 2]]` | `[[1,2,3,4], [21,22,23,24]]` | fancy (linhas) |
| `arrei[[0, 2], 1:3]` | `[[2,3], [22,23]]` | fancy + fatiamento |

> ### 29.3.1 Observação final do professor
> - *Fancy indexing* é extremamente útil para seleções não triviais e aparece com frequência crescente em concursos mais avançados.
> - A principal armadilha é confundir `arrei[0,2]` (escalar) com `arrei[[0,2]]` (duas linhas). A vírgula e os colchetes internos fazem toda a diferença.

## 30. Síntese de Comportamentos (Checklist para Revisão)

| OPERAÇÃO | NOTAÇÃO | RESULTADO NO ARRAY 1D | RESULTADO NO ARRAY 2D (exemplo) |
| --- | --- | --- | --- |
| Índice simples | `arr[i]` | Escalar | Linha i (array 1D) |
| Índice duplo (sequencial) | `arr[i][j]` | N/A | Escalar (linha i, coluna j) |
| Índice duplo (vírgula) | `arr[i, j]` | N/A | Escalar (linha i, coluna j) |
| Fatiamento simples | `arr[i:j]` | Subarray 1D | Subarray de linhas (2D) |
| Fatiamento + índice (vírgula) | `arr[i:j, k]` | N/A | Subarray 1D (coluna k das linhas i:j) |
| Fatiamento + índice (sequencial) | `arr[i:j][k]` | N/A | Subarray 1D (linha k do subarray de linhas) → **diferente** |
| *Fancy* lista de índices | `arr[[a,b,c]]` | Subarray 1D com índices a,b,c | Subarray 2D com linhas a,b,c |
| *Fancy* + fatiamento | `arr[[a,b], c:d]` | N/A | Subarray 2D (linhas a,b; colunas c:d) |
| Máscara booleana | `arr[mascara]` | Elementos onde `True` | Linhas onde `True` (2D) ou elementos achatados? Depende. |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy VI" (fancy indexing e distinções) – professor Rogério Araújo, Gran Concursos.*