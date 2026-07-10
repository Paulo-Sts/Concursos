# Anotações – Tipos de Aprendizado II (Supervisionado, Não Supervisionado, Por Reforço)

## 1. Aprendizado Supervisionado

- O modelo é treinado com **dados rotulados** (pares entrada-saída).
- Aprende a identificar padrões e **realizar previsões** para novos dados.
- **Objetivo:** aprender uma função `Y = f(X)` que mapeia entradas em saídas.

### 1.1 Exemplo prático

| ENTRADA (X) | SAÍDA (Y) |
| --- | --- |
| Imagem | "Pato" ou "Não pato" |
| Dados do cliente | "Cancela" ou "Não cancela" |

> ### 1.1.1 Tarefas supervisionadas
> - **Classificação:** prever categorias (ex.: fraude ou normal).
> - **Regressão:** prever valores numéricos (ex.: preço de venda).

## 2. Aprendizado Não Supervisionado

- O modelo é treinado com **dados não rotulados**.
- O algoritmo **descobre padrões, estruturas ou relacionamentos ocultos** por conta própria.
- **Objetivo:** análise descritiva (entender a estrutura dos dados).

### 2.1 Exemplo prático

- Conjunto de imagens **não classificadas**.
- O algoritmo agrupa imagens semelhantes (ex.: patos juntos, coelhos juntos, ouriços juntos).

### 2.2 Tarefas não supervisionadas

| TAREFA | DESCRIÇÃO |
| --- | --- |
| **Clusterização (Agrupamento)** | Agrupar elementos semelhantes. |
| **Regras de Associação** | Descobrir relações frequentes entre itens. |
| **Redução de Dimensionalidade** | Reduzir o número de atributos. |

## 3. Aprendizado por Reforço (Reinforcement Learning)

- **Agente inteligente** interage com um **ambiente**.
- A cada ação, recebe uma **recompensa** ou **penalidade**.
- **Objetivo:** maximizar a **recompensa cumulativa** ao longo do tempo.

### 3.1 Exemplo prático

- Robô na superfície da Lua:
  - Move-se para frente, trás, esquerda, direita.
  - Colide com parede → penalidade.
  - Anda por caminho seguro → recompensa.
  - Aprende progressivamente a maximizar recompensas.

### 3.2 Exploration vs. Exploitation

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Exploration** | Agente tenta ações novas (desconhecidas) para descobrir recompensas maiores. |
| **Exploitation** | Agente repete ações que já sabe que geram recompensa (zona de conforto). |

> ### 3.2.1 Equilíbrio
> - Se o agente só fizer **exploitation**, pode ficar preso em um ciclo limitado.
> - Políticas típicas: 95% exploitation, 5% exploration.

## 4. Quadro Comparativo

| CRITÉRIO | SUPERVISIONADO | NÃO SUPERVISIONADO | POR REFORÇO |
| --- | --- | --- | --- |
| **Rótulos** | Sim | Não | Não (apenas recompensas/penalidades) |
| **Feedback** | Saída desejada (Y) | Padrões ocultos | Recompensa ou penalidade |
| **Interação** | Estática (dados fixos) | Estática | Dinâmica (agente-ambiente) |
| **Objetivo** | Prever (classificar/regredir) | Descrever (agrupar/associar) | Maximizar recompensa cumulativa |
| **Exemplo** | Detecção de fraude | Segmentação de clientes | Robô que aprende a andar |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/2025/PF – Agente)

**Item:** "Em machine learning supervisionado, o algoritmo aprende, a partir de um conjunto de dados rotulados, a identificar padrões e realizar previsões em novos dados."

**Gabarito: Certo (C).**

### 5.2 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador)

**Item:** "O aprendizado não supervisionado se caracteriza pela utilização de dados previamente rotulados para treinar um modelo de machine learning."

**Gabarito: Errado (E).**

**Comentário:** Não supervisionado usa dados **não rotulados** – a presença de rótulos é característica do aprendizado supervisionado.

### 5.3 (CESPE/CEBRASPE/2025/BDMG – Analista)

**Item:** "Nos algoritmos supervisionados de ML, o modelo é treinado apenas com dados de entrada, e as saídas são geradas automaticamente pelo algoritmo."

