# Redes Neurais Convolucionais

## 1. Conceitos Fundamentais
- Rede neural profunda mais cobrada em concursos, especialmente voltada para classificação de imagens e vídeos.
- Diferencia-se das demais redes por sua arquitetura especializada em extrair características visuais.
- Exemplo prático: TCU utilizou CNNs para auditar cisternas no Nordeste, comparando imagens de satélite históricas e atuais para identificar locais sem cisterna, otimizando o trabalho dos auditores.

### 1.1 Processamento de Imagens
- A imagem é percorrida em "pedaços" (conjuntos de pixels) durante o processamento.
- Na visão computacional, existem dois problemas principais:
  - Segmentação: a CNN separa os pixels mais importantes da imagem;
  - Extração de características: a rede considera apenas os pedaços importantes e extrai as características que representam a imagem.

### 1.2 Estrutura da Rede
- A imagem passa por camadas de convolução, que extraem características.
- O dado entra na camada de convolução e passa por pooling para reduzir a dimensionalidade.
- Ao final, os dados chegam ao "flatten layer" (camada achatada), onde todas as informações são convertidas em um vetor.
- Esse vetor entra em uma rede neural totalmente conectada (rede neural normal).
- Na camada de saída, cada neurônio representa uma classe (ex: pessoa, arma, animal).
- O maior valor entre os neurônios da camada de saída determina a classificação final da rede.

> [!TIP] DICAS: 
> - A CNN é a rede mais cobrada em provas para tarefas com imagens e vídeos.
> - O flatten layer é o ponto de transição entre a parte convolucional e a rede totalmente conectada.

## 2. Camadas da Rede Neural Convolucional
- As CNNs possuem três tipos principais de camadas: convolucional, de agrupamento (pooling) e totalmente conectada.

### 2.1 Camada de Convolução
- Responsável por extrair características da imagem através da aplicação de filtros (kernels).
- Quanto mais interna a camada na rede, mais específica ela se torna para identificar padrões.
- Hierarquia de extração:
  - Camadas iniciais: identificam características de baixo nível (linhas, bordas, círculos, pontos);
  - Camadas intermediárias: organizam padrões em texturas e estruturas simples (triângulos, manchas);
  - Camadas profundas: reconhecem características de alto nível (partes de objetos, detalhes específicos);
  - Últimas camadas: combinam os elementos para identificar objetos completos (ex: planta, fruto, animal).

### 2.2 Camada de Pooling (Agrupamento)
- Tem como função reduzir a quantidade de dados que passam entre as camadas.
- Diminui a dimensionalidade da rede, reduzindo carga computacional, uso de memória e número de parâmetros.
- Não tem relação com aumento da dimensionalidade.
- A subamostragem (redução de dados) ocorre nesta camada, não na camada convolucional.

### 2.3 Camada Totalmente Conectada
- Recebe os dados achatados do flatten layer.
- Realiza a classificação final da imagem.
- Utiliza função de ativação (como ReLU) nas camadas convolucionais.

### 2.4 Função de Ativação ReLU
- É utilizada nas camadas de convolução.
- Introduz não-linearidade à rede, permitindo aprender padrões complexos.

### 2.5 Hiperparâmetros Importantes
- Stride: distância entre os fragmentos (pulos) durante a aplicação do filtro.
- Dilation: aumenta o tamanho do mapa de ativação sem aumentar a quantidade de pixels.
- A dimensão do mapa de ativação depende de hiperparâmetros como stride e dilation.

> [!CAUTION] OBSERVAÇÃO: 
> - As primeiras camadas acham características simples (linhas, círculos, pontos); as camadas mais profundas identificam detalhes específicos. É o oposto do que muitos imaginam.
> - A camada de pooling NUNCA aumenta a dimensionalidade; ela sempre REDUZ a quantidade de informação.

## 3. Aplicações e Características Específicas
- CNNs são projetadas para processar dados com estrutura espacial (imagens e vídeos).
- Não são adequadas para dados sequenciais como texto, áudio ou séries temporais - essas tarefas são para Redes Neurais Recorrentes (RNNs).
- Podem ser usadas tanto para classificação (atribuir rótulos a imagens inteiras) quanto para segmentação (identificar regiões específicas e fornecer mapa pixel a pixel).
- A posição espacial das informações deve ser preservada durante o processo de convolução.

### 3.1 Exemplos de Arquiteturas CNN
- LeNet-5.
- AlexNet.
- ResNet.

### 3.2 Transferência de Aprendizado (Transfer Learning)
- Consiste em iniciar o treinamento com um modelo pré-treinado em dados genéricos.
- O treinamento não começa do zero, aproveitando o conhecimento já adquirido.
- Para ajuste fino, atualiza-se todos os parâmetros do modelo para a nova tarefa.
- É necessário manter a coerência com o formato e tipo de dados da nova tarefa.

### 3.3 Aplicações Práticas
- Detecção de doenças em plantas (identificação de padrões complexos em imagens).
- Mapeamento de uso e cobertura da terra.
- Monitoramento de saúde florestal (identificação e classificação de árvores em tempo real).
- Bioinformática (processamento de sequências genômicas).
- Visão computacional em geral.

> [!TIP] DICAS: 
> - Se a questão mencionar "dados sequenciais", "texto", "áudio" ou "séries temporais", a resposta provavelmente é REDE RECORRENTE, não CNN.
> - Questões de concurso adoram confundir CNN com RNN - fique atento a essa pegadinha!

## 4. Pontos-Chave para Revisão
- CNNs são para IMAGENS E VÍDEOS, não para dados sequenciais.
- Possuem três camadas principais: convolução, pooling e totalmente conectada.
- O ReLU é usado na convolução.
- O pooling REDUZ dimensionalidade.
- As primeiras camadas detectam características simples; as profundas detectam características complexas.
- Transfer learning inicia de um modelo pré-treinado.
- Stride e dilation são hiperparâmetros importantes.