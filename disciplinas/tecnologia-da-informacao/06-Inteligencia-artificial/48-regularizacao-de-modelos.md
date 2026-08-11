# Regularização de Modelos

## 1. Introdução à Regularização
- A regularização é uma técnica que visa reduzir o overfitting e melhorar a capacidade de generalização dos modelos para dados novos.
- O objetivo é ajustar o modelo aos dados de forma a torná-lo menos complexo e menos especializado, evitando que ele decore os dados de treinamento, incluindo ruídos e erros.
- A regularização traz o modelo para a realidade dos dados que ele deve aprender, evitando que se torne sofisticado demais a ponto de se ajustar apenas ao conjunto de treinamento.

### 1.1 Overfitting (Sobreajuste)
- O overfitting ocorre quando a máquina se torna excessivamente especializada no conjunto de treinamento, perdendo a capacidade de generalizar para dados nunca vistos.
- Esse fenômeno acontece quando a máquina é treinada em excesso, levando-a a "decorar" os dados de treinamento, incluindo ruídos e erros presentes nesse conjunto.
- O overfitting também é conhecido como overtraining.
- Para combater o overfitting, recomenda-se utilizar uma máquina menos complexa:
  - Rede neural com menos neurônios;
  - Árvore de decisão com profundidade reduzida.
- O overfitting pode ser identificado quando o erro no conjunto de testes começa a aumentar após um determinado ponto, mesmo que o erro no treinamento continue diminuindo.

> [!TIP] DICAS:
> - Overfitting é o oposto de generalização; quanto mais específico o modelo fica para os dados de treino, pior ele performa em dados novos.
> - A solução para o overfitting é reduzir a complexidade do modelo, ou seja, "diminuir a inteligência" da máquina.

### 1.2 Underfitting
- Embora não seja o foco principal do material, o underfitting ocorre quando o modelo é extremamente simples e não consegue aprender padrões relevantes dos dados de treinamento.
- É o oposto do overfitting: o modelo não se ajusta bem nem aos dados de treino.

## 2. Validação Cruzada (Cross-Validation)
- A validação cruzada é uma técnica utilizada para avaliar a performance de modelos de aprendizado de máquina e mitigar o overfitting.
- O processo consiste em dividir o dataset em k subconjuntos (folds) de tamanhos aproximadamente iguais.
- O modelo é treinado k vezes, utilizando k-1 subconjuntos para treinamento e 1 subconjunto para teste, variando o subconjunto de teste a cada iteração.
- A acurácia final do modelo é calculada pela média das métricas de performance obtidas em cada iteração.

### 2.1 Funcionamento da Validação Cruzada com k=3
- Exemplo prático com k=3:
  - Modelo 1 (M1): subconjuntos 1 e 2 para treinamento; subconjunto 3 para teste.
  - Modelo 2 (M2): subconjuntos 1 e 3 para treinamento; subconjunto 2 para teste.
  - Modelo 3 (M3): subconjuntos 2 e 3 para treinamento; subconjunto 1 para teste.
- Os três modelos são treinados com dados diferentes, variando o conjunto de teste sem repetição.
- Mesmo que um dos modelos entre em overfitting, os outros dois não necessariamente apresentarão o mesmo problema.
- O resultado final pode ser obtido por:
  - Média das métricas (para regressão);
  - Votação (para classificação).

### 2.2 Comparação com Holdout
- Holdout: divisão simples do dataset em duas partes, geralmente 70% para treinamento e 30% para teste.
- Validação cruzada: divisão em k partes, com treinamento e teste iterativos, proporcionando uma estimativa mais confiável da performance do modelo.

> [!CAUTION] OBSERVAÇÃO:
> - A validação cruzada K-fold é um dos métodos que podem ser utilizados para detectar e ajustar a ocorrência de overfitting.
> - É uma estratégia amplamente utilizada na regularização de modelos e frequentemente cobrada em concursos.

## 3. Lasso Regression (Regularização L1)
- A Lasso Regression é um modelo de regularização utilizado em problemas de regressão.
- Adiciona uma penalidade à função de custo baseada na soma dos valores absolutos dos coeficientes (βi).
- A penalidade pode reduzir alguns coeficientes exatamente a zero, promovendo a seleção de variáveis.
- A função de custo é dada por:
  - Custo = Erro Quadrático Médio (MSE) + λ * Σ|βi|
- Onde:
  - λ (lambda) é o hiperparâmetro de regularização que controla a intensidade da penalidade.
  - βi são os coeficientes do modelo.

### 3.1 Efeito do Lambda (α)
- Quanto maior o valor de lambda, mais forte é a penalização aplicada aos coeficientes.
- Valores maiores de lambda forçam mais coeficientes a se aproximarem de zero ou serem zerados.
- Para cada modelo, haverá um valor de lambda que resultará na remoção de alguns coeficientes.
- A escolha adequada de lambda é fundamental para balancear o viés e a variância do modelo.

## 4. Ridge Regression (Regularização L2)
- A Ridge Regression é utilizada em cenários onde há muitas variáveis preditoras ou onde as variáveis são altamente correlacionadas.
- Adiciona uma penalidade à função de custo baseada na soma dos quadrados dos coeficientes (βi) das variáveis preditoras.
- Diferentemente da Lasso, a Ridge não zera os coeficientes dos preditores, apenas os reduz.
- A função de custo é dada por:
  - Custo = Erro Quadrático Médio (MSE) + λ * Σ(βi²)
