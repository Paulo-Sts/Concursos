# Redes Neurais Artificiais

## 1. Introdução às Redes Neurais Artificiais
- As redes neurais artificiais têm essa denominação por seu funcionamento ser baseado no funcionamento das redes neurais naturais.
- Paralelismo:
  - No sistema natural, um estímulo mecânico incide sobre as terminações nervosas (neurônios na extremidade); se o estímulo for suficientemente forte, o neurônio é ativado.
  - O neurônio ativado recebe a informação pelos dendritos e transmite o impulso pelo axônio para os neurônios seguintes.
  - Esse processo se repete sucessivamente até que o impulso alcance a camada de saída (cérebro), onde ocorre a percepção consciente.
  - No sistema artificial, em lugar do choque nervoso, realizam-se computações.
  - Há uma camada de entrada que recebe o impulso inicial, diversas camadas escondidas (hidden layers) e, por fim, uma camada de saída.
- Para que a previsão seja possível, realiza-se um processo de treinamento da rede neural artificial com base em um conjunto de dados (dataset) de entrada e saída.

> [!TIP] DICAS:
> - A analogia biológica é frequentemente cobrada em provas, especialmente a relação entre dendritos (entradas), axônios (saídas) e sinapses (pesos).

> [!CAUTION] OBSERVAÇÃO:
> - A ativação do neurônio depende da intensidade do estímulo (limiar de ativação), assim como no neurônio artificial.

## 2. Estrutura do Neurônio Artificial
- Cada neurônio artificial segue a estrutura básica do perceptron de McCulloch-Pitt.
- Componentes:
  - Entradas (inputs) provenientes da camada anterior.
  - Pesos (weights) armazenados em cada conexão, representados por valores numéricos.
  - Somatório das entradas multiplicadas pelos respectivos pesos: Σ x · w = x₁ · w₁ + x₂ · w₂.
  - Bias (viés): neurônio adicional que insere um valor constante com peso próprio, sendo somado ao resultado; introduz aleatoriedade e não linearidade no modelo.
  - Função de ativação: recebe o somatório e retorna a saída do neurônio.
- Exemplo: função degrau (saída 0 ou 1) - neurônio inativo ou ativo.
- Neurônios da camada de entrada possuem apenas uma entrada e não há peso associado.
- Neurônios intermediários e da camada de saída apresentam entradas ponderadas por pesos.

> [!TIP] DICAS:
> - O bias é um neurônio adicional que, embora receba peso próprio, funciona como um ajuste constante para melhor adaptação do modelo.
> - A capacidade de ajuste do modelo está diretamente relacionada aos pesos atribuídos às conexões.

### 2.1 Arquitetura MLP (Multi-Layer Perceptron)
- Estrutura básica mais comum em redes neurais simples:
  - Uma camada de entrada.
  - Uma ou mais camadas intermediárias (hidden layers ou camadas escondidas).
  - Uma camada de saída.
- Classificação multiclasse: se a saída for 1 e 0 = classe A; 0 e 1 = classe B; 0 e 0 = classe C; 1 e 1 = classe D.

### 2.2 Rede Neural Feedforward
- Rede com camada de entrada, camadas escondidas e camada de saída.
- Os dados são processados necessariamente nessa ordem: da entrada para a saída.
- É considerada a rede neural tradicional.

### 2.3 Rede Neural Recorrente
- A saída de um neurônio pode retornar como entrada para a camada anterior.
- Adequada para análise de séries temporais, pois encadeia o passado com o futuro.

> [!CAUTION] OBSERVAÇÃO:
> - A distinção da rede neural feedforward não está na presença de camadas ocultas (todas as redes podem ter), mas sim no fato de o processamento ocorrer apenas no sentido direto, da entrada para a saída.

### 2.4 Camadas da Rede
- Camada de entrada: recebe os dados de entrada (X do dataset), direcionando cada coluna para cada neurônio de entrada.
- Camadas escondidas (hidden layers): camadas intermediárias que processam as informações.
- Camada de saída: fornece o resultado (Y), correspondente à classificação.

