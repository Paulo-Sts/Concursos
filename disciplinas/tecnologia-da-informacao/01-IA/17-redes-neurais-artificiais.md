# Anotações – Redes Neurais Artificiais

## 1. Conceito de Redes Neurais Artificiais (RNA)

- As **Redes Neurais Artificiais** são modelos computacionais inspirados no funcionamento do **cérebro humano** (redes neurais naturais).
- São compostas por **neurônios artificiais** organizados em camadas:
  - **Camada de entrada:** recebe os dados (X).
  - **Camadas ocultas (hidden layers):** processam as informações.
  - **Camada de saída:** produz o resultado (Y).

> ### 1.1 Paralelo com a rede neural natural
> - **Neurônio natural:** dendritos (entrada) → corpo celular (processamento) → axônio (saída).
> - **Neurônio artificial:** entradas (x) → soma ponderada (Σ x·w) → função de ativação → saída (y).

## 2. Estrutura de um Neurônio Artificial (Perceptron)

### 2.1 Componentes

| COMPONENTE | DESCRIÇÃO |
| --- | --- |
| **Entradas (x₁, x₂, ..., xn)** | Valores recebidos da camada anterior. |
| **Pesos (w₁, w₂, ..., wn)** | Valores multiplicados a cada entrada (ajustados durante o treinamento). |
| **Soma ponderada** | `Σ (xᵢ · wᵢ)` + (opcional) *bias* (viés). |
| **Função de ativação** | Aplica uma transformação não linear à soma ponderada. |
| **Saída (y)** | Resultado do neurônio. |

### 2.2 Bias (Viés)

- O *bias* é um **neurônio adicional** com valor constante (geralmente 1) e peso próprio.
- Permite que a rede aprenda **deslocamentos** e **introduz não linearidade**.

### 2.3 Perceptron Multicamadas (MLP – Multi-Layer Perceptron)

- A arquitetura mais comum de redes neurais é a **MLP**.
- Estrutura: camada de entrada → uma ou mais camadas ocultas → camada de saída.
- É uma rede do tipo **feedforward**: o sinal flui apenas da entrada para a saída (sem ciclos).

## 3. Funções de Ativação

As funções de ativação introduzem **não linearidade** na rede, permitindo que ela aprenda relações complexas. Sem funções de ativação não lineares, múltiplas camadas seriam equivalentes a uma única camada linear.

| FUNÇÃO | DESCRIÇÃO | FAIXA DE SAÍDA | OBSERVAÇÃO |
| --- | --- | --- | --- |
| **Degrau (Limiar)** | 0 se x < 0; 1 se x ≥ 0 | {0, 1} | Função binária, pouco usada atualmente. |
| **Linear** | y = ax + b | Qualquer valor real | Não introduz não linearidade; raramente usada. |
| **Sigmoide (Logística)** | `1 / (1 + e^(-x))` | (0, 1) | Muito usada no passado; saída contínua. |
| **Tangente Hiperbólica (Tanh)** | `(e^x - e^(-x)) / (e^x + e^(-x))` | (-1, 1) | Similar à sigmoide, mas centrada em 0. |
| **ReLU (Rectified Linear Unit)** | max(0, x) | [0, ∞) | Mais usada atualmente (especialmente em CNNs). |
| **Leaky ReLU** | max(αx, x) com α pequeno | (-∞, ∞) | Variação da ReLU para evitar neurônios "mortos". |
| **Softmax** | Normaliza saídas para soma = 1 | (0, 1) [soma = 1] | Usada na camada de saída para classificação multiclasse. |
| **Maxout** | Seleciona o maior valor entre entradas | Varia | Usada na camada de saída. |
| **Gaussiana** | `exp(-(x-c)² / (2σ²))` | (0, 1] | Usada em redes de base radial (RBF). |

> ### 3.1 Sigmoide vs. ReLU
> - **Sigmoide:** saída entre 0 e 1, mas sofre com o problema de *gradiente desaparecendo*.
> - **ReLU:** mais eficiente computacionalmente, evita gradiente desaparecendo, é a mais usada atualmente em redes profundas.

## 4. Treinamento de Redes Neurais – Backpropagation e Gradiente Descendente

### 4.1 Backpropagation (Retropropagação)

- Algoritmo de treinamento de redes neurais.
- **Funcionamento:**
  1. **Fase feedforward:** entrada percorre a rede até a saída (produz uma predição).
  2. **Cálculo do erro:** compara a saída prevista com o valor real (Y do dataset).
  3. **Fase backward (retropropagação):** o erro é "propagado" de volta pela rede.
  4. **Atualização dos pesos:** os pesos são ajustados para reduzir o erro na próxima iteração.

### 4.2 Gradiente Descendente

- Algoritmo de **otimização** que minimiza a função de erro.
- **Funcionamento:** calcula a **derivada parcial** do erro em relação a cada peso e ajusta os pesos na direção que reduz o erro.
- **Fórmula de atualização:**
  - `w_novo = w_antigo - α × ∂Erro/∂w`
- **α (taxa de aprendizado – *learning rate*):**
  - Controla o tamanho dos passos.
  - **Alta:** pode oscilar e não convergir.
  - **Baixa:** treinamento lento.

## 5. Tipos de Redes Neurais

| TIPO | DESCRIÇÃO | APLICAÇÕES |
| --- | --- | --- |
| **Feedforward** | Sinal flui apenas para frente (entrada → saída). | MLP, classificação, regressão. |
| **Recorrente (RNN)** | Possui conexões de volta (ciclos). | Séries temporais, processamento de linguagem natural. |
| **Convolucional (CNN)** | Utiliza camadas de convolução para extrair características espaciais. | Visão computacional, reconhecimento de imagens. |
| **Autoencoder** | Aprende uma representação comprimida dos dados (não supervisionado). | Redução de dimensionalidade, detecção de anomalias. |
| **SOM (Self-Organizing Map)** | Redes neurais não supervisionadas para agrupamento. | Agrupamento de dados, visualização. |

