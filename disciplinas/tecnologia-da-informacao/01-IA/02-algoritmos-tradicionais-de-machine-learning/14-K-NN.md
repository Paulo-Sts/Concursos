# Anotações – K-NN (K-Vizinhos Mais Próximos)

## 1. Conceito de K-NN

- **K-NN (K-Nearest Neighbors)** é um algoritmo de aprendizado de máquina **supervisionado**, **não paramétrico**.
- Pode ser usado para **classificação** e **regressão**.
- Baseia-se no princípio de que pontos próximos no espaço de características tendem a pertencer à mesma classe.

### 1.1 Funcionamento

1. **Treinamento:** todos os dados de treinamento são armazenados (não há modelo explícito – é um algoritmo *lazy*).
2. **Predição (classificação):** para um novo ponto, calcula-se a distância para todos os pontos de treinamento.
3. Selecionam-se os **K vizinhos mais próximos**.
4. A classe do novo ponto é a **classe majoritária** entre os K vizinhos.
5. Para **regressão:** a predição é a **média** dos valores dos K vizinhos.

> ### 1.2 Distância Euclidiana
> - A métrica de distância mais comum é a **distância Euclidiana**.
> - Fórmula: `d(p, q) = √[(p₁-q₁)² + (p₂-q₂)² + ... + (pn-qn)²]`
> - O K-NN pode ser usado com outras métricas de distância, mas a Euclidiana é a mais cobrada.

## 2. Hiperparâmetro K

- **K** é o número de vizinhos considerados.
- **Escolha:** geralmente utiliza-se **valores ímpares** para evitar empates em classificação binária.
- **Impacto:**
  - **K pequeno:** modelo sensível a ruídos (pode levar a overfitting).
  - **K grande:** modelo mais suave, mas pode perder detalhes locais (pode levar a underfitting).
- **K não é aleatório** – deve ser escolhido pelo cientista de dados com base na validação cruzada.

## 3. Pré-processamento dos Dados

- O K-NN é **sensível à escala das variáveis**.
- **Necessidade de normalização ou padronização** para que todas as dimensões tenham o mesmo peso.
- Exemplo: se uma variável varia de 0 a 100 e outra de 0 a 1, a distância será dominada pela primeira.
- **Dados categóricos** devem ser convertidos para numéricos (ex.: *one-hot encoding*).

## 4. Vantagens e Desvantagens

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| Simples de entender e implementar. | Custo computacional alto na predição (calcula distâncias para todos os pontos). |
| Não faz suposições sobre a distribuição dos dados (não paramétrico). | Sensível à escala dos dados – requer normalização. |
| Funciona bem com dados com limites de decisão complexos. | Pode sofrer com a *maldição da dimensionalidade* (espaço esparso em alta dimensão). |
| Pode ser usado para classificação e regressão. | Requer armazenamento de todos os dados de treinamento (*lazy learner*). |

## 5. K-NN vs. K-Means (não confundir!)

| K-NN (K-Vizinhos Mais Próximos) | K-Means (K-Médias) |
| --- | --- |
| Supervisionado | Não supervisionado |
| Classificação / Regressão | Agrupamento (clustering) |
| Usa distância para classificar | Usa distância para formar grupos |
| K = número de vizinhos | K = número de clusters |

> ### 5.1 Atenção (pegadinha)
> - **K-NN** e **K-Means** são algoritmos diferentes! K-NN é supervisionado; K-Means é não supervisionado.

## 6. Questões de Concurso Comentadas

### 6.1 (FGV/2024/TJ-RR – Analista)

**Item:** "Técnica que classifica novas instâncias por associação à classe da maioria das instâncias mais próximas, baseada em métricas de distância."

**Gabarito: c) K-NN.**

### 6.2 (FGV/2024/PREFEITURA DE CUIABÁ – Auditor)

**Afirmativas:**
- I – K-NN classifica com base nas distâncias. **(V)**
- II – K deve ser escolhido aleatoriamente e não tem impacto. **(F)**
- III – K-NN é sensível à escala e requer normalização. **(V)**

**Gabarito: d) I e III, apenas.**

### 6.3 (CESPE/CEBRASPE/2024/ANATEL – Especialista)

**Item:** "KNN é um algoritmo de aprendizado supervisionado não paramétrico que não pode ser utilizado em problemas de classificação."

**Gabarito: Errado (E).**

**Comentário:** K-NN **pode** ser usado para classificação – e é frequentemente usado para isso.

### 6.4 (FGV/2024/DATAPREV – ATI)

**Item:** Classificar o ponto x=(5,5) com K-NN (distância Euclidiana). Dados: (1,1)-A, (4,5)-B, (7,1)-C, (9,9)-D.

**Resolução:**
- Distância para (4,5) é a menor (ponto mais próximo).
- Para K=1 → classe B.

**Gabarito: b) a classe B para k=1, pois a distância para o ponto (4.0, 5.0) é a menor de todas.**

### 6.5 (CESPE/CEBRASPE/2024/CTI – Tecnologista)

**Item:** "O algoritmo de classificação KNN é utilizado na inteligência artificial para reconhecimento de padrões."

**Gabarito: Certo (C).**

### 6.6 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** Com K=3, classificar os pontos (3,2), (3,3) e (4,4).

**Resolução (visual):**
- (3,2) – 3 vizinhos mais próximos são S → **S**
- (3,3) – 2 vizinhos R, 1 S → **R**
- (4,4) – 3 vizinhos R → **R**

**Gabarito: c) [S, R, R].**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/TJ-RR/2024) | c |
| 02 (FGV/CUIABÁ/2024) | d |
| 03 (CESPE/ANATEL/2024) | E |
| 04 (FGV/DATAPREV/2024) | b |
| 05 (CESPE/CTI/2024) | C |
| 06 (CESGRANRIO/IPEA/2024) | c |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **K-NN** | Algoritmo supervisionado baseado em proximidade. |
| **Classificação** | Classe majoritária entre os K vizinhos. |
| **Regressão** | Média dos valores dos K vizinhos. |
| **K** | Número de vizinhos – deve ser escolhido (não aleatório). |
| **Distância Euclidiana** | Métrica mais comum para medir proximidade. |
| **Normalização** | Necessária devido à sensibilidade à escala. |
| **Não paramétrico** | Não assume distribuição prévia dos dados. |
| **Lazy learner** | Não constrói modelo explícito durante o treinamento. |

---

*Material complementar à aula "K-NN" (professor Vitor Kessler/Gran Concursos).*