# Anotações – Banco de Dados – Mapeamento ER-Relacional

## 1. Projeto Lógico e Físico (Revisão)

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **Projeto Lógico** | Preocupa-se com a consistência dos dados e a estrutura das tabelas (como os dados serão armazenados). |
| **Projeto Físico** | Inclui comandos SQL, definição de índices, espaço em memória, particionamento, etc. – gerenciado pelo SGBD. |

> ### 1.1 Observação
> - A estratégia de **Banco de Dados Distribuído (BDD)** é menos utilizada atualmente, devido à evolução de outras formas de armazenamento (ex.: NoSQL, cloud).

## 2. Notação do Modelo Relacional (Textual)

- A notação do modelo relacional é **textual**.
- O nome da relação vem primeiro, seguido pelos atributos entre parênteses.
- Atributos **sublinhados** representam a **chave primária**.

**Exemplo:**
```
MEDICO (CRM, NOME, ENDERECO, TELEFONE)
PACIENTE (CPF, NOME, ENDERECO, TELEFONE)
EXAME (CODIGO, NOME, RESULTADO, COD_CONSULTA)
CONSULTA (CODIGO, OBSERVACAO)
```

> ### 2.1 Correspondência de nomenclatura
> - **MER (Conceitual):** entidade.
> - **Modelo lógico (Relacional):** relação.
> - **Modelo físico:** tabela.

## 3. Objetivos do Mapeamento ER-Relacional

O mapeamento visa:

- Elaborar um modelo lógico com **boa performance** em relação às requisições.
- Simplificar o **desenvolvimento e a manutenção** de sistemas.

### 3.1 Regras Básicas (para otimização)

| REGRA | DESCRIÇÃO | JUSTIFICATIVA |
| --- | --- | --- |
| **I. Evitar o uso de junções** | Junções (JOINs) geram produto cartesiano e podem prejudicar a performance. | Toda junção é uma operação custosa; deve-se evitar quando possível, mas algumas são inevitáveis. |
| **II. Reduzir o número de chaves primárias** | Chaves primárias criam índices, que ocupam espaço e podem tornar a tabela mais lenta. | Índices são estruturas paralelas; usar chaves desnecessárias gera overhead. |
| **III. Evitar campos opcionais** | Campos opcionais geram muitos valores nulos/vazios, ocupando espaço. | Campos com muitos valores nulos não são ideais para o modelo relacional. |

> ### 3.1.1 Nulo vs. Vazio (reforço)
> - **Nulo:** ausência de valor – **não ocupa espaço** no banco.
> - **Vazio (string vazia):** é um valor – **ocupa espaço** e deve ser tratado como um dado (ex.: `''`).

## 4. Estratégias de Mapeamento

As três estratégias principais para mapear elementos do MER para o modelo relacional são:

| ESTRATÉGIA | DESCRIÇÃO | QUANDO USAR |
| --- | --- | --- |
| **Tabela própria** | Cria uma nova tabela para o elemento (ex.: atributo multivalorado, relacionamento N:N). | Atributos multivalorados; relacionamentos muitos-para-muitos; entidades fracas. |
| **Adição de coluna** | Adiciona uma coluna (FK) à tabela existente. | Relacionamentos 1:N ou 1:1 (do lado N ou opcional). |
| **Fusão de tabelas** | Combina duas tabelas em uma única. | Casos raros; geralmente em relacionamentos 1:1 com participação total de ambos os lados `(1,1)`. |

> ### 4.1 Fusão de tabelas
> - É a estratégia **mais rara**.
> - Exemplo: se todo país tem **uma** constituição, pode-se fundir as tabelas `PAIS` e `CONSTITUICAO` em uma única tabela.

## 5. Mapeamento de Elementos Específicos

### 5.1 Entidade Forte

- Mapeada para uma **tabela própria**.
- A chave primária (PK) da entidade torna-se a PK da tabela.

**Exemplo:**
```
CLIENTE (CPF, Nome, Endereco)
```

### 5.2 Entidade Fraca

- A tabela da entidade fraca recebe a **PK da entidade forte** (chave estrangeira) + sua **chave parcial**.
- A PK da tabela resultante é a **combinação** da PK da entidade forte com a chave parcial da entidade fraca.

**Exemplo (Dependente de Funcionário):**
```
DEPENDENTE (CPF_Funcionario, Nome_Dependente, Data_Nasc)
-- PK: (CPF_Funcionario, Nome_Dependente)
```

### 5.3 Atributo Multivalorado

- Deve ser mapeado para uma **tabela própria** (não pode ficar na tabela principal, pois violaria a 1ª Forma Normal).
- A tabela conterá a **PK da entidade** + o atributo multivalorado.
- A PK da nova tabela é a **combinação** da PK da entidade com o atributo multivalorado.

**Exemplo (Telefone de Cliente):**
```
TELEFONE_CLIENTE (CPF_Cliente, Telefone)
-- PK: (CPF_Cliente, Telefone)
```

