# Introdução à Deep Learning

## 1. Definição e Contexto do Deep Learning
- Deep learning é uma área do machine learning na qual o algoritmo/modelo utilizado são redes neurais multicamadas.
- O deep learning foi a área responsável por revolucionar a inteligência artificial, com aplicações em diversas frentes.
- Relação hierárquica entre os conceitos:
  - Inteligência artificial = desenvolver sistemas inteligentes;
  - Machine learning = desenvolver sistemas que aprendem;
  - Deep learning = desenvolver sistemas que aprendem e que usam redes neurais artificiais multicamadas.

### 1.1 Exemplos de Aplicações de Deep Learning
- O transformer, que é uma rede neural profunda utilizada nas IAs generativas de texto;
- O stable diffusion, que é uma rede neural utilizada para geração de imagens;
- Convolutional neural network (CNN), que são utilizadas para a classificação de imagens.

### 1.2 Para que Usar o Deep Learning
- Processamento de imagens com a CNN;
- Realização de análises e séries históricas com redes neurais recorrentes (RNN);
- Nas IAs generativas.

> [!TIP] DICAS: 
> - O deep learning é uma subárea do machine learning, e não um conceito isolado. Essa hierarquia costuma ser cobrada em provas.
> - A CNN é a rede neural mais cobrada para classificação e processamento de imagens.
> - O transformer é a base das IAs generativas de texto, como o ChatGPT.

> [!CAUTION] OBSERVAÇÃO: 
> - Deep learning não se resume apenas a redes neurais com muitas camadas; é o conjunto de técnicas que utiliza redes neurais profundas para aprendizado de representações complexas.

## 2. Estrutura das Redes Neurais Artificiais
- As redes neurais artificiais são compostas por:
  - Camada de entrada;
  - Uma ou mais camadas ocultas (intermediárias);
  - Camada de saída.
- Se a rede neural possuir muitas camadas intermediárias, trata-se de deep learning.
- O número de neurônios (nós) pode variar de uma camada para outra.

### 2.1 Funcionamento de um Neurônio Artificial
- Um neurônio recebe entradas de dados, que vêm de uma camada anterior ou da própria camada de entrada.
- As entradas são multiplicadas pelos pesos, que são as conexões entre os neurônios.
- Todas as redes implementam o viés (bias), um dado aleatório que também é multiplicado por um peso.
- O cálculo interno do neurônio é o somatório de:
  - Entradas (E) × pesos (W) + bias (B) × peso do bias (Wb).
- Uma função de ativação dentro do neurônio processa esse somatório e resulta em uma saída.
- A saída do neurônio serve como entrada para a próxima camada de neurônios.

### 2.2 Arquiteturas de Redes Neurais Mais Cobradas
- Long short-term memory (LSTM);
- Redes neurais recorrentes (RNN);
- Redes neurais convolucionais (CNN);
- Redes neurais da IA generativa.

> [!TIP] DICAS: 
> - Em redes neurais profundas, as camadas mais profundas aprendem características progressivamente mais complexas.
> - Exemplo prático: em uma CNN, as primeiras camadas identificam elementos mais superficiais (linhas, bordas, rostos), enquanto as camadas mais profundas identificam detalhes específicos (olhos, narizes, bocas, sorrisos).

> [!CAUTION] OBSERVAÇÃO: 
> - A afirmação sobre extração de características complexas em camadas mais profundas é verdadeira para CNNs, mas não se aplica da mesma forma a redes como a LSTM, que trabalha com sequências temporais e portões de memória.

## 3. Processadores Específicos para Deep Learning
- O uso de GPUs e TPUs acelera os cálculos necessários para operações matriciais e retropropagação em modelos de deep learning.

### 3.1 GPU (Graphics Processing Unit)
- É um processador iterativo que acompanha placas gráficas.
- O treinamento de redes neurais e algoritmos de machine learning é iterativo, e as GPUs são otimizadas para esse tipo de processamento paralelo.

### 3.2 TPU (Tensor Processing Unit)
- É um processador lançado pelo Google, específico para treinamento de inteligência artificial.

### 3.3 NPU (Neural Processing Unit)
- É um processador menor, voltado para dispositivos como internet das coisas e celulares, focado em processamento de IA.

> [!CAUTION] OBSERVAÇÃO: 
> - Deep learning não elimina completamente a necessidade de pré-processamento de dados. Todo processo de IA envolve as etapas de coleta de dados, pré-processamento, criação do dataset, treinamento, validação e implantação. O examinador do CESPE já considerou essa afirmativa como errada.

## 4. Algoritmo de Treinamento: Backpropagation
- O backpropagation é o algoritmo de treinamento das redes neurais.
- Consiste em:
  - Etapa de propagação para frente (forward propagation);
  - Etapa de ajuste de pesos de toda a rede para minimizar a função de perda.

> [!TIP] DICAS: 
> - Backpropagation é o processo de ajustar os pesos de uma rede neural durante o treinamento para minimizar a função de perda. Esse conceito é frequentemente cobrado em provas.
> - A propagação para frente (forward propagation) é apenas uma etapa do processo; o ajuste efetivo ocorre com a retropropagação.

## 5. Conceitos Fundamentais

### 5.1 Deep Learning e Dados Não Estruturados
- Deep learning é um tipo de aprendizado de máquina que usa redes neurais artificiais para permitir que sistemas digitais aprendam e tomem decisões com base em dados.
- O examinador do CESPE considera que o incompleto não é errado, ou seja, afirmativas que não mencionam todos os detalhes, mas que estão corretas no geral, podem ser consideradas certas.

### 5.2 Relação entre Deep Learning e Cérebro Humano
- Deep learning não é um algoritmo genético. O algoritmo genético trabalha com populações de soluções que cruzam entre si e são selecionadas.
- Redes neurais de deep learning tentam imitar o cérebro humano por meio de uma combinação de entradas de dados, pesos e viés, que trabalham juntos para reconhecer, classificar e descrever objetos dentro dos dados.

### 5.3 Deep Learning e Dados Rotulados
- Deep learning não se restringe apenas a dados não rotulados. Ele pode ser usado tanto com dados supervisionados (rotulados) quanto não supervisionados (não rotulados).

### 5.4 Quantidade de Dados Necessária
- Deep learning pressupõe uma quantidade gigantesca de dados para que a máquina consiga aprender adequadamente.
- Para conjuntos limitados de observações, o uso de deep learning não é o mais adequado.

> [!CAUTION] OBSERVAÇÃO: 
> - Deep learning NÃO elimina a necessidade de pré-processamento de dados. Essa é uma pegadinha comum em provas.
> - Deep learning NÃO é uma rede neural de uma única camada. Pelo contrário, é caracterizado por redes neurais com muitas camadas (multicamadas).