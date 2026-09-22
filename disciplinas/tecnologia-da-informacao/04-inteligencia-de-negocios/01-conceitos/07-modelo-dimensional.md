# Modelo Dimensional

## 1. Introdução
- A modelagem dimensional é o método para preparar o esquema de dados que serão carregados no Data Warehouse (DW).
- Diferentemente de modelos com várias tabelas, o modelo dimensional possui uma tabela central chamada tabela fato, que representa o assunto principal da análise.
- A tabela fato contém várias dimensões, que são representadas por chaves estrangeiras.
- As dimensões fornecem o contexto descritivo para os dados mensurados na tabela fato.
- Este modelo é projetado especificamente para bancos de dados voltados à análise de dados.
- Uma característica fundamental é a criação de estruturas não normalizadas para otimizar a performance de consultas.

## 2. Dimensões e Tabela de Fatos

### 2.1 Dimensões
- As dimensões são os aspectos descritivos dos dados.
- Exemplos comuns de dimensões incluem produtos, clientes, tempo e localização.
- Sua função principal é filtrar, agrupar e organizar as informações para a análise.
- São compostas por hierarquias que permitem a análise em diferentes níveis de detalhe (ex: ano, mês, dia para a dimensão tempo).

### 2.2 Tabela de Fatos
- A tabela de fatos contém as medidas numéricas que representam os eventos de negócio.
- Exemplos de medidas são vendas, lucro e quantidade de produtos.
- Cada linha na tabela fato representa uma instância única de um evento de negócio.
- Possui chaves estrangeiras que se relacionam com as tabelas de dimensão para permitir a consulta e agregação dos dados.

### 2.3 Dimensões Degeneradas
- São atributos descritivos que poderiam ser transformados em dimensões, mas são mantidos na própria tabela de fatos.
- Normalmente são chaves naturais ou valores descritivos com poucos atributos adicionais.
- Não possuem informação significativa além do seu valor individual, não justificando uma tabela de dimensão separada.

### 2.4 Tabelas Factless
- São tabelas de fatos que não possuem medidas numéricas.
- Contêm apenas chaves estrangeiras para as dimensões, registrando a ocorrência de um evento.
- São úteis para registrar eventos como presença em uma aula ou registro de um atendimento, onde a contagem de ocorrências já é a informação desejada.

### 2.5 Tipos de Fatos
- Os fatos são classificados de acordo com a possibilidade de serem agregados numericamente.
- Fato aditivo (Additive Fact):
  - Podem ser somados ou agregados numericamente em qualquer dimensão.
  - São os tipos mais comuns de medidas.
  - Utilizados em operações de agregação como somas, médias e totalizações.
- Fato semiaditivo (Semi-Additive Fact):
  - Podem ser somados apenas em determinados níveis de agregação.
  - Por exemplo, podem ser somados por produto, mas não faz sentido somá-los por data, como ocorre com saldos bancários.
- Fato não aditivo (Non-Additive Fact):
  - Não podem ser somados ou agregados numericamente, como é o caso de razões ou porcentagens.
- Fato derivado (Derived Fact):
  - São calculados a partir de fatos existentes ou por meio de cálculos mais complexos.

> [!TIP] DICAS: 
> - Para identificar o tipo de fato, pergunte-se: "Faz sentido somar esta medida em todas as dimensões?". Se sim, é aditivo. Se apenas em algumas, é semiaditivo. Se em nenhuma, é não aditivo.

## 3. Esquemas

### 3.1 Esquema Estrela
- É um modelo onde uma tabela de fatos central está diretamente ligada a várias tabelas de dimensão.
- Vantagens:
  - Simplicidade do modelo para usuários e ferramentas de BI.
  - Alto desempenho em consultas devido ao menor número de junções.
  - Maior uso de espaço de armazenamento (já que é desnormalizado).
- Desvantagens:
  - Redundância de dados nas tabelas de dimensão.
  - Maior complexidade e custo para manter as atualizações dos dados.

#### 3.1.1 Exemplos do Modelo Estrela
- Tabela de Fatos (Vendas):
  - Chaves estrangeiras:
    - ProdutoID (referencia a dimensão Produto);
    - TempoID (referencia a dimensão Tempo);
    - LocalizacaoID (referencia a dimensão Localizacao).
  - Medidas:
    - QuantidadeVendida;
    - ValorVenda.
- Tabela de Dimensão (Produto):
  - ProdutoID (chave primária);
  - NomeProduto;
  - Categoria;
  - Fabricante;
  - Outros atributos relevantes.
- Tabela de Dimensão (Tempo):
  - TempoID (chave primária);
  - Data;
  - Ano;
  - Mês;
  - Dia.
- Tabela de Dimensão (Localizacao):
  - LocalizacaoID (chave primária);
  - País;
  - Estado;
  - Cidade;
  - Outros atributos relevantes.

### 3.2 Esquema Floco de Neve
- É uma variação do esquema estrela onde as tabelas de dimensão são normalizadas em múltiplas tabelas menores.
- Vantagens:
  - Normalização dos dados, reduzindo a redundância.
  - Maior flexibilidade para mudanças no modelo, pois as alterações são mais localizadas.
  - Otimização do espaço em disco, pois elimina dados duplicados.
- Desvantagens:
  - Aumento da complexidade do modelo para os usuários.
  - Pior desempenho em consultas devido ao maior número de junções entre tabelas.

> [!CAUTION] OBSERVAÇÃO: 
> - Para transformar um modelo estrela em um modelo floco de neve, basta aplicar o processo de normalização nas tabelas de dimensão.

## 4. Cubo de Dados
- O cubo de dados representa a estrutura lógica de dados multidimensionais.
- Sua função é organizar as informações em um formato que seja de fácil compreensão e análise para o usuário.
- As informações de um modelo dimensional podem ser visualizadas como um cubo com três ou mais dimensões.
- Cada eixo do cubo representa uma dimensão do modelo.
- As células do cubo contêm os valores das medidas correspondentes.
- As hierarquias permitem a organização das dimensões em diferentes níveis de detalhe para análises drill-down ou roll-up.