# Anotações – Estrutura de Dados – Filas (Questões de Concurso)

## 1. Conceitos Essenciais (Revisão)

| ESTRUTURA | PRINCÍPIO (SIGLA) | SIGNIFICADO | INSERÇÃO | REMOÇÃO |
| --- | --- | --- | --- | --- |
| **Fila (Queue)** | FIFO / LILO | First In, First Out / Last In, Last Out | No final (uma ponta) | No início (outra ponta) |
| **Pilha (Stack)** | LIFO / FILO | Last In, First Out / First In, Last Out | No topo (mesma ponta) | No topo (mesma ponta) |
| **Deque (Double-Ended Queue)** | Dupla terminação | Inserção e remoção em ambas as extremidades | Início ou fim | Início ou fim |

> ### 1.1 Pegadinha clássica das bancas
> - **FIFO** → fila (queue). **LIFO** → pilha (stack).
> - **Não confunda:** *push/pop* são operações típicas de pilha, mas se `push` insere numa ponta e `pop` remove da outra ponta, continua sendo fila. O que define é o comportamento (FIFO), não o nome da operação.

## 2. Operações e Nomenclaturas

| OPERAÇÃO | NOMES COMUNS (inglês) | ONDE OCORRE (na fila) |
| --- | --- | --- |
| Inserir | `enqueue`, `add`, `append`, `push` (cuidado!) | No **final** (ou em uma ponta) |
| Remover | `dequeue`, `remove`, `pop(0)`, `poll` | No **início** (ou na ponta oposta) |
| Verificar vazia | `isEmpty()` | – |
| Verificar cheia | `isFull()` (apenas para implementação estática) | – |

> ### 2.1 Exemplo em Python (fila usando lista)
> ```python
> fila = []
> fila.append(10)   # enqueue
> fila.append(20)
> removido = fila.pop(0)   # dequeue (remove do início)
> ```

> ### 2.2 Exemplo em Java (fila usando ArrayList – conceitual)
> ```java
> public void enqueue(ELM s) { lst.add(s); }          // insere no final
> public ELM dequeue() { return lst.remove(0); }      // remove do início
> ```

## 3. Questões Comentadas – Sequências de Operações (FIFO)

### 3.1 Questão CESGRANRIO (Banco do Brasil/2021)

**Sequência de operações:**  
`ENFILEIRAR(8)` → `ENFILEIRAR(9)` → `DESENFILEIRAR()` → `ENFILEIRAR(10)` → `ENFILEIRAR(11)` → `ENFILEIRAR(DESENFILEIRAR())` → `ENFILEIRAR(12)` → `DESENFILEIRAR()` → `ENFILEIRAR(13)` → `DESENFILEIRAR()`

**Resolução passo a passo:**

| # | OPERAÇÃO | AÇÃO | ESTADO DA FILA (início → fim) |
| --- | --- | --- | --- |
| 1 | `ENFILEIRAR(8)` | insere 8 | `[8]` |
| 2 | `ENFILEIRAR(9)` | insere 9 | `[8, 9]` |
| 3 | `DESENFILEIRAR()` | remove 8 | `[9]` |
| 4 | `ENFILEIRAR(10)` | insere 10 | `[9, 10]` |
| 5 | `ENFILEIRAR(11)` | insere 11 | `[9, 10, 11]` |
| 6 | `ENFILEIRAR(DESENFILEIRAR())` | remove o primeiro (9) e insere esse mesmo 9 no final | `[10, 11, 9]` |
| 7 | `ENFILEIRAR(12)` | insere 12 | `[10, 11, 9, 12]` |
| 8 | `DESENFILEIRAR()` | remove 10 | `[11, 9, 12]` |
| 9 | `ENFILEIRAR(13)` | insere 13 | `[11, 9, 12, 13]` |
| 10 | `DESENFILEIRAR()` | remove 11 | `[9, 12, 13]` |

> **Resultado final:** `[9, 12, 13]` (alternativa **b**)

**Gabarito:** **b) 9 – 12 – 13**

---

### 3.2 Questão FCC (Prefeitura de Teresina/2016) – com push/pop

