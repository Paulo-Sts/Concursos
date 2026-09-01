# Anotações – Estrutura de Dados – Árvores: Formas de Implementação

## 1. Visão Geral: Implementação de Árvores

- Assim como listas, pilhas e filas, as **árvores** também podem ser implementadas de **duas formas principais**:
  - **Sequencial (estática)** – usando arrays/vetores/arranjos.
  - **Encadeada (dinâmica)** – usando ponteiros.

| FORMA DE IMPLEMENTAÇÃO | ESTRUTURA SUBJACENTE | CARACTERÍSTICA PRINCIPAL |
| --- | --- | --- |
| **Sequencial (estática)** | Array / Vetor / Arranjo | Tamanho fixo; alocação contígua; pode desperdiçar memória |
| **Encadeada (dinâmica)** | Ponteiros | Tamanho variável; alocação sob demanda; sem desperdício de espaço vazio |

> ### 1.1 Relação com listas
> - Listas, filas e pilhas (estruturas lineares) também podem ser implementadas de forma sequencial ou encadeada.
> - Árvores seguem o mesmo princípio, mas com organização **hierárquica** (não linear).

## 2. Implementação Sequencial (Estática)

### 2.1 Como funciona

- Usa um **array** para armazenar os nós da árvore.
- Os nós de cada nível são armazenados de forma **contígua** (sequencial na memória), ordenados da esquerda para a direita.
- Quando um nó **não existe** (ausência de filho em determinada posição), o espaço correspondente no array é deixado **"em branco"** (vazio).

### 2.2 Exemplo fornecido

**Árvore hierárquica (representação visual):**
- Nível 0: A
- Nível 1: B, C (B filho esquerdo de A; C filho direito de A)
- Nível 2: D, E (filhos de B); F (filho esquerdo de C)
- Nível 3: G, H (filhos de D)

**Array resultante (posições preenchidas em ordem de nível):**

| Índice | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Nó | A | B | C | D | E | F | (vazio) | (vazio) | G | H | (vazio) | (vazio) |

> ### 2.2.1 Observação
> - Os espaços vazios correspondem a filhos ausentes em árvores não completas.
> - O **desperdício de memória** ocorre porque espaços vazios são reservados, mesmo sem dados.

### 2.3 Vantagens e desvantagens da implementação sequencial

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| Acesso direto ao nó pelo índice (cálculo de posição) | Tamanho fixo definido previamente (pouca flexibilidade) |
| Implementação simples para árvores completas/cheias | Desperdício de memória com espaços vazios |
| Sem overhead de ponteiros | Dificuldade para crescimento dinâmico |

> ### 2.3.1 Quando usar?
> - Adequada quando se conhece **previamente** o número máximo de nós e a árvore tende a ser **completa**.
> - Exemplo: árvores binárias completas (como *heaps*).

## 3. Implementação Encadeada (Dinâmica)

### 3.1 Como funciona

- Cada nó é alocado individualmente na memória.
- Cada nó contém:
  - Campo(s) **ponteiro(s)** para suas subárvores (filhos).
  - Campo para armazenamento do **dado** (informação).
- Nós **folha** têm todos os ponteiros apontando para **`null`** (ou `None`).

### 3.2 Exemplo: Árvore Binária (dois ponteiros)

**Estrutura de cada nó:**
```
[ filho_esquerdo | dado | filho_direito ]
```

**Representação visual (árvore binária):**
```
        A
       / \
      B   C
     / \   \
    D   E   F
```

- Cada nó tem **dois** ponteiros: *esquerdo* e *direito*.
- Folhas (D, E, F) têm ponteiros esquerdos e direitos **nulos**.

> ### 3.2.1 Terminologia
> - **Árvore binária:** cada nó tem no máximo 2 filhos → 2 ponteiros.
> - **Árvore ternária:** cada nó tem no máximo 3 filhos → 3 ponteiros.
> - **Árvore quaternária:** cada nó tem no máximo 4 filhos → 4 ponteiros.

### 3.3 Exemplo: Árvore Quaternária (quatro ponteiros)

**Estrutura de cada nó:**
```
[ filho0 | filho1 | filho2 | filho3 | dado ]
```

- Usada em estruturas como **árvores *quadtree*** (ex.: representação de imagens, sistemas de informação geográfica).
- Nós folha têm todos os 4 ponteiros nulos.

