# BANCO DE DADOS - Modelo Relacional

## 1. Introdução ao Modelo Relacional
- O modelo relacional foi introduzido por Codd em 1970, em uma pesquisa da IBM.
- Representa um banco de dados como um conjunto de relações (tabelas).
- O modelo relacional se tornou predominante com a evolução dos SGBDs, que, na maior parte do tempo, eram baseados nesse modelo.
- Inicialmente, os sistemas de arquivos evoluíram por meio de modelos hierárquicos e em rede, até a introdução do modelo relacional.
- Atualmente, quando se fala em banco de dados, é comum mencionar os bancos NoSQL, tema abordado na evolução dos bancos de dados.
- O modelo relacional é um modelo formal, fundamentado em princípios matemáticos, especialmente na teoria de conjuntos.
- A álgebra relacional é uma ferramenta matemática utilizada para manipulação e consulta dos dados.
- O SQL, linguagem de consulta estruturada, é baseado nos princípios da álgebra relacional.

> [!TIP] DICAS: 
> - O modelo relacional é formal porque se baseia na teoria de conjuntos.
> - A álgebra relacional é a base teórica do SQL.
> - Para concursos que cobram álgebra relacional, é fundamental assistir a aulas específicas sobre o tema, pois as questões podem envolver operações dessa álgebra.

> [!CAUTION] OBSERVAÇÃO: 
> - Para aqueles que desejam um conhecimento mais profundo sobre banco de dados, essencial para aprovação em concursos de alto nível, é fundamental assistir às aulas de Álgebra Relacional.
> - Esse conteúdo é crucial para a construção de bancos de dados, questões de desempenho e diversos outros aspectos.

## 2. Terminologia do Modelo Relacional
- No modelo relacional, existem terminologias, notações e nomenclaturas específicas que são importantes para a compreensão do assunto.
- Uma linha é chamada de tupla.
- Um cabeçalho de coluna é chamado de atributo.
- Uma tabela é chamada de relação.
- O tipo de dado que descreve os valores que um atributo pode ter é chamado de domínio.
- O domínio refere-se ao conjunto de valores possíveis para um atributo, representando o limite da informação que está sendo expressa.

> [!TIP] DICAS: 
> - Linha ⟶ Tupla
> - Cabeçalho de coluna ⟶ Atributo
> - Tabela ⟶ Relação
> - Tipo de dado ⟶ Domínio

## 3. Regras de Codd para o Modelo Relacional
- Existem 12 regras fundamentais para o modelo relacional, estabelecidas por Codd.
- Na verdade, o número de regras é 13, pois começa a contagem a partir de zero. No entanto, as regras são, em essência, 12.
- A primeira delas estabelece que, para um sistema ser considerado um SGBD, ele deve implementar essas 12 regras.
- A 12ª regra é redundante, pois afirma que não se pode violar nenhuma das regras anteriores.

> [!CAUTION] OBSERVAÇÃO: 
> - A "regra 12" é uma compilação das demais, indicando que não se pode violar as outras regras.

### 3.1 Regra 0
- O sistema precisa ser qualificado como relacional, como um banco de dados, e como um sistema de gerenciamento.

### 3.2 Regra 1
- Regra da informação: ao realizar o mapeamento, deve-se representar a informação no banco de dados de forma adequada.

### 3.3 Regra 2
- Regra de acesso garantido: trata do controle de acesso e da questão do uso por múltiplos usuários.
- Essa questão está relacionada à arquitetura ANSI/SPARC, que define camadas para organizar o gerenciamento de dados.

### 3.4 Regra 3
- Tratamento sistemático de valores nulos.

### 3.5 Regra 4
- Catálogo on-line baseado no modelo relacional.

### 3.6 Regra 5
- Sublinguagem Ampla de Dados.
- Inicialmente, surgiu a necessidade de um padrão para a comunicação com o banco de dados, o que levou à padronização do SQL.
- O ANSI criou o padrão SQL para que, ao utilizar um SGBD, fosse possível uma comunicação uniforme entre os usuários e os bancos de dados, independentemente da tecnologia utilizada.

