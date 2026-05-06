# Anotações

# ATRIBUTOS - CIÊNCIA DE DADOS

## 1. Conceitos Fundamentais

### 1.1 Definições

- **Dataset:** Conjunto de dados bem definido, com uma estrutura rígida. É a "tabela" final que alimenta o modelo de aprendizado de máquina.
- **Atributo (ou Feature):** Cada uma das **colunas** de um *dataset*, que descreve uma característica do objeto que se quer aprender.
- **Exemplo (ou Instância/Ponto):** Cada uma das **linhas** de um *dataset*, que fornece os dados de uma observação específica.
- **Classe (ou Target/Rótulo):** Em problemas de classificação, é a coluna especial que se deseja prever (ex: "Concede Crédito? Sim/Não").

### 1.2 Problemas com Atributos (antes da modelagem)

Antes de modelar, é preciso tratar o *dataset* para garantir a qualidade. Atributos podem ser removidos ou transformados por:
- Terem muitos **dados faltantes**.
- Serem **outliers**.
- Apresentarem **alta correlação** entre si (redundância).
- Haver **muitos atributos** (problema de dimensionalidade).

## 2. Tipos de Atributos

### 2.1 Dados Qualitativos (Categóricos)

| TIPO | DEFINIÇÃO | EXEMPLO |
| :--- | :--- | :--- |
| **Nominal** | Categorias sem uma ordem natural. | Cor de cabelo, sexo (M/F), estado civil. |
| **Ordinal** | Categorias onde é possível estabelecer uma **ordem**, mas não se pode **quantificar a diferença** entre elas. | Escolaridade (Fundamental, Médio, Superior), Classe social (Baixa, Média, Alta). |

### 2.2 Dados Quantitativos (Numéricos)

| TIPO | DEFINIÇÃO | EXEMPLO |
| :--- | :--- | :--- |
| **Discreto** | Valores numéricos que pertencem a um conjunto **finito ou enumerável** (geralmente números inteiros). | Número de filhos, Quantidade de carros. |
| **Contínuo** | Valores numéricos que podem assumir **qualquer valor** em um intervalo (números reais). | Temperatura, altura, peso, salário. |

### 2.3 Atributos Binários

- **Definição:** Um caso especial de atributo nominal que possui **apenas duas categorias** possíveis (ex: 0 ou 1, Verdadeiro ou Falso, Sim ou Não).

## 3. Medidas Descritivas de Atributos

- **Frequência:** Proporções entre os valores.
- **Localização ou Tendência Central:** Média, mediana, moda.
- **Dispersão ou Espalhamento:** Desvio padrão, variância.
- **Distribuição ou Formato:** Análise da distribuição dos dados.

## 4. Análise de Questões de Concurso

### 4.1 Definição de Atributo Ordinal (CESPE/ME/2020)

- **Enunciado:** "Um atributo é denominado ordinal quando as variáveis podem ser colocadas em ordem, mas não é possível quantificar a diferença entre os resultados."
- **Gabarito:** **CERTO**.
- **Análise:** É a definição canônica e precisa de um atributo ordinal. Por exemplo, sabe-se que "Alta" é mais que "Média", mas não se pode dizer que a diferença entre elas é uma quantidade numérica definida.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/ME) | **C** | Atributo ordinal = tem ordem, mas não se quantifica a diferença. |