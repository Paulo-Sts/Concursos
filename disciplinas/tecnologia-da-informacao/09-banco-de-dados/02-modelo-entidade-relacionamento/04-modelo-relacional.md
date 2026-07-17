# Anotações – Banco de Dados – Modelo Relacional

## 1. Introdução ao Modelo Relacional

- **Criador:** Edgar F. Codd, em 1970 (IBM).
- **Representação:** banco de dados como um **conjunto de relações** (tabelas).
- **Fundamento:** teoria de conjuntos e álgebra relacional.
- **Linguagem padrão:** SQL (Structured Query Language), baseada na álgebra relacional.
- **Terminologia formal:**

| CONCEITO COLOQUIAL | TERMO FORMAL |
| --- | --- |
| Tabela | **Relação** |
| Linha | **Tupla** |
| Cabeçalho de coluna | **Atributo** |
| Tipo de dado permitido | **Domínio** |

> ### 1.1 Relação entre MER e Modelo Relacional
> - No modelo conceitual (MER): **entidade**.
> - No modelo lógico (relacional): **relação**.
> - No modelo físico: **tabela**.

## 2. As 13 Regras de Codd (Regra 0 a 12)

Codd estabeleceu 13 regras (contando a partir da regra 0) para que um sistema seja considerado um **Sistema Gerenciador de Banco de Dados Relacional**.

| REGRA | NOME | DESCRIÇÃO RESUMIDA |
| --- | --- | --- |
| **0** | Qualificação | O sistema deve ser capaz de gerenciar bancos de dados usando exclusivamente suas capacidades relacionais. |
| **1** | Informação | Toda informação no BD deve ser representada como valores em tabelas. |
| **2** | Acesso Garantido | Cada dado deve ser acessível por combinação de nome da tabela, chave primária e nome da coluna. |
| **3** | Tratamento de Nulos | Valores nulos devem ser suportados de forma sistemática. |
| **4** | Catálogo Online | O catálogo deve ser armazenado no modelo relacional e acessível via SQL. |
| **5** | Sublinguagem Ampla | Deve haver uma linguagem que suporte definição, manipulação e consulta de dados (SQL). |
| **6** | Atualização por Visões | Visões devem ser atualizáveis. |
| **7** | Operações de Alto Nível | Inserção, atualização e exclusão devem operar sobre conjuntos de dados, não registro a registro. |
| **8** | Independência Física | Alterações no armazenamento físico não afetam os programas de aplicação. |
| **9** | Independência Lógica | Alterações no esquema lógico não afetam as visões e aplicações. |
| **10** | Independência de Integridade | Restrições de integridade devem ser definíveis em SQL e armazenadas no catálogo. |
| **11** | Independência de Distribuição | O SGBD deve funcionar independentemente da distribuição física dos dados. |
| **12** | Não Transposição | Nenhuma das regras anteriores pode ser violada (regra de garantia). |

> ### 2.1 Regra 6 – Atualização por Visões
> - **Visão (VIEW):** consulta armazenada (tabela virtual).
> - **Objetivo:** segurança e separação de diferentes visões dos dados.
> - Atualizações (INSERT/UPDATE/DELETE) podem ser feitas via VIEW, mas com restrições.
> - **Boa prática:** usar VIEW para consultas; realizar inserções diretamente nas tabelas base.

## 3. Conceitos Básicos do Modelo Relacional

### 3.1 Esquema de Relação

**Notação:** `R(A1, A2, ..., An)`

- **R** = nome da relação.
- **A1, A2, ..., An** = atributos.
- **n** = grau da relação (número de atributos).

**Exemplos:**
- `ESTUDANTE (Matricula, Nome, Telefone, Curso, Idade)` – grau 5.
- `DISCIPLINA (Codigo, Nome, Carga_Horaria, Creditos)` – grau 4.

### 3.2 Características de uma Tabela Relacional

| ELEMENTO | DESCRIÇÃO |
| --- | --- |
| **Coluna (atributo)** | Nome distinto; representa um atributo. |
| **Domínio** | Conjunto de valores permitidos para um atributo (valor atômico/indivisível). |
| **Valor Nulo** | Atributo sem valor ou com valor desconhecido. |
| **Linha (tupla)** | Distinta na tabela; representa um registro. |

> ### 3.2.1 Nulo vs. Vazio
> - **Nulo (`NULL`):** ausência de valor (desconhecido ou não aplicável).
> - **Vazio (string vazia):** é um valor (caractere `''`), diferente de `NULL`.
> - Em bancos de dados, `SELECT` retorna `NULL` quando o campo não tem valor.

## 4. Restrições no Modelo Relacional

### 4.1 Restrição de Domínio

- Define os valores válidos para um atributo (tipo de dado + regras adicionais).

