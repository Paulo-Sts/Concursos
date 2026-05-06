# Anotações

# TRATAMENTO DE DADOS – TRATAMENTO DE OUTLIERS

## 1. Conceito e Tipos de Outliers

### 1.1 O que é um Outlier

- Um **outlier** (valor atípico ou anomalia) é uma observação que se diferencia tanto das demais que levanta suspeitas de que foi gerada por um mecanismo distinto.
- **Problema Central:** *Outliers* prejudicam modelos de aprendizado de máquina, distorcendo a análise e gerando ruídos.

### 1.2 Classificação dos Outliers

- **Quanto à Observação:**
    - **Univariado:** Detectado ao analisar a distribuição de uma única variável (ex: uma altura de 3 metros).
    - **Multivariado:** Detectado no espaço "n-dimensional", analisando a relação entre várias variáveis (ex: um salário baixíssimo para alguém com 20 anos de experiência, o que não é um outlier em cada coluna isolada, mas é na combinação).

- **Quanto à Natureza (Critério de Decisão):**
    - **Outlier Natural:** Um valor extremo, porém **verdadeiro e consistente** com o fenômeno (ex: um médico recém-formado com renda altíssima por ser um *influencer*). **Deve ser mantido** no *dataset*.
    - **Outlier Artificial (Erro):** Um valor extremo causado por um **erro** (digitação, amostragem, processamento). **Deve ser removido** ou tratado.

## 2. Técnicas de Identificação (Detecção)

### 2.1 Métodos Universais

- **Observação Direta:** Análise manual do conjunto de dados.
- **Métodos Estatísticos:**
    - **Z-Score:** Valores muito distantes da média (ex: Z-Score > 2.5 ou < -2.5) são fortes candidatos a *outliers*.
    - **Intervalo Interquartil (IQR):** Um valor é considerado *outlier* se estiver **acima do Limite Superior** (Terceiro Quartil + 1,5 * IQR) ou **abaixo do Limite Inferior** (Primeiro Quartil - 1,5 * IQR).

### 2.2 Métodos Gráficos

- **Box-Plot (Diagrama de Caixa):** É a ferramenta visual mais eficaz para identificar *outliers*, pois os plota explicitamente como pontos além dos "bigodes" (limites calculados pelo IQR).
- **Histograma:** Permite visualizar *outliers* como barras isoladas nas extremidades da distribuição.
- ***Scatter Plot* (Gráfico de Dispersão):** Útil para detectar *outliers* no espaço bidimensional.

## 3. Técnicas de Tratamento

- **Eliminação:** Remover a observação (linha) do conjunto de dados.
- **Transformação Logarítmica:** Aplicar uma função log para reduzir o impacto de valores extremos, "comprimindo" a escala.
- **Filtragem:** Substituir os valores extremos por limites (ex: substituir tudo acima do Limite Superior pelo valor do Limite Superior).

## 4. Análise de Questões de Concurso

### 4.1 Identificação no Box-Plot (CESPE/DPE-RO/2022)

- **Enunciado:** No gráfico box-plot, o *outlier* é representado por qual ponto?
- **Gabarito:** **B) E**.
- **Análise:** O *outlier* é o ponto que aparece desconectado, além dos limites superior ou inferior do gráfico.

### 4.2 Definição e Reconhecimento do Problema (FGV/TCE-TO/2022)

- **Enunciado:** Operação de limpeza para tratar **pontos extremos** em uma série temporal.
- **Gabarito:** **D) Tratamento de outlier**.
- **Análise:** "Pontos extremos" são, por definição, *outliers*, e a operação para lidar com eles é o tratamento de *outliers*.

### 4.3 Ferramenta de Detecção (CS-UFG/UFNT/2023)

- **Enunciado:** Gráfico indicado para apresentar quartis, mediana e a possível presença de *outlier*.
- **Gabarito:** **C) Box-plot**.
- **Análise:** O Box-Plot é projetado especificamente para mostrar a dispersão, os quartis e sinalizar explicitamente a presença de *outliers*.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/TJ-SE) | **C** | (Gabarito da questão sobre box-plot não textual da imagem). |
| **02** (CESPE/DATAPREV) | **C** | *Outlier* é uma observação gerada por um mecanismo distinto. |
| **03** (CESPE/DPE-RO) | **B** | No box-plot, o *outlier* é o ponto além dos limites. |
| **04** (CS-UFG/UFNT) | **C** | Gráfico Box-Plot é ideal para mostrar quartis e *outliers*. |
| **05** (FGV/TJ-SE) | **E** | *Outlier* = acima do limite superior ou abaixo do inferior. |
| **06** (CESPE/MPO) | **C** | Um dado anômalo pode ser identificado visualmente no box-plot. |
| **07** (FGV/TCE-TO) | **D** | Tratar pontos extremos = Tratamento de *outliers*. |
| **08** (FGV/TJ-SE) | **B** | Verificar anomalias nos dados = Detecção de *outliers*. |