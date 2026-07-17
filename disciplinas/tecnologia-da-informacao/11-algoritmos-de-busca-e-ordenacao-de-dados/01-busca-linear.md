# Anotações

# ALGORITMOS DE BUSCA – BUSCA LINEAR

## 1. Notação Big O (Complexidade de Algoritmos)

### 1.1 Conceito e Finalidade

- A notação Big O, também chamada de **análise assintótica**, é a forma de medir a complexidade de um algoritmo.
- Seu foco principal é analisar o **pior caso** (maior custo computacional possível) de execução de um algoritmo em função do tamanho da entrada de dados (`n`).
- **Critério de Escolha:** Ao comparar dois algoritmos, escolhe-se aquele cujo pior caso (maior complexidade Big O) for melhor.

### 1.2 Principais Complexidades (Tempo de Execução)

- **Constante – O(1):**
    - O tempo de execução **não depende** do tamanho da entrada de dados.
    - O algoritmo realiza um número fixo de operações, independentemente de processar um ou um milhão de dados.
    - **Exemplo:** Ler apenas o primeiro elemento de um vetor.

- **Linear – O(n):**
    - O tempo de execução **cresce proporcionalmente** ao tamanho da entrada (`n`).
    - Se a quantidade de dados dobra, o tempo de execução também dobrará.
    - **Exemplo:** Percorrer toda uma lista com um laço `for` para imprimir todos os elementos.

- **Logarítmico – O(log n):**
    - O tamanho dos dados de entrada é **reduzido a cada etapa** do algoritmo.
    - A cada passo, o problema é dividido (geralmente pela metade), tornando a busca extremamente rápida em grandes conjuntos de dados.
    - **Exemplo:** Algoritmo de Busca Binária.

- **Quadrático – O(n²):**
    - O processamento é multiplicado pelo número de registros por ele mesmo.
    - É comum em algoritmos que possuem dois laços de repetição aninhados.
    - **Exemplo:** Calcular o produto cartesiano de uma lista com ela mesma.

## 2. Algoritmo de Busca Linear (Sequencial Simples)

### 2.1 Definição e Mecanismo

- É o método de busca mais **simples**, onde cada elemento do conjunto é **verificado sequencialmente**, um a um, até que o elemento desejado seja encontrado.
- Se o algoritmo chegar ao fim da estrutura de dados sem encontrar o elemento, conclui-se que ele não está presente.

### 2.2 Vantagens

- **Simplicidade:** Fácil de entender e implementar.
- **Versatilidade:** Funciona em **qualquer estrutura linear**, seja ela **ordenada ou não ordenada**.

### 2.3 Desvantagens

- **Ineficiência:** É um algoritmo lento para grandes listas, pois pode exigir a verificação de todos os dados.
- **Não se beneficia** do fato de a lista estar ordenada; a quantidade de comparações é a mesma independentemente da ordenação.

### 2.4 Complexidade (Big O)

- **Pior Caso:** **O(n)**.
    - Ocorre quando o elemento procurado é o último da lista ou não está presente na lista. Nesse cenário, `n` comparações serão realizadas, onde `n` é o número de elementos.
- **Melhor Caso:** **O(1)**.
    - Ocorre quando o elemento é encontrado na primeira posição.

## 3. Algoritmo de Busca Linear Otimizada (Sequencial Ordenada)

### 3.1 Definição e Funcionamento

- É uma variação da busca linear tradicional que **exige que a lista esteja previamente ordenada**.
- **Mecanismo de Parada:** O algoritmo percorre a lista e **interrompe a busca** assim que encontra um valor que, pela lógica da ordenação, torna impossível encontrar o valor procurado.
    - **Ordenação Crescente:** A busca é interrompida quando um elemento **maior** que o valor procurado é encontrado.
    - **Ordenação Decrescente:** A busca é interrompida quando um elemento **menor** que o valor procurado é encontrado.

### 3.2 Vantagem sobre a Busca Linear Simples

