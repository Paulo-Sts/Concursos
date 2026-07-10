# Anotações – Banco de Dados – Mapeamento ER-Relacional II (Casos Práticos)

## 1. Mapeamento de Relacionamentos 1:N

### 1.1 Regra geral

- A **chave primária da entidade do lado 1** (pai) é adicionada como **chave estrangeira na tabela do lado N** (filho).
- A FK não pode ser `NULL` se a participação do lado N for total (obrigatória).

**Exemplo (Departamento – Empregado):**
```
DEPARTAMENTO (CodDep, Sigla, LocalDep)
EMPREGADO (CodEmp, Nome, CodDep)   -- FK referencia DEPARTAMENTO
```

- Cada empregado tem um departamento (FK preenchida).
- Um departamento pode ter vários empregados.

> ### 1.1.1 Caso especial (gerente)
> - Se cada departamento deve ter **um gerente** (que é um empregado), adiciona-se uma FK `CodGerente` na tabela `DEPARTAMENTO`.
> - Isso cria uma **dupla referência**: EMPREGADO → DEPARTAMENTO (para o departamento onde trabalha) e DEPARTAMENTO → EMPREGADO (para o gerente).

## 2. Mapeamento de Relacionamentos M:N

### 2.1 Regra geral

- Deve ser criada uma **tabela de associação** (tabela própria, tabela de ligação).
- A tabela contém as **PKs das duas entidades** (como FKs) e, opcionalmente, **atributos do relacionamento**.
- A PK da tabela de associação é a **combinação das duas PKs** (chave composta).
- O relacionamento M:N se transforma em **dois relacionamentos 1:N** (entre a tabela de associação e cada uma das entidades originais).

**Exemplo (Juiz – Assistente – relação M:N):**
```
JUIZ (IdJuiz, Nome)
ASSISTENTE (IdAssistente, Nome)
JUIZ_ASSISTENTE (IdJuiz, IdAssistente)   -- PK: (IdJuiz, IdAssistente)
```

> ### 2.1.1 Atenção (questão FCC/2017)
> - Em relacionamentos M:N, **não** se deve adicionar a PK de uma tabela como FK na outra (isso só vale para 1:N).
> - A solução correta é criar uma **tabela de ligação**.
> - O relacionamento M:N dá origem a **dois relacionamentos 1:N** (tabela de ligação ↔ JUIZ; tabela de ligação ↔ ASSISTENTE).

## 3. Mapeamento de Relacionamento Ternário

- Um relacionamento que envolve **três entidades** é mapeado como uma **tabela própria**.
- A tabela contém as **PKs das três entidades** (FKs) e os atributos do relacionamento.
- A PK é a combinação das três PKs (ou a combinação que garanta a unicidade).

**Exemplo (Fornecedor – Projeto – Material):**
```
FORNECEDOR (CodF, Nome)
PROJETO (CodP, Nome)
MATERIAL (CodM, Nome)
FORNECE (CodF, CodP, CodM, Quantidade)   -- PK: (CodF, CodP, CodM)
```

> ### 3.1 Observação sobre o atributo "Quantidade"
> - A `Quantidade` **não faz parte da chave** (pode repetir).
> - O que não pode repetir é a **combinação dos três códigos** (a mesma trinca de fornecedor, projeto e material).

## 4. Mapeamento de Generalização/Especialização (Disjunção)

- **Disjunção (`d`):** um empregado pode ser médico, advogado ou engenheiro, mas **não mais de um**.
- Estratégias de mapeamento:
  1. **Tabela única com discriminador** (mais simples para casos com poucos atributos específicos).
  2. **Tabela para superclasse + tabela para cada subclasse** (com FK para a superclasse).
  3. **Tabela para cada subclasse repetindo os atributos da superclasse** (menos comum).

> ### 4.1 Restrição de exclusividade
> - Para garantir que um empregado não pertença a mais de uma subclasse, pode-se adicionar uma **restrição** no banco de dados (ex.: `CHECK`, ou controle na aplicação).

## 5. Fusão de Tabelas (caso raro)

- A fusão ocorre em relacionamentos **1:1 com participação total de ambos os lados** `(1,1)`.
- Exemplo: **País tem uma Constituição** – pode-se fundir as duas tabelas em uma única.