> [!CAUTION] OBSERVAÇÃO:
> - A primeira camada oculta recebe os sinais de entrada aplicados aos neurônios (nós de computação) da segunda camada.

## 3. Treinamento da Rede Neural
- Objetivo: ajustar os pesos para que a rede aprenda a acertar o valor de saída Y para um dado X.
- Processo:
  - Os pesos são definidos com valores aleatórios (normalmente entre 0 e 1) no início do treinamento.
  - Insere-se a primeira entrada, executa-se o processamento e observa-se a saída.
  - Se houver acerto por acaso, nenhuma alteração é realizada.
  - Se houver erro, o erro é distribuído pelas conexões e os pesos são alterados.
  - Repete-se o procedimento até que a rede passe a acertar todo o conjunto de treinamento.

> [!CAUTION] OBSERVAÇÃO:
> - O treinamento utiliza um subconjunto do dataset de treinamento (conjunto de treino).

## 4. Backpropagation (Retropropagação)
- Algoritmo de treinamento de redes neurais.
- Etapas:
  - Feedforward: insere-se a entrada, que percorre a rede pelas conexões ponderadas pelos pesos, até a obtenção da saída.
  - Atualização dos pesos: se a saída estiver correta, nada se altera; se houver erro, procede-se à atualização dos pesos de cada conexão.
- Fórmula geral: peso novo = peso antigo - termo de correção.

> [!TIP] DICAS:
> - Backpropagation é o processo de "voltar" o erro pelas camadas para ajustar os pesos, sendo um dos algoritmos mais importantes para redes neurais.

## 5. Gradiente Descendente
- Algoritmo de otimização aplicado sobre o erro.
- Funcionamento:
  - O erro é representado por uma função.
  - O gradiente descendente realiza a derivação dessa função.
  - Partindo de um determinado nível de erro, à medida que se calculam derivadas sucessivas, o valor do erro tende a ser reduzido até a aproximação de um mínimo.
- Taxa de aprendizado:
  - Atualizações muito pequenas: estagnação em um ponto intermediário, sem alcançar o erro mínimo desejado.
  - Atualizações muito grandes: "saltam" o ponto de mínimo e oscilam em níveis mais altos de erro.

> [!TIP] DICAS:
> - "Descendente" porque o procedimento tem por finalidade conduzir à redução progressiva do erro.
> - O gradiente descendente é a função (processo de otimização) destinada a minimizar o erro de cada peso da rede neural, atuando na fase de backpropagation.

> [!CAUTION] OBSERVAÇÃO:
> - O resultado do gradiente descendente depende do ponto em que se inicia a rede neural (pesos originais) e do tempo de treinamento.

## 6. Funções de Ativação
- Função matemática que decide se o neurônio será ativado ou não.
- Responsável por introduzir não linearidade nas redes neurais.
- O neurônio só consegue resolver problemas não lineares por meio da função de ativação.

### 6.1 Função Degrau (Step Function)
- Qualquer valor abaixo de zero produz saída igual a zero (neurônio não ativado).
- Qualquer valor acima de zero produz saída igual a um (neurônio ativado).

### 6.2 Função Linear
- Forma: Y = aX + b.
- O valor de saída acompanha diretamente o valor de entrada acrescido de um termo constante.
- Não é amplamente utilizada em redes neurais.

### 6.3 Função Logística (Sigmoide)
- Mesma função empregada na regressão logística.
- A saída pode assumir valor zero, valor um ou qualquer valor contínuo entre [0,1].
- Interpretação: o neurônio pode não se ativar, ativar-se completamente ou ativar-se parcialmente.
- É especialmente útil para manter o gradiente descendente estável durante o treinamento.
- Fórmula: f(x) = 1/(1 + e^(-x)).

> [!TIP] DICAS:
> - A função sigmoide é frequentemente representada pela fórmula 1/(1 + e^(-x)). Recomenda-se a memorização dessa função, pois é comum em provas.

### 6.4 Função Maxout
- A camada de saída recebe valores provenientes de diferentes neurônios.
- O resultado emitido corresponde ao maior valor dentre eles.
- Comum na camada de saída.