- A Ridge é especialmente eficaz quando há colinearidade entre as variáveis preditoras.
- A penalidade da Ridge reduz a sensibilidade do modelo a pequenas variações nos dados de treino.

> [!TIP] DICAS:
> - Lasso (L1): zera coeficientes que não são importantes (seleção de variáveis).
> - Ridge (L2): diminui coeficientes que não são importantes, mas não os zera.
> - Colinearidade: ocorre quando há atributos que são correlacionados entre si.

## 5. Elastic Net
- A Elastic Net combina as características das regularizações Lasso (L1) e Ridge (L2).
- Aplica ambas as penalidades simultaneamente ao mesmo modelo de regressão.
- É útil quando há múltiplas variáveis correlacionadas e se deseja selecionar grupos de variáveis.
- A função de custo da Elastic Net é:
  - Custo = MSE + λ₁ * Σ|βⱼ| + λ₂ * Σ(βⱼ²)
- Onde λ₁ e λ₂ são os parâmetros de regularização para as penalidades L1 e L2, respectivamente.

> [!TIP] DICAS:
> - Para problemas de regressão, há três tipos principais de regularização: L1 (Lasso), L2 (Ridge) e Elastic Net.
> - A Elastic Net é uma combinação das duas primeiras.

## 6. Dropout
- O Dropout é uma técnica de regularização utilizada em redes neurais.
- Consiste em desativar aleatoriamente uma fração dos neurônios (normalmente entre 20% e 50%) durante o treinamento.
- Neurônios desativados não participam da retropropagação (backpropagation) naquela iteração.
- Em cada iteração subsequente, outro conjunto de neurônios pode ser desativado aleatoriamente.
- O Dropout força a rede a construir uma representação distribuída e redundante, evitando que o modelo dependa excessivamente de combinações específicas de neurônios.
- Durante a predição, todos os neurônios são mantidos ativos, mas seus pesos são escalados (reduzidos) proporcionalmente à fração de dropout usada durante o treinamento.

### 6.1 Taxa de Dropout (p)
- É o principal hiperparâmetro do Dropout.
- Define a fração dos neurônios que serão desativados em cada iteração.
- Tipicamente varia entre 0,2 e 0,5.
- Uma taxa muito baixa pode não ser suficiente para prevenir o overfitting.
- Para realizar o dropout, basta multiplicar as ativações por variáveis aleatórias de Bernoulli com uma determinada probabilidade.

> [!CAUTION] OBSERVAÇÃO:
> - Ao contrário das regularizações L1 e L2, o dropout não depende da modificação da função de custo.
> - O dropout pode ser visto como equivalente a treinar uma grande coleção (ensemble) de modelos que compartilham parâmetros.

## 7. Early Stopping
- O Early Stopping consiste em interromper o treinamento antes que o modelo comece a superajustar aos dados de treino.
- É uma técnica utilizada para evitar o overfitting.
- Parâmetros importantes do Early Stopping:
  - Paciência (patience): define quantas épocas o treinamento pode continuar após o desempenho no conjunto de validação ter parado de melhorar.
  - Min Delta: define uma pequena melhoria mínima que precisa ser observada na métrica de validação para ser considerada uma melhoria significativa.
  - Restore Best Weights: opção para restaurar os pesos do modelo para o ponto em que ele teve o melhor desempenho no conjunto de validação.

> [!CAUTION] OBSERVAÇÃO:
> - O early stopping é utilizado para evitar o overfitting, e não apenas para melhorar a acurácia ou calcular a classificação nos dados de validação.

## 8. Batch Normalization
- A Batch Normalization normaliza as ativações das camadas intermediárias de uma rede neural.
- Ajusta os valores das saídas de uma camada para que tenham uma média próxima de 0 e uma variância próxima de 1.
- Benefícios da Batch Normalization:
  - Permite o uso de taxas de aprendizado mais altas.
  - Reduz o deslocamento covariante interno (mudanças na distribuição das ativações em camadas intermediárias à medida que os parâmetros de camadas anteriores são ajustados).
  - Estabiliza a distribuição das ativações.

## 9. Data Augmentation
- A Data Augmentation aumenta a diversidade dos dados de treinamento sem coletar novos dados.
- Consiste em gerar novas amostras de treinamento aplicando transformações aos dados existentes.
- Exemplos de Data Augmentation:
  - Para imagens: rotação, escala, corte ou distorção.
  - Para textos: substituição de palavras.

## 10. Prevenção de Overfitting em SVM
- Em Máquinas de Vetor de Suporte (SVM), o overfitting pode ser prevenido utilizando um kernel linear.
- A SVM separa os dados utilizando o hiperplano ótimo.
- A kernel trick adiciona uma dimensão ao modelo, permitindo que os dados sejam linearmente separados.
- Existem diversas funções de kernel, sendo a mais simples o kernel linear.
- O uso de um kernel linear reduz a complexidade do modelo, prevenindo o overfitting.

> [!CAUTION] OBSERVAÇÃO:
> - Em SVM, garantir que o hiperplano divida perfeitamente os pontos ou usar todos os pontos para a tomada de decisão pode levar ao overfitting.
> - Misturar o conjunto de teste com o de treinamento não é uma prática recomendada, pois a máquina terá acesso aos dados de teste durante o treinamento.