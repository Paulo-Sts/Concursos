# Visualização de Dados 5

## 1. Funções da Visualização de Dados
- A visualização de dados possui diversas funções que atendem a diferentes objetivos de análise e apresentação.
- Cada função é melhor atendida por métodos específicos de visualização, que utilizam elementos visuais como posição, tamanho, cor, forma e movimento para transmitir a informação.

### 1.1 Fazer Comparações
- Métodos que ajudam a mostrar diferenças ou semelhanças entre variáveis.
- Exemplos: gráfico de barras, gráfico de linha, gráfico de radar.
- O gráfico de barras é eficaz para comparar categorias distintas; o gráfico de linha é ideal para tendências ao longo do tempo; o gráfico de radar compara múltiplas variáveis em um mesmo eixo.

### 1.2 Mostrar Proporções entre Valores
- Métodos que usam tamanho ou área para mostrar diferenças ou semelhanças entre valores ou de partes para um todo.
- Exemplos: mapas de bolhas, nuvem de palavras.
- Mapas de bolhas utilizam o tamanho das bolhas para representar magnitudes; nuvem de palavras destaca frequência de termos pelo tamanho da fonte.

### 1.3 Mostrar Conexões
- Métodos que mostram relacionamentos e conexões entre os dados ou correlações entre duas ou mais variáveis.
- Exemplo: Diagrama de Venn.
- O Diagrama de Venn ilustra interseções e diferenças entre conjuntos de dados.

### 1.4 Mostrar Hierarquias
- Métodos que mostram como os dados ou objetos são classificados e ordenados juntos em uma organização ou sistema.
- Exemplos: organograma, mapa de árvore.
- O organograma representa hierarquia organizacional; o mapa de árvore exibe dados hierárquicos por meio de retângulos aninhados.

### 1.5 Mostrar Conceitos
- Métodos que ajudam a explicar e mostrar ideias ou conceitos.
- Exemplos: fluxograma, mapa mental.
- Fluxogramas ilustram sequências lógicas; mapas mentais organizam ideias de forma radial.

### 1.6 Mostrar Localizações
- Métodos que mostram dados sobre regiões geográficas.
- Exemplo: mapa coroplético, mapa de bolhas, mapa de conexões.
- O mapa coroplético utiliza sombreamento para representar variações regionais; o mapa de bolhas sobrepõe círculos proporcionais a valores; o mapa de conexões traça rotas ou fluxos entre localizações.

### 1.7 Mostrar Relações Parte/Todo
- Métodos que mostram parte (ou partes) de uma variável em relação ao seu total, frequentemente usado para mostrar como algo é dividido.
- Exemplos: gráfico de pizza, gráfico de rosca, mapa de árvore.
- O gráfico de pizza e o gráfico de rosca (donut) são eficazes para proporções simples; o mapa de árvore é útil para hierarquias com partes.

### 1.8 Mostrar Distribuição
- Métodos que exibem frequência, como os dados se espalham em um intervalo ou são agrupados.
- Exemplos: gráfico de caixa, gráfico de densidade, histograma, gráfico de violino.
- O histograma agrupa dados em intervalos (bins) para mostrar frequência; o gráfico de densidade suaviza a distribuição; o gráfico de caixa (box plot) resume a distribuição por meio de quartis e identifica outliers; o gráfico de violino combina box plot com densidade de probabilidade.

> [!CAUTION] OBSERVAÇÃO:
> - O gráfico de caixa (box plot) é uma representação gráfica de dados numéricos a partir de seus quantis, permitindo a detecção visual eficaz de outliers.

### 1.9 Mostrar Como as Coisas Funcionam
- Métodos que ilustram como um objeto ou sistema funciona.
- Exemplos: fluxograma, diagrama de Sankey.
- O fluxograma mostra a sequência de etapas de um processo; o diagrama de Sankey representa fluxos de energia, materiais ou custos.

### 1.10 Apresentar Processos e/ou Métodos
- Métodos que ajudam a explicar processos ou métodos.
- Exemplos: fluxograma, gráfico de Gantt, diagrama de Sankey.
- O gráfico de Gantt é utilizado para planejamento e controle de projetos, mostrando a duração e sobreposição de tarefas.

