# Anotações – Estrutura de Dados – Filas (Conceituação)

## 1. Revisão: Listas e Estruturas Derivadas

### 1.1 Listas (visão geral)

- Listas são coleções de itens dispostos de maneira **sequencial** (ordem lógica).
- Implementações comuns:
  - **Sequencial (estática):** arrays/arranjos/vetores – elementos armazenados em posições contíguas na memória.
  - **Encadeada (dinâmica):** cada elemento possui ponteiro para o próximo (lista simplesmente encadeada) e, opcionalmente, ponteiro para o anterior (lista duplamente encadeada).
- Listas **não possuem restrições** quanto ao local de inserção, remoção ou acesso (pode-se inserir/remover no início, meio ou fim).

### 1.2 Estruturas derivadas especializadas

| ESTRUTURA | PRINCÍPIO | SIGNIFICADO |
| --- | --- | --- |
| **Fila (Queue)** | FIFO | *First In, First Out* – o primeiro elemento inserido é o primeiro a ser removido |
| **Pilha (Stack)** | LIFO | *Last In, First Out* – o último elemento inserido é o primeiro a ser removido |

> ### 1.2.1 Relação com listas
> - Filas e pilhas são **listas especiais** que seguem regras rígidas de inserção e remoção.
> - Também podem ser implementadas de forma **estática** (arrays) ou **dinâmica** (listas encadeadas).

## 2. Filas (Queues) – Conceituação

### 2.1 Definição

- **TAD (Tipo Abstrato de Dados)** – conjunto de dados e operações (semelhante a uma classe de objetos).
- Estrutura de dados do tipo **FIFO** (*First In, First Out*).
- Os elementos são **adicionados no fim** (final da fila) e **removidos do início** (cabeça da fila).

### 2.2 Esquema visual

```
Remoção (dequeue) ← [início]  [elemento 1]  [elemento 2]  [elemento 3]  [fim] ← Inserção (enqueue)
```

- Inserção: direita para esquerda (ou final).
- Remoção: na outra ponta (início).

### 2.3 Princípios equivalentes

| SIGLA | SIGNIFICADO |
| --- | --- |
| FIFO | *First In, First Out* – primeiro a entrar é o primeiro a sair |
| LILO | *Last In, Last Out* – último a entrar é o último a sair |

> ### 2.3.1 Comparação com pilhas
> - Pilhas seguem **LIFO** (*Last In, First Out*) e **FILO** (*First In, Last Out*).

### 2.4 Exemplos de uso no cotidiano

- Controle de documentos para impressão.
- Troca de mensagens entre computadores em rede.
- Atendimento ao público (senhas).
- Fila de processos em sistemas operacionais.

## 3. Implementações de Filas

| TIPO | ESTRUTURA SUBJACENTE | CARACTERÍSTICA |
| --- | --- | --- |
| **Forma estática** | Array / Vetor / Arranjo | Tamanho fixo definido na criação. Necessário controlar capacidade máxima. |
| **Forma dinâmica** | Lista encadeada (simplesmente encadeada) | Tamanho variável, cresce conforme necessidade. |

> ### 3.1 Operações específicas para implementação estática (array)
> - É necessário conhecer a **capacidade máxima** (tamanho do array).
> - Usa-se a operação `isFull()` para verificar se a fila está cheia antes de inserir.

## 4. Operações Básicas de uma Fila

### 4.1 Operações fundamentais

| NOME (genérico) | NOME (português) | DESCRIÇÃO |
| --- | --- | --- |
| `create()` | `criarFila()` | Cria uma fila vazia. |
| `enqueue(x)` | `enfileirar(x)` | Adiciona o elemento `x` após o último elemento da fila (no fim). |
| `dequeue()` | `desenfileirar()` | Remove o elemento que está na primeira posição da fila (início) e o retorna. |

### 4.2 Operações de verificação de estado

| OPERAÇÃO | RETORNO | DESCRIÇÃO |
| --- | --- | --- |
| `isEmpty()` | `true` ou `false` | Retorna `true` se a fila estiver vazia; `false` caso contrário. |
| `isFull()` | `true` ou `false` | Retorna `true` se a fila estiver cheia (implementação estática); `false` caso contrário. `!(isEmpty())` não é suficiente para verificar se está cheia. |

> ### 4.2.1 Exemplo prático (fila estática com 6 posições)
> - Se a fila possui **2 elementos**: `isEmpty()` → `false` (não está vazia); `isFull()` → `false` (ainda há espaço).
> - A operação `isFull()` só é relevante em implementações com **tamanho máximo fixo**.

## 5. Exemplos de Sequências de Operações

### 5.1 Exemplo 1 – Sequência simples

**Operações na ordem:**
1. `criarFila()`
2. `enfileirar(2)`
3. `enfileirar(3)`
4. `desenfileirar()`
5. `enfileirar(1)`
6. `desenfileirar()`
7. `enfileirar(4)`
8. `enfileirar(5)`
9. `desenfileirar()`

**Resolução passo a passo (simulação mental):**

