# Anotações – Estrutura de Dados – Árvores (Introdução e Conceituação)

## 1. Conceitos Fundamentais

### 1.1 Estruturas Lineares vs. Não Lineares

| TIPO | ESTRUTURAS | CARACTERÍSTICA |
| --- | --- | --- |
| **Lineares** | Listas, Pilhas, Filas | Elementos organizados em sequência (ordem linear). Cada elemento tem um predecessor e um sucessor (exceto extremos). |
| **Não lineares** | Árvores, Grafos | Elementos organizados de forma **hierárquica** (relações pai‑filho). Não há uma única ordem linear. |

> ### 1.1.1 Definição (SELECON/2023)
> “Tipo abstrato de dados que armazena elementos de maneira hierárquica. Com exceção do elemento do topo, cada elemento da estrutura tem um elemento pai e zero ou mais elementos filhos.” → **Árvore**.

### 1.2 Terminologia Básica

| TERMO | DEFINIÇÃO |
| --- | --- |
| **Nó (ou nodo)** | Posição na árvore que armazena um valor. |
| **Raiz (root)** | Nó no topo da árvore; não possui pai. Dele descendem todos os outros nós. |
| **Nó pai** | Nó que está imediatamente acima de outro nó (na direção da raiz). |
| **Nó filho** | Nó que está imediatamente abaixo de outro nó (na direção oposta à raiz). |
| **Nós irmãos** | Nós que compartilham o mesmo pai. |
| **Nó folha (terminal/externo)** | Nó que **não possui filhos**. Está no nível mais baixo da hierarquia. |
| **Aresta (edge)** | Conexão (linha) que liga dois nós. |
| **Subárvore** | Conjunto formado por um nó e todos os seus descendentes. |

> ### 1.2.1 Observações importantes
> - A **raiz** é o único nó sem pai.  
> - **Folhas** podem ter grau (número de filhos) igual a zero.  
> - Em uma árvore, **existe um único caminho entre a raiz e qualquer outro nó**.

### 1.3 Propriedades e Medidas

| PROPRIEDADE | DESCRIÇÃO | EXEMPLO (imagem da aula) |
| --- | --- | --- |
| **Nível (nível)** | Distância da raiz até o nó (raiz = nível 0 ou nível 1 – a maioria adota nível 0). | Raiz nível 0, seus filhos nível 1, netos nível 2, etc. |
| **Altura (height)** | Maior nível alcançado na árvore (número de arestas do caminho mais longo entre raiz e uma folha). | Árvore com níveis 0,1,2,3 → altura = 3. |
| **Grau de um nó** | Número de filhos que o nó possui. | Nó folha: grau 0; nó com 2 filhos: grau 2. |
| **Grau da árvore** | Maior grau entre todos os nós da árvore. | Se a raiz tem 3 filhos e nenhum outro nó tem mais que 2, o grau da árvore é 3. |

> ### 1.3.1 Exemplo didático (árvore com raiz 10)
> - Nó 10 (raiz) tem grau 3 (filhos 11, 12).  
> - Nó 12 tem grau 3 (filhos 9, 13, 15).  
> - Nó 9 tem grau 2 (filhos 7, 5).  
> - Nó 15 tem grau 1 (filho 20).  
> - Folhas: 11, 13, 7, 5, 20.  
> - Níveis: 10 (0), 11 e 12 (1), 9,13,15 (2), 7,5,20 (3). Altura = 3.

## 2. Representações de Árvores

| TIPO | DESCRIÇÃO | EXEMPLO (dado na aula) |
| --- | --- | --- |
| **Por parênteses aninhados** | Usa parênteses para aninhar subárvores. | (10 (11) (12 (9 (7)(5)) (13) (15 (20)))) |
| **Por diagrama de inclusão** | Conjuntos concêntricos: o nó raiz contém todos os outros; cada subárvore é um subconjunto. | Raiz 10 engloba 11 e 12; 12 engloba 9,13,15; etc. |
| **Hierárquica (mais comum)** | Diagrama em árvore com nós e arestas, raiz no topo e folhas na base. | Estrutura clássica de árvore (ex.: organograma). |

## 3. Questões de Concurso Comentadas

### 3.1 (SELECON/2023 – Prefeitura de Barra do Bugres)

**Item:** “tipo abstrato de dados que armazena elementos de maneira hierárquica. Com exceção do elemento do topo, cada elemento da estrutura tem um elemento pai e zero ou mais elementos filhos” – refere‑se a:

**Gabarito:** **d) árvores**.

**Comentário:** Listas, filas e pilhas são TADs lineares; apenas árvores são hierárquicas.

### 3.2 (QUADRIX/2023 – CREFITO‑7ª Região)

**Itens (julgue):**

a) “Nas árvores, os nós que estão nos níveis mais baixos da hierarquia são chamados de folhas.” → **Certo**.  
b) “Na estrutura hierárquica conhecida como árvore, os elementos são organizados em níveis ou camadas, com um elemento raiz no topo.” → **Certo**.  
c) “Em uma árvore, cada nó deve ter, no mínimo, um nó filho.” → **Errado** (nós folha não têm filhos).

