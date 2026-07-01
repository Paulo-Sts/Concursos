# Anotações – Árvore de Decisão

## 1. Conceito de Árvore de Decisão

- **Árvore de decisão** é um algoritmo de aprendizado de máquina **supervisionado** que pode ser usado para **classificação** e **regressão**.
- Constrói uma estrutura em forma de árvore onde:
  - **Nó raiz (root node):** primeiro nó, contém o atributo que melhor separa os dados.
  - **Nós internos:** decisões baseadas em atributos.
  - **Folhas:** contêm a classe (classificação) ou a média (regressão).
- O algoritmo escolhe os atributos que **melhor dividem** os dados, reduzindo a **entropia** ou o **índice Gini**.

> ### 1.1 Exemplo prático
> - Atributo **cor** no topo: verde → maçã, amarelo → banana, vermelho → cereja/maçã.
> - A árvore divide o espaço de características em regiões retangulares e rotula cada região com uma classe.

## 2. Conceitos Fundamentais

| CONCEITO | DEFINIÇÃO | INTERPRETAÇÃO |
| --- | --- | --- |
| **Entropia** | Mede o nível de desordem ou incerteza de um conjunto de dados. | Quanto mais misturadas as classes, maior a entropia. Entropia = 0 → todos os exemplos são da mesma classe (nó puro). |
| **Ganho de Informação** | Mede o quanto a entropia diminui ao dividir os dados por um atributo. | Quanto maior o ganho, melhor o atributo para dividir. Escolhe o atributo que mais "organiza" o conjunto. |
| **Índice Gini** | Mede o nível de impureza de um nó (probabilidade de erro ao classificar aleatoriamente). | Gini = 0 → nó puro. Gini alto → nó misto (impuro). Melhor atributo = menor índice Gini. |

> ### 2.1 Entropia
> - **Máxima:** quando as classes estão perfeitamente equilibradas (ex.: 33% A, 33% B, 33% C).
> - **Mínima:** quando todos os exemplos pertencem a uma única classe.
> - **Fórmula:** `H(S) = -∑ p_i * log₂(p_i)`

## 3. Algoritmos de Árvore de Decisão

| ALGORITMO | CRITÉRIO DE DIVISÃO | TRABALHA COM NUMÉRICOS? | TRATA VALORES AUSENTES? | PODA? | REGRESSÃO? |
| --- | --- | --- | --- | --- | --- |
| **ID3** | Ganho de Informação (entropia) | Não (apenas categóricos) | Não | Não | Não |
| **C4.5** | Ganho de Informação Normalizado | Sim | Sim | Sim | Não |
| **CART** | Índice Gini (classificação) / Redução de Variância (regressão) | Sim | Sim | Sim | **Sim** |

> ### 3.1 Diferenças principais
> - **ID3** → mais antigo, só trabalha com variáveis **categóricas**, não faz poda, não trata valores ausentes.
> - **C4.5** → evolução do ID3, trabalha com **dados numéricos**, faz **poda**, trata **valores ausentes**.
> - **CART** → único que faz **regressão** (coloca a média na folha). Faz divisões **binárias** (sempre dois filhos).

### 3.2 Poda (Pruning)

- Técnica para evitar **overfitting** (árvore muito profunda e especializada).
- **Poda pré:** ocorre durante a construção da árvore.
- **Poda pós:** ocorre após a árvore ser construída (remove subárvores e substitui por folhas).
- **ID3** não faz poda; **C4.5** e **CART** fazem.

## 4. Vantagens da Árvore de Decisão

| VANTAGEM | DESCRIÇÃO |
| --- | --- |
| **Interpretabilidade (explicabilidade)** | É possível entender o caminho percorrido para chegar a uma decisão. |
| **Simplicidade** | Fácil de visualizar e explicar para não técnicos. |
| **Versatilidade** | Funciona para classificação e regressão. |
| **Pouco pré-processamento** | Não exige normalização ou padronização dos dados. |

> ### 4.1 Exemplo de explicabilidade
> - Um cliente teve o cartão VIP negado.
> - A árvore mostra: salário < R$ 20.000 → investimentos < R$ 200.000 → dívidas > R$ 1.000 → não VIP.
> - É possível explicar exatamente o motivo da decisão.

