# Anotações

# BUSINESS INTELLIGENCE – OPERAÇÕES OLAP

## 1. Conceito e Objetivo das Operações OLAP

- As operações OLAP são um **conjunto de operações** utilizadas para a **análise interativa de dados multidimensionais** em um modelo dimensional (cubo de dados).
- Permitem que os usuários explorem, visualizem e manipulem os dados de diferentes perspectivas, realizem agregações, filtrem informações e naveguem entre os diferentes **níveis de detalhe (granularidade)**.

## 2. Granularidade

- **Conceito:** Refere-se ao **nível de detalhe** ou resumo existente em uma unidade de dados.
- **Quanto mais detalhado** (ex: dados diários), **menor** o nível de granularidade.
- **Quanto mais sumarizado** (ex: dados anuais), **maior** o nível de granularidade.

## 3. Principais Operações OLAP

| OPERAÇÃO | SINÔNIMOS | DESCRIÇÃO |
| :--- | :--- | :--- |
| **Drill Down** | Roll Down | Aumenta o nível de detalhe, descendo na hierarquia da dimensão (ex: Ano -> Mês). A granularidade diminui. |
| **Roll Up** | Drill Up | Diminui o nível de detalhe, subindo na hierarquia da dimensão (ex: Cidade -> Estado). A granularidade aumenta. |
| **Slice and Dice** | - | **Slice:** "Fatia" o cubo, filtrando um valor em uma dimensão. **Dice:** "Corta" um subcubo, filtrando valores em duas ou mais dimensões. |
| **Pivot** | Rotate, Rotation | Reorganiza os dados multidimensionais, "girando" o cubo para trocar a posição dos eixos (dimensões) e obter uma visão alternativa. |
| **Drill Across** | - | Move-se lateralmente de um conjunto de dados para outro, **mantendo-se no mesmo nível de detalhe**, mas mudando a dimensão. |
| **Drill Through** | - | Salta de um nível de detalhe em uma dimensão para outro nível em uma dimensão diferente (ex: muda a consulta para um conjunto de dados diferente). |

## 4. Análise de Questões de Concurso

### 4.1 Identificação de Operações (FGV/SEFAZ-AM/2022)

- **Enunciado:** "A operação analítica que se caracteriza por analisar dados em níveis de agregação progressivamente mais detalhados e de menor granularidade, é denominada:"
- **Gabarito:** **C) drill-down**.
- **Análise:** A descrição de "mais detalhado" e "menor granularidade" é a definição exata do Drill Down.

### 4.2 Trocas de Posição (FCC/SABESP/2018)

- **Enunciado:** "Um Técnico executou uma operação de visualização OLAP que rotacionou os eixos de um determinado cubo, provendo uma visão alternativa dos dados... Ele executou a operação:"
- **Gabarito:** **D) pivot**.
- **Análise:** "Rotacionar os eixos" para ter uma visão alternativa é a definição principal do Pivot.

### 4.3 Caso Hipotético da Câmara Legislativa (FCC/CLDF/2018)

- **Enunciado:** Análise de dados de votos. Ações: [1] detalhar de trimestre para mês; [2] agregar de cidade para estado; [3] trocar a posição dos eixos.
- **Gabarito:** **A) drill-down – roll-up e pivot**.
- **Análise:**
    - Detalhar de trimestre (agregado) para mês (detalhe) = **Drill Down**.
    - Agregar de cidade (detalhe) para estado (agregado) = **Roll Up**.
    - Trocar os eixos = **Pivot**.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/CNMP) | **E** | Quanto mais detalhes, **menor** a granularidade. |
| **2** (CESGRANRIO/ELETROBRAS) | **A** | Estado -> Município = **Drill Down**. |
| **3** (FGV/SEFAZ-AM) | **C** | Mais detalhado, menor granularidade = **Drill Down**. |
| **4** (FCC/SEFAZ-SC) | **A** | Aumentar o nível de detalhe = **Drill Down**. |
| **5** (FCC/CLDF) | **A** | Detalhar (mês), Agregar (estado) e Trocar eixos = Drill-down, Roll-up, Pivot. |
| **6** (CESGRANRIO/BB) | **E** | T->X (Roll-Up), T->Y (Rotation/Pivot). |
| **7** (FGV/IBGE) | **D** | Troca de eixos para visão alternativa = **Pivot**. |
| **8** (CESPE/TCE-RJ) | **C** | Drill-down aumenta detalhe (certo); drill-up diminui granularidade (certo). |
| **9** (FCC/SABESP) | **D** | Rotacionar eixos = **Pivot**. |
| **10** (CESPE/TJ-RJ) | **E** | Combinar células para um nível maior de generalização = Roll Up. |
| **11** (CESPE/ME) | **E** | Rollup **diminui** o detalhamento. |
| **12** (FGV/SEFAZ-AM) | **C** | Mais detalhado = **Drill Down**. |
| **13** (CESPE/TCE-SC) | **C** | Drill-down = detalhe; Drill-across = lateral. |
| **14** (FCC/TRF-4) | **C** | Focar em um detalhe (bimestre e cidade) = **Drill Down**. |
| **15** (FCC/SANASA) | **A** | Mudar a análise de uma visão para outra = **Drill Through**. |
| **16** (AOCP/SUSIPE) | **C** | Operação Rotation = Visualização sob nova perspectiva. |