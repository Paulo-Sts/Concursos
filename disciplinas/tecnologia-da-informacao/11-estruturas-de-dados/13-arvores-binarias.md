# Anotações – Estrutura de Dados – Árvores Binárias (Introdução e Conceituação)

## 1. Conceituação de Árvore Binária

### 1.1 Definição formal

- **Árvore binária** é uma árvore de **grau 2** (máximo 2 filhos por nó).
- Cada nó pode ter **0, 1 ou 2 filhos**.
- Estrutura vazia (`T = ∅`) ou composta por:
  - Um nó especial chamado **raiz**.
  - **Subárvore esquerda** (`TE`).
  - **Subárvore direita** (`TD`).

> ### 1.1.1 Representação de expressões matemáticas
> - Exemplo: `((a + b) / (c - d)) × (e + f)`
>   - Raiz: `×` (multiplicação).
>   - Subárvore esquerda: divisão `(a + b) / (c - d)`.
>   - Subárvore direita: soma `(e + f)`.

### 1.2 Graus possíveis em uma árvore binária

| GRAU DO NÓ | SIGNIFICADO |
| --- | --- |
| 0 | Nó folha (sem filhos) |
| 1 | Nó com apenas um filho (esquerdo ou direito) |
| 2 | Nó com dois filhos (esquerdo e direito) |

> ### 1.2.1 Comparação com árvores gerais
> - Árvores gerais não têm limite de filhos.
> - Árvores binárias limitam a no máximo **2 filhos por nó**.

## 2. Quantidade de Nós por Nível (Árvore Binária Completa)

Para uma árvore binária **completa** (todos os níveis preenchidos):

| NÍVEL | FÓRMULA | QUANTIDADE DE NÓS NO NÍVEL |
| --- | --- | --- |
| 0 | `2⁰` | 1 |
| 1 | `2¹` | 2 |
| 2 | `2²` | 4 |
| 3 | `2³` | 8 |
| ... | ... | ... |
| n | `2ⁿ` | `2ⁿ` |

- **Total de nós até o nível n** (inclusive): `2⁽ⁿ⁺¹⁾ - 1`
- Exemplo (níveis 0 a 3): `1 + 2 + 4 + 8 = 15 = 2⁴ - 1`

> ### 2.1 Importante
> - O nível da raiz é **0** (assim como a indexação de arrays em Java/Python).
> - Esta fórmula aplica-se a **árvores binárias completas/cheias**.

## 3. Árvore Binária vs. Árvore Binária de Busca (BST)

| CARACTERÍSTICA | ÁRVORE BINÁRIA GENÉRICA | ÁRVORE BINÁRIA DE BUSCA |
| --- | --- | --- |
| Organização dos valores | Qualquer ordem | Filhos à esquerda < raiz < filhos à direita |
| Restrição de ordenação | Não há | Sim (propriedade de busca) |
| Eficiência de busca | Pode ser O(n) | O(log n) em árvores balanceadas |

> ### 3.1 Atenção (pegadinha)
> - **Nem toda árvore binária é uma árvore binária de busca.**
> - Afirmativas do tipo *"em uma árvore binária, os nós da direita sempre têm valor maior que o pai"* são **falsas** para árvores binárias genéricas.
> - Isso só é verdade para **árvores binárias de busca**.

## 4. Estrutura de um Nó (Implementação Encadeada)

Cada nó de uma árvore binária geralmente contém:

| CAMPO | DESCRIÇÃO |
| --- | --- |
| `esquerdo` (left) | Ponteiro para o filho esquerdo |
| `conteúdo` (data) | Valor armazenado (chave) |
| `direito` (right) | Ponteiro para o filho direito |
| `p` (parent) | Ponteiro para o pai (opcional) |

## 5. Questões de Concurso Comentadas

### 5.1 (PR-4/UFRJ/2023 – Analista de TI)

**Item:** "Toda árvore com `n` nós que possui exatamente `n + 1` subárvores vazias entre suas subárvores esquerdas e direitas é denominada:"