> ### 3.3.1 Relação entre tipo de árvore e número de ponteiros
> - **Grau máximo** da árvore = número de ponteiros por nó.
> - Uma árvore de **grau `n`** (ex.: `n=4`) é implementada com **n ponteiros** por nó.

### 3.4 Vantagens e desvantagens da implementação encadeada

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| **Tamanho dinâmico** – cresce conforme necessidade | **Overhead de memória** (cada nó guarda ponteiros) |
| **Sem desperdício** por espaços vazios | **Acesso não indexado** – requer percorrer ponteiros |
| Flexível para inserção/remoção de nós | Complexidade de implementação (gerenciamento de ponteiros) |

> ### 3.4.1 Quando usar?
> - Quando o **tamanho da árvore é desconhecido** ou variável.
> - Para árvores **esparsas** (poucos nós em relação à capacidade máxima).
> - Na maioria das aplicações práticas (ex.: árvores binárias de busca, AVL, rubro‑negras).

## 4. Questões de Concurso Comentadas

### 4.1 (CCV/UFC/2016/UFC – Técnico de TI)

**Item:** "As árvores binárias somente podem ser implementadas através de alocação dinâmica, devido à impossibilidade de determinar a quantidade de elementos que a árvore terá."

**Gabarito:** **Errado (E)**.

**Comentário:** É possível implementar árvores binárias de forma **estática** (com array) desde que se conheça previamente o número máximo de nós. A afirmação diz "somente" – isso torna o item falso.

### 4.2 (CESPE/CEBRASPE/2015/MEC – Desenvolvedor)

**Item:** "Uma árvore implementada por meio de encadeamento deve apresentar, além do nó pai, um encadeamento entre os nodos por meio de um campo de elo (ponteiro) e uma indicação de final de árvore por meio de um ponteiro nulo."

**Gabarito:** **Errado (E)**.

**Comentário:**
- Em árvores encadeadas, cada nó possui **ponteiros para os filhos**, não há um ponteiro específico para o "nó pai" (a menos que seja uma árvore com ligação para o pai).
- A "indicação de final de árvore" não existe como um ponteiro especial; os ponteiros dos filhos são **nulos** em nós que não têm filhos (folhas).
- A redação da afirmativa é confusa e incorreta.

### 4.3 (CESPE/CEBRASPE/2010/BANCO DA AMAZÔNIA – Técnico Científico)

**Item:** "As árvores, cujas relações de hierarquia e composição entre os dados são de subordinação, podem ser alocadas na memória por adjacência ou encadeamento, ao contrário do que ocorre com as listas lineares."

**Gabarito:** **Errado (E)**.

**Comentário:**
- A primeira parte está correta: árvores podem ser alocadas **por adjacência (sequencial)** ou **encadeamento**.
- O erro está em "ao contrário do que ocorre com as listas lineares". **Listas lineares também podem ser alocadas por adjacência (arrays) ou encadeamento.** Não há contraste; ambas as estruturas aceitam os dois tipos de alocação.

## 5. Síntese para Revisão Rápida

| IMPLEMENTAÇÃO | ESTRUTURA | ALOCAÇÃO | FLEXIBILIDADE | MEMÓRIA |
| --- | --- | --- | --- | --- |
| **Sequencial (estática)** | Array | Contígua | Tamanho fixo | Desperdício com espaços vazios |
| **Encadeada (dinâmica)** | Ponteiros | Dispersa | Tamanho variável | Overhead de ponteiros |

> ### 5.1 Definição do tipo de árvore pelo número de ponteiros
> - **Árvore binária:** cada nó tem **2 ponteiros** (esq/dir).
> - **Árvore ternária:** cada nó tem **3 ponteiros**.
> - **Árvore quaternária:** cada nó tem **4 ponteiros**.
> - Generalização: árvore de grau `k` → `k` ponteiros por nó.

> ### 5.2 Diferença fundamental entre listas encadeadas e árvores encadeadas
> - **Lista encadeada:** cada nó tem **um ponteiro** (para o próximo). Há um único caminho.
> - **Árvore encadeada:** cada nó pode ter **múltiplos ponteiros** (para os filhos). Há múltiplos caminhos (hierarquia).

## GABARITO DAS QUESTÕES DO ARQUIVO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CCV/UFC/2016) | E |
| 02 (CESPE/2015/MEC) | E |
| 03 (CESPE/2010/BASA) | E |

---

*Material complementar à aula "Árvores – Formas de Implementação" (professor Rogério Gildo Araujo, Gran Concursos).*