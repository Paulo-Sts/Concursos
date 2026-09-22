# Banco De Dados - Conceitos Iniciais

## 1. Introdução Aos Bancos De Dados
- Os bancos de dados estão presentes em diversas atividades cotidianas, como recuperação de informações na internet, operações com cartão de crédito, compra de passagens aéreas, marcação de consultas, reservas em hotéis, operações bancárias, renovação de CNH, compras em supermercados e declaração do imposto de renda.
- De forma geral, tudo o que guarda informações pode ser chamado de banco de dados.

> [!TIP] DICAS:
> - A definição ampla de banco de dados como "tudo que guarda informações" é um conceito introdutório, mas para concursos é necessário conhecer a definição técnica.

### 1.1 Ambiente Dos Sistemas Tradicionais De Processamento De Arquivos
- A visão que se tinha dos sistemas tradicionais de processamento de dados era de um sistema altamente acoplado, onde os programas de aplicação faziam o próprio gerenciamento dos dados.
- Nesse modelo, para alterar o programa era necessário alterar os dados, e vice-versa.
- A evolução trouxe a divisão entre dados e programas, com a independência entre eles por intermédio do SGBD.

### 1.2 Limitações Dos Sistemas Tradicionais De Processamento De Arquivos
- Os sistemas tradicionais de processamento de arquivos apresentavam as seguintes limitações:
  - Complexidade no controle de segurança;
  - Inconsistência;
  - Problemas de atomicidade;
  - Ausência de padronização;
  - Complexidade para acessar dados;
  - Redundância não controlada.

> [!CAUTION] OBSERVAÇÃO:
> - Atomicidade é um conceito fundamental dos SGBDs que garante que todas as etapas de uma transação sejam concluídas ou revertidas integralmente.
> - A inconsistência e a redundância não controlada são problemas diretamente abordados pela definição de estruturas e restrições nos bancos de dados.

### 1.3 Compartilhamento De Dados – Redundância Controlada
- A redundância controlada é uma técnica que evita a duplicidade de informações.
- É utilizada principalmente em bases de dados com muitos leitores e poucas operações de escrita.

## 2. Conceitos Fundamentais De Banco De Dados
Um banco de dados é caracterizado por:
- Coleção de dados relacionados;
- Conjunto de dados integrados com o intuito de atender a uma comunidade de usuários;
- Fatos conhecidos que podem ser registrados e possuem significado implícito;
- Coleção lógica e coerente de dados.

### 2.1 Minimundo Ou Universo De Discurso (Uod – Universe Of Discourse)
O minimundo representa:
- Algum aspecto do mundo real;
- A parte do mundo real sobre a qual será criado o banco de dados e sua aplicação;
- Uma coleção logicamente coerente de dados com algum significado inerente;
- Uma construção para uma finalidade específica;
- Pode ser manual ou informatizado;
- Possui complexidade variável e qualquer tamanho.

## 3. Sgbd – Sistema De Gerenciamento De Banco De Dados
- O SGBD (ou DBMS – DataBase Management Systems) é um sistema de gerenciamento de banco de dados que permite a criação, manipulação e administração de bancos de dados.
- DBMS e SGBD são termos que se referem ao mesmo software que permite criar, gerenciar e armazenar dados.
- É uma coleção de programas que permite aos usuários criar e manter um banco de dados.
- Trata-se de um software de propósito geral que possibilita a definição, construção e manipulação de bancos de dados.
- O SGBD é dependente de tecnologia.

### 3.1 Funções Do Sgbd
- O SGBD incorpora as seguintes funções:
  - Definir um banco de dados envolve especificar os tipos de dados, as estruturas e as restrições para os dados que serão armazenados (a definição de estruturas e restrições busca resolver o problema da inconsistência);
  - Construir o banco de dados é o processo de armazenar os dados em algum meio de armazenamento controlado pelo SGBD;
  - Manipular o banco de dados inclui funções de recuperação e atualização de dados.

### 3.2 Exemplos De Sgbds
- Os SGBDs mais famosos em concursos são:
  - SQL Server;
  - PostgreSQL;
  - MySQL (MariaDB é uma versão modificada do MySQL);
  - Oracle.

> [!TIP] DICAS:
> - Fique atento aos exemplos de SGBDs, pois são frequentemente cobrados em provas de concursos.

## 4. Metadados
- Metadados são os dados sobre os dados.
- São informações sobre outros dados que permitem que estes sejam identificados, organizados, localizados e usados de forma mais eficiente.

## 5. Conceito Correto De Banco De Dados Relacional
- O banco de dados relacional não pode ser chamado de diretório.
- Para que um conjunto de informações seja considerado um banco de dados relacional, é necessária uma série de elementos para organizar as informações, como estruturas de tabelas, relacionamentos, chaves e restrições.
- Um diretório com arquivos não possui, por si só, a organização e as propriedades de um banco de dados relacional.

> [!CAUTION] OBSERVAÇÃO:
> - É uma pegadinha comum em provas: confundir um simples diretório com arquivos com um banco de dados relacional.
> - Um banco de dados relacional exige organização estruturada em tabelas, tuplas, atributos e chaves, além de um SGBD para gerenciar as informações.