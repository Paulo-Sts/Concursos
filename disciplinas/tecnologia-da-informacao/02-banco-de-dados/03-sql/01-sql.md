# Banco de Dados - Linguagem SQL

## 1. SQL (Structured Query Language)
- SQL é uma linguagem de consulta que implementa as operações da álgebra relacional de forma amigável.
- O movimento NoSQL (Not Only SQL) não eliminou os bancos relacionais, pois o SQL é baseado em fundamentos sólidos como matemática, consistência e normalização.
- SQL foi padronizada pelo American National Standards Institute (ANSI), garantindo uniformidade na linguagem.
- Desenvolvida por pesquisadores da IBM – System R.
- Inicialmente chamada de SEQUEL (Structured English Query Language).
- ISO e ANSI lançaram em 1986 a primeira versão do padrão da linguagem SQL, o SQL-86 (SQL1).
- Em 1992, houve uma revisão e expansão do padrão, gerando a SQL2 (SQL92).
- Em 1999, SQL3 trouxe características de BDOO (SQL99), incluindo novos tipos de dados (CLOB), predicados e tipos abstratos de dados.
- Versões posteriores: SQL:2003, SQL:2006, SQL:2008, SQL:2011 e SQL:2016.
- O SQL permite definir estrutura de dados e restrições de integridade, modificar dados no BD, especificar restrições de segurança e controle de transações e utilizar linguagens hospedeiras.

> [!CAUTION] OBSERVAÇÃO: 
> - Linguagem hospedeira refere-se à linguagem em que o SQL pode estar embutido dentro de SGBDs. Não tem relação com o filme Alien, o oitavo passageiro.

### 1.1 Esquema
- Um esquema é definido por um nome e inclui um identificador de autorização para indicar o usuário que é o dono do esquema.
- Exemplo: CREATE SCHEMA PF AUTHORIZATION agente_silva.
- Esquema inclui tabelas, restrições, visões (views) e domínios.
- Alguns bancos separam o conceito de esquema do conceito do próprio banco que está no SGBD. Outros consideram tudo junto.
- O esquema representa a estrutura das informações que estão no banco de dados.

### 1.2 Classificação dos Comandos em SQL
- Os comandos em SQL são divididos em categorias.

#### 1.2.1 DDL (Data Definition Language)
- Criação do esquema do banco de dados.
- Comandos: CREATE, DROP, ALTER e, às vezes, RENAME.
- Atuam diretamente sobre os objetos do banco, como tabelas.

#### 1.2.2 DML (Data Manipulation Language)
- Manipulação de dados propriamente ditos.
- Comandos: INSERT, UPDATE, DELETE e SELECT (clássicos do CRUD).

#### 1.2.3 DCL (Data Control Language)
- Controle de acesso e segurança.
- Comandos: GRANT e REVOKE.

#### 1.2.4 DTL (Data Transaction Language)
- Controle de transações.
- Comandos: COMMIT, ROLLBACK e SAVEPOINT.

> [!CAUTION] OBSERVAÇÃO: 
> - Algumas bancas utilizam a classificação DQL (Data Query Language) exclusivamente para o comando SELECT.
> - Essa classificação não é consenso entre os professores, sendo considerada desnecessária por criar uma categoria para um único comando.

> [!TIP] DICAS: 
> - É importante classificar corretamente os comandos, pois bancas como a FGV podem exigir conhecimento aprofundado.
> - Não é aceitável errar uma questão que pergunta o que são DDL e DML.

## 2. DDL (Data Definition Language)
- Permite especificar um conjunto de relações, bem como o esquema, o domínio de valores, as restrições de integridade e o conjunto de índices de cada relação.

### 2.1 CREATE TABLE
- Usado para especificar uma nova relação (tabela), incluindo seus atributos e restrições.
- Exemplo:
```sql
CREATE TABLE empregado (
    cod_empregado VARCHAR(9) NOT NULL,
    nome VARCHAR(15),
    data_nascimento DATE,
    cod_departamento INT NOT NULL DEFAULT 0,
    PRIMARY KEY (cod_empregado),
    FOREIGN KEY (cod_departamento) REFERENCES departamento(cod_departamento) ON DELETE CASCADE
);
```

- Tipos de dados comuns:
  - VARCHAR(n): armazena apenas a quantidade de caracteres utilizada. Exemplo: varchar(15) com “José” ocupa 4 caracteres.
  - CHAR(n): sempre ocupa o espaço total definido. Exemplo: char(15) com “José” ocupa 15 caracteres (os 11 restantes são preenchidos com espaços em branco).
  - INT: números inteiros, sem casas decimais.
  - DECIMAL(p, s): números reais com precisão definida.
  - DATE: formato pode variar dependendo do SGBD.

