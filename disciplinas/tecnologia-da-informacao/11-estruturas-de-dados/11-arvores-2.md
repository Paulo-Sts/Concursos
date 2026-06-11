# Anotações – Estrutura de Dados – Árvores: Grau, Nível e Altura

## 1. Grau de um Nó (Grau de Saída)

- **Definição:** número de **filhos** que um nó possui.
- **Nó folha:** grau = 0 (zero filhos).
- **Nó interno:** grau diferente de zero.

> ### 1.1 Relação com subárvores
> - O grau de um nó corresponde ao **número de subárvores** que têm esse nó como raiz.

## 2. Grau da Árvore

- É o **maior grau** entre todos os nós da árvore.
- Determinado pelo nó que possui o maior número de filhos.

## 3. Nível de um Nó

- Medida da **profundidade** do nó em relação à raiz.
- **Cálculo:** número de arestas (saltos) no caminho da raiz até o nó.
- **Raiz:** geralmente nível **0** (alguns autores usam nível 1; a maioria das bancas adota nível 0).
- À medida que se desce na árvore, o nível é incrementado.

## 4. Altura de um Nó

- Distância do nó até a **folha mais distante** abaixo dele.
- **Cálculo:** número de arestas no caminho mais longo do nó até uma folha descendente.
- **Nó folha:** altura = 0.

## 5. Altura da Árvore

- É a **altura do nó raiz**.
- Corresponde ao **nível mais alto** da árvore (distância da raiz à folha mais distante).

> ### 5.1 Diferença fundamental (atenção!)
> - **Nível:** da raiz **até** o nó (caminho descendente).
> - **Altura do nó:** do nó **até** a folha mais distante (caminho descendente a partir do nó).
> - Um mesmo nó pode ter nível pequeno e altura grande, ou vice-versa.

## 6. Exemplo Consolidado (árvore do material)

Considere a árvore com raiz **10** e estrutura:
```
        10
       /  \
      11   12
          / | \
         9 13 15
        / \    \
       7   5    20
```

### 6.1 Grau dos nós

| Nó | Filhos | Grau |
| --- | --- | --- |
| 10 | 11, 12 | 2 |
| 11 | – | 0 (folha) |
| 12 | 9, 13, 15 | 3 |
| 9 | 7, 5 | 2 |
| 13 | – | 0 (folha) |
| 15 | 20 | 1 |
| 7 | – | 0 (folha) |
| 5 | – | 0 (folha) |
| 20 | – | 0 (folha) |

- **Grau da árvore:** 3 (nó 12).

### 6.2 Nível (raiz = nível 0)

| Nó | Nível |
| --- | --- |
| 10 | 0 |
| 11, 12 | 1 |
| 9, 13, 15 | 2 |
| 7, 5, 20 | 3 |

- **Altura da árvore:** nível máximo = 3.

### 6.3 Altura dos nós

| Nó | Caminho até folha mais distante | Altura |
| --- | --- | --- |
| 7 | (já é folha) | 0 |
| 5 | (folha) | 0 |
| 20 | (folha) | 0 |
| 11 | (folha) | 0 |
| 13 | (folha) | 0 |
| 9 | 9 → 7 ou 5 → altura 1 | 1 |
| 15 | 15 → 20 → altura 1 | 1 |
| 12 | 12 → 9 → 7 (2 arestas) → altura 2 | 2 |
| 10 | 10 → 12 → 9 → 7 (3 arestas) → altura 3 | 3 (altura da árvore) |

## 7. Tabela Comparativa – Nível vs. Altura

| CONCEITO | DEFINIÇÃO | EXEMPLO (nó 12 na árvore acima) |
| --- | --- | --- |
| **Nível** | Distância da raiz até o nó | Nível = 1 |
| **Altura do nó** | Distância do nó até a folha mais distante abaixo | Altura = 2 |

## 8. Questões de Concurso Comentadas

### 8.1 (FUNDATEC/2023 – IF Farroupilha/RS)

**Árvore fornecida (nós A a K). Pergunta:** “O nó C possui, respectivamente, grau e nível:”

- **Grau do nó C:** 3 (conforme a figura, C tem 3 filhos).
- **Nível do nó C:** nível 1 (raiz A nível 0; B e C nível 1).

**Gabarito:** **b) 3 e 2? Cuidado: o gabarito no material original indica “b. 3 e 2”.**  
*Revisão: na figura, raiz A nível 0, seus filhos B e C nível 1 → nível de C = 1. O material aponta nível 2? Pode ser que a raiz esteja no nível 1 adotado pela banca. Mais seguro: seguir a definição mais comum (raiz nível 0).*

### 8.2 (COSEAC/2023/UFF – Técnico)

**Figura de árvore. Pergunta:** “A altura e o grau da árvore representada são, respectivamente:”

- Altura da árvore = 3 (maior nível: raiz nível 0 → níveis 0,1,2,3).
- Grau da árvore = 2 (nó com mais filhos = 2).

**Gabarito:** **d) 3 e 2**.

### 8.3 (QUADRIX/2022/CRMV-MS – Técnico)

**Item:** “Na definição de árvore, não há relação entre o número de subárvores de um nó e o grau de um nó, uma vez que são conceitos distintos.”

**Gabarito:** **Errado** (há relação direta: grau = número de subárvores).