### 6.5 Função Gaussiana
- Fórmula: φ(x) = exp[-(x - c_j)² / (2σ_j²)].
- Utilizada para construir funções gaussianas em redes de função de base radial (redes de função de base radial).
- A curva gerada possui formato típico de sino.

### 6.6 Função Tangente Hiperbólica (Tanh)
- Produz valores de saída entre -1 e 1.
- Interpretação: valores próximos a -1 = ausência de ativação; valores próximos a 1 = ativação.

### 6.7 Função ReLU (Rectified Linear Unit)
- Muito utilizada atualmente, especialmente em redes neurais convolucionais.
- Funcionamento:
  - Se o valor de entrada for menor ou igual a zero: saída é zero.
  - Se o valor de entrada for maior que zero: saída é igual ao próprio valor de entrada.

### 6.8 Função Leaky ReLU
- Introduz uma variação na ReLU.
- Por meio de ajustes matemáticos adicionais, produz um valor de saída levemente diferente na região negativa.

> [!TIP] DICAS:
> - A função ReLU é caracterizada pela regra: se entrada ≤ 0, saída = 0; se entrada > 0, saída = entrada.
> - Recomenda-se a memorização da função ReLU e da função logística para provas.

> [!CAUTION] OBSERVAÇÃO:
> - Transformações exclusivamente lineares não conferem capacidade expressiva adequada ao modelo. A utilização de neurônios apenas com função linear não é adequada.
> - Funções de ativação não lineares são essenciais para que o modelo possa aprender representações complexas, pois múltiplas camadas de transformações lineares equivaleriam a uma única transformação linear.

## 7. Aprendizado em Redes Neurais
| TIPO DE APRENDIZADO | CONCEITO | TIPO DE DADO | PROCESSO DE TREINAMENTO | PRINCIPAIS ARQUITETURAS |
|---------------------|----------|--------------|------------------------|------------------------|
| SUPERVISIONADO | A rede aprende a partir de exemplos com entradas e saídas conhecidas (rótulos) | Dados rotulados (input → output) | Calcula o erro → retropropaga (backpropagation) → ajusta pesos via gradiente descendente | Perceptron Multicamadas (MLP); Redes Convolucionais (CNNs); Redes Recorrentes (RNNs, LSTM) |
| NÃO SUPERVISIONADO | A rede aprende sem rótulos, buscando padrões e estruturas ocultas nos dados | Dados não rotulados (somente input) | Baseia-se em métricas de similaridade ou autoaprendizagem | Mapas Auto-Organizáveis (SOM – Kohonen); Autoencoders |
| APRENDIZADO POR REFORÇO | O agente aprende por tentativa e erro, interagindo com o ambiente e recebendo recompensas | Dados gerados por interações com o ambiente | Baseia-se em recompensas (positivas/negativas) e políticas de decisão | Deep Q-Networks (DQN); Policy Gradient; Actor-Critic (A3C, PPO) |

> [!CAUTION] OBSERVAÇÃO:
> - Há redes neurais em todos os tipos de aprendizado (supervisionado, não supervisionado e por reforço); o que se altera é o tipo de aprendizado empregado.
> - No aprendizado supervisionado, a rede aprende a partir da entrada para prever a saída.
> - No aprendizado não supervisionado, destacam-se modelos como mapa auto-organizável (SOM) e Autoencoder, utilizados em tarefas de agrupamento.
> - No aprendizado por reforço, a rede toma uma decisão, recebe o resultado produzido pelo ambiente e aprende ao longo do tempo quais decisões adotar.

> [!TIP] DICAS:
> - No aprendizado por reforço, a rede não recebe diretamente o resultado de um dataset previamente rotulado; a entrada de dados passa a ser a resposta do ambiente à decisão tomada.

## 8. Deep Learning (Aprendizado Profundo)
- Caracteriza-se pela utilização de redes neurais com dezenas, centenas ou milhares de camadas de neurônios.
- Redes neurais mais simples, com três a cinco camadas, são normalmente tratadas dentro do escopo de aprendizado de máquina.
- Quando se ultrapassa esse patamar de profundidade, passa-se a enquadrá-las como Deep Learning.