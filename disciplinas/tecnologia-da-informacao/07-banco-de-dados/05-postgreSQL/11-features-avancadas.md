# Anotações – PostgreSQL – Features Avançadas

## 1. Índices (Indexes)

### 1.1 Conceito

- Índices aceleram a localização de linhas em consultas, similar ao índice de um livro.
- **Comando:** `CREATE INDEX nome_do_indice ON tabela (coluna);`
- **Remoção:** `DROP INDEX nome_do_indice;`

### 1.2 Tipos de índices no PostgreSQL

| TIPO | DESCRIÇÃO |
| --- | --- |
| **B-tree** | Padrão. Ideal para consultas com igualdade e intervalo (ex.: `=`, `<`, `>`, `BETWEEN`). |
| **Hash** | Apenas para comparações de igualdade (`=`). |
| **GiST** | Para dados geométricos, texto (busca de similaridade) e outros tipos complexos. |
| **SP-GiST** | Para dados com estrutura não balanceada (ex.: árvores de busca). |
| **GIN** | Para busca em arrays, JSON, texto (índices invertidos). |
| **BRIN** | Para tabelas muito grandes com ordenação natural (ex.: dados temporais). |

> ### 1.2.1 Índices multicoluna
> - Apenas os tipos **B-tree, GiST, GIN e BRIN** suportam índices em várias colunas.

### 1.3 Características importantes

- Índices podem ser criados ou removidos a qualquer momento.
- O PostgreSQL decide automaticamente se usa o índice ou faz uma varredura sequencial.
- Apenas **índices B-tree** podem ser declarados como `UNIQUE`.

## 2. Arquivos de Configuração

| ARQUIVO | FUNÇÃO |
| --- | --- |
| **`postgresql.conf`** | Configurações gerais do servidor (auditoria, autenticação, criptografia, memória, etc.). |
| **`pg_hba.conf`** | Gerencia **quem** (quais máquinas/usuários) pode acessar o banco e qual método de autenticação usar (`trust`, `md5`, `crypt`, etc.). |

> ### 2.1 `pg_hba.conf`
> - **HBA** = *Host-Based Authentication*.
> - Padrão: instalado quando o diretório de dados é inicializado pelo `initdb`.

## 3. Backup e Restauração

| FERRAMENTA | FUNÇÃO |
| --- | --- |
| **`pg_dump`** | Exporta (backup) um banco de dados para um arquivo. |
| **`pg_restore`** | Restaura um banco de dados a partir de um backup gerado pelo `pg_dump`. |
| **`psql`** | Ferramenta de administração em modo texto (também usada para restaurar scripts SQL). |

### 3.1 Exemplo de `pg_dump`

```bash
pg_dump -U db_user -W -F t db_name > /path/to/backup.tar
```

### 3.2 Exemplo de `pg_restore`

```bash
pg_restore -d db_name /path/to/backup.tar -c -U db_user
```

## 4. Escalabilidade

| TIPO | DESCRIÇÃO |
| --- | --- |
| **Vertical** | Adição de recursos a uma única máquina (mais CPU, RAM, disco). O PostgreSQL é **muito bom** nesse modelo. |
| **Horizontal** | Adição de novos nós (máquinas). O PostgreSQL tem suporte limitado, via replicação (Master-Slave), mas é mais adequado para bancos NoSQL. |

## 5. Usuários, Grupos e Roles (Permissões)

### 5.1 `CREATE USER` / `DROP USER` / `ALTER USER`

- `CREATE USER` é um **alias** para `CREATE ROLE` (atualmente).
- `DROP USER` remove o usuário, mas **não remove** objetos que pertencem a ele (tabelas, views, etc.).

### 5.2 `CREATE GROUP` / `DROP GROUP` / `ALTER GROUP`

- Grupos facilitam o gerenciamento de privilégios (conceder/revogar permissões para um conjunto de usuários).

### 5.3 `CREATE ROLE` (principal)

- **Role** (papel) é a entidade central de permissões no PostgreSQL.
- Pode representar um **usuário** ou um **grupo** (ou ambos).
- `CREATE ROLE` substitui `CREATE USER` e `CREATE GROUP`.

