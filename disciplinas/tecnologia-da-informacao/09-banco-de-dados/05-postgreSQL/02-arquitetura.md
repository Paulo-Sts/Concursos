# Anotações – PostgreSQL – Arquitetura e Utilitários

## 1. Arquitetura do PostgreSQL

### 1.1 Visão geral

- Arquitetura **cliente-servidor**.
- Mais simples que a do Oracle, um pouco mais complexa que a do SQL Server.
- Um processo servidor chamado **`postgres`** gerencia:
  - Os arquivos do banco de dados.
  - As conexões das aplicações clientes.
  - A execução de ações no banco de dados em nome dos clientes.

### 1.2 Componentes principais

| COMPONENTE | DESCRIÇÃO |
| --- | --- |
| **Processo servidor** | Chamado de `postgres`. Fica em execução contínua, aguardando conexões de clientes. |
| **Aplicação cliente** | Pode ser gráfica (PGAdmin), linha de comando (`psql`), servidor web, etc. |
| **Postmaster** | *Daemon* fundamental para rodar o PostgreSQL. Gerencia o processo servidor. |
| **Comunicação** | Via rede **TCP/IP**. Pode ser localhost (mesma máquina) ou em hosts diferentes. |

### 1.3 Sessão do PostgreSQL

- Uma sessão consiste em:
  1. Um **processo de servidor** (`postgres`).
  2. Uma **aplicação cliente** que deseja executar operações no banco.

> ### 1.3.1 Conexões simultâneas
> - O PostgreSQL pode trabalhar com **várias conexões de clientes simultâneas**.
> - Um novo processo é iniciado para cada conexão.

### 1.4 Diagrama simplificado

```
┌─────────────────────────┐         ┌─────────────────────────────────────────┐
│         CLIENTE         │         │            SERVIDOR (postgres)          │
│  ┌───────────────────┐  │         │  ┌───────────────────────────────────┐  │
│  │ Aplicação Cliente  │  │         │  │         postmaster (daemon)      │  │
│  └───────────────────┘  │         │  └───────────────────────────────────┘  │
│  ┌───────────────────┐  │         │  ┌───────────────────────────────────┐  │
│  │    Bibliotecas    │  │         │  │      Gerenciador de conexões      │  │
│  └───────────────────┘  │         │  └───────────────────────────────────┘  │
│         Conexão         │◄───────►│  ┌───────────────────────────────────┐  │
│    (autenticação)       │         │  │      Buffer compartilhado         │  │
└─────────────────────────┘         │  └───────────────────────────────────┘  │
                                    │  ┌───────────────────────────────────┐  │
                                    │  │         Disco (data files)        │  │
                                    │  └───────────────────────────────────┘  │
                                    └─────────────────────────────────────────┘
```

## 2. Regras de Nomeação no PostgreSQL

### 2.1 Tipo `name`

- Objetos (tabelas, colunas, databases, etc.) devem ser nomeados usando o tipo **`name`**.
- **Limite:** 63 caracteres.
  - Se um nome tiver mais de 63 caracteres, o PostgreSQL **descarta** o restante sem aviso.
  - Outros SGBDs geralmente avisam sobre o limite.

### 2.2 Regras básicas

| REGRA | DESCRIÇÃO | EXEMPLO VÁLIDO |
| --- | --- | --- |
| Início | Deve começar com uma letra ou sublinhado (`_`). | `my_table`, `_temp` |
| Caracteres permitidos | Letras, dígitos e sublinhados. | `my_2nd_table` |
| Acentuação | Permitida (letras não latinas também). | `échéanciers` |
| Case-sensitive (com aspas) | Nomes entre aspas duplas diferenciam maiúsculas de minúsculas. | `"1040Forms"` ≠ `"1040forms"` |
| Case-insensitive (sem aspas) | Nomes sem aspas são convertidos para **minúsculas**. | `MyTable` → `mytable` |

### 2.3 Palavras reservadas

- Não é possível usar palavras reservadas do SQL (ex.: `SELECT`, `INTEGER`, `BETWEEN`) para nomear objetos.
- **Exceção:** pode-se usar uma palavra reservada se ela estiver entre **aspas duplas**.
  - Exemplo: `"3.14159"`, `"createtable"`.

> ### 2.3.1 Aspas duplas vs. aspas simples
> - **Aspas duplas (`"`):** usadas para criar identificadores (nomes de objetos) com caracteres especiais ou palavras reservadas.
> - **Aspas simples (`'`):** usadas para **valores literais** (strings) em consultas.

### 2.4 Exemplos de nomes válidos e inválidos

| NOME | VÁLIDO? | OBSERVAÇÃO |
| --- | --- | --- |
| `my_table` | ✅ | Inicia com letra. |
| `my_2nd_table` | ✅ | Contém dígitos e sublinhados. |
| `échéanciers` | ✅ | Acentuação permitida. |
| `"2nd_table"` | ✅ | Entre aspas duplas (começa com número). |
| `"createtable"` | ✅ | Palavra reservada entre aspas. |
| `"1040Forms"` | ✅ | Case-sensitive. |
| `2nd_table` | ❌ | Não inicia com letra ou sublinhado (sem aspas). |

## 3. Utilitários do PostgreSQL

O PostgreSQL possui utilitários (programas executados na linha de comando) para tarefas administrativas.

### 3.1 Principais utilitários

| UTILITÁRIO | FUNÇÃO |
| --- | --- |
| `createdb` | Cria um novo banco de dados. |
| `dropdb` | Remove um banco de dados. |
| `psql` | Terminal interativo para executar comandos SQL e comandos internos. |
| `pg_dump` | Faz backup (dump) do banco de dados. |
| `pg_restore` | Restaura um backup. |

