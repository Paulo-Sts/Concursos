# Interpretabilidade de Modelos

## 1. Introdução à Interpretabilidade
- A interpretabilidade de modelos é uma característica desejável que permite a um modelo receber uma entrada, gerar uma saída e explicar como chegou a essa saída.
- Modelos como a árvore de decisão são tradicionalmente conhecidos como altamente interpretáveis, pois suas decisões são baseadas em atributos bem definidos.
- Exemplo: uma árvore de decisão pode indicar que o valor de uma transação acima de mil reais ou realizada online com cartão de crédito durante a madrugada sugere um potencial de fraude.
- Diferente de redes neurais, que possuem baixa interpretabilidade, os cientistas de dados criaram métricas para identificar quais atributos são mais importantes em uma previsão.
- A interpretabilidade é fundamental para setores como saúde, finanças e justiça, onde decisões baseadas em IA precisam ser justificáveis.
- Exemplo na saúde: é fundamental saber por que uma máquina recomendou um tratamento específico ao analisar exames e prontuários, garantindo a segurança do paciente.
- Exemplo nas finanças: ao negar um empréstimo, é essencial entender o porquê da decisão para evitar injustiças ou erros.

### 1.1. Benefícios da Interpretabilidade
- Melhora a transparência do modelo.
- Ajuda a identificar erros ou vieses nos dados e no algoritmo.
- Aumenta a confiança do usuário no modelo.

### 1.2. Níveis de Interpretabilidade
- Global: oferece uma visão geral de como o modelo funciona, como saber que uma árvore de decisão classifica instâncias com base em regras claras de divisão.
- Local: foca em explicar por que o modelo tomou uma decisão específica para um determinado caso.
  - Ferramentas como LIME e SHAP são úteis para explicações locais, ajudando a justificar por que uma entrada específica (X) gerou uma saída específica (Y).

> [!CAUTION] OBSERVAÇÃO:
> - O nível local é mais específico e detalhado para cada previsão individual, enquanto o global dá uma visão macro do funcionamento do modelo.

## 2. Modelos quanto à Interpretabilidade

### 2.1. Modelos Mais Interpretáveis
- Regressão linear e logística: fáceis de interpretar devido à relação clara entre entrada e saída, tornando as previsões previsíveis e compreensíveis.
- Árvores de decisão: são visualizáveis e permitem entender as regras usadas para dividir os dados, facilitando a compreensão das decisões.

### 2.2. Modelos Menos Interpretáveis
- Redes neurais profundas: são poderosas, mas difíceis de entender devido à complexidade das interações entre camadas e neurônios.
- Ensembles: como Random Forests e XGBoost, são compostos por vários modelos, o que torna a interpretação mais complicada.

## 3. Feature Importance
- Mede o quanto cada feature (variável) afeta a previsão do modelo, sendo um método que depende do modelo utilizado.

### 3.1. Vantagens da Feature Importance
- Fácil de entender em modelos simples, como árvores de decisão.
- Útil para identificar as variáveis mais influentes no modelo global.
- Pode ser usado para reduzir a dimensionalidade: ao descobrir que uma variável (ex.: x3) não é importante, ela pode ser removida no retreinamento do modelo.

### 3.2. Limitações da Feature Importance
- Não capta bem a relação entre variáveis em modelos mais complexos, como redes neurais.
- A interpretação pode variar dependendo do método de cálculo utilizado, sendo necessário, em alguns casos, recorrer a ferramentas como LIME ou SHAP.

### 3.3. Técnicas Comuns de Feature Importance

#### 3.3.1. Análise de Coeficientes em Modelos Lineares
- Em modelos lineares, como a regressão logística, coeficientes com maior variação influenciam mais a decisão do modelo.
- Essa análise indica o quanto cada variável contribui para o resultado, seja de forma positiva ou negativa.
- Exemplo: no dataset Iris, atributos como largura e comprimento de pétalas podem ser mais relevantes que o tamanho da cepa.

