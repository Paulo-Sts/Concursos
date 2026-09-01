# Anotações

# ALGORITMOS DE ORDENAÇÃO – SELECTION SORT E INSERTION SORT

## 1. Algoritmo de Selection Sort (Ordenação por Seleção)

### 1.1 Definição e Funcionamento

- **Selection Sort** é um algoritmo de ordenação baseado na ideia de, repetidamente, encontrar o **menor** (ou maior) elemento da lista e colocá-lo diretamente na posição correta.
- **Processo Passo a Passo:**
    1.  Percorrer toda a lista para encontrar o **menor elemento**.
    2.  Trocar esse menor elemento de lugar com o elemento que está na **primeira posição** da lista.
    3.  Repetir o processo para o restante da lista (ignorando a primeira posição já ordenada): encontrar o segundo menor elemento e trocá-lo com o elemento da segunda posição.
    4.  Continuar assim, sucessivamente, até que todos os elementos estejam ordenados.

### 1.2 Características do Algoritmo

- **Ordenação por Comparação:** Decide a ordem comparando os elementos entre si.
- **Não Estável:** Pode alterar a ordem relativa de elementos com a mesma chave.
- ***In-place* (No Local):** Realiza as trocas dentro da própria estrutura de dados, sem criar uma cópia.

### 1.3 Complexidade de Tempo (Big O)

- **Melhor Caso:** **O(n²)**.
- **Caso Médio:** **O(n²)**.
- **Pior Caso:** **O(n²)**.
- **Observação:** Diferentemente de outros algoritmos, a complexidade do Selection Sort é sempre quadrática, independentemente de o vetor já estar ordenado ou não.

## 2. Algoritmo de Insertion Sort (Ordenação por Inserção)

### 2.1 Definição e Funcionamento

- **Insertion Sort** é um algoritmo que constrói a lista ordenada **um elemento por vez**, inserindo cada novo valor na posição correta em relação aos elementos já analisados.
- **Analogia Clássica:** Funciona como organizar cartas em uma mão. Você pega uma carta nova do monte e a insere na posição correta entre as cartas que já estão organizadas na sua mão.
- **Processo Passo a Passo:**
    1.  Assumir que o primeiro elemento da lista está "ordenado".
    2.  Pegar o **próximo elemento** do conjunto não ordenado.
    3.  Compará-lo com os elementos da parte já ordenada, da direita para a esquerda.
    4.  Deslocar os elementos maiores para a direita até encontrar a posição correta para o novo elemento.
    5.  Inserir o elemento na posição encontrada.
    6.  Repetir a partir do passo 2 até que todos os elementos tenham sido inseridos.

### 2.2 Características do Algoritmo

- **Ordenação por Comparação:** Compara elementos para definir a ordem.
- **Estável:** Mantém a ordem relativa entre elementos com chaves iguais, pois insere o novo elemento sempre após os existentes de mesmo valor.
- ***In-place* (No Local):** Ordena usando a própria estrutura, sem necessitar de uma cópia do vetor.

### 2.3 Complexidade de Tempo (Big O)

- **Melhor Caso:** **O(n)**.
    - Ocorre quando o vetor já está **ordenado**. O algoritmo apenas percorre a lista, verifica cada elemento sem precisar deslocar nenhum.
- **Caso Médio:** **O(n²)**.
- **Pior Caso:** **O(n²)**.
    - Ocorre quando o vetor está em **ordem inversa** (decrescente para ordenação crescente). Cada novo elemento é menor que todos os anteriores e precisa ser deslocado até o início da lista, gerando o máximo de comparações e movimentações.

---

# QUESTÕES DE CONCURSOS - SELECTION SORT E INSERTION SORT

## 1. Identificação de Algoritmos

### 1.1 (FUNDEP/UFOP/2024 - Analista de Tecnologia)

- **Enunciado:** Algoritmo descrito pelos passos: "1. Encontre o menor item do vetor. 2. Troque-o com o item da primeira posição. 3. Repita com os n-1 itens restantes...". Qual o método?
- **Gabarito:** **C) Seleção**.
- **Análise:** A descrição de "encontrar o menor e trocar com o primeiro" é a definição exata do funcionamento do **Selection Sort**.

### 1.2 (IF-MG/2024 - Professor EBTT)

- **Enunciado:** Identificar o algoritmo de ordenação representado por uma figura que mostra elementos sendo inseridos um a um na parte já ordenada da lista.
- **Gabarito:** **C) Insertion Sort**.
- **Análise:** A representação visual ou descritiva de "pegar um novo item e inseri-lo no local correto entre os já ordenados" é a assinatura do Insertion Sort.

### 1.3 (FGV/CVM/2024 - Analista)

- **Enunciado:** Análise de um código que utiliza um laço `para K de 2 até n`, armazena um valor em `X`, e um laço `enquanto` desloca elementos maiores que `X` para a direita, abrindo espaço para inseri-lo na posição correta.
- **Gabarito:** **B) Insertion Sort**.
- **Análise:** O mecanismo de "deslocar elementos maiores para abrir espaço" e "inserir o valor na posição correta" dentro de um laço que avança linearmente é a implementação característica do **Insertion Sort**.

## 2. Análise do Comportamento (Complexidade e Movimentações)

### 2.1 (CEBRASPE/PREF. CACHOEIRO/2024 - Analista de Sistemas)

- **Enunciado:** "Na execução do Insertion Sort, o número máximo de movimentações em função das comparações acontecerá quando, no vetor original, nenhum elemento for maior que seu sucessor."
- **Gabarito:** **ERRADO**.
- **Análise:**
    - A afirmativa descreve um vetor onde "nenhum elemento é maior que seu sucessor", ou seja, um vetor **já ordenado** (crescente).
    - No vetor já ordenado, o Insertion Sort opera em seu **melhor caso** (O(n)), realizando o **mínimo** de movimentações.
    - O **número máximo** de movimentações (pior caso) ocorre justamente no cenário oposto, quando o vetor está em **ordem decrescente**, forçando cada novo elemento a ser movido até o início da lista.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FUNDEP/UFOP/2024) | **C** | Encontrar o menor e trocar com o primeiro = Selection Sort. |
| **02** (IF-MG/2024) | **C** | Inserir um a um na parte ordenada = Insertion Sort. |
| **03** (FGV/CVM/2024) | **B** | Código que desloca elementos para inserir = Insertion Sort. |
| **04** (CEBRASPE/2024) | **E** | Vetor já ordenado é o **melhor caso** (mínimo de movimentações). |