- Oferece um ganho de desempenho ao evitar percorrer toda a lista desnecessariamente, reduzindo o número médio de comparações quando o elemento não existe ou está no início.

### 3.3 Complexidade (Big O)

- **Pior Caso:** **O(n)**.
    - Embora otimizada, a complexidade do pior caso permanece `O(n)`. Isso ocorre porque, se o elemento procurado for o último da lista ou for maior que o último elemento, todos os `n` elementos serão comparados.
- **Melhor Caso:** **O(1)**.
    - Ocorre quando o elemento é encontrado na primeira posição.

---

# QUESTÕES DE CONCURSOS - ALGORITMOS DE BUSCA (BUSCA LINEAR)

## 1. Análise de Comparações em Vetor Ordenado

### 1.1 (INSTITUTO CONSULPLAN/PREF. CACOAL/2024 - Analista)

- **Enunciado:** Considere o vetor ordenado V = [3, 8, 15, 19, 24, 30, 42]. Usando o algoritmo de pesquisa linear, qual é o número de comparações realizadas para encontrar o elemento 24?
- **Gabarito:** **C) 5.**
- **Análise:** A busca linear simples percorre o vetor elemento a elemento da esquerda para a direita. As comparações são feitas com cada valor:
    1.  3 (não é 24)
    2.  8 (não é 24)
    3.  15 (não é 24)
    4.  19 (não é 24)
    5.  24 (é 24). Para e retorna.
    Portanto, são realizadas **5 comparações**, que correspondem às verificações feitas até encontrar o valor.

## 2. Diferença entre Busca Linear e Otimizada

### 2.1 (CEBRASPE/ABIN/2018 - Oficial Técnico)

- **Enunciado:** "Na pesquisa do tipo sequencial, há aumento do desempenho se a tabela estiver ordenada pelo valor da chave."
- **Gabarito:** **CERTO.**
- **Análise:** A afirmação se refere à **Busca Sequencial Otimizada** (e não à simples). A ordenação permite que o algoritmo pare a busca assim que um valor inviabiliza a procura, aumentando o desempenho ao reduzir o número de comparações na maioria dos casos.

## 3. Busca Otimizada em Sequências Ordenadas e Desordenadas

### 3.1 (CESGRANRIO/BANCO DO BRASIL/2021 - Agente de Tecnologia)

- **Enunciado:** Usando um algoritmo de busca sequencial otimizado (esquerda para direita), encontrar o **menor número de comparações** para buscar a senha `52` entre as diferentes sequências.
- **Gabarito:** **A.** (Sequência: 23; 45; 81; 97; 112; 138; 154)
- **Análise:**
    - **Sequência A (Crescente):** Busca-se `52`. As comparações são: 23 (continua), 45 (continua), 81 (para, pois 81 > 52). O algoritmo conclui que o `52` não está ali. Total: **3 comparações**. Este é o menor número possível entre as opções.
    - **Sequência B (Crescente):** Busca o 52. Comparações: 13, 25, 37, 44, 52 (encontrado). Total: **5 comparações**.
    - **Sequência C (Crescente):** Busca o 52. Comparações: 17, 28, 32, 49, 67 (para, 67 > 52). Total: **5 comparações**.
    - **Sequência D (Desordenada):** O algoritmo otimizado não é aplicável em sua forma pura, mas se usado apenas o sequencial simples, teria que procurar em toda a lista. O 52 está presente e seriam necessárias **7 comparações**.
    - **Sequência E (Desordenada):** Mesmo caso da D, o 52 não está presente e seriam necessárias **7 comparações** para percorrer toda a lista e concluir a ausência.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (INST. CONSULPLAN/2024) | **C** | 5 comparações: 3, 8, 15, 19 e 24. |
| **02** (CEBRASPE/2018) | **C** | A ordenação melhora o desempenho da busca **sequencial otimizada**. |
| **03** (CESGRANRIO/2021) | **A** | 3 comparações (Sequência A) é o menor número entre as opções. |