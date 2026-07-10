# Anotações – Visão Computacional II

## 1. OCR (Optical Character Recognition)

- **OCR (Reconhecimento Óptico de Caracteres):** técnica usada para extrair texto de imagens ou documentos digitalizados.

### 1.1 Etapas principais do OCR

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **Segmentação** | Separação das regiões de texto da imagem das regiões não textuais. |
| **Reconhecimento de caracteres** | Uso de técnicas de classificação para identificar letras, números e símbolos a partir das regiões segmentadas. |
| **Pós-processamento** | Correção de erros no reconhecimento de caracteres, usando dicionários ou regras gramaticais para aumentar a precisão. |

## 2. Segmentação de Imagens

- **Segmentação:** processo de dividir a imagem em partes ou regiões com base em características como cor, textura, bordas ou similaridade de intensidade.

### 2.1 Técnicas de Segmentação

| TÉCNICA | DESCRIÇÃO |
| --- | --- |
| **Thresholding (Limiarização)** | Divisão da imagem em regiões com base em um valor de limiar de intensidade (ex.: binarização – preto e branco). Pode ter 2 a 4 níveis de intensidade. |
| **Segmentação baseada em regiões** | Agrupamento de pixels vizinhos com características semelhantes. |
| **Segmentação baseada em clusterização** | Agrupamento de pixels com base em aprendizado não supervisionado (ex.: K-means). |
| **Watershed** | Técnica que vê a imagem como um relevo topográfico: os **vales** correspondem a objetos e os **picos** são os limites entre eles. |

> ### 2.1.1 Definição (questão CESPE)
> - **Segmentação** corresponde ao **particionamento de regiões** na imagem que tenham significados específicos para determinada aplicação.

## 3. Etapas Básicas da Visão Computacional

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **Aquisição da imagem** | Captura da imagem por meio de câmeras ou sensores. |
| **Processamento da imagem** | Pré-processamento, extração de características. |
| **Segmentação da imagem** | Divisão da imagem em regiões de interesse. |

> ### 3.1 Observação (questão FGV)
> - Algumas bancas consideram que as **etapas básicas** são apenas **aquisição e processamento**, mas a **segmentação** também é fundamental.

## 4. Redes Neurais Convolucionais (CNNs) – Visão Geral

| COMPONENTE | FUNÇÃO |
| --- | --- |
| **Camada de convolução** | Aplica **filtros** à imagem para extrair características (bordas, texturas, formas). Cada camada se especializa em um tipo de padrão. |
| **Filtro (kernel)** | Tamanho do bloco de pixels que percorre a imagem. |
| **Passo (stride)** | Quantos pixels o filtro percorre para a direita/baixo a cada movimento. |
| **Camada de pooling** | Reduz a dimensionalidade (subamostragem) dos mapas de características. |
| **Camada totalmente conectada (Flatten + Dense)** | Achata as informações extraídas e as conecta a uma rede neural para classificação final. |
| **Função de ativação ReLU** | Transforma em zero os resultados negativos, mantendo os outros valores. |
| **Função Softmax** | Na camada de saída, pega a saída de todos os neurônios e escolhe a de maior valor (classificação). |

> ### 4.1 ReLU (Rectified Linear Unit)
> - **Definição:** `f(x) = max(0, x)`
> - Se `x < 0`, saída = 0.
> - Se `x ≥ 0`, saída = x (mantém o valor).
> - **Propriedade principal:** transforma em zero os resultados negativos, mantendo os outros valores.

## 5. Técnicas de Visão Computacional

| TÉCNICA | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Estimativa de Pose (Pose Estimation)** | Identifica a posição e orientação de um objeto ou corpo humano. | Análise de movimentos em reabilitação física. |
| **Detecção de Objeto (Object Detection)** | Identifica e localiza objetos em uma imagem. | "Onde está a zebra?" |
| **Reconhecimento de Atividade (Activity Recognition)** | Identifica o tipo de ação realizada em uma sequência de vídeos. | "O indivíduo está nadando." |
| **Structure from Motion (SfM)** | Reconstrói a forma tridimensional a partir de imagens bidimensionais. | Modelagem 3D. |
| **SLAM (Localização e Mapeamento Simultâneos)** | Robô/dispositivo constrói um mapa do ambiente enquanto estima sua posição. | Robô aspirador, carros autônomos. |

