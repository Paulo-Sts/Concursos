# Anotações – Introdução ao Machine Learning

## 1. Conceito de Machine Learning

- **Machine Learning (ML)** é uma **subárea da Inteligência Artificial (IA)**.
- Objetivo: criar máquinas que **aprendem a partir de dados**, em vez de seguir regras fixas e programadas manualmente.
- O modelo identifica **padrões** e faz **previsões** automaticamente.

> ### 1.1 Analogia (aprendizado humano vs. máquina)
> - Assim como uma pessoa que repete um trajeto várias vezes e aprende o caminho, a máquina aprende com a **exposição repetida a dados históricos**.
> - Quanto mais dados e exemplos, mais precisos se tornam os resultados.

### 1.2 Diferença entre sistemas tradicionais e ML

| SISTEMA TRADICIONAL | SISTEMA DE MACHINE LEARNING |
| --- | --- |
| Regras fixas programadas manualmente. | Regras são **aprendidas** a partir dos dados. |
| O programador define explicitamente a lógica. | O sistema descobre padrões por conta própria. |
| Exemplo: "bloquear compras acima de R$ 1.000". | Exemplo: analisa milhões de transações e aprende quais padrões indicam fraude. |

> ### 1.2.1 Contexto histórico
> - Nos anos 1950/1960, surgiram os primeiros algoritmos de IA (ex.: xadrez).
> - O avanço só ocorreu com:
>   - **Grandes volumes de dados** (Big Data).
>   - **Capacidade de processamento** adequada (hardware).
> - A partir do final dos anos 2000, houve uma **explosão** no uso de IA.

## 2. Três Grandes Aplicações do Machine Learning

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Análise descritiva** | Identifica padrões ocultos em grandes bases de dados. | Agrupar alunos por desempenho (baixo, médio, alto). |
| **Análise preditiva** | Utiliza dados históricos para prever eventos futuros. | Detecção de fraudes em cartões de crédito. |
| **IA Generativa** | Cria novos conteúdos originais com base em dados de treinamento. | Textos, imagens, vídeos, músicas. |

## 3. Etapas de um Projeto de Machine Learning

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **Coleta e preparação dos dados** | Reunir informações relevantes de diversas fontes (ex.: Data Lakes). |
| **Pré-processamento** | Limpar, transformar, normalizar, integrar e padronizar os dados. |
| **Treinamento do modelo** | O algoritmo aprende a partir dos exemplos (iterativamente). |
| **Validação e teste** | Avaliar se o modelo generaliza bem para dados nunca vistos. |
| **Implantação** | Uso prático do modelo para previsões, classificações ou apoio à decisão. |

> ### 3.1 Dataset
> - É o conjunto de dados **estruturado** (linhas e colunas) utilizado para treinar o modelo.
> - A etapa de pré-processamento é a **mais trabalhosa**: dados heterogêneos, inconsistentes, com lacunas.

## 4. Estrutura do Dataset – Terminologia

| TERMO | SINÔNIMOS | DESCRIÇÃO |
| --- | --- | --- |
| **Linha** | Exemplo, caso, registro, instância, dado, ponto. | Cada unidade de informação apresentada ao algoritmo. |
| **Coluna** | Atributo, campo, feature, variável independente, dimensão. | Característica que descreve cada exemplo. |
| **Classe** | Rótulo, alvo, target, variável dependente, meta. | O que o modelo precisa aprender a prever (apenas em aprendizado supervisionado). |

## 5. Representação Matemática

```
Y = f(X)
```

- **X** = conjunto de variáveis de entrada (atributos, preditores).
- **Y** = variável de saída (classe, alvo).
- **f** = modelo de aprendizado de máquina (função aprendida a partir dos dados).

## 6. Questões de Concurso Comentadas

### 6.1 (CESPE/CEBRASPE/DATAPREV/2023)

