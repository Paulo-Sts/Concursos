# Anotações – Naive Bayes

## 1. Conceito de Naive Bayes

- **Naive Bayes** é um algoritmo de aprendizado de máquina **supervisionado** baseado no **Teorema de Bayes**.
- É um **classificador probabilístico** que calcula a probabilidade de uma instância pertencer a uma classe.
- **Trabalha exclusivamente com classificação** – não realiza regressão (previsão de números).

> ### 1.1 Fórmula de Bayes
> ```
> P(A|B) = [P(B|A) × P(A)] / P(B)
> ```
> - **P(A|B):** probabilidade de A ocorrer dado que B ocorreu (probabilidade **a posteriori**).
> - **P(B|A):** probabilidade de B ocorrer dado que A ocorreu (probabilidade condicional).
> - **P(A):** probabilidade de A ocorrer (probabilidade **a priori**).
> - **P(B):** probabilidade de B ocorrer.

## 2. Suposições Ingênuas

| SUPOSIÇÃO | DESCRIÇÃO |
| --- | --- |
| **Independência condicional** | As características (atributos) são **independentes entre si** – esta é a suposição "ingênua". |
| **Igual contribuição** | Cada evento (atributo) contribui igualmente para a classificação. |

> ### 2.1 Observação
> - Na prática, as características **não são independentes** (ex.: em um e-mail spam, a presença de certas palavras pode estar correlacionada).
> - Apesar disso, o Naive Bayes ainda funciona bem, especialmente em **classificação de textos**.

## 3. Funcionamento do Algoritmo

### 3.1 Treinamento

1. O algoritmo recebe dados de treinamento com atributos e categorias (rótulos).
2. Calcula a **probabilidade a priori** de cada categoria (com base na proporção de exemplos de cada classe).
3. Calcula a **probabilidade condicional** de cada atributo, dada cada categoria (ex.: P(palavra|spam)).

### 3.2 Predição (Classificação)

1. Para uma nova entrada, calcula a **probabilidade a posteriori** de cada categoria (P(categoria|entrada)).
2. Seleciona a categoria com **maior probabilidade** como a previsão.

### 3.3 Exemplo prático (classificação de e-mails)

- **Dataset:** cada linha = um e-mail; cada coluna = uma palavra (1 se presente, 0 se ausente).
- **Rótulo:** spam ou normal.
- **Treinamento:** o algoritmo calcula P(palavra|spam) e P(palavra|normal) para cada palavra.
- **Predição:** para um novo e-mail, calcula a probabilidade de ser spam com base nas palavras presentes.

## 4. Aplicações Típicas

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Filtragem de spam** | Classificar e-mails como spam ou normais. |
| **Análise de sentimento** | Classificar textos como positivos, negativos ou neutros. |
| **Classificação de documentos** | Categorizar textos em tópicos. |
| **Diagnóstico médico** | Prever a probabilidade de uma doença com base em sintomas. |

## 5. Vantagens e Desvantagens

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| Simples, rápido e eficiente. | Suposição de independência raramente é verdadeira. |
| Funciona bem com dados de alta dimensionalidade (ex.: textos). | Sensível a dados com pouca representação (probabilidades zero). |
| Lida bem com dados categóricos. | Requer tratamento para **suavização** (ex.: Laplace) para evitar probabilidades zero. |
| Requer poucos dados de treinamento. | Não é adequado para regressão (apenas classificação). |

## 6. Naive Bayes vs. Regressão Logística

| NAIVE BAYES | REGRESSÃO LOGÍSTICA |
| --- | --- |
| Classificador probabilístico. | Classificador probabilístico. |
| Baseado no Teorema de Bayes. | Baseado na função sigmoide. |
| Supõe independência entre atributos. | Não supõe independência entre atributos. |
| Melhor para textos e dados categóricos. | Melhor para dados numéricos e relações mais complexas. |
| Rápido e eficiente. | Pode ser mais preciso com dados bem ajustados. |

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/CEBRASPE/2023/TC-DF – Auditor)

