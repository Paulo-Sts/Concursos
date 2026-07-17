# Anotações

# ALGORITMOS DE ORDENAÇÃO – HEAP SORT E CONSOLIDAÇÃO

## 1. Algoritmo de Heap Sort (Ordenação por Heap)

### 1.1 Definição e Funcionamento

- **Heap Sort** é um algoritmo de ordenação baseado na estrutura de dados **Heap** (estudada anteriormente).
- Ele utiliza as propriedades do *Max-Heap* (ou *Min-Heap*) para extrair o elemento de maior prioridade repetidamente e construir a lista ordenada.

### 1.2 Características do Algoritmo

- **Ordenação por Comparação:** Sim.
- **Estável:** **Não**. Elementos com chaves iguais podem ter sua ordem relativa alterada.
- ***In-place* (No Local):** **Sim**. O vetor é ordenado sobre si mesmo, sem necessidade de grandes estruturas auxiliares.

### 1.3 Complexidade de Tempo (Big O)

- **Construção da Heap (*Heapify*):** O(n)
- **Reordenação (Extrações e Correções):** O(n log n)
- **Complexidade Total em Todos os Casos:** **O(n log n)**.
    - Esta é uma grande vantagem do Heap Sort: sua complexidade O(n log n) é garantida e estável para o melhor, médio e pior caso.

## 2. Tabela Comparativa de Algoritmos de Ordenação

| ALGORITMO | ESTÁVEL | IN-PLACE | MELHOR CASO | MÉDIO CASO | PIOR CASO | TIPO |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Bubble Sort** | Sim | Sim | O(n) | O(n²) | O(n²) | Comparação |
| **Insertion Sort** | Sim | Sim | O(n) | O(n²) | O(n²) | Comparação |
| **Selection Sort** | Não | Sim | O(n²) | O(n²) | O(n²) | Comparação |
| **Merge Sort** | Sim | Não | O(n log n) | O(n log n) | O(n log n) | Comparação |
| **Quick Sort** | Não | Sim | O(n log n) | O(n log n) | O(n²) | Comparação |
| **Heap Sort** | Não | Sim | O(n log n) | O(n log n) | O(n log n) | Comparação |
| **Counting Sort** | Sim | Não | O(n + k) | O(n + k) | O(n + k) | Não Comparativo |

---

# QUESTÕES DE CONCURSOS - HEAP SORT E CONSOLIDAÇÃO

## 1. Identificação por Complexidade

### 1.1 (FGV/CVM/2024 - Analista)

- **Enunciado:** Algoritmo que no **pior caso** tem relação **quadrática (O(n²))** e no **caso médio** se aproxima de **O(n log n)**.
- **Gabarito:** **A) Quicksort**.
- **Análise:** A descrição "pior caso O(n²) e caso médio O(n log n)" é a assinatura de complexidade do Quick Sort. O Merge Sort e o Heap Sort têm pior caso O(n log n), e o Insertion/Selection Sort não melhoram para O(n log n) no caso médio.

### 1.2 (CESGRANRIO/BANCO DA AMAZÔNIA/2024 - Técnico Científico)

- **Enunciado:** Selecionar dois algoritmos com a **menor complexidade de pior caso** entre: inserção, mergesort, heapsort e bubblesort.
- **Gabarito:** **C) Mergesort e Heapsort**.
- **Análise:** O Merge Sort e o Heap Sort têm pior caso de **O(n log n)**, que é a menor complexidade entre os quatro. Insertion Sort e Bubble Sort têm pior caso O(n²), sendo piores.

### 1.3 (INSTITUTO CONSULPLAN/PREF. CACOAL/2024 - Analista de Sistemas)

- **Enunciado:** Característica correta sobre o algoritmo Heapsort.
- **Gabarito:** **B) O tempo de execução do Heapsort no pior caso é O(n log n)**.
- **Análise:**
    - A) Falsa. O Heapsort **não é estável**.
    - B) Correta. O(n log n) é a complexidade do pior caso.
    - C) Falsa. Pode sim ser implementado em uma estrutura de árvore/array.
    - D) Falsa. O Heapsort é ***in-place***, não utiliza espaço adicional proporcional a N.

### 1.4 (FGV/PC-MG/2025 - Perito Criminal)

- **Enunciado 1:** Opção que representa a complexidade **O(n log n)** mais comumente observada.
- **Gabarito:** **C) Algoritmos de ordenação rápida (QuickSort)**.
- **Enunciado 2:** Algoritmo com o **menor tempo de execução para grandes bases**, considerando o **pior caso**.
- **Gabarito:** **D) Merge sort**.
- **Análise:** Para o pior caso e grandes bases, o Merge Sort (O(n log n) garantido) é mais seguro que o Quick Sort (que pode cair para O(n²)). O Bubble e o Selection Sort são O(n²), piores. "Evaluation sort" não existe.

## 2. Conceitos Gerais sobre Algoritmos e Estruturas

### 2.1 (INSTITUTO CONSULPLAN/TJ-RO/2025 - Analista Judiciário)

- **Enunciado:** Assinalar a afirmativa INCORRETA sobre complexidade de algoritmos e estruturas.
- **Gabarito:** **B) As tabelas hash oferecem uma busca com complexidade O(1) no pior caso.**
- **Análise:** A afirmativa é **FALSA**. A complexidade de busca em uma tabela hash é O(1) no **caso médio**. No **pior caso** (muitas colisões), a busca pode degradar para **O(n)**.

### 2.2 (CESGRANRIO/IPEA/2024 - Técnico)

- **Enunciado:** Ordenar array aleatório de 10k elementos. Algoritmo cujo **consumo no caso médio** é proporcional ao consumo do **pior caso do Quick Sort (O(n²))**. Qual algoritmo tem caso médio O(n²)?
- **Gabarito:** **C) Insertion Sort**.
- **Análise:** O Quick Sort (pior caso) = O(n²). A pergunta é: qual algoritmo tem seu **caso médio** também igual a O(n²)? O Insertion Sort e o Selection Sort são os que têm a complexidade quadrática em todos os cenários principais.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/CVM/2024) | **A** | Pior O(n²) e Médio O(n log n) = Quick Sort. |
| **02** (CESGRANRIO/2024) | **C** | Merge Sort e Heap Sort = Menor complexidade de pior caso (O(n log n)). |
| **03** (CONSULPLAN/PREF. CACOAL/2024) | **B** | Heap Sort = Pior Caso O(n log n), não-estável e in-place. |
| **04** (FGV/PC-MG/2025) | **C** | Complexidade O(n log n) é do Quick Sort. |
| **05** (FGV/PC-MG/2025) | **D** | Melhor para grandes bases no pior caso = Merge Sort. |
| **06** (CONSULPLAN/TJ-RO/2025) | **B** | Hash = Busca O(1) no **médio**, O(n) no **pior**. |
| **07** (CESGRANRIO/IPEA/2024) | **C** | Caso Médio O(n²) = Insertion Sort (ou Selection Sort). |