# Machine Learning

## Inteligência Artificial (IA)
- Capacidade de um sistema interpretar dados externos, aprender com eles e utilizar essas aprendizagens para atingir objetivos específicos através de adaptação flexível.

## Machine Learning (ML)
- Subcampo da IA que permite aos computadores aprender sem serem explicitamente programados.
- Processo onde o desempenho em uma tarefa aumenta com a experiência extraída de novos dados.
- Difere da programação tradicional: gera regras a partir de resultados, e não o contrário.
- Modelos gerados são regras estatísticas na forma de modelos matemáticos e parâmetros.
- Etapa de treinamento é mais custosa; etapa de inferência é menos custosa.

## Fontes de erro em modelos preditivos
- Erro: diferença entre o valor previsto e o valor real.
- Ocorrem devido à aleatoriedade ou variáveis desconhecidas.
- Foco: encontrar padrões generalizáveis por uma função que reduz o erro de generalização.

## Fluxo do machine learning
1. **Pré-processamento:** Entrada de categorias e dados brutos. Gera conjuntos de dados para treinamento e teste.
2. **Aprendizado:** Aplica o treinamento com os dados processados.
3. **Avaliação:** Gera o modelo.
4. **Predição:** Cerne do ML.

## Conjuntos de dados
- Dados de Treinamento: Dividem-se em:
  - Dados de Treino
  - Dados de Validação (para calibragem)
- Dados de Testes: Dados nunca vistos pelo modelo.

## Underfitting e Overfitting
- **Underfitting (Subajuste):** Modelo não se ajusta bem aos dados de treino. Alto viés, baixa variância.
- **Overfitting (Sobreajuste):** Modelo superajustado aos dados de treino. Baixo viés, alta variância.
- **Viés:** Diferença entre a predição média e o valor correto.
- **Variância:** Sensibilidade do modelo a novos conjuntos de dados.
- **Modelo ideal:** Baixo viés e baixa variância.

#### Soluções
- Overfitting: Usar mais dados de treinamento (com maior variedade).
- Underfitting: Aumentar complexidade do modelo, tempo de treino, selecionar variáveis, reduzir regularização.

## Técnicas de regularização
- Ajuste fino da complexidade do modelo.
- Limita a flexibilidade do modelo para evitar overfitting.
- Introduz parâmetros de regularização (fatores de regularização ou termos de penalização) para controlar a magnitude dos pesos dos parâmetros.

## Otimização de hiperparâmetros
- Hiperparâmetro: Parâmetro cujo valor é definido antes do início do aprendizado.
- Valores de outros parâmetros são derivados via treinamento.

## Separabilidade de dados
- Separabilidade linear bidimensional: Existe ao menos uma linha reta que separa dois conjuntos de pontos.
- Em três dimensões, ocorre por meio de um hiperplano.
- É possível modificar a representação dos dados para um formato onde as classes sejam mais facilmente separáveis (coordenadas polares, cilíndricas, etc.).

## Redução de dimensionalidade
- Aprendizagem Não Supervisionada.
- Obtém representação reduzida ou compactada dos dados originais.
- Cria novas características sintéticas a partir das originais.
- **Seleção de recursos:** Remoção de recursos irrelevantes ou redundantes.
- **Extração de recursos:** Transformação dos dados em recursos adequados para modelagem.
- Técnicas:
  - PCA (Principal Component Analysis): Foca nas principais características variáveis.
  - t-SNE (T-distributed Stochastic Neighbor Embedding): Algoritmo para vetorização com distribuição estocástica de valores vizinhos.

## Modelos lineares
- Função matemática aplicada a dados para identificar padrões e oferecer previsões.
- Tipos:
  - **Regressão Linear:** Isola o efeito de uma variável mantendo outras constantes (aspecto quantitativo contínuo).
  - **Regressão Logística:** Algoritmo supervisionado para classificação binária.

## Classificador Naive Bayes
- Utiliza teoria das probabilidades para encontrar a classificação mais provável.
- Simples, rápido e escalável (assume independência entre variáveis).
- Funciona bem com classificação de texto, NLP, detecção de spam.
- Requer poucos dados de treinamento para estimar parâmetros.