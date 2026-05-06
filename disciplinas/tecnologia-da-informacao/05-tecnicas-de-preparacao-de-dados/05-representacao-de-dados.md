# Anotações

# REPRESENTAÇÃO DE DADOS NUMÉRICOS, TEXTUAIS E ESTRUTURADOS

## 1. Representação de Dados Numéricos

### 1.1 Conceito e Formas de Armazenamento

- **Dados Numéricos:** São valores quantitativos expressos em forma de números (inteiros, decimais).
- **Formas de Representação Base:**
    - **Inteiros:** Representação decimal (base 10), binária (base 2), hexadecimal (base 16).
    - **Ponto Flutuante:** Notação decimal (ex: 3.14) ou notação científica (ex: 6.022 × 10^23).
    - **Frações:** Formato de fração numerador/denominador.
    - **Porcentagens:** Notação percentual (ex: 50%).

### 1.2 Visualização em Projetos de Business Intelligence (BI)

- Gráficos de **Barra**.
- Gráficos de **Linha**.
- Gráficos de **Pizza**.
- **Tabelas** de dados.
- **Indicadores de performance** (KPIs).
- ***Dashboards* interativos**.

### 1.3 Representação em Projetos de Machine Learning (ML)

- **Matriz NumPy:** Estrutura onde cada linha é uma instância de dados e cada coluna é um atributo.
- ***DataFrame* do Pandas:** Estrutura de dados tabular com colunas rotuladas, semelhante a uma tabela de banco de dados ou planilha Excel. É a estrutura padrão para *datasets*.
- **Esparsidade:** Para dados com muitos zeros, usam-se matrizes esparsas (ex: `SciPy`) que armazenam apenas os valores não nulos e suas coordenadas, economizando espaço.
- **Normalização e Padronização:** Etapas essenciais de pré-processamento antes de fornecer os dados ao algoritmo.

## 2. Representação de Dados Textuais

### 2.1 Conceito e Aplicações

- **Dados Textuais:** Informações expressas em formato de texto (palavras, frases, documentos), armazenados como texto simples, HTML, PDF, etc.
- **Análise:** Envolve técnicas de **Processamento de Linguagem Natural (PLN)** para extrair informações significativas.

### 2.2 Técnicas de Vetorização (Transformação em Números)

- **Vetorização Baseada em Frequência:**
    - ***Bag of Words* (Saco de Palavras):** Cria um vocabulário e representa cada documento como um vetor com a **contagem** de ocorrências de cada palavra.
    - **TF-IDF:** Calcula um **peso** para cada palavra com base em sua frequência no documento e sua raridade em todo o conjunto de documentos.
- **Representação por N-gramas:** Contagem ou codificação de sequências contíguas de `n` palavras.
- **Incorporação de Palavras (*Word Embeddings*):**
    - ***Word2Vec* e GloVe:** Técnicas que mapeiam palavras para vetores de números reais densos, capturando **relações semânticas e contextuais**.

### 2.3 Visualização em Projetos de BI

- **Tabelas textuais.**
- ***Word Cloud* (Nuvem de Palavras):** Destaca visualmente as palavras mais frequentes.
- ***Word Network* (Rede de Palavras):** Mostra as conexões entre palavras.
- **Análise de Sentimento:** Classifica a polaridade de um texto (Positivo, Negativo, Neutro) com base em seu conteúdo.

### 2.4 Representação em Projetos de ML

- **Conversão *One-Hot Encoding*:**
    - Uma abordagem simples para converter texto em vetor.
    - Cada palavra única é mapeada para um vetor binário do tamanho do vocabulário: `1` se a palavra estiver presente, `0` caso contrário.