### 3.7 Regra 6
- Atualização por meio de Visualizações (Views).

### 3.8 Regra 7
- Inserção, Atualização, e exclusão de Alto nível.
- A inserção, atualização e exclusão de alto nível referem-se a operações em que não é necessário acessar diretamente os ponteiros de memória para realizar modificações.

### 3.9 Regra 8
- Independência Física de dados: permite modificar as estruturas de memória sem afetar a camada lógica.

### 3.10 Regra 9
- Independência Lógica de Dados: assegura que, ao criar uma nova relação, não seja necessário se preocupar com sua implementação específica.

### 3.11 Regra 10
- Independência de Integridade: assegura que os dados permaneçam íntegros após o processo de normalização, evitando inconsistências.

### 3.12 Regra 11
- Independência de Distribuição: significa que o banco de dados pode estar fisicamente em diferentes locais, mas, ao realizar uma consulta (select) na estrutura do catálogo, não se sabe se o banco está em um único local ou distribuído em diferentes regiões.

### 3.13 Regra 12
- A não transposição das regras.

> [!TIP] DICAS: 
> - View é uma estrutura que visa proporcionar segurança e a separação de diferentes visões dos dados.
> - View é geralmente uma consulta armazenada que opera sobre as tabelas do banco de dados.
> - O SGBD deve permitir que atualizações sejam feitas por meio da View, ou seja, ao realizar um INSERT na View, o dado é enviado para a tabela subjacente.
> - Não é considerada uma boa prática realizar atualizações diretamente através de views.
> - Para alimentar os dados, deve-se realizar a inserção diretamente na tabela, utilizando a view apenas para consultas.

> [!CAUTION] OBSERVAÇÃO: 
> - O conceito de ACID, que se aplica ao Banco de Dados Relacional, envolve quatro características essenciais: atomicidade, consistência, isolamento e durabilidade.
> - Esses princípios garantem que o banco de dados seja robusto no que tange à integridade e consistência dos dados.
> - A escalabilidade horizontal refere-se à capacidade de adicionar recursos a um sistema, aumentando sua capacidade sem necessariamente aumentar a capacidade de uma única máquina.
> - Bancos de dados NoSQL são conhecidos por se destacarem na escalabilidade horizontal.
> - O Banco de Dados Relacional também é capaz de operar bem na escalabilidade horizontal, mas a garantia de atomicidade das transações pode gerar latência.

## 4. Conceitos Básicos

### 4.1 Esquema de Relação
- É uma expressão da forma R(A1, A2,..., An), onde:
  - R: nome da relação;
  - Ai: nome de um atributo, cujo domínio em R é denotado por dom(Ai);
  - n: grau da relação.
- Exemplo:
  - A relação "Estudante" possui cinco atributos, portanto, é de grau 5.
  - A relação "Disciplina" possui os atributos: código, nome, carga horária e número de créditos.
  - A relação "Aluno" inclui os atributos matrícula, nome, telefone, curso e idade, com as tuplas representando os dados de cada aluno.

> [!TIP] DICAS: 
> - O grau da relação é o número de atributos (colunas) que ela possui.
> - Embora as bancas de concurso não cobrem esse conceito com frequência, pode ser exigido em futuras provas.

### 4.2 Chaves no Modelo Relacional
- Superchave: é o conjunto mínimo de atributos necessários para identificar uma tupla.
- Chave primária: é uma superchave composta por um único atributo (idealmente), embora seja possível ter uma chave composta, que envolve mais de um atributo.
- Chave candidata: quando existe uma chave primária e outra chave na tabela, esta pode ser usada de maneira alternativa.
- Chave secundária: com a implementação e a compatibilização de paradigmas de orientação a objetos, o conceito de chave secundária deixou de ser amplamente utilizado.
- Chave primária: geralmente é um auto incremento, utilizado para representar o identificador único global (OIG).
- Exemplo:
  - DEPARTAMENTO (COD, NOME_DEP)
    - COD: chave primária.
    - NOME_DEP: nome do departamento.