- Restrições (constraints):
  - NOT NULL: indica que o campo não pode estar vazio (null).
  - PRIMARY KEY: define a chave primária da tabela (não pode ser nula).
  - FOREIGN KEY: define a chave estrangeira, que referencia outra tabela.
  - DEFAULT: define um valor padrão para o campo. Exemplo: DEFAULT 0.

> [!CAUTION] OBSERVAÇÃO: 
> - Espaço em branco ou vazio tem representação na tabela ASCII e é diferente de null. O null representa ausência de valor.
> - O campo “not null” apenas indica se o campo pode ou não estar vazio. Se houver qualquer valor, mesmo que incompleto, já não será considerado null.

#### 2.1.1 ON DELETE CASCADE
- Define o comportamento ao se deletar um departamento.
- Com ON DELETE CASCADE: se um departamento for excluído, todos os empregados vinculados a ele também serão removidos automaticamente.
- Sem ON DELETE CASCADE: não será possível apagar o departamento caso haja um funcionário vinculado a ele.

> [!TIP] DICAS: 
> - O campo “codigo do supervisor” é uma chave estrangeira que pode ser nula, pois nem todos os empregados são supervisores.
> - Trata-se de uma situação de autorrelacionamento, em que a tabela “empregado” referencia a si mesma.

### 2.2 ALTER TABLE
- Usado para adicionar ou remover atributos e restrições de uma relação, e para alterar a definição de um atributo.
- Exemplos:
  1. ALTER TABLE Produto ADD Marca VARCHAR(30); (adiciona uma nova coluna)
  2. ALTER TABLE Produto ALTER COLUMN Preco SET DEFAULT 0; (altera característica de coluna existente)
  3. ALTER TABLE Produto DROP COLUMN Preco; (exclui uma coluna)

### 2.3 DROP TABLE
- Usado para remover uma relação de um banco de dados.
- Exemplo: DROP TABLE Produto; (elimina toda a tabela)

## 3. DML (Data Manipulation Language)
- Comandos para manipulação de dados.

### 3.1 Comandos Principais
- INSERT: inclusão de dados.
- DELETE: exclusão de dados.
- UPDATE: alteração de dados.
- SELECT: seleção de dados.

### 3.2 SELECT
- Representa a operação de seleção da álgebra relacional.
- A maioria das questões em provas é baseada em consultas.
- SELECT * retorna todos os atributos da tabela.
- Pode-se especificar quais atributos se deseja consultar, aplicando filtros e condições.

### 3.3 Operadores
- Utilizados em conjunto na cláusula WHERE para filtrar o resultado da consulta.

#### 3.3.1 Operadores Relacionais
- Utilizados para realizar comparações entre valores.

| OPERADOR | SIGNIFICADO | EXEMPLO |
|----------|-------------|---------|
| = | Igual | select * from produto where codigo = 10 |
| < | Menor que | select * from produto where qtdc < 5 |
| <= | Menor ou igual a | select * from produto where preco <= 50 |
| > | Maior que | select * from produto where preco > 500 |
| >= | Maior ou igual a | select * from produto where preco >= 500 |
| <> | Diferente | select * from produto where codigo <> 2 |

#### 3.3.2 Operadores Lógicos
- Utilizados para realizar operações que tenham um resultado booleano (verdadeiro/falso).

| OPERADOR | SIGNIFICADO | EXEMPLO |
|----------|-------------|---------|
| AND | E | select * from produto where marca = 'LG' and preco > 1500 |
| OR | OU | select * from produto where qtdc < 5 or qtdc > 100 |
| NOT | NEGAÇÃO | select * from produto where preco is not null |

#### 3.3.3 Operadores Especiais
| OPERADOR | SIGNIFICADO | EXEMPLO |
|----------|-------------|---------|
| IS NULL ou IS NOT NULL | Testa se o valor é nulo ou não nulo | select * from produto where preco is null |
| BETWEEN | Delimita um intervalo de valores para a consulta | select * from produto where preco between 10 and 100 |
| LIKE | Define um padrão para uma cadeia de caracteres | select * from produto where nome like 'A%' |
| IN | Compara o valor de uma coluna com um conjunto | select * from produto where codigo in (2, 5, 15, 29) |
| DISTINCT | Elimina duplicidades | select distinct categoria from produto |

> [!TIP] DICAS: 
> - A linguagem SQL exige prática constante para obter um bom desempenho, especialmente em questões elaboradas por bancas como a FGV.
> - Não basta apenas assistir às aulas: é fundamental praticar, testar comandos e realizar exercícios.
> - O aprendizado em SQL demanda esforço individual, com revisão e aplicação do conteúdo estudado.
> - SQL é uma linguagem declarativa, o que significa que é possível resolver um mesmo problema de diversas formas.
> - Apenas a combinação entre teoria e prática torna o estudante realmente proficiente em SQL.