# Anotações (Continuação – Estruturas de Dados)

## 12. Listas Circulares

### 12.1 Conceituação

- Lista em que o **último elemento aponta para o primeiro**, formando um ciclo (não há ponteiro `null` no `next` do último nó).
- Podem ser implementadas como:
  - **Lista simplesmente encadeada circular** – apenas ponteiro `next`; o último nó aponta para o primeiro.
  - **Lista duplamente encadeada circular** – ponteiros `next` e `prev`; o último nó aponta para o primeiro e o primeiro aponta para o último.

> ### 12.1.1 Representação (circular simples)
> ```
> [ info | next ] → [ info | next ] → [ info | next ] ↘
>    ↑_________________________________________________↙
> ```

> ### 12.1.2 Definição (questão VUNESP/2012 e VUNESP/2014)
> - Estrutura em que o **último elemento apresenta como próximo elemento o primeiro elemento** é denominada **Lista Circular** (ou Lista Encadeada Circular).

### 12.2 Características

| CARACTERÍSTICA | LISTA CIRCULAR | LISTA LINEAR (NÃO CIRCULAR) |
| --- | --- | --- |
| Ponteiro `next` do último nó | Aponta para o **primeiro** nó | Aponta para `null` (ou `None`) |
| Travessia | Pode percorrer indefinidamente (cuidado com loop infinito) | Termina ao encontrar `null` |
| Acesso ao primeiro nó a partir do último | Direto (O(1)) | Não é possível sem percorrer toda a lista |
| Implementação de filas circulares | Comum (aproveita espaço fixo) | Não se aplica |

> ### 12.2.1 Observação sobre listas duplamente encadeadas circulares (CESPE/2016)
> - Em uma lista circular duplamente encadeada:
>   - O ponteiro `prev` do primeiro nó aponta para o **último** nó.
>   - O ponteiro `next` do último nó aponta para o **primeiro** nó.
> - A afirmação "ponteiro anterior ao início da lista aponta para o fim, e o ponteiro próximo à célula do fim aponta para o início" está **correta** para esse tipo de estrutura.

## 13. Nó Cabeça (Header) / Sentinela

### 13.1 Conceituação

- Nó especial, geralmente o primeiro nó da lista (posição 0), que **não armazena um dado útil** da aplicação.
- Pode conter **informações globais sobre a lista**, como:
  - Número de elementos da lista (tamanho).
  - Ponteiro para o último elemento (em listas não circulares).
  - Outros metadados relevantes para a implementação.

### 13.2 Nomenclaturas (sinônimos)

| TERMO | SIGNIFICADO |
| --- | --- |
| Nó cabeça | *Head node* |
| Nó cabeçalho | *Header node* |
| Sentinela | *Sentinel node* |
| Nó dummy | *Dummy node* |

### 13.3 Funções do nó sentinela

- **Simplificar operações** – evita tratamento de casos especiais (inserção/remoção no início, lista vazia).
- **Armazenar tamanho da lista** – evita percorrer toda a lista para contar elementos (reduz custo de O(n) para O(1)).
- **Armazenar referência ao fim da lista** – útil para inserção no final em O(1).
- **Representar lista vazia** – uma lista vazia pode conter apenas o nó sentinela (sem elementos úteis).

> ### 13.3.1 Exemplo de uso (questão CESPE/2012)
> - "Em algumas implementações, uma lista vazia pode ter um único nó, chamado de sentinela, nó cabeça ou header. Entre suas possíveis funções, inclui-se simplificar a implementação de algumas operações realizadas sobre a lista, como inserir novos dados, recuperar o tamanho da lista, entre outras." – **Afirmação correta**.

## 14. Relação entre Listas, Pilhas e Filas

### 14.1 Conceito de "Listas Especiais"

- **Listas sequenciais ou encadeadas** (genéricas) permitem inserção e remoção em **qualquer ponto** (início, meio, fim).
- **Pilhas (stacks)** e **filas (queues)** são **listas especiais** que **restringem** as operações de inserção e remoção segundo princípios específicos.
- Podem ser implementadas tanto com alocação sequencial (arrays) quanto com alocação encadeada.

| ESTRUTURA | PRINCÍPIO | INSERÇÃO | REMOÇÃO |
| --- | --- | --- | --- |
| **Pilha** | LIFO (Last In, First Out) | No topo (final) | Do topo (final) |
| **Fila** | FIFO (First In, First Out) | No final | Do início |
| **Deque** | Double-ended queue | Em ambas as pontas | Em ambas as pontas |

> ### 14.1.1 Atenção (questão IFRS/2016)
> - "[D] Pilhas, filas e árvores são consideradas também estruturas de dados lineares, baseadas em listas encadeadas." – **Afirmação errada**.
> - Justificativa: **Árvores não são estruturas lineares** (são hierárquicas/não lineares). Apenas pilhas e filas são lineares. Além disso, as árvores não são baseadas em listas encadeadas (embora usem nós com ponteiros, a estrutura é diferente).

