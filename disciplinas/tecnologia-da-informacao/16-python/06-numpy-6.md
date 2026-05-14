# Anotações (Continuação - NumPy VI)

## 21. Fatiamento em Arrays 2D – Sintave com Vírgula vs. Colchetes Sequenciais

### 21.1 Notações fundamentais

| NOTAÇÃO | SIGNIFICADO | EIXOS ATUADOS |
| --- | --- | --- |
| `array[linhas, colunas]` | Fatiamento **simultâneo** (dentro do mesmo par de colchetes, separado por vírgula) | Eixo 0 (linhas) e Eixo 1 (colunas) ao mesmo tempo |
| `array[linhas][colunas]` | Fatiamento **sequencial** (primeiro linhas, depois sobre o resultado aplica-se colunas) | Primeiro opera no eixo 0; o segundo operador atua sobre o **subarray resultante** |

> ### 21.1.1 Distinção crucial (ênfase do professor)
> - **Com vírgula (`array[linhas, colunas]`):** os dois fatiamentos são aplicados **simultaneamente** nos dois eixos da matriz original.
> - **Com colchetes separados (`array[linhas][colunas]`):** o primeiro fatiamento gera um **subarray intermediário**; o segundo fatiamento (ou índice) é aplicado **sobre esse subarray**, **não** diretamente sobre a matriz original.
> - **Os resultados podem ser completamente diferentes.** Esta é uma das pegadinhas mais comuns em concursos.

### 21.2 Array base para todos os exemplos

```python
arrei = np.array([[1, 2, 3, 4],
                  [15, 16, 17, 18],
                  [21, 22, 23, 24]])
# Linhas (eixo 0): índices 0, 1, 2
# Colunas (eixo 1): índices 0, 1, 2, 3
```

## 22. Extração de Linhas e Colunas

### 22.1 Selecionar uma linha inteira

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0,:]` | `[1, 2, 3, 4]` | Linha 0, todas as colunas (fatiamento `:` em colunas) |
| `arrei[1,:]` | `[15, 16, 17, 18]` | Linha 1, todas as colunas |
| `arrei[2]` | `[21, 22, 23, 24]` | Apenas o índice 2 (sem fatiamento) → linha completa (equivalente a `[2,:]`) |
| `arrei[0]` | `[1, 2, 3, 4]` | Índice 0 retorna a primeira linha |

> ### 22.1.1 Observação
> - `arrei[2]` é uma forma abreviada de `arrei[2, :]` quando se omite o fatiamento de colunas.

### 22.2 Selecionar uma coluna inteira (notação correta)

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[:, 0]` | `[1, 15, 21]` | Todas as linhas, coluna 0 (primeira coluna) |
| `arrei[:, 1]` | `[2, 16, 22]` | Todas as linhas, coluna 1 |
| `arrei[:, 2]` | `[3, 17, 23]` | Todas as linhas, coluna 2 |
| `arrei[:, 3]` | `[4, 18, 24]` | Todas as linhas, coluna 3 |

### 22.3 Erro comum: colchetes sequenciais para extrair coluna

```python
# ERRADO (para extrair coluna):
arrei[:][0]   # Isso NÃO retorna a coluna 0.
# O que acontece: arrei[:] retorna a matriz inteira; [0] então retorna a primeira linha [1,2,3,4].

# CORRETO para extrair coluna:
arrei[:, 0]   # Retorna [1, 15, 21]
```

> ### 22.3.1 Por que `arrei[:][0]` ≠ `arrei[:,0]`?
> - `arrei[:]` é um fatiamento **apenas no eixo 0** (linhas) que retorna **todas as linhas** – uma cópia da matriz original.
> - Em seguida, `[0]` indexa esse resultado, obtendo a **primeira linha** da matriz copiada.
> - Já `arrei[:,0]` é um fatiamento **simultâneo** no eixo 0 (todas as linhas) e no eixo 1 (apenas coluna 0).

## 23. Submatrizes e Fatiamento Simultâneo (com vírgula)

### 23.1 Submatriz contínua

```python
print(arrei[0:2, 1:3])
# Linhas: 0 a 1 (exclusive linha 2)
# Colunas: 1 a 2 (exclusive coluna 3)
# Resultado: [[2, 3],
#             [16, 17]]
```

### 23.2 Inversão de colunas em linhas específicas

```python
print(arrei[0:2, ::-1])
# Linhas 0 e 1; colunas em ordem inversa (::-1)
# Resultado: [[4, 3, 2, 1],
#             [18, 17, 16, 15]]
```

### 23.3 Inversão simultânea de linhas e colunas

```python
print(arrei[::-1, ::-1])
# Linhas invertidas (2,1,0) E colunas invertidas (3,2,1,0)
# Resultado: [[24, 23, 22, 21],
#             [18, 17, 16, 15],
#             [4, 3, 2, 1]]
```

### 23.4 Combinando índice com fatiamento parcial (linha + colunas)

```python
print(arrei[1, 0:2])   # Linha 1, colunas 0 e 1 → [15, 16]
print(arrei[2][1:3])   # Linha 2 (índice), depois colunas 1 a 2 → [22, 23]
```

