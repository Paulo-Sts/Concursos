# Regras de Associação

## 1. Conceitos Fundamentais
- A regra de associação é um tipo de tarefa de aprendizado de máquina não supervisionado, ou seja, a máquina recebe dados não rotulados.
- As regras de associação servem para extrair da base de dados linhas ou ocorrências que se repetem.
- O algoritmo de regra de associação extrai informações da base de dados que compara valores e verifica se eles são co-ocorrentes.

## 2. Introdução às Regras de Associação
- A regra de associação é representada por: A ⇒ B.
- A e B são subconjuntos disjuntos de itens.
- A é chamado de antecedente e B de consequente.
- A regra busca descobrir elementos que ocorrem em comum em uma base de dados.

### 2.1 Principais Algoritmos
- Apriori;
- Eclat;
- Partition;
- FP-Growth.

> [!TIP] DICAS:
> - Os principais algoritmos de regra de associação são: Apriori, Eclat, Partition e FP-Growth.
> - O algoritmo Apriori é o mais conhecido e cobrado em provas.

### 2.2 Casos de Uso
- Análise de cesta de compras;
- Sistemas de recomendação;
- Segmentação de clientes;
- Bioinformática;
- Saúde pública.

> [!TIP] DICAS:
> - O exemplo mais clássico é o do Walmart nos anos 90, que criou uma base de dados de vendas para extrair padrões de compra.
> - Os casos de uso mais cobrados em concursos são: análise de cesta de compras e sistemas de recomendação.

## 3. Mineração de Dados e Regras de Associação
- Mineração de dados é a extração de informação relevante da base de dados.
- As regras de associação adotadas em mineração de dados buscam padrões frequentes entre conjuntos de dados.
- As regras podem ser úteis para caracterizar hábitos de consumo de clientes, onde as preferências são identificadas e associadas a outros potenciais produtos de interesse.

### 3.1 Objetivo da Mineração de Regras de Associação
- Extrair regras de associação de um determinado conjunto de dados.
- O processo é chamado de Mineração de Regras de Associação (ARM - Association Rule Mining).

> [!CAUTION] OBSERVAÇÃO:
> - Regras de associação são diferentes de árvores de decisão: as regras de associação podem gerar múltiplas regras com diferentes conclusões, enquanto as árvores de decisão geralmente produzem uma única conclusão por regra.
> - A afirmação de que "algoritmos de regras de associação constroem regras com apenas uma única conclusão" é ERRADA, pois eles podem gerar várias regras com diferentes consequentes.