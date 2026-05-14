# Anotações (Continuação - NumPy IX)

## 37. Iteração sobre Arrays

### 37.1 Iteração com `for` usando `range` e índice

- Utiliza-se `len(arrei)` para obter a quantidade de elementos na **primeira dimensão**.
- `range(len(arrei))` gera sequência de índices de `0` até `len(arrei) - 1`.

```python
arrei = np.array(["Python", "Java", "PHP", "C"])
for i in range(len(arrei)):
    print(arrei[i])
```

- **Aplicabilidade:** útil quando se precisa do índice para manipulação, não apenas do valor.

> ### 37.1.1 Atenção
> - `len(arrei)` em arrays **multidimensionais** retorna apenas o tamanho da primeira dimensão (número de linhas), **não** o total de elementos. Para total de elementos, use `.size`.

### 37.2 Iteração direta com `for` (elemento por elemento)

**Em arrays 1D:**
```python
for i in arrei:
    print(i)
```

- A variável `i` assume cada elemento do array sequencialmente.

**Em arrays 2D (aninhado):**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
for i in arrei:          # i assume cada linha (array 1D)
    for j in i:          # j assume cada elemento da linha
        print(j)
```

- **For externo:** percorre as linhas (primeira dimensão).
- **For interno:** percorre os elementos de cada linha (segunda dimensão).

> ### 37.2.1 Comportamento
> - Quando se itera diretamente sobre um array 2D com `for i in arrei`, `i` é um **array 1D** correspondente a cada linha.
> - Para iterar sobre todos os elementos individualmente sem aninhamento, use `np.nditer()`.

### 37.3 Iteração com `while`

```python
i = 0
while i < len(arrei):
    print(arrei[i])
    i += 1
```

- Funciona de forma análoga ao `for` com `range`, exigindo controle manual do índice.

### 37.4 Compreensão de lista (*list comprehension*)

```python
[print(i) for i in arrei]
```

- Sintaxe concisa, mas **não é a forma mais eficiente** quando se deseja apenas o efeito colateral (impressão). A compreensão de lista cria uma lista de resultados (neste caso, `None` para cada iteração).
- Pode ser aplicada a listas e tuplas do Python também.

> ### 37.4.1 Recomendação do professor
> - Para iteração simples, prefira o loop `for` tradicional. A compreensão de lista é mais adequada para **criar novas listas** a partir de uma existente.

## 38. Iteradores Especializados do NumPy

### 38.1 `np.nditer()`

- Percorre **todos os elementos** de um array de **qualquer dimensionalidade** em uma única estrutura de repetição.
- Oferece controle de ordem, leitura/escrita e suporte a *broadcasting*.
- **Útil quando:** não se deseja usar loops aninhados para arrays multidimensionais.

```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
for i in np.nditer(arrei):
    print(i)
```

**Resultado:** `1 2 3 4 15 16 17 18` (elemento por elemento, na ordem em que estão armazenados em memória).

> ### 38.1.1 Vantagem
> - `np.nditer()` funciona para arrays 1D, 2D, 3D ou mais – **não exige conhecimento prévio do número de dimensões** para iterar sobre todos os elementos.

### 38.2 `np.ndenumerate()`

- Retorna, a cada iteração, uma **tupla com dois elementos**:
  - `id` (ou `índice`): tupla com os índices do elemento em cada dimensão.
  - `valor`: o elemento propriamente dito.

**Exemplo com array 1D:**
```python
arrei = np.array([1, 2, 3, 4])
for id, i in np.ndenumerate(arrei):
    print(id, i)
```
**Resultado:**
```
(0,) 1
(1,) 2
(2,) 3
(3,) 4
```

**Exemplo com array 2D:**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
for id, i in np.ndenumerate(arrei):
    print(id, i)
```
**Resultado:**
```
(0, 0) 1
(0, 1) 2
(0, 2) 3
(0, 3) 4
(1, 0) 15
(1, 1) 16
(1, 2) 17
(1, 3) 18
```

