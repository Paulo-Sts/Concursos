# Anotações – Deep Learning – Introdução

## 1. Conceito de Deep Learning

- **Deep Learning (Aprendizado Profundo)** é uma **subárea do Machine Learning**.
- Utiliza **redes neurais artificiais com muitas camadas** (redes profundas).
- Permite que o sistema aprenda **representações de dados em múltiplos níveis de abstração**.

> ### 1.1 Hierarquia das áreas
> - **Inteligência Artificial (IA):** desenvolver sistemas inteligentes.
> - **Machine Learning:** desenvolver sistemas que **aprendem** a partir de dados.
> - **Deep Learning:** desenvolver sistemas que aprendem usando **redes neurais multicamadas**.

## 2. Arquitetura de uma Rede Neural Profunda

| CAMADA | FUNÇÃO |
| --- | --- |
| **Camada de entrada** | Recebe os dados brutos (ex.: pixels de uma imagem, palavras de um texto). |
| **Camadas ocultas (hidden layers)** | Processam os dados progressivamente, extraindo características **cada vez mais complexas**. |
| **Camada de saída** | Produz o resultado final (classificação, previsão, etc.). |

> ### 2.1 Camadas ocultas e abstração
> - **Camadas iniciais:** capturam características **simples** (ex.: bordas, cores, linhas em imagens).
> - **Camadas mais profundas:** capturam características **complexas** (ex.: olhos, nariz, rosto).
> - Esse aprendizado hierárquico é o que torna o Deep Learning tão poderoso.

## 3. Exemplos de Arquiteturas de Deep Learning

| ARQUITETURA | DESCRIÇÃO | APLICAÇÃO |
| --- | --- | --- |
| **CNN (Convolutional Neural Network)** | Redes neurais convolucionais – utilizam camadas de convolução para extrair características espaciais. | Visão computacional, reconhecimento de imagens, diagnóstico por imagem. |
| **RNN (Recurrent Neural Network)** | Redes neurais recorrentes – possuem conexões de volta (memória). | Séries temporais, processamento de linguagem natural (texto, áudio). |
| **LSTM (Long Short-Term Memory)** | Tipo especial de RNN que resolve o problema do *gradiente desaparecendo*. | Análise de séries históricas, reconhecimento de fala. |
| **Transformer** | Arquitetura baseada em mecanismo de atenção. | IAs generativas de texto (ex.: GPT). |
| **Stable Diffusion** | Rede neural para geração de imagens. | Geração de imagens a partir de texto. |

## 4. Treinamento de Redes Neurais – Backpropagation

- **Backpropagation (retropropagação)** é o algoritmo de treinamento de redes neurais.
- **Processo:**
  1. **Forward Propagation:** a entrada percorre a rede até a saída (produz uma predição).
  2. **Cálculo da perda:** compara-se a saída prevista com o valor real (função de perda).
  3. **Backward Propagation:** o erro é propagado de volta pela rede.
  4. **Ajuste dos pesos:** os pesos são atualizados para minimizar a função de perda (gradiente descendente).

## 5. GPUs, TPUs e NPUs

| PROCESSADOR | DESCRIÇÃO |
| --- | --- |
| **GPU (Graphics Processing Unit)** | Processador gráfico – acelera cálculos matriciais e iterativos, essenciais para treinamento de redes neurais. |
| **TPU (Tensor Processing Unit)** | Processador específico para treinamento de IA, desenvolvido pelo Google. |
| **NPU (Neural Processing Unit)** | Processador para dispositivos móveis e IoT, otimizado para inferência de IA (processamento rápido, baixo consumo). |

## 6. Deep Learning e Dados

- **Requer grandes volumes de dados** – redes profundas precisam de muitos exemplos para aprender.
- **Não elimina a necessidade de pré-processamento** – dados ainda precisam ser limpos e preparados.
- Pode trabalhar com dados **não estruturados** (imagens, textos, áudio).

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/ANATEL/2024 – Especialista)

**Item:** "Deep learning é um tipo de aprendizado de máquina que usa redes neurais artificiais para permitir que sistemas digitais aprendam e tomem decisões com base em dados não estruturados e não rotulados."

**Gabarito: Certo (C).**

**Comentário:** Deep learning usa redes neurais profundas e pode trabalhar com dados não estruturados (imagens, textos).

### 7.2 (CESPE/CNPQ/2024 – Analista)

**Item:** "Deep learning é um algoritmo que simula o cérebro humano por meio de algoritmos probabilísticos de aprendizado do comportamento em que uma população de representações abstratas de solução é selecionada em busca de soluções melhores."

**Gabarito: Errado (E).**

**Comentário:** A descrição corresponde a **algoritmos genéticos**, não a deep learning.

### 7.3 (CESPE/ANTT/2024 – Especialista)

