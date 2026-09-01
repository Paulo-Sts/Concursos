# Anotações – Estrutura de Dados – Árvores Binárias: Outros Tópicos (Cheia, Completa, Estritamente Binária, Zique-Zague)

## 1. Classificação das Árvores Binárias

### 1.1 Visão geral dos tipos

| TIPO | CARACTERÍSTICA PRINCIPAL | GRAUS PERMITIDOS |
| --- | --- | --- |
| **Estritamente Binária** | Nós têm grau 0 (folha) ou grau 2 (dois filhos) | 0 ou 2 (proibido grau 1) |
| **Cheia (Full)** | Estritamente binária + todas as folhas no **último nível** | 0 ou 2 |
| **Completa (Complete)** | Cheia até o penúltimo nível; folhas podem estar no último ou penúltimo nível | 0, 1 ou 2 (mas preenchimento da esquerda para a direita) |
| **Zique-Zague (Degenerada)** | Cada nó interno tem **exatamente 1 filho** (esquerdo ou direito) | 1 (nós internos) |

> ### 1.1.1 Relação entre os tipos (importante!)
> - **Toda árvore cheia é estritamente binária** (mas nem toda estritamente binária é cheia – as folhas podem não estar todas no último nível).
> - **Toda árvore cheia é completa** (mas nem toda completa é cheia – completa pode ter nós com grau 1 no penúltimo nível).
> - **Árvore cheia** = estritamente binária + completa.

## 2. Detalhamento por Tipo

### 2.1 Árvore Estritamente Binária

| PROPRIEDADE | VALOR |
| --- | --- |
| Graus permitidos | 0 ou 2 (não pode ter nó com grau 1) |
| Relação entre nós folhas e nós internos | `nós internos = nós folhas - 1` |
| Exemplo de aplicação | Árvores de Huffman, árvores de expressões |

**Exemplo visual:**
```
       A
      / \
     B   C
    / \   \
   D   E   F   ← F tem grau 2? Na verdade, F tem grau 0 (folha). Esta árvore NÃO é estritamente binária porque C tem grau 1 (apenas filho direito).
```

### 2.2 Árvore Binária Cheia (Full Tree)

| PROPRIEDADE | VALOR |
| --- | --- |
| Graus permitidos | 0 ou 2 (não há grau 1) |
| Posição das folhas | Todas no **último nível** (mesma profundidade) |
| Número total de nós (altura `h`, raiz nível 0) | `2^(h+1) - 1` |
| Número de folhas (altura `h`) | `2^h` |
| Número de nós internos | `2^h - 1` |

**Exemplo visual (árvore cheia de altura 2, raiz nível 0 → níveis 0,1,2):**
```
         A
       /   \
      B     C
     / \   / \
    D   E F   G   (todas as folhas no nível 2)
```

> ### 2.2.1 Fórmula do total de nós (decore!)
> - `total = 2^(h+1) - 1`, onde `h` é a altura da árvore (raiz nível 0, folhas nível h).
> - Exemplo: altura `h = 2` → `2^(3) - 1 = 8 - 1 = 7` nós.

### 2.3 Árvore Binária Completa (Complete Tree)

| PROPRIEDADE | VALOR |
| --- | --- |
| Preenchimento | Todos os níveis, exceto talvez o último, estão **completamente preenchidos** |
| Ordem das folhas | As folhas no último nível estão **o mais à esquerda possível** |
| Graus permitidos | 0, 1 ou 2 (pode haver nó com grau 1 no penúltimo nível) |
| Relação com árvore cheia | Toda árvore cheia é completa; nem toda completa é cheia |

**Exemplo visual (árvore completa, não cheia – falta um filho à direita no último nível):**
```
         A
       /   \
      B     C
     / \   /
    D   E F     (F está à esquerda; falta o filho direito de C)
```

> ### 2.3.1 Característica importante
> - As árvores completas são **cheias até o penúltimo nível**.
> - No último nível, os nós são preenchidos **da esquerda para a direita**.

### 2.4 Árvore Binária Zique-Zague (Degenerada)

