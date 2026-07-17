# Anotações

# ALGORITMOS DE ORDENAÇÃO – COUNTING SORT E MERGE SORT

## 1. Algoritmo de Counting Sort (Ordenação por Contagem)

### 1.1 Definição e Funcionamento

- **Counting Sort** é um algoritmo de ordenação **não baseado em comparação**. Ele utiliza a **frequência (contagem)** de ocorrência dos elementos para ordenar os dados.
- **Pré-Requisito:** É eficiente quando se conhece previamente o intervalo dos valores a serem ordenados (ex: todos os números são inteiros entre 0 e `k`, onde `k` é o maior elemento).
- **Processo Resumido:** Em vez de comparar elementos entre si, o algoritmo:
    1.  **Conta** quantas vezes cada valor aparece no vetor original.
    2.  **Acumula** essas contagens para determinar posições.
    3.  **Reconstrói** o vetor ordenado a partir dessas contagens.

### 1.2 Características do Algoritmo

- **Ordenação Não Comparativa:** Não decide a ordem pela comparação de chaves diretamente.
- **Estável:** Mantém a posição relativa entre elementos com a mesma chave.
- **Não é *In-place*:** Cria estruturas auxiliares para contagem e para construir o vetor final ordenado.

### 1.3 Complexidade de Tempo (Big O)

- **Melhor, Caso Médio e Pior Caso:** **O(n + k)**.
    - `n` é o número de elementos no vetor.
    - `k` é o intervalo de valores (maior valor presente).
- **Observação:** Se `k` não for excessivamente grande, o algoritmo pode ter complexidade linear.

## 2. Algoritmo de Merge Sort (Ordenação por Combinação)

### 2.1 Definição e Funcionamento

- **Merge Sort** é um algoritmo de ordenação baseado no paradigma **"dividir para conquistar"** (*Divide and Conquer*).
- **Processo em Duas Etapas:**
    1.  **Dividir (*Divide*):** O vetor é dividido recursivamente em **duas metades** até que cada subvetor tenha apenas **um elemento** (que é trivialmente ordenado).
    2.  **Conquistar (*Merge*):** Os subvetores atômicos são **intercalados (combinados)** de forma ordenada, produzindo subvetores ordenados cada vez maiores. Este processo se repete até que o vetor inteiro esteja completamente ordenado.

### 2.2 Características do Algoritmo

- **Ordenação por Comparação:** Compara os elementos durante o processo de intercalação.
- **Estável:** Mantém a ordem relativa entre elementos com chaves iguais durante a intercalação.
- **Não é *In-place*:** Necessita de espaço auxiliar proporcional ao tamanho do vetor para realizar a intercalação.

### 2.3 Complexidade de Tempo (Big O)

- **Melhor, Caso Médio e Pior Caso:** **O(n log n)**.
    - Esta é a complexidade de tempo característica e uma das grandes vantagens do Merge Sort, sendo consistente em todos os cenários.

---

# QUESTÕES DE CONCURSOS - COUNTING SORT E MERGE SORT

## 1. Identificação de Algoritmos

### 1.1 (FADESP/PREF. CAPANEMA/2024 - Analista de Sistemas)

- **Enunciado:** Análise de uma sequência de passos para ordenar um vetor. O algoritmo utilizado foi o:
- **Gabarito:** **B) Merge-sort**.
- **Análise:** A descrição do enunciado (não textual no resumo, mas implícita na questão) remete ao processo de divisão e intercalação que caracteriza o Merge Sort.

### 1.2 (FUNDEP/UFOP/2024 - Analista de Tecnologia)

- **Enunciado:** Algoritmo descrito pelos passos: "1. Dividir recursivamente o vetor até obter n vetores de 1 elemento. 2. Aplicar a intercalação formando um vetor ordenado. 3. Repetir esse processo formando vetores ordenados cada vez maiores...".
- **Gabarito:** **A) Mergesort**.
- **Análise:** A tríade "dividir recursivamente", "aplicar intercalação" e "formar vetores cada vez maiores" é a definição canônica do funcionamento do Merge Sort.

### 1.3 (INSTITUTO AOCP/IF-MA/2023 - Analista de Tecnologia)

- **Enunciado:** Método de ordenação com complexidade de tempo médio **O(n log n)** e que utiliza a técnica de **dividir e conquistar**.
- **Gabarito:** **E) Merge sort**.
- **Análise:** Embora o Quick Sort também use "dividir para conquistar", a combinação de ser um algoritmo estável e ter complexidade garantida O(n log n) identifica exclusivamente o Merge Sort (o Quick Sort tem pior caso O(n²)).

## 2. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FADESP/2024) | **B** | Descrição do processo de intercalação = Merge Sort. |
| **02** (FUNDEP/UFOP/2024) | **A** | Dividir recursivamente e intercalar = Merge Sort. |
| **03** (AOCP/IF-MA/2023) | **E** | Complexidade O(n log n) e técnica de dividir e conquistar. |