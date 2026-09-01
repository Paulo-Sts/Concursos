# Anotações – Estrutura de Dados – Pilhas (Teoria)

## 1. Revisão Rápida: Filas vs. Pilhas

Antes de iniciar o estudo de pilhas, é importante relembrar as filas para fixar a diferença:

| ESTRUTURA | PRINCÍPIO | SIGNIFICADO | INSERÇÃO | REMOÇÃO |
| --- | --- | --- | --- | --- |
| **Fila (Queue)** | FIFO / LILO | First In, First Out / Last In, Last Out | Em uma ponta (final) | Na outra ponta (início) |
| **Pilha (Stack)** | LIFO / FILO | Last In, First Out / First In, Last Out | No topo (mesma ponta) | No topo (mesma ponta) |

> ### 1.1 Analogias para fixar
> - **Fila:** caixa de banco. A pessoa mais antiga na fila é a primeira a ser atendida. O último da fila será o último atendido.
> - **Pilha:** pilha de pratos sujos. Você sempre começa a lavar pelo último prato que foi colocado no topo. O último prato que entrou é o primeiro a ser lavado.

## 2. Conceituação de Pilhas

### 2.1 Definição

- **Pilha (Stack)** – Tipo Abstrato de Dados (TAD) que armazena dados e oferece operações específicas.
- Estrutura de dados do tipo **LIFO** (*Last In, First Out*): o último elemento a ser inserido será o primeiro a ser retirado.
- Os elementos são **adicionados no topo** e **removidos do topo**.

### 2.2 Acesso restrito

- Permite acesso apenas a um item de dados por vez: o **topo** (último elemento inserido).
- Para processar o penúltimo elemento, é necessário remover o último antes.

### 2.3 Esquema visual

```
      TOPO
       ↓
┌─────────────┐
│     5       │  ← último inserido (primeiro a sair)
├─────────────┤
│     3       │
├─────────────┤
│     2       │
├─────────────┤
│     1       │  ← primeiro inserido (último a sair)
└─────────────┘
```

## 3. Princípios Equivalentes

| PRINCÍPIO | SIGNIFICADO | ESTRUTURA |
| --- | --- | --- |
| **LIFO** | *Last In, First Out* – último a entrar, primeiro a sair | Pilha |
| **FILO** | *First In, Last Out* – primeiro a entrar, último a sair | Pilha |
| **FIFO** | *First In, First Out* – primeiro a entrar, primeiro a sair | Fila |
| **LILO** | *Last In, Last Out* – último a entrar, último a sair | Fila |

> ### 3.1 Atenção (pegadinha)
> - **LIFO e FILO são princípios equivalentes** para pilhas (apenas formas diferentes de descrever o mesmo comportamento).
> - Bancas podem tentar confundir: LIFO é pilha; FIFO é fila.

## 4. Exemplos de Uso de Pilhas

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Funções recursivas** | Em compiladores, quando uma função chama a si mesma. As chamadas são empilhadas. |
| **Mecanismo desfazer/refazer (Undo/Redo)** | Editores de texto (ex.: Ctrl+Z). As ações são empilhadas; desfazer remove a última ação. |
| **Navegação entre páginas web** | Botão "voltar" utiliza pilha de páginas visitadas. |
| **Avaliação de expressões** | Conversão de notação infixa para pós-fixa (RPN). |

## 5. Implementações de Pilhas

| TIPO | ESTRUTURA SUBJACENTE | CARACTERÍSTICA |
| --- | --- | --- |
| **Forma estática** | Array / Vetor / Arranjo | Tamanho fixo definido na criação; requer `isFull()`. |
| **Forma dinâmica** | Lista encadeada (simplesmente encadeada) | Tamanho variável, cresce conforme necessidade. |

## 6. Operações Básicas de uma Pilha

### 6.1 Operações fundamentais

| NOME (inglês) | NOME (português) | DESCRIÇÃO |
| --- | --- | --- |
| `create()` | `criarPilha()` | Cria uma pilha vazia. |
| `push(x)` | `empilhar(x)`, `inserir(x)` | Adiciona o elemento `x` no **topo** da pilha. Recebe o elemento como parâmetro. |
| `pop()` | `desempilhar()`, `retirar()` | Remove o elemento do **topo** da pilha e o retorna. **Não precisa de parâmetro** (só pode remover do topo). |
| `top()` | `topo()` | Retorna o elemento do topo **sem removê-lo** (operação de leitura/consulta). |
| `isEmpty()` | `estaVazia()` | Retorna `true` se a pilha estiver vazia; `false` caso contrário. |
| `isFull()` | `estaCheia()` | Retorna `true` se a pilha estiver cheia (apenas para implementação estática com array). |

> ### 6.1.1 Destaque do professor
> - O método `pop()` não precisa de parâmetro porque, em uma pilha, **só se pode remover o elemento do topo**. Não há escolha de qual elemento remover.
> - `push(x)` sempre insere no topo.

## 7. Exemplos de Sequências de Operações

### 7.1 Exemplo 1 (sequência simples)

**Operações na ordem:**
1. `criarPilha()`
2. `push(2)`
3. `push(3)`
4. `pop()`
5. `push(1)`
6. `pop()`
7. `push(4)`
8. `push(5)`
9. `pop()`

**Simulação passo a passo:**

