# Exploração de Dados e Data Mining 

## 1. Conceitos básicos
- **Data Mining:** Exploração e análise automática ou semiautomática de grandes bases de dados para descobrir padrões e regras significativos para tomada de decisão.
- **Lei de Moore:** A capacidade de processamento dobra a cada 18 meses, acompanhando o crescimento do volume de dados.

#### Pilares do Data Mining
- Estatística
- Inteligência Artificial
- Aprendizado de Máquina

## 2. Objetivos do Data Mining (PICO)
- **P**revisão: Comportamento futuro baseado em dados passados.
- **I**dentificação: Detecção de eventos e atividades por meio de padrões.
- **C**lassificação: Partição dos dados em categorias com base em parâmetros.
- **O**timização: Uso eficiente de recursos para melhorar resultados.

## 3. KDD (Knowledge Discovery in Databases)
- Processo mais amplo que inclui o Data Mining como uma de suas etapas:
  1. Seleção
  2. Pré-processamento
  3. Formatação
  4. Mineração de Dados (Data Mining)
  5. Interpretação/Avaliação

## 4. CRISP-DM (Cross-Industry Standard Process for Data Mining)
- Metodologia não proprietária com 6 fases interativas:
  1. **Entendimento do Negócio:** Definir objetivos e entender o problema.
  2. **Entendimento dos Dados:** Avaliar qualidade, volume e fontes dos dados.
  3. **Preparação dos Dados (70–80% do esforço):**
    - Limpeza (dados faltantes, ruidosos);
    - Transformação (normalização, seleção de atributos, discretização);
    - Redução (cubo de dados, redução de dimensionalidade).
  4. **Modelagem:** Aplicação de algoritmos de mineração.
  5. **Avaliação:** Teste e validação do modelo.
  6. **Implantação:** Implementação do modelo na organização.

## 5. Tipos de análises/modelagens

#### Modelagens descritivas (não supervisionadas)
- **Detecção de Anomalias:** Identifica padrões raros ou fora do comum (ex.: análise de outliers).
- **Regras de Associação:** Descobre correlações entre variáveis (ex.: market basket analysis).
- **Agrupamento (Clustering):** Separa dados por semelhança (ex.: métodos de particionamento, hierárquicos).

#### Modelagens preditivas (supervisionadas)
- **Estimação:** Prediz um valor com base em padrões conhecidos.
- **Predição:** Antecipa comportamentos futuros.
- **Classificação:** Atribui dados a categorias pré-definidas.

## 6. Técnicas comuns

#### Descritivas
- Análise de outliers
- Indução por árvore de decisão
- Agregações e gráficos
- Market basket analysis
- Métodos de particionamento (ex.: k-means)

#### Preditivas
- Regressão (linear, múltipla, logística)
- Classificação Bayesiana
- Redes neurais
- Análise de vizinhança

## 7. Aprendizado de máquina

#### Não supervisionado
- Não há saída conhecida.
- Ex.: clustering, associação, detecção de anomalias.

#### Supervisionado
- Usa dados anotados para treinar o modelo.
- Ex.: classificação, regressão.