# Anotações – Banco de Dados – MER (Modelo Entidade-Relacionamento)

## 1. Introdução ao MER

### 1.1 O que é o MER?

- **Modelo Entidade-Relacionamento (MER):** modelo conceitual de alto nível, projetado para ser compreensível aos usuários comuns.
- **Criador:** Peter Chen, em 1976, com o artigo *"The Entity-Relationship Model"*.
- **Objetivo:** servir como guia antes da implementação do banco de dados, oferecendo visão clara e estruturada das entidades e seus relacionamentos.

> ### 1.1.1 MER vs. DER
> - **MER (Modelo Entidade-Relacionamento):** é o modelo conceitual em si (a estrutura lógica).
> - **DER (Diagrama Entidade-Relacionamento):** é a representação gráfica (visual) desse modelo.
> - O DER é o "desenho" que materializa o MER.

### 1.2 Etapas do projeto de banco de dados

| ETAPA | DESCRIÇÃO | PRODUTO |
| --- | --- | --- |
| **Projeto conceitual** | Modelagem de alto nível, independente de SGBD. | MER / DER |
| **Projeto lógico** | Mapeamento para o modelo de dados do SGBD (ex.: relacional). | Esquema lógico (relações, atributos, chaves) |
| **Projeto físico** | Implementação física no SGBD. | Tabelas, índices, armazenamento |

> ### 1.2.1 Equivalência de terminologia
> | NÍVEL | TERMO |
> | --- | --- |
> | Conceitual | Entidade |
> | Lógico | Relação |
> | Físico | Tabela |

## 2. Notações do MER (Principais)

| NOTAÇÃO | ENTIDADE | RELACIONAMENTO | CARDINALIDADE | CARACTERÍSTICA |
| --- | --- | --- | --- | --- |
| **Peter Chen** | Retângulo | Losango | Números (1, N) ou símbolos | Atributo chave = campo preenchido/sublinhado |
| **James Martin** | Retângulo | Linha | "Pé de galinha" | Notação mais simples, muito usada em ferramentas de modelagem |

> ### 2.1 Observação
> - As bancas podem usar **variações** ou **combinações** dessas notações.
> - É essencial conhecer ambas para interpretar corretamente os diagramas em provas.

## 3. Conceitos Fundamentais do MER

### 3.1 Entidade

- **Definição:** "coisa" do mundo real com existência independente.
- Pode ser:
  - **Física:** carro, casa, pessoa.
  - **Conceitual:** empresa, serviço, consulta.
- **Representação:** retângulo com o nome da entidade.
- Descrita por **atributos**.

> ### 3.1.1 Instância vs. Tipo de Entidade
> - **Tipo de entidade:** a definição abstrata (ex.: ALUNO).
> - **Instância de entidade:** uma ocorrência específica (ex.: o aluno João Silva).

### 3.2 Atributo

- **Definição:** propriedade que descreve uma característica particular de uma entidade **ou de um relacionamento**.
- **Atenção:** relacionamentos também podem ter atributos!

### 3.3 Classificação dos Atributos

#### 3.3.1 Quanto à composição

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Simples (Atômico)** | Indivisível, não pode ser decomposto. | Sexo, peso, cor, CPF |
| **Composto** | Pode ser dividido em partes menores. | Endereço (logradouro, bairro, CEP); Nome (nome + sobrenome) |

#### 3.3.2 Quanto ao número de valores

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Monovalorado** | Um único valor por instância. | Idade, sexo, CPF |
| **Multivalorado** | Múltiplos valores por instância. | Telefone de contato, localização do departamento |

> ### 3.3.3 Quanto à origem do valor
> | TIPO | DESCRIÇÃO | EXEMPLO |
> | --- | --- | --- |
> | **Armazenado** | É persistido diretamente no banco de dados. | Data de nascimento, nome, CPF |
> | **Derivado** | Obtido a partir de outros atributos ou entidades relacionadas. | Idade (calculada a partir da data de nascimento); total de alunos (calculado por contagem) |

#### 3.3.4 Atributo Complexo

- **Definição:** atributo que é **composto e multivalorado ao mesmo tempo**.
- **Exemplo:** endereço (composto: logradouro, bairro, CEP) e uma pessoa pode ter **mais de um** endereço.

#### 3.3.5 Valores Nulos

- Utilizado quando uma entidade **não possui valor** para determinado atributo.
- Pode ocorrer quando:
  - O atributo **não é aplicável** àquela entidade (ex.: número de reservista para mulheres).
  - O valor é **desconhecido** no momento do cadastro.
- **Atenção:** no projeto conceitual, deve-se especificar se um atributo aceita valores nulos.

### 3.4 Domínio de Valores

- **Definição:** conjunto de valores válidos que podem ser atribuídos a um atributo.
- **Exemplos:**
  - Atributo "endereço" → domínio = cadeia de caracteres (string).
  - Atributo "ano do veículo" (em concessionária de seminovos) → domínio = inteiros entre 2000 e 2020.
  - Atributo "idade" → domínio = inteiros entre 0 e 120.

