# Anotações (Continuação – Estruturas de Dados)

## 8. Listas Encadeadas (Linked Lists)

### 8.1 Conceituação

- **Não possuem restrição de tamanho** – podem aumentar ou diminuir conforme a necessidade durante a execução.
- As células (nós) **não estão alocadas sequencialmente** na memória.
- **Não há definição de tamanho fixo em tempo de compilação**.
- Cada componente (nó) possui:
  - Espaço para armazenamento do **valor** (informação/dado).
  - Espaço para armazenamento de um **ponteiro** (referência) para o próximo elemento da lista.
- O último elemento da lista aponta para **`null`** (ou `None`, ou `0` – dependendo da linguagem/convenção).

> ### 8.1.1 Representação
> ```
> [ Dados | Próx ] → [ Dados | Próx ] → [ Dados | Próx ] → null
> ```

### 8.2 Vantagens e Desvantagens

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| **Tamanho dinâmico** – aloca memória sob demanda, sem desperdício | **Acesso sequencial** – não é possível acessar um elemento diretamente pelo índice (necessário percorrer a lista) |
| **Inserção/remoção eficientes** – não requer deslocamento de elementos (basta ajustar ponteiros) | **Maior consumo de memória** – cada nó armazena um ponteiro adicional |
| **Não há necessidade de estimativa prévia de tamanho** | **Cache localidade** – elementos não contíguos podem impactar desempenho |

> ### 8.2.1 Diferencial (CESPE/2015)
> - A implementação de lista por meio de apontadores permite utilizar posições não contíguas de memória, de modo a se poder **inserir e retirar elementos sem que haja necessidade de deslocar os itens seguintes** da lista.

### 8.3 Tipos de Listas Encadeadas

| TIPO | DESCRIÇÃO |
| --- | --- |
| **Lista Simplesmente Encadeada** (*Singly Linked List*) | Cada nó aponta apenas para o próximo nó. A travessia é unidirecional (do início para o fim). |
| **Lista Duplamente Encadeada** (*Doubly Linked List*) | Cada nó aponta para o próximo **e** para o anterior. Permite travessia bidirecional. |
| **Lista Circular** (*Circular Linked List*) | O último nó aponta de volta para o primeiro (ou para outro nó). Pode ser simplesmente ou duplamente encadeada. |

> ### 8.3.1 Questão (QUADRIX/2022)
> - A estrutura em que cada elemento armazena dados e um ponteiro para o próximo elemento, permitindo operações como inserir no início, inserir no fim, consultar toda a lista, remover elemento e esvaziar, é a **lista simplesmente encadeada e não ordenada** (a ordem é lógica, não necessariamente numérica).

### 8.4 Lista Simplesmente Encadeada (LLSE)

#### 8.4.1 Estrutura do nó

| CAMPO | DESCRIÇÃO |
| --- | --- |
| **Informação** (info/dado) | Armazena o valor efetivo do elemento. |
| **Próximo** (next/prox) | Ponteiro para o próximo nó da lista (ou `null` se for o último). |

#### 8.4.2 Operações básicas

**Criação da lista:**
- Inicialmente, a lista está vazia – o ponteiro para o primeiro elemento (`head`) é `null`.

**Criação do primeiro elemento:**
- Aloca-se um novo nó.
- Preenche-se o campo de informação.
- Define-se o ponteiro `próximo` como `null`.
- O ponteiro `head` passa a apontar para esse nó.

**Inserção no início:**
- Cria-se um novo nó.
- O ponteiro `próximo` do novo nó aponta para o nó que era o primeiro (`head`).
- O ponteiro `head` passa a apontar para o novo nó.
- **Custo:** O(1) – nenhum deslocamento de elementos existentes.

**Inserção no final:**
- Percorre-se a lista até o último nó (onde `próximo` é `null`).
- O ponteiro `próximo` do último nó é ajustado para apontar para o novo nó.
- O novo nó tem `próximo = null`.
- **Custo:** O(n) – é necessário percorrer a lista.

**Inserção no meio (após uma determinada posição):**
- Localiza-se o nó após o qual se deseja inserir.
- O ponteiro `próximo` do novo nó aponta para o sucessor do nó localizado.
- O ponteiro `próximo` do nó localizado é ajustado para apontar para o novo nó.
- **Custo:** O(n) – devido à localização.

**Acesso a um elemento:**
- Não há acesso direto por índice. É necessário percorrer a lista sequencialmente, partindo do `head`, até encontrar o elemento desejado.
- **Custo:** O(n) no pior caso.

**Remoção no início:**
- O ponteiro `head` passa a apontar para o segundo nó.
- O primeiro nó é desalocado (memória liberada).
- **Custo:** O(1).

**Remoção no final:**
- Percorre-se a lista até o penúltimo nó.
- O ponteiro `próximo` do penúltimo nó é ajustado para `null`.
- O último nó é desalocado.
- **Custo:** O(n).

**Remoção no meio:**
- Localiza-se o nó anterior ao que será removido.
- O ponteiro `próximo` do nó anterior é ajustado para apontar para o sucessor do nó removido.
- O nó removido é desalocado.
- **Custo:** O(n).

> ### 8.4.3 Exemplo de remoção de elemento do meio (questão VUNESP/2013)
> - Lista: E1 → E2 → E3 → E4 → E5 (E5 aponta para `null`).
> - Para remover **E3**: basta fazer **E2 passar a apontar para E4** e liberar E3.
> - Não há necessidade de deslocar os demais elementos.

