# Anotações – PLN – Introdução

## 1. Conceito de Processamento de Linguagem Natural (PLN)

- **PLN (Processamento de Linguagem Natural)** – *NLP – Natural Language Processing* em inglês.
- É um campo da **Inteligência Artificial** que busca permitir que computadores **compreendam, interpretem e gerem** linguagem humana (escrita ou falada).
- Conecta áreas como: **Linguística, Estatística, Machine Learning, Redes Neurais e Computação**.

> ### 1.1 O que é PLN?
> - Reconhece texto, classifica-o e o gera (ex.: IA generativa de texto).
> - Exemplo: áudio é transformado em texto, que é processado pela IA para gerar uma resposta.

## 2. Por que o PLN é Desafiador?

A linguagem humana é complexa e apresenta diversos fenômenos que dificultam o processamento automático:

| DESAFIO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Ambiguidade** | Uma mesma palavra pode ter múltiplos significados. | "Manga" (fruta ou parte da roupa); "Sinistro" (acidente ou algo legal). |
| **Ironia / Sarcasmo** | O sentido literal difere do sentido real. | "Que dia maravilhoso!" em um dia de chuva. |
| **Contexto cultural** | Palavras têm significados diferentes em regiões distintas. | "Pai d'égua" (Belém) = algo bom. |
| **Polissemia** | Palavras com múltiplos sentidos. | "Banco" (instituição financeira ou assento). |
| **Dependências longas** | O significado de uma palavra pode depender de outra distante no texto. | O sujeito de uma oração pode estar longe do verbo. |
| **Ruídos** | Erros de digitação, gírias, variações, pronomes neutros. | "vc" em vez de "você". |

## 3. Etapas do Processamento de Linguagem Natural

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **1. Coleta** | Reunir os dados textuais (corpus). |
| **2. Pré-processamento** | Limpeza e preparação – reduzir a quantidade de palavras processadas. |
| **3. Vetorização (Representação)** | Transformar texto em números (vetores) para que algoritmos possam processar. |
| **4. Modelagem** | Aplicar algoritmos de ML/DL para classificação, geração, etc. |

## 4. Paradigmas do PLN

| PARADIGMA | DESCRIÇÃO | TÉCNICAS |
| --- | --- | --- |
| **Simbólico (Baseado em Regras)** | Regras gramaticais e léxicos são programados explicitamente por especialistas. | Árvores sintáticas, gramáticas formais, dicionários. |
| **Estatístico (Probabilístico)** | A linguagem é tratada como um fenômeno estatístico; o computador aprende padrões a partir de grandes quantidades de texto. | Naive Bayes, TF-IDF. |
| **Neural (Aprendizado Profundo)** | A linguagem é representada como vetores densos que capturam significado; a rede aprende representações distribuídas. | Word2Vec, GloVe, RNN, LSTM, Transformers (BERT, GPT, T5, LLaMA). |

> ### 4.1 Paradigma Neural
> - A principal inovação é a representação de palavras como **vetores densos (word embeddings)** que capturam relações semânticas.
> - **Word2Vec** e **GloVe** são exemplos de técnicas de *word embedding*.
> - Modelos modernos como **GPT** e **BERT** são baseados em **Transformers**.

## 5. Aplicações Clássicas de PLN

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Chatbots e assistentes virtuais** | Interação com usuários (Alexa, Siri, etc.). |
| **Análise de sentimento** | Classificar textos como positivos, negativos ou neutros (ex.: comentários de produtos, redes sociais). |
| **Tradução automática** | Traduzir textos entre idiomas. |
| **Corretores ortográficos** | Corrigir erros de digitação e gramática. |
| **Busca inteligente** | Melhorar a relevância de buscas. |
| **Sistemas de recomendação** | Sugerir conteúdo com base em preferências. |
| **Extração de informação** | Extrair dados estruturados de documentos não estruturados. |
| **Geração de relatórios automáticos** | Produzir textos a partir de dados. |

## 6. Questões de Concurso Comentadas

