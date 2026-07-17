# Anotações (Continuação – Estruturas de Dados)

## 10. Listas Duplamente Encadeadas (Doubly Linked Lists)

### 10.1 Conceituação

- Cada elemento (nó) possui **três componentes**:
  - Espaço para armazenamento da **informação** (dado).
  - Espaço para armazenamento da **referência do próximo elemento** da lista (`next`).
  - Espaço para armazenamento da **referência do elemento anterior** da lista (`prev`).
- Permite a **travessia bidirecional** – é possível percorrer a lista tanto do início para o fim quanto do fim para o início.
- Tanto o **primeiro** quanto o **último** elemento apontam para `null` (ou `None`, ou `0`).

> ### 10.1.1 Representação
> ```
> null ← [ Dados | Prev | Next ] → [ Dados | Prev | Next ] → [ Dados | Prev | Next ] → null
> ```
> Ou, de forma mais esquemática:
> ```
> [ prev | info | next ] <-> [ prev | info | next ] <-> [ prev | info | next ]
> ```

### 10.2 Vantagens e Desvantagens em relação à Lista Simplesmente Encadeada

| CRITÉRIO | LISTA SIMPLESMENTE ENCADEADA | LISTA DUPLAMENTE ENCADEADA |
| --- | --- | --- |
| **Travessia** | Unidirecional (apenas do início para o fim) | Bidirecional (início → fim e fim → início) |
| **Inserção/Remoção em posição conhecida** | O(1) com ponteiro para o anterior | O(1) com ponteiro para o nó (mais flexível) |
| **Remoção do último nó** | Necessário percorrer até o penúltimo – O(n) | Direta se houver ponteiro para o fim – O(1) |
| **Memória adicional** | 1 ponteiro por nó | 2 ponteiros por nó (mais overhead) |
| **Complexidade de implementação** | Mais simples | Mais complexa (manter dois ponteiros) |

> ### 10.2.1 Diferencial (questão VUNESP/2014)
> - Em uma lista duplamente encadeada, os dois ponteiros apontam, genericamente, para a **célula anterior** e para a **próxima célula**.

### 10.3 Operações em Listas Duplamente Encadeadas

#### 10.3.1 Estrutura do nó

| CAMPO | DESCRIÇÃO |
| --- | --- |
| `prev` (anterior) | Ponteiro para o nó anterior (ou `null` se for o primeiro) |
| `info` (dado) | Valor armazenado |
| `next` (próximo) | Ponteiro para o próximo nó (ou `null` se for o último) |

#### 10.3.2 Criação do primeiro elemento
- Aloca-se um novo nó.
- `prev = null`
- `info = valor`
- `next = null`
- Os ponteiros `head` (início) e `tail` (fim) apontam para este nó.

#### 10.3.3 Inserção no início
- Cria-se um novo nó.
- `new_node.prev = null`
- `new_node.next = head`
- Se a lista não estiver vazia: `head.prev = new_node`
- `head = new_node`
- **Custo:** O(1).

#### 10.3.4 Inserção no final
- Cria-se um novo nó.
- `new_node.prev = tail`
- `new_node.next = null`
- Se a lista não estiver vazia: `tail.next = new_node`
- `tail = new_node`
- **Custo:** O(1) se houver ponteiro para o fim (`tail`).

#### 10.3.5 Inserção no meio (após um determinado nó)
- Localiza-se o nó de referência (`current`).
- `new_node.prev = current`
- `new_node.next = current.next`
- Se `current.next` não for `null`: `current.next.prev = new_node`
- `current.next = new_node`
- **Custo:** O(n) para localização + O(1) para inserção.

#### 10.3.6 Acesso a um elemento
- Pode ser feito do início ou do fim (dependendo da posição alvo – otimização possível).
- Ainda assim, no pior caso, é O(n).

#### 10.3.7 Remoção no início
- `head = head.next`
- Se `head` não for `null`: `head.prev = null`
- O nó removido é desalocado.
- **Custo:** O(1).

#### 10.3.8 Remoção no final
- `tail = tail.prev`
- Se `tail` não for `null`: `tail.next = null`
- O nó removido é desalocado.
- **Custo:** O(1) (com ponteiro para o fim).

