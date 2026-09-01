# Anotações

# ALGORITMOS DE BUSCA – BUSCA BINÁRIA

## 1. Definição e Pré-Requisitos

### 1.1 O que é a Busca Binária

- É um algoritmo de busca que localiza um elemento em uma estrutura de dados dividindo repetidamente o conjunto de dados pela metade.
- A cada passo, o algoritmo compara o valor procurado com o elemento central do intervalo de busca atual. Com base nessa comparação, descarta a metade do conjunto onde o elemento **não pode** estar.

### 1.2 Pré-Requisito Fundamental

- **Ordenação:** A busca binária **só funciona em conjuntos de dados ORDENADOS**. Esta é a exigência mais crucial e mais cobrada em provas. O vetor pode estar ordenado de forma crescente ou decrescente, mas precisa estar ordenado.
- **Estrutura de Dados Adequada:** Aplica-se perfeitamente a **vetores (arrays)**, que permitem **acesso direto** a qualquer elemento por meio de seu índice. Em listas encadeadas, mesmo que ordenadas, a busca binária não é eficientemente aplicável devido à impossibilidade de acesso direto ao elemento central sem percorrer a lista.

## 2. Funcionamento do Algoritmo

### 2.1 Passo a Passo Conceitual

1.  Definir os limites `min` (início) e `max` (fim) do intervalo de busca.
2.  Calcular o índice do meio: `meio = (min + max) / 2` (normalmente arredondando para baixo).
3.  Comparar o valor buscado com o elemento na posição `meio`.
    - Se for igual, o elemento foi encontrado. O algoritmo termina.
    - **Se o valor buscado for MAIOR** que o elemento do meio: descartar a metade esquerda, atualizando `min = meio + 1`.
    - **Se o valor buscado for MENOR** que o elemento do meio: descartar a metade direita, atualizando `max = meio - 1`.
4.  Repetir o processo a partir do passo 2 até encontrar o elemento ou até o intervalo de busca ficar vazio (`min > max`), indicando que o valor não existe.

### 2.2 Exemplo Prático (Vetor Crescente)

- Vetor: [3, 7, 12, 18, 21, 25, 30, 34, 39, 42, 50] (11 elementos)
- Busca: 50
    - Intervalo inicial: min=0, max=10. Meio = 5 (valor 25). 50 > 25 → busca na direita (min=6).
    - Novo intervalo: min=6, max=10. Meio = 8 (valor 39). 50 > 39 → busca na direita (min=9).
    - Novo intervalo: min=9, max=10. Meio = 9 (valor 42). 50 > 42 → busca na direita (min=10).
    - Novo intervalo: min=10, max=10. Meio = 10 (valor 50). Encontrado!
- O algoritmo realizou 4 comparações, enquanto a busca linear faria 11.

## 3. Vantagens e Desvantagens

### 3.1 Vantagens

- **Eficiência:** Extremamente mais rápido que a busca linear para **grandes volumes de dados**.
- **Previsibilidade:** O número máximo de comparações é conhecido e limitado a `log₂(n)`.

### 3.2 Desvantagens

- **Pré-requisito rígido:** Exige que os dados estejam previamente **ordenados**.
- **Implementação mais complexa:** É mais difícil de codificar corretamente (cuidado com índices) do que a busca linear, e pode ser implementada de forma **recursiva ou iterativa**.
- **Limitação Estrutural:** Não funciona eficientemente em listas encadeadas devido à falta de acesso direto.

## 4. Complexidade de Tempo (Big O)

- **Pior Caso:** **O(log n)**.
    - Ocorre quando o elemento é o último a ser encontrado após sucessivas divisões, ou quando se descobre que ele não está presente no vetor.
    - O valor exato do número máximo de comparações (`k`) para uma lista de tamanho `n` é o menor inteiro `k` tal que `2ᵏ ≥ n`, ou seja, `k = ⌈log₂(n)⌉`.