**Sequência:** `Push 3, Push 5, Pop 3, Push 7, Pop 5, Push 9, Push 8`  
*Atenção: aqui `Push` = enfileirar (inserir no fim) e `Pop` = desenfileirar (remover do início). O número após `Pop` é o valor removido (distrator).*

**Simulação:**

| OPERAÇÃO | ESTADO DA FILA |
| --- | --- |
| `Push 3` | `[3]` |
| `Push 5` | `[3, 5]` |
| `Pop 3` (remove o 3) | `[5]` |
| `Push 7` | `[5, 7]` |
| `Pop 5` (remove o 5) | `[7]` |
| `Push 9` | `[7, 9]` |
| `Push 8` | `[7, 9, 8]` |

**Resultado:** `7 – 9 – 8` → alternativa **d**.

**Gabarito:** **d) 7 – 9 – 8**

---

### 3.3 Questão CESGRANRIO (Banco da Amazônia/2014)

**Sequência:** `INSERE(2)` → `INSERE(3)` → `RETIRA()` → `INSERE(1)` → `RETIRA()` → `INSERE(4)` → `INSERE(5)` → `RETIRA()`

**Simulação:**

| OPERAÇÃO | ESTADO |
| --- | --- |
| `INSERE(2)` | `[2]` |
| `INSERE(3)` | `[2, 3]` |
| `RETIRA()` | remove 2 → `[3]` |
| `INSERE(1)` | `[3, 1]` |
| `RETIRA()` | remove 3 → `[1]` |
| `INSERE(4)` | `[1, 4]` |
| `INSERE(5)` | `[1, 4, 5]` |
| `RETIRA()` | remove 1 → `[4, 5]` |

**Resultado final:** `[4, 5]` → alternativa **d**? Cuidado: o gabarito do material indica **e) 5**.  
*Provável erro: o último `RETIRA()` remove o 4, sobrando `[5]` se a fila for `[1,4,5]` → remove 1 → fica `[4,5]`. Se houvesse mais uma remoção, sobraria `[5]`. Mas seguindo a sequência dada, o correto é `[4,5]`. O professor comenta que o resultado é **5** (apenas um elemento), então assuma que a banca considerou que após a última remoção restou `[5]` (talvez a sequência original tenha uma remoção a mais).*

**Gabarito pelo material:** **e) 5**.

---

## 4. Questões sobre Implementação e Classes (Java)

### 4.1 CESGRANRIO (Banco da Amazônia/2021)

A questão apresentava uma classe `Queue` parcial e pedia a implementação correta de `enqueue` e `dequeue` para garantir FIFO, usando um `ArrayList` chamado `lst`.

**Resolução:**  
- `enqueue` deve inserir no **final** → `lst.add(s)`  
- `dequeue` deve remover do **início** → `return lst.remove(0)`

**Alternativa correta:** **b** (a que usava `lst.add(s)` e `lst.remove(0)`).

> ### 4.1.1 Análise das outras opções
> - Opções que inseriram na posição 0 (`lst.add(0,s)`) e removeram do final → comportamento de pilha (ou fila invertida).
> - Opções que inseriram no final e removeram do final → também pilha.
> - Opção que usou `get(0)` (sem remover) → não remove o elemento.

## 5. Questões sobre Deque e Filas Circulares

| ESTRUTURA | CARACTERÍSTICA |
| --- | --- |
| **Deque** | Inserção e remoção em **ambas as extremidades** (dupla terminação). Subclasse de fila. |
| **Fila circular** | Último elemento ligado ao primeiro. Permite aproveitar espaço em implementação com array. |

**Exemplos de questões:**
- CESPE/TRE-BA/2017: a estrutura que amplia a fila permitindo inserir/remover do início e do fim é o **deque** (alternativa c). A questão foi anulada porque **lista duplamente encadeada** também atende, mas o conceito específico é deque.
- FCC/2010: "fila duplamente terminada" → **deque**.
- CESPE/2004: "em uma fila circular, o último elemento é ligado de volta ao primeiro" → **Certo**.

## 6. Questões sobre Aplicações (Fila de Impressão, Atendimento)