#### 3.3.2. Importância das Features no Random Forest
- Modelos como Random Forest possuem seus próprios métodos internos para calcular a importância de cada feature, geralmente baseados na redução de impureza ou na frequência de uso.

#### 3.3.3. Permutation Feature Importance
- É uma técnica para avaliar a importância de uma variável observando o impacto no erro do modelo quando seus valores são aleatorizados.
- Passo a passo:
  - Treine o modelo com todos os dados e calcule o erro. Para regressão, utiliza-se o Mean Squared Error (MSE); para classificação, a acurácia.
  - Exemplo: MSE original = 100.
  - Permute (embaralhe) os valores de uma feature (ex.: número de quartos) para remover sua informação do modelo.
  - Calcule o MSE com os valores permutados.
  - Exemplo: MSE permutado = 130.
  - Compare a diferença: 130 - 100 = 30.
  - Repita o processo para todas as features e classifique as diferenças: features com maiores diferenças no MSE são as mais importantes.
- Se o erro piorar muito após a permutação, o atributo é importante. Se o erro melhorar, o atributo estava atrapalhando o modelo e pode ser removido.

> [!TIP] DICAS:
> - A Permutation Feature Importance é uma técnica direta e intuitiva para entender o impacto de cada variável no modelo, sendo útil para depuração e seleção de atributos.

> [!CAUTION] OBSERVAÇÃO:
> - A Permutation Feature Importance não é uma técnica baseada exclusivamente em árvores de decisão, podendo ser aplicada a diversos modelos.

## 4. SHAP (Shapley Additive Explanations)
- SHAP é um método baseado na teoria dos jogos cooperativos para atribuir uma contribuição justa a cada variável em uma previsão individual.
- Em termos práticos, o modelo fornece valores que indicam o quanto cada atributo contribui para uma previsão específica, sem a necessidade de detalhamento matemático profundo.
- Exemplo: para uma pessoa de 65 anos com previsão de 0,4, o SHAP explicará que essa previsão é influenciada pela idade e pelo fato de ser mulher, justificando o resultado.

### 4.1. Vantagens do SHAP
- Fornece explicações localmente precisas, ou seja, previsão por previsão.
- Considera a interação entre variáveis e gera valores justos para cada feature.
- Pode ser usado com praticamente qualquer tipo de modelo.

### 4.2. Limitações do SHAP
- O cálculo dos valores de Shapley é computacionalmente intensivo para modelos complexos com muitas variáveis.
- Pode ser difícil de entender para pessoas não familiarizadas com a matemática por trás da teoria dos jogos.

> [!TIP] DICAS:
> - SHAP é a ferramenta mais recomendada quando se busca uma explicação justa e matematicamente fundamentada para cada previsão, especialmente em modelos complexos.

## 5. LIME (Local Interpretable Model-Agnostic Explanations)
- O LIME gera uma explicação local ajustando um modelo interpretável, geralmente linear, em torno de uma previsão específica do modelo original.
- O método perturba os dados de entrada e observa como as mudanças afetam a previsão, fornecendo explicações para uma instância específica.

### 5.1. Vantagens do LIME
- Funciona com qualquer tipo de modelo, mesmo aqueles considerados "caixas pretas", como redes neurais profundas (é um modelo-agnóstico).
- É simples de implementar e fornece explicações interpretáveis localmente.
- É rápido para modelos menores e com menos variáveis.

### 5.2. Limitações do LIME
- As explicações são locais e podem não refletir o comportamento global do modelo.
- Depende fortemente de como a vizinhança local é definida, o que pode levar a inconsistências nas explicações.

> [!TIP] DICAS:
> - O LIME é ideal para explicar uma previsão específica de forma rápida e sem depender da estrutura interna do modelo, sendo muito versátil.

> [!CAUTION] OBSERVAÇÃO:
> - Uma limitação crítica do LIME é que ele não fornece uma visão global do modelo, o que pode levar a interpretações equivocadas se usado isoladamente.