## 5. Desvantagem

- **Overfitting:** árvores muito profundas podem se especializar demais no conjunto de treinamento.
- **Solução:** poda (pruning), limitar profundidade (`max_depth`), validação cruzada.

## 6. Questões de Concurso Comentadas

### 6.1 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** Árvore de regressão com `max_depth=2`. Para `x1 = 0.6`, a decisão é:
- 0.6 > 0.1 → segue à direita.
- 0.6 ≤ 0.772 → segue à esquerda.
- Saída: **0.111**.

**Gabarito: c) 0.111.**

### 6.2 (CESPE/CEBRASPE/2024/CTI – Tecnologista)

**Item:** "Árvore de decisão estima a probabilidade de um evento ocorrer usando estimativa a priori."

**Gabarito: Errado (E).**

**Comentário:** A descrição não corresponde a árvores de decisão – seria mais adequada para **Naive Bayes**.

### 6.3 (FGV/2025/DPE-RO – Analista Programador)

**Item:** Técnica que recebe vetor de atributos e retorna um resultado (discreto ou contínuo), classificando como verdadeiro ou falso.

**Gabarito: b) árvore de decisão.**

### 6.4 (FGV/2025/TCE-PE – Analista)

**Item:** Detecção de fraudes em transações bancárias (supervisionado, classificação binária).

**Gabarito: a) Árvore de Decisão.**

### 6.5 (CESPE/CEBRASPE/2024/CTI – Análise e Mineração)

**Item:** "Árvore de decisão utiliza predição para identificar grupos com características em comum."

**Gabarito: Errado (E).**

**Comentário:** "Grupos" remete a **agrupamento (clusterização)** – não supervisionado. Árvore de decisão é supervisionada.

### 6.6 (FGV/2024/TRF-1 – Analista)

**Item:** Diferença entre ID3 e C4.5.

**Gabarito: d) O C4.5 permite a existência de atributos com valores contínuos, e o ID3 não.**

### 6.7 (CESPE/CEBRASPE/2025/FUNPRESP – Analista)

**Item:** "Árvores de decisão particionam iterativamente os dados em subconjuntos homogêneos baseados em variáveis explicativas."

**Gabarito: Certo (C).**

### 6.8 (CESPE/CEBRASPE/2025/PF – Perito)

**Item:** "Entropia é máxima quando as classes estão equilibradas e mínima quando todos pertencem a uma única classe."

**Gabarito: Certo (C).**

### 6.9 (FGV/2023/TCE-SP – Agente)

**Item:** "João precisa criar um modelo interpretável com regras de escolha complexas."

**Gabarito: b) árvore de decisão.**

### 6.10 (FGV/2024/CGE-PB – Auditor)

**Item:** "Modelo simples e interpretável para classificação binária."

**Gabarito: c) árvore de decisão.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/IPEA) | c |
| 02 (CESPE/CTI) | E |
| 03 (FGV/DPE-RO) | b |
| 04 (FGV/TCE-PE) | a |
| 05 (CESPE/CTI) | E |
| 06 (FGV/TRF-1) | d |
| 07 (CESPE/FUNPRESP) | C |
| 08 (CESPE/PF) | C |
| 09 (FGV/TCE-SP) | b |
| 10 (FGV/CGE-PB) | c |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Árvore de Decisão** | Algoritmo supervisionado para classificação e regressão. |
| **Entropia** | Mede a desordem – mínima (puro), máxima (equilibrado). |
| **Ganho de Informação** | Quanto a entropia diminui com a divisão – escolhe o melhor atributo. |
| **Índice Gini** | Mede impureza – menor é melhor. |
| **ID3** | Apenas categóricos, sem poda, sem valores ausentes. |
| **C4.5** | Numéricos, com poda, com valores ausentes. |
| **CART** | Numéricos, com poda, com regressão, divisões binárias. |
| **Poda** | Técnica para reduzir overfitting. |
| **Explicabilidade** | Principal vantagem da árvore de decisão. |

---

*Material complementar à aula "Árvore de Decisão" (professor Vitor Kessler/Gran Concursos).*