**Gabarito:** **e) árvore binária**.

**Comentário:** A propriedade "n + 1 subárvores vazias" é característica de árvores binárias (cada nó tem dois ponteiros – para esquerda e direita).

### 5.2 (CESPE/CEBRASPE/2023/SEPLAN-RR – Analista)

**Item:** "Uma árvore binária deve ter, no mínimo, 3 nós."

**Gabarito:** **Errado (E)**.

**Comentário:** Uma árvore binária pode ser **vazia** (0 nós) ou ter apenas 1 nó (raiz sem filhos). Não há mínimo obrigatório.

### 5.3 (AVANÇA SP/2023 – Analista de TI)

**Item:** "Árvores cujos nós têm dois filhos (possivelmente vazios) e cada filho é designado como filho à esquerda ou filho à direita é chamada de:"

**Gabarito:** **e) Árvore Binária**.

**Comentário:** A definição descreve exatamente uma árvore binária (grau máximo 2, filhos rotulados como esquerdo/direito).

### 5.4 (QUADRIX/2022/SEDF – Professor)

**Item:** "Em uma árvore binária, todos os nós de uma subárvore direita são maiores que o nó raiz."

**Gabarito oficial:** **Certo** (controvérsia apontada pelo professor).

**Comentário do professor:** A afirmação está **errada** para árvores binárias genéricas. Isso só é verdade para **árvores binárias de busca (BST)**. O gabarito oficial deveria ser **Errado**.

### 5.5 (VUNESP/2021/TJM-SP – Desenvolvedor)

**Item:** Estrutura de dados com três campos (conteúdo, ponteiro esquerdo, ponteiro direito) → **a) Árvore binária**.

### 5.6 (OBJETIVA/2021/Prefeitura de Santa Maria – Analista)

**Item:** Estrutura com atributos `esquerda`, `direita` e `p` (pai) → **a) Árvores de busca binárias**.

**Comentário:** Embora a estrutura física seja de árvore binária, a questão menciona a existência de ponteiro para o pai, comum em implementações de BST. As demais alternativas são estruturas lineares.

### 5.7 (INSTITUTO AOCP/2020/Novo Hamburgo – Analista)

**Análise da árvore (nós A,B,C,D,E,F,G,H,I):**

- **d) TA é a subárvore enraizada em "A", portanto toda a árvore.** ✅
- As demais alternativas estão incorretas:
  - (a) A é raiz, não filho de todos.
  - (b) B e C são nós internos, não "caules".
  - (c) B tem grau 2, não 3; C tem grau 1, não 2.
  - (e) Nem todos os demais nós são folhas (B, C, E são internos).

**Gabarito:** **d**.

### 5.8 (QUADRIX/2019/CREA-GO – Analista)

**Item:** "Nas árvores binárias, os nós da direita sempre possuem valor superior ao do nó-pai."

**Gabarito:** **Errado (E)** (não é verdade para árvores binárias genéricas).

### 5.9 (INSTITUTO AOCP/2018/UFOB – Analista)

**Item:** "Para um nó raiz de uma árvore binária qualquer, sempre há dois nós filhos: esquerdo e direito."

**Gabarito:** **Falso**.

**Comentário:** A raiz pode ter 0, 1 ou 2 filhos. Subárvores podem estar vazias.

### 5.10 (FAURGS/2018/UFCSPA – Técnico)

**Item:** "Uma árvore binária é caracterizada por ter:"

**Alternativa correta:** **c) no máximo dois nós-filhos por nó-pai**.

### 5.11 (CESPE/2016/FUB – Técnico)

**Item:** "Uma estrutura do tipo árvore é considerada binária se e somente se um conjunto infinito de elementos denominados nós existir."

**Gabarito:** **Errado (E)**.

**Comentário:** Árvores binárias podem ser **finitas** (incluindo vazia). Não há exigência de infinitos elementos.

### 5.12 (CETRO/2015/AMAZUL – Engenheiro)

**Afirmativas:**

