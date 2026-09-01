## Dados Desbalanceados

### 1. Introdução aos Dados Desbalanceados
- Ocorrem quando as classes de um conjunto de dados não estão distribuídas de maneira equilibrada, resultando em uma classe (chamada de majoritária) com significativamente mais amostras do que a outra (chamada de minoritária).
- Um exemplo típico é uma base onde 95% dos dados pertencem a uma classe e apenas 5% à outra.
- Este fenômeno é comum em problemas de detecção de anomalias, como fraudes ou falhas de equipamentos.
- Modelos de aprendizado de máquina treinados com esses dados podem se tornar tendenciosos, aprendendo a privilegiar a classe majoritária em detrimento da minoritária.
- Em tarefas de detecção de anomalias, o erro de falso negativo (quando a máquina não identifica uma anomalia) é o mais crítico e não pode passar despercebido.
- Para mitigar esse problema, faz-se necessário balancear os dados, seja aumentando a quantidade da classe minoritária ou diminuindo a da classe majoritária.
- A diferença entre um dado da classe positiva (a anomalia) e um da classe negativa (o normal), muitas vezes, é muito tênue.

> [!TIP] DICAS:
> - A classe minoritária costuma ser a mais importante para o negócio, como a classe de "fraude" ou "falha".
> - Em prova, a "detecção de anomalias" é o exemplo clássico para justificar a necessidade de balanceamento.

> [!CAUTION] OBSERVAÇÃO:
> - É crucial entender que a alta acurácia em um problema desbalanceado pode ser uma ilusão. Se o modelo prevê 100% da classe majoritária, a acurácia será de 95%, mas ele será inútil para encontrar os 5% que realmente importam.

### 2. Oversampling (Sobreamostragem)
- Técnica que cria ou duplica amostras da classe minoritária para equilibrar a distribuição.
- O objetivo é aumentar a representatividade da classe minoritária no conjunto de treinamento.

#### 2.1 Random Oversampling
- Funciona duplicando aleatoriamente amostras da classe minoritária até que seu número se iguale ou se aproxime ao da classe majoritária.
- Vantagem: é um método simples de implementar.
- Desvantagem: pode levar ao overfitting, pois as mesmas amostras são repetidas várias vezes, fazendo com que o modelo decore os dados de treino e perca a capacidade de generalização.

#### 2.2 Oversampling com Smote (Synthetic Minority Over-sampling Technique)
- Cria novas amostras sintéticas da classe minoritária, em vez de simplesmente duplicar as existentes.
- A técnica funciona por interpolação, ou seja, criando novos pontos entre duas ou mais amostras reais da classe minoritária que são próximas no espaço de características.
- Vantagem: ajuda a evitar o overfitting, pois gera exemplos novos e diversos.
- Desvantagem: pode criar exemplos sintéticos que não representam bem a distribuição real dos dados, podendo introduzir ruído no modelo.

### 3. Undersampling (Subamostragem)
- Técnica que remove amostras da classe majoritária para equilibrar a distribuição com a classe minoritária.

#### 3.1 Random Undersampling
- Funciona removendo aleatoriamente amostras da classe majoritária até que o número de exemplos de ambas as classes se torne semelhante.
- Vantagem: é fácil de implementar e reduz o tempo de treinamento, pois menos dados precisam ser processados.
- Desvantagem: pode levar à perda de informações importantes da classe majoritária, o que pode prejudicar o desempenho do modelo.

#### 3.2 Undersampling com Clusterização (Tomer Links, Nearmiss)
- Remove seletivamente amostras da classe majoritária que estão próximas às amostras da classe minoritária ou aquelas que causam confusão entre as classes.
- Vantagem: remove exemplos que criam ambiguidade, ajudando a melhorar a separação entre as classes.
- Desvantagem: é computacionalmente mais caro e ainda pode resultar na perda de dados importantes da classe majoritária.

### 4. Dados Sintéticos
- São gerados artificialmente para aumentar o número de amostras da classe minoritária, com base nos padrões observados nos dados reais.
- O Smote é uma técnica popular para gerar dados sintéticos por interpolação.
- GANs (Generative Adversarial Networks) podem ser usadas para gerar dados sintéticos de alta qualidade, especialmente em domínios complexos como imagens ou texto.

### 5. Ajuste dos Pesos
- Altera a importância das classes na função de custo (ou perda) do modelo, durante o treinamento.
- Dá um peso maior à classe minoritária, fazendo com que ela tenha mais influência no cálculo do erro e, consequentemente, na atualização dos parâmetros do modelo.
- O principal efeito é reduzir o impacto das amostras da classe majoritária durante o treinamento, forçando o modelo a prestar mais atenção à classe minoritária.

### 6. Métricas Adequadas: Precisão e Recall
- A acurácia (proporção de acertos totais) não é uma métrica confiável para dados desbalanceados, pois pode ser alta mesmo que o modelo não identifique nenhum exemplo da classe minoritária.
- As métricas mais adequadas são a Precisão e o Recall, que focam no desempenho do modelo na classe positiva (minoritária).

#### 6.1 Precisão
- Mede a proporção de verdadeiros positivos (VP) em relação ao total de positivos preditos pelo modelo (VP + Falsos Positivos - FP).
- Em termos simples, a precisão responde: "de tudo o que o modelo classificou como positivo, quanto realmente é positivo?".
- Fórmula: Precisão = VP / (VP + FP)

#### 6.2 Recall (ou Sensibilidade)
- Mede a proporção de verdadeiros positivos (VP) em relação ao total de positivos reais (VP + Falsos Negativos - FN).
- Em termos simples, o recall responde: "de todos os positivos reais, quantos o modelo conseguiu capturar?".
- É a métrica mais utilizada em problemas de dados desbalanceados, pois penaliza o modelo por não encontrar os exemplos da classe minoritária (falsos negativos).
- Fórmula: Recall = VP / (VP + FN)

### 7. F1-Score
- É a média harmônica entre a Precisão e o Recall, oferecendo um equilíbrio entre as duas métricas.
- É uma métrica útil quando se deseja um único número para avaliar o desempenho do modelo, considerando tanto a capacidade de encontrar os positivos (recall) quanto a precisão dessas classificações.
- Fórmula: F1-Score = 2 x (Precisão x Recall) / (Precisão + Recall)

> [!TIP] DICAS:
> - Foco na Classe Minoritária: Sempre priorize o Recall em problemas de detecção (fraude, falha, doença), pois o custo de um falso negativo é alto.
> - Smote vs. Undersampling: Em prova, o Smote é geralmente a resposta mais adequada para evitar overfitting, pois gera dados novos. O oversampling aleatório é criticado por replicar dados e causar overfitting.
> - Ajuste de Pesos: O ajuste de pesos não cria novos dados, ele apenas altera a importância dos dados existentes durante o treinamento.

> [!CAUTION] OBSERVAÇÃO:
> - Cuidado com a pegadinha do ajuste de pesos: o objetivo é dar maior peso à classe minoritária, e não à majoritária. Atribuir maior peso à classe majoritária pioraria ainda mais o problema.