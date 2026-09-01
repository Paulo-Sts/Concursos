# Anotações (Continuação - NumPy XII)

## 49. Empilhamento com `np.stack()` – Criando Nova Dimensão

### 49.1 Diferença fundamental entre `concatenate` e `stack`

| MÉTODO | COMPORTAMENTO | NÚMERO DE DIMENSÕES DO RESULTADO |
| --- | --- | --- |
| `np.concatenate()` | Junta arrays **ao longo de um eixo existente** | **Mantém** o mesmo `ndim` dos arrays de entrada |
| `np.stack()` | **Empilha** arrays **criando uma nova dimensão** | **Aumenta** `ndim` em 1 em relação aos arrays de entrada |

> ### 49.1.1 Condição para `stack`
> - Todos os arrays a serem empilhados devem ter **o mesmo `shape`**.
> - A nova dimensão é inserida no eixo especificado por `axis` (padrão = 0).

### 49.2 Exemplos com arrays 1D

```python
arrei1 = np.array([1, 2, 3, 4])   # shape (4,), ndim=1
arrei2 = np.array([15, 16, 17, 18])  # shape (4,), ndim=1

# CONCATENATE: mantém 1D
arrei_conc = np.concatenate((arrei1, arrei2))
print(arrei_conc)   # [1 2 3 4 15 16 17 18] → shape (8,), ndim=1

# STACK: cria nova dimensão (padrão axis=0)
arrei_stack = np.stack((arrei1, arrei2))
print(arrei_stack)  # [[1 2 3 4]
                    #  [15 16 17 18]] → shape (2, 4), ndim=2
```

- `concatenate` → resultado **1D** (elementos em sequência).
- `stack` → resultado **2D** (cada array original torna-se uma linha).

### 49.3 Exemplos com arrays 2D e efeito do `axis`

**Arrays base (ambos 2D, shape (1,4)):**
```python
arrei1 = np.array([[1, 2, 3, 4]])    # shape (1,4)
arrei2 = np.array([[15, 16, 17, 18]]) # shape (1,4)
```

| OPERAÇÃO | RESULTADO | `ndim` | `shape` |
| --- | --- | --- | --- |
| `np.concatenate((arrei1, arrei2))` | `[[1,2,3,4], [15,16,17,18]]` | 2 | (2,4) |
| `np.stack((arrei1, arrei2), axis=0)` | `[[[1,2,3,4]], [[15,16,17,18]]]` | 3 | (2,1,4) |
| `np.stack((arrei1, arrei2), axis=1)` | `[[[1,2,3,4], [15,16,17,18]]]` | 3 | (1,2,4) |

> ### 49.3.1 Interpretação
> - `axis=0`: nova dimensão no início (empilha os arrays como blocos separados).
> - `axis=1`: nova dimensão entre as existentes (intercala os arrays ao longo do eixo 1).

### 49.4 Parâmetro `axis` em `stack` com múltiplos arrays

**Exemplo com três arrays 1D (cada um shape (4,)):**
```python
arrei1 = np.array([1, 2, 3, 4])
arrei2 = np.array([15, 16, 17, 18])
arrei3 = np.array([21, 22, 23, 24])

# axis=0 (padrão): empilha como linhas
stack0 = np.stack((arrei1, arrei2, arrei3), axis=0)
# shape (3, 4) → 3 linhas, 4 colunas
# [[1 2 3 4]
#  [15 16 17 18]
#  [21 22 23 24]]

# axis=1: empilha como colunas (cada array vira uma coluna)
stack1 = np.stack((arrei1, arrei2, arrei3), axis=1)
# shape (4, 3) → 4 linhas, 3 colunas
# [[1 15 21]
#  [2 16 22]
#  [3 17 23]
#  [4 18 24]]
```

- **`axis=0`**: a nova dimensão organiza os arrays **um abaixo do outro** (como linhas).
- **`axis=1`**: a nova dimensão organiza os arrays **lado a lado** (como colunas).

### 49.5 `stack` com arrays 2D – exemplo consolidado

```python
arrei1 = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])  # shape (2,4)
arrei2 = np.array([[21, 22, 23, 24], [36, 37, 38, 39]]) # shape (2,4)

# axis=0: empilha os arrays inteiros → shape (2,2,4)
stack0 = np.stack((arrei1, arrei2), axis=0)
# Resultado: primeiro bloco = arrei1, segundo bloco = arrei2

# axis=1: intercala as linhas dos arrays → shape (2,2,4)
stack1 = np.stack((arrei1, arrei2), axis=1)
# Resultado: [[[1,2,3,4], [21,22,23,24]],
#             [[15,16,17,18], [36,37,38,39]]]
```

