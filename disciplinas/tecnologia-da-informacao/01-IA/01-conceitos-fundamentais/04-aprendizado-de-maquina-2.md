# Anotações – Aprendizado de Máquina – Divisão de Dados e Validação

## 1. Conjuntos de Dados: Treinamento, Validação e Teste

### 1.1 Por que dividir os dados?

- O modelo precisa ser treinado com dados rotulados (treinamento).
- Durante o treinamento, o modelo pode **decorar** os dados de treino, perdendo a capacidade de **generalizar** para dados novos (overfitting).
- Para avaliar se o modelo generaliza bem, usam-se dados que ele **nunca viu** (teste).

### 1.2 Os três conjuntos

| CONJUNTO | FUNÇÃO | TAMANHO TÍPICO |
| --- | --- | --- |
| **Treinamento (Training)** | Ajustar os parâmetros internos do modelo (aprendizado efetivo). | 60% – 80% |
| **Validação (Validation)** | Ajustar hiperparâmetros, comparar modelos, monitorar overfitting. | 10% – 20% |
| **Teste (Test)** | Avaliação final e imparcial do modelo (dados nunca vistos). | 10% – 20% |

> ### 1.2.1 Parâmetros vs. Hiperparâmetros
> - **Parâmetros:** características ajustáveis do modelo que são aprendidas durante o treinamento (ex.: pesos das conexões em uma rede neural).
> - **Hiperparâmetros:** configurações definidas antes do treinamento (ex.: taxa de aprendizagem, número de neurônios, número de camadas).

## 2. Métodos de Particionamento de Dados

### 2.1 Hold-Out (Divisão única)

- O dataset é dividido **uma única vez** em treino e teste (e, opcionalmente, validação).
- **Vantagem:** simples e rápido.
- **Desvantagem:** pode não ser representativo se a divisão for mal feita (ex.: classes desbalanceadas).

**Exemplo:** 80% treino, 20% teste.

> ### 2.1.1 Estratificação
> - Quando as classes são desbalanceadas, é importante manter a **proporção original** das classes em cada subconjunto (treino, validação, teste).
> - Exemplo: se o dataset tem 90% de transações normais e 10% fraudulentas, o split deve preservar essa proporção em todos os conjuntos.

### 2.2 K-Fold Cross-Validation (Validação Cruzada)

- O dataset é dividido em **k partes (folds)** de tamanhos iguais (ex.: k=5 ou k=10).
- Em cada rodada:
  - **k-1 folds** são usados para **treinamento**.
  - **1 fold** é usado para **teste**.
- O processo é repetido **k vezes**, cada vez com um fold diferente para teste.
- A performance final é a **média** das performances de cada rodada.

**Vantagem:** todos os dados são usados para treino em algum momento, e todos são testados em algum momento.

> ### 2.2.1 Stratified K-Fold
> - Variante do k-fold que mantém a **proporção das classes** em cada fold.
> - Essencial para conjuntos de dados com classes desbalanceadas.

### 2.3 Leave-One-Out (LOOCV)

- Cada rodada usa **apenas uma amostra** para teste e **todas as outras** para treino.
- O processo é repetido N vezes (N = número total de amostras).
- **Vantagem:** avaliação exaustiva.
- **Desvantagem:** custo computacional muito alto para datasets grandes.
- **Uso típico:** bases de dados pequenas.

### 2.4 Bootstrap

- Cria múltiplos conjuntos de treinamento por meio de **amostragem com reposição**.
- O conjunto de teste é composto pelos registros **não selecionados** para o treino (out-of-bag).
- Permite estimar a variabilidade do modelo.

> ### 2.4.1 Exemplo (bootstrap com 3 modelos)
> - Dataset original: 10 dados.
> - Para cada modelo, sorteiam-se **10 dados com reposição** para treino.
> - Os dados não sorteados formam o conjunto de teste.
> - A performance final é a média dos resultados.

## 3. Comparação dos Métodos

| MÉTODO | DIVISÃO | REPETIÇÃO | USO DE TODOS OS DADOS PARA TESTE? | CUSTO COMPUTACIONAL |
| --- | --- | --- | --- | --- |
| **Hold-Out** | 1 vez | Não | Não | Baixo |
| **K-Fold** | k partes | k vezes | Sim (cada dado testado uma vez) | Médio |
| **LOOCV** | N partes | N vezes | Sim | Muito alto |
| **Bootstrap** | Amostragem com reposição | N vezes | Não (out-of-bag) | Médio |

## 4. Overfitting (Sobreajuste)

- Ocorre quando o modelo **decora os dados de treinamento** em vez de aprender padrões gerais.
- Sintoma: erro baixo no treino, erro alto no teste.
- Como evitar:
  - Usar validação cruzada.
  - Usar um conjunto de validação para monitorar o erro durante o treino.
  - Parar o treinamento quando o erro de validação começar a aumentar (early stopping).

## 5. Questões de Concurso Comentadas

### 5.1 (CESGRANRIO/2024/IPEA – Técnico)

**Item:** "Separou 20% para avaliação (teste) e 80% para treino, uma única vez" → **Hold-Out**.  
"Depois, separou em 10 partes, usando uma diferente para teste em cada rodada" → **K-Fold**.

**Gabarito: b) hold-out e k-fold.**

### 5.2 (FGV/DATAPREV – Analista)

**Item:** "Característica da validação cruzada com k conjuntos:"

**Gabarito: a) considera, na sua versão estratificada, a proporção de exemplos de cada classe quando da geração de subconjuntos mutuamente exclusivos.**

### 5.3 (CESPE/CEBRASPE/2025/SUSEP – Analista)

**Item:** "Em validação cruzada k-fold, cada instância do conjunto de dados é utilizada uma única vez para teste, o que garante avaliação equilibrada."

**Gabarito: Certo (C).**

**Comentário:** No k-fold, cada amostra é testada exatamente uma vez (em uma das k rodadas).

### 5.4 (FGV/2025 – Analista de Controle Externo)

**Item:** "Método em que o conjunto de treinamento é gerado por N sorteios aleatórios com reposição; o conjunto de testes é composto pelos registros não selecionados."

**Gabarito: b) Bootstrap.**

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/2024) | b |
| 02 (FGV/DATAPREV) | a |
| 03 (CESPE/2025) | C |
| 04 (FGV/2025) | b |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Treinamento** | Dados usados para ajustar os parâmetros do modelo. |
| **Validação** | Dados usados para ajustar hiperparâmetros e evitar overfitting. |
| **Teste** | Dados nunca vistos, usados para avaliação final e imparcial. |
| **Hold-Out** | Divisão única em treino e teste. |
| **K-Fold** | Divisão em k partes; cada parte é usada uma vez como teste. |
| **Stratified K-Fold** | Mantém a proporção de classes em cada fold. |
| **LOOCV** | Uma amostra para teste, todas as outras para treino. |
| **Bootstrap** | Amostragem com reposição para gerar conjuntos de treino. |
| **Overfitting** | Modelo decora os dados de treino e não generaliza. |

---

*Material complementar às aulas "Introdução II" e "Divisão de Dados" (professor Vitor Kessler/Gran Concursos).*