> ### 38.2.1 Utilidade
> - `np.ndenumerate()` é ideal quando se precisa **saber a posição exata** (índices) de cada elemento durante a iteração, sem necessidade de loops aninhados ou cálculos manuais de índice.

## 39. Tamanho do Array – `size` vs `len`

### 39.1 `.size` (atributo do NDArray)

- Retorna a **quantidade total de elementos** do array (produto dos valores de `shape`).
- **Forma mais recomendada** para obter o número total de elementos em arrays NumPy.

### 39.2 `len(array)` (função embutida do Python)

- Retorna o **tamanho da primeira dimensão** (eixo 0) – número de "blocos" principais.
- Em arrays 1D, `len()` equivale a `.size`.
- Em arrays 2D ou superiores, **`len()` retorna apenas o número de linhas**, não o total de elementos.

### 39.3 Exemplos comparativos

**Array 1D:**
```python
arrei = np.array(["Python", "Java", "PHP", "C"])
print(arrei.size)   # 4
print(len(arrei))   # 4 → equivalentes
```

**Array 2D:**
```python
arrei = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])
print(arrei.size)   # 8 (total de elementos)
print(len(arrei))   # 2 (apenas o número de linhas)
```

| FUNÇÃO/ATRIBUTO | RETORNO | QUANDO USAR |
| --- | --- | --- |
| `.size` | Total de elementos (produto das dimensões) | **Sempre** que se quer o número total de elementos |
| `len()` | Tamanho da primeira dimensão (eixo 0) | Útil para saber número de linhas em arrays 2D ou iterar sobre linhas |

> ### 39.3.1 Dica de prova
> - Questões costumam confundir `len()` com `.size` em arrays multidimensionais. **Para NumPy, a forma correta de obter o total de elementos é `.size`.**

## 40. Cópias e Visualizações

### 40.1 Conceitos fundamentais

| CONCEITO | DESCRIÇÃO | COMPORTAMENTO |
| --- | --- | --- |
| **Cópia** (*copy*) | Novo array com **seu próprio buffer de dados** independente. | Alterações na cópia **não afetam** o original; alterações no original **não afetam** a cópia. |
| **Visualização** (*view*) | "Janela" para o **mesmo buffer de dados** do array original. | Alterações em um refletem no outro (compartilham memória). |

> ### 40.1.1 Analogia
> - **Cópia:** fotocópia de um documento – escrever na cópia não altera o original.
> - **Visualização:** óculos escuros – o que se vê é o mesmo objeto, apenas com uma "filtragem".

### 40.2 Cópia profunda com `.copy()`

- O método `.copy()` cria um **novo array independente**, com memória própria.
- **Útil quando:** se deseja modificar dados com segurança sem alterar o array original.

**Exemplo:**
```python
arrei = np.array([1, 2, 3, 4])
x = arrei.copy()      # x é uma cópia independente
arrei[0] = 15         # modifica apenas o array original

print(arrei)          # [15, 2, 3, 4]
print(x)              # [1, 2, 3, 4] → permanece inalterado
```

### 40.3 Identidade de objetos (`id()`)

- `id(arrei)` retorna o endereço de memória (identificador único) do objeto.
- Arrays diferentes (original vs. cópia) têm `id`s distintos, confirmando que são objetos separados.

```python
print(id(arrei))      # ex.: 22585693306288
print(id(x))          # ex.: 22585693302928 → diferente
```

> ### 40.3.1 Dica de prova
> - O conceito de **cópia vs. visualização** é cobrado em questões que envolvem alterações inesperadas em arrays. Quando se atribui um array a uma variável sem `.copy()`, pode ser apenas uma nova referência ao mesmo buffer, não uma cópia independente.
> - **Método `.view()`** cria uma visualização (não abordado detalhadamente neste material, mas é o oposto de `.copy()`). O foco do professor foi na cópia.

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy IX" (professor Rogério Araújo, Gran Concursos).*