**Gabarito: Errado (E).**

**Comentário:** Supervisionado exige **pares entrada-saída** (rótulos). A descrição se aproxima do **aprendizado auto-supervisionado** (ex.: Transformers, ChatGPT).

### 5.4 (FGV/2025/TCE-PE – Analista)

**Item:** "Característica fundamental do aprendizado supervisionado:"

**Gabarito: b) Em aprendizado supervisionado, o modelo é treinado com dados de entrada e suas respectivas saídas esperadas, permitindo que ele aprenda a prever rótulos para novos dados.**

### 5.5 (FGV/2025/PGM-RJ – Analista)

**Item:** "Modelos que precisam inferir suas próprias regras e fazem previsões com base em dados que não contêm respostas corretas, e cujo objetivo é identificar padrões significativos nos dados, são conhecidos como:"

**Gabarito: b) Aprendizado não supervisionado.**

### 5.6 (CESPE/CEBRASPE/2025/EMBRAPA – Analista)

**Item:** "O aprendizado de máquina não supervisionado utiliza algoritmos para analisar conjuntos de dados não rotulados, a fim de descobrir padrões ocultos sem necessidade de intervenção humana."

**Gabarito: Certo (C).**

### 5.7 (CESPE/CEBRASPE/2025/SUSEP – Analista)

**Item:** "O modelo de aprendizado supervisionado ajusta uma função de mapeamento a partir de exemplos rotulados para generalizar dados ainda não vistos."

**Gabarito: Certo (C).**

### 5.8 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador – Reforço)

**Item:** "Diferentemente do aprendizado supervisionado e não supervisionado, o aprendizado por reforço baseia-se em um agente que interage com um ambiente e recebe recompensas ou penalidades conforme suas ações."

**Gabarito: Certo (C).**

### 5.9 (FGV/2024/SEDUC-SP – Professor)

**Afirmativas sobre os três tipos:**

- I – Supervisionado usa dados rotulados. **(V)**
- II – Não supervisionado usa dados sem rótulos e identifica padrões. **(V)**
- III – Reforço envolve agente com recompensas/punições. **(V)**

**Gabarito: b) As afirmativas I, II e III estão corretas.**

### 5.10 (FGV/2024/CGM-BH – Auditor)

**Itens:**
- ( ) Supervisionado = dataset rotulado. **(V)**
- ( ) Não supervisionado = dataset não rotulado, estrutura descoberta pelo algoritmo. **(V)**
- ( ) Reforço = prever variável dependente a partir de independentes. **(F)** – isso é regressão (supervisionado).

**Gabarito: d) V – V – F.**

### 5.11 (CESPE/CEBRASPE/2023/DATAPREV – Analista)

**Item:** "O aprendizado por reforço é um tipo de aprendizagem de máquina que tem por objetivo prever o resultado de um atributo alvo exclusivamente por meio de reforço no treinamento do modelo."

**Gabarito: Errado (E).**

**Comentário:** Previsão de atributo-alvo é característica do **supervisionado**. Reforço envolve agente, ambiente e recompensas/penalidades.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/PF/2025) | C |
| 02 (CESPE/EMBRAPA/2025) | E |
| 03 (CESPE/BDMG/2025) | E |
| 04 (FGV/TCE-PE/2025) | b |
| 05 (CESPE/EMBRAPA/2025) | C |
| 06 (FGV/PGM-RJ/2025) | b |
| 07 (CESPE/SUSEP/2025) | C |
| 08 (CESPE/EMBRAPA/2025) | C |
| 09 (FGV/SEDUC-SP/2024) | b |
| 10 (FGV/CGM-BH/2024) | d |
| 11 (CESPE/DATAPREV/2023) | E |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Supervisionado** | Aprende com dados rotulados (X → Y). |
| **Não supervisionado** | Aprende com dados sem rótulos, descobre padrões. |
| **Por reforço** | Agente interage com ambiente, recebe recompensas/penalidades. |
| **Exploration** | Tentar ações novas para descobrir melhores recompensas. |
| **Exploitation** | Repetir ações que já deram recompensa. |

---

*Material complementar à aula "Tipos de Aprendizado II" (professor Vitor Kessler/Gran Concursos).*