# Ajuste de Modelos Underfitting e Overfitting

## 1. Treinamento e Avaliação de Modelos
- O processo de treinamento de máquinas envolve a divisão do conjunto de dados em dois subconjuntos principais: treinamento e teste.
- Os dados de treinamento são utilizados para criar a inteligência artificial, enquanto os dados de teste servem para avaliar o desempenho final.
- A avaliação deve obrigatoriamente ocorrer em dados não vistos anteriormente pela máquina durante a fase de treinamento.
- O objetivo central do processo é garantir que a inteligência artificial possua poder de generalização, sendo capaz de processar dados novos com precisão.

> [!CAUTION] OBSERVAÇÃO:
> - Avaliar o modelo utilizando apenas o conjunto de treinamento gera um falso resultado positivo, pois a máquina tende a aprender e decorar esses exemplos específicos em vez de aprender o padrão geral.

## 2. Comportamento do Erro e Complexidade do Modelo
- A complexidade do modelo está diretamente relacionada ao tempo e ao volume de treinamento realizado.
- A tendência natural é que o erro no conjunto de treinamento diminua continuamente conforme a máquina é treinada e se torna mais complexa.
- No conjunto de teste, o erro inicialmente diminui, mas volta a subir após atingir um ponto ideal denominado ajuste apropriado ou best fit.
- O estágio anterior ao erro mínimo no teste é o underfitting; o estágio posterior, onde o erro de teste sobe enquanto o de treino cai, é o overfitting.

## 3. Conceitos de Viés e Variância
- Viés ou bias: refere-se a previsões erradas decorrentes do aprendizado de padrões distorcidos nos dados de treinamento.
- O viés algorítmico pode gerar impactos éticos negativos ao reproduzir preconceitos humanos contidos nas bases de dados, como o racismo em dosimetria de penas.
- Variância: indica a sensibilidade do modelo a mudanças no conjunto de treinamento, onde pequenas alterações nos dados geram mudanças drásticas no modelo final.
- Modelos com alta variância tentam se adaptar milimetricamente a qualquer variação ou ruído da base de dados.

| CARACTERÍSTICA | MODELO EM UNDERFITTING | MODELO EM OVERFITTING |
|---|---|---|
| Variância | Baixa | Alta |
| Viés | Alto | Baixo |
| Complexidade | Insuficiente para os dados | Excessiva para os dados |

## 4. Overfitting ou Sobreajuste
- O overfitting ocorre quando o modelo se ajusta excessivamente aos dados de treinamento, capturando inclusive os ruídos e padrões irrelevantes.
- Ruídos representam dados mal classificados ou colunas pouco relevantes que não auxiliam na previsão correta do rótulo.
- O modelo apresenta alta precisão no treinamento, mas desempenho significativamente pior em dados novos e desconhecidos.
- É considerado um comportamento problemático e indesejável em projetos de aprendizado de máquina.

### 4.1 Causas do Overfitting
- Uso de algoritmos excessivamente complexos para bases de dados simples;
- Quantidade insuficiente de dados de treinamento para representar o mundo real;
- Presença de dados desbalanceados ou muitos ruídos na base original;
- Utilização de atributos pouco relevantes para a relação entre as variáveis.

### 4.2 Soluções para o Overfitting
- Regularização: técnica para reduzir a complexidade do algoritmo e atingir o ajuste ideal;
- Poda de árvores de decisão: redução das decisões da árvore para torná-la menos especializada;
- Dropout: técnica de apagar neurônios em redes neurais para evitar a especialização excessiva;
- Early stopping: parada antecipada do treinamento assim que o erro de teste ou validação começar a subir;
- Validação cruzada e data augmentation para balanceamento de classes;
- Uso de ensembles: combinação de múltiplos modelos para realizar uma votação final e reduzir erros individuais.

## 5. Underfitting ou Subajuste
- O underfitting ocorre quando o modelo é muito simples para aprender os padrões de uma base de dados complexa.
- O sistema falha em determinar uma relação significativa entre os dados de entrada e saída esperada.
- Apresenta baixa capacidade preditiva e altos índices de erro tanto no conjunto de treinamento quanto no de teste.

### 5.1 Causas do Underfitting
- Uso de algoritmos com complexidade insuficiente para o problema;
- Tempo de treinamento reduzido ou insuficiente para a quantidade de dados;
- Atributos não representativos ou aplicação de regularização excessiva.

### 5.2 Soluções para o Underfitting
- Aumentar a complexidade do modelo utilizado ⟶ trocar modelos lineares por modelos curvos;
- Prolongar o tempo de treinamento para permitir que o modelo atinja níveis de erro mais baixos;
- Encontrar dados melhores ou aumentar a quantidade de dados de entrada;
- Reduzir a aplicação de técnicas de regularização.

> [!TIP] DICAS:
> - Para identificar o overfitting em questões de prova, busque por termos como especialização excessiva, captura de ruídos e alta precisão exclusiva no treino.
> - O ajuste ideal ou appropriate-fitting é aquele onde o modelo ignora os ruídos e foca apenas nos padrões reais dos dados.