## 6. Viés e Desbalanceamento de Dados em Visão Computacional

- **Exemplo (questão FGV):** modelo treinado para identificar uso de capacete classificava erroneamente um chefe calvo como "com capacete".
- **Causa mais provável:** o conjunto de dados de treinamento **não tinha uma quantidade balanceada de pessoas calvas sem utilizar o capacete**, fazendo o modelo associar erroneamente a calvície com o uso de capacete.

## 7. Questões de Concurso Comentadas

### 7.1 (CESPE/CTI/2024 – Tecnologista)

**Item:** "Segmentação corresponde ao particionamento de regiões na imagem que tenham significados específicos para determinada aplicação."

**Gabarito: Certo (C).**

### 7.2 (FGV/PREFEITURA DE SÃO JOSÉ DOS CAMPOS/2024 – Analista)

**Item:** "Etapas básicas da visão computacional: aquisição, processamento e segmentação."

**Gabarito: c) I e II, apenas.** (a banca considerou que segmentação não é etapa básica, mas sim parte do processamento).

### 7.3 (FGV/MF/2024 – Auditor)

**Item:** "Técnica para capturar e analisar movimentos do corpo humano, identificando posições e partes específicas do corpo."

**Gabarito: a) Estimativa de Pose (Pose Estimation).**

### 7.4 (CESGRANRIO/CNU/2024 – Tecnologia)

**Item:** "Propriedade principal da função ReLU."

**Gabarito: e) transformar em zero os resultados negativos, mantendo os outros valores.**

### 7.5 (CESPE/ANTT/2024 – Especialista)

**Item:** "No treinamento, as redes neurais convolucionais recebem imagens e aplicam filtros, que possibilitam a extração de características; após essa extração, a camada de rede neural é utilizada para classificar a imagem."

**Gabarito: Certo (C).**

### 7.6 (CESPE/CTI/2024 – Tecnologista)

**Item:** "Filtros convolucionais não podem ser utilizados, por exemplo, na detecção de bordas na imagem."

**Gabarito: Errado (E).**

**Comentário:** Filtros convolucionais são **amplamente utilizados** para detecção de bordas.

### 7.7 (FGV/CÂMARA DOS DEPUTADOS/2023 – Analista)

**Item:** "Causa mais provável do modelo identificar chefe calvo como estando de capacete."

**Gabarito: d) O conjunto de dados de treinamento não tinha uma quantidade balanceada de pessoas calvas sem utilizar o capacete, fazendo o modelo associar erroneamente a calvície com o uso de capacete.**

### 7.8 (FGV/RECEITA FEDERAL/2023 – Auditor)

**Itens sobre detecção de câncer de pele:**

- I – Sensibilidade (Recall) é a métrica mais importante para minimizar falsos negativos. **(V)**
- II – Precisão não é a mais importante neste caso. **(F)**
- III – Minimizar FN geralmente aumenta FP. **(V)**
- IV – Treinamento mais longo pode causar overfitting. **(F)**

**Gabarito: a) I e III, apenas.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/CTI/2024) | C |
| 02 (FGV/SÃO JOSÉ/2024) | c |
| 03 (FGV/MF/2024) | a |
| 04 (CESGRANRIO/CNU/2024) | e |
| 05 (CESPE/ANTT/2024) | C |
| 06 (CESPE/CTI/2024) | E |
| 07 (FGV/CÂMARA/2023) | d |
| 08 (FGV/RECEITA/2023) | a |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **OCR** | Extrai texto de imagens. |
| **Segmentação** | Divide imagem em regiões de interesse. |
| **Thresholding** | Binarização por limiar de intensidade. |
| **Watershed** | Relevo topográfico – vales = objetos, picos = limites. |
| **ReLU** | `f(x)=max(0,x)` – zera negativos, mantém positivos. |
| **Pose Estimation** | Identifica posição/orientação de corpo/objeto. |
| **Object Detection** | Localiza objetos na imagem. |
| **Activity Recognition** | Identifica ações em vídeos. |
| **SLAM** | Mapeia ambiente e localiza robô simultaneamente. |

---

*Material complementar à aula "Visão Computacional II" (professor Vitor Kessler/Gran Concursos).*