- O ID geralmente será a chave, e o CODE refere-se a um código específico.
- Normalmente existe um relacionamento entre as entidades, como o caso do empregado, que terá a chave do departamento associada.
- Não se deve duplicar os nomes, pois isso configura redundância.

## 5. Características da Tabela
- Coluna: possui um nome distinto e representa um atributo.
- Atributo: possui um domínio.
- Domínio: possui valor atômico (indivisível).
- Valor Nulo (null): utilizado quando um atributo não possui valor ou seu valor não é conhecido.
- Linha: é distinta na tabela e representa uma tupla.

> [!CAUTION] OBSERVAÇÃO: 
> - Cada atributo possui um domínio, que normalmente é um valor atômico, ou seja, indivisível.
> - O domínio define o tipo de dado permitido para o atributo.
> - O tratamento de valores nulos é necessário, pois um atributo pode, eventualmente, não receber valor algum.

## 6. Restrições sobre uma Relação
- Domínio.
- Chave Primária.
- Integridade:
  - Restrições de Integridade da Entidade;
  - Restrições de Integridade Referencial.

### 6.1 Restrição de Domínio
- Determinam que, para cada tupla, o valor de um atributo deve ser um valor atômico do domínio.
- O domínio refere-se ao conjunto de valores permitidos para um atributo.
- O tipo de dado é uma restrição de domínio.
- Exemplos:
  - Matrícula dos Servidores: conjunto de todas as matrículas possíveis para a totalidade de servidores.
  - Placas de Veículos: conjunto de todas as placas de veículos dentro de determinada região.
  - Idade: conjunto de idades possíveis.
  - CPF do Servidor: string de 11 caracteres.
  - Placa do Veículo: string com três letras seguidas de um espaço e quatro dígitos: XYZ 9999.
  - Idade do Servidor: inteiro entre 18 e 100.

> [!CAUTION] OBSERVAÇÃO: 
> - O modelo relacional assegura consistência, impedindo, por exemplo, que um campo de matrícula aceite um nome como valor.
> - O banco de dados impede a inserção de dados que não atendem às restrições estabelecidas.

### 6.2 Restrição de Chave Primária
- Implica da possibilidade de identificar unicamente cada tupla da relação.
- As tuplas da relação devem ser distintas.
- Como garantir esta propriedade?
- Restrição de Unicidade - Definição de Chaves.
- A chave primária (PK) não pode ser nula em nenhuma tupla de qualquer relação.
- Se a chave for composta (mais de um atributo), nenhum deles pode ser nulo.
- A chave primária não pode se repetir.

> [!TIP] DICAS: 
> - A chave primária, por ser única, nunca pode ser nula, pois um valor nulo não representa um valor válido.
> - Caso um atributo seja nulo, pode haver múltiplos registros com o valor nulo, o que impede a diferenciação única entre as tuplas.
> - Se a chave primária for composta, os atributos que a compõem também não podem ser nulos.

> [!CAUTION] OBSERVAÇÃO: 
> - A notação relacional exige que a chave primária seja representada sem sublinhado.
> - Quando o nome de um atributo está sublinhado, ele representa a chave primária.
> - A diferença entre "nulo" e "vazio" deve ser compreendida de forma clara: "nulo" representa a ausência de valor, enquanto "vazio" indica que há um valor presente, embora seja um caractere de espaço em branco.