> ### 23.4.1 Equivalência neste caso específico
> - `arrei[1, 0:2]` é equivalente a `arrei[1][0:2]` porque, após selecionar a linha 1 (que é 1D), o fatiamento nas colunas age sobre o array 1D resultante. Mas isso nem sempre vale para fatiamentos em ambos os eixos.

## 24. Distinção Fundamental: Vírgula vs. Colchetes em Sequência

### 24.1 Exemplo comparativo

```python
# CASO 1: Fatiamento simultâneo com vírgula
print(arrei[0:2, 0])   # Resultado: [1, 15]  (coluna 0 das linhas 0 e 1)

# CASO 2: Fatiamento sequencial com colchetes
print(arrei[0:2][0])   # Resultado: [1, 2, 3, 4] (primeira linha do subarray com linhas 0 e 1)
```

| OPERAÇÃO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0:2, 0]` | `[1, 15]` | Simultâneo: linhas 0 e 1, coluna 0 de cada. |
| `arrei[0:2][0]` | `[1, 2, 3, 4]` | Sequencial: `arrei[0:2]` → subarray com linhas 0 e 1; depois `[0]` → primeira linha desse subarray (linha original 0). |

### 24.2 Outro exemplo comparativo

```python
print(arrei[0:2, 1:3])   # Submatriz 2x2: [[2,3], [16,17]]
print(arrei[0:2][1:2])   # Subarray: [[15,16,17,18]] (linha 1 apenas)
```

> ### 24.2.1 Regra de ouro (professor)
> - **Vírgula dentro de um único par de colchetes:** os fatiamentos/índices à esquerda da vírgula atuam no **eixo 0 (linhas)**; os à direita atuam no **eixo 1 (colunas)** – operação **simultânea**.
> - **Colchetes em sequência:** cada novo par de colchetes opera sobre o **resultado da operação anterior** – operação **sequencial**.
> - **Não confundir:** `array[:][0]` **não** é uma forma válida de extrair a coluna 0. Use `array[:,0]`.

### 24.3 Exemplos de fatiamento sequencial já vistos (aula V)

```python
print(arrei[0:2][1])        # Subarray com linhas 0 e 1, depois índice 1 → linha 1: [15,16,17,18]
print(arrei[::-1][0])       # Matriz invertida nas linhas, depois primeira linha → [21,22,23,24]
```

## 25. Quadro Resumo – Fatiamento em Arrays 2D

| OBJETIVO | SINTAXE CORRETA | RESULTADO (sobre a matriz exemplo) |
| --- | --- | --- |
| Matriz completa | `arrei[:,:]` ou `arrei[:]` | Todas as linhas e colunas |
| Primeira linha | `arrei[0,:]` ou `arrei[0]` | `[1, 2, 3, 4]` |
| Última linha | `arrei[-1,:]` ou `arrei[-1]` | `[21, 22, 23, 24]` |
| Primeira coluna | `arrei[:,0]` | `[1, 15, 21]` |
| Última coluna | `arrei[:,-1]` | `[4, 18, 24]` |
| Submatriz (linhas 0-1, colunas 1-2) | `arrei[0:2, 1:3]` | `[[2,3], [16,17]]` |
| Linhas 0 e 2 (pular linha 1) | `arrei[::2, :]` | `[[1,2,3,4], [21,22,23,24]]` |
| Todas as linhas, colunas invertidas | `arrei[:, ::-1]` | `[[4,3,2,1], [18,17,16,15], [24,23,22,21]]` |
| Linhas invertidas, coluna 1 | `arrei[::-1, 1]` | `[22, 16, 2]` (ordem inversa das linhas) |

> ### 25.1 Dica para provas
> - Quando a questão apresentar códigos como `array[:][0]` ou `array[0:2][0]`, desconfie: provavelmente está testando se o candidato sabe que isso **não** equivale a `array[:,0]` ou `array[0:2,0]`.
> - Leia atentamente se a notação utiliza **vírgula dentro dos colchetes** ou **colchetes separados**. A diferença é decisiva para o resultado.

## 26. Exemplos Integrados (da aula)

### 26.1 Extração de coluna via fatiamento simultâneo

```python
# Coluna 0 de todas as linhas
print(arrei[:, 0])   # [1, 15, 21]

# Coluna 1 de todas as linhas
print(arrei[:, 1])   # [2, 16, 22]
```

### 26.2 Fatiamento de linhas com passo negativo e seleção de coluna

```python
# Linhas invertidas, depois coluna 1 (respeitando a nova ordem)
print(arrei[::-1, 1])   # [22, 16, 2]
```

### 26.3 Fatiamento de linhas com passo 2 e seleção de coluna

```python
# Linhas 0 e 2, coluna 2
print(arrei[::2, 2])    # [3, 23]
```

### 26.4 Erro conceitual demonstrado na aula

```python
# ERRADO: tentativa de obter coluna usando fatiamento total seguido de índice
print(arrei[:][0])      # [1, 2, 3, 4] (primeira linha) – NÃO é a coluna 0.
```

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy VI" (professor Rogério Araújo, Gran Concursos).*