# Monitoramento de Modelos

## 1. Monitoramento de Desempenho de Modelos
- Processo de garantir que o modelo de aprendizado de máquina continue a fornecer previsões precisas e úteis após a sua implantação.
- O objetivo é verificar se o modelo está executando a tarefa para a qual foi projetado, mantendo a eficácia ao longo do tempo.

### 1.1 Indicadores de Desempenho
- Acurácia: mede a proporção de previsões corretas em comparação com os resultados reais.
- Precisão, Recall e F1-Score: métricas essenciais para modelos de classificação, com ênfase em cenários com dados desbalanceados.
- Erro Quadrático Médio e Erro Absoluto Médio: utilizados em modelos de regressão para quantificar o desvio das previsões em relação aos valores reais.
- A escolha da métrica mais adequada depende do contexto do problema; por exemplo, em detecção de anomalias, o Recall é frequentemente a métrica mais apropriada.

> [!CAUTION] OBSERVAÇÃO:
> - O monitoramento de desempenho não se limita à fase de treinamento ou desenvolvimento; ele deve ser contínuo e executado após a implantação do modelo em produção.

## 2. Tipos de Variações no Desempenho do Modelo
- O monitoramento pode identificar diferentes padrões de degradação do desempenho ao longo do tempo.

### 2.1 Sudden Drift
- Ocorre quando o modelo começa a apresentar erros de forma repentina e abrupta.

### 2.2 Gradual Drift
- Os erros surgem de maneira lenta e progressiva, tornando-se mais perceptíveis com o passar do tempo.

### 2.3 Incremental Drift
- Mais comum em problemas de regressão.
- O modelo faz boas previsões inicialmente, mas, com o tempo, a lógica subjacente dos dados se altera, causando um aumento gradual dos erros.

### 2.4 Recurring Concepts
- Frequente em séries temporais.
- O modelo tem bom desempenho na maioria do tempo, mas falha em períodos específicos onde as condições mudam e para os quais não foi treinado adequadamente.

## 3. Data Drift
- Fenômeno que ocorre quando há mudanças na distribuição dos dados de entrada ao longo do tempo.
- Os dados que o modelo processa atualmente não representam mais com precisão os dados com os quais foi treinado originalmente.
- Consequência direta: o modelo pode começar a perder precisão e eficácia.
- Principais causas:
  - Mudanças nos padrões de comportamento dos usuários.
  - Surgimento de novos tipos de dados.
  - Alterações no contexto de negócios ou no ambiente operacional.

### 3.1 Exemplos de Data Drift
- Modelo de recomendação de produtos: treinado com dados de compras de verão, mas ao chegar o inverno, o padrão de consumo muda para roupas de frio.
- Modelo de detecção de fraudes: treinado com transações presenciais, mas com o aumento de pagamentos digitais, as características das transações se alteram significativamente.
- Modelo de previsão de vendas em supermercado: treinado com dados históricos de demanda, mas durante a pandemia, o comportamento de compra mudou para maior volume em menos dias e priorização de itens básicos.

### 3.2 Tipos de Data Drift

#### 3.2.1 Prior Probability Shift
- Ocorre quando a distribuição da variável de saída se altera.
- A distribuição dos dados de entrada permanece inalterada.
- Exemplo: um modelo de detecção de fraudes treinado com uma taxa de 2% de transações fraudulentas. Com o tempo, essa taxa sobe para 5%, alterando a probabilidade de saída, embora as características de entrada (valor, país, horário) continuem as mesmas.

#### 3.2.2 Covariate Shift
- A distribuição dos dados de entrada muda.
- A relação entre as variáveis de entrada e a variável de saída permanece a mesma.
- Exemplo: um modelo treinado para prever a demanda de transporte público com base na temperatura. Se o modelo foi treinado em uma cidade com temperaturas entre 10°C e 30°C e é aplicado em outra com temperaturas de 20°C a 40°C, a distribuição dos dados de entrada mudou, mas a lógica da relação permanece a mesma (temperaturas mais baixas aumentam a demanda).

## 4. Concept Drift
- Fenômeno que ocorre quando a própria relação entre as variáveis de entrada e a variável de saída se altera ao longo do tempo.
- Diferentemente do data drift, a natureza da correlação entre os dados e o resultado previsto é que muda.

### 4.1 Exemplos de Concept Drift
- Detecção de fraudes financeiras: um modelo treinado para identificar fraudes com base em transações fora do horário comercial ou de grandes valores. Os fraudadores mudam suas táticas para fazer pequenas transações dentro do horário comercial, alterando a relação entre as características e o resultado.
- Classificação de e-mails como spam: um modelo treinado para detectar spam com base em palavras-chave suspeitas. Os spammers evoluem e passam a usar frases mais sutis, imitando e-mails legítimos, o que faz com que as palavras-chave percam sua capacidade preditiva.

### 4.2 Diferença Fundamental entre Data Drift e Concept Drift
- No concept drift, o comportamento subjacente muda completamente, podendo exigir o desenvolvimento de um modelo totalmente novo.
- No data drift, embora a distribuição dos dados se altere, o modelo existente pode ainda ser funcional, desde que seja atualizado.

## 5. Detecção de Drifts
- Processo sistemático para identificar quando um modelo não está mais se comportando conforme o esperado devido a data drift ou concept drift.
- Envolve o monitoramento contínuo das distribuições dos dados de entrada e saída e a comparação com as distribuições originais utilizadas no treinamento.
- A deterioração das métricas de desempenho contínuas é um forte indicador da presença de drift.

### 5.1 Técnicas de Detecção
- Testes estatísticos: utilização de testes como o de Kolmogorov-Smirnov para comparar a distribuição dos dados atuais com os dados históricos e detectar diferenças significativas.
- Análise de janelas deslizantes: verificação da consistência dos padrões do modelo em diferentes períodos de tempo.

## 6. Retreino e Atualização de Modelos
- Processos essenciais para manter a eficácia do modelo em ambientes dinâmicos, readequando-o a novos padrões nos dados.

### 6.1 Estratégias de Retreino
- Batch Retreino: o modelo é retreinado em intervalos regulares ou quando uma quantidade significativa de novos dados está disponível.
- Online Learning: o modelo é atualizado constantemente com novos dados em tempo real, permitindo uma adaptação mais rápida.
- Incremental Learning: o modelo é ajustado com base em pequenas atualizações nos dados, sem a necessidade de um retreino completo.

### 6.2 Estratégias de Atualização
- Atualização de Hiperparâmetros: reajuste de parâmetros como taxa de aprendizado, regularização ou profundidade de árvores.
- Feature Engineering: criação ou seleção de novas variáveis que se tornaram relevantes, ou remoção daquelas que perderam importância.
- Mudança de Modelo: substituição completa do tipo de modelo por um mais adequado à nova realidade dos dados.