- Em ambos os casos, o `ndim` vai de 2 para 3.
- O produto dos elementos do `shape` permanece constante (2×2×4 = 16 elementos).

> ### 49.5.1 Regra prática
> - `stack` **sempre** aumenta o número de dimensões em 1.
> - O eixo escolhido (`axis`) determina onde a nova dimensão será inserida na tupla `shape`.

## 50. Funções Auxiliares Especializadas: `vstack` e `hstack`

### 50.1 `np.vstack()` – *Vertical Stack*

- Empilha arrays **verticalmente** (um abaixo do outro), **aumentando o número de linhas**.
- Mantém o número de dimensões (diferente do `stack` geral, que cria nova dimensão – cuidado!).
- Equivalentes:
  - Para arrays 2D com mesmo número de colunas, `vstack` equivale a `concatenate` com `axis=0`.
  - Para arrays 1D, `vstack` primeiro os transforma em arrays 2D de linha (shape (1, n)) e depois empilha.

**Exemplo com array 2D:**
```python
arrei1 = np.array([[1, 2, 3, 4], [15, 16, 17, 18]])  # shape (2,4)
nova_linha = np.array([[30, 31, 33, 34]])            # shape (1,4)

resultado_vstack = np.vstack((arrei1, nova_linha))
# shape (3,4)
# [[1 2 3 4]
#  [15 16 17 18]
#  [30 31 33 34]]

# Equivalente a:
resultado_concatenate = np.concatenate((arrei1, nova_linha), axis=0)
```

> ### 50.1.1 Relação entre `vstack` e `concatenate`
> - Para arrays **2D** com mesmo número de colunas: `vstack` ≡ `concatenate` com `axis=0`.
> - Para arrays **1D**: `vstack` converte cada array em linha (shape (1, n)) antes de empilhar, resultando em array 2D. O `concatenate` com `axis=0` manteria 1D (se ambos fossem 1D). Portanto, **não são equivalentes** para 1D.

**Exemplo com arrays 1D:**
```python
a = np.array([1,2,3])
b = np.array([4,5,6])
print(np.vstack((a,b)))  # [[1 2 3], [4 5 6]] → shape (2,3), ndim=2
print(np.concatenate((a,b)))  # [1 2 3 4 5 6] → shape (6,), ndim=1
```

### 50.2 `np.hstack()` – *Horizontal Stack*

- Empilha arrays **horizontalmente** (lado a lado), **aumentando o número de colunas**.
- Mantém o número de dimensões (exceto quando arrays 1D são misturados com 2D).

**Exemplo (2D):**
```python
arrei1 = np.array([[1,2,3,4], [15,16,17,18]])  # shape (2,4)
nova_coluna = np.array([[21], [22]])            # shape (2,1)
resultado_hstack = np.hstack((arrei1, nova_coluna))
# shape (2,5)
# [[1 2 3 4 21]
#  [15 16 17 18 22]]
```

> ### 50.2.1 Relação com `concatenate`
> - Para arrays **2D** com mesmo número de linhas: `hstack` ≡ `concatenate` com `axis=1`.
> - Para arrays 1D, `hstack` apenas os concatena em um único array 1D (não cria nova dimensão), o que é equivalente a `concatenate` com `axis=0`.

## 51. Tabela Comparativa – `concatenate`, `stack`, `vstack`, `hstack`

| FUNÇÃO | AUMENTA `ndim`? | EQUIVALÊNCIA | TÍPICO USO |
| --- | --- | --- | --- |
| `np.concatenate(..., axis=0)` | Não | `vstack` para arrays 2D | Juntar ao longo de eixo existente |
| `np.concatenate(..., axis=1)` | Não | `hstack` para arrays 2D | Juntar ao longo de outro eixo |
| `np.stack(..., axis=0)` | **Sim** (+1) | – | Criar nova dimensão (ex.: empilhar imagens) |
| `np.vstack(...)` | Pode (1D → 2D) | `concatenate axis=0` para 2D | Empilhar linhas (vertical) |
| `np.hstack(...)` | Não (para 1D) | `concatenate axis=1` para 2D | Empilhar colunas (horizontal) |

> ### 51.1 Dica de prova
> - Questões costumam confundir `stack` com `concatenate`. Lembre-se: **`stack` cria nova dimensão**; **`concatenate` mantém as dimensões**.
> - `vstack` e `hstack` são atalhos semânticos, mas seus comportamentos com arrays 1D merecem atenção (principalmente `vstack`, que transforma 1D em 2D).

---

*Material complementar à aula "Python para Análise de Dados/IA - NumPy XII" (professor Rogério Araújo, Gran Concursos).*