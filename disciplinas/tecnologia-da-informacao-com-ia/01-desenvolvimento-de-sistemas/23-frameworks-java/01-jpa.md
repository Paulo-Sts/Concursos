# Persistência com JPA e Hibernate

## 1. Java Persistence API (JPA)
- O JPA é uma especificação, não uma implementação, que define uma interface comum para frameworks ORM (Object-Relational Mapping).
- A implementação mais utilizada do JPA é o Hibernate, mas existem outras como EclipseLink.
- O JPA faz parte do ecossistema Jakarta EE (anteriormente Java EE).
- Exemplo: assim como uma interface define métodos que uma classe deve implementar, o JPA define um padrão que as tecnologias de persistência devem seguir.
- A padronização permite a troca entre diferentes implementações (ex.: Hibernate para EclipseLink) de forma simplificada, pois todas seguem a mesma interface.

### 1.1 Mapeamento Objeto-Relacional (ORM)
- O ORM facilita o mapeamento entre classes Java e tabelas de bancos de dados relacionais.
- Resolve a complexidade das relações entre objetos em Java (redes complexas de relacionamentos) e as referências em tabelas relacionais (chaves estrangeiras).
- Com JPA e Hibernate, é possível manipular tabelas como se fossem objetos, simplificando o trabalho do desenvolvedor Java.

> [!CAUTION] OBSERVAÇÃO: 
> - O Hibernate NÃO é uma especificação/interface; ele é uma tecnologia que IMPLEMENTA a especificação JPA.
> - O JPA NÃO é uma implementação do Hibernate; o JPA é a especificação e o Hibernate é a implementação.

## 2. Objetivo e Benefícios do JPA
- Objetivo: facilitar o mapeamento entre classes Java e tabelas de bancos de dados relacionais.

### 2.1 Abstração do Código SQL com JPQL
- O JPA permite abstrair o código SQL através da linguagem JPQL (Java Persistence Query Language), uma linguagem de alto nível.
- Com JPQL, desenvolvedores escrevem consultas sem acoplamento direto ao banco de dados específico.
- O código JPQL é traduzido para o SQL nativo do banco configurado, promovendo portabilidade entre diferentes bancos de dados.

> [!CAUTION] OBSERVAÇÃO: 
> - JPQL NÃO é acesso direto a tabelas do banco de dados. O acesso direto é feito pelo SQL, enquanto a JPQL é traduzida em SQL para acessar as tabelas de entidades.

### 2.2 Configuração e Dialeto
- O arquivo persistence.xml define configurações como nome da unidade de persistência, classes mapeadas e propriedades específicas do banco (driver, usuário, senha e dialeto).
- O dialeto é configurado conforme o tipo de banco utilizado (ex.: SQL Server, MySQL, H2) e facilita a tradução de JPQL para o SQL específico daquele banco.
- A configuração do dialeto garante que o JPA realize a tradução correta para o banco configurado.

### 2.3 Controle de Transações
- Transações permitem que um conjunto de operações seja tratado como uma única operação indivisível.
- Isso garante que todas as operações sejam concluídas para obter um resultado final preciso; em caso de erro, o processo deve ser reiniciado sem perda de dados.
- Exemplo: cálculo de imposto devido na Receita Federal com base em declarações de Imposto de Renda, onde todas as etapas devem ser realizadas sem falhas.

### 2.4 Evolução das Versões do JPA
- JPA 1.0: 2006;
- JPA 2.0: 2008, introduziu a Criteria API, recurso que possibilita a criação de consultas de forma programática e tipada (código SQL escrito de forma tipada);
- JPA 2.1: 2013;
- JPA 2.2: 2017, com suporte a Java 8;
- JPA 3.0: 2020, com o pacote jakarta.persistence e transição para o Jakarta EE.

## 3. Componentes Principais do JPA
- Ao representar o mundo real no Java, cria-se uma classe que modela uma entidade (ex.: classe "Estudante" com atributos como matrícula e nome).
- Essas classes são mapeadas para tabelas correspondentes no banco de dados.
- O JPA utiliza o Entity Manager para gerenciar as entidades.
- Para criar o Entity Manager, utiliza-se uma fábrica (Entity Manager Factory) baseada no padrão de projeto Factory, devido à complexidade de criação desse objeto, que depende de um arquivo XML de configuração.

### 3.1 Arquivo Persistence.xml
- O arquivo persistence.xml é fundamental no contexto do JPA.
- Define as configurações do banco de dados: nome da unidade de persistência, classes que serão mapeadas, propriedades específicas (banco, driver, usuário, senha e dialeto).
- A partir da versão 5 do Java, é possível utilizar anotações que simplificam a configuração, evitando o mapeamento manual de todas as entidades no arquivo XML.

### 3.2 Exemplo Prático de Operação
- Cria-se uma transação;
- Define-se uma string com o código JPQL (ex.: consulta que retorna todos os registros da classe "Pessoa" cujos nomes são iguais a "João");
- Executa-se a consulta, resultando em uma lista de objetos do tipo entidade;
- Itera-se sobre a lista para, por exemplo, imprimir os nomes de cada "Pessoa";
- Encerra-se a transação e fecha-se o Entity Manager.

## 4. Principais Anotações do JPA
- @Entity: marca uma classe Java como uma entidade persistente;
- @Table: especifica a tabela do banco de dados correspondente. Exemplo: @Table(name = "nome_da_tabela") quando o nome da classe é diferente do nome da tabela. Se forem iguais, a anotação não é necessária;
- @Id: define a chave primária da entidade.

### 4.1 Mapeamento de Herança
- O JPA suporta mapeamento de herança entre entidades.
- Para isso, utiliza-se a anotação @MappedSuperclass.

## 5. Exemplo de Estrutura de Tabela
| COLUNA | TIPO | DESCRIÇÃO |
|---|---|---|
| id | Long | Chave primária |
| nome | String | Nome da pessoa |