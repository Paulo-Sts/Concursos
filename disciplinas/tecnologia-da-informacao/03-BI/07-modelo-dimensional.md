# Anotações

# BUSINESS INTELLIGENCE – MODELO DIMENSIONAL (TEORIA)

## 1. Conceitos Fundamentais da Modelagem Dimensional

### 1.1 Definição e Características

- A **modelagem dimensional** é uma técnica de design lógico usada para preparar o esquema de dados que será carregado em um Data Warehouse (DW).
- Projeta bancos de dados especializados em **análise de dados**, criando estruturas **não normalizadas** (diferente do OLTP).
- O modelo é composto por uma **Tabela Fato** central e várias **Tabelas Dimensão** ao redor.

### 1.2 Componentes Principais

- **Tabela Fato:**
    - Armazena as **medidas numéricas** e quantitativas que representam os eventos de negócio (ex: quantidade vendida, valor da venda, lucro).
    - Cada linha corresponde a uma instância de um evento.
    - Contém chaves estrangeiras que se relacionam com as tabelas Dimensão.

- **Tabelas Dimensão:**
    - Contêm os **aspectos descritivos** dos dados, fornecendo o contexto para as medidas da tabela fato.
    - Descrevem o "quem, o quê, quando, onde e como" do negócio.
    - São usadas para **filtrar, agrupar e organizar** as informações nas consultas.
    - Exemplos: Produto, Cliente, Tempo, Localização.
    - São compostas por **hierarquias** (ex: País -> Estado -> Cidade).

## 2. Tipos Especiais de Fatos

### 2.1 Classificação pelo Comportamento de Agregação

- **Fato Aditivo (*Additive Fact*):**
    - Podem ser **somados** livremente em todas as dimensões.
    - São os mais comuns.
    - Exemplo: Valor de venda.

- **Fato Semiaditivo (*Semi-Additive Fact*):**
    - Podem ser somados apenas em **determinadas dimensões**.
    - Exemplo: Saldo de estoque (pode ser somado por produto, mas não ao longo do tempo).

- **Fato Não Aditivo (*Non-Additive Fact*):**
    - **Não podem ser somados** em nenhuma dimensão.
    - Exemplo: Percentual, razão, temperatura.

### 2.2 Outros Conceitos

- **Fato Derivado (*Derived Fact*):**
    - É calculado a partir de outros fatos existentes na tabela.
    - Exemplo: Lucro (Receita - Custo).

- **Dimensões Degeneradas:**
    - Atributos que seriam dimensões, mas, por não terem atributos próprios além de um identificador, são armazenados diretamente na **Tabela Fato**.
    - Exemplo: Número da Nota Fiscal, Código do Pedido.

- **Tabelas Factless (*Factless Fact Table*):**
    - Tabelas de fatos que **não possuem medidas numéricas**. Contêm apenas chaves estrangeiras para as dimensões.
    - Servem para representar a ocorrência de um **evento**.
    - Exemplo: Registro de presença em uma aula.

## 3. Esquemas de Modelagem Dimensional

### 3.1 Esquema Estrela (*Star Schema*)

- **Estrutura:** Uma tabela de fato central conectada a múltiplas tabelas de dimensão **desnormalizadas**.
- **Vantagens:** Simplicidade de entendimento, melhor **desempenho** em consultas.
- **Desvantagens:** Redundância de dados e maior uso de espaço de armazenamento.

### 3.2 Esquema Floco de Neve (*Snowflake Schema*)

- **Estrutura:** As tabelas de dimensão são **normalizadas**, ou seja, são divididas em sub-tabelas.
- **Vantagens:** Otimização do espaço em disco, maior flexibilidade nas mudanças do modelo.
- **Desvantagens:** Maior **complexidade** nas consultas e, consequentemente, pior **desempenho**.

## 4. Cubo de Dados

### 4.1 Definição

- O **Cubo de Dados** é a representação lógica e visual da estrutura de dados multidimensionais de um modelo dimensional.
- Cada **eixo** do cubo representa uma **Dimensão** (ex: Produto, Tempo, Loja).
- As **células** internas do cubo contêm os valores das **Medidas** (Fatos) correspondentes ao cruzamento das dimensões.
- As **hierarquias** das dimensões permitem navegar por diferentes níveis de detalhe, da visão mais sumarizada à mais detalhada.