# Algoritmo K-Nn (K-Vizinhos Mais Próximos)

## 1. Fundamentos do Algoritmo K-Nn
- O K-NN é um algoritmo de aprendizado de máquina supervisionado, não paramétrico, utilizado para tarefas de classificação e regressão.
- Seu princípio baseia-se na premissa de que a classificação ou previsão de um novo ponto é determinada pela sua proximidade com outros pontos em um conjunto de dados pré-existentes.
- O modelo não segue uma função pré-definida (como a regressão linear), mas sim a distribuição dos dados no espaço n-dimensional.

### 1.1 Funcionamento para Classificação
- Durante o treinamento, o algoritmo apenas armazena todos os pontos do conjunto de dados (ou "aprende" o espaço de características).
- Para classificar uma nova instância, o K-NN calcula a distância entre este novo ponto e todos os pontos do conjunto de treinamento.
- Em seguida, seleciona os K vizinhos mais próximos.
- A classe do novo ponto é definida pela classe que aparece com maior frequência entre esses K vizinhos (votação majoritária).
- Exemplo: Para um novo ponto, se K=5 e os 5 vizinhos mais próximos pertencem às classes A, A, B, B, B, o ponto será classificado como classe B.

### 1.2 Funcionamento para Regressão
- O K-NN também pode ser utilizado para prever valores numéricos contínuos.
- Neste caso, o valor previsto para o novo ponto é a média (ou a mediana) dos valores numéricos dos K vizinhos mais próximos.

## 2. O Hiperparâmetro K
- O valor de K é um hiperparâmetro crucial, definido pelo cientista de dados antes do treinamento do modelo.
- Ele determina quantos vizinhos serão considerados na decisão de classificação ou regressão.
- A escolha de K impacta diretamente o desempenho do modelo e pode gerar resultados diferentes para a classificação de um mesmo ponto.

### 2.1 Critérios e Boas Práticas para a Escolha de K
- O valor de K não deve ser escolhido aleatoriamente.
- Valores pequenos de K tornam o modelo mais sensível a ruídos e outliers (sobreajuste).
- Valores grandes de K podem suavizar demais a fronteira de decisão (subajuste).
- Uma prática comum é utilizar valores ímpares para K quando o problema possui apenas duas classes, com o objetivo de evitar situações de empate na votação.

> [!TIP] DICAS: 
> - O valor de K é uma decisão do cientista de dados e influencia o desempenho do modelo.
> - A escolha de K ímpares ajuda a evitar empates em problemas binários.

## 3. Métrica de Distância
- O algoritmo K-NN avalia a proximidade entre os pontos por meio de métricas de distância.
- A distância Euclidiana é a métrica mais utilizada, definida como a distância em linha reta no espaço geométrico ortogonal.
- A fórmula da distância Euclidiana entre dois pontos (p e q) em um espaço n-dimensional é: d(p, q) = √(Σ (pᵢ - qᵢ)²).

### 3.1 Importância da Normalização dos Dados
- O K-NN é sensível à escala das variáveis de entrada.
- Se uma variável possui valores em uma escala muito maior que outra, ela dominará o cálculo da distância, distorcendo os resultados.
- Por isso, a normalização ou padronização dos dados (ex.: Min-Max Scaling, Z-score) é um pré-requisito fundamental antes da aplicação do algoritmo, garantindo que todas as dimensões tenham o mesmo poder de discriminação.

> [!CAUTION] OBSERVAÇÃO: 
> - O K-NN trabalha exclusivamente com dados numéricos. Dados categóricos ou discretos devem ser convertidos para o formato numérico (por exemplo, por meio de codificação one-hot).

## 4. Características e Propriedades do K-Nn

### 4.1 Dimensionalidade
- O algoritmo é robusto e capaz de operar com dezenas ou centenas de colunas (dimensões).
- Embora seja mais facilmente visualizado em duas ou três dimensões (para fins didáticos), ele se mantém eficaz em espaços de alta dimensionalidade, embora sofra da "maldição da dimensionalidade", onde a distância entre os pontos se torna menos discriminativa.

### 4.2 Natureza do Aprendizado
- É um algoritmo de aprendizado preguiçoso (lazy learner), pois não constrói um modelo explícito durante o treinamento; ele apenas armazena os dados de treinamento.
- Toda a computação (cálculo de distâncias) é realizada no momento da classificação ou previsão (tempo de inferência).

### 4.3 Aplicações
- O K-NN é amplamente utilizado para reconhecimento de padrões e problemas de classificação, como sistemas de recomendação, filtragem de spam e detecção de anomalias.