### 6.1 (CESPE/ANTT/2024 – Especialista)

**Item:** "Para permitir que computadores processem a linguagem humana na forma de dados de texto ou de voz, entendendo seu significado integral, o processamento de linguagem natural combina linguística computacional, modelagem com base em regras da linguagem humana, com modelos estatísticos, de machine learning e de deep learning."

**Gabarito: Certo (C).**

**Comentário:** A afirmação abrange os três paradigmas (simbólico, estatístico e neural).

### 6.2 (FGV/RECEITA FEDERAL/2023 – Auditor)

**Afirmativas:**
- I – PLN envolve compreensão e geração de linguagem humana. **(V)**
- II – A tarefa principal do PLN é traduzir textos. **(F)** – tradução é uma das tarefas, não a principal.
- III – PLN não é utilizado para processamento de voz. **(F)** – PLN inclui reconhecimento de fala.
- IV – PLN é aplicado em sistemas de recuperação de informação e assistentes virtuais. **(V)**

**Gabarito: a) I e IV, apenas.**

### 6.3 (CESPE/ANTT/2024 – Especialista)

**Item:** "O PNL estuda o desenvolvimento de programas computacionais que analisam, reconhecem e/ou geram textos em linguagens humanas ou naturais."

**Gabarito: Certo (C).**

**Comentário:** A sigla correta é PLN (Processamento de Linguagem Natural); em inglês, NLP.

### 6.4 (CESPE/CNPQ/2024 – Analista)

**Item:** "PNL é um campo da ciência da computação que trata da interação entre computadores e linguagens humanas e tem por objetivo proporcionar aos computadores a capacidade de compreender e reproduzir a linguagem humana."

**Gabarito: Certo (C).**

### 6.5 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "Modelos recentes, como o Gemini e o GPT, embora compartilhem algumas similaridades com o PLN, têm sua base fundamental na aplicação de aprendizado profundo, uma abordagem que dispensa a necessidade de regras linguísticas explícitas."

**Gabarito: Errado (E).**

**Comentário:** GPT e Gemini **são PLN** – são modelos de linguagem baseados em deep learning (Transformers). A afirmação tenta separá-los do PLN, o que é incorreto.

### 6.6 (FGV/TCE-GO/2024 – Analista)

**Item:** "São paradigmas de PLN:"

**Gabarito: a) Neural e Simbólico.** (Faltou o estatístico na lista, mas dentre as opções, esta é a mais correta).

### 6.7 (CESGRANRIO/BNDES/2024 – Analista)

**Item:** "Aplicação de PLN para análise de grandes volumes de textos."

**Gabarito: b) empregar a extração de informação para identificar e classificar as relações entre as entidades em um corpus de documentos, e em seguida aplicar a sumarização de texto para criar resumos automáticos do conteúdo.**

**Comentário:** As demais alternativas confundem tarefas de pré-processamento (POS-tagging, NER) com aplicações finais de PLN.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/ANTT/2024) | C |
| 02 (FGV/RECEITA/2023) | a |
| 03 (CESPE/ANTT/2024) | C |
| 04 (CESPE/CNPQ/2024) | C |
| 05 (CESPE/EMBRAPA/2025) | E |
| 06 (FGV/TCE-GO/2024) | a |
| 07 (CESGRANRIO/BNDES/2024) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **PLN** | IA para compreender, interpretar e gerar linguagem humana. |
| **Paradigma Simbólico** | Regras gramaticais programadas por especialistas. |
| **Paradigma Estatístico** | Aprende padrões a partir de grandes volumes de texto. |
| **Paradigma Neural** | Representações vetoriais densas (Word2Vec, Transformers). |
| **Aplicações** | Chatbots, análise de sentimento, tradução, corretores, busca inteligente. |
| **Desafios** | Ambiguidade, ironia, contexto cultural, polissemia. |
| **Etapas** | Coleta → Pré-processamento → Vetorização → Modelagem. |

---

*Material complementar à aula "PLN – Introdução" (professor Vitor Alexandre Kessler De Almeida/Gran Concursos).*