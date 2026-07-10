# Anotações – Aprendizado de Máquina – Tipos de Aprendizado

## 1. Relação entre Tipos de Aprendizado e Análises

| TIPO DE ANÁLISE | TIPO DE APRENDIZADO | OBJETIVO |
| --- | --- | --- |
| **Análise preditiva** | Supervisionado | Prever valores ou categorias futuras. |
| **Análise descritiva** | Não Supervisionado | Encontrar padrões ocultos, agrupar dados. |

## 2. Aprendizado Supervisionado

- O modelo aprende a partir de **exemplos rotulados** (dados de entrada e saída conhecidas).
- **Objetivo:** prever um **rótulo (classe)** ou um **valor numérico** para novos dados.

### 2.1 Principais tarefas

| TAREFA | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Classificação** | Prever uma **variável categórica** (classe). | Detectar se uma transação é fraudulenta ou não; identificar se o cliente vai cancelar o contrato. |
| **Regressão** | Prever um **valor numérico contínuo**. | Prever temperatura, preço de ações, valor de venda. |

> ### 2.1.1 Diferença fundamental
> - **Classificação:** saída é uma categoria (ex.: "fraude" ou "normal").
> - **Regressão:** saída é um número (ex.: "R$ 1.500,00").

### 2.2 Exemplos de tarefas supervisionadas

| TAREFA | EXEMPLO PRÁTICO |
| --- | --- |
| Classificação | Identificar clientes com maior chance de cancelar o contrato (churn). |
| Classificação | Reconhecer bandidos em imagens de câmeras de segurança. |
| Regressão | Prever a pena (em anos) a ser aplicada a um réu. |
| Regressão | Prever vendas futuras ou preços de ações. |

> ### 2.2.1 Observação (questão CESPE)
> - A detecção de **transações fraudulentas** é um problema de **classificação**, **não** de regressão.

## 3. Aprendizado Não Supervisionado

- O modelo **não recebe rótulos de saída**.
- Busca **estruturas, padrões ou relacionamentos ocultos** nos dados.
- Amplamente usado em **exploração de dados** e **descoberta de conhecimento** (análise descritiva).

### 3.1 Principais tarefas

| TAREFA | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Clusterização (Agrupamento)** | Agrupar elementos semelhantes sem rótulos prévios. | Dividir alunos em grupos de desempenho (baixo, médio, alto) a partir de suas notas. |
| **Regras de Associação** | Descobrir relações frequentes entre atributos ou itens. | "Quem compra pão também compra manteiga" (vendas casadas). |
| **Redução de Dimensionalidade** | Representar dados complexos em menos dimensões (colunas). | Reduzir o número de atributos para acelerar o treinamento e eliminar ruído. |

### 3.2 Exemplo de Regras de Associação

- Em um supermercado, cada **linha** é uma venda; cada **coluna** é um produto.
- Se o produto foi vendido, o valor é `1`; caso contrário, `0`.
- A IA pode extrair regras como: "Sempre que o produto X for comprado, o produto Y também é comprado".
- Isso permite identificar **vendas casadas**.

### 3.3 Clusterização (Clustering)

- Agrupa dados semelhantes em **clusters**.
- **Não atribui categorias** aos grupos – apenas separa os dados.
- Exemplo: agrupar clientes por comportamento de compra.

## 4. Detecção de Anomalias

- Identificação de **outliers** (pontos fora da curva).
- Pode ser supervisionada ou não supervisionada, dependendo do contexto.
- Exemplo: detectar transações suspeitas em cartões de crédito.

## 5. Quadro Comparativo

| CRITÉRIO | SUPERVISIONADO | NÃO SUPERVISIONADO |
| --- | --- | --- |
| **Rótulos** | Sim (classe/target) | Não |
| **Objetivo** | Prever (classificar ou regredir) | Descrever (agrupar, associar, reduzir) |
| **Tipo de análise** | Preditiva | Descritiva |
| **Exemplos** | Classificação, Regressão | Clusterização, Regras de Associação, Redução de Dimensionalidade |

## 6. Questões de Concurso Comentadas

### 6.1 (CESPE/CEBRASPE/SEFAZ-SE/2025)

**Item:** "Identificar clientes que possuem maior chance de cancelar o contrato no próximo mês, a partir de variáveis como tempo de permanência, valor gasto mensal e histórico de reclamações."

**Gabarito: c) a classificação.**

**Comentário:** O objetivo é prever uma **categoria** (cancela ou não cancela) – problema de classificação.

### 6.2 (CESPE/CEBRASPE/PF/2025)

**Item:** "Em aprendizado de máquina, as técnicas de classificação e regressão são exemplos de aplicações práticas para a solução de problemas."

**Gabarito: Certo (C).**

### 6.3 (CESPE/CEBRASPE/ANM/2025)

**Item:** "A regressão é o método de data mining usado para prever valores contínuos – por exemplo, previsão de vendas, preços de ações, identificação de transações fraudulentas, entre outros."

**Gabarito: Certo (C) (com ressalva: identificação de fraudes é classificação).**

### 6.4 (CESPE/CEBRASPE/SERPRO/2023)

**Item:** "As técnicas de agrupamento têm por objetivo fazer a previsão de um atributo alvo a partir do agrupamento de dados que compartilhem padrões semelhantes."

**Gabarito: Errado (E).**

**Comentário:** Previsão é tarefa de aprendizado **supervisionado** (classificação/regressão). Agrupamento (clustering) é **não supervisionado** e não faz previsão de um alvo.

### 6.5 (CESPE/CEBRASPE/PF/2025)

**Item:** "A técnica de clustering em data mining atribui categorias aos grupos de dados para facilitar a análise e a tomada de decisão."

**Gabarito: Errado (E).**

**Comentário:** Clustering **não atribui categorias** – apenas separa os dados em grupos. A atribuição de significado aos grupos é feita pelo analista posteriormente.

### 6.6 (CESPE/CEBRASPE/EMBRAPA/2025)

**Item:** "A utilização de técnicas de aprendizado não supervisionado, como clustering, pode identificar padrões em dados visuais sem a necessidade de grandes conjuntos de dados rotulados."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/SEFAZ-SE/2025) | c |
| 02 (CESPE/PF/2025) | C |
| 03 (CESPE/ANM/2025) | C |
| 04 (CESPE/SERPRO/2023) | E |
| 05 (CESPE/PF/2025) | E |
| 06 (CESPE/EMBRAPA/2025) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Supervisionado** | Aprende com exemplos rotulados. |
| **Não supervisionado** | Aprende sem rótulos, encontra padrões. |
| **Classificação** | Prever categoria (supervisionado). |
| **Regressão** | Prever número (supervisionado). |
| **Clusterização** | Agrupar dados semelhantes (não supervisionado). |
| **Regras de Associação** | Descobrir relações frequentes entre itens (não supervisionado). |
| **Redução de Dimensionalidade** | Reduzir número de colunas (não supervisionado). |
| **Detecção de Anomalias** | Identificar outliers (pode ser supervisionado ou não). |

---

*Material complementar à aula "Tipos de Aprendizado" (professor Vitor Kessler/Gran Concursos).*