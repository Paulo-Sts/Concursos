# Anotações – Algoritmos Hierárquicos e DBSCAN

## 1. Algoritmos Hierárquicos

### 1.1 Conceito

- Algoritmos de agrupamento (clustering) que constroem uma **hierarquia de grupos**.
- O resultado é representado por um **dendrograma** (árvore de agrupamentos).
- **Não exigem** a definição prévia do número de clusters (K) – o usuário pode escolher após visualizar o dendrograma.

### 1.2 Tipos de abordagem

| ABORDAGEM | DIREÇÃO | DESCRIÇÃO |
| --- | --- | --- |
| **Aglomerativa (Bottom-Up)** | De baixo para cima | Cada ponto começa como um cluster individual; os clusters mais próximos são **unidos** sucessivamente até formar um único cluster. |
| **Divisiva (Top-Down)** | De cima para baixo | Todos os pontos começam em um único cluster; o cluster é **dividido** sucessivamente até que cada ponto seja um cluster individual. |

> ### 1.2.1 Dendrograma
> - Representação gráfica da hierarquia de agrupamentos.
> - Pode ser "cortado" em um nível específico para definir o número de clusters desejado.

## 2. DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

### 2.1 Conceito

- **DBSCAN** é um algoritmo de agrupamento **baseado em densidade**.
- **Não supervisionado.**
- **Não requer** a definição prévia do número de clusters (diferente do K-Means).

### 2.2 Parâmetros do DBSCAN

| PARÂMETRO | DESCRIÇÃO |
| --- | --- |
| **Epsilon (ε)** | Raio máximo ao redor de um ponto para considerar outro ponto como vizinho (distância máxima para formar um cluster). |
| **MinPts (Min Points)** | Número mínimo de pontos necessários para formar uma região densa (cluster). |

### 2.3 Funcionamento

1. Para cada ponto, verifica-se se há pelo menos `MinPts` pontos dentro do raio `ε`.
2. Pontos que atendem a essa condição são **pontos centrais** – formam ou expandem clusters.
3. Pontos que estão dentro do raio de um ponto central, mas não são centrais, são **pontos de borda** – pertencem ao cluster.
4. Pontos que não estão próximos o suficiente de nenhum cluster são classificados como **outliers (ruído)**.

### 2.4 Características do DBSCAN

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Robusto a outliers** | Pontos isolados são classificados como ruído – não distorcem os clusters. |
| **Número de clusters** | Não precisa ser definido previamente (diferente do K-Means). |
| **Forma dos clusters** | Pode encontrar clusters de **formas arbitrárias** (não apenas esféricos). |
| **Parâmetros** | Dois parâmetros: ε (raio) e MinPts (mínimo de pontos). |

## 3. K-Means vs. DBSCAN vs. Hierárquico (Comparação)

| CARACTERÍSTICA | K-MEANS | DBSCAN | HIERÁRQUICO |
| --- | --- | --- | --- |
| **Tipo** | Particional | Baseado em densidade | Hierárquico |
| **K (número de clusters)** | **Definido previamente** | Não necessário | Não necessário (definido após dendrograma) |
| **Sensível a outliers** | Sim | **Não** (outliers são ruído) | Pode ser |
| **Forma dos clusters** | Esféricos | Formas arbitrárias | Qualquer forma |
| **Parâmetros** | K | ε e MinPts | Métrica de distância e ligação |

## 4. Questões de Concurso Comentadas

### 4.1 (FGV/2024/EPE – Analista)

**Correspondência:**
- K-means: sensível ao número de clusters (K deve ser definido) → **(2)**
- Hierárquico: top-down/bottom-up, dendrograma → **(1)**
- K-means: avalia distâncias e atualiza centroides → **(2)**

**Gabarito: d) 2 – 1 – 1 – 2.**

### 4.2 (CESPE/CEBRASPE/2024/ANATEL – Especialista)

**Item:** "Uma das formas de se realizar um agrupamento é por meio de técnicas de agrupamento baseadas em hierarquia, em que se pode criar estrutura hierárquica de acordo com a proximidade entre os indivíduos, o que resulta em uma árvore binária."

**Gabarito: Certo (C).**

### 4.3 (CESPE/CEBRASPE/2025/SUSEP – Analista)

**Item:** "No agrupamento hierárquico, ao contrário do k-means, não se exige especificação prévia do número de clusters."

**Gabarito: Certo (C).**

### 4.4 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** "Algoritmo mais apropriado para agrupamento hierárquico (subdividir grupos em menores)."

**Gabarito: a) Agglomerative Hierarchical Clustering.**

### 4.5 (FGV/2024/CGM-BH – Auditor)

**Afirmativas:**
- Hierárquicos: aglomerativos e divisíveis. **(V)**
- Aglomerativo: bottom-up (começa com clusters individuais → vai unindo). **(F)** – a descrição dada foi de divisivo.
- Divisíveis: top-down (um cluster → dividido). **(V)**

**Gabarito: b) V – F – V.**

### 4.6 (CESPE/CEBRASPE/2025/MPE-CE – Analista)

**Item:** "Nos algoritmos aglomerativos, primeiro cada objeto é um grupo e depois combinam-se grupos; nos divisivos, todos começam em um único grupo e são subdivididos."

**Gabarito: Certo (C).**

### 4.7 (FGV/2024/TCE-PA – Auditor)

**Correspondência DBSCAN vs. K-Means:**
- Precisa de K inicial → **(1)** K-means.
- Mais robusto a outliers → **(2)** DBSCAN.
- Precisa de MinPts e ε → **(2)** DBSCAN.
- Determina centroides → **(1)** K-means.

**Gabarito: e) 1 – 2 – 2 – 1.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/EPE/2024) | d |
| 02 (CESPE/ANATEL/2024) | C |
| 03 (CESPE/SUSEP/2025) | C |
| 04 (CESGRANRIO/IPEA/2024) | a |
| 05 (FGV/CGM-BH/2024) | b |
| 06 (CESPE/MPE-CE/2025) | C |
| 07 (FGV/TCE-PA/2024) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Hierárquico Aglomerativo** | Bottom-up: cada ponto é um cluster; une os mais próximos. |
| **Hierárquico Divisivo** | Top-down: todos em um cluster; divide sucessivamente. |
| **Dendrograma** | Representação gráfica da hierarquia de clusters. |
| **DBSCAN** | Algoritmo baseado em densidade – não precisa de K. |
| **ε (Epsilon)** | Raio máximo para considerar vizinhos. |
| **MinPts** | Número mínimo de pontos para formar um cluster. |
| **Outlier** | Pontos não classificados em nenhum cluster (ruído). |
| **Robusto a outliers** | Característica do DBSCAN (diferente do K-Means). |

---

*Material complementar à aula "Algoritmos Hierárquicos e DBSCAN" (professor Vitor Kessler/Gran Concursos).*