# Tipos de Usuários, Linguagens e Arquitetura SGBD

## 1. Tipos de Usuários em Banco de Dados

#### 1.1 Projetista de Banco de Dados
- Responsabilidade: identificar os dados a serem armazenados e escolher a estrutura apropriada para representá-los.
- Atua principalmente na modelagem conceitual (nível mais alto de abstração).
- Define quais dados serão armazenados e como se relacionam.

#### 1.2 Administrador de Banco de Dados (DBA – Database Administrator)
- Responsável pela administração do banco de dados e do SGBD.
- O DBA cuida de questões como monitoramento, segurança, desempenho e disponibilidade do SGBD.

| ATRIBUIÇÃO DO DBA | DESCRIÇÃO |
|---|---|
| Monitoramento | Monitora o uso do BD em relação à segurança, tempo de resposta, desempenho, etc. |
| Segurança e autorização | Especifica regras de segurança e autoriza o acesso ao BD. |
| Estruturas de armazenamento | Define estruturas de armazenamento e métodos de acesso (ex.: índices). |
| Backup e recuperação | Define procedimentos de cópia (backup), recuperação (restore), etc. |

#### 1.3 Programador de Aplicações
- Escreve os programas de aplicação que acessam o banco de dados.
- Realiza requisições ao SGBD por meio de:
  - Comandos SQL (SELECT, INSERT, DELETE, UPDATE).
  - Ferramentas RAD (Rapid Application Development).

#### 1.4 Usuário Final
- Manipula o banco de dados por meio de linguagens de consulta e programas de aplicação.

| TIPO DE USUÁRIO FINAL | CARACTERÍSTICA |
|---|---|
| Leigos | Interagem com o BD apenas através dos programas de aplicação (não escrevem consultas SQL). |
| Casuais | Acessam o BD eventualmente; podem solicitar informações diferentes a cada vez. Nível hierárquico médio ou elevado. |
| Avançados | Interagem diretamente com o BD submetendo requisições em linguagem de consulta (ex.: SQL). |

#### 1.5 Administrador de Dados (AD – Data Administrator)
- Não deve ser confundido com o DBA (são funções distintas).
- É importante quando há necessidade de uma visão única dos dados (bases corporativas).
- Opera uma variedade de bancos de dados, atendendo a diversas áreas de negócio.
- Atua quando há falta de uniformidade nos dados, implicando redundância em diversos níveis (bancos de dados, colunas, tabelas, etc.).

| ATRIBUIÇÃO DO ADMINISTRADOR DE DADOS | DESCRIÇÃO |
|---|---|
| Padronização | Define padrões de nomenclatura. |
| Conhecimento das informações | Deve conhecer as informações representadas no BD e preocupar-se com a integração entre bancos de dados distintos. |
| Levantamento de requisitos | Faz o levantamento dos requisitos funcionais do banco de dados. |
| Modelagem conceitual | Cria o modelo conceitual do banco de dados. |

#### 1.6 DBA vs. Administrador de Dados

| FUNÇÃO | DBA | ADMINISTRADOR DE DADOS |
|---|---|---|
| Foco principal | Administração do SGBD (monitoramento, segurança, backup) | Administração dos dados em si (organização, padronização, integração) |
| Preocupação central | Desempenho, disponibilidade, segurança do sistema | Qualidade, consistência e significado dos dados |
| Abrangência | Geralmente um SGBD específico | Múltiplos bancos de dados e sistemas |

## 2. Linguagens do SGBD
- A linguagem SQL combina VDL, DDL e DML. É a linguagem padrão para bancos de dados relacionais.

| LINGUAGEM | SIGLA | FUNÇÃO | OBSERVAÇÃO |
|---|---|---|---|
| Linguagem de Definição de Visões | VDL (*View Definition Language*) | Especificar o esquema externo (visões) de acordo com os tipos de usuários e seus acessos. | Na prática, o SQL combina VDL, DDL e DML. |
| Linguagem de Definição de Dados | DDL (*Data Definition Language*) | Especificar o esquema conceitual (estrutura do banco de dados). | CREATE, ALTER, DROP. |
| Linguagem de Definição de Armazenamento | SDL (*Storage Definition Language*) | Especificar o esquema interno (como os dados são armazenados fisicamente). | Na maioria dos SGBDs, a DDL é usada para definir tanto o esquema externo, conceitual quanto o interno. |
| Linguagem de Manipulação de Dados | DML (*Data Manipulation Language*) | Recuperar, inserir, excluir e modificar dados (CRUD). | SELECT, INSERT, DELETE, UPDATE. |

#### 2.1 Exemplo de DDL – CREATE TABLE

```sql
CREATE TABLE AUTOMOVEL (
    PLACA CHAR(7) PRIMARY KEY NOT NULL,
    ANO INT NOT NULL,
    MARCA VARCHAR(30) NOT NULL,
    MODELO VARCHAR(30) NOT NULL,
    COR VARCHAR(20)
);
```