| PROPRIEDADE | VALOR |
| --- | --- |
| Graus permitidos | Nós internos têm **grau 1** (exatamente um filho, esquerdo OU direito) |
| Folhas | Apenas uma folha (no final da cadeia) |
| Formato | Assemelha-se a uma **lista encadeada** (linear) |
| Altura máxima | Para `n` nós, a altura pode ser `n-1` (pior caso de árvore de busca) |

**Exemplo visual (zique-zague, sempre à direita):**
```
    A
     \
      B
       \
        C
         \
          D   (apenas um filho por nó)
```

## 3. Fórmulas e Cálculos (Decore!)

| GRANDEZA | FÓRMULA (raiz nível 0, altura `h`) |
| --- | --- |
| **Número máximo de nós no nível `k`** | `2^k` |
| **Total de nós em árvore cheia até nível `h`** | `2^(h+1) - 1` |
| **Total de nós em árvore completa (mínimo)** | `2^h` (quando apenas a raiz está no último nível? Cuidado) |
| **Total de nós em árvore completa (máximo)** | `2^(h+1) - 1` |
| **Número de folhas em árvore cheia** | `2^h` |
| **Altura máxima para `n` nós (árvore degenerada)** | `n - 1` |

> ### 3.1 Exemplo prático (questão CESPE)
> - Para uma árvore binária **completa** (cheia até o penúltimo nível) com **altura 3** (raiz nível 0, folhas no nível 3):
>   - Máximo de nós: `2^(4) - 1 = 15`
>   - Mínimo de nós: `8` (apenas a raiz e o mínimo para ter altura 3? Na verdade, uma árvore completa de altura 3 tem pelo menos 8 nós – nível 0:1, nível1:2, nível2:4, nível3:1 preenchido à esquerda = 8)

## 4. Questões de Concurso Comentadas

### 4.1 (INSTITUTO AOCP/2023/IF-MA – Analista de TI)

**Definição de árvore binária completa:** "todos os níveis, exceto talvez o último, estão completamente preenchidos, e todas as folhas no último nível estão o mais à esquerda possível."

**Pergunta:** alternativa correta sobre árvore binária completa.

**Análise das alternativas:**
- a) "altura sempre igual ao número de nós" → **FALSO**.
- b) "no máximo 2^(h+1) – 1 nós" → **VERDADEIRO** (é o máximo, não o exato).
- c) "no mínimo 2^(h+1) – 1 nós" → **FALSO** (esse é o máximo).
- d) "exatamente 2^(h+1) – 1 nós" → **FALSO** (só árvore cheia tem exatamente isso).
- e) "no máximo 2^h – 1 nós" → **FALSO** (fórmula errada).

**Gabarito:** **b**.

### 4.2 (FGV/2023/TJ-RN – Analista Judiciário)

**Item:** "[1] Numa árvore binária toda página folha possui a mesma profundidade."

**Gabarito:** **Errado (E)**.

**Comentário:** Isso só é verdade para **árvores binárias cheias**. Árvores binárias genéricas podem ter folhas em níveis diferentes.

### 4.3 (CESPE/CEBRASPE/2022/DPE-RO – Analista)

**Item:** "Uma árvore binária completa com 15 nós tem altura igual a:"

**Resolução:** `2^(h+1) - 1 = 15` → `2^(h+1) = 16` → `h+1 = 4` → `h = 3`.

**Gabarito:** **c) 3**.

### 4.4 (CCV/UFC/2019 – Técnico de TI)

**Item correto sobre árvores binárias:**
- a) Errado – definição confunde cheia com completa.
- b) Errado – "todos os nós devem ter 0 ou 2 filhos" é árvore estritamente binária, não condição para balanceamento.
- c) Errado – árvore não pode ter duas raízes.
- d) Errado – pode ser implementada estaticamente (array) se tamanho conhecido.
- e) **Correto** – definição de árvore binária de busca.

**Gabarito:** **e**.

### 4.5 (CS/UFG/2017 – Analista de Sistemas)

**Item:** "Dentre as árvores binárias que possuem sete nós, a maior altura possível é:"

**Resolução:** Maior altura = árvore degenerada (zique-zague) com 7 nós → altura máxima = 6 (raiz nível 0, último nó nível 6).

**Gabarito:** **b) 6**.