### 8.4 (COSEAC/2019/UFF – Técnico)

**Afirmativas:**

- I – “O número de nível mais alto de uma árvore é conhecido como grau de uma árvore.” → **Falsa** (é a altura; grau é o maior número de filhos).
- II – “Quando um nó possui grau zero, diz-se que ele é um nó terminal ou folha.” → **Verdadeira**.
- III – “Árvores são estruturas de dados estáticas...” → **Falsa** (são dinâmicas).

**Sequência:** F, V, F → **Gabarito: b) F, V e F**.

### 8.5 (NUCEPE/2018/PC-PI – Perito Criminal) – questões 3,4,5

**Análise da árvore com raiz 18, filhos 10 e 20, etc.**

- **Questão 3 – nós 6,14,19,31 são folhas?** Sim, grau zero. (item B – considerado **Certo** no gabarito).
- **Questão 4 – “Os nós 10 e 20 estão no nível 1 da estrutura e são descendentes do nó raiz.”**  
  *Raiz 18 nível 0; 10 e 20 são nível 1. Afirmação **Certa**.*
- **Questão 5 – “A altura dos nós 4,14,19,31 é zero.”**  
  Folhas têm altura 0 → **Certo**.

### 8.6 (FCC/2017/TRE/SP – Técnico)

**Organização de diretório (Dados → Técnicos/Práticos → ...).**  
A estrutura de dados mais adequada para representar um diretório é **árvore**.  
A opção correta foi **d) árvore, que consegue armazenar este diretório, é de ordem 5** (a banca usou “ordem” para se referir ao grau máximo, que é 5).

### 8.7 (CESPE/2017/TRF1 – Analista)

**Item:** “A árvore representada abaixo tem grau 3.”

- Análise: a árvore é binária (grau máximo 2). Afirmação **Errada**.

### 8.8 (MPE/RS/2015 – Técnico Superior)

**Lacuna:** “Denomina-se _____ de um nodo de uma árvore o número de subárvores que são subordinadas diretamente a este nodo.”

**Gabarito:** **e) grau**.

### 8.9 (FCC/2011/TRT19 – Técnico)

**Item:** “Em uma árvore binária, todos os nós têm grau” → **b) 0, 1 ou 2**.

### 8.10 (FCC/2010/TRF4 – Analista)

**Afirmativas:**

- I – “O número de subárvores de um nodo denomina-se grau.” → **Correta**.
- II – “Uma árvore binária não pode ser nula.” → **Incorreta** (pode ser vazia).
- III – “Toda árvore, inclusive as nulas, possui um nodo especial denominado raiz.” → **Incorreta** (árvore nula não tem raiz).

**Gabarito:** **a) I, apenas**.

### 8.11 (IPAD/2009/COMPESA)

**Item incorreto:** “Altura de um nó v é o número de nós do caminho da raiz até o nó v.”  
- Isso é definição de **nível** (ou profundidade). Altura é o caminho do nó até a folha mais distante.

**Gabarito:** **d**.

### 8.12 (CONSULPLAN/2007/CHESF)

**Item incorreto:** “O nível diz qual é a quantidade de nós de uma árvore.”  
- Nível não é quantidade de nós; é a distância da raiz.

**Gabarito:** **e**.

## 9. Síntese para Revisão Rápida

| TERMO | DEFINIÇÃO | EXEMPLO (na árvore do item 6) |
| --- | --- | --- |
| **Grau do nó** | Número de filhos | Nó 12 → grau 3 |
| **Grau da árvore** | Maior grau entre todos os nós | 3 |
| **Nível (raiz nível 0)** | Distância da raiz ao nó (arestas) | Nó 7 → nível 3 |
| **Altura do nó** | Distância do nó à folha mais distante | Nó 12 → altura 2 |
| **Altura da árvore** | Altura da raiz = nível máximo | 3 |

> ### 9.1 Pegadinha comum
> - **Não confundir nível com altura:** nível mede distância da raiz **para baixo**; altura mede distância de um nó **para baixo** até uma folha.
> - **Grau da árvore** não é número de níveis, e sim o **máximo de filhos** que um nó possui.

## GABARITO DAS QUESTÕES DO ARQUIVO

| QUESTÃO | GABARITO |
| --- | --- |
| 1 (FUNDATEC/2023) | b |
| 2 (COSEAC/2023) | d |
| 3 (QUADRIX/2022 – item isolado) | E |
| 4 (COSEAC/2019) | b |
| 5 (NUCEPE/2018 – q3) | C (no contexto, certo) |
| 6 (NUCEPE/2018 – q4) | C |
| 7 (NUCEPE/2018 – q5) | E (a afirmativa era falsa? Na verdade, era certa; o gabarito final do bloco indica “E” para a questão 5? Verificar: o professor anotou como “E” na correção. Mas o item em si estava correto. Atenção!) |
| 8 (FCC/2017) | d |
| 9 (CESPE/2017) | E |
| 10 (MPE/RS/2015) | e |
| 11 (FCC/2011) | b |
| 12 (FCC/2010) | a |
| 13 (IPAD/2009) | d |
| 14 (CONSULPLAN/2007) | e |

---

*Material complementar às aulas "Árvores – Grau, Nível e Altura I e II" (professor Rogério Gildo Araujo, Gran Concursos).*