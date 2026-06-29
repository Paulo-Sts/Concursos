# Anotações – PostgreSQL

## 1. Introdução ao PostgreSQL

### 1.1 Definição

- **PostgreSQL** é um **SGBD objeto-relacional** (SGBDRO) – sistema de gerenciamento de banco de dados relacional de objetos.
- Incorpora **características da orientação a objetos**, mas **não é** um banco de dados orientado a objetos.
- É um banco de dados **relacional** com funcionalidades estendidas (ex.: herança, tipos definidos pelo usuário).

### 1.2 Origem

- Baseado no **POSTGRES**, desenvolvido na **Universidade da Califórnia, Berkeley**.
- Liderado pelo professor **Michael Stonebraker**.
- Patrocinado por: DARPA, ARO, NSF e ESL, Inc.

### 1.3 Evolução

| ANO | EVENTO |
| --- | --- |
| 1994 | Andrew Yu e Jolly Chen adicionaram um interpretador SQL ao POSTGRES → **Postgres95**. |
| 1996 | Sistema renomeado para **PostgreSQL** (refletindo a relação entre POSTGRES e SQL). |

> ### 1.3.1 Nome informal
> - Muitas pessoas ainda se referem ao PostgreSQL como **"Postgres"** (nome mais curto e fácil de pronunciar).

## 2. Posição no Mercado

### 2.1 Ranking DB-Engines (2019 – mantido estável até 2023)

| POSIÇÃO | SGBD |
| --- | --- |
| 1º | Oracle |
| 2º | MySQL |
| 3º | Microsoft SQL Server |
| 4º | **PostgreSQL** |
| 5º | MongoDB |

> ### 2.1.1 Observação
> - Os quatro primeiros são os **SGBDs mais cobrados em concursos**.
> - O **MongoDB** (5º lugar) é um SGBD **orientado a documentos (NoSQL)**.

### 2.2 Licenciamento

| SGBD | LICENÇA | PAGA? |
| --- | --- | --- |
| Oracle | Comercial | Sim |
| SQL Server | Comercial | Sim |
| MySQL | Comercial (após aquisição pela Oracle) | Sim (para uso comercial) |
| **PostgreSQL** | **Licença PostgreSQL** (open-source, similar a BSD/MIT) | **Não** |

> ### 2.2.1 Características da Licença PostgreSQL
> - Licença liberal de código-fonte aberto.
> - Permite uso, modificação e distribuição **gratuitamente** para qualquer fim (privado, comercial ou acadêmico).
> - Semelhante às licenças **BSD** ou **MIT**.
> - **Não é GPL** (GNU General Public License). Os criadores afirmam: *"nós gostamos da nossa licença e não queremos alterá-la"*.

## 3. Características Principais do PostgreSQL

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Compatibilidade com padrões** | Suporta grande parte do padrão ANSI SQL. |
| **Arquitetura** | Cliente-servidor. |
| **Porta padrão** | **5432** (TCP). |
| **Sistemas operacionais** | Linux, Windows (2000 SP4+), FreeBSD, OpenBSD, NetBSD, macOS, AIX, HP/UX, Solaris. |
| **Arquiteturas de CPU** | x86, x86_64, IA64, PowerPC, ARM, MIPS, Sparc, entre outras. |
| **Linguagem procedural nativa** | **PL/pgSQL** (própria do PostgreSQL). Também suporta PL/Python, PL/Java, PL/Perl. |
| **Suporte a índices** | B-Tree, rTree, Hash. |
| **Mecanismo de concorrência** | **MVCC** (Multiversion Concurrency Control). |
| **Logging** | **WAL** (Write-Ahead Logging) – garante integridade e logging de transações. |
| **Replicação** | **Master-Slave** com instâncias **read-only** (alta disponibilidade). |
| **Escalabilidade** | Excelente **escalabilidade vertical**; alguma escalabilidade horizontal via replicação. |

