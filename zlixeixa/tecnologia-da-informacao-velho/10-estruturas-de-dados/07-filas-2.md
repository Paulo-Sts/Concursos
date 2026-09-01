# Anotações – Estrutura de Dados – Filas (Questões Comentadas)

## 1. Revisão Rápida – Conceitos de Filas

- **Fila (Queue):** estrutura de dados do tipo **FIFO** (*First In, First Out*) – o primeiro elemento inserido é o primeiro a ser removido.
- **Princípio equivalente:** LILO (*Last In, Last Out*) – o último a entrar é o último a sair.
- **Inserção (enqueue/enfileirar):** ocorre sempre no **final** da fila.
- **Remoção (dequeue/desenfileirar):** ocorre sempre no **início** da fila.
- **Implementações possíveis:**
  - **Estática:** usando array/vetor (tamanho fixo; requer `isFull()`).
  - **Dinâmica:** usando lista encadeada (tamanho variável).

> ### 1.1 Comparação com Pilhas
> - **Pilha (Stack):** LIFO (*Last In, First Out*) ou FILO (*First In, Last Out*).
> - Pegadinha comum em provas: confundir FIFO (fila) com LIFO (pilha).

## 2. Operações Básicas (nomes mais comuns)

| OPERAÇÃO | NOME EM INGLÊS | DESCRIÇÃO |
| --- | --- | --- |
| Criar fila | `create()` | Inicializa uma fila vazia. |
| Inserir | `enqueue(x)` | Adiciona `x` no final da fila. |
| Remover | `dequeue()` | Remove e retorna o elemento do início. |
| Verificar se está vazia | `isEmpty()` | Retorna `true` se não houver elementos. |
| Verificar se está cheia | `isFull()` | Usado apenas em implementação estática (array). |

> ### 2.1 Observação sobre nomenclatura
> - As bancas podem usar nomes diferentes (ex.: `append` e `pop(0)` no Python, `add` e `poll` no Java). O que importa é: **inserção em uma ponta, remoção na ponta oposta**.

## 3. Implementação de Fila em Python (exemplo)

```python
linguagens = []                # lista vazia
linguagens.append("Java")      # enqueue
linguagens.append("Python")
linguagens.append("PHP")
linguagens.append("C")
print(linguagens)              # ['Java', 'Python', 'PHP', 'C']
removido = linguagens.pop(0)   # dequeue (remove do início)
print("Removido:", removido)   # Java
print(linguagens)              # ['Python', 'PHP', 'C']
```

- `append` insere no final; `pop(0)` remove do início → comportamento de fila.

## 4. Filas Circulares

- Estrutura onde o **último elemento se liga ao primeiro**, formando um círculo.
- Útil para implementações com array (aproveita espaços ociosos).
- Operações: após chegar ao fim do array, a inserção continua no início (se houver posições livres).

> ### 4.1 Esquema mental
> - Inserção (`enqueue`): adiciona após o último e antes do primeiro.
> - Remoção (`dequeue`): remove o primeiro elemento; o segundo passa a ser o novo primeiro.

## 5. Deques (Double-Ended Queues)

| CARACTERÍSTICA | FILA TRADICIONAL | DEQUE |
| --- | --- | --- |
| Inserção | Apenas em uma ponta (final) | Em ambas as pontas |
| Remoção | Apenas na outra ponta (início) | Em ambas as pontas |
| Nome | *Queue* | *Deque* (Double-Ended Queue) |

- **Deque** = fila de dupla terminação.
- Permite operações `insert_front`, `insert_rear`, `remove_front`, `remove_rear`.
- Exemplo prático: Canal do Panamá (barcos entram e saem por ambas as extremidades).

## 6. Questões de Concurso Comentadas

### 6.1 (INQC/2023/COMDEP/RJ – TÉCNICO EM INFORMÁTICA)

**Item:** Estrutura onde se adiciona itens no fim e remove do início → **fila**.

**Gabarito:** **a) fila**.

**Comentário:** Pilha remove do mesmo lado da inserção (topo); lista duplamente encadeada permite inserção/remoção em qualquer posição.