### 5.4 Auto-Relacionamento

- Um campo da própria tabela referencia a PK da mesma tabela (chave estrangeira para a própria tabela).
- Pode permitir `NULL` para o nó raiz (ex.: órgão que não tem superior).

**Exemplo (Órgão com subordinação):**
```
ORGAO (Codigo, Nome, Cod_Superior)
-- Cod_Superior referencia Codigo da própria tabela (pode ser NULL)
```

### 5.5 Relacionamento 1:1

- Pode ser mapeado de duas formas:
  - **Adição de coluna:** a PK de uma das tabelas é adicionada como FK na outra (escolhe-se o lado com participação opcional, se houver).
  - **Fusão de tabelas:** quando ambos os lados têm participação total `(1,1)`.

**Exemplo (Casamento – HOMEM e MULHER):**

**Opção 1 – Adicionar FK em HOMEM:**
```
HOMEM (CodHomem, NomeHomem, CodEsposa)
MULHER (CodMulher, NomeMulher)
```

**Opção 2 – Adicionar FK em MULHER:**
```
HOMEM (CodHomem, NomeHomem)
MULHER (CodMulher, NomeMulher, CodMarido)
```

> ### 5.5.1 Regra prática
> - A FK deve ser adicionada na tabela que tem participação **opcional** ou, se ambos forem opcionais, em qualquer uma.
> - A FK pode ser `NULL` se a participação for opcional.

### 5.6 Relacionamento 1:N

- A **PK da entidade do lado 1** (pai) é adicionada como **FK na tabela do lado N** (filho).
- Exemplo: DEPARTAMENTO (1) – EMPREGADO (N) → FK `Cod_Departamento` em EMPREGADO.

### 5.7 Relacionamento M:N

- Deve ser criada uma **tabela própria** (tabela de associação/relacionamento).
- A tabela conterá as **PKs das duas entidades** (FKs) e, possivelmente, atributos do relacionamento.
- A PK da tabela de associação é a **combinação das duas PKs** (chave composta).

**Exemplo (MEDICO consulta PACIENTE):**
```
CONSULTA (CRM_Medico, CPF_Paciente, Data_Consulta)
-- PK: (CRM_Medico, CPF_Paciente, Data_Consulta)
```

### 5.8 Generalização/Especialização

- Estratégias de mapeamento:
  1. **Tabela para cada subclasse:** cada subclasse tem sua própria tabela com seus atributos específicos + FK para a superclasse.
  2. **Tabela única para superclasse com atributos de todas as subclasses:** inclui um discriminador (tipo) para identificar a subclasse.
  3. **Tabela para cada subclasse com atributos da superclasse:** cada subclasse repete os atributos da superclasse (menos comum).

## 6. Exemplo de Mapeamento – Relacionamento 1:N (Departamento – Empregado)

**Regra:** um departamento (1) tem vários empregados (N); cada empregado trabalha em um departamento (1).

**Esquema resultante:**
```
DEPARTAMENTO (Codigo, Nome, Sigla)
EMPREGADO (Matricula, Nome, Cod_Departamento)
-- FK: Cod_Departamento referencia Codigo em DEPARTAMENTO
```

> ### 6.1 Se houver um gerente
> - A FK `Cod_Gerente` pode ser adicionada em `DEPARTAMENTO`, pois cada departamento tem **um** gerente (que é um empregado).
> - Assim, `DEPARTAMENTO` passa a ter uma FK para `EMPREGADO`.

**Exemplo final:**
```
DEPARTAMENTO (Codigo, Nome, Sigla, Cod_Gerente)
EMPREGADO (Matricula, Nome, Cod_Departamento)
```

## GABARITO (as questões não estão no arquivo; manter a estrutura)

---

## Síntese para Revisão Rápida

| ELEMENTO DO MER | MAPEAMENTO PARA MODELO RELACIONAL |
| --- | --- |
| Entidade Forte | Tabela própria com seus atributos; PK é a chave da entidade. |
| Entidade Fraca | Tabela própria com PK da entidade forte + chave parcial (PK composta). |
| Atributo Multivalorado | Tabela própria com PK da entidade + atributo (PK composta). |
| Relacionamento 1:1 | Adição de coluna (FK) em uma das tabelas; ou fusão de tabelas (raro). |
| Relacionamento 1:N | Adição de coluna (FK) na tabela do lado N (filho). |
| Relacionamento M:N | Tabela própria com as PKs das duas entidades (PK composta). |
| Auto-relacionamento | FK na própria tabela (referencia a PK), permitindo NULL para o nó raiz. |
| Generalização/Especialização | Tabela para superclasse + tabelas para subclasses com FK; ou tabela única com discriminador. |

---

*Material complementar à aula "Mapeamento ER-Relacional" (professor Washington Almeida, Gran Concursos).*