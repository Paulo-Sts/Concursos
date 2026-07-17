# Anotações

# TRANSFORMAÇÃO DE DADOS

## 1. Conceito e Justificativas

### 1.1 O que é Transformação de Dados

- A **transformação de dados** é o processo de converter um dado de seu formato original para outro formato ou tipo. Envolve alterar a estrutura, o valor ou a representação de um atributo.

### 1.2 Por que Transformar Dados

- **Organização:** Consolidar ou estruturar dados (ex: unificar várias colunas em uma).
- **Pré-validação e Limpeza:** Identificar e tratar problemas como dados faltantes antes da modelagem.
- **Preparação para Modelagem:**
    - Adaptar os dados a técnicas que exigem tipos específicos de *input* (ex: muitos algoritmos de ML só aceitam dados numéricos).
    - Melhorar a *performance* de modelos que são sensíveis à escala dos valores numéricos, exigindo normalização.

## 2. Tipos de Transformação

### 2.1 De Simbólico (Categórico) para Numérico

- **Atributo Simbólico com Dois Valores (Binário):**
    - Converter diretamente para um atributo binário numérico (0 ou 1).

- **Atributo Nominal (sem ordem):**
    - ***One-Hot Encoding* (Codificação One-Hot):** É a técnica mais comum. Cada valor distinto do atributo categórico se torna uma **nova coluna binária** (0 ou 1). Ex: A coluna "Cor" com valores "Azul", "Verde", "Vermelho" se transforma em três colunas: `Cor_Azul`, `Cor_Verde`, `Cor_Vermelha`, com valores 1 ou 0.

- **Atributo Ordinal (com ordem):**
    - **Codificação Ordinal (Label Encoding):** Mapear cada categoria para um **valor inteiro ordenado** (ex: "Ruim"=0, "Bom"=1, "Ótimo"=2).
    - **Codificação Termômetro ou Código Cinza:** Codificações que representam a ordem de uma forma mais complexa, atribuindo códigos sequenciais.

### 2.2 De Numérico para Simbólico (Discretização)

- **Discretização:** Transformar uma escala numérica contínua em um número finito de categorias ou intervalos.
- **Processo:**
    1.  Ordenar os valores numéricos.
    2.  Definir intervalos (classes) (ex: "Baixa", "Média", "Alta").
    3.  Mapear cada valor para a classe correspondente.

### 2.3 De Numérico para Numérico

- **Reescala (Normalização Min-Max):**
    - `Valor Novo = (Valor Atual – Menor Valor) / (Maior Valor – Menor Valor)`
    - Transforma os dados para um intervalo, geralmente [0, 1].

- **Padronização (Z-Score):**
    - `Valor Novo = (Valor Atual – Média) / Desvio Padrão`
    - Transforma os dados para terem média 0 e desvio padrão 1.

- **Tradução:**
    - Aplicar funções para converter a unidade ou o significado do dado.
    - Exemplos: Converter data de nascimento em idade; converter temperatura de Celsius para Fahrenheit.

## 3. Análise de Questões de Concurso

### 3.1 Etapa de Ocorrência da Imputação (NC-UFPR/PREF. CURITIBA/2019)

- **Enunciado:** "O método de 'imputação de dados' para suprir a ausência de valores acontece na etapa de transformação dos dados."
- **Gabarito:** **ERRADO**.
- **Análise:** A imputação (tratamento de dados faltantes) é uma atividade de **limpeza** e **pré-processamento**, que ocorre antes ou como parte da preparação, mas não é classificada estritamente como uma transformação de tipo/formato dos dados. A transformação está mais ligada a mudar a natureza do dado (ex: numérico para categórico).

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (NC-UFPR/Pref. Curitiba) | **E** | Imputação = etapa de limpeza/pré-processamento, não de transformação. |