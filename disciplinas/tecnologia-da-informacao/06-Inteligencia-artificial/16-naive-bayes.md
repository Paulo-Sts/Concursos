# Naive Bayes

## 1. Conceito e Definição
- O Naive Bayes (também conhecido como Bayes Ingênuo) é um algoritmo de aprendizado de máquina supervisionado.
- Sua característica distintiva em relação à maioria dos outros algoritmos é que ele trabalha exclusivamente com classificação, não realizando previsões numéricas ou regressão.
- É uma família de algoritmos baseados em probabilidade.
- O algoritmo é amplamente utilizado em problemas de classificação, especialmente em aplicações de processamento de linguagem natural (PLN) e análise de texto.

## 2. Suposições Ingênuas do Modelo
O algoritmo se baseia em duas suposições consideradas "ingênuas":

### 2.1 Independência Condicional entre as Características
- O algoritmo assume que todas as características (atributos ou colunas) do conjunto de dados são independentes entre si.
- Na prática, essa suposição raramente se mantém estritamente. Por exemplo, na classificação de e-mails spam, a presença de determinadas palavras pode aumentar significativamente a probabilidade de ocorrência de outras.
- Apesar disso, o Naive Bayes ainda se mostra um classificador eficiente, especialmente na classificação de textos.

### 2.2 Contribuição Igual de Cada Evento
- O algoritmo assume que cada evento (característica) contribui igualmente para o resultado da classificação.
- Na prática, alguns atributos podem ter maior relevância para a decisão do que outros.

> [!TIP] DICAS:
> - A "ingenuidade" do modelo é justamente essa suposição de independência condicional entre as variáveis preditoras. É esse o ponto que os examinadores costumam cobrar em provas.
> - Apesar de as suposições serem matematicamente "ingênuas", o algoritmo tem um bom desempenho, especialmente em conjuntos de dados com muitas características (como textos).

## 3. Fundamentação Matemática: Teorema de Bayes
- O algoritmo baseia-se no Teorema de Bayes para calcular probabilidades a posteriori.
- A fórmula de Bayes é:
  - P(A|B) = [P(B|A) * P(A)] / P(B)
  - P(A|B) é a probabilidade de A ocorrer dado que B ocorreu (probabilidade a posteriori).
  - P(B|A) é a probabilidade de B ocorrer dado que A ocorreu (probabilidade condicional ou verossimilhança).
  - P(A) e P(B) são as probabilidades a priori de A e B, respectivamente.
- No contexto do Naive Bayes, a fórmula é aplicada para estimar a probabilidade de uma instância pertencer a uma determinada classe, dadas as suas características.
- O algoritmo constrói uma matriz de probabilidades condicionais (ou a posteriori) para cada classe, com base nos dados de treinamento.

### 3.1 Exemplo de Aplicação da Fórmula
O material apresentou o seguinte exemplo clássico de aplicação da fórmula de Bayes:
- Um médico sabe que a meningite (M) causa torcicolo (T) em 50% dos casos.
- Ele também sabe que a probabilidade de uma pessoa ter meningite é de 1/50.000 e que a probabilidade de uma pessoa ter torcicolo é de 1/20.
- Pergunta: Qual é a probabilidade de uma pessoa ter meningite, dado que ela está com torcicolo?

- Dados:
  - P(T|M) = 0,5
  - P(M) = 1/50.000
  - P(T) = 1/20

- Cálculo:
  P(M|T) = [P(T|M) * P(M)] / P(T)
  P(M|T) = [0,5 * (1/50.000)] / (1/20)
  P(M|T) = 0,0002 = 2/10.000 = 0,02%

> [!CAUTION] OBSERVAÇÃO:
> - O exemplo demonstra como o teorema é usado para calcular a probabilidade de uma causa (meningite) dado um efeito (torcicolo). É um modelo clássico para entender a lógica do classificador.

## 4. Funcionamento e Aplicações Práticas

### 4.1 Classificação de E-mails (Spam ou Normal)
- Esta é a aplicação mais conhecida e frequentemente citada do algoritmo.
- O treinamento do algoritmo consiste em aprender probabilidades a partir de um dataset rotulado.
- Cada linha do dataset representa um e-mail.
- Cada coluna representa uma palavra específica, indicando a presença (1) ou ausência (0) daquela palavra no e-mail.
- O dataset também inclui uma coluna com o rótulo da classe (spam ou normal).
- Exemplo de estrutura do dataset:

| ID   | AMOR | NIGERIANO | VENDER | CLASSE |
|------|------|-----------|--------|--------|
| 1    | 1    | 0         | 0      | Normal |
| 2    | 0    | 1         | 1      | Spam   |
| 3    | 1    | 1         | 0      | Normal |

- Após o treinamento, o algoritmo calcula a probabilidade de um novo e-mail ser spam com base na presença ou ausência de palavras como "nigeriano" ou "vender", e a probabilidade de ser normal considerando palavras como "amor".
- Para classificar um novo e-mail, o algoritmo avalia cada palavra presente e calcula as probabilidades condicionais de ser spam ou normal, utilizando a abordagem de classificadores bayesianos.

### 4.2 Outras Aplicações
- O Naive Bayes é indicado para tarefas de classificação binária e também para classificação multiclasse.
- É amplamente utilizado em:
  - Filtragem de spam;
  - Classificação de textos e documentos;
  - Análise de sentimentos;
  - Sistemas de recomendação.

## 5. Características Técnicas Adicionais
- O algoritmo realiza aprendizado supervisionado, ou seja, necessita de dados rotulados para o treinamento.
- É eficiente no uso de dados categóricos, embora também possa lidar com dados numéricos (desde que seja aplicada uma distribuição de probabilidade adequada, como a Gaussiana).
- Não é um algoritmo de otimização, portanto não utiliza uma abordagem de "força bruta" para encontrar a solução ótima.
- Deve ser diferenciado de outros algoritmos como:
  - Regressão Logística (modela a relação entre variáveis independentes e uma dependente categórica usando a função logística).
  - K-Means (aprendizado não supervisionado para particionamento de dados).
  - Random Forest (combina múltiplas árvores de decisão).
  - Regressão Linear (estima relação entre variáveis contínuas).