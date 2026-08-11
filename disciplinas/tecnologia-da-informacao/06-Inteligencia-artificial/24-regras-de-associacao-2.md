# Regras de Associação e Algoritmo Apriori

## 1. Regras de Associação
- As regras de associação são utilizadas para encontrar relações de coocorrência entre itens em uma base de dados, gerando regras no formato A ⟶ B.
- Para avaliar a qualidade de uma regra, são utilizadas métricas que determinam sua validade e utilidade.

### 1.1 Suporte
- O suporte mede a frequência com que uma regra aparece no conjunto de dados.
- É calculado pela fórmula: Support(A ⟶ B) = |A ∪ B| / |D|, onde |A ∪ B| é o número de transações que contêm ambos os itens A e B, e |D| é o número total de transações.
- Representa a porcentagem de transações em que a regra ocorre.
- Exemplo: Em 4 vendas, a regra A → B aparece em 3 transações. O suporte é 3/4 = 75%.
- Lista:
  - Suporte alto indica que a regra é frequente;
  - Suporte baixo indica que a regra é rara.

### 1.2 Confiança
- A confiança mede a probabilidade de o consequente (B) ocorrer dado que o antecedente (A) ocorreu.
- É calculada como o suporte da regra dividido pelo suporte do antecedente.
- Exemplo: Se o leite aparece em 4 vendas e, dessas, o pão aparece em 3, a confiança da regra leite → pão é 3/4 = 75%.
- Lista:
  - Confiança alta indica uma forte relação entre A e B;
  - Confiança baixa indica uma relação fraca.

### 1.3 Lift
- O lift mede o quanto a ocorrência de A influencia a ocorrência de B, comparando com a probabilidade de B ocorrer independentemente.
- É calculado pela fórmula: Lift(A ⟶ B) = Confidence(A ⟶ B) / Support(B).
- Interpretação:
  - Lift > 1: Correlação positiva. A presença de A aumenta a probabilidade de B.
  - Lift = 1: Independência. A e B não têm relação.
  - Lift < 1: Correlação negativa. A presença de A diminui a probabilidade de B.

> [!CAUTION] OBSERVAÇÃO:
> - O lift não deve ser confundido com confiança. O lift considera a probabilidade base do consequente, enquanto a confiança não.

## 2. Algoritmo Apriori
- É o algoritmo mais utilizado para mineração de regras de associação.
- Utiliza limites mínimos de suporte e confiança para selecionar as regras.
- Funciona de forma iterativa, explorando conjuntos de itens (itemsets) de tamanho crescente.

### 2.1 Passo 1: Geração de Itemsets Frequentes
- O algoritmo realiza uma busca em largura, começando com itemsets de tamanho 1.
- Conta a frequência de cada item individualmente e seleciona aqueles que atendem ao suporte mínimo. Esses formam a lista L1.
- Em seguida, combina os itens de L1 para formar itemsets de tamanho 2 (pares) e calcula o suporte de cada par.
- Os pares que atendem ao suporte mínimo formam a lista L2.
- O processo se repete para itemsets de tamanho 3, 4, e assim por diante, até que não haja mais combinações possíveis.
- Lista:
  - Este processo elimina itemsets não frequentes, reduzindo o espaço de busca;
  - Exemplo: Com suporte mínimo de 3 transações, itens como A, B, C e D são avaliados. Pares como AB e AD podem ser descartados se não atingirem o suporte mínimo.

> [!TIP] DICAS:
> - O Apriori usa o princípio de que um itemset só é frequente se todos os seus subconjuntos também forem frequentes.

### 2.2 Passo 2: Geração de Regras de Associação
- Para cada itemset frequente (ex: {A, C}), todas as possíveis regras são geradas (ex: A → C e C → A).
- Calcula-se a confiança de cada regra.
- São selecionadas apenas as regras cuja confiança está acima do limite mínimo estabelecido.
- Exemplo: Para o itemset {A, C} com suporte de 4/8 (50%), a confiança de A → C é 4/5 = 80% (aprovada), enquanto a confiança de C → A é 4/6 = 67% (reprovada, se o limite for 70%).

> [!CAUTION] OBSERVAÇÃO:
> - Confundir suporte com confiança é um erro comum. Suporte é sobre a frequência da regra, enquanto confiança é sobre a força da relação entre antecedente e consequente.
> - O Apriori não realiza busca em profundidade, mas sim em largura, como descrito no passo 1.