| COMANDO | FUNÇÃO |
| --- | --- |
| `CREATE ROLE nome` | Cria um papel. |
| `ALTER ROLE nome` | Altera atributos de um papel. |
| `DROP ROLE nome` | Remove um papel (se não houver dependências). |

> ### 5.3.1 Atenção
> - Não é possível remover um papel que ainda possui objetos ou privilégios.
> - Antes de remover, é necessário transferir a propriedade dos objetos ou revogar privilégios.

## 6. Privilégios (`GRANT` e `REVOKE`)

### 6.1 Dono do objeto

- O **dono** (owner) de um objeto é o usuário que o criou.
- Apenas o dono ou um superusuário pode alterar o objeto.

### 6.2 `GRANT` – Conceder privilégios

```sql
GRANT {SELECT, INSERT, UPDATE, DELETE, ...} ON tabela TO usuario;
GRANT ALL PRIVILEGES ON tabela TO usuario;
```

| PRIVILÉGIO | DESCRIÇÃO |
| --- | --- |
| `SELECT` | Ler dados. |
| `INSERT` | Inserir dados. |
| `UPDATE` | Atualizar dados. |
| `DELETE` | Excluir dados. |
| `TRIGGER` | Criar triggers. |
| `CREATE` | Criar objetos. |
| `EXECUTE` | Executar funções. |
| `USAGE` | Usar objetos (ex.: sequences). |
| `ALL PRIVILEGES` | Todos os privilégios. |

### 6.3 `REVOKE` – Revogar privilégios

```sql
REVOKE {SELECT, INSERT} ON tabela FROM usuario;
```

### 6.4 `SECURITY DEFINER` (funções)

- Permite que uma função seja executada com as **permissões do criador**, e não do usuário que a chama.
- Útil para dar acesso controlado a dados restritos.

## 7. Comandos SQL – Classificação

| CATEGORIA | COMANDOS |
| --- | --- |
| **DDL** | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME` |
| **DML** | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** | `GRANT`, `REVOKE` |
| **TCL** | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

> ### 7.1 `TRUNCATE`
> - Remove **todos os dados** da tabela, mas mantém a estrutura.
> - É considerado **DDL** porque também apaga estruturas acessórias (índices, etc.).

## 8. Questões de Concurso Comentadas

### 8.1 (CESPE/2019/TJ-AM)

**Item:** "A manipulação de ROLES é feita exclusivamente por comandos CREATE e DROP fornecidos com o banco de dados."

**Gabarito: Errado (E)**.

**Comentário:** Também existe o comando **`ALTER ROLE`** para manipular roles.

### 8.2 (FCC/2018/DPE-AM)

**Código com `octet_length` e concatenação:**

```sql
CREATE TABLE processo (proc_num character(24));
INSERT INTO processo SELECT '0000125-40.' || '1981.403.6100';
SELECT proc_num, octet_length(proc_num) FROM processo;
```

**Gabarito: a) `0000125-40.1981.403.6100` e `24`.**

**Comentário:**
- `||` é o operador de concatenação.
- `character(24)` tem tamanho fixo de 24 caracteres; `octet_length` retorna o tamanho em bytes (24, pois é fixo).

### 8.3 (FCC/2018/DPE-AM)

**Item:** Backup e restauração no PostgreSQL → **d) `pg_dump` e `psql`** (ou `pg_restore`). A alternativa correta foi `d) pg_dump e psql`.

### 8.4 (CESPE/2017/TRF-1)

**Item com `SAVEPOINT`:**

```sql
BEGIN;
SAVEPOINT primeiro;
CREATE TABLE tbl_conceito (id int, nome varchar);
ROLLBACK TO SAVEPOINT primeiro;
COMMIT;
```

**Gabarito: Certo (C)** (a tabela não é criada, pois o `ROLLBACK` desfaz a criação).

### 8.5 (CESPE/2017/TRT-7)

**Item:** Restrição de acesso por IP → **b) `pg_hba.conf`**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2019) | E |
| 02 (FCC/2018) | a |
| 03 (FCC/2018) | d |
| 04 (CESPE/2017) | C |
| 05 (CESPE/2017) | b |

---

*Material complementar à aula "PostgreSQL – Features Avançadas" (professor Washington Henrique Almeida, Gran Concursos).*