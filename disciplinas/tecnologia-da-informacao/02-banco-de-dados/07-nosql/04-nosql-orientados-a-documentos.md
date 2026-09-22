# NoSQL Orientados a Documentos

## 1. Relembrando os Modelos NoSQL
- Antes de aprofundar no modelo orientado a documentos, é importante relembrar os outros tipos de bancos NoSQL para contextualizar.
- Coluna: utilizado para pegar um Data 7 e usar na ciência de dados.
- Chave-valor: é para ter uma relação de documentos, relacionados a cada um dos rashs.
- Grafo: utilizado para representar um grafo dentro do banco.

## 2. Modelo Orientado a Documentos
- É para armazenar arquivos semiestruturados.
- Enquanto os bancos de dados relacionais tradicionais são especialistas em armazenar tabelas, os bancos de dados orientados a documentos trabalham com dados semiestruturados, como HTML, XML, JSON.
- Os arquivos têm a internet em comum.

### 2.1 Exemplo Prático: Nota Fiscal Eletrônica (XML)
- O sistema de nota fiscal da Receita Federal gera um XML que representa uma nota fiscal.
- O XML é um formato com tags que trazem todos os dados da nota:
  - Tag "produto" com o produto discriminado;
  - Tag com o CPF do comprador;
  - Tag com o CNPJ do vendedor.
- Todas as informações estão armazenadas em pares de chave e valor.
- Esse XML pode ser consumido por qualquer outro aplicativo.

### 2.2 Limitação dos Bancos Relacionais com Dados Semiestruturados
- O banco de dados relacional não nasceu para trabalhar com XML.
- É mais lento, pois possui uma série de travas para garantir que o dado está estruturado.
- Para dados semiestruturados, é necessário um banco que, sem muitas amarras, consiga guardar documentos XML e JSON e que consiga operá-los de forma rápida.
- A velocidade é essencial para grandes bases de dados com pesquisas específicas que precisam responder em uma velocidade razoável.

## 3. Características dos Bancos Orientados a Documentos
- Armazenam e consultam documentos JSON, BSON (MongoDB), XML, OWL, HTML, etc.
- Cada documento é uma linha ou registro da base.

### 3.1 Estrutura de Armazenamento
- Não existe esquema.
- Não existe informação sobre um documento fora do documento.
- Isso é o que traz a velocidade, pois não é necessário fazer joins entre tabelas como em bancos relacionais.
- Exemplo: em uma base relacional, na tabela cliente, não é possível encontrar o endereço sem ir a outra tabela.
- Em bancos orientados a documentos, tudo está no próprio documento.

### 3.2 Representação dos Dados
- Representa-se, dentro do banco, um documento.
- Há uma lista de pares de chave-valor.
- Exemplo de estrutura XML:
  - `<autor> Vitor Kesseler </autor>`;
  - `<livro> Nome do livro </livro>`.

### 3.3 Casos de Uso
- Aplicativos mobile.
- E-Commerce: é possível armazenar todos os dados do produto (preço, nome, modelo, especificações, largura, altura, comprimento) em um único documento; o carrinho também é organizado com pares de chave-valor; a página é construída rapidamente sem necessidade de buscar informações em outras tabelas.
- Internet das Coisas (IoT): Alexa, geladeira com Wi-Fi, TV com Wi-Fi.
- Analytics em tempo real: coleta de informações ao vivo da internet, transformadas em XML ou JSON e enviadas para o banco.
- Blogs e CMS: uma postagem de blog é, na verdade, um arquivo JSON com texto, autor, data.

> [!TIP] DICAS:
> - O foco é a velocidade para consultas, pois os dados já estão todos no documento.
> - Bancos relacionais são ruins para dados semiestruturados pela necessidade de joins.
> - HTML, XML, JSON, OWL são exemplos clássicos de dados semiestruturados.

## 4. Sobre Índices e Esquemas
- Esquema é uma estrutura maior acima das tabelas do banco de dados relacional que define como serão suas tabelas.
- Em bancos orientados a documentos, não se tem um esquema, apenas pares chave-valor.
- Índice é a ideia de indexar o banco para que as consultas tragam respostas mais rapidamente.
- Normalmente, ao fazer uma consulta, é preciso ordenar os resultados (maior-menor, ordem alfabética).
- O índice já traz a ordem, sem perder tempo ordenando.
- A ordenação é cara computacionalmente, pois o computador precisa olhar linha por linha.
- Índices foram criados como estruturas/colunas auxiliares que ordenam e indexam a base, deixando as pesquisas mais comuns já salvas.

> [!CAUTION] OBSERVAÇÃO:
> - A inexistência de esquema NÃO impossibilita a definição de índices.
> - Índices são estruturas auxiliares que podem ser criadas independentemente da existência de um esquema formal.

## 5. Atomicidade e Transações
- Atomicidade significa que as transações são únicas e indivisíveis.
- Em bancos orientados a documentos, a atomicidade é garantida, normalmente, em nível do documento (XML).
- Exemplo: ao atualizar um documento XML alterando os campos nome, autor, cidade, data de nascimento, se faltar energia no processo, a transação incompleta é desfeita.
- Geralmente, transações ocorrem no nível de documento e são consideradas atômicas.
- Transações envolvendo mais de uma operação não são possíveis na maioria dos bancos.
- RavenDB (base orientada a documentos) é uma exceção, pois suporta transações atômicas com múltiplas operações em vários documentos.

## 6. Expressões Regulares
- Não há previsão de uso de expressão regular nos bancos de dados NoSQL orientados a documentos.
- Expressão regular é uma forma de escrever uma consulta no formato de texto, mas não é suportada nesse modelo.

## 7. Principais SGBDs NoSQL por Modelo
| TIPO DE MODELO | SGBD MAIS FAMOSO |
|----------------|------------------|
| Orientado a grafo | N4OJ (Neo4J) |
| Orientado a coluna | Cassandra |
| Chave-valor | Redis |
| Orientado a documento | MongoDB |