#### 10.3.9 Remoção no meio (remoção de um nó específico)
- Se o nó a ser removido (`current`) for o primeiro: aplicar remoção no início.
- Se for o último: aplicar remoção no final.
- Caso contrário:
  - `current.prev.next = current.next`
  - `current.next.prev = current.prev`
  - Desaloca `current`.
- **Custo:** O(1) após localizar o nó (localização é O(n)).

> ### 10.3.10 Exemplo de remoção do meio (questão FCC/2011)
> - Lista com 3 itens ligados duplamente.
> - Para remover o **segundo elemento**:
>   - Ponteiro `next` do **primeiro** deve apontar para o **terceiro**.
>   - Ponteiro `prev` do **terceiro** deve apontar para o **primeiro**.
> - O segundo elemento é desalocado.

### 10.4 Representação com Quádrupla (questões FGV)

- Algumas bancas representam cada nó de uma lista duplamente encadeada como uma quádrupla ou tupla:
  - `<id>, <id do anterior>, <id do seguinte>, <conteúdo>`
- O valor `0` (zero) geralmente representa `null` (ausência de ponteiro).

**Exemplo (FGV/2021/TJ/RO):**
```
(1, 3, 0, "Verde")
(2, 4, 3, "Azul")
(3, 2, 1, "Amarelo")
(4, 0, 2, "Vermelho")
```

**Análise:**
- Quem tem anterior `0`? Elemento `4` (Vermelho) → primeiro da lista.
- A partir dele: `id 4` tem seguinte `2` → Azul.
- `id 2` tem seguinte `3` → Amarelo.
- `id 3` tem seguinte `1` → Verde (e seguinte `0`, então Verde é o último).
- **Ordem:** Vermelho (4), Azul (2), Amarelo (3), Verde (1).

> ### 10.4.1 Método para resolver
> 1. Encontrar o elemento com **anterior = 0** (primeiro).
> 2. Percorrer pelos campos "seguinte" até encontrar `0` (fim).

## 11. Questões de Concurso Comentadas

### 11.1 (FGV/2021/TJ/RO – ANALISTA JUDICIÁRIO)

**Item:** Lista duplamente encadeada representada por quádruplas (id, anterior, seguinte, conteúdo). Determinar a ordem dos conteúdos.

**Resolução:** Conforme análise acima: Vermelho, Azul, Amarelo, Verde.

**Gabarito:** **e) Vermelho, Azul, Amarelo, Verde**.

### 11.2 (FGV/2018/MPE/AL – ANALISTA DE BANCO DE DADOS)

**Tabela com nós (Nó, Time, Anterior, Posterior):**

| Nó | Time | Anterior | Posterior |
| --- | --- | --- | --- |
| 1 | Real Madrid | 4 | 2 |
| 2 | Roma | 1 | - |
| 3 | Barcelona | - | 5 |
| 4 | Bayern | 5 | 1 |
| 5 | Chelsea | 3 | 4 |

**Análise:**
- Quem tem anterior `-` (null)? **Nó 3 (Barcelona)** → primeiro.
- Seguindo: Barcelona (3) → posterior 5 (Chelsea) → posterior 4 (Bayern) → posterior 1 (Real Madrid) → posterior 2 (Roma) e posterior `-` (fim).
- **Ordem:** Barcelona, Chelsea, Bayern, Real Madrid, Roma.

**Gabarito:** **a) Barcelona, Chelsea, Bayern, Real Madrid, Roma**.

### 11.3 (FGV/2016/SEE/PE – PROFESSOR DE DESENVOLVIMENTO DE SISTEMAS)

**Tabela (Elemento, Anterior, Valor, Próximo):**

| Elemento | Anterior | Valor | Próximo |
| --- | --- | --- | --- |
| 1 | 4 | Santos | 2 |
| 2 | 2 | São Paulo | 3 |
| 3 | 3 | São Caetano | 5 |
| 4 | - | Cruzeiro | 1 |
| 5 | 5 | Coritiba | - |

**Análise (trata-se de uma fila implementada como lista encadeada – a questão usa “fila” mas a estrutura é de lista com ponteiros):**
- Quem tem anterior `-`? **Elemento 4 (Cruzeiro)** → primeiro.
- Cruzeiro (4) → próximo 1 (Santos) → próximo 2 (São Paulo) → próximo 3 (São Caetano) → próximo 5 (Coritiba) → próximo `-` (fim).
- **Ordem:** Cruzeiro (1º), Santos (2º), São Paulo (3º), São Caetano (4º), Coritiba (5º).