### 6.3 Restrição de Integridade Referencial
- Mantém a consistência entre tuplas de duas relações.
- Declara que se uma tupla t1 em uma relação R1 faz referência a uma relação R2, então t1 deve fazer referência a uma tupla existente em R2.
- É definida entre a chave estrangeira (FK) de uma relação esquema R1 e a chave primária (PK) de uma relação esquema R2.
- FK de R1 é chave estrangeira de R1, que faz referência à chave primária (PK) de R2, se:
  - Os atributos de FK têm os mesmos domínios que os atributos de PK.
  - Um valor de FK em uma tupla t1 do estado corrente de R1(R1): ocorre como um valor de PK para alguma tupla t2 no estado corrente R2(R2) (t1 [FK]= t2 [PK]) ou tem o valor null (t1 [FK]= null).
- Exemplo:
  - Em um relacionamento entre entidades, como aluno e dependente, um dependente deve estar sempre associado a um funcionário.
  - Não pode existir um dependente sem um funcionário.
  - Para garantir essa associação, é necessário utilizar a chave do funcionário.
  - No modelo conceitual, essa chave é chamada de chave parcial.
  - A chave estrangeira do dependente, que é o CPF do funcionário, deve ser preenchida obrigatoriamente para manter a consistência do relacionamento entre as entidades.
  - Em uma tabela com relacionamento, a chave é composta, ou seja, consiste na combinação de dois atributos, como o nome do dependente e o CPF do funcionário.
  - O nome do dependente por si só não pode ser considerado uma chave; é necessário criar uma chave adicional, como uma ID, para identificar de forma única o dependente junto com o CPF do funcionário.

> [!TIP] DICAS: 
> - A chave estrangeira faz referência à chave primária de uma tabela diferente.
> - Exceção: autorrelacionamento, que ocorre quando uma chave estrangeira referencia a chave primária da mesma tabela.
> - A chave estrangeira contém os valores que devem estar presentes previamente na chave primária da tabela de referência, e não o contrário.
> - A chave estrangeira depende da existência dos valores na chave primária, e não o inverso.

> [!CAUTION] OBSERVAÇÃO: 
> - Em um departamento, o código funciona como chave primária, além da sigla e do nome do departamento.
> - O servidor é identificado pela matrícula, que também é chave primária, e deve conter a chave estrangeira (FK), que corresponde ao código do departamento, sendo do mesmo tipo de dado.
> - A chave estrangeira (FK) pode ter valor nulo, indicando a ausência de alocação do servidor no departamento (dependendo da cardinalidade).
> - A chave primária não pode ter valores nulos.
> - A chave estrangeira pode ter valores nulos, o que não ocorre com a chave primária.

## 7. Violação de Restrições de uma Relação
- As operações de INSERÇÃO (insert), REMOÇÃO (delete) ou ATUALIZAÇÃO (update), quando aplicadas em bancos de dados relacionais, não podem violar as restrições de domínio, de chave e de integridade de entidade e referencial.
- O Sistema de Gerenciamento de Banco de Dados (SGBD) assegura a integridade, impedindo operações que ferem essas restrições.
- Exemplos de violação:
  - Inserir tupla em SERVIDOR com Matricula=null viola restrição de integridade de entidade.
  - Inserir tupla em SERVIDOR com Matricula já existente no BD viola restrição de chave.
  - Inserir tupla em SERVIDOR com Código de Departamento inexistente em departamento viola integridade referencial.
  - Excluir um DEPARTAMENTO que é referenciado por tuplas em SERVIDOR.

> [!CAUTION] OBSERVAÇÃO: 
> - Excluir um departamento que ainda é referenciado por tuplas em servidor também viola a integridade referencial, pois, ao excluir o departamento, os dados relacionados aos servidores que o referenciam seriam corrompidos.
> - O SGBD impede essas ações, mas também oferece meios para configurar regras que, em certos casos, permitam a exclusão ou atualização de dados de forma controlada.
> - No SQL, é possível configurar comportamentos específicos para a exclusão de registros, como apagar também todos os vínculos de servidores relacionados a esse departamento.
> - Normalmente configura-se o sistema para impedir esse tipo de ação, pois busca-se manter o histórico dos dados.