> ### 5.1 Quando NÃO fundir
> - Se a participação for opcional em algum lado, a fusão não é recomendada (geraria muitos valores nulos).
> - A fusão também não é adequada se as entidades tiverem muitos atributos específicos diferentes.

## 6. Questões de Concurso Comentadas

### 6.1 (CESPE/2018/MPE-PI – Analista Ministerial)

**Modelo lógico proposto:**
```
TipoDeProduto (CodigoTipoProduto, DescricaoTipoProduto)
Produto (CodigoProduto, DescricaoProduto, PrecoProduto, CodigoTipoProduto)
-- CodigoTipoProduto referencia TipoDeProduto
```

**Item:** "nesse modelo lógico, um TipoDeProduto se relaciona com várias entidades do tipo Produto. Com essa notação, a visão do cliente se torna clara e direta sobre como serão implementados e armazenados os dados."

**Gabarito:** **Certo (C)**.

**Comentário:**
- O modelo lógico mostra claramente que `TipoDeProduto` (1) se relaciona com vários `Produto` (N) via FK `CodigoTipoProduto`.
- A notação relacional é direta sobre a implementação (como os dados serão armazenados).

### 6.2 (CESPE/2018/POLÍCIA FEDERAL – Agente)

**Item (com diagrama ER):** "Considerando-se apenas o diagrama apresentado, infere-se que, na aplicação das regras para a transformação do modelo ER em um modelo relacional, é necessário realizar a fusão das tabelas referentes às entidades envolvidas no relacionamento."

**Gabarito:** **Errado (E)**.

**Comentário:**
- A **fusão de tabelas** é uma estratégia **rara**, usada apenas em relacionamentos **1:1 com participação total** de ambos os lados.
- No diagrama, não há indicação de que esse seja o caso.
- A transformação padrão para a maioria dos relacionamentos é **adição de coluna** (1:N) ou **tabela própria** (M:N), não fusão.

### 6.3 (CESPE/2018/POLÍCIA FEDERAL – Agente)

**Item:** "Paulo deve invalidar o modelo ER em questão, pois ele está semanticamente errado, já que não pode haver chaves primárias com nomes iguais, ainda que em entidades distintas."

**Gabarito:** **Errado (E)**.

**Comentário:**
- **Não há problema** em duas entidades diferentes terem um atributo com o mesmo nome (ex.: `codigo` em `TipoDeProduto` e `codigo` em `Produto`).
- Cada atributo pertence a uma entidade/tabela diferente e é independente.
- O que não pode haver é **duplicação de valores** dentro da mesma tabela para a chave primária.

### 6.4 (FCC/2017/TRE-PR – Técnico Judiciário)

**Item (Juiz – Assistente – relação M:N):** "Se Juiz e Assistente forem entidades de um modelo de dados relacional, a cardinalidade entre elas será n:m."

**Alternativa correta:** **b) será necessário criar uma tabela de ligação entre Juiz e Assistente e o relacionamento n:m dará lugar a dois relacionamentos 1:n.**

**Comentário:**
- Relacionamentos M:N são implementados com **tabela própria** (tabela de ligação/associação).
- A tabela de ligação contém as PKs das duas entidades (como FKs).
- O relacionamento M:N transforma-se em **dois relacionamentos 1:N**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/MPE-PI/2018) | C |
| 02 (CESPE/PF/2018) | E |
| 03 (CESPE/PF/2018) | E |
| 04 (FCC/TRE-PR/2017) | b |

---

## Síntese para Revisão Rápida

| TIPO DE RELACIONAMENTO | MAPEAMENTO | PK DA TABELA RESULTANTE |
| --- | --- | --- |
| **1:N** | Adicionar FK na tabela do lado N (filho). | PK original da tabela filho. |
| **1:1** | Adicionar FK em uma das tabelas (ou fusão, em caso de participação total de ambos). | PK original de cada tabela. |
| **M:N** | Tabela própria (tabela de ligação). | Combinação das duas PKs (chave composta). |
| **Ternário** | Tabela própria com as três PKs. | Combinação das três PKs. |
| **Atributo multivalorado** | Tabela própria com PK da entidade + atributo. | Combinação da PK + atributo. |
| **Entidade fraca** | Tabela própria com PK da entidade forte + chave parcial. | Combinação da PK da entidade forte + chave parcial. |

---

*Material complementar à aula "Mapeamento ER-Relacional II" (professor Washington Almeida, Gran Concursos).*