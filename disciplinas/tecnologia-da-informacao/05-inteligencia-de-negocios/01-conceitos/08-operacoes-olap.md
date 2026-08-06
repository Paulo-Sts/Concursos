# Operações OLAP

## 1. Conceitos Fundamentais
- Conjunto de operações para análise interativa de dados multidimensionais em um modelo dimensional.
- Permite explorar e visualizar dados de diferentes perspectivas, realizar agregações, filtrar informações e navegar entre diferentes níveis de detalhe.
- Granularidade: quanto maior a granularidade de um dado, mais detalhado ele se encontra.

> [!TIP] DICAS: 
> - Granularidade é o nível de detalhe dos dados.
> - Quanto mais detalhado, menor a granularidade (pegadinha comum em provas).
> - Quanto mais resumido/agregado, maior a granularidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Em data warehouse, o conceito de granularidade refere-se ao nível de detalhe ou resumo existente em uma unidade de dados.
> - Cuidado: quanto mais detalhes, menor o nível de granularidade (não maior, como algumas bancas tentam confundir).

## 2. Operações OLAP

### 2.1 Roll-up (Drill-Up)
- Navega de um nível de detalhe inferior para um nível hierarquicamente superior.
- Exemplo: passar de dados de vendas diárias para dados de vendas mensais ou anuais.
- Combina células de uma ou mais dimensões para atingir um nível maior de generalização.
- Efeito: diminui o detalhamento (menor granularidade).

### 2.2 Drill-down (Roll-Down)
- Navega de um nível hierarquicamente superior para um nível de detalhe inferior.
- Exemplo: passar de dados de vendas anuais para dados de vendas trimestrais ou mensais.
- Efeito: aumenta o nível de detalhe (menor granularidade).
- Permite analisar dados em níveis de agregação progressivamente mais detalhados.

> [!TIP] DICAS: 
> - Roll-up = subir na hierarquia = resumir = menor detalhe.
> - Drill-down = descer na hierarquia = detalhar = maior detalhe.

### 2.3 Slice and Dice
- Permite filtrar os dados multidimensionais com base em critérios específicos.

#### 2.3.1 Slice
- "Corta" uma fatia do cubo de dados.
- Seleciona um subconjunto de valores em uma ou mais dimensões.
- Exemplo: analisar apenas um estado específico.

#### 2.3.2 Dice
- "Corta" um subcubo de dados.
- Seleciona um subconjunto de valores em várias dimensões simultaneamente.
- Ajuda a restringir os dados e obter informações específicas.
- Exemplo: analisar um estado específico, em um trimestre específico, para um produto específico.

### 2.4 Pivot (Rotate)
- Permite reorganizar os dados multidimensionais, girando o cubo de dados ao longo de um eixo específico.
- Proporciona uma visualização diferente dos dados e facilita a análise de diferentes perspectivas.
- Rotaciona os eixos de um determinado cubo, provendo uma visão alternativa dos dados.
- Exemplo: trocar de posição os eixos tempo e região para obter uma visão alternativa.

> [!CAUTION] OBSERVAÇÃO: 
> - Pivot não altera o nível de detalhamento, apenas reorganiza a visualização dos dados.

### 2.5 Drill Across
- Realiza saltos entre os níveis de uma mesma dimensão.
- Permite mover-se lateralmente de um conjunto de dados para outro, mantendo-se no mesmo nível de detalhe.
- Exemplo: analisar dados de produção de celulares e pagers, mantendo o mesmo nível de detalhe entre as dimensões.

### 2.6 Drill Through
- Mudança de dimensão durante uma consulta.
- Permite ao analista mudar o foco dimensional, passando de uma análise em uma dimensão para outra.
- Exemplo: após analisar dados de abastecimento por bairros, passar a analisar a informação por ano.

> [!TIP] DICAS: 
> - Roll-up e Drill-down são operações que alteram o nível de detalhamento.
> - Slice, Dice, Pivot, Drill Across e Drill Through não alteram a granularidade.
> - Drill Across mantém o mesmo nível de detalhe.
> - Drill Through permite mudança de dimensão durante a consulta.

## 3. Granularidade e Hierarquia
- Níveis hierárquicos comuns: dia > mês > trimestre > ano.
- Quanto mais abaixo na hierarquia, menor a granularidade (mais detalhes).
- Quanto mais acima na hierarquia, maior a granularidade (mais resumido).

> [!CAUTION] OBSERVAÇÃO: 
> - Não confundir: drill-down aumenta o detalhamento, mas a granularidade é menor (pois os dados são mais detalhados).
> - Roll-up diminui o detalhamento e a granularidade é maior (dados mais agregados).