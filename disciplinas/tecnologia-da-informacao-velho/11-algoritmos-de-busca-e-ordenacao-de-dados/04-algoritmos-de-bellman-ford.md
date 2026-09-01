# Anotações

# ALGORITMOS DE BELLMAN-FORD E HASH

## 1. Algoritmo de Bellman-Ford

### 1.1 Definição e Propósito

- O algoritmo de **Bellman-Ford** é um algoritmo de **busca e otimização em grafos ponderados** utilizado para encontrar o **caminho de menor custo** de um nó inicial (origem) para todos os outros nós do grafo.

### 1.2 Características Fundamentais

- **Diferencial Principal:** Diferentemente do algoritmo de Dijkstra, o Bellman-Ford **funciona com arestas de peso negativo**. Dijkstra exige pesos não negativos.
- **Detecção de Ciclos Negativos:** Se, após o número máximo de iterações, ainda for possível reduzir o custo de algum caminho, o algoritmo identifica a presença de um **ciclo de custo negativo**. Nessa situação, ele interrompe a execução e sinaliza que não é possível calcular um caminho mínimo confiável.
- **Abordagem:** Adota uma abordagem centrada nas **arestas**. Em cada iteração, **todas as arestas** do grafo são percorridas para verificar se há um caminho mais curto para os vértices vizinhos.
- **Número de Iterações:** O algoritmo realiza exatamente **V - 1 iterações** (onde V é o número de vértices) para garantir que o menor caminho seja encontrado (se não houver ciclo negativo).
- **Complexidade de Tempo:** **O(V · E)**, onde V é o número de vértices e E é o número de arestas.

### 1.3 Funcionamento Passo a Passo

1.  **Inicialização:** Marcar o nó inicial com custo 0. Todos os outros nós recebem custo infinito (∞).
2.  **Relaxamento Global:** Repetir V - 1 vezes o processo de "relaxamento" para cada aresta `(u, v)` do grafo:
    - Se `custo[u] + peso(u, v) < custo[v]`, então atualizar `custo[v] = custo[u] + peso(u, v)`.
3.  **Verificação de Ciclo Negativo:** Executar mais uma iteração (a V-ésima) de relaxamento sobre todas as arestas. Se **qualquer** custo for atualizado nessa iteração extra, significa que existe um **ciclo negativo** no grafo.

## 2. Busca por Tabela Hash (Hashing)

### 2.1 Definição e Propósito

- A busca por **hash** (ou *hashing*) é uma técnica de **acesso direto** que utiliza uma **função de hash** para calcular o endereço (índice) de armazenamento de um dado a partir de sua chave (k).
- **Objetivo:** Localizar dados de forma extremamente rápida.
- **Estrutura:** Os dados são armazenados em uma **tabela hash** (tabela de espalhamento).

### 2.2 Funcionamento e Características

- **Função de Hash (`h(k)`):** Uma função que recebe a chave `k` de um elemento e retorna um número inteiro, que é o **índice** da tabela onde o elemento será armazenado ou buscado.
- **Determinismo:** A função é **determinística**. Para a mesma chave, a função sempre retornará o mesmo índice.
- **Colisão:** Uma **colisão** ocorre quando duas chaves diferentes (`k1` e `k2`) geram o mesmo índice (`h(k1) == h(k2)`). As estratégias para tratar colisões são essenciais para o funcionamento da tabela hash.
- **Boa Função de Hash:** Uma função eficiente deve ter baixa taxa de colisão, distribuição uniforme dos dados pela tabela e processamento otimizado.

### 2.3 Tratamento de Colisões: Overflow Area

- **Técnica:** Área de Overflow (ou Encadeamento Externo).
- **Funcionamento:** Quando ocorre uma colisão, o novo elemento é armazenado em uma **área auxiliar** (fora da tabela principal). Os elementos que colidiram no mesmo índice são ligados sequencialmente (como em uma lista encadeada).
- **Remoção (Lazy Deletion):** Ao remover um elemento da área de overflow, o espaço não deve ficar simplesmente vazio. Deve-se deixar uma **marcação** (ex: *flag* "D" de deletado) para que a busca por outros elementos da lista não seja interrompida prematuramente ao encontrar um "buraco", continuando até achar um espaço realmente nunca utilizado.

