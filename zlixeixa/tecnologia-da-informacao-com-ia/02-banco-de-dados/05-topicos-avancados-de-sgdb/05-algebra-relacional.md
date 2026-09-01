# Álgebra Relacional

## 1. Conceito e Operações
- A álgebra relacional constitui um conjunto básico de operações do modelo relacional.
- As operações permitem ao usuário especificar solicitações básicas de recuperação de tuplas.
- O resultado de uma recuperação é uma nova relação, que pode ser formada a partir de uma ou mais relações (operações em cascata).
- Uma sequência de operações forma uma expressão, cujo resultado também será uma relação.
- As operações são divididas em dois grupos:
  - Operações da teoria matemática dos conjuntos: união (∪), interseção (∩), diferença (–) e produto cartesiano (×).
  - Operações específicas para bancos de dados relacionais: seleção (σ), projeção (π) e junção (⨝).

## 2. Operadores de Álgebra Relacional
| OPERAÇÃO | FINALIDADE | NOTAÇÃO |
|----------|------------|---------|
| Seleção | Seleciona todas as tuplas que satisfazem a condição de seleção de uma relação R. | σ <condição seleção> (R) |
| Projeção | Produz uma nova relação com apenas alguns atributos de R e remove tuplas duplicadas. | π <lista atributos> (R) |
| Junção Theta | Produz todas as combinações de tuplas de R1 e R2 que satisfazem a condição de junção. | R1 <condição junção> R2 |
| Equijunção | Produz todas as combinações de tuplas de R1 e R2 que satisfazem uma condição de junção apenas com comparações de igualdade. | R1 <condição junção> R2 ou R1 <(atributos junção 1)>, (<atributos junção 2>) R2 |
| Junção Natural | Mesmo que equijoin, exceto que atributos de junção de R1 não são incluídos na relação resultante; se os atributos de junção tiverem os mesmos nomes, eles não precisam ser especificados. | R1 <condição junção> R2 ou R1 (<atributos junção 1>), (<atributos junção 2>) R2 ou R1 * R2 |
| União | Produz uma relação que inclui todas as tuplas em R1 e R2, ou em ambos; R1 e R2 precisam ser compatíveis na união. | R1 ∪ R2 |
| Interseção | Produz uma relação que inclui todas as tuplas em R1 e R2; R1 e R2 precisam ser compatíveis na união. | R1 ∩ R2 |
| Diferença | Produz uma relação que inclui todas as tuplas em R1 que não estão em R2; R1 e R2 precisam ser compatíveis na união. | R1 – R2 |
| Produto Cartesiano | Produz uma relação que tem os atributos de R1 e R2 e inclui como tuplas todas as combinações possíveis de tuplas de R1 e R2. | R1 × R2 |
| Divisão | Produz uma relação R[X] que inclui todas as tuplas t[X] em R1(Z) que aparecerem em R1 em combinação com toda tupla de R2(Y), onde Z = X ∪ Y. | R1 (Z) ÷ R2 (Y) |

- A junção theta usa o produto cartesiano, cruzando operações de forma combinatória.

## 3. Operador Select (σ)
- A operação de seleção é utilizada para selecionar um subconjunto de tuplas de uma relação que satisfaça a uma condição de seleção.
- O operador σ é unário, ou seja, aplicado a uma única relação.
- Representação: σ <condição seleção> (R).
- Uma condição de seleção é uma expressão booleana, podendo usar os operadores E (and), OU (or) e NÃO (not).

### 3.1 Exemplo de Seleção
- Relação produtos:

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Café | Mercearia | R$ 8,99 | KG |
| Açúcar | Mercearia | R$ 10,20 | 5 KG |
| Sabão em Pó | Limpeza | R$ 9,90 | KG |
| Vinho | Bebida | R$ 59,90 | 750 ML |
| Refrigerante | Bebida | R$ 7,90 | 2 L |

