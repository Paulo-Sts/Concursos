# Anotações – Redes Neurais Convolucionais (CNNs)

## 1. Conceito de CNN

- **CNN (Convolutional Neural Network – Rede Neural Convolucional)** é uma arquitetura de **Deep Learning** especializada no processamento de **dados com estrutura espacial**.
- **Principal aplicação:** **visão computacional** – classificação, detecção e segmentação de imagens e vídeos.
- Também pode ser usada para processamento de texto (em menor escala) e séries temporais.

> ### 1.1 Características principais
> - **Fluxo unidirecional** (feedforward).
> - Utiliza **filtros (kernels)** para extrair características das imagens.
> - Aprendizado **hierárquico**: camadas iniciais capturam características simples (linhas, bordas); camadas mais profundas capturam estruturas complexas (olhos, rostos, objetos).

## 2. Camadas de uma CNN

| CAMADA | FUNÇÃO |
| --- | --- |
| **Camada de entrada** | Recebe a imagem (ex.: matriz de pixels). |
| **Camada de convolução** | Aplica **filtros (kernels)** sobre a imagem para extrair características locais (bordas, texturas). Gera **mapas de características**. |
| **Camada de ativação** | Geralmente usa **ReLU** para introduzir não linearidade. |
| **Camada de pooling (subamostragem)** | Reduz a dimensionalidade dos mapas de características (diminui carga computacional e controle de overfitting). |
| **Camada totalmente conectada (flatten + dense)** | Achata os dados e os conecta a uma rede neural tradicional para classificação final. |
| **Camada de saída** | Produz a classificação (ex.: "gato", "cachorro"). |

> ### 2.1 Pooling (Subamostragem)
> - **Objetivo:** reduzir a quantidade de dados entre camadas convolucionais.
> - **Tipos:** Max Pooling (pega o valor máximo de uma região), Average Pooling (pega a média).
> - Reduz o uso de memória, a carga computacional e ajuda a controlar **overfitting**.

## 3. Hiperparâmetros das Camadas Convolucionais

| PARÂMETRO | DESCRIÇÃO |
| --- | --- |
| **Stride** | Distância entre as aplicações do filtro (passos). |
| **Dilation** | Aumenta o campo de visão do filtro sem aumentar o número de pixels (expande o filtro). |
| **Kernel (filtro)** | Matriz que desliza sobre a imagem para extrair características. |

## 4. Aprendizado por Transferência (Transfer Learning) com CNNs

- **Transfer Learning:** utiliza um modelo pré-treinado (ex.: ResNet, AlexNet) em uma tarefa genérica (ex.: ImageNet) e o adapta para uma tarefa específica (ex.: classificar passarinhos).
- **Vantagem:** não é necessário treinar do zero – o modelo já aprendeu características básicas.
- **Fine-tuning:** ajusta todos os parâmetros do modelo para a nova tarefa (retreina todo o modelo).

## 5. Arquiteturas Famosas de CNN

| ARQUITETURA | DESCRIÇÃO |
| --- | --- |
| **LeNet-5** | Uma das primeiras CNNs, usada para reconhecimento de dígitos manuscritos. |
| **AlexNet** | CNN que venceu o ImageNet em 2012 – popularizou o Deep Learning. |
| **ResNet** | Introduziu as *skip connections* (residuais), permitindo redes muito profundas. |

## 6. CNN vs. RNN – Aplicações

| ARQUITETURA | APLICAÇÃO PRINCIPAL |
| --- | --- |
| **CNN** | Imagens, vídeos, visão computacional. |
| **RNN / LSTM** | Dados sequenciais (texto, áudio, séries temporais). |

## 7. Questões de Concurso Comentadas

### 7.1 (FGV/TCE-PA/2024 – Auditor)

**Item:** Arquitetura com fluxo unidirecional, camadas que filtram características e reduzem dimensionalidade.

**Gabarito: c) convolucionais.**

### 7.2 (CESPE/ANTT/2024 – Especialista)

**Item:** "As redes neurais convolucionais distinguem-se das demais redes neurais por seu desempenho superior, tendo suas entradas três tipos principais de camadas: convolucional, de agrupamento e totalmente conectada."

**Gabarito: Certo (C).**

### 7.3 (CESPE/TRF-6/2025 – Analista)

**Item:** "As redes neurais convolucionais são projetadas para processar dados sequenciais, como texto ou áudio."

**Gabarito: Errado (E).**

**Comentário:** Isso é característica das **redes neurais recorrentes (RNN)** – CNN é para imagens.

### 7.4 (FGV/CGE-SC/2023 – Auditor)

**Item:** "Ao treinar CNNs utilizando transferência de aprendizado para ajuste fino, começamos com um modelo pré-treinado e atualizamos todos os parâmetros do modelo para nossa nova tarefa."

**Gabarito: b)** (correta).

### 7.5 (CESPE/TJ-PA/2025 – Analista)

**Item:** "Redes neurais convolucionais são utilizadas principalmente em tarefas de processamento sequencial, como tradução automática."

**Gabarito: Errado (E).**

**Comentário:** CNN é para **imagens**; RNN é para processamento sequencial.

### 7.6 (CESPE/PF/2025 – Perito)

**Item:** "Entre duas camadas convolucionais de uma CNN, a aplicação de pooling permite aumentar a dimensionalidade da rede."

**Gabarito: Errado (E).**

**Comentário:** Pooling **reduz** a dimensionalidade (subamostragem).

