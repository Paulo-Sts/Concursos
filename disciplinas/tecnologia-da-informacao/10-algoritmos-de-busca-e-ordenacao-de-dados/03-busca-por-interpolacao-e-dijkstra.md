# Anotações

# ALGORITMOS DE BUSCA – BUSCA POR INTERPOLAÇÃO E DIJKSTRA

## 1. Algoritmo de Busca por Interpolação

### 1.1 Definição e Conceito

- A **Busca por Interpolação** é uma evolução da busca binária, considerada uma versão mais avançada.
- É um algoritmo de busca em **vetores ordenados**.
- Em vez de dividir o vetor exatamente no meio (como a busca binária), ele **estima a posição provável** do elemento procurado com base em uma **interpolação linear**.

### 1.2 Funcionamento e Pré-Requisitos

- **Estimativa Inteligente:** O algoritmo calcula a posição provável do alvo (`X`) usando uma fórmula que considera os valores nas extremidades e o valor buscado. É como abrir um dicionário perto do começo para buscar uma palavra com "B".
- **Pré-Requisito:** Exige que os dados, além de **ordenados**, tenham uma **distribuição relativamente uniforme**. Se os dados são muito irregulares, a estimativa de posição pode não ser tão precisa.
- **Fórmula da Posição (Estimativa):**
    ```
    pos = inicio + ((alvo - arr[inicio]) * (fim - inicio)) / (arr[fim] - arr[inicio])
    ```
    - `alvo`: O valor que se deseja encontrar.
    - `arr[inicio]`: O valor do primeiro elemento do intervalo de busca.
    - `arr[fim]`: O valor do último elemento do intervalo de busca.

### 1.3 Exemplo de Funcionamento

- **Vetor Uniforme:** `[1, 4, 7, 10, 13, 16, 19, 22]` (8 elementos, crescendo no passo 3).
- **Buscar o valor `4`:**
    - `pos = 0 + ((4 - 1) * (7 - 0)) / (22 - 1)`
    - `pos = (3 * 7) / 21 = 21 / 21 = 1`.
    - O valor `4` está exatamente no índice `1`.
- **Buscar o valor `16`:**
    - `pos = 0 + ((16 - 1) * (7 - 0)) / (22 - 1)`
    - `pos = (15 * 7) / 21 = 105 / 21 = 5`.
    - O valor `16` está exatamente no índice `5`.

## 2. Algoritmo de Dijkstra

### 2.1 Definição e Propósito

- O algoritmo de Dijkstra é um algoritmo de **busca e otimização em grafos ponderados** (grafos com peso nas arestas).
- Seu objetivo é encontrar o **caminho de menor custo** (menor distância, menor tempo, menor peso) de um **nó inicial (origem) para todos os outros nós** de um grafo.

### 2.2 Características Fundamentais

- **Pesos Não Negativos:** O algoritmo exige que os **pesos das arestas sejam não negativos** (≥ 0). Ele não funciona corretamente com pesos negativos.
- **Algoritmo Guloso (*Greedy*):** Em cada etapa, ele toma a decisão que parece ser a melhor localmente (escolher o nó com menor distância acumulada), esperando que essa sequência de decisões locais ótimas leve a uma solução global ótima.
- **Aplicabilidade:** Funciona tanto em grafos **orientados** (com setas) quanto em grafos **não orientados**.
- **Complexidade de Tempo:** O(n²), onde 'n' é o número de vértices do grafo.
- **Aplicações Práticas:** Amplamente utilizado em sistemas de **GPS**, protocolos de **roteamento de redes**, planejamento logístico e análise de rotas.

### 2.3 Funcionamento Passo a Passo (Lógica Conceitual)

1.  **Inicialização:**
    - Marcar o nó inicial com **custo 0** (distância para ele mesmo).
    - Marcar todos os outros nós com **custo infinito** (∞) (ainda não alcançados).
2.  **Seleção:** Escolher o nó **não visitado** que possui o **menor custo atual**. Este será o nó a ser processado.
3.  **Relaxamento (Atualização de Vizinhos):** Para cada vizinho do nó atual, verificar se o caminho para ele passando pelo nó atual é mais curto (barato) do que o custo registrado até agora.
    - **Cálculo:** `custo_vizinho = custo_no_atual + peso_da_aresta`.
    - Se `custo_vizinho` for **menor** que o custo previamente registrado para aquele vizinho, atualiza-se o custo e registra-se que o melhor caminho para ele vem do nó atual.
4.  **Marcar como Visitado:** Após processar todos os vizinhos, o nó atual é marcado como **visitado**. Ele não será mais processado.
5.  **Repetição:** Repetir os passos 2 a 4 até que **todos os nós tenham sido visitados**.
6.  **Resultado Final:** Ao final, a tabela de custos indicará a menor distância do nó de origem para cada um dos outros nós do grafo.

---

# QUESTÕES DE CONCURSOS - BUSCA POR INTERPOLAÇÃO E DIJKSTRA

## 1. Identificação do Algoritmo de Busca

### 1.1 (CEBRASPE/TRT 7ª REG./2017 - Técnico Judiciário)

- **Enunciado:** Algoritmo de pesquisa em arquivo **previamente ordenado**, caracterizado por realizar **comparação de chaves e sucessivas divisões** no espaço de busca até encontrar o termo... Trata-se de um algoritmo de:
- **Gabarito:** **B) pesquisa binária.**
- **Análise:** A descrição de "sucessivas divisões no espaço" é a assinatura da busca binária. A busca por interpolação também divide o espaço, mas o faz por meio de uma estimativa, não por uma divisão fixa ao meio. A descrição é clássica da binária.

## 2. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CEBRASPE/TRT 7ª/2017) | **B** | "Sucessivas divisões no espaço" é a definição da **Busca Binária**. |