# Visualização de Dados

## 1. Conceitos Fundamentais

### 1.1 Definição de Visualização de Dados
- Processo de representar graficamente informações e dados para facilitar a compreensão e a interpretação de padrões, tendências e outliers (pontos fora da curva).
- Os dados são transformados em gráficos e integrados em um painel interativo ou dashboard, permitindo a interação com as informações necessárias.
- Evolução: anteriormente era realizada através da abertura de uma planilha ou tabela no Excel, seguida da solicitação para criar um gráfico; hoje é necessária a capacidade de trabalhar com dados como tabelas, planilhas e bases de dados em SQL para gerar visualizações atraentes.

### 1.2 Análise Exploratória dos Dados
- Na exploração de dados, visualizam-se não apenas as estatísticas, mas também informações relevantes.
- Exemplos de análises possíveis:
  - Correlação entre variáveis;
  - Correlação entre colunas da tabela;
  - Relação entre o aumento do peso de uma pessoa e o aumento da altura dessa pessoa.
- O gráfico de dispersão permite observar visualmente a relação entre duas variáveis.
- É fundamental conhecer melhor os dados quando se está coletando dados para utilizá-los no treinamento de uma Inteligência Artificial (IA).

### 1.3 Aplicação Prática em Projetos de IA
- Exemplo: criação de uma IA que prevê se uma transação é fraudulenta ou não, bloqueando transações com indícios de fraude e gerando uma economia de milhões de reais mensais.
- Cria-se um gráfico de linha demonstrando o quanto o novo projeto de IA economizou mensalmente para a instituição bancária.
- Esse gráfico estará integrado em um dashboard que o proprietário do banco poderá observar para comprovar o quanto valeu a pena investir em IA.

> [!TIP] DICAS: 
> - A visualização de dados não é apenas estatística; envolve apresentação e visualização para facilitar a tomada de decisão.
> - Gráficos como o histograma são cobrados em várias questões sobre estatística e cálculos de frequência, não se encaixando em um curso específico sobre visualização de dados.

## 2. Tipos de Gráficos

### 2.1 Gráfico de Barras
- Utilizado para comparar quantidades em diferentes categorias.
- As barras podem ser dispostas verticalmente ou horizontalmente.
- A altura (ou comprimento) das barras indica o valor de cada categoria.
- Barras mais longas representam maiores valores.

#### 2.1.1 Quando Usar
- Para comparar dados discretos ou categóricos, como o número de vendas por mês ou o desempenho de diferentes equipes.

#### 2.1.2 Interpretação
- Cada barra representa uma categoria.
- O valor da categoria é proporcional ao tamanho da barra.
- Permite comparação visual direta entre as categorias.

> [!TIP] DICAS: 
> - Em provas, fique atento à escala do gráfico para não errar os cálculos.
> - Verifique se a questão pede comparação entre categorias ou cálculo de proporções.
> - Em gráficos de barras, a soma de todas as barras pode representar o total, a menos que especificado de outra forma.

> [!CAUTION] OBSERVAÇÃO: 
> - O gráfico de barras pode ser usado para comparar valores absolutos, mas pode perder a noção do todo, diferente do gráfico de pizza.
> - Cuidado com variações percentuais: calcule sempre usando o valor anterior como base.

### 2.2 Gráfico de Pizza ou Gráfico de Setor
- Mostra a divisão de um todo em partes, em formato circular.
- Cada fatia representa uma proporção de uma categoria.
- O tamanho de cada fatia indica a porcentagem que essa categoria ocupa no total.
- As fatias não devem ser muito numerosas para evitar confusão.

#### 2.2.1 Quando Usar
- Quando se deseja mostrar a proporção de partes em relação ao total.
- Exemplo: porcentagem de participação de mercado de diferentes empresas.

#### 2.2.2 Interpretação
- Cada fatia corresponde a uma categoria.
- O ângulo ou área de cada fatia é proporcional ao valor que ela representa.
- A soma de todas as fatias corresponde a 100% do total.

> [!TIP] DICAS: 
> - O gráfico de pizza é mais indicado quando o número de categorias é pequeno.
> - É caracterizado por ser um gráfico para se ter uma noção das proporções das categorias entre si.
> - Em provas, o gráfico de pizza é frequentemente chamado de gráfico de setores.

> [!CAUTION] OBSERVAÇÃO: 
> - Gráficos de pizza são utilizados na visualização e na análise exploratória de dados em painéis e dashboards.
> - Quando se tem muitas categorias, o gráfico de pizza pode ficar poluído e de difícil interpretação, sendo preferível o gráfico de barras.

## 3. Outros Tipos de Gráficos Mencionados

### 3.1 Gráfico de Linhas
- Utilizado para visualizar a variação de uma variável ao longo do tempo.
- Permite identificar tendências e padrões temporais.

### 3.2 Gráfico de Dispersão
- Apresenta diversos valores e permite a comparação entre uma variável e outra.
- Útil para identificar correlações entre variáveis.

### 3.3 Boxplot (Gráfico de Caixa)
- Utilizado para identificar outliers (pontos fora da curva).
- Mostra a distribuição dos dados através de quartis.

### 3.4 Mapa de Temperatura
- Mapas coloridos com cores mais quentes ou mais frias para assinalar, por exemplo, a maior densidade demográfica em uma região.
- Utilizado para representar dados geográficos ou matrizes de correlação.

> [!TIP] DICAS: 
> - Cada tipo de gráfico tem uma finalidade específica. Escolha o gráfico adequado ao tipo de dado que você deseja visualizar.
> - Em provas, preste atenção ao que cada gráfico pode representar ou não.

## 4. Conceitos-Chave para Provas

### 4.1 Visualização de Dados
- Processo de representar graficamente informações e dados.
- Facilita a compreensão e a interpretação de padrões, tendências e outliers.

### 4.2 Análise Exploratória de Dados
- Envolve a visualização de estatísticas e a identificação de correlações.
- Permite conhecer melhor os dados antes de utilizá-los em projetos.

### 4.3 Gráfico de Barras
- Compara quantidades em diferentes categorias.
- A altura/comprimento da barra indica o valor.

### 4.4 Gráfico de Pizza (Setores)
- Mostra a divisão de um todo em partes.
- Cada fatia representa uma proporção do total.
- Mais indicado quando o número de categorias é pequeno.

> [!CAUTION] OBSERVAÇÃO: 
> - Não confunda a função de cada tipo de gráfico:
>   - Barras: comparação entre categorias.
>   - Pizza: proporção em relação ao todo.
>   - Linhas: variação ao longo do tempo.
>   - Dispersão: relação entre duas variáveis.
>   - Boxplot: identificação de outliers.
> - Gráficos de pizza não devem ser utilizados para muitos dados, pois perdem a clareza.