- Listar produtos da categoria Bebida:
  - σ categoria = “bebida” (produtos)

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Vinho | Bebida | R$ 59,90 | 750 ML |
| Refrigerante | Bebida | R$ 7,90 | 2 L |

- Listar produtos da categoria Bebida com preço maior que R$ 10 (uso de “and”):
  - σ categoria = “bebida” and preço > 10 (produtos)

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Vinho | Bebida | R$ 59,90 | 750 ML |

### 3.2 Propriedades do Operador Select
- O operador σ é comutativo, ou seja, a ordem das condições não importa:
  - σ <condição1> (σ <condição2> (R)) = σ <condição2> (σ <condição1> (R)).
- O grau da relação resultante é o mesmo grau de R.
- O número de tuplas na relação resultante é sempre menor ou igual ao número de tuplas de R.
- Exemplo:
  - σ categoria = ‘bebida’ (σ preço > 10 (produtos)) = σ preço > 10 (σ categoria = ‘bebida’ (produtos)).

> [!CAUTION] OBSERVAÇÃO:
> - O comando WHERE do SQL corresponde à operação de seleção (σ), e não à projeção.

## 4. Operador Project (π)
- O operador π seleciona determinadas colunas da relação R, descartando outras.
- Representação: π <lista de atributos> (R).
- O operador π é unário, aplicado a uma única relação.
- Remove tuplas duplicadas quando os atributos projetados não pertencem à chave da relação R.
- O grau da relação resultante é igual ao número de atributos na lista.
- O número de tuplas na relação resultante é sempre menor ou igual ao número de tuplas de R.
- A operação de projeção não é comutativa:
  - π <list1> (π <list2> (R)) = π <list> (R), desde que a ordem seja respeitada (não é possível alterar a ordem das projeções).

### 4.1 Exemplos de Projeção
- Listar o nome e o preço de todos os produtos:
  - π nome, preço (produtos)

| NOME | PREÇO |
|------|-------|
| Café | R$ 8,99 |
| Açúcar | R$ 10,20 |
| Sabão em Pó | R$ 9,90 |
| Vinho | R$ 59,90 |
| Refrigerante | R$ 7,90 |

- Listar as categorias de produtos:
  - π categoria (produtos)

| CATEGORIA |
|-----------|
| Mercearia |
| Limpeza   |
| Bebida    |

- Usando o operador SELECT, seriam listados todos os 5 nomes na categoria produtos. Com o operador PROJECT, como existem categorias repetidas (bebida e mercearia), essas são eliminadas, resultando em apenas 3 registros.

> [!TIP] DICAS:
> - O operador PROJECT remove tuplas duplicadas, característica bastante cobrada em provas.

## 5. Operador Rename (ρ)
- Permite renomear relações ou atributos.
- Sintaxe:
  - ρ <novoNome> (Relação) ou ρ <novoAtributo>/<atributoOriginal> (Relação).
- É possível agrupar operações e criar relações de resultado intermediário usando atribuição (←).
- Exemplo:
  - Bebidas ← σ categoria = ‘bebida’ (produto).
  - Em seguida, aplicar projeção: π nome, preço (Bebidas).

## 6. Combinação de Operadores
- As operações podem ser combinadas em expressões, com o resultado de uma servindo de entrada para outra.
- Exemplo: listar o nome dos produtos da categoria ‘mercearia’ com preço superior a R$ 10,00:
  - π nome (σ categoria = ‘mercearia’ and preço > 10 (produtos)).

| NOME |
|------|
| Açúcar |

- Grande parte das questões lida com a interpretação de operações da álgebra.

## 7. Resumo dos Elementos
| ELEMENTO | SIGNIFICADO |
|----------|-------------|
| ← (atribuição) | Armazena o resultado de uma operação numa variável |
| σ (seleção) | Filtra linhas com base em uma condição |
| π (projeção) | Seleciona colunas específicas |
| ρ (rename) | Renomeia relação ou atributos |