### 4.6 (FUNRIO/2016/IF-PA – Analista de TI)

**Item:** Árvore binária **cheia** com 1.048.575 chaves. Qual a altura?

**Resolução:** `2^(h+1) - 1 = 1.048.575` → `2^(h+1) = 1.048.576 = 2^20` → `h+1 = 20` → `h = 19`.

**Gabarito:** **c) 20?** Atenção: a questão pede altura `h`, e o resultado é 19. Mas as alternativas eram 10,15,20,25,30. O professor recomendou marcar o **mais próximo** → 20. O gabarido indicado no material é **c) 20**.

### 4.7 (VUNESP/2014/EMPLASA – Analista)

**Figura:** Árvore estritamente binária, cheia até o penúltimo nível, folhas no último nível → **árvore binária completa**.

**Gabarito:** **c) Binária Completa**.

### 4.8 (FUNCAB/2010/PRODAM – Analista de TI)

**Item:** Expressão para calcular número de nós de uma árvore binária cheia em função da altura `h` → `2^(h+1) - 1`.

**Gabarito:** **e) 2^(h+1) - 1**.

### 4.9 (FCC/2010/MPE-RN – Analista)

**Item:** "Uma árvore binária completa tem, no 5º nível, uma quantidade de nós igual a:"

**Atenção:** Se a raiz é nível **0**, o 5º nível é o nível de índice 5 → `2^5 = 32`. Se a raiz é nível **1**, o 5º nível é o nível de índice 4 → `2^4 = 16`. A banca considerou raiz nível 1 → **16**.

**Gabarito:** **e) 16**.

### 4.10 (CESPE/CEBRASPE/2009/ANAC – Especialista)

**Figura de árvore binária completa até o nível 10:**
- Total de nós = `2^(10+1) - 1 = 2^11 - 1 = 2048 - 1 = 2047` → **Certo**.
- Folhas no nível 5 (raiz nível 0) = `2^5 = 32` (não 2^5 * 2?).
- Profundidade 3 → nível 3 → folhas = `2^3 = 8` → **Certo**.

## 5. Síntese para Revisão Rápida

| TIPO | GRAU DOS NÓS | POSIÇÃO DAS FOLHAS | TOTAL DE NÓS (altura h, raiz nível 0) |
| --- | --- | --- | --- |
| **Estritamente binária** | 0 ou 2 (não 1) | qualquer | Não há fórmula fixa |
| **Cheia** | 0 ou 2 | todas no **último nível** | `2^(h+1) - 1` |
| **Completa** | 0,1 ou 2 | último ou penúltimo nível (preenchidas à esquerda) | entre `2^h` e `2^(h+1)-1` |
| **Zique-Zague (degenerada)** | 1 (exceto folha) | apenas uma folha | = n (número de nós) |

> ### 5.1 Pegadinhas comuns
> - **Árvore cheia ≠ árvore completa.** Toda cheia é completa, mas nem toda completa é cheia.
> - **Árvore completa pode ter nó com grau 1** (no penúltimo nível, quando falta um filho à direita).
> - **Nível da raiz:** muitas bancas adotam **nível 0**, mas algumas usam **nível 1**. Leia o enunciado com atenção.
> - **Altura máxima para n nós:** `n-1` (árvore degenerada).

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 1 (AOCP/2023) | b |
| 2 (FGV/2023) | E |
| 3 (CESPE/2022) | c |
| 4 (CCV/2019) | e |
| 5 (CS/UFG/2017) | b |
| 6 (AOCP/2016) | e |
| 1 (arquivo 3 – FUNRIO) | c |
| 2 (CCV/2016) | C (no gabarito) |
| 3 (VUNESP/2014) | c |
| 4 (FGV/2014) | d |
| 5 (FUNCAB/2010) | e |
| 6 (FCC/2010) | e |
| 7 (IPAD/2009) | b |
| 8 (FCC/2009 – TRE/PI) | a |
| 9 (FCC/2009 – TJ/SE) | d |
| 10 (CESPE/2009 – ANAC) | C, E, C |

---

*Material complementar às aulas "Árvores Binárias – Outros Tópicos I, II e III" (professor Rogério Gildo Araujo, Gran Concursos).*