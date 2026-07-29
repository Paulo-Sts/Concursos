# Anotações – K-Means (K-Médias)

## 1. Conceito de K-Means

- **K-Means** é um algoritmo de aprendizado de máquina **não supervisionado** usado para **agrupamento (clustering)**.
- **Objetivo:** particionar um conjunto de dados em **K grupos (clusters)** de modo que:
  - Elementos **dentro do mesmo grupo** sejam **semelhantes** entre si.
  - Elementos **de grupos diferentes** sejam **dissimilares**.

> ### 1.1 K-Means vs. K-NN (não confundir!)
> - **K-Means:** não supervisionado, agrupamento (clustering).
> - **K-NN:** supervisionado, classificação/regressão.
> - São algoritmos **completamente diferentes** – a banca pode tentar confundir!

## 2. Funcionamento do K-Means

### 2.1 Passos do algoritmo

1. **Definir K:** o cientista de dados escolhe o número de grupos (clusters).
2. **Inicialização:** K centroides são posicionados **aleatoriamente** no espaço n-dimensional.
3. **Atribuição:** cada ponto de dado é atribuído ao **centroide mais próximo** (distância Euclidiana).
4. **Atualização:** os centroides são recalculados como a **média** dos pontos atribuídos a cada cluster.
5. **Repetição:** os passos 3 e 4 são repetidos **iterativamente** até que os centroides **parem de se mover** (convergência).

> ### 2.2 Convergência
> - O algoritmo converge quando os centroides não se movem mais entre iterações.
> - A convergência pode depender da **inicialização dos centroides**.

## 3. Classificação dos Algoritmos de Agrupamento

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Particional (Partitivo)** | Divide o espaço n-dimensional em K grupos. | **K-Means** |
| **Hierárquico** | Cria uma hierarquia de grupos (dendrograma). | Agrupamento hierárquico (aglomerativo/divisivo) |
| **Baseado em Densidade** | Forma grupos com base na densidade de pontos. | DBSCAN |
| **Baseado em Grade** | Divide o espaço em células de grade. | STING, CLIQUE |
| **Baseado em Grafo** | Utiliza grafos para formar grupos. | Spectral Clustering |

> ### 3.1 K-Means é um algoritmo **particional**, não hierárquico.

## 4. Características do K-Means

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Tipo de aprendizado** | Não supervisionado |
| **Tipo de problema** | Agrupamento (clustering) |
| **Parâmetro K** | Número de clusters (definido pelo usuário) |
| **Centroide** | Média dos pontos do cluster |
| **Métrica de distância** | Geralmente distância Euclidiana |
| **Inicialização** | Centroides são escolhidos aleatoriamente |
| **Resultado** | K grupos de dados semelhantes |

> ### 4.1 Importância da inicialização
> - Uma boa inicialização dos centroides **melhora** a qualidade dos clusters.
> - O algoritmo pode ser executado múltiplas vezes com diferentes inicializações.

## 5. Aplicações Típicas

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Segmentação de clientes** | Agrupar clientes por comportamento de compra. |
| **Análise de perfis** | Identificar grupos de usuários com interesses comuns. |
| **Detecção de padrões atípicos** | Identificar registros que não se encaixam em nenhum grupo. |
| **Agrupamento de documentos** | Organizar textos por assunto. |
| **Segmentação de imagens** | Separar regiões de uma imagem. |

## 6. Questões de Concurso Comentadas

### 6.1 (FGV/2025/TCE-PE – Auditor)

**Item:** "Dados não rotulados, descobrir grupos de registros similares."

**Gabarito: b) K-means.**

**Comentário:** K-means é um algoritmo não supervisionado para agrupamento – exatamente o que o problema descreve.

### 6.2 (FGV/2024/PREF. MACAÉ – Analista)

**Item:** "Técnica mais adequada para identificar agrupamentos em dados não rotulados."

**Gabarito: b) K-means.**

### 6.3 (CESPE/CEBRASPE/2025/EMBRAPA – Analista)

**Item:** "O algoritmo de aprendizagem supervisionada K-means é amplamente utilizado para classificação de dados rotulados."

**Gabarito: Errado (E).**

**Comentário:** K-means é **não supervisionado** e usado para **agrupamento**, não classificação.

### 6.4 (FGV/2024/DATAPREV – ATI)

**Item:** "K-Means, em sua versão original, é classificado como um tipo de algoritmo:"

**Gabarito: d) partitivo.**

### 6.5 (CESPE/CEBRASPE/2024/CTI – Tecnologista)

**Item:** "No algoritmo K-means, a similaridade intragrupo é avaliada considerando-se o valor médio dos objetos em um grupo, que pode ser visto como o seu centro de gravidade ou o centroide."

