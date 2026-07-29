# Tipos de Aprendizado de Máquina

## 1. Categorias Principais de Tarefas
- O conteúdo referente aos tipos de aprendizado é identificado como o tema mais cobrado em provas sobre machine learning.
- As tarefas resolvidas por meio do aprendizado de máquina dividem-se em duas grandes categorias:
- Análise descritiva ⟶ os padrões e estruturas são identificados diretamente nas bases de dados.
- Análise preditiva ⟶ o sistema é desenvolvido para realizar a previsão de um resultado ou valor futuro.

## 2. Aprendizado Supervisionado
- Caracteriza-se pelo uso de conjuntos de dados que contêm exemplos rotulados, ou seja, as saídas ou respostas já são conhecidas.
- O modelo aprende a prever a saída (rótulo ou classe) a partir dos atributos de entrada fornecidos.
- O objetivo central é prever um rótulo categórico ou um valor numérico para novos dados que o sistema ainda não processou.
- Esta categoria realiza essencialmente a análise preditiva.

### 2.1 Classificação
- Consiste na tarefa de prever uma variável categórica ou rótulo.
- Envolve a minimização do erro entre o valor que o modelo previu e o valor real presente no dataset.
- Exemplo: uma câmera que captura biometria e classifica se o indivíduo está ou não em dia com a mensalidade da academia.
- Exemplo: identificação de criminosos através de filmagens de ruas da cidade.

### 2.2 Regressão
- Consiste na tarefa de prever um valor numérico contínuo.
- Exemplo: previsão da temperatura de um determinado dia com base em dados climáticos do dia anterior.
- Exemplo: estimativa de quantos anos de pena serão aplicados a um réu.

> [!CAUTION] OBSERVAÇÃO: 
> - A identificação de transações fraudulentas é tecnicamente uma tarefa de classificação (fraude ou não fraude) e não de regressão, embora algumas questões de prova possam tentar confundir esses conceitos.

## 3. Aprendizado Não Supervisionado
- Caracteriza-se pelo fato de o modelo não receber rótulos de saída durante o treinamento.
- O sistema busca identificar estruturas, padrões, agrupamentos ou relacionamentos ocultos nos dados por conta própria.
- Esta categoria realiza essencialmente a análise descritiva, também conhecida como descoberta de conhecimento.

### 3.1 Clusterização ou Agrupamento
- Consiste em agrupar elementos que possuem características semelhantes entre si.
- A inteligência artificial verifica a similaridade dos dados e mantém registros parecidos no mesmo grupo, enquanto dados diferentes ficam em grupos distintos.
- Exemplo: divisão automática de alunos em grupos de acordo com suas notas escolares.

### 3.2 Regras de Associação
- Consiste em descobrir relações frequentes e pontos que coocorrem entre atributos em grandes bases de dados.
- Exemplo: descobrir vendas casadas em um supermercado, como o fato de que sempre que se compra banana, também se compra laranja.

### 3.3 Redução de Dimensionalidade
- Consiste em reduzir o número de colunas (dimensões) do dataset.
- O objetivo é simplificar o conjunto de dados para reduzir o tempo de treinamento e eliminar atributos que não são relevantes para o aprendizado.

| TIPO DE APRENDIZADO | CARACTERÍSTICA DOS DADOS | TAREFAS PRINCIPAIS |
|---|---|---|
| Supervisionado | Dados rotulados com saídas conhecidas | Classificação e regressão |
| Não supervisionado | Dados sem rótulos ou classes prévias | Clusterização, associação e redução de dimensionalidade |

> [!CAUTION] OBSERVAÇÃO: 
> - A técnica de clustering apenas separa os dados em grupos por similaridade; ela não atribui categorias ou rótulos nominais aos grupos, o que seria uma tarefa de classificação.

> [!TIP] DICAS: 
> - Para construir um modelo eficiente, é fundamental selecionar apenas as colunas (atributos) que possuam relação direta com o rótulo que se deseja prever, descartando dados irrelevantes.