- **Melhor Caso:** **O(1)**.
    - Ocorre quando o elemento procurado está exatamente na posição central do vetor na primeira tentativa.

---

# QUESTÕES DE CONCURSOS - BUSCA BINÁRIA

## 1. Aplicabilidade e Escolha do Algoritmo

### 1.1 (AOCP/ITEP-RN/2021 - Perito Criminal)

- **Enunciado:** Vetor com algumas centenas de elementos **ordenados** e buscas constantes. Qual o método mais adequado?
- **Gabarito:** **B) Busca Binária**.
- **Análise:** Como o vetor está ordenado e as buscas são frequentes, a busca binária é a mais eficiente (O(log n)). Busca Linear/Sequencial seriam ineficientes (O(n)), e Bubble Sort/Quick Sort são algoritmos de ordenação, não de busca.

### 1.2 (CESGRANRIO/BANCO DO BRASIL - Agente de Tecnologia)

- **Enunciado:** Três coleções: I- array ordenado; II- lista encadeada desordenada; III- lista encadeada ordenada. Métodos mais eficientes.
- **Gabarito:** **B) I – binária; II – sequencial; III – sequencial**.
- **Análise:**
    - **I (Array ordenado):** **Binária** (acesso direto + ordenação = eficiência máxima).
    - **II (Lista encadeada desordenada):** **Sequencial** (única opção viável).
    - **III (Lista encadeada ordenada):** **Sequencial** (apesar de ordenada, a estrutura de lista encadeada impede o acesso direto necessário para a busca binária).

### 1.3 (FGV/IBGE - Analista Censitário)

- **Enunciado:** Para poder ser aplicado, o algoritmo de pesquisa binária exige que os elementos...
- **Gabarito:** **B) estejam ordenados**.
- **Análise:** A ordenação é o pré-requisito fundamental e inegociável. Os dados podem ser de qualquer tipo (não apenas números) e podem ser repetidos.

## 2. Complexidade e Número Máximo de Comparações

### 2.1 (FGV/TRF 1ª REGIÃO - Técnico Judiciário)

- **Enunciado:** Complexidade de tempo correta para a busca binária em uma lista de `n` elementos.
- **Gabarito:** **C) O(log n)**.
- **Análise:** É a definição da complexidade logarítmica. O(n), O(n log n) e O(n²) são complexidades de outros algoritmos (linear, mergesort, bubble sort, etc.).

### 2.2 (FGV/IMBEL - Analista Especializado)

- **Enunciado:** Número máximo de acessos em uma busca binária numa lista ordenada de 20 chaves.
- **Gabarito:** **B) 5**.
- **Análise:** O número máximo de comparações é `⌈log₂(20)⌉`. Como `log₂(16) = 4` e `log₂(32) = 5`, o valor de `log₂(20)` está entre 4 e 5. O valor máximo será o teto, ou seja, **5**.

### 2.3 (CESGRANRIO/TRANSPETRO/2018 - Analista de Sistemas)

- **Enunciado:** Vetor de 750 elementos. Número máximo de iterações da busca binária.
- **Gabarito:** **C) 10**.
- **Análise:** Calcula-se `⌈log₂(750)⌉`. `log₂(512)=9` e `log₂(1024)=10`. Como `750 > 512`, o teto é **10**.

### 2.4 (FCC/DPE-AM - Programador)

- **Enunciado:** Lista ordenada com 1.000 nomes. Máximo de comparações na busca binária.
- **Gabarito:** **B) 10 comparações**.
- **Análise:** `⌈log₂(1000)⌉`. `log₂(1000) ≈ 9.96`. O teto de 9.96 é **10**.

## 3. Descrição do Funcionamento do Algoritmo

### 3.1 (CS-UFG/PREF. MORRINHOS/GO - Técnico em Suporte)

