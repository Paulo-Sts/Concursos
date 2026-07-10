# Anotações – RNN e LSTM

## 1. Redes Neurais Recorrentes (RNN)

### 1.1 Conceito

- **RNN (Recurrent Neural Network – Rede Neural Recorrente)** é uma arquitetura de rede neural projetada para processar **dados sequenciais**.
- Ao contrário das redes *feedforward* (onde o fluxo é unidirecional), as RNNs possuem **conexões de retorno**: a saída de um neurônio em um instante **retorna como entrada** para o próprio neurônio (ou para camadas anteriores) no instante seguinte.
- **Característica principal:** **memória de curto prazo** – a informação do passado influencia o processamento do presente e do futuro.

> ### 1.2 Aplicações típicas
> - **Séries temporais** (previsão de temperatura, ações, etc.).
> - **Processamento de Linguagem Natural (PLN)** – cada palavra depende das anteriores.
> - Reconhecimento de fala.
> - Análise de sentimento.

### 1.3 Limitação das RNNs tradicionais

- **Problema do gradiente:** com sequências longas, o gradiente pode **desaparecer (vanishing gradient)** ou **explodir (exploding gradient)**.
- Isso faz com que a rede **"esqueça"** informações de passos mais antigos.

## 2. LSTM (Long Short-Term Memory)

### 2.1 Conceito

- **LSTM (Long Short-Term Memory)** é um tipo especial de **RNN** projetada para superar as limitações das RNNs tradicionais.
- Foi desenvolvida para **capturar dependências de longo prazo** em sequências longas.
- Utiliza **células de memória** com **mecanismos de porteamento (gates)** para controlar o fluxo de informações.

> ### 2.2 Inovação arquitetônica da LSTM
> - A principal inovação da LSTM são as **células de memória com mecanismos de gating** (portas).
> - Isso permite que a rede **decida o que lembrar, o que esquecer e o que revelar** a cada passo.

## 3. Estrutura da Célula LSTM

- Cada célula LSTM recebe **três entradas**:
  1. **`h_{t-1}`** – saída do passo anterior.
  2. **`c_{t-1}`** – memória do passo anterior.
  3. **`x_t`** – dado de entrada no instante atual.
- Produz **duas saídas**:
  1. **`c_t`** – memória atualizada.
  2. **`h_t`** – saída atual (estado oculto).

### 3.1 Portões (Gates) da LSTM

| PORTÃO | FUNÇÃO |
| --- | --- |
| **Forget Gate (Portão de Esquecimento)** | Decide quais informações da memória passada devem ser **esquecidas** (descartadas). |
| **Input Gate (Portão de Entrada)** | Decide **quais novas informações** devem ser armazenadas e **como** representá-las. |
| **Output Gate (Portão de Saída)** | Decide **o que deve ser revelado** como saída da célula no instante atual. |

### 3.2 Fluxo de processamento

1. **Forget Gate:** aplica uma função sigmoide (`σ`) sobre `h_{t-1}` e `x_t` – decide o que esquecer da memória `c_{t-1}`.
2. **Input Gate:** combina uma sigmoide (decide o que guardar) com uma tangente hiperbólica (`tanh`) (cria uma "versão" da nova informação).
3. **Atualização da memória:** `c_t = (c_{t-1} × f) + (i × g)` – soma do que foi mantido com o que foi aprendido.
4. **Output Gate:** aplica sigmoide sobre `h_{t-1}` e `x_t`, e multiplica por `tanh(c_t)` – gera a saída `h_t`.

> ### 3.2.1 Funções de ativação na LSTM
> - **Sigmoide (`σ`):** atua como um "filtro de importância" – decide quanto de cada informação passa (valores entre 0 e 1).
> - **Tangente hiperbólica (`tanh`):** transforma a informação em um formato adequado (valores entre -1 e 1).

## 4. Problemas Resolvidos pela LSTM

| PROBLEMA | COMO A LSTM RESOLVE |
| --- | --- |
| **Vanishing Gradient** | As células de memória e os portões permitem que o gradiente flua por longas sequências sem desaparecer. |
| **Exploding Gradient** | O porteamento e a normalização ajudam a controlar a magnitude dos gradientes. |
| **Esquecimento de longo prazo** | O Forget Gate decide o que manter; a memória `c_t` preserva informações por longos períodos. |

