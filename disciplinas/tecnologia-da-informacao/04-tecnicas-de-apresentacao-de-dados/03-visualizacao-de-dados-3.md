# Anotações

# INTRODUÇÃO À VISUALIZAÇÃO DE DADOS III

## 1. Revisão e Aprofundamento: Histograma

### 1.1 Definição e Uso

- **Descrição:** Gráfico de barras que mostra a **distribuição de uma variável contínua**. As barras representam faixas de valores (classes/intervalos), e a altura indica a **frequência** com que os dados ocorrem naquele intervalo.
- **Quando Usar:** Para visualizar a forma da distribuição (ex: distribuição etária de uma população, distribuição de salários).
- **Interpretação:** O formato ajuda a identificar se a distribuição é normal, assimétrica, uniforme, etc. e onde os valores são mais frequentes.

### 1.2 Confronto com Outros Gráficos (Questões Comparativas)

- **Sequência de etapas de um processo:** É representada por um **Fluxograma**, não por um histograma (CESPE/MME/2023).
- **Relação entre duas variáveis (causa e efeito):** É representada por um **Gráfico de Dispersão**, não por um histograma (QUADRIX/CRECI/2023).
- **Correlação a partir de nuvens de pontos:** É o Gráfico de **Dispersão**, não o histograma (CESPE/ANAC/2024).

## 2. Boas Práticas para Criação de Visualizações

### 2.1 Princípios de Integridade e Clareza Visual

- **Escala dos Eixos:**
    - Deve ser **proporcional** aos dados.
    - **Evitar truncar** os eixos (especialmente o eixo Y), pois isso distorce a percepção das diferenças entre categorias.
    - **Sempre iniciar a escala do eixo Y em zero** em gráficos de barras, para não exagerar ou minimizar variações.

- **Séries Múltiplas e Legendas:**
    - Diferentes séries de dados devem ser claramente distinguíveis (por cores, texturas ou marcadores).
    - As legendas devem ser claras.

- **Ênfase e Destaque:**
    - Use cores, negrito ou marcadores para destacar o dado mais importante sem distorcer o restante.
    - Para destacar uma barra ou fatia específica, use uma cor diferente. A ênfase deve ser sutil.
    - **Nunca ocultar** o que não se quer mostrar.

- **Regras Específicas:**
    - **Gráficos 3D:** Devem ser usados apenas quando há três dimensões a representar, o que **exclui gráficos de pizza** (a pizza representa proporção de um todo, que é unidimensional) (UFMA/2022).
    - **Dois Eixos Y:** É recomendada a **não utilização** de dois eixos Y, pois pode gerar confusão (UFMA/2022).
    - **Fonte:** A fonte dos dados **sempre é necessária** e deve estar presente (FGV/Jaboatão/2023).

### 2.2 Erros Comuns ao Interpretar Visualizações

- Não prestar atenção ao escopo da informação.
- Não verificar a fonte e a confiabilidade dos dados.
- Extrapolar conclusões além do que os dados suportam.
- Considerar a possibilidade de correlação espúria (falsa) entre variáveis em um gráfico de dispersão **é uma prática CORRETA de análise**, não um erro (UFMA/2023).

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (IDHTEC/Ilha Itamaracá) | **C** | Distribuição de variável contínua em faixas = Histograma. |
| **02** (SELECON/SEDUC-MT) | **C** | Dados de frequência em classes = Histograma. |
| **03** (CESPE/SEDUC-AL) | **E** | Análise de dados de histograma. |
| **04** (CESGRANRIO/CNU) | **A** | Distribuição populacional por faixa salarial = Histograma. |
| **05** (FUNDATEC/AL-RS) | **C** | Histograma é a representação gráfica da distribuição de dados. |
| **06** (CESPE/MME) | **E** | Sequência de etapas = Fluxograma. |
| **07** (QUADRIX/CRECI) | **E** | Relação de causa e efeito entre duas variáveis = Dispersão. |
| **08** (CESPE/ANAC) | **E** | Nuvem de pontos e relação entre conjuntos de dados = Dispersão. |
| **09** (CESGRANRIO/BB) | **E** | Histograma = frequências em intervalos de valores. |
| **10** (CESPE/SEBRAE) | **B** | I e III. Barras classificam categorias; histograma é para distribuição. |
| **11** (UFMA) | **C** | Gráficos de pizza **não são sempre recomendados**. |
| **12** (UFMA) | **A** | Considerar correlação espúria é boa prática de análise. |
| **13** (FGV/Jaboatão) | **A** | Omissão do zero e ausência do eixo vertical induzem a erro. |