### 6.2 (FUNDATEC/2023/PREFEITURA DE BALNEÁRIO PINHAL/RS – PROFESSOR II)

**Item:** Estrutura FIFO (first in, first out) → **fila**.

**Gabarito:** **e) Fila**.

**Comentário:** Pilha = LIFO; lista ligada e vetor são formas de implementação, não definem o princípio FIFO.

### 6.3 (FCC/2023/COPERGÁS/PE – ANALISTA DE SISTEMAS)

**Item:** "Pilha (ou queue) é do tipo FIFO..."

**Gabarito:** **Errado**.

**Comentário:** Confunde os termos: **pilha** (stack) = LIFO; **fila** (queue) = FIFO. A afirmação está incorreta.

### 6.4 (CESPE/CEBRASPE/2023/SEPLAN/RR – ANALISTA)

**Item:** "Sempre que houver uma remoção na fila, o elemento removido será aquele que está na estrutura há mais tempo."

**Gabarito:** **Certo**.

**Comentário:** Princípio FIFO: o primeiro a entrar (mais antigo) é o primeiro a sair.

### 6.5 (AVANÇA/SP/2023/CÂMARA MUNICIPAL DE TABOÃO DA SERRA – ANALISTA)

**Item:** Filas são estruturas do tipo **FIFO**.

**Gabarito:** **c) FIFO**.

**Comentário:** FILO é característico de pilhas.

### 6.6 (UFRPE/2022 – TÉCNICO EM TECNOLOGIA DA INFORMAÇÃO)

**Item:** "Filas podem ser implementadas em listas encadeadas ou em vetores."

**Gabarito:** **Certo**.

**Comentário:** Filas (e pilhas) podem ser implementadas de forma estática (vetor) ou dinâmica (lista encadeada).

### 6.7 (QUADRIX/2022/PRODAM/AM – ANALISTA DE TI)

**Item:** Operação que aumenta o tamanho da fila → **enfileirar (enqueue)**.

**Gabarito:** **b) enfileira**.

**Comentário:** `enfileirar` insere novo elemento; `desenfileirar` remove (diminui); `iniciaf` cria; `vaziaf` e `cheiaf` são verificações.

### 6.8 (FGV/2022/SEAD/AP – PROFESSOR DE INFORMÁTICA)

**Item:** Atendimento de caixa de banco é simulado por uma lista do tipo **FIFO**.

**Gabarito:** **b) FIFO**.

**Comentário:** Ordem de chegada = primeiro a entrar é o primeiro a ser atendido. FIFO = fila.

### 6.9 (CESPE/CEBRASPE/2022/BNB – ANALISTA DE SISTEMAS)

**Item:** "Os elementos de uma fila poderão ser retirados somente na ordem inversa em que foram inseridos (last in, first out)."

**Gabarito:** **Errado**.

**Comentário:** Essa é a definição de **pilha** (LIFO). Fila segue FIFO (ordem direta de inserção).

## 7. Síntese para Revisão Rápida

| ESTRUTURA | PRINCÍPIO | INSERÇÃO | REMOÇÃO |
| --- | --- | --- | --- |
| **Fila (Queue)** | FIFO / LILO | No final | No início |
| **Pilha (Stack)** | LIFO / FILO | No topo | No topo |
| **Deque** | Dupla terminação | Em qualquer ponta | Em qualquer ponta |

> ### 7.1 Pegadinhas frequentes
> - **FIFO** → fila (first in, first out).
> - **LIFO** → pilha (last in, first out).
> - **FILO** → também pilha (first in, last out).
> - **LILO** → também fila (last in, last out).
> - Confundir os nomes em inglês: *queue* (fila) vs. *stack* (pilha).

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (INQC/2023) | a |
| 02 (FUNDATEC/2023) | e |
| 03 (FCC/2023) | E |
| 04 (CESPE/2023) | C |
| 05 (AVANÇA/2023) | c |
| 06 (UFRPE/2022) | C |
| 07 (QUADRIX/2022) | b |
| 08 (FGV/2022) | b |
| 09 (CESPE/2022) | E |

---

*Material baseado na aula do professor Rogério Gildo Araujo (Gran Concursos).*