## 6. Redes Neurais e Tipos de Aprendizado

- As redes neurais podem ser usadas nos **três tipos de aprendizado**:

| TIPO DE APRENDIZADO | ARQUITETURAS COMUNS |
| --- | --- |
| **Supervisionado** | MLP, CNN, RNN, LSTM, Transformers. |
| **Não supervisionado** | SOM (Kohonen), Autoencoders. |
| **Por reforço** | Deep Q-Networks (DQN), Policy Gradient, Actor-Critic. |

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/CEBRASPE/2024/INPI – Pesquisador)

**Item:** "Redes neurais artificiais foram inicialmente inspiradas no potencial de ação de células nervosas."

**Gabarito: Certo (C).**

### 7.2 (CESPE/CEBRASPE/2024/CTI – Tecnologista)

**Item:** "As redes neurais permitem construir modelos padronizados de acordo com o funcionamento do cérebro humano."

**Gabarito: Certo (C).**

### 7.3 (FGV/2024/DATAPREV – ATI)

**Item:** "Conceito diretamente relacionado ao desenvolvimento de sistemas que aprendem com os dados e melhoram seu desempenho ao longo do tempo."

**Gabarito: b) Redes Neurais Artificiais.** (na verdade, o conceito é *Machine Learning*, mas redes neurais são uma subárea).

### 7.4 (FGV/2025/AGSUS – Analista)

**Correspondência:**
- Regressão logística → classificação categórica. **(2)**
- Clustering → agrupamento não supervisionado. **(3)**
- Neural networks → nós interligados. **(1)**
- Decision trees → sequência ramificada de decisões. **(4)**

**Gabarito: b) 2 – 3 – 1 – 4.**

### 7.5 (FGV/2025/TCE-RR – Auditor)

**Afirmativas:**
- Árvore de decisão é grafo cíclico? **(F)**
- Redes neurais: neurônios conectados a todos da camada anterior. **(V)**
- SVM usa hiperplano. **(V)**

**Gabarito: d) F – V – V.**

### 7.6 (CESPE/CEBRASPE/2025/ANM – Especialista)

**Item:** "Aumentar significativamente a dimensão da rede neural tem aumento insignificante do esforço computacional."

**Gabarito: Errado (E).**

### 7.7 (CESPE/CEBRASPE/2025/ANM – Feedforward)

**Item:** "Rede neural feedforward se distingue das demais pela presença de camadas ocultas."

**Gabarito: Errado (E).**

**Comentário:** A característica distintiva da feedforward é o **fluxo unidirecional** (entrada → saída), não apenas a presença de camadas ocultas.

### 7.8 (CESPE/CEBRASPE/2025/ANM – Camada de entrada)

**Item:** "Os nós de origem na camada de entrada fornecem os sinais de entrada para os neurônios da primeira camada oculta."

**Gabarito: Errado (E).**

**Comentário:** Os neurônios de entrada **não têm pesos** e apenas repassam os valores.

### 7.9 (FGV/2023/CÂMARA DOS DEPUTADOS – Analista)

**Item:** Função matemática `1/(1+e^(-x))` → **c) Sigmoide.**

### 7.10 (CESPE/CEBRASPE/2025/SUSEP – Analista)

**Item:** "Funções de ativação não lineares são essenciais para que o modelo possa aprender representações complexas."

**Gabarito: Certo (C).**

### 7.11 (CESPE/CEBRASPE/2025/EMBRAPA – Pesquisador)

**Item:** "Funções de ativação do tipo sigmoide são não lineares, suaves e continuamente diferenciáveis."

**Gabarito: Certo (C).**

### 7.12 (CESPE/CEBRASPE/2024/LNA – Tecnologista)

**Item:** "No processo de aprendizado das RNA, pode ser utilizado o paradigma de aprendizado por reforço."

**Gabarito: a)** (as demais alternativas estão incorretas).

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/INPI/2024) | C |
| 02 (CESPE/CTI/2024) | C |
| 03 (FGV/DATAPREV/2024) | b |
| 04 (FGV/AGSUS/2025) | b |
| 05 (FGV/TCE-RR/2025) | d |
| 06 (CESPE/ANM/2025) | E |
| 07 (CESPE/ANM/2025) | E |
| 08 (CESPE/ANM/2025) | E |
| 09 (FGV/CÂMARA/2023) | c |
| 10 (CESPE/SUSEP/2025) | C |
| 11 (CESPE/EMBRAPA/2025) | C |
| 12 (CESPE/LNA/2024) | a |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Rede Neural Artificial** | Modelo inspirado no cérebro, com neurônios e camadas. |
| **Perceptron** | Neurônio artificial com soma ponderada e função de ativação. |
| **Função de ativação** | Introduz não linearidade (sigmoide, ReLU, tanh, etc.). |
| **Backpropagation** | Treinamento que ajusta pesos propagando o erro de trás para frente. |
| **Gradiente Descendente** | Otimização para minimizar o erro (ajusta pesos com derivadas). |
| **Taxa de aprendizado (α)** | Controla a velocidade do treinamento. |
| **Feedforward** | Sinal flui apenas da entrada para a saída. |
| **MLP** | Perceptron multicamadas (a arquitetura mais comum). |

---

*Material complementar à aula "Redes Neurais Artificiais" (professor Vitor Kessler/Gran Concursos).*