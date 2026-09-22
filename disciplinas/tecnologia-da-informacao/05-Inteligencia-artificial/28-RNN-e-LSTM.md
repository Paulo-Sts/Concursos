# RNN E LSTM

## 1. Redes Neurais Recorrentes (RNN)

### 1.1 Conceito Fundamental
- As RNNs introduzem uma modificação no fluxo das redes neurais tradicionais (Feed-Forward), onde a saída de um neurônio segue para frente e também retorna para ele próprio.
- Em algumas arquiteturas, essa saída pode ser direcionada inclusive para neurônios de camadas anteriores.
- O fluxo não é exclusivamente progressivo, passando a apresentar retornos e realimentações.

### 1.2 Funcionamento Temporal
- Uma entrada no instante T é processada pelo neurônio, e a saída gerada nesse instante retorna como uma entrada no instante T+1.
- A saída do passado alimenta a entrada do futuro, criando um encadeamento entre os dados processados ao longo do tempo.
- Esse comportamento é característico de séries temporais, nas quais existem entradas em diferentes instantes (T=1, T=2, T=3, etc.).

### 1.3 Aplicações Práticas
- Previsão de temperatura a partir de dados meteorológicos: o valor não depende apenas das informações do dia atual, mas também dos dados dos dias anteriores.
- Processamento de linguagem natural: as palavras de uma frase estão encadeadas, e a previsão da próxima palavra depende das palavras anteriores.

> [!CAUTION] OBSERVAÇÃO:
> - Um dos problemas das redes neurais recorrentes tradicionais é o esquecimento gradual das entradas mais antigas (T-3, T-4 ou T-5), uma vez que essas informações vão se diluindo ao serem incorporadas em uma única entrada ao longo do tempo.

### 1.4 Limitações e Evolução
- As RNNs tradicionais enfrentam o problema do desvanecimento do gradiente em sequências longas.
- Posteriormente, surgiram as redes transformers, baseadas no mecanismo de atenção e em estratégias de pre-training, que passaram a superar as RNNs em diversas aplicações.
- Embora as LSTM estejam gradualmente entrando em desuso em alguns contextos, elas ainda se mantêm relevantes, especialmente na análise de séries temporais.

## 2. LSTM (Long Short-Term Memory)

### 2.1 Definição e Características
- A LSTM é uma rede neural recorrente específica que possui portões (gates): portão de esquecimento, portão de entrada e portão de saída.
- Trata-se de uma rede em que a saída de uma célula de memória é utilizada como entrada na próxima iteração.
- A memória é tratada como uma informação própria, processada e atualizada ao longo do tempo, o que evita a perda do histórico.

### 2.2 Entradas da Célula LSTM
- A célula LSTM recebe três entradas simultaneamente:
  - A memória que veio do passado (C[t-1]): como um "diário" trazendo tudo o que a LSTM estava lembrando até o momento anterior.
  - A saída do passo anterior (h[t-1]): o "resumo" que a LSTM produziu na etapa anterior.
  - A informação nova do instante atual (x[t]): o dado fresco chegando agora (palavra, número, sensor, etc.).

> [!TIP] DICAS:
> - A memória explícita é o diferencial da LSTM em relação às redes neurais recorrentes tradicionais, nas quais as informações passadas ficam restritas ao mecanismo de atualização dos pesos.
> - Esse conceito é cobrado em provas (FGV/2024/CVM) como a inovação arquitetônica distintiva da LSTM.

### 2.3 Forget Gate (Portão do Esquecimento)
- Logo após as entradas, a célula se pergunta: "Da memória passada, o que ainda é importante manter? O que posso descartar?"
- O símbolo σ (sigmóide) atua como um filtro de importância sobre os dados que chegam.
- O símbolo x representa que a porta realmente apaga ou mantém o conteúdo.
- O Forget Gate decide o que continua na memória e o que some, eliminando dados antigos ou irrelevantes.

### 2.4 Input Gate (Portão de Entrada)
- A próxima área colorida é o Input Gate, responsável por lidar com a entrada nova, fazendo duas perguntas:

#### 2.4.1 "Vale a pena guardar essa informação nova?"
- O bloco σ decide se a célula deve permitir que algo entre na memória.

#### 2.4.2 "Como devemos representar essa novidade?"
- O bloco tanh cria uma "versão trabalhada" da nova informação, como se fosse uma anotação limpa.
- Em seguida, o símbolo x combina a decisão (do σ) com o conteúdo aprendido (do tanh).

- O Input Gate recebe como entradas o h[t-1] e o x[t], realizando uma combinação envolvendo uma função de ativação sigmoide e outra função de ativação tangente hiperbólica.

> [!CAUTION] OBSERVAÇÃO:
> - Até aqui, a célula já decidiu: o que apagar, o que acrescentar de novo e como transformar essa novidade.

### 2.5 Atualização da Memória
- O símbolo de + no centro junta:
  - O que sobrou do passado (depois do Forget Gate).
  - O que foi aprendido agora (do Input Gate).
- Surge a nova memória da célula (C[t]), que incorpora tanto as informações preservadas quanto as informações recém-adicionadas.

