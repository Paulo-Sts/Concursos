# Anotações

# TRATAMENTO DE DADOS – TRATAMENTO DE DADOS AUSENTES

## 1. Conceito e Causas dos Dados Ausentes

### 1.1 O que são e por que acontecem

- Dados ausentes ou faltantes (*missing data*) são uma ocorrência muito comum em conjuntos de dados.
- **Causas Comuns:** Erros de digitação, leitura incorreta de sensores, perda de dados, campos não aplicáveis (ex: campo "gestante" para um paciente masculino), ou exclusão deliberada de *outliers*.

### 1.2 Taxonomia (Tipos de Ausência)

| TIPO | SIGLA | DESCRIÇÃO |
| :--- | :--- | :--- |
| **Perdidos Completamente de Forma Aleatória** | **MCAR** | A ausência do dado **não tem relação** com nenhum outro valor, observado ou não. É puramente aleatória. |
| **Perdidos Aleatoriamente** | **MAR** | A ausência do dado pode ser explicada/prevista por **outros dados observados** no conjunto, mas não pelo valor do próprio dado faltante. É possível recuperá-lo. |
| **Perdidos Não Aleatoriamente** | **MNAR** | A ausência do dado está relacionada ao **próprio valor faltante** ou a fatores não medidos. É o caso mais complexo. |

## 2. Técnicas de Tratamento

### 2.1 Métodos de Preenchimento (Imputação)

- **Estatísticas Descritivas:** Preencher com a **média**, **mediana** (para dados numéricos) ou **moda** (para dados categóricos).
- **Valor Constante:** Substituir por um valor padrão.
- **Último/Próximo Válido:** Em séries temporais, repetir o valor imediatamente anterior (ou posterior).
- **Interpolação Linear:** Para séries temporais, calcular um valor intermediário entre o ponto anterior e o posterior.
- **Imputação por KNN (*K-Nearest Neighbors*):** Prever o valor faltante com base nos seus "vizinhos" mais próximos (linhas similares) no conjunto de dados.
- **Criação de Categoria "Ausente":** Para dados discretos/categóricos, criar uma nova categoria exclusiva para representar a ausência.
- **Regressão Linear:** Prever o valor faltante com base em uma regressão usando outras variáveis.
- *Hot Deck/Cold Deck:* Preencher com um valor existente na mesma base (*Hot Deck*) ou em outra base de dados (*Cold Deck*).

### 2.2 Métodos de Exclusão

- ***Listwise Deletion* (Caso Completo):** **Excluir toda a linha** (registro/observação) do conjunto de dados que contiver **qualquer** valor faltante.
- ***Pairwise Deletion* (Casos Disponíveis):** Excluir seletivamente as observações apenas nas análises específicas onde as variáveis de interesse têm dados faltantes, aproveitando o registro para outras análises.
- **Exclusão do Atributo:** Remover toda a coluna (atributo) se a quantidade de dados ausentes for muito alta.

## 3. Análise de Questões de Concurso

### 3.1 Identificação de Métodos Válidos (CS-UFG/TJ-AC/2024)

- **Enunciado:** Métodos para tratamento de dados faltantes.
- **Gabarito:** **A) interpolação de vizinhos mais próximos, valor médio do atributo, valor modal.**
- **Análise:** A alternativa lista métodos reais de imputação. As demais alternativas misturam conceitos de validação de modelos de ML e otimização, que são sobre avaliação do modelo, e não sobre tratamento do dado bruto faltante.

### 3.2 Tratamento de Dados como Etapa Obrigatória (CESPE-CEBRASPE/MPO/2024)

- **Enunciado:** "O tratamento de dados ausentes é prescindível..."
- **Gabarito:** **ERRADO.**
- **Análise:** "Prescindível" significa desnecessário. O tratamento de dados ausentes **não é opcional**; é uma etapa essencial do pré-processamento, pois a maioria dos algoritmos não funciona bem com dados faltantes.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESPE/SERPRO) | **E** | Preencher com zeros não é suficiente, é uma decisão que pode enviesar os dados. |
| **02** (CESPE/MPO) | **E** | O tratamento de dados ausentes é **imprescindível**, não opcional. |
| **03** (CS-UFG/TJ-AC) | **A** | Interpolação KNN, média e moda são métodos de imputação. |
| **04** (FGV/CGE-SC) | **B** | Média, KNN, moda e valor aleatório são métodos de tratamento de dados faltantes. |