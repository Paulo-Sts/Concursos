# Anotações – Redução de Dimensionalidade e PCA

## 1. Conceito de Redução de Dimensionalidade

- **Redução de dimensionalidade:** processo de **diminuir o número de colunas (atributos)** de um dataset.
- **Objetivos:**
  - Reduzir o custo computacional (treinamento mais rápido).
  - Eliminar atributos irrelevantes ou redundantes.
  - Evitar a **maldição da dimensionalidade** (overfitting e degradação do desempenho).
  - Facilitar a visualização dos dados (ex.: redução para 2D/3D).

> ### 1.1 Maldição da Dimensionalidade
> - À medida que o número de colunas aumenta, o desempenho do modelo melhora até um certo ponto.
> - Após esse ponto, o excesso de dimensões **degrada** o desempenho do modelo.
> - A redução de dimensionalidade visa encontrar o **ponto ideal** de colunas.

## 2. Tipos de Redução de Dimensionalidade

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Seleção de atributos** | Escolhe um subconjunto dos atributos originais, descartando os menos relevantes. | *Wrapper* (avalia adicionando/removendo colunas e medindo impacto na acurácia), *Filter*, *Embedded*. |
| **Extração de atributos** | Cria **novos atributos** a partir da combinação dos originais. | **PCA (Análise de Componentes Principais)**, ICA (Análise de Componentes Independentes). |

> ### 2.1 Seleção de atributos (Wrapper)
> - Parte-se de um modelo com algumas colunas.
> - Adiciona-se uma nova coluna – se a acurácia **melhora**, mantém-se; se **piora**, descarta-se.
> - Processo iterativo até não haver mais ganho.

## 3. PCA – Análise de Componentes Principais

### 3.1 Conceito

- **PCA (Principal Component Analysis)** é a técnica de redução de dimensionalidade **mais cobrada**.
- É uma técnica de **extração de atributos** (não seleção).
- Transforma **variáveis correlacionadas** em **componentes principais não correlacionados**.
- Os componentes principais são ordenados pela **quantidade de variância** que explicam dos dados originais.

### 3.2 Características do PCA

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Tipo** | Aprendizado **não supervisionado** (não usa rótulos). |
| **Entrada** | Dados numéricos (requer normalização se as variáveis estiverem em escalas diferentes). |
| **Saída** | Componentes principais (combinações lineares das variáveis originais). |
| **Primeiro componente** | Representa a **direção de máxima variância** dos dados. |
| **Objetivo** | Preservar o máximo de variância possível com o menor número de componentes. |

> ### 3.2.1 Normalização antes do PCA
> - As variáveis **devem estar na mesma escala** para que o PCA não seja distorcido.
> - Se uma variável tem variância muito maior que as outras, ela dominará os componentes principais.

### 3.3 Seleção de Componentes

- Os componentes são escolhidos com base na **variância explicada**.
- Exemplo: se 5 componentes explicam 95% da variância dos dados originais, pode-se reduzir de 50 colunas para 5.

## 4. Redução de Dimensionalidade no Ciclo de Vida da Ciência de Dados

- A redução de dimensionalidade é executada na fase de **limpeza e preparação dos dados** (pré-processamento).

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/TC-DF/2023 – Auditor)

**Item:** "Uma das consequências da utilização da técnica de redução da dimensionalidade é a complexidade da análise."

**Gabarito: Errado (E).**

**Comentário:** Redução de dimensionalidade **diminui** a complexidade da análise.

### 5.2 (FGV/CÂMARA DOS DEPUTADOS/2023 – Analista)

**Item:** "Random Forest é um algoritmo de aprendizado profundo, amplamente utilizado em reconhecimento de fala."

**Gabarito: d)** (afirmativa incorreta).

**Comentário:** Random Forest é um **ensemble de árvores de decisão** – não é deep learning.

### 5.3 (FGV/PREFEITURA DE VITÓRIA/2024 – Analista)

**Item:** "Na redução de dimensionalidade em PLN, a técnica utilizada é chamada:"

**Gabarito: c) PCA (Principal Component Analysis).**

### 5.4 (CESPE/INPI/2024 – Pesquisador)

**Item:** "PCA é uma técnica empregada para reduzir a dimensionalidade do conjunto de dados, reduzindo o número de valores usados para representar cada observação, mas sem reduzir o número de observações."

**Gabarito: Certo (C).**

### 5.5 (CESPE/EMBRAPA/2025 – Analista)

**Item:** "A análise de componentes independentes é uma técnica que pode ser usada na redução de dimensionalidade e busca separar sinais ou fontes que sejam estatisticamente independentes."

**Gabarito: Certo (C).**

### 5.6 (CESPE/ANA/2024 – Especialista)

**Item:** "A redução de dimensionalidade acrescenta variáveis nos modelos de inteligência artificial para torná-los mais específicos e objetivos."

**Gabarito: Errado (E).**

**Comentário:** Redução de dimensionalidade **retira** variáveis (reduz o número de colunas).

### 5.7 (CESPE/INSA/2025 – Tecnologista)

**Item:** "A PCA pode ser usada para prever novas observações a partir de componentes principais."

**Gabarito: Errado (E).**

**Comentário:** PCA é usada para **redução de dimensionalidade**, não para previsão (isso é tarefa de modelos supervisionados).