| OPERAÇÃO | AÇÃO | PILHA (base → topo) |
| --- | --- | --- |
| `criarPilha()` | inicializa | `[ ]` |
| `push(2)` | insere 2 | `[2]` |
| `push(3)` | insere 3 | `[2, 3]` (topo = 3) |
| `pop()` | remove topo (3) | `[2]` |
| `push(1)` | insere 1 | `[2, 1]` (topo = 1) |
| `pop()` | remove topo (1) | `[2]` |
| `push(4)` | insere 4 | `[2, 4]` (topo = 4) |
| `push(5)` | insere 5 | `[2, 4, 5]` (topo = 5) |
| `pop()` | remove topo (5) | `[2, 4]` (topo = 4) |

> **Resultado final:** pilha com 2 elementos: `[2, 4]` (base=2, topo=4).

### 7.2 Exemplo 2 (com `push(pop())`)

**Operações:**
1. `criarPilha()`
2. `push(2)`
3. `push(3)`
4. `pop()`
5. `push(1)`
6. `push(pop())`   → primeiro remove o topo, depois insere esse mesmo valor no topo
7. `push(5)`
8. `pop()`
9. `push(pop())`

**Simulação:**

| OPERAÇÃO | AÇÃO | PILHA |
| --- | --- | --- |
| `criarPilha()` | – | `[]` |
| `push(2)` | insere 2 | `[2]` |
| `push(3)` | insere 3 | `[2, 3]` |
| `pop()` | remove 3 | `[2]` |
| `push(1)` | insere 1 | `[2, 1]` |
| `push(pop())` | remove topo (1), depois insere 1 | `[2, 1]` (o 1 sai e volta) – na prática, a pilha não se altera, mas houve remoção e reinserção. Cuidado: o correto é que o elemento removido é o 1, e ele é reinserido no topo. Então permanece `[2, 1]`. |
| `push(5)` | insere 5 | `[2, 1, 5]` |
| `pop()` | remove 5 | `[2, 1]` |
| `push(pop())` | remove topo (1), depois insere 1 | `[2, 1]` (novamente permanece igual) |

> **Resultado final:** `[2, 1]` (dois elementos; topo = 1).

## 8. Exemplos de Código

### 8.1 Java (usando `Stack` da biblioteca)

```java
import java.util.Stack;

Stack<String> linguagens = new Stack<>();
linguagens.push("Java");
linguagens.push("Python");
linguagens.push("PHP");
linguagens.push("C");

System.out.println("Linguagens: " + linguagens);   // [Java, Python, PHP, C]
String removido = linguagens.pop();
System.out.println("Elemento removido: " + removido); // C
System.out.println("Linguagens: " + linguagens);   // [Java, Python, PHP]
```

### 8.2 Python (usando lista como pilha)

```python
linguagens = []
linguagens.append("Java")    # push
linguagens.append("Python")
linguagens.append("PHP")
linguagens.append("C")
print("Linguagens:", linguagens)   # ['Java', 'Python', 'PHP', 'C']
removido = linguagens.pop()        # pop (remove do final)
print("Elemento removido:", removido)  # C
print("Linguagens:", linguagens)   # ['Java', 'Python', 'PHP']
```

> ### 8.2.1 Observação
> - Em Python, `append` insere no final da lista e `pop()` remove do final → comportamento de pilha (LIFO).
> - Para simular uma fila com lista, usar-se-ia `pop(0)` (remove do início), mas isso é menos eficiente.

## 9. Questão de Concurso Comentada

### 9.1 (VUNESP/TCM/SP/AUXILIAR TÉCNICO – TÉCNICO DE INFORMÁTICA/2023)

**Sequência:** `PUSH 1` → `PUSH 2` → `POP` → `PUSH 3` → `POP` → `PUSH 4` → `POP` → `PUSH 5`

**Pergunta:** número de elementos na pilha e valor no topo após todas as operações.

**Simulação:**

| OPERAÇÃO | ESTADO DA PILHA (base → topo) | TOPO |
| --- | --- | --- |
| `PUSH 1` | `[1]` | 1 |
| `PUSH 2` | `[1, 2]` | 2 |
| `POP` | `[1]` | 1 |
| `PUSH 3` | `[1, 3]` | 3 |
| `POP` | `[1]` | 1 |
| `PUSH 4` | `[1, 4]` | 4 |
| `POP` | `[1]` | 1 |
| `PUSH 5` | `[1, 5]` | 5 |

**Resultado:**
- Número de elementos: **2** (1 e 5)
- Valor no topo: **5**

**Gabarito:** **e) 2 e 5**.

> ### 9.1.1 Variações comuns da questão
> - Pode-se perguntar: "Quantos elementos ficaram?", "Qual o valor do topo?", "Qual o valor da base?", "Quais os elementos que estão na pilha?".
> - Sempre simular passo a passo respeitando LIFO.

## 10. Síntese para Revisão Rápida (Checklist)

- [ ] **LIFO / FILO** = pilha (stack). **FIFO / LILO** = fila (queue).
- [ ] `push(x)` = insere no **topo**.
- [ ] `pop()` = remove do **topo** (sem parâmetro).
- [ ] `top()` = consulta o topo sem remover.
- [ ] Implementações: estática (array) ou dinâmica (lista encadeada).
- [ ] Exemplos práticos: recursão, Ctrl+Z, navegação web.
- [ ] Em códigos: Java usa `push/pop`, Python usa `append/pop()`.

---

## Gabarito da questão

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (VUNESP/2023) | e |

---

*Material baseado na aula do professor Rogério Gildo Araujo (Gran Concursos).*