**Item:** "O machine learning é um subconjunto da inteligência artificial, o qual é utilizado para analisar, por meio de algoritmos, grandes volumes de dados e permite que uma máquina ou um sistema aprenda e melhore com base na experiência."

**Gabarito: Certo (C).**

### 6.2 (CESPE/CEBRASPE/EMBRAPA/2025)

**Item:** "A técnica de machine learning é particularmente aplicável em situações em que há um baixo conjunto de dados para análise."

**Gabarito: Errado (E).**

**Comentário:** ML é indicado para **grandes conjuntos de dados** – a aprendizagem ocorre a partir da análise de padrões em larga escala.

### 6.3 (CESPE/CEBRASPE/ANM/2025)

**Item:** "Aprendizado de máquina é o processo de treinar um modelo para identificar padrões e fazer previsões ou gerar novos conteúdos com base nas informações processadas."

**Gabarito: Certo (C).**

### 6.4 (CESPE/CEBRASPE/MPO/2024)

**Item:** "Pode-se utilizar machine learning para um mecanismo de busca na Internet que funcione de forma automatizada."

**Gabarito: Certo (C).**

### 6.5 (CESPE/CEBRASPE/CAESB-DF/2025)

**Item:** "Ciência do desenvolvimento de algoritmos e modelos estatísticos utilizados por sistemas de computador para a realização de tarefas sem instruções explícitas, baseando-se em padrões e inferências, de modo que um sistema aprenda e melhore automaticamente e com base na experiência."

**Gabarito: d) machine learning.**

### 6.6 (CESPE/CEBRASPE/CTI/2024)

**Item:** "Aprendizado de máquina pode ser definido como a criação e o uso de modelos que são aprendidos a partir dos dados."

**Gabarito: Certo (C).**

### 6.7 (CESPE/CEBRASPE/CTI/2024)

**Item:** "O aprendizado de máquina computacional tem como objetivo validar padrões em dados e ratificar padrões que podem ser observados explicitamente nos dados."

**Gabarito: Errado (E).**

**Comentário:** O objetivo é **descobrir e extrair padrões implícitos**, não apenas validar os já observáveis.

### 6.8 (CESPE/CEBRASPE/TCE-PR/2024)

**Item:** "No processo de classificação do aprendizado de máquina, a etapa que inicia o processo é conhecida como:"

**Gabarito: d) treinamento.**

**Comentário:** O processo efetivo de ML começa com o **treinamento do modelo**, etapa em que o algoritmo aprende a partir dos dados.

### 6.9 (CESPE/CEBRASPE/SERPRO/2023)

**Item:** "Em aprendizado de máquina, as características de entrada e saída são definidas, respectivamente, como atributos previsores e atributos alvo ou meta."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/DATAPREV/2023) | C |
| 02 (CESPE/EMBRAPA/2025) | E |
| 03 (CESPE/ANM/2025) | C |
| 04 (CESPE/MPO/2024) | C |
| 05 (CESPE/CAESB/2025) | d |
| 06 (CESPE/CTI/2024) | C |
| 07 (CESPE/CTI/2024) | E |
| 08 (CESPE/TCE-PR/2024) | d |
| 09 (CESPE/SERPRO/2023) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Machine Learning** | Subárea da IA que aprende padrões a partir de dados. |
| **Sistema tradicional** | Regras fixas programadas manualmente. |
| **Sistema ML** | Regras aprendidas automaticamente a partir dos dados. |
| **Análise descritiva** | Identifica padrões ocultos. |
| **Análise preditiva** | Preve eventos futuros com base em dados históricos. |
| **IA Generativa** | Cria novos conteúdos. |
| **Dataset** | Conjunto estruturado de dados (linhas e colunas). |
| **Features (atributos)** | Variáveis de entrada (X). |
| **Target (alvo/classe)** | Variável de saída (Y). |

---

*Material complementar à aula "Introdução ao Machine Learning" (professor Vitor Kessler/Gran Concursos).*