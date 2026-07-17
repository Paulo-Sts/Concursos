# Anotações – Banco de Dados – Normalização II (2FN, 3FN, FNBC)

## 1. Segunda Forma Normal (2FN) – Continuação

### 1.1 Definição

- Uma relação está na **2FN** se:
  1. Estiver na **1FN**.
  2. Todo atributo não chave possuir **dependência funcional total** em relação à chave primária (ou seja, não pode haver dependência parcial).

### 1.2 Exemplo didático (Aluno × Curso)

**Tabela NÃO normalizada (PK composta: {ID_Aluno, ID_Curso}):**

| ID_Aluno | ID_Curso | Nome_Aluno | Nome_Curso | Professor |
| --- | --- | --- | --- | --- |
| 101 | 1 | João | Matemática | Prof. Carlos |
| 101 | 2 | João | Física | Prof. Maria |

**Problemas (dependências parciais):**
- `ID_Aluno → Nome_Aluno` (Nome_Aluno depende apenas do ID_Aluno, não da chave completa).
- `ID_Curso → Nome_Curso` e `ID_Curso → Professor` (dependem apenas do ID_Curso).

**Decomposição para 2FN:**

**Tabela ALUNO (PK: ID_Aluno):**
| ID_Aluno | Nome_Aluno |
| --- | --- |
| 101 | João |

**Tabela CURSO (PK: ID_Curso):**
| ID_Curso | Nome_Curso | Professor |
| --- | --- | --- |
| 1 | Matemática | Prof. Carlos |
| 2 | Física | Prof. Maria |

**Tabela ALUNO_CURSO (PK: {ID_Aluno, ID_Curso}):**
| ID_Aluno | ID_Curso |
| --- | --- |
| 101 | 1 |
| 101 | 2 |

## 2. Dependência Funcional Transitiva

### 2.1 Definição

- Uma **dependência funcional transitiva** ocorre quando:
  - `A → B`
  - `B → C`
  - Então `A → C` (transitiva)
- **Problema:** um atributo não chave (`C`) depende de outro atributo não chave (`B`), que por sua vez depende da chave (`A`).

### 2.2 Exemplo (Pedido × Vendedor)

**Tabela PEDIDO (PK: NumPedido):**

| NumPedido | CodVendedor | NomeVendedor |
| --- | --- | --- |
| 101 | 1 | João |
| 102 | 1 | João |
| 103 | 2 | Maria |

**Dependência transitiva:**
- `NumPedido → CodVendedor` (cod_vendedor depende do pedido)
- `CodVendedor → NomeVendedor` (nome_vendedor depende do cod_vendedor)
- `NumPedido → NomeVendedor` (transitiva)

## 3. Terceira Forma Normal (3FN)

### 3.1 Definição

- Uma relação está na **3FN** se:
  1. Estiver na **2FN**.
  2. Nenhum atributo não chave for **transitivamente dependente** da chave primária.

### 3.2 Solução para o exemplo acima

**Decomposição para 3FN:**

**Tabela PEDIDO (PK: NumPedido):**
| NumPedido | CodVendedor |
| --- | --- |
| 101 | 1 |
| 102 | 1 |
| 103 | 2 |

**Tabela VENDEDOR (PK: CodVendedor):**
| CodVendedor | NomeVendedor |
| --- | --- |
| 1 | João |
| 2 | Maria |

- Elimina a dependência transitiva (NomeVendedor agora depende diretamente de CodVendedor, que é PK da nova tabela).

## 4. Forma Normal de Boyce-Codd (FNBC)

### 4.1 Definição

- Uma relação está na **FNBC** se, **para toda dependência funcional `X → Y`, `X` é uma superchave**.
- A FNBC é **mais restritiva** que a 3FN.
- Toda relação na FNBC também está na 3FN, mas **nem toda relação na 3FN está na FNBC**.

