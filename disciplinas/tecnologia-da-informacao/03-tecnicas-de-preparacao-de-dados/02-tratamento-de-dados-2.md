# Anotações

# TRATAMENTO DE DADOS – DISCRETIZAÇÃO

## 1. Conceito de Discretização

- **Definição:** Discretização é o processo de transformar dados em **escala contínua** (numéricos) em **escala discreta** (categóricos ou em intervalos).
- **Objetivo:** Limitar o número de estados distintos de um atributo e simplificar a análise. É uma forma de classificação onde os intervalos discretos podem receber "nomes" ou rótulos.
- **Contexto:** É uma importante tarefa de **pré-processamento** ou **preparação de dados** para mineração de dados e aprendizado de máquina.

## 2. Principais Técnicas de Discretização

| TÉCNICA | DESCRIÇÃO | CARACTERÍSTICAS |
| :--- | :--- | :--- |
| **Discretização de Largura Igual** (*Equal-Width*) | Divide o intervalo de valores da variável em *k* intervalos de **tamanho idêntico**. | Simples, mas não garante que cada intervalo tenha o mesmo número de observações. |
| **Discretização de Frequência Igual** (*Equal-Frequency* / Quantis) | Divide os dados em *k* intervalos de forma que cada um contenha **aproximadamente o mesmo número de observações**. | Útil para criar intervalos balanceados. |
| **Discretização Binária** (*Binary*) | Transforma uma variável contínua em uma variável categórica com **duas categorias**. | Comum em problemas de classificação binária; usa-se um ponto de corte (limiar). |
| **Discretização por Entropia** | Utiliza a **entropia** para dividir a variável em intervalos que maximizam a **homogeneidade** das classes. | Frequentemente usada em algoritmos de **árvore de decisão**. |
| **Discretização por Clustering** | Utiliza algoritmos como o **K-Means** para agrupar dados. Os *clusters* formam os intervalos discretos. | Não garante que os intervalos tenham o mesmo número de observações. |
| **Discretização por Intervalos de Probabilidade** | Baseia-se na **distribuição de probabilidade** dos dados para criar intervalos. Cria intervalos com base em percentis. | Semelhante à discretização de frequência igual. |

## 3. Análise de Questões de Concurso

### 3.1 Definição Geral (FGV/TJ-SE/2023)

- **Enunciado:** Operação de pré-processamento que transforma dados quantitativos (contínuos) em dados qualitativos, obtendo uma partição não sobreposta de um domínio contínuo.
- **Gabarito:** **D) Discretização.**
- **Análise:** É a definição canônica de discretização. Transforma o numérico (ex: 38.5) em categórico (ex: "38-40").

### 3.2 Número Igual de Observações (CESGRANRIO/IPEA/2024)

- **Enunciado:** Técnica para discretizar uma variável em 10 intervalos com aproximadamente o mesmo número de observações.
- **Gabarito:** **E) de Frequência Igual.**
- **Análise:** O objetivo de ter o "mesmo número de observações" por intervalo é a característica definidora da discretização por Frequência Igual (ou quantis).

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (QUADRIX/CREA-GO) | **C** | Definição correta de discretização. |
| **02** (FGV/TJ-SE) | **D** | Transformar contínuo em qualitativo (categórico) = Discretização. |
| **03** (FGV/TCE-SP) | **D** | Transformar valores de temperatura em intervalos = Discretização. |
| **04** (CESGRANRIO/IPEA) | **E** | Mesmo número de observações = Frequência Igual. |
| **05** (CESPE/MPO) | **C** | Afirmação correta sobre discretização de frequência igual. |