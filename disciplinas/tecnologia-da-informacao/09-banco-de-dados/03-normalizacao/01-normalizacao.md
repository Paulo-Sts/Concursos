# Anotações – Banco de Dados – Normalização

## 1. Conceito de Normalização

- **Normalização:** conjunto de técnicas aplicáveis a uma tabela com o objetivo de corrigir erros de projeto que resultam em **anomalias de atualização**.
- Consiste em analisar relações para satisfazer requisitos cada vez mais rigorosos (**Formas Normais** mais elevadas).
- Envolve a **decomposição de esquemas** para evitar anomalias de inclusão, exclusão e modificação.

## 2. Anomalias de Atualização

São problemas decorrentes de bancos de dados **não normalizados**, com redundância de dados e dependências parciais/transitivas.

| TIPO DE ANOMALIA | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Inserção** | Ao inserir um registro, exige-se informações de outra tabela, ou é necessário inserir valores nulos. | Inserir um novo empregado exige incluir todos os dados do departamento (NomeDep, SiglaDep) ou deixar campos nulos. |
| **Exclusão** | Ao excluir um registro, perdem‑se dados relacionados a outra entidade. | Excluir a funcionária Juliana (CPF=77) remove também todas as informações do Departamento Jurídico. |
| **Modificação** | Ao alterar um dado, é necessário atualizar múltiplas ocorrências espalhadas pela tabela. | Alterar a sigla do departamento (TI → TEC) requer modificar todos os registros de funcionários desse departamento. |

> ### 2.1 Causa raiz
> - A causa das anomalias é a **redundância de dados** (repetição desnecessária de informações) e as **dependências funcionais** mal gerenciadas.

## 3. Formas Normais – Visão Geral

| FORMA NORMAL | OBJETIVO PRINCIPAL | O QUE ELIMINA |
| --- | --- | --- |
| **1FN** | Valores atômicos | Atributos multivalorados e compostos; grupos de repetição. |
| **2FN** | Dependência total | Dependências funcionais **parciais** (atributos não chave dependem de parte da PK). |
| **3FN** | Dependência direta | Dependências funcionais **transitivas** (atributos não chave dependem de outro atributo não chave). |
| **BCNF** | Normalização avançada | Dependências funcionais em que o determinante não é uma superchave. |

## 4. Primeira Forma Normal (1FN)

### 4.1 Definição

- Uma relação está na **1FN** se, e somente se, **todos os seus atributos contêm apenas valores atômicos (indivisíveis)** .
- Não pode conter:
  - Atributos **multivalorados**.
  - Atributos **compostos**.
  - Combinações destes (grupos de repetição).

### 4.2 Exemplo – Antes da 1FN (atributo multivalorado)

**Tabela DEPARTAMENTO (não normalizada):**

| Código | Nome | Sigla | Localização |
| --- | --- | --- | --- |
| 1 | Financeiro | FIN | São Paulo, Rio de Janeiro |
| 2 | Tecnologia da Informação | TI | Salvador, Belo Horizonte |

- O atributo `Localização` é **multivalorado** (mais de um valor por registro).
- Viola a 1FN.

### 4.3 Após a 1FN (decomposição)

**Tabela DEPARTAMENTO:**

| Código | Nome | Sigla |
| --- | --- | --- |
| 1 | Financeiro | FIN |
| 2 | Tecnologia da Informação | TI |

**Tabela DEPARTAMENTO_LOCALIZACAO:**

| Código | Localização |
| --- | --- |
| 1 | São Paulo |
| 1 | Rio de Janeiro |
| 2 | Salvador |
| 2 | Belo Horizonte |

- A decomposição elimina o atributo multivalorado, criando uma tabela separada.
- A nova tabela tem PK composta (`Código`, `Localização`).

## 5. Dependência Funcional (DF)

### 5.1 Conceito

