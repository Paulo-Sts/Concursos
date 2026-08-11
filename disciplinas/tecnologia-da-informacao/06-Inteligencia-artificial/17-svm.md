# Máquinas de Vetores de Suporte (SVM)

## 1. Conceitos Fundamentais do SVM
- O SVM (Support Vector Machine) é um algoritmo de aprendizado de máquina supervisionado.
- Tradicionalmente empregado em tarefas de classificação, com posterior adaptação para regressão.
- O algoritmo é considerado antigo e de formulação simples.
- Em sua forma original, pressupõe dados linearmente separáveis.

> [!CAUTION] OBSERVAÇÃO:
> - O SVM é um classificador não probabilístico, ou seja, não determina distribuições de probabilidade para a classificação.
> - O SVM combina modelos lineares com técnicas de aprendizagem baseadas em instâncias.

### 1.1 Definição de Vetor de Suporte
- Vetores de suporte são os pontos localizados nas margens do hiperplano.
- Esses pontos são utilizados para o cálculo do hiperplano ótimo.
- São os pontos mais próximos da classe oposta em cada grupo.
- A partir dos vetores de suporte, define-se o hiperplano ótimo que realiza a separação entre as classes.

### 1.2 O Hiperplano Ótimo
- O hiperplano ótimo é aquele que maximiza a distância em relação aos vetores de suporte.
- Outras retas que funcionam como hiperplanos, mas não maximizam essa distância, não são consideradas ótimas.
- A distância entre a margem e o exemplo da classe positiva deve ser igual à distância entre a margem e o exemplo da classe negativa.
- Essa condição de igualdade caracteriza o hiperplano ótimo no contexto do SVM.
- A máxima distância para os vetores de suporte é o critério determinante para a posição do hiperplano.

> [!TIP] DICAS:
> - Quando a questão perguntar qual algoritmo utiliza o hiperplano ótimo para separar classes, a resposta correta é o SVM.
> - Em um espaço bidimensional, o hiperplano equivale a uma linha.
> - Em um espaço tridimensional, o hiperplano equivale a um plano.
> - Em n dimensões, trata-se de um hiperplano n-dimensional.

#### 1.2.1 Representação do Hiperplano em Diferentes Dimensões
- Em uma dimensão (1D): o hiperplano ótimo corresponde a um ponto.
- Em duas dimensões (2D): o hiperplano ótimo corresponde a uma reta (linha) que separa adequadamente os dados.
- Em três dimensões (3D): o hiperplano ótimo corresponde a um plano.
- Em quatro ou mais dimensões: o hiperplano ótimo é um hiperplano quadridimensional ou n-dimensional.
- Embora não seja possível visualizar representações em múltiplas dimensões, o algoritmo é capaz de calcular o hiperplano ótimo que realiza a separação linear.

## 2. Kernel Trick
- O Kernel trick consiste em aplicar uma função de kernel para adicionar uma ou mais dimensões ao espaço original.
- O objetivo é tornar os dados linearmente separáveis quando não o são no espaço original.
- O método foi desenvolvido em 1992.
- O mapeamento realizado pelo kernel é implícito, e não explícito.
- Principais funções de kernel:
  - Kernel linear;
  - Kernel radial;
  - Kernel polinomial;
  - Entre outros.

> [!TIP] DICAS:
> - O kernel trick permite que o SVM lide com dados não linearmente separáveis.
> - Quando os dados não são linearmente separáveis em uma dimensão, utiliza-se o kernel trick para adicionar dimensões.
> - Exemplo: em um conjunto de dados unidimensional com valores que não permitem separação linear, o kernel trick adiciona uma nova dimensão, deslocando pontos de uma classe para valores mais altos e mantendo os da outra classe em valores mais baixos.

## 3. Soft Margin (Margem Suave)
- O conceito de soft margin foi introduzido em 1995.
- Nesse caso, admitem-se violações à margem, permitindo que alguns pontos fiquem mal classificados.
- Essa abordagem é importante para evitar overfitting.
- O hiperplano de margem suave não separa perfeitamente os pontos de diferentes classes.
- Permite a existência de erros de classificação, possibilitando que pontos de uma classe apareçam no lado oposto.
- O cálculo da margem pode incluir pontos que ultrapassam o limite, o que reduz o risco de overfitting.

> [!TIP] DICAS:
> - A soft margin é utilizada quando se deseja um modelo mais equilibrado no espaço n-dimensional, em vez de tentar separar perfeitamente todos os exemplos do conjunto de treinamento.

## 4. Características Gerais do SVM
- O SVM é um algoritmo de aprendizado supervisionado.
- Utiliza o hiperplano ótimo que maximiza as distâncias dos vetores de suporte.
- Pode ser usado para desafios de classificação ou regressão.
- Quando os dados não são linearmente separáveis, aplica-se a técnica kernel trick para adicionar uma dimensão e tornar a separação linear.
- O SVM é baseado em instâncias, pois identifica exemplos (vetores de suporte) para o cálculo do hiperplano.
- Uma margem mais ampla geralmente indica um melhor desempenho na classificação, pois sugere uma separação mais clara entre as classes.

> [!CAUTION] OBSERVAÇÃO:
> - O SVM não se limita a dados linearmente separáveis, pois o kernel trick permite lidar com dados linearmente inseparáveis.
> - O SVM não é um algoritmo de agrupamento (aprendizado não supervisionado), mas sim de classificação e regressão (supervisionado).