> ### 3.1 O que é MVCC?
> - **Multiversion Concurrency Control** (Controle de Concorrência de Multiversão).
> - Permite que **leituras não bloqueiem escritas** e vice-versa.
> - Cada usuário trabalha com sua própria "versão" da instância do banco de dados.
> - Reduz drasticamente a contenção entre transações concorrentes e previne **deadlocks**.
> - **Atenção:** não corrige aplicações mal construídas.

### 3.2 O que é WAL?

- **Write-Ahead Logging** (Log de Escrita Antecipada).
- Garante a **integridade dos dados** e o **logging de transações**.
- As alterações são registradas no log **antes** de serem aplicadas ao banco de dados.

## 4. Comparação com Outros SGBDs

| CARACTERÍSTICA | PostgreSQL | MySQL | Oracle | SQL Server |
| --- | --- | --- | --- | --- |
| Tipo | Objeto-relacional | Relacional | Relacional | Relacional |
| Licença | Open-source (BSD-like) | Comercial (Oracle) | Comercial | Comercial |
| Integridade referencial | **Nativa** desde o início | Disponível apenas com InnoDB | Sim | Sim |
| Linguagem procedural | PL/pgSQL | MySQL (stored procedures) | PL/SQL | T-SQL |
| Forte compatibilidade | **Com Oracle** (para facilitar migração) | – | – | – |

> ### 4.1 PostgreSQL vs. Oracle
> - O PostgreSQL tem **forte compatibilidade com o Oracle** para facilitar a migração de usuários.
> - **Procedures** foram implementadas no PostgreSQL em versões avançadas porque o Oracle já as possuía.

## 5. Instalação do PostgreSQL

### 5.1 Formas de instalação

| MÉTODO | DESCRIÇÃO | VANTAGEM | DESVANTAGEM |
| --- | --- | --- | --- |
| Gerenciador de pacotes da distribuição | `apt-get install postgresql-12` (Linux) | Fácil e rápida. | Versão pode não ser a mais recente. |
| Repositórios oficiais | Baixar do site oficial do PostgreSQL. | Versão mais recente. | Requer configuração adicional. |
| Código-fonte | Compilar a partir do código-fonte. | Máxima flexibilidade (personalização). | Mais complexa e demorada. |

### 5.2 Interface gráfica

- **PGAdmin** – interface gráfica do PostgreSQL.
- Ao baixar o PostgreSQL para Windows, o PGAdmin já está **incluso**.

## 6. Dicas para Provas

| DICA | EXPLICAÇÃO |
| --- | --- |
| **Porta padrão** | **5432** (TCP). |
| **Licença** | PostgreSQL é **open-source** com licença própria (BSD-like). |
| **Tipo** | SGBD **objeto-relacional**, não puramente relacional. |
| **MVCC** | Controle de concorrência de multiversão – leituras não bloqueiam escritas. |
| **PL/pgSQL** | Linguagem procedural nativa do PostgreSQL. |
| **Comparações** | Questões costumam comparar PostgreSQL com Oracle, MySQL, SQL Server. |
| **Integridade referencial** | Nativa no PostgreSQL (diferente do MySQL, que dependia da InnoDB). |

## 7. Síntese para Revisão Rápida

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Tipo** | Objeto-relacional (relacional com características OO). |
| **Origem** | POSTGRES (Berkeley) → Postgres95 → PostgreSQL. |
| **Licença** | Open-source, BSD-like, gratuita. |
| **Porta padrão** | 5432. |
| **Linguagem procedural** | PL/pgSQL (nativa); também PL/Python, PL/Java, PL/Perl. |
| **Mecanismo de concorrência** | MVCC. |
| **Logging** | WAL (Write-Ahead Logging). |
| **Replicação** | Master-Slave com instâncias read-only. |
| **Índices** | B-Tree, rTree, Hash. |
| **Compatibilidade** | Forte compatibilidade com Oracle. |

---

*Material complementar à aula "PostgreSQL" (professor Washington Henrique Almeida, Gran Concursos).*