- **Enunciado:** Descrição correta do funcionamento da busca binária.
- **Gabarito:** **D) O algoritmo opera em vetores ordenados... comparação do valor buscado com o valor do elemento central ... metade da esquerda ou direita ... recursivamente, até que o valor seja encontrado ou se descubra que não existe.**
- **Análise:**
    - A) Incorreta: "Binária" não se refere à conversão de dados.
    - B) Incorreta: Não opera em vetores não ordenados.
    - C) Incorreta: Não faz varredura nem usa mapa de bits.
    - D) Correta: É a descrição fiel do mecanismo.

### 3.2 (AOCP/IBGE - Analista Censitário)

- **Enunciado:** Análise de um passo a passo de algoritmo de busca (definição de min/max, cálculo da média, redirecionamento).
- **Gabarito:** **B) busca binária.**
- **Análise:** Os passos descritos (cálculo do meio, ajuste de `min` e `max` baseado no palpite) correspondem exatamente ao laço principal da busca binária.

## 4. Simulação do Algoritmo e Identificação de Algoritmos

### 4.1 (CESGRANRIO/ELETRONUCLEAR - Analista de Sistemas)

- **Enunciado:** Busca binária do número `50`. Elementos visitados na ordem: 54, 17, 33, 50. Qual o vetor?
- **Gabarito:** **D) [ 5, 17, 33, 50, 54, 60, 87, 93, 111, 121 ]**.
- **Análise:** Simulação da busca binária:
    1.  Vetor com 10 elementos. Índice do meio: 5 → valor **54**. (Primeiro visitado). Como 50 < 54, busca à esquerda.
    2.  Subvetor esquerdo: [5, 17, 33, 50]. Meio: índice 2 → valor **17** (segundo visitado). Como 50 > 17, busca à direita.
    3.  Subvetor direito: [33, 50]. Meio: índice 3 → valor **33** (terceiro visitado). Como 50 > 33, busca à direita.
    4.  Resta apenas o elemento no índice 4 → valor **50** (quarto visitado). Encontrado.
    Apenas o vetor da letra D reproduz essa sequência.

### 4.2 (CEBRASPE/BNB - Especialista Técnico)

- **Enunciado:** "O algoritmo a seguir apresenta um exemplo de busca sequencial." (descrição de algoritmo que faz trocas de elementos).
- **Gabarito:** **ERRADO**.
- **Análise:** O algoritmo descrito realiza comparações e **trocas de posição**, o que é característico de um **algoritmo de ordenação**, especificamente o **Bubble Sort**. Algoritmos de busca não alteram a posição dos elementos.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (AOCP/ITEP/2021) | **B** | Vetor ordenado + buscas constantes = Busca Binária. |
| **02** (CESGRANRIO/BB) | **B** | Binária para array ordenado; Sequencial para qualquer lista encadeada. |
| **03** (FGV/TRF/1) | **C** | Complexidade da Busca Binária: **O(log n)**. |
| **04** (CS-UFG/MORRINHOS) | **D** | Descrição correta do funcionamento (dividir para conquistar). |
| **05** (CESGRANRIO/ELETRONUCLEAR) | **D** | Vetor da alternativa D reproduz a sequência de visitas (54, 17, 33, 50). |
| **06** (FGV/IMBEL) | **B** | Para n=20, máximo de comparações = `⌈log₂(20)⌉` = **5**. |
| **07** (AOCP/IBGE) | **B** | Passo a passo descreve a **busca binária**. |
| **08** (CESGRANRIO/TRANSPETRO) | **C** | Para n=750, máximo de iterações = `⌈log₂(750)⌉` = **10**. |
| **09** (FGV/IBGE) | **B** | Requisito fundamental: elementos **ordenados**. |
| **10** (CEBRASPE/BNB) | **E** | Algoritmo descrito é o **Bubble Sort** (ordenação), não busca. |
| **11** (FCC/DPE-AM) | **B** | Para n=1000, máximo de comparações = **10**. |