## 5. LSTM vs. RNN vs. CNN vs. Transformer

| ARQUITETURA | APLICAÇÃO PRINCIPAL | CARACTERÍSTICA |
| --- | --- | --- |
| **RNN** | Dados sequenciais | Memória de curto prazo, sofre com vanishing gradient. |
| **LSTM** | Dados sequenciais longos | Memória de longo prazo, portões de controle. |
| **CNN** | Imagens, visão computacional | Extrai características espaciais. |
| **Transformer** | PLN, séries longas | Mecanismo de atenção, processa sequências em paralelo. |

> ### 5.1 Transformer vs. LSTM
> - Os **Transformers** superaram as LSTMs em muitas aplicações de PLN (ex.: GPT, BERT).
> - **Vantagem:** processam sequências **em paralelo** (não sequencialmente), com mecanismo de atenção.
> - **Desvantagem:** custo computacional mais alto.

## 6. Questões de Concurso Comentadas

### 6.1 (FGV/PREF. MACAÉ/2024 – Analista)

**Item:** "Técnica mais adequada para capturar a dependência contextual de palavras em uma frase."

**Gabarito: d) Redes Neurais Recorrentes (RNN).**

**Comentário:** RNNs são projetadas para capturar dependências sequenciais, como as existentes entre palavras em uma frase.

### 6.2 (FGV/CVM/2024 – Analista)

**Item:** "Inovação arquitetônica distintiva da LSTM."

**Gabarito: b) As células de memória com mecanismos de gating.**

**Comentário:** A inovação da LSTM são os portões (forget, input, output) que controlam o fluxo de informações na célula de memória.

### 6.3 (FGV/TRF-1/2024 – Analista)

**Item:** "Elemento responsável por extrair informação útil do estado atual para ser utilizada no cálculo do estado oculto."

**Gabarito: a) Saída (Output Gate).**

**Comentário:** O Output Gate define o que será revelado como saída da célula (`h_t`).

### 6.4 (CESPE/SUSEP/2025 – Analista)

**Item:** "Os modelos baseados em arquitetura transformer superaram as RNN e LSTM principalmente pela capacidade de tais modelos processarem sequências mais longas com menor custo computacional."

**Gabarito: Errado (E).**

**Comentário:** Transformers processam sequências longas com **maior custo computacional**, não menor.

### 6.5 (CESPE/PF/2025 – Perito)

**Item:** "Vanishing gradient e exploding gradient são duas condições que podem ser encontradas em redes RNN; o emprego de célula de memória busca mitigar a ocorrência dessas condições em redes LSTM."

**Gabarito: Certo (C).**

### 6.6 (FGV/MF/2024 – Auditor)

**Item:** "Rede neural especialmente projetada para superar o problema do desvanecimento do gradiente em sequências longas."

**Gabarito: b) LSTM.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/MACAÉ/2024) | d |
| 02 (FGV/CVM/2024) | b |
| 03 (FGV/TRF-1/2024) | a |
| 04 (CESPE/SUSEP/2025) | E |
| 05 (CESPE/PF/2025) | C |
| 06 (FGV/MF/2024) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **RNN** | Rede neural com conexões de retorno – processa sequências. |
| **LSTM** | Tipo de RNN com células de memória e portões (forget, input, output). |
| **Forget Gate** | Decide o que esquecer da memória passada. |
| **Input Gate** | Decide o que aprender e como representar. |
| **Output Gate** | Decide o que revelar como saída. |
| **Vanishing Gradient** | Gradiente desaparece em sequências longas – LSTM resolve. |
| **Exploding Gradient** | Gradiente explode – LSTM ajuda a controlar. |
| **LSTM vs. RNN** | LSTM tem memória de longo prazo; RNN tradicional tem memória de curto prazo. |
| **Transformer** | Arquitetura com atenção – superou LSTM em PLN, mas custa mais. |

---

*Material complementar à aula "RNN e LSTM" (professor Vitor Alexandre Kessler De Almeida/Gran Concursos).*