> ### 4.1.1 Lembretes
> - **Superchave:** qualquer conjunto de atributos que identifica unicamente uma tupla.
> - **Chave primária:** superchave de **cardinalidade mínima**.
> - **Chave candidata:** superchave mínima (todas as possíveis chaves primárias).

### 4.2 Exemplo (Leciona – Aluno, Disciplina, Instrutor)

**Tabela LECIONA:**

| Aluno | Disciplina | Instrutor |
| --- | --- | --- |
| João | Banco de dados | Navathe |
| João | Linguagem de Programação | Deitel |
| João | Sistemas Operacionais | Tanenbaum |
| Ana | Banco de dados | Korth |
| Ana | Engenharia de Software | Pressman |
| Artur | Linguagem de Programação | Mark |
| Pedro | Banco de Dados | Date |

**Dependências funcionais:**
- `{Aluno, Disciplina} → Instrutor` (PK composta candidata)
- `Instrutor → Disciplina` (um instrutor leciona uma única disciplina? No exemplo, parece que sim)

**Problema:** a dependência `Instrutor → Disciplina` tem um **determinante que não é superchave** (`Instrutor` não identifica unicamente a tupla por si só, pois um instrutor pode aparecer em várias linhas com alunos diferentes). Isso viola a FNBC.

**Solução (decomposição):**

**Tabela INSTRUTOR_DISCIPLINA (PK: Instrutor):**
| Instrutor | Disciplina |
| --- | --- |
| Navathe | Banco de dados |
| Deitel | Linguagem de Programação |
| Tanenbaum | Sistemas Operacionais |

**Tabela ALUNO_INSTRUTOR (PK: {Aluno, Instrutor}):**
| Aluno | Instrutor |
| --- | --- |
| João | Navathe |
| João | Deitel |
| Ana | Korth |

- Agora, toda dependência tem determinante que é superchave.

> ### 4.2.1 Comparação 3FN vs. FNBC
> - **3FN:** elimina dependências transitivas de atributos não chave.
> - **FNBC:** elimina qualquer dependência funcional cujo determinante **não seja superchave** (inclusive quando o determinante é parte da chave).

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/2018/PF – Perito Criminal)

**Item:** "A tabela colaborador está na primeira forma normal."

**Gabarito: Certo (C)**.

**Comentário:** Para estar na 1FN, a tabela não pode ter atributos multivalorados, compostos ou grupos de repetição. Se a tabela não apresenta esses problemas, está em 1FN.

### 5.2 (FUNCAB/2010/SES-GO – Análise de Sistemas)

**Item:** "Uma variável está na Forma Normal de Boyce e Codd (FNBC) se, e somente se:"

**Alternativa correta:** **b) seus únicos determinantes forem chaves candidatas.**

**Comentário:**
- a) Incorreto – dependências multivaloradas são tratadas na 4FN.
- c) Incorreto – isso é definição de 2FN (dependência total da PK).
- d) Incorreto – isso é definição de 3FN (eliminação de dependência transitiva).
- e) Incorreto – a FNBC não exige que haja apenas uma chave candidata.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2018) | C |
| 02 (FUNCAB/2010) | b |

---

## Síntese para Revisão Rápida

| FORMA NORMAL | CRITÉRIO | O QUE ELIMINA |
| --- | --- | --- |
| **1FN** | Valores atômicos | Atributos multivalorados e compostos |
| **2FN** | 1FN + dependência total da PK | Dependência funcional **parcial** |
| **3FN** | 2FN + dependência direta da PK | Dependência funcional **transitiva** |
| **FNBC** | 3FN + todo determinante é superchave | Dependências funcionais com determinante não superchave |

> ### 5.1 Dependências funcionais – resumo
> - **Parcial:** atributo depende de **parte** da chave → viola 2FN.
> - **Transitiva:** atributo depende de **atributo não chave** → viola 3FN.
> - **Determinante não superchave:** → viola FNBC.

---

*Material complementar à aula "Banco de Dados – Normalização II" (professor Washington Henrique Almeida, Gran Concursos).*