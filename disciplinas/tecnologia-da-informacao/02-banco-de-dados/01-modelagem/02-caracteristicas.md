# Banco de Dados - Tipos de Usuários, Linguagens e Arquitetura SGBD

## 1. Tipos De Usuários Em Banco De Dados

### 1.1 Projetista De Banco De Dados
- Responsável pela identificação dos dados a serem armazenados e pela escolha da estrutura apropriada para representar e armazenar esses dados.
- No projeto de bancos de dados existem diferentes níveis de participantes, como o responsável pela modelagem conceitual (nível mais alto).

### 1.2 Administrador De Banco De Dados (DBA - Database Administrator)
- É responsável pela administração do banco de dados e do SGBD.
- Atribuições:
  - Monitora o uso do BD em relação à segurança, tempo de resposta, etc.;
  - Especifica as regras de segurança e autoriza o acesso ao BD;
  - Define estruturas de armazenamento e métodos de acesso;
  - Define procedimentos de cópia (backup), recuperação, dentre outros.

### 1.3 Programador De Aplicações
- Escreve os programas de aplicação.
- Realiza requisições ao SGBD por meio das aplicações (Select, Insert, Delete e Update) ou através de ferramentas RAD (Rapid Application Development).

### 1.4 Usuário Final
- Manipula o banco de dados por meio de linguagens de consulta e programas de aplicação.
- Classificações:
  - Leigos: Interagem com o BD através dos programas;
  - Casuais: Acessam o BD eventualmente, podendo solicitar informações diferentes de cada vez. São de nível hierárquico médio ou elevado;
  - Avançados: Interagem com o BD submetendo requisições em uma linguagem de consulta de banco de dados (por exemplo, SQL).

### 1.5 Administrador De Dados
- Não deve ser confundido com o administrador de banco de dados (DBA).
- É importante quando há a necessidade de uma visão única dos dados (Bases Corporativas).
- Opera uma variedade de bancos de dados, atendendo a diversas áreas de negócio.
- Age quando há falta de uniformidade nos dados, implicando em redundância em diversos níveis, tais como bancos de dados, colunas, tabelas, dentre outros.
- Atribuições:
  - Definir padrões de nomenclatura;
  - Deve conhecer as informações representadas no banco de dados e ter a preocupação com a integração das informações entre os bancos de dados distintos;
  - Fazer o levantamento de requisitos funcionais do banco de dados;
  - Criar o modelo conceitual do banco de dados.

> [!TIP] DICAS:
> - Enquanto o DBA cuida de questões como monitoramento e segurança, o Administrador de Dados cuida da administração dos dados inseridos e de sua organização.

## 2. Linguagens Do SGBD
- O SGBD apresenta uma estrutura em camadas que permite a edição de forma que não haja reflexo direto na aplicação.
- Cada nível pode ser editado sem que outra parte da estrutura seja afetada.

### 2.1 Linguagem De Definição De Visões (VDL - View Definition Language)
- Especifica o esquema externo ou de visão.
- Lida com os tipos de usuários e seus acessos.

### 2.2 Linguagem De Definição De Dados (DDL - Data Definition Language)
- Usada para especificar o esquema conceitual.
- Na maioria dos SGBDs, a DDL é utilizada para definir tanto o esquema externo, conceitual e interno.

### 2.3 Linguagem De Definição De Armazenamento (SDL - Storage Definition Language)
- Utilizada para especificar o esquema interno.

> [!CAUTION] OBSERVAÇÃO:
> - A linguagem SQL (Structured Query Language) combina VDL, DDL e DML.

### 2.4 Linguagem De Manipulação De Dados (DML - Data Manipulation Language)
- O SGBD fornece uma linguagem de manipulação de dados para essa finalidade.
- A manipulação inclui recuperação, inclusão, exclusão e modificação dos dados (CRUD - Create, Read, Update e Delete).
- Funções:
  - Recuperação de dados armazenados (SELECT);
  - Inserção de novos dados (INSERT);
  - Remoção de dados (DELETE);
  - Modificação de dados (UPDATE).

#### 2.4.1 Tipos De DMLs
| TIPO | CARACTERÍSTICA | EXEMPLO |
|------|----------------|---------|
| Procedurais | Requerem do usuário a especificação de qual dado é necessário e de como obtê-lo | Embutidas em linguagem de programação (Pascal, C, C++) ou oferecidas pelo SGBD (PL/SQL, Transact-SQL) |
| Não procedurais | Requerem do usuário a especificação de qual dado é necessário sem especificar como obtê-lo | Usualmente mais fáceis de aprender e usar |

### 2.5 Exemplo De DDL
- Criação de uma tabela que possui informações sobre veículos:
  - CREATE TABLE (criação);
  - ALTER TABLE (alteração da estrutura);
  - DROP TABLE (exclusão).

```sql
CREATE TABLE AUTOMOVEL
(PLACA CHAR(7) PRIMARY KEY NOT NULL,
ANO INT NOT NULL,
MARCA VARCHAR(30) NOT NULL,
MODELO VARCHAR(30) NOT NULL,
COR VARCHAR(20)
);
```
- Para a criação da tabela são especificados os tipos de dados utilizados e a chave primária de identificação.
- Isso restringe as informações adicionadas para que cada item no banco de dados apresente a mesma quantidade de informações e não existam inconsistências.

### 2.6 Exemplo De DML
- Selecionar todos os veículos do ano de 2016:
```sql
SELECT * FROM AUTOMOVEL WHERE ANO = 2016;
```

## 3. Módulos E Componentes Do SGBD
- O SGBD possui as características ACID em todas as suas relações:
  - Atomicidade: a informação deve chegar até o fim da cadeia;
  - Consistência: a informação deve atravessar os diferentes módulos se mantendo consistente;
  - Independência (Isolamento): uma transação não deve se misturar a outra;
  - Durabilidade: a informação deve permanecer salva, sem possibilidade de deterioramento.

### 3.1 Componentes
- Gerenciador de dados armazenados: controla o acesso aos dados armazenados no disco.
- Compilador (Processador) DDL: compila as definições do esquema, armazenando-as no catálogo do SGBD.
- Processador do BD em tempo de execução (run-time): recebe as operações de recuperação ou atualização e executa tais operações sobre o banco de dados.
- Compilador de consultas: compila as consultas de alto nível que são fornecidas interativamente, e gera chamadas ao run-time.
- Pré-compilador: extrai comandos DML de um programa de aplicação escritos em uma linguagem de programação hospedeira e envia ao compilador DML.
- Compilador da DML: recebe e compila os comandos DML extraídos pelo pré-compilador, e gera o código objeto para acesso ao banco de dados.

## 4. Metadados
- A informação armazenada no catálogo é chamada metadado.
- Descreve a estrutura do banco de dados.
- Contém informações como: a estrutura de cada arquivo, o tipo e o formato de armazenamento de cada item de dados e diversas restrições sobre os dados.

> [!CAUTION] OBSERVAÇÃO:
> - A modelagem conceitual define quais dados vão aparecer no banco de dados, mas sem considerar a sua implementação. Em um nível conceitual não há preocupação com a implementação.