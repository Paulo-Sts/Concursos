# Anotações (Continuação - NumPy V)

## 18. Fatiamento (Slicing) com Índices Negativos e Passo Negativo

### 18.1 Regras fundamentais para início, fim e passo

| SITUAÇÃO | CONDIÇÃO | EFEITO |
| --- | --- | --- |
| **Passo positivo** (padrão = 1) | `início < fim` | Percorre da esquerda para a direita (crescente) |
| **Passo negativo** | `início > fim` | Percorre da direita para a esquerda (decrescente) |

> ### 18.1.1 Atenção do professor
> - Com passo positivo, o valor de **início deve ser menor que o valor de fim** para que haja elementos a serem retornados.
> - Com passo negativo, o valor de **início deve ser maior que o valor de fim** (pois o índice será decrementado).

### 18.2 Exemplos com índices negativos e passo negativo

**Array base:**
```python
arrei = np.array(["Python", "Java", "PHP", "C"])
# Índices positivos:   0         1       2     3
# Índices negativos:  -4        -3      -2    -1
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[:-1]` | `['Python', 'Java', 'PHP']` | Do início ao índice -1 exclusive (não inclui 'C') |
| `arrei[-1:-4:-1]` | `['C', 'PHP', 'Java']` | Do índice -1 ao -4 exclusive, passo -1 (decrescente) |
| `arrei[-1:-4:-2]` | `['C', 'Java']` | Do índice -1 ao -4 exclusive, passo -2 (pula um a cada iteração) |
| `arrei[-4:-1]` | `['Python', 'Java', 'PHP']` | Do índice -4 ao -1 exclusive, passo padrão 1 (crescente) |
| `arrei[-4:-1:2]` | `['Python', 'PHP']` | Do índice -4 ao -1 exclusive, passo 2 |

**Equivalência entre índices positivos e negativos (passo negativo):**
```python
arrei[-1:-4:-1]  # equivale a:
arrei[3:0:-1]    # mesmo resultado: ['C', 'PHP', 'Java']
```

> ### 18.2.1 Lógica do passo negativo
> - O índice **início** deve ser **maior** que o índice **fim**.
> - A cada iteração, soma-se o passo (negativo), decrementando o índice.
> - O índice **fim** não é incluído no resultado.

### 18.3 Exemplo com array numérico (revisão)

```python
data = np.array([1, 5, 3, 4, 2, 6, 7])
# Índices:         0  1  2  3  4  5  6
```

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `data[:]` | `[1 5 3 4 2 6 7]` | Todos os elementos |
| `data[0:3]` | `[1 5 3]` | Índices 0, 1, 2 |
| `data[5:2:-1]` | `[6 2 4]` | Índices 5, 4, 3 (passo -1, fim=2 exclusive) |
| `data[::2]` | `[1 3 2 7]` | Índices 0, 2, 4, 6 (passo 2) |
| `data[::-1]` | `[7 6 2 4 3 5 1]` | Todos os elementos em ordem inversa |

## 19. Questão de Concurso Comentada

### 19.1 (CESPE/CEBRASPE/2025/EMBRAPA)

**Item (julgue):** Considere o código a seguir, que utiliza NumPy.

```python
import numpy as np
data = np.array([1, 5, 3, 4, 2, 6, 7])
print(data[:-2])
```

Após a execução desse código, o resultado será `[1 3 2 7]`.

**Gabarito fornecido pelo material:** **Certo**.

> ### 19.1.1 Análise técnica (observação)
> - O código `data[:-2]` seleciona os elementos do início até o índice **-2 exclusive** (índice -2 corresponde ao penúltimo elemento, valor 6).
> - O resultado real de `data[:-2]` é: `[1 5 3 4 2]` (índices 0 a 4).
> - O resultado `[1 3 2 7]` corresponde a `data[::2]` (passo 2 em todo o array).
> - **Portanto, a afirmativa está tecnicamente incorreta.** No entanto, o gabarito do material indica "Certo". Recomenda-se verificar a literalidade da questão na fonte original.

## 20. Fatiamento em Arrays 2D (Bidimensionais)

### 20.1 Sintaxe geral

```python
array[linhas, colunas]
# ou
array[linhas][colunas]
```

- **Eixo 0 (`axis=0`):** linhas (primeira dimensão)
- **Eixo 1 (`axis=1`):** colunas (segunda dimensão)

### 20.2 Exemplo base

```python
arrei = np.array([[1, 2, 3, 4],
                  [15, 16, 17, 18],
                  [21, 22, 23, 24]])
# Linhas:     0       1        2
# Colunas: 0  1  2  3
```

### 20.3 Acesso a elementos específicos (indexação)

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0, 3]` | `4` | Linha 0, coluna 3 |
| `arrei[1][1]` | `16` | Linha 1, coluna 1 (notação separada) |
| `arrei[-1, -4]` | `21` | Última linha, primeira coluna (índice -4) |
| `arrei[-2][-1]` | `18` | Penúltima linha, última coluna |

### 20.4 Fatiamento apenas no eixo 0 (linhas)

| CÓDIGO | RESULTADO | EXPLICAÇÃO |
| --- | --- | --- |
| `arrei[0:2]` | `[[1,2,3,4], [15,16,17,18]]` | Linhas 0 e 1 (fim=2 exclusive) |
| `arrei[:]` | Todas as 3 linhas | Início e fim omitidos |
| `arrei[::-1]` | Linhas na ordem inversa: `[[21,22,23,24], [15,16,17,18], [1,2,3,4]]` | Passo -1 sobre linhas |
| `arrei[:2]` | Mesmo que `[0:2]` | Início padrão 0 |
| `arrei[0:]` | Todas as 3 linhas | Do início ao fim |
| `arrei[::2]` | `[[1,2,3,4], [21,22,23,24]]` | Linhas 0 e 2 (passo 2) |

### 20.5 Encadeamento de fatiamento e indexação

- É possível aplicar um **índice ou fatiamento adicional** sobre o resultado de um primeiro fatiamento.

```python
# Exemplo: arrei[0:2][1]
# Passo 1: arrei[0:2] → subarray com linhas 0 e 1
# Passo 2: [1] aplicado sobre o subarray → linha 1 (segunda linha do subarray)
# Resultado: [15, 16, 17, 18]
```

```python
# Exemplo: arrei[::-1][0]
# Passo 1: arrei[::-1] → subarray com linhas invertidas (2, 1, 0)
# Passo 2: [0] → primeira linha desse subarray (linha original 2)
# Resultado: [21, 22, 23, 24]
```

> ### 20.5.1 Diferenciação importante (professor)
> - **`arrei[0:2, 1]`** seria um fatiamento simultâneo de linhas e colunas (retorna elementos específicos).
> - **`arrei[0:2][1]`** é um fatiamento de linhas **seguido** de uma indexação sobre o resultado – são operações sequenciais, não simultâneas.
> - Provas de concurso podem cobrar essa distinção.

## GABARITO DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/CEBRASPE/2025/EMBRAPA) | C (conforme material do professor) |

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy V" (professor Rogério Araújo, Gran Concursos).*