### 3.3 (FURB/2023 – FURB/SC)

**Afirmativas sobre estruturas de dados:**

- I – Árvore: estrutura hierárquica, cada nó tem zero ou mais filhos. **(V)**  
- II – Fila: princípio LIFO? (Falso – fila é FIFO). **(F)**  
- III – Pilha: princípio FIFO? (Falso – pilha é LIFO). **(F)**  
- IV – Existem listas encadeadas, duplamente encadeadas e circulares. **(V)**

**Gabarito:** **c) I e IV, apenas**.

### 3.4 (QUADRIX/2022 – PRODAM‑AM)

**Item:** “Estrutura muito útil para implementação de algoritmos que necessitam de estruturas hierárquicas, sendo caracterizada como bidimensional, não linear” → **d) árvore**.

### 3.5 (QUADRIX/2022 – AM/PROGRAMADOR)

**Item:** “Nó do topo da árvore, do qual descendem os demais nós” → **c) raiz**.

### 3.6 (CONSULPLAN/2022 – MPE‑PA)

**Afirmativas sobre árvores:**

I – “Todos os nós possuem um nó pai e zero ou mais filhos.” → **Falso** (a raiz não tem pai).  
II – “Nó que não possui filho é denominado folha.” → **Verdadeiro**.  
III – “Subárvore de um nó consiste nesse nó e todos os seus descendentes.” → **Verdadeiro**.

**Gabarito:** **d) II e III, apenas**.

### 3.7 (FGV/2015 – DPE‑MT)

**Item:** “Estruturas lineares e não lineares, respectivamente” → **d) Pilha e árvore binária de busca** (pilha é linear; árvore é não linear).

### 3.8 (FGV/2013 – AL‑MT)

**Item:** “Nó de uma árvore sem nós filhos” → **e) folha**.

### 3.9 (FUNDEP/2012 – MPE‑MG)

**Afirmativas sobre árvores:**

I – “Todos os nós podem ser acessados a partir da raiz.” → **V** (caminho único).  
II – “Estruturas muito eficientes no armazenamento de grandes quantidades de dados.” → **V** (ex.: índices de BD).  
III – “Existem vários caminhos entre a raiz e qualquer outro nó.” → **F** (existe apenas um).

**Gabarito:** **a) apenas I e II**.

### 3.10 (CESPE/2012 – BANCO DA AMAZÔNIA)

**Item:** “O tipo de dados árvore representa organizações hierárquicas entre dados.” → **Certo**.

### 3.11 (CESPE/2011 – MEC)

**Item:** “Árvore é uma coleção finita de dados, em que um deles é denominado raiz e os demais, folhas. Não é possível que a árvore seja nula.” → **Errado**. Justificativa: existem nós internos (não folha); a árvore pode ser vazia (conjunto vazio).

### 3.12 (CONSULPLAN/2006 – Prefeitura de Natal)

**Item:** “Linha que liga dois nós de uma árvore é denominada” → **a) aresta**.

## 4. Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO / VALOR |
| --- | --- |
| **Raiz** | Nó sem pai; topo da árvore. |
| **Folha** | Nó sem filhos. |
| **Nós irmãos** | Mesmo pai. |
| **Nível** | Distância da raiz (raiz = 0, mais comum). |
| **Altura** | Maior nível + 1 ou número de arestas do caminho mais longo (depende da definição). |
| **Grau de um nó** | Número de filhos. |
| **Grau da árvore** | Máximo grau entre todos os nós. |
| **Caminho único** | Entre a raiz e qualquer nó existe exatamente um caminho. |

> ### 4.1 Pegadinha comum
> - A raiz **não tem pai**; as folhas **não têm filhos**.
> - Árvore **não é uma estrutura linear** (diferente de listas, pilhas, filas).
> - Árvores são **hierárquicas** e muito usadas em bancos de dados (ex.: índices B‑Tree).

## GABARITO DAS QUESTÕES (consolidado)

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (SELECON) | d |
| 02 (QUADRIX/2023 – a) | C |
| 02 (QUADRIX/2023 – b) | C |
| 02 (QUADRIX/2023 – c) | E |
| 03 (FURB) | c |
| 04 (QUADRIX/2022 – PRODAM) | d |
| 05 (QUADRIX/2022 – PROGRAMADOR) | c |
| 06 (CONSULPLAN/2022 – MPE‑PA) | d |
| 07 (FGV/2015) | d |
| 08 (FGV/2013) | e |
| 09 (FUNDEP/2012) | a |
| 10 (CESPE/2012) | C |
| 11 (CESPE/2011) | E |
| 12 (CONSULPLAN/2006) | a |

---

*Material complementar às aulas "Árvores – Introdução e Conceituação I e II" (professor Rogério Gildo Araujo, Gran Concursos).*