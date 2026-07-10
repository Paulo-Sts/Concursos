# Anotações – SVM (Support Vector Machines)

## 1. Conceito de SVM

- **SVM (Support Vector Machine – Máquina de Vetores de Suporte)** é um algoritmo de aprendizado de máquina **supervisionado**.
- Pode ser usado para **classificação** e **regressão** (embora seja mais conhecido por classificação).
- **Principal característica:** encontrar um **hiperplano ótimo** que separa as classes com a **maior margem** possível.

> ### 1.1 Hiperplano Ótimo
> - O hiperplano é a **linha (em 2D)**, o **plano (em 3D)** ou a **superfície (em n dimensões)** que separa as classes.
> - **Otimização:** maximizar a distância entre o hiperplano e os pontos mais próximos de cada classe (os **vetores de suporte**).
> - A distância entre o hiperplano e os vetores de suporte de ambos os lados deve ser **igual**.

## 2. Vetores de Suporte (Support Vectors)

- **Vetores de suporte** são os pontos de cada classe que estão **mais próximos do hiperplano**.
- Eles são usados para definir a posição do hiperplano ótimo.
- Apenas esses pontos influenciam o hiperplano – os demais podem ser ignorados.

> ### 2.1 Margem
> - **Margem:** distância entre o hiperplano e os vetores de suporte.
> - O hiperplano ótimo é aquele que **maximiza a margem**.

## 3. Kernel Trick

- **Problema original do SVM:** assume dados **linearmente separáveis**.
- **Kernel Trick:** técnica que adiciona **dimensões extras** ao espaço original, tornando os dados **linearmente separáveis** em um espaço de maior dimensão.
- O mapeamento é **implícito** (não é necessário calcular explicitamente as novas coordenadas).
- **Principais kernels:**
  - Linear.
  - Polinomial.
  - RBF (Radial Basis Function) / Gaussiano.

> ### 3.1 Exemplo
> - Dados não linearmente separáveis em 2D.
> - Aplicação do kernel adiciona uma terceira dimensão (ex.: z = x² + y²).
> - Os dados se tornam linearmente separáveis no espaço 3D.

## 4. Soft Margin (Margem Suave)

- Introduzida em 1995 para permitir **erros de classificação** no treinamento.
- Útil para evitar **overfitting** quando os dados não são perfeitamente separáveis.
- **Custo:** permite que alguns pontos fiquem do lado errado do hiperplano, em troca de uma margem maior e melhor generalização.

## 5. SVM – Resumo das Características

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Tipo** | Supervisionado |
| **Problemas** | Classificação e regressão |
| **Hiperplano** | Divide as classes com margem máxima |
| **Vetores de suporte** | Pontos mais próximos do hiperplano, usados para defini-lo |
| **Kernel Trick** | Adiciona dimensões para lidar com dados não linearmente separáveis |
| **Soft Margin** | Permite erros de classificação para evitar overfitting |
| **Não probabilístico** | SVM é um classificador determinístico (não calcula probabilidades) |

> ### 5.1 SVM vs. Regressão Logística
> - **SVM:** hiperplano com margem máxima; não probabilístico.
> - **Regressão Logística:** função sigmoide; calcula probabilidades.

## 6. Questões de Concurso Comentadas

### 6.1 (FGV/2024/DATAPREV – ATI)

**Item:** "SVM utiliza um mapeamento não linear para transformar os dados de treino originais em um espaço de dimensão superior."

**Gabarito: e)** (corresponde ao kernel trick).

### 6.2 (FGV/2023/TJ-RN – Analista)

**Item:** "Algoritmo que divide os dados por uma reta, com distância máxima e igual para ambas as classes."

**Gabarito: e) Máquina de Vetores de Suporte.**

### 6.3 (CESPE/CEBRASPE/2023/DATAPREV – Analista)

**Item:** "Os algoritmos SVM realizam apenas tarefas de regressão."

**Gabarito: Errado (E).**

**Comentário:** SVM também realiza **classificação** – e é mais conhecido por isso.

### 6.4 (CESPE/CEBRASPE/2024/ANATEL – Especialista)

**Item:** "SVM é um algoritmo de aprendizado de máquina supervisionado que pode ser usado para desafios de classificação ou regressão."

**Gabarito: Certo (C).**

### 6.5 (FGV/2024/TCE-PA – Auditor)

**Afirmativas:**
- I – Regressão logística determina hiperplano. **(F)** – isso é SVM.
- II – SVM é probabilístico. **(F)** – SVM é não probabilístico.
- III – KNN classifica pelos vizinhos mais próximos. **(V)**

**Gabarito: c) III, apenas.**

### 6.6 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** "Algoritmo adequado para dados não linearmente separáveis usando kernel."

**Gabarito: d) Máquina de Vetores de Suporte.**

### 6.7 (FGV/2025/MPE-RJ – Analista)

**Itens sobre algoritmos:**
- I – Regressão logística: classificação binária. **(V)**
- II – SVM trabalha apenas com dados linearmente separáveis. **(F)** – kernel trick.
- III – Árvore de decisão é não supervisionada. **(F)** – é supervisionada.

**Gabarito: e) I, apenas.**

### 6.8 (CESPE/CEBRASPE/2024/ANATEL – Figura com hiperplanos)

**Item:** "Uma margem mais ampla geralmente indica um melhor desempenho na classificação."

**Gabarito: a)** – quanto maior a margem, melhor a separação.

### 6.9 (CESPE/CEBRASPE/2024/MPE-CE – Analista)

**Item:** "SVM é um classificador não probabilístico que utiliza um hiperplano com margem máxima para separar dados em diferentes categorias, combina modelos lineares com técnicas de aprendizagem baseadas em instâncias e pode executar classificações lineares ou realizar classificações não lineares."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/DATAPREV/2024) | e |
| 02 (FGV/TJ-RN/2023) | e |
| 03 (CESPE/DATAPREV/2023) | E |
| 04 (CESPE/ANATEL/2024) | C |
| 05 (FGV/TCE-PA/2024) | c |
| 06 (CESGRANRIO/IPEA/2024) | d |
| 07 (FGV/MPE-RJ/2025) | e |
| 08 (CESPE/ANATEL/2024) | a |
| 09 (CESPE/MPE-CE/2024) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **SVM** | Algoritmo supervisionado para classificação/regressão. |
| **Hiperplano ótimo** | Separa as classes com margem máxima. |
| **Vetores de suporte** | Pontos mais próximos do hiperplano. |
| **Kernel Trick** | Adiciona dimensões para tornar dados não lineares separáveis. |
| **Soft Margin** | Permite erros para evitar overfitting. |
| **SVM é** | Não probabilístico, baseado em instâncias. |
| **SVM vs. Regressão Logística** | SVM: margem máxima; RL: probabilidades. |

---

*Material complementar à aula "SVM" (professor Vitor Kessler/Gran Concursos).*