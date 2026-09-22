# Visão Computacional 2

## 1. Processo de Identificação de Imagens
- O processo para que a máquina comece a identificar imagens passa por um pré-processamento, onde a imagem é organizada e trabalhada para facilitar as etapas subsequentes.
- Quando a imagem contém texto, é necessário realizar a extração desse texto.

## 2. OCR (Optical Character Recognition)
- Técnica utilizada para extrair texto de imagens ou documentos digitalizados.

### 2.1 Etapas Principais do OCR
- Segmentação: Separação das regiões de texto da imagem das regiões não textuais.
- Reconhecimento de caracteres: Uso de técnicas de classificação para identificar letras, números e símbolos a partir das regiões segmentadas.
- Pós-processamento: Correção de erros no reconhecimento de caracteres, como o uso de dicionários ou regras gramaticais para aumentar a precisão.

## 3. Segmentação
- Processo de dividir a imagem em partes ou regiões com base em características como cor, textura, bordas ou similaridade de intensidade.
- Corresponde ao particionamento de regiões na imagem que tenham significados específicos para determinada aplicação.

### 3.1 Técnicas de Segmentação
- Thresholding: Divisão da imagem em regiões com base em um valor de limiar de intensidade (exemplo: binarização de imagens). É possível ter até 3 a 4 níveis de intensidade.
- Segmentação baseada em regiões: Agrupamento de pixels vizinhos com características semelhantes.
- Segmentação baseada em clusterização: Agrupamento de pixels vizinhos com base em aprendizado não supervisionado.
- Watershed: Técnica que vê a imagem como um relevo topográfico, onde os vales correspondem a objetos e os picos são os limites.

> [!TIP] DICAS: 
> - A segmentação é uma etapa fundamental no processamento de imagens, pois permite isolar os elementos de interesse para análise posterior.
> - Embora algumas bancas considerem apenas aquisição e processamento como etapas básicas, a segmentação também pode ser considerada uma etapa básica pela sua importância no processo.

## 4. Etapas Básicas da Visão Computacional
- Aquisição da imagem.
- Processamento da imagem.
- Segmentação da imagem.

## 5. Redes Neurais Convolucionais (CNN)
- As redes neurais convolucionais recebem imagens e aplicam filtros, que possibilitam a extração de características.
- Após a extração, a camada de rede neural é utilizada para classificar a imagem.

### 5.1 Componentes das CNNs
- Filtro: Tamanho de pixel que será a entrada da imagem.
- Passo (Stride): Quantos pixels são percorridos para a direita desse filtro.
- Cada camada da convolução será especialista em algum aspecto da imagem.
- O processo é repetido para cada pedaço da imagem.

### 5.2 Camada de Pooling
- Ao juntar as camadas de convolução, há uma camada de pooling que realiza a diminuição dos padrões.
- A camada final de pooling traz informações específicas que auxiliam na identificação da imagem, que se torna uma entrada para uma rede neural.

### 5.3 Classificação e Saída
- A saída da rede neural é a classificação da imagem.
- A função de ativação SoftMax pega a saída de todos os neurônios da camada e escolhe a de maior saída.

> [!CAUTION] OBSERVAÇÃO: 
> - Filtros convolucionais podem ser utilizados, por exemplo, na detecção de bordas na imagem de uma câmera de um sistema detector de embalagens. Portanto, a afirmação de que não podem ser utilizados para essa finalidade está incorreta.

## 6. Técnicas de Visão Computacional

### 6.1 Estimativa de Pose (Pose Estimation)
- Identifica a posição e orientação de um objeto ou de um corpo humano em uma imagem ou vídeo.
- Utilizada para capturar e analisar movimentos do corpo humano, avaliando a execução correta de exercícios e sugerindo ajustes.

### 6.2 Detecção de Objeto (Object Detection)
- Identifica objetos dentro de uma imagem.
- Exemplo: "Onde está a zebra?"

### 6.3 Reconhecimento de Atividade (Activity Recognition)
- Identifica o tipo de ação realizada por uma pessoa em uma sequência de vídeos.
- Exemplo: "O indivíduo está nadando."

### 6.4 Structure from Motion (SfM)
- Permite reconstruir a forma tridimensional a partir de imagens bidimensionais.

### 6.5 Localização e Mapeamento Simultâneos (SLAM)
- Um robô ou dispositivo constrói um mapa do ambiente enquanto estima a posição aproximada.
- Exemplo: robô aspirador de pó.

## 7. Funções de Ativação

### 7.1 ReLU (Rectified Linear Unit)
- Propriedade principal: transforma em zero os resultados negativos, mantendo os outros valores.
- Se o valor de x for menor que zero, a saída será zero.
- Se o valor de x for maior que zero, a saída será o mesmo valor de x.

### 7.2 SoftMax
- Pega a saída de todos os neurônios da camada e escolhe a de maior saída.
- Utilizada na camada de saída para classificação.

## 8. Métricas de Avaliação

### 8.1 Sensibilidade (Recall ou Revocação)
- Métrica que indica a capacidade do modelo de identificar corretamente os casos positivos.
- Fórmula: R = VP / (VP + FN)
- Quando a máquina não tem falso negativo, o recall assume o valor máximo (1).
- Quando tem muitos falsos negativos, o recall diminui.

### 8.2 Precisão (Precision)
- Métrica que indica a proporção de previsões positivas que estavam corretas.
- Fórmula: P = VP / (VP + FP)
- Indica quanto a máquina produz de falso positivo.

> [!CAUTION] OBSERVAÇÃO: 
> - Em diagnósticos médicos auxiliados por IA, os erros de tipo 1 (falso positivo) são mais tolerados, pois há análise posterior por um médico especialista.
> - Os erros de tipo 2 (falso negativo) são os mais críticos, pois podem resultar em diagnóstico tardio ou falho, comprometendo a saúde do paciente.
> - Ao ajustar o modelo para minimizar erros de tipo 2, geralmente os erros de tipo 1 tendem a aumentar. Isso ocorre porque quando a máquina é ajustada para não deixar passar falso negativo, aumenta a possibilidade de falso positivo.

## 9. Possíveis Causas de Comportamento Anômalo em Modelos de Visão Computacional
- Conjunto de dados desbalanceado, com muito mais exemplos de uma classe do que de outra.
- Características únicas não aprendidas corretamente durante o treinamento.
- Overfitting (superajuste): o modelo captura detalhes muito específicos do conjunto de treinamento que não generalizam bem para dados não vistos.
- Falta de balanceamento de características específicas no conjunto de dados de treinamento.
- Diferença significativa na resolução da câmera utilizada durante a demonstração em comparação com a usada para coletar imagens do conjunto de dados de treinamento.