**Item:** "O algoritmo Naive Bayes é utilizado para categorizar palavras com base na frequência; um exemplo do uso desse algoritmo é a classificação de e-mails como spam."

**Gabarito: Certo (C).**

### 7.2 (CESPE/CEBRASPE/2023/TC-DF – Auditor)

**Item:** "Naive Bayes é um algoritmo de machine learning supervisionado que realiza classificação com base no princípio da independência condicional de classe a partir do teorema de Bayes."

**Gabarito: Certo (C).**

### 7.3 (FGV/2024/PREFEITURA DE VITÓRIA – Estatístico)

**Item:** "Afirmativa correta sobre classificadores Naive Bayes:"

**Gabarito: e) utilizam a regra de Bayes para calcular a probabilidade posterior.**

### 7.4 (FGV/2023/RECEITA FEDERAL – Auditor)

**Item:** "Algoritmo implementado nos passos (probabilidade a priori, probabilidade condicional, maior probabilidade):"

**Gabarito: b) Naive Bayes.**

### 7.5 (FGV/2024/TCE-GO – Analista)

**Item:** "O princípio fundamental do algoritmo Naive Bayes:"

**Gabarito: c) considera a independência condicional entre os atributos dos dados.**

### 7.6 (CESPE/CEBRASPE/2024/ANATEL – Especialista)

**Item:** "Naive Bayes é um algoritmo de classificação baseado na aprendizagem por reforço."

**Gabarito: Errado (E).**

**Comentário:** Naive Bayes é baseado no **Teorema de Bayes** e no **aprendizado supervisionado**, não em aprendizado por reforço.

### 7.7 (CESPE/CEBRASPE/2024/ANATEL – Especialista)

**Item:** "Naive Bayes não pode ser empregado em atividades de classificação textual."

**Gabarito: Errado (E).**

**Comentário:** Classificação de texto é uma das principais aplicações do Naive Bayes (ex.: spam).

### 7.8 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** "A ingenuidade do modelo Naive Bayes é caracterizada pela:"

**Gabarito: c) suposição de independência condicional entre as variáveis preditoras.**

### 7.9 (CESPE/CEBRASPE/2025/TRT-10 – Analista)

**Item:** "O algoritmo Naive Bayes poderia ser utilizado na análise dos dados de A (idade, renda, filhos → empregado) e B (textos → spam)."

**Gabarito: Certo (C).**

**Comentário:** Naive Bayes pode ser usado com dados numéricos (A) e textos (B) para classificação.

### 7.10 (CESPE/CEBRASPE/2025/ANM – Especialista)

**Item:** "O Naive Bayes, algoritmo de classificação probabilística eficiente no uso de dados categóricos, é indicado para aplicações de classificação de texto, tais como filtragem de spams e classificação de textos."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/TC-DF/2023) | C |
| 02 (CESPE/TC-DF/2023) | C |
| 03 (FGV/VITÓRIA/2024) | e |
| 04 (FGV/RECEITA/2023) | b |
| 05 (FGV/TCE-GO/2024) | c |
| 06 (CESPE/ANATEL/2024) | E |
| 07 (CESPE/ANATEL/2024) | E |
| 08 (CESGRANRIO/IPEA/2024) | c |
| 09 (CESPE/TRT-10/2025) | C |
| 10 (CESPE/ANM/2025) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Naive Bayes** | Classificador probabilístico baseado no Teorema de Bayes. |
| **Aprendizado** | Supervisionado. |
| **Tipo de problema** | Classificação (não regressão). |
| **Suposição ingênua** | Independência condicional entre atributos. |
| **Fórmula base** | P(A|B) = P(B|A) × P(A) / P(B) |
| **Aplicações** | Filtragem de spam, análise de sentimento, classificação de textos. |
| **Vantagem** | Simples, rápido, eficiente com dados de alta dimensionalidade. |
| **Desvantagem** | Suposição de independência raramente é verdadeira. |

---

*Material complementar à aula "Naive Bayes" (professor Vitor Kessler/Gran Concursos).*