## 15. Questões de Concurso Comentadas

### 15.1 (FAURGS/2018/TJ/RS – PROGRAMADOR)

**Estrutura com posições, códigos, nomes, idades, cargos e endereços de próximo (`End_Prox`).** Fluxograma percorre a lista encadeada (simples) a partir do registro especial na posição 1, seguindo os ponteiros.

**Pergunta:** Qual a ordem em que os registros serão impressos?

**Gabarito:** **c) Alfabética de Nome**.

**Comentário:** A ordem dos ponteiros (`End_Prox`) foi construída de modo que, ao seguir os encadeamentos, os registros são visitados em ordem alfabética crescente dos nomes (independentemente da ordem física ou de outros campos).

### 15.2 (CESPE/2017/TRT 7ª REGIÃO – ANALISTA JUDICIÁRIO)

**Item:** Estrutura em que cada elemento tem ligações com seu sucessor e predecessor, permitindo percorrer em qualquer sentido → **lista duplamente encadeada**.

**Gabarito:** **c) uma lista duplamente encadeada**.

### 15.3 (VUNESP/2012/TJ/SP – ANALISTA DE SISTEMAS)

**Item:** Lista em que o último elemento aponta para o primeiro → **Lista Circular**.

**Gabarito:** **a) Circular**.

### 15.4 (VUNESP/2014/SP/URBANISMO – ANALISTA ADMINISTRATIVO)

**Item:** Lista encadeada com 10 elementos, primeiro e último ligados entre si → **Lista Encadeada Circular**.

**Gabarito:** **d) Encadeada Circular**.

### 15.5 (IFRS/2016 – PROFESSOR/INFORMÁTICA GERAL)

**Item (letra D):** "Pilhas, filas e árvores são consideradas também estruturas de dados lineares, baseadas em listas encadeadas."

**Gabarito:** **Errado** (conforme análise acima – árvores não são lineares).

### 15.6 (IBADE/2018/CÂMARA DE VILHENA/RO – ANALISTA ADMINISTRATIVO)

**Item:** Estrutura onde existe coleção ordenada de entidades, com busca baseada em deslocamento relativo ao primeiro (cabeça) → **lista**.

**Gabarito:** **b) lista**.

### 15.7 (CESPE/2016/TCE/PA – AUDITOR DE CONTROLE EXTERNO)

**Item:** "Em uma lista circular, o ponteiro anterior ao início da lista aponta para o fim, e o ponteiro próximo à célula do fim da lista aponta para o início."

**Gabarito:** **Certo** (trata-se de lista duplamente encadeada circular).

### 15.8 (CESPE/2012/BASA – CARGO 16)

**Item 1:** "Em algumas implementações, uma lista vazia pode ter um único nó, chamado de sentinela, nó cabeça ou header. Entre suas possíveis funções, inclui-se simplificar a implementação de algumas operações realizadas sobre a lista, como inserir novos dados, recuperar o tamanho da lista, entre outras."

**Gabarito:** **Certo**.

**Item 2:** "As listas duplamente encadeadas diferenciam-se das listas simplesmente encadeadas pelo fato de, na primeira, os nós da lista formarem um anel com o último elemento ligado ao primeiro da lista."

**Gabarito:** **Errado**.

**Comentário:** A formação de anel (circular) não é característica de listas duplamente encadeadas em geral, mas sim de **listas circulares** (que podem ser simples ou duplamente encadeadas).

### 15.9 (CESPE/2009/ANAC – TÉCNICO ADMINISTRATIVO)

**Item:** "Em uma lista circular duplamente encadeada, cada nó aponta para dois outros nós da lista, um anterior e um posterior."

**Gabarito:** **Certo** (independentemente de ser circular, a lista duplamente encadeada tem dois ponteiros).

### 15.10 (AOCP/2016/PREFEITURA DE JUIZ DE FORA – PROGRAMADOR)

**Item (figura):** Lista onde o último elemento retorna ao primeiro → **lista circular** (simplesmente encadeada circular).

**Gabarito:** **e) Lista circular**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FAURGS/2018) | c |
| 02 (CESPE/2017) | c |
| 03 (VUNESP/2012) | a |
| 04 (VUNESP/2014) | d |
| 05 (IFRS/2016 – letra D) | E (Errado) |
| 06 (IBADE/2018) | b |
| 07 (CESPE/2016 – circular) | C (na ementa consta como questão 8, gabarito C) |
| 08 (CESPE/2012 – sentinela) | C |
| 09 (CESPE/2012 – dupla circular) | E |
| 10 (CESPE/2009 – dupla circular) | C |
| 11 (AOCP/2016) | e |

*Observação: a numeração das questões no material original é variada; o gabarito consolidado acima segue a ordem apresentada no arquivo.*

---

*Material complementar à aula "Estruturas de Dados – Listas Circulares, Nó Cabeça e Questões" (professor Rogério Araújo, Gran Concursos).*