> ### 3.4.1 Importância
> - Restrições de domínio evitam **inconsistências** e garantem que apenas dados válidos sejam armazenados.

## 4. Chaves (Identificadores)

### 4.1 Hierarquia das chaves

```
Superchave
    ↓
Chave Candidata (superchave mínima)
    ↓
Chave Primária (escolhida entre as candidatas)
```

### 4.2 Definições

| CONCEITO | DEFINIÇÃO | EXEMPLO (entidade ALUNO) |
| --- | --- | --- |
| **Superchave** | Qualquer conjunto de atributos que identifique unicamente cada instância. | `{Nome, Curso, Matrícula}`, `{Idade, Nome, CPF}` |
| **Chave Candidata** | Superchave com **conjunto mínimo** de atributos (não se pode excluir nenhum). Pode haver mais de uma. | `{Matrícula}`, `{CPF}` |
| **Chave Primária** | Chave candidata **escolhida** no projeto para identificar unicamente as instâncias. | `{Matrícula}` |
| **Chave Alternativa (Secundária)** | Chave candidata **não escolhida** como chave primária. | `{CPF}` |
| **Chave Composta** | Chave formada por **mais de um atributo**. | `{Paciente, Médico, Data}` (entidade Consulta) |

> ### 4.2.1 Chave primária vs. chave estrangeira (visão geral)
> - **Chave primária:** identifica unicamente um registro na própria tabela.
> - **Chave estrangeira:** referência à chave primária de outra tabela (estabelece relacionamento).

## 5. Instância e Esquema

| CONCEITO | DESCRIÇÃO | SINÔNIMO | FREQUÊNCIA DE ALTERAÇÃO |
| --- | --- | --- | --- |
| **Instância** | Coleção de dados armazenados em um dado momento. | Extensão do BD | **Constante** (inserções, atualizações, exclusões) |
| **Esquema** | Descrição da estrutura do BD (entidades, relacionamentos, restrições). | Intenção do BD | **Raramente** alterado |

## 6. Questões de Concurso Comentadas

### 6.1 (UFCG/2019 – Analista de TI)

**Item:** "Um modelo básico de entidade-relacionamento é composto por tipos de entidades e específica relacionamentos existentes entre entidades."

**Alternativa correta:** **c) De acordo com Peter Chen, autor desse modelo, entidades são instâncias de tipos de entidades.**

**Análise:**
- a) Falso – modelo foi desenvolvido em 1976 (anos 1970).
- b) Falso – relacionamentos também podem ter atributos.
- c) Correto – uma entidade é uma instância de um tipo de entidade.
- d) Falso – entidades também representam conceitos abstratos (consulta, serviço).
- e) Falso – na notação de Chen, relacionamentos são **losangos**, não retângulos.

### 6.2 (IDECAN/2019/UNIVASF – Analista)

**Item:** "Sobre o Modelo Entidade-Relacionamento, é correto afirmar que:"

**Alternativa correta:** **e) o modelo ER descreve os dados como entidades, relacionamentos e atributos.**

## 7. Representação dos Atributos (Notação Chen)

| TIPO DE ATRIBUTO | REPRESENTAÇÃO |
| --- | --- |
| Atributo Simples | Oval com nome |
| Atributo Chave | Oval com nome **sublinhado** (ou campo preenchido) |
| Atributo Derivado | Oval com nome entre **parênteses** ou tracejado |
| Atributo Multivalorado | Oval com **dupla borda** |
| Atributo Composto | Oval com ramificações para subatributos |
| Atributo Chave Parcial (entidade fraca) | Oval com nome **tracejado/sublinhado** |

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (UFCG/2019) | c |
| 21 (IDECAN/2019) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Entidade** | Coisa do mundo real com existência independente. | Aluno, Carro, Consulta |
| **Atributo** | Propriedade que descreve uma entidade ou relacionamento. | Nome, CPF, Data da consulta |
| **Atributo Simples** | Indivisível. | Sexo, peso |
| **Atributo Composto** | Divisível em partes. | Endereço, Nome completo |
| **Atributo Multivalorado** | Múltiplos valores. | Telefones, localizações |
| **Atributo Derivado** | Calculado a partir de outros dados. | Idade, total de alunos |
| **Domínio** | Conjunto de valores válidos. | Ano: 2000–2020 |
| **Superchave** | Conjunto de atributos que identifica unicamente uma instância. | {Nome, Curso, Matrícula} |
| **Chave Candidata** | Superchave mínima. | {Matrícula}, {CPF} |
| **Chave Primária** | Chave candidata escolhida. | Matrícula |
| **Instância** | Dados em um dado momento (extensão). | Os alunos cadastrados hoje |
| **Esquema** | Estrutura do BD (intenção). | Tabelas, colunas, relacionamentos |

---

*Material baseado na aula do professor Washington Henrique Almeida (Gran Concursos).*