### 5.8 (CESPE/INSA/2025 – Tecnologista)

**Item:** "A PCA transforma variáveis correlacionadas em componentes principais não correlacionados, preservando a máxima variabilidade dos dados."

**Gabarito: Certo (C).**

### 5.9 (CESPE/DATAPREV/2023 – Analista)

**Item:** "A compressão de atributos é uma técnica de redução de dimensionalidade nos quais atributos irrelevantes ou redundantes são identificados e desconsiderados."

**Gabarito: Errado (E).**

**Comentário:** Compressão/extracão de atributos (ex.: PCA) **transforma** os atributos em novos, não apenas desconsidera.

### 5.10 (CESPE/MPE-CE/2025 – Analista)

**Item:** "PCA é uma técnica usada para enfatizar a variação e trazer os padrões fortes em um conjunto de dados, e pode ser utilizada para facilitar a exploração e visualização dos dados."

**Gabarito: Certo (C).**

### 5.11 (CESPE/ANATEL/2024 – Especialista)

**Item:** "Para utilizar de forma adequada a PCA, é essencial normalizar os dados; se as variáveis não estiverem na mesma escala, aquelas com maior variância terão maior impacto."

**Gabarito: Certo (C).**

### 5.12 (CESPE/EMBRAPA/2025 – Analista)

**Item:** "PCA transforma um conjunto de variáveis correlacionadas em um conjunto menor de variáveis não correlacionadas (componentes principais) que retêm a maior parte da variância dos dados originais."

**Gabarito: Certo (C).**

### 5.13 (FGV/CVM/2024 – Inspetor)

**Item:** "No ciclo de vida da ciência de dados, a tarefa de redução de dimensionalidade dos dados é executada na fase:"

**Gabarito: d) limpeza e preparação dos dados.**

### 5.14 (CESPE/ANTT/2024 – Especialista)

**Item:** "Redução de dimensionalidade é usada para reduzir o número de entradas de dados a um tamanho gerenciável, não havendo, nesse caso, preservação da integridade do conjunto de dados."

**Gabarito: Errado (E).**

**Comentário:** PCA **preserva** a maior parte da variância (integridade dos dados) ao reduzir dimensionalidade.

### 5.15 (FGV/TCE-PI/2025 – Auditor)

**Afirmativas:**
- Agregação forma novos atributos combinando grupos dos originais. **(V)**
- Seleção de atributos descarta parte dos atributos originais. **(V)**
- Seleção de atributos embutidas são aplicadas no pré-processamento. **(F)** – são aplicadas durante o treinamento.

**Gabarito: d) V – V – F.**

### 5.16 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "A PCA transforma variáveis correlacionadas em componentes principais ortogonais; a seleção dos componentes é realizada com base na variância explicada por cada componente."

**Gabarito: Certo (C).**

### 5.17 (FGV/RECEITA FEDERAL/2023 – Analista)

**Item:** "Objetivo principal da PCA."

**Gabarito: b) Redução da dimensionalidade dos dados.**

### 5.18 (CESGRANRIO/IPEA/2024 – Técnico)

**Item:** "A primeira componente principal de um conjunto de dados representa a:"

**Gabarito: d) variância máxima dos dados.**

### 5.19 (CESPE/SUSEP/2025 – Analista)

**Item:** "A aplicação de PCA em contexto não supervisionado independe de rótulos para extrair componentes de maior variância."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/TC-DF/2023) | E |
| 02 (FGV/CÂMARA/2023) | d |
| 03 (FGV/VITÓRIA/2024) | c |
| 04 (CESPE/INPI/2024) | C |
| 05 (CESPE/EMBRAPA/2025) | C |
| 06 (CESPE/ANA/2024) | E |
| 07 (CESPE/INSA/2025) | E |
| 08 (CESPE/INSA/2025) | C |
| 09 (CESPE/DATAPREV/2023) | E |
| 10 (CESPE/MPE-CE/2025) | C |
| 11 (CESPE/ANATEL/2024) | C |
| 12 (CESPE/EMBRAPA/2025) | C |
| 13 (FGV/CVM/2024) | d |
| 14 (CESPE/ANTT/2024) | E |
| 15 (FGV/TCE-PI/2025) | d |
| 16 (CESPE/EMBRAPA/2025) | C |
| 17 (FGV/RECEITA/2023) | b |
| 18 (CESGRANRIO/IPEA/2024) | d |
| 19 (CESPE/SUSEP/2025) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Redução de Dimensionalidade** | Diminui o número de colunas do dataset. |
| **Seleção de atributos** | Escolhe um subconjunto das colunas originais. |
| **Extração de atributos** | Cria novas colunas a partir das originais (PCA). |
| **PCA** | Técnica de extração não supervisionada; cria componentes principais ortogonais. |
| **Primeiro componente** | Direção de máxima variância. |
| **Normalização** | Necessária antes do PCA se as variáveis estiverem em escalas diferentes. |
| **Maldição da dimensionalidade** | Degradação do modelo com excesso de colunas. |
| **Fase de execução** | Limpeza e preparação dos dados (pré-processamento). |

---

*Material complementar à aula "Redução de Dimensionalidade e PCA" (professor Vitor Kessler/Gran Concursos).*