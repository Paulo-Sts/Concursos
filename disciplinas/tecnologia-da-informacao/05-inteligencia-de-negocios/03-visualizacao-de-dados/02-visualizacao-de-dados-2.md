# Visualização de Dados 2

## 1. Gráfico de Linha
- Representa dados contínuos ao longo do tempo, com pontos conectados por linhas.
- Quando usar: para visualizar tendências ao longo do tempo, como o crescimento das vendas mensais ou a variação da temperatura ao longo dos dias.
- Interpretação:
  - A inclinação da linha mostra a direção da tendência (aumento, diminuição ou estabilidade).
  - Pontos elevados indicam picos de valor, enquanto pontos baixos indicam quedas.
- Exemplo: evolução das vendas mensais de uma empresa ao longo de um ano.
- Comparação com gráfico de barras:
  - Gráfico de barras: útil para comparar várias categorias de dados, cada categoria representada por uma barra.
  - Gráfico de linhas: adequado para identificar padrões em conjuntos de dados contínuos.

> [!TIP] DICAS:
> - O gráfico de linhas é a melhor opção no Excel para representar a evolução de dados ao longo do tempo, como vendas mensais.
> - O gráfico de barras empilhadas é usado quando há mais de uma categoria sendo apresentada por cada categoria no gráfico de barras.

> [!CAUTION] OBSERVAÇÃO:
> - Em gráficos de linhas com duas variáveis (dupla entrada), os dados estão nos pontos, não nas linhas. A linha é apenas uma projeção visual e não necessariamente indica igualdade de valores entre as variáveis.

## 2. Gráfico de Dispersão (Scatter Plot)
- Usa pontos para representar a relação entre duas variáveis numéricas. Cada ponto no gráfico representa um par de valores (x, y).
- Quando usar: para analisar a correlação entre duas variáveis, por exemplo, entre horas de estudo e notas de alunos, ou entre salário e crédito no banco.
- Interpretação:
  - Padrões nos pontos podem indicar correlação positiva (quanto maior uma variável, maior a outra).
  - Correlação negativa (quanto maior uma variável, menor a outra).
  - Ausência de correlação (pontos dispersos sem padrão definido).
- Para montar o gráfico, é necessária uma tabela com duas colunas (x e y).

### 2.1 Força da Correlação
- Correlação perfeita: todos os pontos se alinham exatamente sobre uma reta ou curva.
- Correlação forte: pontos próximos à linha de tendência, com pouco espalhamento.
- Correlação fraca: pontos com espalhamento apreciável em torno da linha de tendência.
- Correlação positiva fraca: há uma tendência de crescimento de y em função de x, mas com dispersão considerável.
- Correlação negativa fraca: há uma tendência de decrescimento de y em função de x, mas com dispersão considerável.

### 2.2 Padrões Não Lineares
- O diagrama de dispersão pode apresentar padrões que não são lineares, como uma forma de "telhado" (crescimento até um ponto e depois decrescimento).
- Nesses casos, não se pode afirmar a existência de correlação linear, embora possa haver relação entre as variáveis.
- Exemplo: relação entre área desmatada (km²) e número de termos de autuação do Ibama entre 2018 e 2023. Quanto maior o número de autuações, menor tende a ser a área desmatada, indicando correlação negativa (com algumas exceções).
- Exemplo prático: em uma agência pública, identificar correlação entre tempo de atendimento ao público e tempo de experiência dos funcionários. Espera-se correlação negativa: mais experiência ⟶ menor tempo de atendimento.

> [!TIP] DICAS:
> - Gráfico de dispersão é ideal para examinar a relação entre duas variáveis quantitativas e identificar possíveis correlações.
> - O gráfico de dispersão é a ferramenta adequada para entender se uma relação de causa e efeito faz sentido.

> [!CAUTION] OBSERVAÇÃO:
> - Boxplot é utilizado para encontrar outliers, não para correlação.
> - Histograma mostra a variação da frequência de um valor, não a relação entre duas variáveis.
> - Gráfico de Pareto (80/20) e diagrama espinha de peixe (causas de um problema) não servem para correlação.

## 3. Histograma
- Gráfico de barras que mostra a distribuição de uma variável contínua.
- As barras representam faixas de valores (intervalos) e a altura indica a frequência de ocorrência.
- Quando usar: para visualizar a distribuição de dados, como a distribuição de idades em uma população, ou a frequência de determinada faixa etária.
- Interpretação:
  - O formato do histograma ajuda a identificar a distribuição dos dados (normal, enviesada, uniforme).
  - Os intervalos onde as barras são mais altas indicam os valores mais frequentes.
- Exemplo: para identificar a faixa etária mais comum na população brasileira, o histograma é a melhor forma, pois coloca a quantidade de pessoas por faixa de idade.

> [!CAUTION] OBSERVAÇÃO:
> - O gráfico de pizza não é apropriado para variáveis quantitativas, mesmo que sejam discretas ou ordinais. Para esse tipo de dado, o gráfico de colunas ou histograma é mais adequado.

## 4. Outros Tipos de Gráficos (Menção Rápida)
- Gráfico de pizza: apresenta um círculo dividido em fatias, cada uma com uma cor diferente. Útil para mostrar proporções de um todo, mas não para evolução temporal ou correlação.
- Mapa de árvores (treemap): quanto maior o tamanho do retângulo, maior o valor associado àquele retângulo. Vem sendo muito utilizado.
- Gráfico de Gantt: cronograma com tarefas a serem entregues, não serve para correlação.
- Diagrama espinha de peixe: descreve as causas de um problema (ferramenta de qualidade, mas não para correlação).