**Terceiro lugar:** São Paulo.

**Gabarito:** **e) São Paulo**.

### 11.4 (FGV/2015/TCE/SE – ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

**Tabela (Elemento, Anterior, Seguinte, Cor) – ordem correta: Marrom-Verde-Azul-Vermelho-Amarelo.**

| Elemento | Anterior | Seguinte | Cor |
| --- | --- | --- | --- |
| 1 | 4 | 2 | ? |
| 2 | 1 | 3 | ? |
| 3 | 2 | 5 | ? |
| 4 | 5 | 1 | ? |
| 5 | 3 | 4 | ? |

**Resolução:**
- A ordem correta é linear: Marrom → Verde → Azul → Vermelho → Amarelo.
- Atribuindo posições: Marrom (pos1), Verde (pos2), Azul (pos3), Vermelho (pos4), Amarelo (pos5).
- A ordem na tabela (segundo os ponteiros) deve corresponder à ordem natural. Percorrendo a partir de quem tem anterior `null` (não há, pois é circular? A tabela tem Anterior 5 e 4 etc. – na verdade é uma lista duplamente encadeada não circular, então quem tem anterior `-`? Nenhum? Vamos analisar os ponteiros: Elemento 4 tem anterior 5 e seguinte 1; Elemento 1 tem anterior 4 e seguinte 2; Elemento 2 tem anterior 1 e seguinte 3; Elemento 3 tem anterior 2 e seguinte 5; Elemento 5 tem anterior 3 e seguinte 4. Isso forma um ciclo? Anterior/Seguinte formam um ciclo fechado? 4→1→2→3→5→4. É uma lista **circular**. O enunciado diz "lista duplamente encadeada", não especifica circular. A ordem pedida é a sequência linear. O gabarito indica que a ordem na tabela (cima para baixo) deve ser Azul, Vermelho, Amarelo, Verde, Marrom. A partir daí, ajusta-se.

Pelo gabarito do material: **d) Azul-Vermelho-Amarelo-Verde-Marrom**.

### 11.5 (VUNESP/2014/TJ/PA – ANALISTA JUDICIÁRIO)

**Item:** Em uma Lista Duplamente Ligada, os dois ponteiros apontam para a **célula anterior e para a próxima célula**.

**Gabarito:** **a) célula anterior e para a próxima célula**.

### 11.6 (FUMARC/2014/AL/MG – ANALISTA DE SISTEMAS)

**Figura de uma estrutura circular duplamente encadeada.** Questiona qual característica **NÃO** pertence.

**Alternativa incorreta (exceção):** **b) O último elemento inserido é sempre o primeiro a ser retirado da estrutura**.

**Comentário:** Essa é a característica de uma **pilha (LIFO)** , não de uma lista duplamente encadeada (que é uma estrutura linear genérica, não necessariamente LIFO ou FIFO).

### 11.7 (FCC/2011/INFRAERO – ANALISTA DE DESENVOLVIMENTO)

**Item:** Lista duplamente ligada com 3 itens. Para retirar o segundo elemento:

**Alternativa correta:** **b) ponteiro `next` do item 1 deve conter o endereço do item 3 e o ponteiro `prev` do item 3 deve conter o endereço do item 1**.

**Comentário:** Após a remoção, o primeiro item aponta para o terceiro, e o terceiro aponta de volta para o primeiro.

### 11.8 (FCC/2010/DPE-SP – AGENTE DE DEFENSORIA)

**Item:** Estrutura de dados com três campos: dois ponteiros e campo de informação → **lista encadeada dupla**.

**Gabarito:** **a) lista encadeada dupla**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/2021/TJ/RO) | e |
| 02 (FGV/2018/MPE/AL) | a |
| 03 (FGV/2016/SEE/PE) | e |
| 04 (FGV/2015/TCE/SE) | d |
| 05 (VUNESP/2014/TJ/PA) | a |
| 06 (FUMARC/2014/AL/MG) | b |
| 07 (FCC/2011/INFRAERO) | b |
| 08 (FCC/2010/DPE-SP) | a |

---

*Material complementar à aula "Estruturas de Dados – Listas Duplamente Encadeadas" (professor Rogério Araújo, Gran Concursos).*