### 7.7 (CESPE/ANTT/2024 – Especialista)

**Item:** "No treinamento, as redes neurais convolucionais recebem imagens e aplicam filtros, que possibilitam a extração de características; após essa extração, a camada de rede neural é utilizada para classificar a imagem."

**Gabarito: Certo (C).**

### 7.8 (CESPE/BDMG/2025 – Analista)

**Item:** "As redes neurais convolucionais são especialmente adequadas para o processamento de dados sequenciais, como séries temporais e texto."

**Gabarito: Errado (E).**

**Comentário:** CNN é para imagens; RNN é para sequências.

### 7.9 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "Os algoritmos de aprendizado profundo, como as redes neurais convolucionais, vêm sendo aplicados no mapeamento de uso e cobertura da terra devido à sua capacidade de identificar padrões espaciais complexos."

**Gabarito: Certo (C).**

### 7.10 (CESPE/PF/2025 – Perito)

**Item:** "Em uma rede CNN, a dimensão do mapa de ativação depende, entre outros hiperparâmetros, dos parâmetros denominados stride e dilation."

**Gabarito: Certo (C).**

### 7.11 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "Os sistemas de visão computacional baseados em técnicas de redes neurais convolucionais podem ser empregados para identificar e classificar árvores em tempo real."

**Gabarito: Certo (C).**

### 7.12 (CESPE/SUSEP/2025 – Analista)

**Item:** "As redes neurais convolucionais (CNN) são fundamentais para tarefas de visão computacional porque implementam operações de convolução que permitem a extração hierárquica de características visuais, desde bordas e texturas em camadas iniciais, até estruturas mais complexas em camadas profundas."

**Gabarito: Certo (C).**

### 7.13 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "As redes neurais convolucionais são amplamente utilizadas em bioinformática para o processamento de sequências genômicas."

**Gabarito: Errado (E).**

**Comentário:** Sequências são processadas por **RNNs** – CNN é para imagens.

### 7.14 (FGV/TCE-RR/2025 – Auditor)

**Afirmativas:**
- I – Pooling é a camada de subamostragem, não convolucional. **(F)**
- II – LeNet-5, AlexNet e ResNet são arquiteturas CNN. **(V)**
- III – CNN não é composta exclusivamente por convolução e pooling – tem camadas totalmente conectadas. **(F)**

**Gabarito: b) II, apenas.**

### 7.15 (CESPE/EMBRAPA/2025 – Analista)

**Item:** "A utilização de redes neurais convolucionais (CNNs) para a detecção de doenças em plantas pode ser mais eficaz que a inspeção manual, já que as CNNs conseguem identificar padrões complexos em imagens, porém, sua acurácia depende da quantidade e qualidade dos dados de treinamento."

**Gabarito: Certo (C).**

### 7.16 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "A operação de convolução nas CNN gera mapas de características... Esse processo resulta em uma transformação que não preserva necessariamente a posição espacial das informações relevantes da imagem."

**Gabarito: Errado (E).**

**Comentário:** A posição espacial **deve ser preservada** – é essencial para a interpretação da imagem.

### 7.17 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "No emprego das redes neurais convolucionais... os módulos iniciais conseguem identificar linhas e bordas; os módulos seguintes organizam esses padrões em texturas... os últimos módulos combinam esses elementos em objetos de interesse."

**Gabarito: Certo (C).**

### 7.18 (CESPE/CAESB-DF/2025 – Analista)

**Item:** "Redes neurais convolucionais podem ser usadas tanto para a classificação, em que a rede atribui rótulos a imagens inteiras, quanto para a segmentação, em que a rede identifica regiões específicas da imagem e fornece um mapa pixel a pixel."

**Gabarito: d)** (correta).

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/TCE-PA/2024) | c |
| 02 (CESPE/ANTT/2024) | C |
| 03 (CESPE/TRF-6/2025) | E |
| 04 (FGV/CGE-SC/2023) | b |
| 05 (CESPE/TJ-PA/2025) | E |
| 06 (CESPE/PF/2025) | E |
| 07 (CESPE/ANTT/2024) | C |
| 08 (CESPE/BDMG/2025) | E |
| 09 (CESPE/EMBRAPA/2025) | C |
| 10 (CESPE/PF/2025) | C |
| 11 (CESPE/EMBRAPA/2025) | C |
| 12 (CESPE/SUSEP/2025) | C |
| 13 (CESPE/EMBRAPA/2025) | E |
| 14 (FGV/TCE-RR/2025) | b |
| 15 (CESPE/EMBRAPA/2025) | C |
| 16 (CESPE/EMBRAPA/2025) | E |
| 17 (CESPE/EMBRAPA/2025) | C |
| 18 (CESPE/CAESB/2025) | d |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **CNN** | Rede neural para imagens/vídeos. |
| **Convolução** | Aplica filtros (kernels) para extrair características. |
| **Pooling** | Reduz dimensionalidade (subamostragem). |
| **Flatten** | Achata os dados para entrada em uma rede densa. |
| **ReLU** | Função de ativação comum em CNNs. |
| **Stride / Dilation** | Hiperparâmetros que afetam o mapa de características. |
| **Transfer Learning** | Reutiliza modelo pré-treinado para nova tarefa. |
| **CNN ≠ RNN** | CNN = imagens; RNN = sequências (texto, áudio). |

---

*Material complementar à aula "Redes Neurais Convolucionais" (professor Vitor Kessler/Gran Concursos).*