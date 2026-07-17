# Anotações

# ALGORITMOS DE ORDENAÇÃO – BUBBLE SORT

## 1. Definição e Conceito

### 1.1 O que é o Bubble Sort

- **Bubble Sort** (Ordenação por Flutuação ou "Algoritmo da Bolha") é um algoritmo de ordenação baseado em **comparações consecutivas de pares de elementos adjacentes**.
- A ideia central é que, a cada **iteração** (ou passagem) pelo vetor, o maior (ou menor) elemento "borbulha" até a extremidade correta da lista, como uma bolha subindo na água.
- **Funcionamento Básico:** O algoritmo percorre repetidamente a lista, compara elementos vizinhos e os troca de posição se estiverem na ordem errada. O maior elemento, por exemplo, será "empurrado" para a última posição após a primeira passagem completa. O processo se repete para o subvetor restante até que toda a lista esteja ordenada.

### 1.2 Características do Algoritmo

- **Ordenação por Comparação:** Decide a ordem dos elementos comparando-os entre si.
- **Estável:** Mantém a **ordem relativa** entre elementos iguais. Se dois elementos têm a mesma chave, a ordem em que aparecem na lista original é preservada após a ordenação.
- ***In-place* (No Local):** Utiliza a **própria estrutura** de dados (vetor original) para realizar as trocas. Apenas uma pequena variável auxiliar é usada para efetuar as permutações, sem necessidade de criar uma cópia da estrutura.

### 1.3 Versão Otimizada

- O algoritmo pode ser otimizado com o uso de uma **flag (variável de controle)**, geralmente chamada `trocado` ou `trocou`.
- A cada iteração, a flag é iniciada como `false`. Se uma troca ocorrer, a flag é marcada como `true`.
- **Critério de Parada:** Se, ao final de uma iteração completa, a flag permanecer `false` (nenhuma troca foi feita), significa que o vetor já está completamente ordenado, e o algoritmo pode ser encerrado antecipadamente, evitando passagens desnecessárias.

## 2. Complexidade de Tempo (Big O)

- **Melhor Caso:** **O(n)**.
    - Ocorre quando o vetor já está ordenado. O algoritmo percorre a lista uma única vez, não realiza trocas e encerra.
- **Caso Médio:** **O(n²)**.
    - Em uma situação de entradas aleatórias, o número de comparações e trocas cresce quadraticamente.
- **Pior Caso:** **O(n²)**.
    - Ocorre quando o vetor está em ordem inversa (ex: ordenado decrescentemente e se deseja ordem crescente). Nesse cenário, o número máximo de comparações e trocas é realizado.

---

# QUESTÕES DE CONCURSOS - BUBBLE SORT

## 1. Identificação pelo Funcionamento

### 1.1 (FUNDEP/PREF. CURVELO/2024 - Analista de Sistemas)

- **Enunciado:** Método que percorre a lista, comparando elementos **adjacentes** e **trocando-os** de posição caso não estejam em ordem.
- **Gabarito:** **A) Bolha**.
- **Análise:** A descrição de "comparar elementos adjacentes e trocá-los" é a assinatura principal do Bubble Sort. "Bolha" é a tradução literal de *bubble*.

### 1.2 (SELECOM/PREF. LUCAS RIO VERDE/2024 - Técnico de Informática)

- **Enunciado:** Algoritmo que percorre o conjunto diversas vezes e, a cada passagem, aloca para o **topo o maior elemento** da sequência.
- **Gabarito:** **B) Bubble Sort**.
- **Análise:** A característica de "empurrar" o maior elemento para o final (ou topo) a cada iteração é exclusiva do Bubble Sort e reflete o "borbulhar" da bolha.

### 1.3 (FUNDATEC/IF-RS/2023 - Professor)

- **Enunciado:** "Algoritmo de ordenação popular que funciona **permutando repetidamente elementos adjacentes** que estão fora de ordem."
- **Gabarito:** **A) Bubble sort**.
- **Análise:** A frase "permutando repetidamente elementos adjacentes" é a definição canônica do Bubble Sort, distinguindo-o de outros algoritmos que não operam exclusivamente sobre adjacentes.

## 2. Identificação por Análise de Código

### 2.1 (IF-MT/2023 - Técnico de Laboratório)

- **Enunciado:** Análise de um trecho de algoritmo com um laço aninhado que compara elementos adjacentes (`vet[j]` e `vet[j+1]`) e os troca se o primeiro for maior.
- **Gabarito:** **C) De ordenação Bubble Sort**.
- **Análise:** O código com dois laços aninhados (`for`), onde o laço interno percorre o vetor, compara pares consecutivos e realiza trocas, é a implementação clássica do Bubble Sort.

### 2.2 (UFG/CM MORRINHOS/2025 - Analista de TI)

- **Enunciado:** Código Python que implementa um algoritmo com laço aninhado, uma flag `trocado = False`, e compara elementos adjacentes (`lista[j] > lista[j+1]`). Se a flag permanecer `False` ao fim do laço interno, executa um `break`.
- **Gabarito:** **C) BubbleSort**.
- **Análise:** A presença da flag `trocado` para interromper a execução quando a lista já está ordenada é a característica marcante da **versão otimizada do Bubble Sort**.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (IF-MT/2023) | **C** | Código com dois laços aninhados e trocas de adjacentes. |
| **02** (FUNDEP/2024) | **A** | Bolha = Bubble Sort. Descrição: comparar e trocar adjacentes. |
| **03** (SELECOM/2024) | **B** | Aloca o maior elemento para o fim a cada passagem. |
| **04** (UFG/CM MORRINHOS/2025) | **C** | Código com flag `trocado` para parada antecipada. |
| **05** (FUNDATEC/IF-RS/2023) | **A** | Permutar repetidamente elementos adjacentes. |