O que é definido:
- Tipos de dados (CHAR, INT, VARCHAR).
- Restrições (`PRIMARY KEY`, `NOT NULL`).
- A chave primária (`PLACA`) identifica cada registro de forma unívoca.
- As restrições (como `NOT NULL` e `PRIMARY KEY`) garantem que:
  - Todos os registros tenham a mesma estrutura.
  - Não haja inconsistências nos dados.

#### 2.2 Exemplo de DML – SELECT

```sql
SELECT * FROM AUTOMOVEL WHERE ANO = 2016;
```

- Recupera todos os veículos do ano de 2016.

#### 2.3 DML Procedural vs. Não Procedural
- DML Não Procedural: O usuário diz o que quer, o SGBD decide como buscar.
- DML Procedural: O usuário diz o que e como buscar (passo a passo).

| TIPO | CARACTERÍSTICA | EXEMPLOS |
|---|---|---|
| DML Procedural | Requer que o usuário especifique qual dado é necessário e como obtê-lo. | PL/SQL (Oracle), Transact-SQL (SQL Server). Pode ser embutida em linguagens como Pascal, C, C++. |
| DML Não Procedural (Declarativa) | Requer que o usuário especifique qual dado é necessário sem especificar como obtê-lo. | SQL padrão (SELECT). É mais fácil de aprender e usar. |

## 3. Módulos e Componentes do SGBD

#### 3.1 Propriedades ACID (base para todos os módulos)

| PROPRIEDADE | DESCRIÇÃO |
|---|---|
| Atomicidade | Uma transação deve ser executada por completo ou não ser executada (tudo ou nada). |
| Consistência | A transação leva o banco de dados de um estado consistente a outro estado consistente. |
| Isolamento (Independência) | Transações concorrentes não interferem umas nas outras (como se fossem executadas em sequência). |
| Durabilidade | Após a confirmação (commit), as alterações são permanentes, mesmo em caso de falha. |

#### 3.2 Principais Componentes do SGBD

| COMPONENTE | FUNÇÃO |
|---|---|
| Gerenciador de dados armazenados | Controla o acesso aos dados armazenados no disco (leitura/escrita). |
| Compilador (Processador) DDL | Compila as definições do esquema (CREATE, ALTER, DROP) e armazena-as no catálogo do SGBD. |
| Processador do BD em tempo de execução (run-time) | Recebe as operações de recuperação ou atualização e as executa sobre o banco de dados. |
| Compilador de consultas | Compila consultas de alto nível (SQL) e gera chamadas ao módulo run-time. |
| Pré-compilador | Extrai comandos DML de um programa de aplicação escrito em linguagem hospedeira (ex.: C, Java) e envia ao compilador DML. |
| Compilador da DML | Recebe e compila os comandos DML extraídos pelo pré-compilador, gerando código objeto para acesso ao banco de dados. |

#### 3.3 Catálogo do SGBD
- O catálogo (ou dicionário de dados) armazena os metadados (estrutura do banco de dados, tipos de dados, restrições, etc.).
- É consultado sempre que o SGBD precisa entender a estrutura dos dados.

## 4. Questões de Concurso Comentadas

#### 4.1 (ESPP/2010/MPE-PR – Técnico Científico)

**Item:** "Uma característica fundamental da abordagem de banco de dados é que seu sistema contém não apenas o próprio banco de dados, mas também uma definição ou descrição completa de sua estrutura e restrições. Essa definição é armazenada no catálogo do sistema gerenciador de banco de dados (...). A informação armazenada no catálogo é chamada \_\_\_\_\_, e descreve a estrutura do banco de dados."

**Alternativa correta:** **d) metadado**.

**Comentário:**
- **Metadados** são "dados sobre os dados".
- Descrevem a estrutura, tipos, restrições – tudo o que está no catálogo.
- **Cursor:** mecanismo para navegar pelos resultados de uma consulta.
- **Construtor:** método especial em programação orientada a objetos.
- **Instância:** os dados efetivamente armazenados em um dado momento.
- **Heap:** estrutura de dados ou área de memória.

#### 4.2 (CESPE/2016/FUB – Técnico de TI)

**Item:** "Em um projeto de banco de dados, a modelagem conceitual define quais dados vão aparecer no banco de dados, mas sem considerar a sua implementação."

**Gabarito:** **Certo (C)**.

**Comentário:**
- A **modelagem conceitual** (ex.: Diagrama Entidade-Relacionamento – DER) preocupa-se com **o que** será armazenado e seus relacionamentos.
- Não considera aspectos de implementação como:
  - Qual SGBD será usado.
  - Tipos de dados específicos da linguagem.
  - Índices, particionamento, etc.
- Esses aspectos são tratados nas fases de **modelagem lógica** (adequada ao modelo relacional) e **modelagem física** (implementação).

#### Gabarito das Questões

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (ESPP/2010/MPE-PR) | d |
| 02 (CESPE/2016/FUB) | C |