| ATRIBUTO | DOMÍNIO (EXEMPLO) |
| --- | --- |
| CPF | String de 11 caracteres numéricos (`CHAR(11)`) |
| Placa do Veículo | String: 3 letras + espaço + 4 dígitos (ex.: `XYZ 9999`) |
| Idade do Servidor | Inteiro entre 18 e 100 |

### 4.2 Restrição de Chave Primária

- Garante a **identificação única** de cada tupla.
- **Características:**
  - **Unicidade:** não pode haver duas tuplas com o mesmo valor para a chave primária.
  - **Não nulidade:** a chave primária não pode ser `NULL` (nem seus componentes, se for composta).
- **Chave Composta:** dois ou mais atributos formam a chave primária. Nenhum deles pode ser `NULL`.

### 4.3 Restrição de Integridade Referencial

- Mantém a **consistência entre tuplas de duas relações**.
- Uma chave estrangeira (FK) em uma relação deve:
  1. Fazer referência a uma chave primária (PK) existente em outra relação.
  2. Pode ser `NULL` (se a participação for opcional).
- **Exemplo:** a tabela `SERVIDOR` tem uma FK `Cod_Departamento` que referencia a PK `Codigo` da tabela `DEPARTAMENTO`.
  - Um servidor pode não estar alocado a nenhum departamento → FK pode ser `NULL`.

> ### 4.3.1 Comparação
> | CHAVE | PODE SER NULL? | PODE SE REPETIR? |
> | --- | --- | --- |
> | **Chave Primária (PK)** | Não | Não |
> | **Chave Estrangeira (FK)** | Sim (se participação opcional) | Sim |

## 5. Violação de Restrições (Operações)

| OPERAÇÃO | VIOLAÇÃO | EXEMPLO |
| --- | --- | --- |
| **INSERT** | Inserir `NULL` na PK | Inserir servidor com `Matricula = NULL` → viola integridade da entidade. |
| **INSERT** | Inserir PK duplicada | Inserir servidor com matrícula já existente → viola restrição de chave. |
| **INSERT** | Inserir FK inexistente | Inserir servidor com `Cod_Departamento` que não existe → viola integridade referencial. |
| **DELETE** | Excluir PK referenciada | Excluir departamento que ainda tem servidores → viola integridade referencial. |

> ### 5.1 Comportamentos possíveis para DELETE de PK referenciada
> - **RESTRICT / NO ACTION:** impede a exclusão se houver referências.
> - **CASCADE:** exclui também os registros que referenciam a PK.
> - **SET NULL:** define a FK como `NULL` nos registros referenciados.

## 6. Questões de Concurso Comentadas

### 6.1 (FCC/2017/DPE-RS – Analista)

**Item:** "Supondo K um conjunto de atributos da tabela T, K terá a propriedade da unicidade se:"

**Gabarito:** **d) Não houver duas tuplas de T com o mesmo valor para K.**

**Comentário:** A unicidade significa que não pode haver duas tuplas com os mesmos valores para o conjunto de atributos K.

### 6.2 (IFB/2017 – Professor/Informática)

**Item:** "Na terminologia formal do modelo relacional, uma linha, um cabeçalho de coluna e a tabela são chamados, respectivamente, de:"

**Gabarito:** **b) Tupla, atributo e relação.**

### 6.3 (CESPE/2016/TCE-PA – Auditor)

**Item:** "No modelo relacional de dados, uma tabela é um conjunto ordenado de campos."

**Gabarito:** **Errado (E)**.

**Comentário:** No modelo relacional, a relação (tabela) é um **conjunto**, e conjuntos **não possuem ordem** (nem entre as tuplas, nem entre os atributos).

### 6.4 (CESPE/2016/FUNPRESP-EXE – Especialista)

**Item:** "A integridade referencial assegura que os valores dos campos presentes na chave estrangeira apareçam na chave primária da mesma tabela."

**Gabarito:** **Errado (E)**.

**Comentário:** A chave estrangeira geralmente referencia a chave primária de **outra** tabela. A exceção é o **autorrelacionamento**, em que a FK referencia a PK da **mesma** tabela.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FCC/2017) | d |
| 02 (IFB/2017) | b |
| 03 (CESPE/2016/TCE-PA) | E |
| 04 (CESPE/2016/FUNPRESP) | E |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Relação** | Tabela no modelo relacional. | `ALUNO` |
| **Tupla** | Linha da tabela. | `(123, "Ana", "9999-9999", "Computação", 20)` |
| **Atributo** | Coluna da tabela. | `Nome`, `Matricula` |
| **Domínio** | Conjunto de valores válidos. | `Matricula` = inteiro de 6 dígitos. |
| **Chave Primária** | Identifica unicamente cada tupla. | `Matricula` |
| **Chave Estrangeira** | Referência a PK de outra tabela. | `Cod_Departamento` em `SERVIDOR` |
| **Integridade Referencial** | FK deve referenciar PK existente ou ser NULL. | Dependente sempre vinculado a um funcionário. |

---

*Material baseado na aula do professor Washington Henrique Almeida (Gran Concursos).*