### 1.11 Mostrar Movimentos
- Métodos úteis para mostrar dados de movimento ou o fluxo de dados.
- Exemplos: mapa de conexões, diagrama de Sankey.
- Mapas de conexões podem representar rotas de transporte ou migração.

### 1.12 Revelar Padrões
- Métodos que podem revelar formas ou padrões nos dados para dar significado a eles.
- Exemplos: gráfico de área, gráfico de barras, mapa de pontos.
- O gráfico de área é útil para acumulações ao longo do tempo; o mapa de pontos (scatter plot) mostra relações entre duas variáveis.

### 1.13 Mostrar Distância dentro dos Dados
- Métodos que exibem as variações entre os limites superior e inferior de uma escala.
- Exemplos: gráfico de caixa, gráfico de violino.
- Ambos os gráficos mostram a dispersão e a amplitude dos dados.

### 1.14 Mostrar Variação de Dados ao Longo do Tempo
- Métodos que mostram dados ao longo de um período de tempo para encontrar tendências ou mudanças.
- Exemplos: gráfico de velas, gráfico de Gantt, gráfico de linha.
- O gráfico de velas (candlestick) é comum em análise financeira; o gráfico de linha é amplamente utilizado para séries temporais.

### 1.15 Analisar Textos
- Métodos que revelam padrões e insights de um corpo de texto.
- Exemplo: nuvem de palavras.
- A nuvem de palavras (word cloud) destaca termos mais frequentes em um conjunto de textos.

## 2. Princípios e Boas Práticas em Visualização de Dados

### 2.1 Ênfase na Informação
- O critério técnico para a utilização da cor em gráficos numéricos deve priorizar a ênfase na informação a ser destacada pelo gráfico.
- A cor deve ser usada para chamar atenção para os dados mais relevantes, não apenas para fins estéticos ou para combinar com uma paleta predefinida.
- A harmonia e a estética são secundárias em relação à clareza e à transmissão do conhecimento.

### 2.2 Impacto Visual e Relevância
- Um dos princípios fundamentais das técnicas de visualização de dados é o impacto visual.
- As informações com maior relevância devem ser facilmente distinguidas das informações de menor relevância, utilizando elementos visuais como cor, tamanho e posição de forma intencional.

### 2.3 Ferramentas de Visualização
- Kibana: software de visualização de dados, frequentemente utilizado em conjunto com o Elasticsearch.
- Elasticsearch: banco de dados NoSQL que possui mecanismos de pesquisa internos.
- PowerBI: ferramenta moderna utilizada para gerar dashboards de visualização de dados oriundos de fontes separadas, facilitando a integração de conteúdos armazenados em arquivos de formatos diferentes.

### 2.4 Mapas Coropléticos
- Visualização que utiliza mapas com sombreamento, tonalidades ou padrões para exibir como um valor difere na proporção em uma localização geográfica ou região.
- Exibe rapidamente diferenças relativas, com sombreamento que varia de claro (menos frequente/inferior) para escuro (mais frequente/superior).
- É uma ferramenta eficaz para dados demográficos, econômicos ou de indicadores por região.

> [!TIP] DICAS:
> - Para comparar categorias, prefira gráficos de barras ou colunas.
> - Para mostrar evolução ao longo do tempo, o gráfico de linha é a escolha mais comum e intuitiva.
> - Ao utilizar mapas, certifique-se de que a escala de cores seja clara e a legenda esteja visível.
> - Em gráficos de pizza, limite o número de fatias para evitar poluição visual; use gráficos de rosca para uma alternativa mais moderna.
> - O box plot é uma ferramenta poderosa para identificar outliers e comparar distribuições entre grupos.

> [!CAUTION] OBSERVAÇÃO:
> - O gráfico de caixa (box plot) também é conhecido como "gráfico de caixa e bigodes" (box-and-whisker plot).
> - Em visualização de dados, a prioridade é sempre a clareza da informação, e não a estética ou a harmonização com uma paleta de cores predefinida.
> - Ferramentas como PowerBI e Kibana são cobradas em concursos, com ênfase em suas funcionalidades básicas e casos de uso.