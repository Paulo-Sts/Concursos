# Anotações

# ALGORITMOS DE ORDENAÇÃO – QUICK SORT E HEAP

## 1. Algoritmo de Quick Sort (Ordenação Rápida)

### 1.1 Definição e Funcionamento

- **Quick Sort** é um algoritmo do tipo **"dividir para conquistar"**, assim como o Merge Sort, mas com uma abordagem diferente.
- **Processo:**
    1.  **Escolha do Pivô:** Um elemento é escolhido como **pivô**.
    2.  **Particionamento:** O vetor é reorganizado de forma que todos os elementos **menores** que o pivô fiquem à sua **esquerda**, e todos os elementos **maiores** fiquem à sua **direita**. Após esta etapa, o pivô já está em sua posição correta final.
    3.  **Recursão:** As etapas 1 e 2 são aplicadas recursivamente nos subvetores da esquerda e da direita, que não contêm o pivô.

### 1.2 Características do Algoritmo

- **Ordenação por Comparação:** Utiliza comparações para particionar os dados.
- **Não Estável:** Durante as trocas do particionamento, a ordem relativa de elementos iguais pode ser alterada.
- ***In-place* (No Local):** Diferentemente do Merge Sort, o Quick Sort é *in-place*. Ele opera dentro da própria estrutura de dados, não necessitando de espaço auxiliar proporcional ao tamanho da entrada.

### 1.3 Complexidade de Tempo (Big O)

- **Melhor Caso:** **O(n log n)**.
    - Ocorre quando o pivô divide o vetor em duas metades de tamanhos sempre balanceados.
- **Caso Médio:** **O(n log n)**.
- **Pior Caso:** **O(n²)**.
    - Ocorre quando a escolha do pivô é ruim e gera partições muito desbalanceadas (ex: o pivô é sempre o maior ou o menor elemento).

## 2. Estrutura de Dados Heap

### 2.1 Definição e Propriedade

- O **Heap** é uma **árvore binária completa** que satisfaz a "propriedade do heap".
- **Definição da Propriedade:**
    - **Max-Heap (Heap Máximo):** O valor de um nó pai é **maior ou igual** ao valor de seus nós filhos.
    - **Min-Heap (Heap Mínimo):** O valor de um nó pai é **menor ou igual** ao valor de seus nós filhos.
- **Árvore Binária Completa:** Significa que todos os níveis da árvore estão completamente preenchidos, com a exceção do último nível, que é preenchido da esquerda para a direita.

### 2.2 Representação como Vetor

- Um heap é comumente implementado e visualizado como um **vetor (array)**.
- **Fórmulas de Localização (Vetor com índice inicial 1):**
    - **Pai do nó `i`:** `i / 2` (divisão inteira).
    - **Filho Esquerdo do nó `i`:** `2 * i`.
    - **Filho Direito do nó `i`:** `2 * i + 1`.
- **Fórmulas de Localização (Vetor com índice inicial 0):**
    - **Pai do nó `i`:** `(i - 1) / 2`.
    - **Filho Esquerdo do nó `i`:** `2 * i + 1`.
    - **Filho Direito do nó `i`:** `2 * i + 2`.

### 2.3 Processo de Inserção (Subida - Sift Up)

- **Passo 1:** Inserir o novo elemento na **próxima posição disponível** do vetor, mantendo a propriedade de árvore completa (no final do vetor).
- **Passo 2 (Heapify Up):** Comparar o valor inserido com o valor do seu nó pai. Se violar a propriedade do heap (ex: em um max-heap, se o filho for maior que o pai), **trocar** os dois de posição (swap).
- **Passo 3:** Repetir o passo 2 recursivamente, "subindo" o novo elemento até que a propriedade do heap seja restaurada ou ele se torne a raiz.

---

# QUESTÕES DE CONCURSOS - QUICK SORT E HEAP

## 1. Identificação de Algoritmos (Quick Sort)

### 1.1 (INST. CONSULPLAN/PREF. CAMPOS/2024 - Analista de Sistemas)

- **Enunciado:** Relacionar descrições com métodos de ordenação.
- **Gabarito:** **B) 5, 1, 2, 4, 3**.
- **Análise das Associações:**
    1.  "Divide a lista em sublistas menores, ordena e mescla": **(5) Insertion Sort** (na forma como a banca interpretou a descrição, embora comum no Merge Sort, a mesclagem de sublistas ordenadas também é uma metáfora para o funcionamento do Insertion ao inserir elementos em uma lista "ordenada".
    2.  "Algoritmo que percorre repetidamente a lista, compara elementos adjacentes e os troca": **(1) Bubble Sort**.
    3.  "Divide a lista em duas partes; ordena-as individualmente e combina-as": **(2) Merge Sort**. (A tríade "dividir, ordenar e combinar" é a definição principal).
    4.  "Algoritmo que seleciona iterativamente o elemento mínimo e coloca-o na posição correta": **(4) Selection Sort**.
    5.  "Algoritmo que escolhe um elemento como pivô; divide a lista em dois subconjuntos e ordena-os recursivamente": **(3) Quick Sort**.

### 1.2 (UFG/PREF. INHUMAS/2024 - Administrador de Rede)

- **Enunciado:** A operação de partição na qual um elemento específico é escolhido como **pivô** é executada pelo algoritmo de ordenação...
- **Gabarito:** **B) Quicksort**.
- **Análise:** O conceito de "pivô" e "particionamento" é a assinatura exclusiva e central do Quick Sort.

## 2. Características de Outros Algoritmos (Merge Sort)

### 2.1 (UFG/IF-SE/2024 - Professor EBTT)

- **Enunciado:** A complexidade de tempo do algoritmo Merge Sort, quando ordenando uma lista de tamanho n, é:
- **Gabarito:** **C) O(n log n)**.
- **Análise:** Esta é a complexidade de tempo padrão, para todos os casos, do Merge Sort.

### 2.2 (INST. CONSULPLAN/TJ-MA/2024 - Analista de Sistemas)

- **Enunciado:** Qual das seguintes afirmativas sobre o Merge Sort é verdadeira?
- **Gabarito:** **B) MergeSort é um algoritmo de ordenação estável, preservando a ordem relativa de elementos iguais.**
- **Análise:**
    - **A) Falsa:** A complexidade média de ambos é O(n log n).
    - **B) Verdadeira:** Esta é uma característica importante e correta do Merge Sort.
    - **C) Falsa:** A divisão pode não ser exata (ex: vetor ímpar resulta em uma metade com um elemento a mais).
    - **D) Falsa:** Merge Sort **não** é *in-place*; ele requer espaço adicional.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CONSULPLAN/2024) | **B** | Sequência correta: 5, 1, 2, 4, 3. |
| **02** (UFG/INHUMAS/2024) | **B** | Pivô e particionamento = Quick Sort. |
| **03** (UFG/IF-SE/2024) | **C** | Complexidade Merge Sort: O(n log n). |
| **04** (CONSULPLAN/TJ-MA/2024) | **B** | Merge Sort é **estável**. |