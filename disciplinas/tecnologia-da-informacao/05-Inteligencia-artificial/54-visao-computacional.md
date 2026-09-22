# Visão Computacional

## 1. Introdução
- A visão computacional replica as funções da visão humana.
- Trata-se de uma área da inteligência artificial focada na compreensão e extração de informações de imagens e vídeos.
- Exemplo: a máquina percorre todo o frame do vídeo em busca de identificar os itens com os quais foi treinada para reconhecer.

## 2. Aplicações
- Sistemas de Auxílio a Diagnóstico:
  - Exemplo: a máquina tem uma assertividade maior do que o médico humano para identificar tumores.
- Aplicações Industriais:
  - Exemplo: considera-se uma caldeira, em uma indústria, que precisa passar por manutenção a cada 6 meses, aproximadamente, de acordo com o aparecimento de fissuras. Para saber quando está no momento exato de fazer a manutenção, coloca-se uma câmera em cima da caldeira que gerará um alerta ao detectar pequenas fissuras antes que elas se tornem grandes fissuras.
- Biometria.
- Identificação e Segurança.

## 3. Etapas
- Formação e Aquisição da imagem.
- Pré-Processamento: transformar a imagem em um vetor numérico.
- Segmentação: identificar os objetos de interesse dentro da imagem.
- Extração de Características.
- Processamento.

> [!TIP] DICAS:
> - O processo de reconhecimento é caracterizado pela identificação de objetos, ou seja, as características de um objeto precisam ser reconhecidas e identificadas.
> - A obtenção das imagens visa registrar o ambiente em que o robô está inserido e é feita por meio de câmeras.

## 4. Conceitos de Representação de Imagens
- Converter uma imagem em uma forma numérica que possa ser processada por um algoritmo.

### 4.1 Imagem em Escala de Cinza
- Cada pixel da imagem é representado por um valor de intensidade, variando entre 0 (preto) e 255 (branco).

### 4.2 Imagem Colorida (RGB)
- Cada pixel é representado por três canais de cor (vermelho, verde e azul), cada um com um valor de intensidade.

### 4.3 Representação em Nível de Pixels
- Cada pixel da imagem contém informações sobre suas características (cor, intensidade, textura) que podem ser analisadas por algoritmos de processamento.

### 4.4 Modelos de Cores (HSV)
- Representam cores de maneira diferente, separando os componentes de luminosidade (brilho) e cromaticidade (tom e saturação).

> [!CAUTION] OBSERVAÇÃO:
> - É possível transformar uma imagem colorida em uma imagem em tons de cinza quando se quer deixar o dataset mais leve, mas isso faz com que informações se percam.
> - A imagem colorida digitalizada origina três matrizes.

## 5. Técnicas de Pré-Processamento de Imagem
- É preciso pré-processar a imagem antes de gerar a matriz, para diminuir o tamanho da imagem, simplificar o projeto, melhorar a qualidade da segmentação, facilitando as etapas posteriores.

### 5.1 Transformações na Imagem Original
- Melhorar qualidade.
- Facilitar etapas posteriores de análise e de processamento.

### 5.2 Normalização
- Ajusta os níveis de brilho e contraste de uma imagem para garantir que as características importantes sejam destacadas.

### 5.3 Redimensionamento
- Alteração do tamanho da imagem para reduzir a complexidade computacional ou se adequar a modelos de redes neurais convolucionais (CNN).

### 5.4 Redução de Ruído
- Aplicação de filtros (como filtro de média, filtro de mediana ou Gaussian Blur) para reduzir artefatos indesejados ou ruído sem perder as características importantes.

### 5.5 Equalização de Histograma
- Técnica que ajusta o contraste de uma imagem, distribuindo uniformemente os valores de intensidade, para melhorar a visibilidade dos detalhes.
- O histograma demonstra uma distribuição de frequências da quantidade de pixels para cada valor possível que cada pixel pode assumir.
- Ao aplicar a equalização de histograma, faz-se a distribuição de pixels ao longo das possibilidades, tornando o que é cinza escuro em preto, e o que está perto do branco torna-se mais branco.

## 6. Tabela de Níveis de Cinza
| TIPO DE IMAGEM | NÍVEIS DE CINZA |
|----------------|-----------------|
| Imagem com 256 níveis de cinza | 256 |
| Imagem com 16 níveis de cinza | 16 |
| Imagem com 2 níveis de cinza | 2 |

## 7. Tabela de Resolução de Imagem
| TIPO DE RESOLUÇÃO | DIMENSÃO |
|-------------------|----------|
| Alta resolução | 492px x 492px |
| Média resolução | 246px x 246px |
| Baixa resolução | 62px x 62px |

> [!TIP] DICAS:
> - A visão computacional consiste na classificação, identificação e segmentação de imagens e vídeos.
> - A visão computacional consegue fazer a identificação não só de objetos básicos como também de objetos complexos, como rostos.
> - A visão computacional usa algoritmos para processar imagens, não para alterá-las em aspectos como nitidez, suavização, filtragem ou aprimoramento.