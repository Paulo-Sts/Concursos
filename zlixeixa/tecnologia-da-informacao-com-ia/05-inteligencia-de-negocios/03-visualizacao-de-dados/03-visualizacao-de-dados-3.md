# Visualização de Dados 3

## 1. Tipos de Gráficos

### 1.1 Histograma
- Gráfico de barras que mostra a distribuição de uma variável contínua.
- As barras representam faixas de valores e a altura indica a frequência de ocorrência.
- Utilizado para visualizar a distribuição de dados, como a distribuição de idades em uma população.
- O formato do histograma ajuda a identificar a distribuição dos dados (normal, enviesada, uniforme) e os intervalos onde os valores são mais frequentes.

> [!TIP] DICAS: 
> - O histograma é um gráfico de barras, mas com barras coladas (sem espaços), pois representa uma variável contínua.

> [!CAUTION] OBSERVAÇÃO: 
> - O histograma tem uma variável x e uma frequência (quantidade de dados em cada intervalo).
> - Não confundir com gráfico de barras (que representa variáveis categóricas).

## 2. Boas Práticas para a Criação de Visualizações

### 2.1 Escala dos Eixos
- Deve ser proporcional aos dados.
- Escalas não proporcionais podem distorcer a interpretação visual dos dados.
- Evite truncar os eixos, especialmente no caso de gráficos de barras, para não exagerar ou minimizar a diferença entre as categorias.
- Boa prática: iniciar o eixo y sempre com zero, com o valor mínimo possível.
- A omissão do zero e a ausência do eixo vertical são inadequações que podem levar a erro de interpretação.

> [!CAUTION] OBSERVAÇÃO: 
> - Gráficos em três dimensões devem ser utilizados apenas quando há três dimensões a representar, o que exclui gráficos em pizza (pois representam apenas uma variável/dimensão).

### 2.2 Margens de Erro
- Certifique-se de que as séries estejam claramente distinguíveis através de cores, texturas ou marcadores.
- Garanta que as legendas sejam claras.

### 2.3 Ênfase em Informações Específicas
- Use cores, negrito ou marcadores de destaque para evidenciar a informação sem distorcer o restante dos dados.
- Não pode ser escondido o que não se pretende mostrar.
- Deve-se destacar o que é mais importante.
- Para destacar uma barra ou fatia específica, use uma cor ou tonalidade diferente.
- Evite o uso excessivo de destaques, pois pode causar confusão.
- A ênfase deve ser sutil, permitindo que o resto dos dados também seja interpretado corretamente.

### 2.4 Diretrizes Gerais
- A escala dos gráficos pode distorcer as informações, então é importante ter atenção ao construir gráficos comparativos.
- A fonte dos dados sempre deve ser verificada para determinar sua confiabilidade.
- É recomendada a não utilização de dois eixos y.
- Gráficos em pizza não são recomendados sempre que possível, pois há problemas de dimensionamento das participações em visualizações em duas dimensões.

## 3. Distinção entre Ferramentas de Qualidade

### 3.1 Fluxograma
- Ferramenta de qualidade adequada para ilustrar a sequência das etapas de um processo.

### 3.2 Gráfico de Dispersão
- Mostra o que acontece com determinada variável quando a outra muda, a fim de que se avaliem possíveis relações de causa e efeito.
- Retrata uma técnica gráfica usada para encontrar e mostrar relações entre dois conjuntos de dados associados que ocorrem em pares.
- As relações entre os conjuntos de dados são inferidas pelo formato das nuvens de pontos formados.

### 3.3 Gráfico de Linhas
- Mais adequado para acompanhar a evolução de uma variável ao longo do tempo.

### 3.4 Gráfico de Barras
- Classifica os dados de acordo com o valor de várias categorias.

> [!CAUTION] OBSERVAÇÃO: 
> - Não existe "série temporal" como tipo de gráfico; utiliza-se um gráfico de linhas para representar uma série temporal.
> - Boxplot (diagrama de caixa) é utilizado em forma de caixa para identificar outliers.
> - Gráfico de cascata não existe como visualização gráfica padrão.