- I – "Árvores binárias permitem que cada nó tenha dois nós sucessores (filhos)." ✅ (máximo 2)
- II – "Raiz é o nó mais inferior da árvore..." ❌ (raiz é o nó mais **superior**)
- III – "Folha é qualquer nó que não tenha sucessores (filhos)." ✅

**Gabarito:** **e) I e III, apenas**.

### 5.13 (VUNESP/2014/DESENVOLVESP – Analista)

**Figura (árvore completa com todos os níveis preenchidos):** Árvore binária **completa/cheia**.

**Gabarito:** **a) Árvore Binária**.

### 5.14 (FCC/2011/TRT19 – Técnico)

**Item:** "Em uma árvore binária, todos os nós têm grau:"

**Gabarito:** **b) 0, 1 ou 2**.

### 5.15 (CESPE/2010/BASA – Técnico Científico)

**Item:** "Em uma árvore binária de busca, como em toda árvore binária, todos os nós têm grau máximo igual a 2. Entretanto, nem toda árvore binária pode ser considerada uma árvore binária de busca."

**Gabarito:** **Certo**.

**Comentário:** A primeira parte é verdadeira (grau máximo 2); a segunda parte também é verdadeira (nem toda árvore binária é BST).

### 5.16 (CESPE/2010/DETRAN-ES – Analista)

**Item:** "Denomina-se árvore binária a que possui apenas dois nós."

**Gabarito:** **Errado (E)**.

**Comentário:** Árvores binárias podem ter 0, 1, 2, 3... nós. "Apenas dois" é restritivo demais.

### 5.17 (FCC/2005/TRE-MG – Analista)

**Definição de árvore binária:** "Um conjunto finito de elementos que ou está vazio ou está dividido em 3 subconjuntos: um elemento chamado raiz; dois subconjuntos, cada um dos quais é, por si mesmo, uma árvore binária (subárvore direita e subárvore esquerda)."

**Gabarito (lacunas):** **c) I Uma árvore binária II raiz da árvore III uma árvore binária**.

## 6. Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Árvore binária** | Árvore de grau máximo 2 |
| **Grau do nó** | 0 (folha), 1 ou 2 |
| **Raiz** | Nível 0; único nó sem pai |
| **Nível** | Distância da raiz (raiz = nível 0) |
| **Número máximo de nós no nível n** | `2ⁿ` |
| **Árvore binária completa** | Todos os níveis preenchidos até o último |
| **Árvore binária de busca (BST)** | Esq < raiz < dir (ordenação) |

> ### 6.1 Pegadinhas comuns
> - **Nem toda árvore binária é BST.** Não assuma ordenação em questões genéricas.
> - **Árvore binária pode ser vazia** – muitas questões erram ao afirmar que "toda árvore binária tem pelo menos 1 nó".
> - **Grau máximo é 2**, mas nós podem ter grau 0 ou 1 também.
> - **Nível da raiz é 0** (na maioria das bancas).

## GABARITO DAS QUESTÕES (consolidado)

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (PR-4/UFRJ) | e |
| 02 (CESPE/2023) | E |
| 03 (AVANÇA SP) | e |
| 04 (QUADRIX/2022) | C (controvérsia – deveria ser E) |
| 05 (METROCAPITAL) | e |
| 1 (arquivo 2 – VUNESP) | a |
| 2 (OBJETIVA) | a |
| 3 (AOCP/2020) | d |
| 4 (QUADRIX/2019 – CREA) | E |
| 5 (QUADRIX/2019 – CRA) | E |
| 6 (AOCP/2018) | E |
| 7 (FAURGS/2018) | c |
| 8 (CESPE/2016) | E |
| 9 (CETRO/2015) | e |
| 10 (VUNESP/2014) | a |
| 11 (FCC/2011) | b |
| 12 (CESPE/2010 – BASA) | C |
| 13 (CESPE/2010 – DETRAN) | E |
| 14 (FCC/2005) | c |

---

*Material complementar às aulas "Árvores Binárias – Introdução e Conceituação I e II" (professor Rogério Gildo Araujo, Gran Concursos).*