> ### 3.1.1 Usuário padrão
> - **`postgres`** é o usuário padrão do PostgreSQL (semelhante ao `SA` do SQL Server e ao `root` do MySQL).

## 4. Criação de Banco de Dados (Database)

### 4.1 Usando o utilitário `createdb`

```bash
# Logar como usuário postgres
[root@postgresql ~]# su -l postgres

# Criar database
[postgres@postgresql ~]$ createdb mydatabase
```

- O sistema retorna apenas "banco de dados criado".

### 4.2 Usando `psql` (SQL)

```bash
# Acessar o psql
[postgres@postgresql ~]$ psql
psql (12.1)
postgres=#

# Criar database
postgres=# CREATE DATABASE mydatabase;
CREATE DATABASE
```

- Para listar databases existentes: `\l` (dentro do `psql`).
- Para sair do `psql`: `\q`.

### 4.3 Usando PGAdmin (interface gráfica)

- Acessar o servidor no PGAdmin.
- Abrir o editor de consultas e executar:
  ```sql
  CREATE DATABASE mydatabase;
  ```

### 4.4 Diferença entre `createdb` e `CREATE DATABASE`

| `createdb` (utilitário) | `CREATE DATABASE` (comando SQL) |
| --- | --- |
| Executado na linha de comando (shell). | Executado dentro do `psql` ou PGAdmin. |
| É um programa externo. | É uma instrução SQL padrão. |
| Não pode ser usado dentro de uma conexão ativa. | Pode ser usado dentro de uma conexão ativa (servidor). |

> ### 4.4.1 Observação
> - Não é possível criar um banco de dados **dentro de outro banco de dados**. O comando `CREATE DATABASE` só pode ser executado no nível do servidor (conexão sem database específica).

## 5. Remoção de Banco de Dados (DROP DATABASE)

### 5.1 Usando o utilitário `dropdb`

```bash
[postgres@postgresql ~]$ dropdb mydatabase
```

### 5.2 Usando `psql` (SQL)

```sql
postgres=# DROP DATABASE mydatabase;
DROP DATABASE
```

### 5.3 Verificação

- Use `\l` dentro do `psql` para listar as databases e confirmar a remoção.

> ### 5.3.1 Cuidado
> - `dropdb` é um **utilitário**; `DROP DATABASE` é o **comando SQL**.
> - Não confunda os dois.

## 6. Acessando um Banco de Dados com `psql`

### 6.1 Acessar diretamente uma database específica

```bash
[postgres@postgresql ~]$ psql mydatabase
psql (12.1)
mydatabase=#
```

- O prompt `mydatabase=#` indica que o `psql` está conectado **diretamente ao banco** `mydatabase`.

### 6.2 Conectar ao servidor (sem database específica)

```bash
[postgres@postgresql ~]$ psql
postgres=#
```

- O prompt `postgres=#` indica conexão ao servidor (pode criar databases, etc.).

## 7. Comandos SQL Básicos dentro do `psql`

### 7.1 Consultar a versão do PostgreSQL

```sql
mydatabase=# SELECT version();
```

**Saída (exemplo):**
```
version
--------------------------------------------------------------------------------
PostgreSQL 12.1 on x86_64-pc-linux-gnu, compiled by gcc (GCC) 4.8.5 ...
(1 row)
```

### 7.2 Consultar a data atual

```sql
mydatabase=# SELECT current_date;
```

**Saída (exemplo):**
```
current_date
--------------
2026-06-26
(1 row)
```

## 8. Comandos Internos do `psql` (começam com `\`)

| COMANDO | FUNÇÃO |
| --- | --- |
| `\l` | Lista todas as databases. |
| `\h` | Exibe ajuda sobre comandos SQL. |
| `\q` | Sai do `psql`. |
| `\dt` | Lista todas as tabelas. |
| `\du` | Lista usuários/roles. |

> ### 8.1 Recomendação do professor
> - As bancas **não costumam cobrar comandos específicos** do `psql` com frequência.
> - Foque nos comandos SQL padrão (`CREATE`, `DROP`, `SELECT`, etc.).

## 9. Questão de Concurso Comentada

### 9.1 (CCV-UFC/2018/UFC – Analista de TI)

**Item:** "Sob qual tipo de licença o banco de dados PostgreSQL é lançado atualmente?"

**Alternativa correta:** **e) PostgreSQL license**.

**Comentário:**
- O PostgreSQL é lançado sob a **PostgreSQL License**.
- É uma licença liberal de código aberto, semelhante às licenças **BSD** e **MIT**.
- Os criadores afirmam que não pretendem alterá-la para GPL.

## GABARITO DA QUESTÃO

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CCV-UFC/2018) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Arquitetura** | Cliente-servidor. Processo servidor = `postgres`. |
| **Porta padrão** | 5432 (TCP). |
| **Usuário padrão** | `postgres`. |
| **Limite de nome** | 63 caracteres (tipo `name`). |
| **Case-sensitive** | Apenas com aspas duplas (`"Nome"`). |
| **Palavras reservadas** | Podem ser usadas entre aspas duplas. |
| **Utilitários principais** | `createdb`, `dropdb`, `psql`, `pg_dump`, `pg_restore`. |
| **Comando SQL para criar DB** | `CREATE DATABASE nome;` |
| **Comando SQL para remover DB** | `DROP DATABASE nome;` |
| **Licença** | **PostgreSQL License** (open-source, BSD-like). |

---

*Material complementar à aula "PostgreSQL – Arquitetura e Utilitários" (professor Washington Henrique Almeida, Gran Concursos).*