### 8.5 Comparação entre Lista Sequencial (Array) e Lista Encadeada

| CRITÉRIO | LISTA SEQUENCIAL (ARRAY) | LISTA ENCADEADA |
| --- | --- | --- |
| **Tamanho** | Fixo (definido na criação) | Dinâmico (cresce/shrink conforme necessário) |
| **Memória** | Alocação contígua | Alocação não contígua (nós espalhados) |
| **Acesso** | Direto (aleatório) por índice – O(1) | Sequencial – O(n) |
| **Inserção/Remoção (início/meio)** | O(n) – requer deslocamento | O(1) (após localizar a posição) + custo de busca |
| **Inserção/Remoção (final)** | O(1) (se houver espaço) | O(n) (se não houver ponteiro para o fim) |
| **Espaço adicional** | Nenhum (apenas os dados) | Ponteiros (overhead de memória) |

## 9. Questões de Concurso Comentadas

### 9.1 (VUNESP/2019/UFABC/TÉCNICO DE TECNOLOGIA DA INFORMAÇÃO)

**Item:** Uma estrutura de dados definida como uma sequência de células em que cada célula contém um elemento e o endereço da célula seguinte recebe o nome de:

**Alternativa correta:** **e) lista encadeada**.

**Comentário:** A definição descreve exatamente uma lista encadeada (simplesmente encadeada).

### 9.2 (IFRS/2016/PROFESSOR/INFORMÁTICA GERAL)

**Item:** "O tamanho (quantidade de elementos) de uma lista encadeada deve ser definido na hora da criação."

**Gabarito:** **Errado** (falso).

**Comentário:** Listas encadeadas são dinâmicas – o tamanho pode variar durante a execução, não sendo definido previamente.

### 9.3 (FCC/2013/DPE/SP)

**Item (completar lacunas):** "Em uma **lista encadeada**, para cada novo elemento inserido na estrutura, alocamos um espaço de memória para armazená-lo... não podemos garantir que os elementos armazenados na lista ocuparão um espaço de **memória** contíguo... devemos explicitamente guardar o encadeamento dos elementos, o que é feito armazenando-se, junto com a informação de cada elemento, um **ponteiro** para o próximo elemento da **lista**."

**Gabarito:** **b) lista encadeada – memória – lista – ponteiro – lista**.

### 9.4 (CESPE/2015/TER/GO)

**Item:** "A implementação de lista por meio de apontadores permite utilizar posições não contíguas de memória, de modo a se poder inserir e retirar elementos sem que haja necessidade de deslocar os itens seguintes da lista."

**Gabarito:** **Certo**.

### 9.5 (CESPE/2012/BASA)

**Item:** "Estruturas ligadas como listas encadeadas superam a limitação das matrizes que não podem alterar seu tamanho inicial."

**Gabarito:** **Certo**.

**Comentário:** Matrizes (arrays) têm tamanho fixo; listas encadeadas superam essa limitação ao permitirem crescimento dinâmico.

### 9.6 (QUADRIX/2022/PRODAM/AM)

**Item:** Tipo de estrutura em que cada elemento armazena dados e um ponteiro para o próximo elemento, com operações de inserção/remoção/consulta – **lista simplesmente encadeada e não ordenada**.

**Gabarito:** **a**.

### 9.7 (FUNDATEC/2022/IF/RS)

**Figura (LLSE):** A estrutura representada é uma **lista ligada** (simplesmente encadeada).

**Gabarito:** **d) Lista ligada**.

### 9.8 (FGV/2010/DETRAN/RN)

**Algoritmo com `info` e `prox`:** Estrutura representada é **lista simplesmente encadeada**.

**Gabarito:** **d**.

### 9.9 (VUNESP/2013/MPE/ES)

**Remoção de E3 da lista E1→E2→E3→E4→E5:** Ação correta – **E2 passa a apontar para E4; libera-se E3**.

**Gabarito:** **b**.

### 9.10 (IFRS/2016 – itens a e b)

**a)** "Uma lista encadeada é uma coleção linear de objetos de uma classe autorreferenciada, chamados de nós. Pode ser acessada por meio de um ponteiro para o primeiro nó..." – **Correto** (verdadeiro).
**b)** "Por convenção, o ponteiro de link do último nó de uma lista é inicializado em 0 (zero)." – **Correto** (verdadeiro – ou `null`).

### 9.11 (FAURGS/2013/UFRGS)

**Estrutura com campo Dados e ELO (ponteiro):** É uma **lista encadeada** e permite acessar os registros em ordem **alfabética crescente** (através do encadeamento).

**Gabarito:** **d) lista encadeada – alfabética crescente**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (VUNESP/2019) | e |
| 02 (IFRS/2016) | E (Errado) |
| 03 (FCC/2013) | b |
| 04 (CESPE/2015) | C |
| 05 (CESPE/2012) | C |
| 06 (QUADRIX/2022) | a |
| 07 (FUNDATEC/2022) | d |
| 08 (FGV/2010) | d |
| 09 (VUNESP/2013) | b |
| 10 (IFRS/2016 – itens a e b) | a: V / b: V (ambos corretos) |
| 11 (FAURGS/2013) | d |

---

*Material complementar à aula "Estruturas de Dados – Listas Encadeadas e Simplesmente Encadeadas" (professor Rogério Araújo, Gran Concursos).*