| SITUAÇÃO | ESTRUTURA ADEQUADA | POR QUÊ? |
| --- | --- | --- |
| Impressora compartilhada (ordem de chegada) | **Fila** | Primeiro a enviar é o primeiro a imprimir (FIFO) |
| Servidor Web com requisições sequenciais | **Fila** | Processa na ordem de chegada |
| Caixa de banco (atendimento) | **Fila** | FIFO |
| Substituição de página (página mais antiga) | **FIFO** (estrutura) | Remove a página que está há mais tempo |

> ### 6.1 Questão exemplo (FCC/2013 – MPE/MA)
> Ana precisa gerenciar trabalhos de impressão na ordem de envio. Estrutura adequada: **fila (e)**.

## 7. Erros Comuns em Provas (Afirmações Falsas)

| AFIRMAÇÃO (ERRADA) | CORREÇÃO |
| --- | --- |
| "Pilha usa método de inserção FIFO" | Pilha usa LIFO; fila usa FIFO. |
| "Na fila, o primeiro inserido é o último a sair (LIFO)" | Na fila é FIFO; isso é pilha. |
| "Pilha é usada para fila de impressão" | Fila de impressão é fila. |
| "Fila: inserção e remoção na mesma ponta" | Inserção e remoção em pontas opostas. |
| "Deque é o mesmo que fila circular" | Deque é dupla terminação; fila circular é outra especialização. |

## 8. Síntese para Revisão Rápida (Checklist)

- [ ] **FIFO** = fila. **LIFO** = pilha.
- [ ] **Enqueue** = insere no final. **Dequeue** = remove do início.
- [ ] **Deque** = insere/remove em ambas as extremidades.
- [ ] **Fila circular** = último aponta para o primeiro.
- [ ] Implementações possíveis: array (estática) ou lista encadeada (dinâmica).
- [ ] Nomes das operações podem variar (push/pop, append/pop(0), add/remove). O importante é **uma ponta insere, outra remove**.
- [ ] Questões de sequência: simular passo a passo, sempre respeitando FIFO.

---

## Gabarito Consolidado (Questões dos arquivos 3 a 6)

| Questão | Fonte | Gabarito |
| --- | --- | --- |
| 1 (3 questões iniciais) | IUDS/IF-RJ | d |
| 2 | FUNDATEC/PGE-RS | b |
| 3 | CESGRANRIO/BB | b |
| 4 (classe Queue) | CESGRANRIO/BASA | b |
| 1 (arquivo 4) | COPESE/UFPI | a |
| 2 | CESPE/TRT7 | b |
| 3 | CESPE/TRF1 | C |
| 4 | CESPE/TRE-BA | Anulado |
| 5 | SUGEP/UFRPE | C |
| 6 | AOCP/EBSERH | a |
| 7 | IFRS | E |
| 8 | IFPE | E |
| 9 | FGV/Paulínia | a |
| 10 | FCC/TRT23 | b |
| 1 (arquivo 5) | COPESE/UFPI | a |
| 2 | CESPE/TRT7 | b |
| 3 | CESPE/TRF1 | C |
| 4 | CESPE/TRE-BA | Anulado |
| 5 | SUGEP/UFRPE | C |
| 6 | AOCP/EBSERH | a |
| 7 | IFRS | E |
| 8 | IFPE | E |
| 9 | FGV/Paulínia | a |
| 10 | FCC/TRT23 | b |
| 1 (arquivo 6) | FCC/Teresina | d |
| 2 | COMVEST/UFAM | C |
| 3 | CESPE/TCE/PA | C |
| 4 | CESPE/FUB | C |
| 5 | FUNRIO/UFRB | c |
| 6 | FGV/TJ/PI | b |
| 7 | COMPERVE/UFRN | d |
| 8 | CESGRANRIO/BASA | e |
| 9 | FCC/MPE/MA | e |
| 10 | CESPE/CNJ | C |
| 11 | FCC/MPE/AP | c |
| 12 | FCC/MPE/AP | E |
| 13 | FCC/MPE/AP | E |
| 14 | FCC/MPE/AP | E |
| 15 | FCC/TRT22 | d |
| 16 | FCC/MPE/RS | c |
| 17 | CESPE/TRE/AL | C |

---

**Próximos passos:** Se desejar, posso criar um resumo único e compacto sobre **Filas** (teoria + questões) para impressão. Basta pedir. Bons estudos!