### 2.6 Output Gate (Portão de Saída)
- A última área colorida é o Output Gate, que se pergunta: "O que devo compartilhar com o mundo lá fora neste instante?"
- Utiliza:
  - Um σ para decidir quanto da memória mostrar.
  - Um tanh para transformar a memória em um formato mais adequado.
  - Um x final para combinar as duas coisas.
- O Output Gate recebe como entradas o h[t-1] e o x[t], que passam por uma função de ativação sigmoide.
- Em paralelo, o conteúdo da memória atual é processado por uma função de ativação tangente hiperbólica.

### 2.7 Saídas Finais da Célula
- A LSTM produz duas saídas:
  - A memória atualizada (C[t]): aquilo que ela decidiu carregar adiante.
  - A saída atual (h[t]): aquilo que ela resolveu revelar no presente.
- O h[t] representa a saída da célula LSTM no instante atual, que vai para a próxima célula LSTM (como h[t-1]) e para as camadas superiores da rede.

> [!TIP] DICAS:
> - Em provas (FGV/2024/TRF-1), o portão de saída é o elemento responsável por extrair informação útil do estado atual para ser utilizada no cálculo do estado oculto.
> - O estado oculto corresponde ao novo estado gerado a partir da informação processada, associado ao conhecimento que é efetivamente extraído e disponibilizado como saída da célula.

## 3. Problemas do Gradiente em RNNs e Solução com LSTM

### 3.1 Vanishing Gradient (Desaparecimento do Gradiente)
- Condição em que ocorre perda de informação do passado durante o treinamento.
- As informações mais antigas (T-3, T-4, T-5) vão se diluindo ao serem incorporadas em uma única entrada ao longo do tempo.

### 3.2 Exploding Gradient (Explosão do Gradiente)
- Condição em que ocorre a geração de valores excessivamente grandes durante o treinamento.
- Pode tornar o processo de aprendizado instável.

### 3.3 Solução Proporcionada pela LSTM
- A introdução de células de memória e, em especial, do portão de esquecimento permite avaliar quais informações devem ser mantidas ou descartadas.
- Contribui para mitigar esses efeitos e tornar o fluxo de informações mais estável ao longo do tempo.
- A LSTM foi desenvolvida especificamente para lidar com problemas relacionados ao gradiente, sendo ideal para processar e prever eventos em dados de série temporal com dependências de longo prazo.

> [!CAUTION] OBSERVAÇÃO:
> - A LSTM representa um avanço em relação às RNNs tradicionais, tendo sido desenvolvida para lidar com problemas relacionados ao gradiente, como o desaparecimento e a explosão.
> - Esse é um ponto recorrente em questões de concurso (CEBRASPE-CESPE/2025/POLÍCIA FEDERAL).

## 4. Comparativo entre Arquiteturas
| ARQUITETURA | CARACTERÍSTICA PRINCIPAL | APLICAÇÃO TÍPICA | LIMITAÇÃO |
|-------------|--------------------------|------------------|-----------|
| Rnn tradicional | Fluxo com realimentação; saída retorna como entrada futura | Séries temporais; dados sequenciais | Esquecimento gradual de entradas antigas; problemas de gradiente |
| Lstm | Células de memória com mecanismos de gating (forget, input, output) | Séries temporais com dependências de longo prazo; PLN | Maior custo computacional que RNNs simples; gradualmente substituída por transformers em algumas aplicações |
| Transformer | Mecanismo de atenção; processamento paralelo | PLN; sequências longas | Alto custo computacional; necessidade de grandes volumes de dados |

> [!CAUTION] OBSERVAÇÃO:
> - No processamento de linguagem natural, os modelos baseados em arquitetura transformer superaram as RNN e LSTM, mas o custo computacional das arquiteturas transformer é maior quando comparado ao das RNN e LSTM.
> - O limite dos transformers está associado à capacidade de processamento disponível, enquanto RNN e LSTM apresentam limitações estruturais para lidar com sequências longas.
> - Atenção à ambiguidade em enunciados de concurso que não deixam claro a quais "tais modelos" se referem.

## 5. Representação de Textos em PLN

### 5.1 Técnicas de Pré-processamento e Vetorização
- Bag of Words (BoW): representação que conta a frequência de palavras em um texto, ignorando a ordem.
- TF-IDF: pondera a frequência de termos pela raridade em todo o corpus.
- Word2Vec: cria representações vetoriais densas que capturam relações semânticas entre palavras.
- Tokenização: processo de dividir o texto em unidades menores (palavras, subpalavras ou caracteres).

### 5.2 Modelagem com Arquiteturas Sequenciais
- Após a etapa de vetorização, ocorre a modelagem propriamente dita.
- Nessa fase, arquiteturas especializadas em tratar dados sequenciais são aplicadas para capturar o contexto presente na frase.
- As RNNs e LSTMs foram amplamente utilizadas nesse papel antes de serem superadas pelos transformers.

> [!TIP] DICAS:
> - As técnicas como Bag of Words, TF-IDF, Word2Vec e tokenização pertencem ao pré-processamento ou à vetorização de textos.
> - Apenas após essa etapa é que arquiteturas como RNN, LSTM ou transformers são aplicadas para capturar dependências contextuais.
> - Esse entendimento é fundamental para questões que perguntam sobre a técnica mais adequada para capturar dependência contextual de palavras em uma frase.