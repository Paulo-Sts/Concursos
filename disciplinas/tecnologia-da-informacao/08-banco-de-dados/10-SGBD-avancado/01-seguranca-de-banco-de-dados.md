# Anotações – Segurança de Banco de Dados (GRANT e REVOKE)

## 1. Contexto Geral

- A segurança em banco de dados é tratada por comandos da **Data Control Language (DCL)**, um subconjunto da linguagem SQL.
- O SGBD possui um **subsistema de autorização e segurança** para garantir que apenas usuários autorizados realizem operações sobre os dados.
- A segurança visa garantir os pilares da segurança da informação:
  - **Confidencialidade (sigilo):** usuários não acessam dados não autorizados.
  - **Integridade:** apenas usuários autorizados podem modificar dados.
  - **Disponibilidade:** dados acessíveis quando requisitados por usuários autorizados.

> ### 1.1 Responsabilidade
> - A implementação dos mecanismos de segurança é de responsabilidade do **Administrador de Banco de Dados (DBA)**.

## 2. Mecanismos de Controle de Acesso

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Discricionário** | Concede privilégios a usuários específicos, caso a caso, por meio de GRANT e REVOKE. | Um usuário pode ter permissão de SELECT em uma tabela sem repassá-la a outros. |
| **Obrigatório (Mandatório)** | Regras de segurança baseadas em classificações atribuídas aos usuários (perfis/grupos). Mais rígido e estruturado. | Usuários associados a perfis predefinidos (ex.: "gerente", "analista"). |

> ### 2.1 Controle de acesso discricionário
> - Baseado na atribuição de privilégios específicos a usuários, sem necessidade de agrupá-los em perfis.
> - O criador de um objeto (owner) possui todos os privilégios sobre ele.
> - O SGBD mantém uma **tabela interna de privilégios** que registra quem tem quais permissões.

## 3. Comandos DCL – GRANT e REVOKE

### 3.1 GRANT – Conceder privilégios

```sql
GRANT <privilégios> ON <objeto> TO <usuário> [WITH GRANT OPTION];
```

| ELEMENTO | DESCRIÇÃO |
| --- | --- |
| **Privilégios** | SELECT, INSERT, UPDATE, DELETE, REFERENCES, etc. |
| **Objeto** | Tabela, visão (view), esquema, etc. |
| **WITH GRANT OPTION** | Permite que o usuário repasse os privilégios concedidos a outros usuários. |

**Exemplos:**
```sql
-- Concede SELECT e INSERT na tabela Funcionarios para João (sem repasse)
GRANT SELECT, INSERT ON Funcionarios TO Joao;

-- Concede SELECT na tabela Funcionarios para Joana com permissão de repasse
GRANT SELECT ON Funcionarios TO Joana WITH GRANT OPTION;
```

> ### 3.1.1 WITH GRANT OPTION
> - Sem essa opção, o usuário pode **usar** o privilégio, mas **não pode repassá-lo**.
> - Com essa opção, o usuário pode conceder o mesmo privilégio a terceiros.

### 3.2 REVOKE – Revogar privilégios

```sql
REVOKE <privilégios> ON <objeto> FROM <usuário> [RESTRICT | CASCADE];
```

| ELEMENTO | DESCRIÇÃO |
| --- | --- |
| **RESTRICT** | Impede a revogação se houver dependências (ex.: outros usuários receberam o privilégio via GRANT OPTION). |
| **CASCADE** | Remove o privilégio do usuário e de todos os que receberam o privilégio por meio dele (em cadeia). |

**Exemplo (cadeia de concessão):**
- João concede SELECT (com GRANT OPTION) a Maria.
- Maria concede SELECT a Renata.
- João revoga SELECT de Maria com **CASCADE** → Maria e Renata perdem o privilégio.

> ### 3.2.1 Comportamento do CASCADE
> - Se a revogação for feita com **CASCADE**, todos os privilégios concedidos pela cadeia são removidos.
> - Se for com **RESTRICT**, a operação falha se houver dependências.

## 4. Principais Privilégios no SQL

| PRIVILÉGIO | DESCRIÇÃO |
| --- | --- |
| `SELECT` | Permite consultar (ler) dados da tabela/visão. |
| `INSERT` | Permite inserir novas linhas na tabela. |
| `DELETE` | Permite excluir linhas da tabela. |
| `UPDATE(coluna)` | Permite atualizar colunas específicas. |
| `REFERENCES(coluna)` | Permite definir chaves estrangeiras que referenciam a coluna. |
| `ALL PRIVILEGES` | Todos os privilégios disponíveis. |

## 5. Questões de Concurso Comentadas

### 5.1 (CESGRANRIO/2013/IBGE – Analista)

**Item:** "Controle de acesso discricionário é suportada no SQL pelos comandos:"

**Gabarito: d) GRANT e REVOKE.**

### 5.2 (FCC/2015/MPE-PB – Administrador de BD)

**Item:** "Conceder SELECT e INSERT na tabela Processo ao usuário Pedro, com permissão para repassar."

**Gabarito: d) GRANT select, insert ON Processo TO Pedro WITH GRANT OPTION.**

### 5.3 (FCC/2017/TRT-MS – Analista Judiciário)

**Item:** "Para permitir que o usuário Paulo repasse o privilégio SELECT para outros usuários."

**Gabarito: b) GRANT OPTION.**

### 5.4 (CESPE/2012/BANCO DA AMAZÔNIA – Técnico)

**Item:** "Os comandos GRANT e REVOKE permitem especificar, respectivamente, concessão e revogação de privilégios."

**Gabarito: Certo (C).**

### 5.5 (CESPE/2018/EBSERH – Técnico)

**Item:** "O comando GRANT DELETE ON Hospital TO esberh tem a finalidade de conceder o privilégio de remoção de registro da tabela Hospital ao usuário esberh."

**Gabarito: Errado (E).**

**Comentário:** O comando `GRANT DELETE` concede o privilégio de **exclusão de registros** (DELETE), não de "remoção de privilégios". O termo "remoção da delação" da questão indica confusão com a semântica correta do comando.

### 5.6 (CESPE/2018/STJ – Técnico Judiciário)

**Item:** "O comando GRANT é utilizado para conceder privilégios em um objeto do SGBD, ao passo que o comando REVOKE serve para cancelar um privilégio já concedido."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/2013) | d |
| 02 (FCC/2015) | d |
| 03 (FCC/2017) | b |
| 04 (CESPE/2012) | C |
| 05 (CESPE/2018 – EBSERH) | E |
| 06 (CESPE/2018 – STJ) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **DCL** | Data Control Language – comandos GRANT e REVOKE. |
| **Controle Discricionário** | Concessão individual de privilégios (GRANT/REVOKE). |
| **Controle Mandatório** | Controle baseado em perfis/grupos predefinidos. |
| **GRANT** | Concede privilégios a usuários. |
| **REVOKE** | Revoga privilégios concedidos. |
| **WITH GRANT OPTION** | Permite que o usuário repasse privilégios. |
| **CASCADE** | Revoga privilégios em cascata (inclui dependentes). |
| **RESTRICT** | Impede a revogação se houver dependências. |
| **Owner (dono)** | Criador do objeto – possui todos os privilégios sobre ele. |

---

*Material complementar à aula "Segurança de Banco de Dados" (professor Washington Henrique Almeida/Gran Concursos).*