### 2.4 Complexidade de Tempo (Big O)

- **Caso Médio (com boa função de hash e carga balanceada):** **O(1)**. O acesso é direto e praticamente constante.
- **Pior Caso (muitas colisões, função hash ruim):** **O(n)**. Se todos os elementos colidem e a estrutura vira uma lista sequencial, a busca se torna uma busca linear.

---

# QUESTÕES DE CONCURSOS - BELLMAN-FORD E HASH

## 1. Algoritmo de Bellman-Ford

### 1.1 (CESPE-CEBRASPE/INPI/2024 - Analista)

- **Enunciado:** "Os algoritmos de Dijkstra e de Bellman-Ford resolvem o problema de caminhos mais curtos de única origem. Enquanto este aceita arestas de pesos negativos, aquele aceita somente arestas não negativas."
- **Gabarito:** **CERTO**.
- **Análise:** A afirmação está perfeitamente correta e descreve a principal diferença entre os dois algoritmos. Bellman-Ford suporta pesos negativos; Dijkstra, não.

## 2. Busca por Tabela Hash (Hashing)

### 2.1 (INSTITUTO CONSULPLAN/TJ-MA/2024 - Analista Judiciário)

- **Enunciado:** Considerando uma tabela Hash com uma boa função de Hash e carga balanceada, qual é a complexidade de tempo médio para a operação de busca?
- **Gabarito:** **A) O(1)**.
- **Análise:** Sob condições ideais (boa função, balanço de carga), o tempo médio de busca em uma tabela hash é constante. O(n) é o pior caso, e O(log n) é típico de árvores balanceadas.

### 2.2 (FGV/PGM NITERÓI/2023 - Analista de Tecnologia)

- **Enunciado:** Base de dados com centenas de milhares de registros, chave de busca é CPF. Método de busca que oferece a **melhor complexidade**.
- **Gabarito:** **E) Tabela Hash**.
- **Análise:** A melhor complexidade média é a da Tabela Hash (O(1)). A busca binária em um array teria O(log n), que é muito bom, mas a hash oferece a melhor performance teórica.

### 2.3 (FGV/SEE-PE/2016 - Professor)

- **Enunciado:** Tabela hash com função razoavelmente protegida de conflitos. O número **médio de acessos** ao disco para localizar uma chave é mais próximo de:
- **Gabarito:** **E) 2**.
- **Análise:** Em uma tabela hash bem projetada, o esperado é localizar o dado no primeiro acesso (índice calculado). Se houver colisão, uma verificação adicional a resolve. Portanto, a média se aproxima de 2 acessos.

## 3. Diferenciação entre Algoritmos de Busca e Ordenação

### 3.1 (COSEAC/UFF/2023 - Técnico de Laboratório)

- **Enunciado:** São algoritmos de busca possíveis para utilização, **EXCETO**:
- **Gabarito:** **E) quicksort**.
- **Análise:** Esta é uma pegadinha de prova, mas simples. A questão lista pesquisa sequencial, binária, interpolação e hashing, que são todos algoritmos de busca. **Quicksort** é um algoritmo de ordenação, não de busca.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESPE/INPI/2024) | **C** | Bellman-Ford aceita pesos negativos; Dijkstra não. |
| **02** (INST. CONSULPLAN/2024) | **A** | Boa função hash + carga balanceada = complexidade média **O(1)**. |
| **03** (COSEAC/UFF/2023) | **E** | Quicksort é algoritmo de ordenação, não de busca. |
| **04** (FGV/PGM/2023) | **E** | Tabela Hash oferece a **melhor complexidade** (O(1)) para busca. |
| **05** (FGV/SEE-PE/2016) | **E** | Número médio de acessos em hash com poucos conflitos é próximo de **2**. |