**Item:** "As redes neurais de deep learning tentam imitar o cérebro humano por meio de uma combinação de entradas de dados, pesos e viés; esses elementos trabalham juntos para reconhecer, classificar e descrever com precisão os objetos dentro dos dados."

**Gabarito: Certo (C).**

### 7.4 (CESPE/STM/2025 – Analista Judiciário)

**Item:** "Deep learning é um campo da IA cujos modelos conseguem reconhecer padrões de dados, tais como imagens e textos, para produzir insights e previsões precisas, sendo as redes neurais sua tecnologia subjacente."

**Gabarito: Certo (C).**

### 7.5 (CESPE/ANM/2025 – Especialista)

**Item:** "O uso de GPUs e TPUs acelera os cálculos necessários para operações matriciais e retropropagação em modelos de deep learning."

**Gabarito: Certo (C).**

### 7.6 (CESPE/ANM/2025 – Especialista)

**Item:** "O deep learning elimina completamente a necessidade de pré-processamento de dados, pois as redes neurais são capazes de aprender todas as características automaticamente."

**Gabarito: Errado (E).**

**Comentário:** Deep learning **não elimina** a necessidade de pré-processamento – dados ainda precisam ser limpos e preparados.

### 7.7 (CESPE/ANTT/2024 – Especialista)

**Item:** "As redes neurais artificiais são um subconjunto de machine learning, estão no cerne dos algoritmos de deep learning e são compostas por camadas de um nó, contendo uma camada de entrada, uma ou mais camadas ocultas e uma camada de saída."

**Gabarito: Certo (C).**

### 7.8 (CESPE/EMBRAPA/2025 – Pesquisador)

**Item:** "Deep learning é um tipo de aprendizado de máquina que se baseia no uso de redes neurais de uma única camada."

**Gabarito: Errado (E).**

**Comentário:** Deep learning utiliza redes neurais **multicamadas** (profundas).

### 7.9 (CESPE/CAU-BR/2024 – Analista)

**Item:** "O reconhecimento facial por imagens nas redes sociais é embasado no aprendizado de máquina chamado deep learning, que simula a rede neural do cérebro humano."

**Gabarito: Certo (C).**

**Comentário:** Reconhecimento facial usa **CNNs**, que são arquiteturas de deep learning.

### 7.10 (CESPE/INPI/2024 – Pesquisador)

**Item:** "Quando se dispõe de um conjunto limitado de observações (ex.: imagens de poucos pacientes) para treinar o modelo, é adequado o uso de algoritmos de aprendizado profundo (deep learning)."

**Gabarito: Errado (E).**

**Comentário:** Deep learning requer **grandes volumes** de dados – com poucos dados, o modelo não generaliza bem.

### 7.11 (CESPE/STM/2025 – Analista Judiciário)

**Item:** "No contexto do deep learning, a função das camadas ocultas em uma rede neural profunda é extrair e processar os dados de forma que a rede aprenda características progressivamente mais complexas nas camadas mais profundas."

**Gabarito: Certo (C).**

**Comentário:** É exatamente o princípio do aprendizado hierárquico em redes profundas.

### 7.12 (FGV/PREFEITURA DE MACAÉ/2024 – Analista)

**Item:** "Processo de ajustar os pesos de uma rede neural durante o treinamento, de modo a minimizar a função de perda."

**Gabarito: d) Backpropagation.**

**Comentário:** Backpropagation é o algoritmo que ajusta os pesos propagando o erro de trás para frente.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/ANATEL/2024) | C |
| 02 (CESPE/CNPQ/2024) | E |
| 03 (CESPE/ANTT/2024) | C |
| 04 (CESPE/STM/2025) | C |
| 05 (CESPE/ANM/2025) | C |
| 06 (CESPE/ANM/2025) | E |
| 07 (CESPE/ANTT/2024) | C |
| 08 (CESPE/EMBRAPA/2025) | E |
| 09 (CESPE/CAU-BR/2024) | C |
| 10 (CESPE/INPI/2024) | E |
| 11 (CESPE/STM/2025) | C |
| 12 (FGV/MACAÉ/2024) | d |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Deep Learning** | Subárea do ML com redes neurais profundas (multicamadas). |
| **Rede Neural Profunda** | Camada de entrada → múltiplas camadas ocultas → camada de saída. |
| **CNN** | Rede neural convolucional – usada para imagens. |
| **RNN / LSTM** | Redes recorrentes – usadas para séries temporais e texto. |
| **Transformer** | Arquitetura com mecanismo de atenção – usada em IAs generativas. |
| **Backpropagation** | Algoritmo de treinamento que ajusta os pesos (propaga o erro de trás para frente). |
| **GPU / TPU** | Processadores que aceleram o treinamento de deep learning. |
| **Dados** | Deep learning requer grandes volumes de dados. |

---

*Material complementar à aula "Deep Learning – Introdução" (professor Vitor Kessler/Gran Concursos).*