| OPERAÇÃO | ESTADO DA FILA (início → fim) |
| --- | --- |
| `criarFila()` | `[ ]` (vazia) |
| `enfileirar(2)` | `[2]` |
| `enfileirar(3)` | `[2, 3]` |
| `desenfileirar()` | remove `2` → fila: `[3]` |
| `enfileirar(1)` | `[3, 1]` |
| `desenfileirar()` | remove `3` → fila: `[1]` |
| `enfileirar(4)` | `[1, 4]` |
| `enfileirar(5)` | `[1, 4, 5]` |
| `desenfileirar()` | remove `1` → fila: `[4, 5]` |

> ### 5.1.1 Respostas (questões de prova)
> - **Quantos elementos após as operações?** 2 elementos (4 e 5).
> - **Qual a estrutura da fila após as operações?** `[4, 5]` (ou `[5]`? Cuidado: o material original indica `[5]` – provavelmente há erro. Pela simulação correta, após `desenfileirar()` remove o `4`, resta `[5]`. Vamos refazer a última linha: a nona operação é `desenfileirar()`. Antes dela, fila = `[1,4,5]`. Remove o início (1) → fila = `[4,5]`. O material diz "apenas um elemento, o número 5". Isso indica que provavelmente a sequência original do professor tinha `enfileirar(5)` após o último `desenfileirar()`? Ou o último `desenfileirar()` remove o 4? Na verdade, lendo com atenção: 
>   - Após passo 8: `[1,4,5]` (assumindo ordem correta: inserções no fim, remoções no início).
>   - `desenfileirar()` remove o `1`, sobra `[4,5]`. Ainda tem dois elementos.
>   - Talvez o material tenha considerado `desenfileirar()` removendo o `4`? Isso só aconteceria se a fila fosse `[4,5]` e houvesse mais um `desenfileirar()`.
>   - **Conclusão:** siga a lógica FIFO; o gabarito do material aparentemente está inconsistente. Para fins de estudo, a sequência correta leva a `[4,5]`. Se a questão pedir após todas as operações, resultado esperado é `[4,5]`.

### 5.2 Exemplo 2 – com operação `enfileirar(desenfileirar())`

**Operações:**
1. `criarFila()`
2. `enfileirar(2)`
3. `enfileirar(3)`
4. `desenfileirar()`
5. `enfileirar(1)`
6. `enfileirar(desenfileirar())`
7. `enfileirar(5)`
8. `desenfileirar()`
9. `enfileirar(desenfileirar())`

**Simulação:**

| OPERAÇÃO | AÇÃO | ESTADO DA FILA |
| --- | --- | --- |
| 1 | criar | `[]` |
| 2 | enfileirar(2) | `[2]` |
| 3 | enfileirar(3) | `[2,3]` |
| 4 | desenfileirar() | remove `2` → retorna `2` | `[3]` |
| 5 | enfileirar(1) | `[3,1]` |
| 6 | enfileirar(desenfileirar()) | `desenfileirar()` remove `3` → retorna `3`; depois `enfileirar(3)` | `[1,3]` (primeiro remove o 3, fila fica `[1]`; depois insere 3 no fim → `[1,3]`) |
| 7 | enfileirar(5) | `[1,3,5]` |
| 8 | desenfileirar() | remove `1` → retorna `1` | `[3,5]` |
| 9 | enfileirar(desenfileirar()) | `desenfileirar()` remove `3` → retorna `3`; depois `enfileirar(3)` | `[5,3]` (após remoção do 3, fila fica `[5]`; insere 3 no fim → `[5,3]`) |

> ### 5.2.1 Respostas
> - **Quantos elementos após as operações?** 2 elementos.
> - **Quais são os elementos?** `[5, 3]` (primeiro o 5, depois o 3).

## 6. Exemplo em Java (conceitual)

```java
Queue<String> linguagens = new LinkedList<>();
linguagens.add("Java");
linguagens.add("Python");
linguagens.add("PHP");
linguagens.add("C");
String removido = linguagens.poll(); // remove o primeiro (Java)
System.out.println("Linguagens: " + linguagens); // [Python, PHP, C]
System.out.println("Elemento removido: " + removido); // Java
```

- **Resultado da execução:**
  - Linguagens: `[Python, PHP, C]`
  - Elemento removido: `Java`

## 7. Síntese para Provas (pontos-chave)

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **FIFO** | *First In, First Out* – o primeiro que entra é o primeiro que sai. |
| **LILO** | *Last In, Last Out* – sinônimo de FIFO. |
| **Enfileirar (enqueue)** | Insere no **final** da fila. |
| **Desenfileirar (dequeue)** | Remove do **início** da fila. |
| **isEmpty()** | Verifica se a fila está vazia. |
| **isFull()** | Verifica se a fila está cheia (implementação estática com array). |
| **Implementação estática** | Usa array; tamanho fixo; requer `isFull()`. |
| **Implementação dinâmica** | Usa lista encadeada; tamanho variável. |

> ### 7.1 Pegadinha comum
> - Em filas, **o elemento removido por `desenfileirar()` pode ser usado imediatamente como argumento para `enfileirar()`** (ex.: `enfileirar(desenfileirar())`). Nesse caso, a remoção ocorre primeiro, e o valor removido é inserido no final da fila **após a remoção**.

---

*Material baseado na aula do professor Rogério Gildo Araujo (Gran Concursos).*