- **Dependência funcional:** em uma tabela relacional, um atributo Y **depende funcionalmente** de um atributo X quando, para cada valor de X, há **um único valor** correspondente em Y (em todas as tuplas).
- **Notação:** `X → Y` (X determina Y).

### 5.2 Exemplo (CLIENTE)

**Tabela:**

| CPF | Nome | DataNascimento |
| --- | --- | --- |
| 11 | João Pereira | 10/01/1980 |
| 22 | Ana de Carvalho | 01/01/1994 |

**Dependências funcionais:**
- `CPF → Nome` (o CPF determina o Nome)
- `CPF → DataNascimento`
- `Nome → CPF`? **Não** (nomes podem se repetir).
- `DataNascimento → CPF`? **Não** (várias pessoas podem nascer na mesma data).

### 5.3 Tipos de Dependência Funcional

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Total** | Atributo depende da chave completa. | `{CPF, CodProj} → Horas` (Horas depende de ambos). |
| **Parcial** | Atributo depende apenas de **parte** da chave. | `CodProj → NomeProj` (NomeProj depende apenas de CodProj, não do CPF). |
| **Transitiva** | Atributo depende de outro atributo não chave (que depende da chave). | `CodDep → Sigla`, `Sigla → Localizacao` → `CodDep → Localizacao` (transitiva). |

## 6. Segunda Forma Normal (2FN)

### 6.1 Definição

- Uma relação está na **2FN** se:
  1. Estiver na **1FN**.
  2. **Todo atributo não chave possuir dependência funcional total em relação à chave primária** (não pode haver dependência parcial).

### 6.2 Exemplo (EMPREGADO_PROJETO – NÃO normalizado)

**Tabela (PK composta: {CPF, CodProj}):**

| CPF | NomeEmp | CodProj | NomeProj | Horas |
| --- | --- | --- | --- | --- |
| 11 | João Pereira | 001 | Rodovia | 15 |
| 22 | Ana de Carvalho | 001 | Rodovia | 20 |

**Dependências funcionais parciais (violam 2FN):**
- `CPF → NomeEmp` (NomeEmp depende só do CPF, não da chave completa).
- `CodProj → NomeProj` (NomeProj depende só do CodProj, não da chave completa).

### 6.3 Decomposição para 2FN

**Tabela EMPREGADO (PK: CPF):**
| CPF | NomeEmp |
| --- | --- |
| 11 | João Pereira |
| 22 | Ana de Carvalho |

**Tabela PROJETO (PK: CodProj):**
| CodProj | NomeProj |
| --- | --- |
| 001 | Rodovia |
| 002 | Ponte |

**Tabela EMPREGADO_PROJETO (PK: {CPF, CodProj}):**
| CPF | CodProj | Horas |
| --- | --- | --- |
| 11 | 001 | 15 |
| 22 | 001 | 20 |

> ### 6.3.1 Por que funciona?
> - `NomeEmp` agora está na tabela EMPREGADO – depende totalmente da PK (`CPF`).
> - `NomeProj` agora está na tabela PROJETO – depende totalmente da PK (`CodProj`).
> - `Horas` depende da chave completa `{CPF, CodProj}` – é dependência total.

## 7. Síntese para Revisão Rápida

| FORMA NORMAL | CRITÉRIO | O QUE DEVE SER ELIMINADO |
| --- | --- | --- |
| **1FN** | Valores atômicos | Atributos multivalorados e compostos. |
| **2FN** | 1FN + dependência total da PK | Dependências funcionais **parciais**. |
| **3FN** | 2FN + dependência direta da PK | Dependências funcionais **transitivas**. |

> ### 7.1 Dependência funcional (forma resumida)
> - **Parcial:** atributo depende de **parte** da chave (viola 2FN).
> - **Transitiva:** atributo depende de um **atributo não chave** (viola 3FN).

---

*Material complementar à aula "Banco de Dados – Normalização" (professor Washington Henrique Almeida, Gran Concursos).*