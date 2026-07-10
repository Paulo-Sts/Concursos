# Anotações – Visão Computacional

## 1. Conceito de Visão Computacional

- **Visão computacional** é uma área da **Inteligência Artificial** focada na **compreensão e extração de informações de imagens e vídeos**.
- **Objetivo:** replicar as funções da visão humana de forma computacional.
- A máquina percorre cada *frame* de um vídeo (ou cada imagem) em busca de identificar os itens com os quais foi treinada para reconhecer.

> ### 1.1 Diferença entre visão computacional e processamento de imagens
> - **Processamento de imagens:** altera imagens (nitidez, suavização, filtragem, aprimoramento) – foco na melhoria da imagem.
> - **Visão computacional:** classificação, identificação, segmentação e interpretação de imagens e vídeos – foco na extração de significado.

## 2. Aplicações da Visão Computacional

| APLICAÇÃO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Sistemas de auxílio a diagnóstico** | Identificação de padrões em imagens médicas. | IA identifica tumores com assertividade superior à humana. |
| **Aplicações industriais** | Monitoramento de equipamentos por meio de câmeras. | Detecção de fissuras em caldeiras antes que se tornem grandes. |
| **Biometria** | Reconhecimento de características físicas. | Impressão digital, reconhecimento facial, íris. |
| **Identificação e segurança** | Reconhecimento de pessoas e objetos. | Sistemas de vigilância, controle de acesso. |

## 3. Etapas da Visão Computacional

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **1. Formação e aquisição da imagem** | Captura da imagem por meio de câmeras ou sensores. |
| **2. Pré-processamento** | Transformação da imagem em um **vetor numérico** (normalização, redimensionamento, redução de ruído). |
| **3. Segmentação** | Identificação dos objetos de interesse dentro da imagem. |
| **4. Extração de características** | Extração de atributos relevantes (bordas, texturas, formas). |
| **5. Processamento / Classificação** | Interpretação e tomada de decisão com base nas características extraídas. |

> ### 3.1 Processo de reconhecimento
> - O processo de reconhecimento é caracterizado pela **identificação de objetos** – as características de um objeto precisam ser reconhecidas e identificadas.

## 4. Conceitos de Representação de Imagens

- Converter uma imagem em uma **forma numérica** que possa ser processada por um algoritmo.

### 4.1 Imagem em escala de cinza

- Cada pixel é representado por um valor de **intensidade** (brilho) variando entre **0 (preto)** e **255 (branco)**.
- **Exemplo:** 256 níveis de cinza (8 bits).

### 4.2 Imagem colorida (RGB)

- Cada pixel é representado por **três canais de cor** (vermelho, verde, azul – *Red, Green, Blue*).
- Cada canal tem um valor de intensidade (0 a 255).
- **Exemplo:** ao digitalizar uma imagem colorida, originam-se **três matrizes**, uma para cada canal.

### 4.3 Modelo de cores HSV

- Representa cores separando:
  - **Luminosidade (brilho)** .
  - **Cromaticidade (tom e saturação)** .

## 5. Técnicas de Pré-processamento de Imagem

- **Objetivo:** reduzir o tamanho da imagem, simplificar o projeto, melhorar a qualidade da segmentação e facilitar etapas posteriores.

### 5.1 Normalização

- Ajusta os níveis de **brilho e contraste** para destacar características importantes.
- Exemplo: redução de 256 níveis de cinza para 16 ou 2 níveis.

### 5.2 Redimensionamento

- Alteração do tamanho da imagem para:
  - Reduzir a complexidade computacional.
  - Adequar-se a modelos de redes neurais convolucionais (CNNs).
- Exemplo: reduzir resolução de 492×492 para 246×246 ou 62×62 pixels.

### 5.3 Redução de Ruído

- Aplicação de **filtros** para reduzir artefatos indesejados sem perder características importantes.
- **Filtros comuns:** filtro de média, filtro de mediana, *Gaussian Blur*.

### 5.4 Equalização de Histograma

- Técnica que ajusta o **contraste** da imagem, distribuindo uniformemente os valores de intensidade.
- **Histograma:** distribuição de frequências da quantidade de pixels para cada valor possível.
- **Efeito:** distribui os pixels ao longo das possibilidades, tornando o que era cinza escuro em preto e o que estava perto do branco em branco mais puro.

## 6. Questões de Concurso Comentadas

### 6.1 (CESPE/ANTT/2024 – Especialista)

**Item:** "A visão computacional usa algoritmos para alterar imagens, no que diz respeito, por exemplo, a nitidez, suavização, filtragem ou aprimoramento."

**Gabarito: Errado (E).**

**Comentário:** Isso é **processamento de imagens** – visão computacional foca em classificação, identificação e interpretação.

### 6.2 (CESPE/ANTT/2024 – Especialista)

**Item:** "Visão computacional consiste no reconhecimento de imagem (análise de pixel e padrão de imagens), pela identificação de objetos básicos em uma imagem."

**Gabarito: Errado (E).**

**Comentário:** Visão computacional identifica não apenas objetos básicos, mas também **objetos complexos**, como rostos.

### 6.3 (VUNESP/2013/CTA – Tecnologista)

**Item:** "O processo de reconhecimento pode ser caracterizado como:"

**Gabarito: d) a identificação de objetos, ou seja, as características de um objeto precisam ser reconhecidas e identificadas.**

### 6.4 (VUNESP/2013/CTA – Tecnologista)

**Item:** "A imagem colorida, quando digitalizada, origina três matrizes, cada uma armazenando o valor de cada pixel para uma determinada cor."

**Gabarito: b.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/ANTT/2024) | E |
| 02 (CESPE/ANTT/2024) | E |
| 03 (VUNESP/2013) | d |
| 04 (VUNESP/2013) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Visão Computacional** | Extração de informações de imagens/vídeos. |
| **Processamento de Imagens** | Alteração de imagens (nitidez, filtros). |
| **RGB** | 3 canais (vermelho, verde, azul) – 3 matrizes. |
| **Escala de cinza** | 1 canal – valores de 0 (preto) a 255 (branco). |
| **HSV** | Matiz, saturação, valor (brilho). |
| **Pré-processamento** | Normalização, redimensionamento, redução de ruído, equalização de histograma. |
| **Etapas** | Aquisição → Pré-processamento → Segmentação → Extração → Classificação. |

---

*Material complementar à aula "Visão Computacional" (professor Vitor Kessler/Gran Concursos).*