**Gabarito: Certo (C).**

### 6.6 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador)

**Item:** "O algoritmo de agrupamento K-means – baseado em centroides, que divide um conjunto de dados em grupos semelhantes com base na distância entre seus centroides – pode ser utilizado para identificar comunidades de usuários com interesses comuns."

**Gabarito: Certo (C).**

### 6.7 (FGV/2025/TCE-RR – Auditor)

**Afirmativas:**
- K-means também conhecido como K-NN? **(F)** – são algoritmos diferentes.
- Coeficiente de Gini do nó sempre maior que o do pai? **(F)** – em árvores de decisão, o Gini dos filhos é menor (mais puro).
- SVM utilizado apenas para classificação, não com dados não linearmente separáveis? **(F)** – SVM pode ser usado para regressão e com kernel trick para dados não linearmente separáveis.

**Gabarito: e) F – F – F.**

### 6.8 (FGV/2025/CNU – Cultura e Educação)

**Item:** "Identificar grupos latentes de usuários com padrões semelhantes de comportamento" (dados não rotulados).

**Gabarito: c) iniciar com clusterização por k-médias, caracterizar os grupos com análise descritiva e, então, empregar regressão preditiva.**

### 6.9 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador)

**Item:** "O algoritmo de classificação K-Means é baseado em um método de agrupamento hierárquico."

**Gabarito: Errado (E).**

**Comentário:** K-means é um algoritmo **particional**, não hierárquico.

### 6.10 (CESPE/CEBRASPE/2025/PF – Perito)

**Item:** "O algoritmo k-means é um método de clusterização do tipo particional que requer a definição prévia do número de clusters e utiliza a média dos elementos como critério para a atualização dos centroides."

**Gabarito: Certo (C).**

### 6.11 (FCC/2025/PREF. SÃO PAULO – Analista)

**Item:** "Prever demanda (regressão) e identificar agrupamentos de regiões."

**Gabarito: b) aplicar Regressão Linear para prever a demanda e utilizar o algoritmo não supervisionado K-Means para identificar agrupamentos.**

### 6.12 (CESPE/CEBRASPE/2023/SEFIN FORTALEZA – Analista)

**Item:** "K-means é um algoritmo de aprendizado não supervisionado, em que se calcula a distância entre os objetos e cada centroide, atribuindo cada objeto ao centroide mais próximo."

**Gabarito: Certo (C).**

### 6.13 (CESPE/CEBRASPE/2023/DATAPREV – Analista)

**Item:** "O algoritmo k-means seleciona objetos reais de uma base de dados como centroide do grupo."

**Gabarito: Errado (E).**

**Comentário:** Os centroides são calculados como a **média** dos pontos – não são objetos reais selecionados da base.

### 6.14 (CESPE/CEBRASPE/2025/ANM – Especialista)

**Item:** "O algoritmo K-means garante a otimização dos clusters, independentemente da inicialização dos centroides."

**Gabarito: Errado (E).**

**Comentário:** A qualidade dos clusters **depende** da inicialização dos centroides.

### 6.15 (FGV/2025/SEFAZ-PR – Auditor)

**Item:** "Agrupar beneficiários conforme seus perfis."

**Gabarito: d) K-means.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/TCE-PE/2025) | b |
| 02 (FGV/MACAÉ/2024) | b |
| 03 (CESPE/EMBRAPA/2025) | E |
| 04 (FGV/DATAPREV/2024) | d |
| 05 (CESPE/CTI/2024) | C |
| 06 (CESPE/EMBRAPA/2025) | C |
| 07 (FGV/TCE-RR/2025) | e |
| 08 (FGV/CNU/2025) | c |
| 09 (CESPE/EMBRAPA/2025) | E |
| 10 (CESPE/PF/2025) | C |
| 11 (FCC/SP/2025) | b |
| 12 (CESPE/SEFIN/2023) | C |
| 13 (CESPE/DATAPREV/2023) | E |
| 14 (CESPE/ANM/2025) | E |
| 15 (FGV/SEFAZ-PR/2025) | d |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **K-Means** | Algoritmo não supervisionado para agrupamento. |
| **K** | Número de clusters (definido pelo usuário). |
| **Centroide** | Média dos pontos de um cluster. |
| **Distância** | Geralmente Euclidiana. |
| **Tipo** | Particional (não hierárquico). |
| **K-Means ≠ K-NN** | K-Means: não supervisionado (agrupamento). K-NN: supervisionado (classificação/regressão). |

---

*Material complementar à aula "K-Means" (professor Vitor Kessler/Gran Concursos).*