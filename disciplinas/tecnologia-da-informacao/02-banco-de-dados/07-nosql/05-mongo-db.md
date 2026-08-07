# MongoDB

## 1. Introdução e Características Gerais
- O MongoDB é um banco de dados open-source escrito em C++.
- Utiliza o formato BSON (Binary JSON), que armazena os dados em pares de chave-valor de forma binária, ocupando menos espaço e facilitando a extração de informações.
- Possui alta performance, é multiplataforma e não possui esquemas rígidos.
- Pertence à categoria NoSQL (Not Only SQL), sendo um banco de dados não relacional.

## 2. Consultas e Funcionalidades
- Permite consultas ad hoc, incluindo:
  - Expressões regulares;
  - Recuperação de documentos completos ou de partes específicas;
  - Amostras randômicas.
- Utiliza a MongoDB Query API para interagir com os dados.
- O Mongosh é a shell do MongoDB, onde as consultas são realizadas e as respostas são obtidas em linha de texto.

## 3. Replicação
- São criadas bases de dados réplica e uma primária.
- A primária (PRIMARY) é responsável pelas operações de escrita.
- As réplicas (SECONDARY) são utilizadas para operações de leitura.
- Se a primária falhar, uma réplica assume a posição de primária automaticamente.

> [!TIP] DICAS: 
> - A gravação é feita somente no PRIMARY, enquanto a leitura pode ser feita tanto no PRIMARY quanto nos SECONDARY.

## 4. Indexação
- Permite indexação de documentos e de campos dos mais variados tipos.
- A indexação melhora o desempenho do banco em pesquisas e consultas.
- Para criar um índice, utiliza-se o comando: `db.collection.createIndex({<fieldname>: (1|-1)})`. O valor 1 indica ordem crescente e -1 ordem decrescente.

> [!CAUTION] OBSERVAÇÃO: 
> - O índice é criado dentro de um par de chave-valor, especificando o nome do campo. Não se cria índice dentro do banco de dados ou da coleção diretamente.

## 5. Conceitos Fundamentais
- Base de dados: contêiner físico para coleções.
- Coleção: grupo de documentos (equivalente a uma tabela no modelo relacional).
- Documento: conjunto de pares chave-valor com esquema dinâmico (equivalente a uma linha no modelo relacional).

### 5.1 Esquema Dinâmico
- Documentos em uma mesma coleção podem ter campos diferentes.
- Um mesmo campo pode ter tipos de dados diferentes em documentos distintos.
- O MongoDB oferece a capacidade de validar esquemas durante operações de inserção e atualização, embora não seja obrigatório.

> [!TIP] DICAS: 
> - Diferentemente do modelo relacional, no MongoDB não há necessidade de definir previamente a estrutura dos documentos.

## 6. Principais Comandos e Operações

### 6.1 Exibição e Manipulação de Coleções
- `show collections`: exibe as coleções existentes no banco de dados atual.
- `db.createCollection("minhacolecao")`: cria uma nova coleção.
- `db.nome_da_colecao.drop()`: deleta uma coleção.

### 6.2 Inserção de Documentos
- `db.posts.insertOne({ title: "Post Title 1", body: "Body of post.", category: "News", likes: 1, tags: ["news", "events"], date: Date() })`: insere um documento na coleção "posts".
- `db.minhacolecao.insert({ "_id": 0, "site": "terminal root", "url": "terminalroot.com.br", "content": "sobre mongodb" })`: insere um documento com _id definido.

### 6.3 Consulta e Exibição de Dados
- `db.nome_da_colecao.find().pretty()`: exibe todos os documentos de uma coleção formatados.
- `db.posts.find({ category: "News" })`: exibe documentos com categoria "News".
- `db.forecedores.distinct("pais")`: retorna os valores distintos do campo "pais" em uma coleção, sem repetição.

### 6.4 Atualização e Remoção
- `db.minhacolecao.update({ 'content': 'mongodb' }, { $set: { 'content': 'mongodb para concursos' } })`: atualiza o conteúdo de um documento.
- `db.dados.remove({ "mail": "james@brown.org" })`: remove o documento com o campo "mail" igual a "james@brown.org".

### 6.5 Backup e Utilidades
- `mongodump`: aplicativo para criar backups no MongoDB. Exporta os dados em formato BSON, incluindo informações sobre Sharded Clusters e Replica Sets.
- `db.collection.count()`: retorna a quantidade de documentos em uma coleção.

> [!CAUTION] OBSERVAÇÃO: 
> - O MongoDB não utiliza SQL como linguagem de acesso. As operações são realizadas por meio de sua própria API e funções específicas.

## 7. Estrutura de Dados
- Os dados são armazenados no formato BSON (JSON-like), que é uma representação binária do JSON.
- A estrutura hierárquica do MongoDB é: Base de Dados ⟶ Coleções ⟶ Documentos ⟶ Pares Chave-Valor.
- No modelo relacional, a estrutura equivalente seria: Base de Dados ⟶ Tabelas ⟶ Linhas/Registros.

## 8. Projeções
- Uma projeção é uma expressão JSON que determina quais campos de um documento serão incluídos ou excluídos na saída final.
- A projeção consiste em pares de chave-valor (key:value).

> [!TIP] DICAS: 
> - A projeção permite filtrar os campos retornados, otimizando a consulta.

## 9. Database Profiling
- Componente do MongoDB que permite a coleta de informações detalhadas sobre as operações executadas em uma instância.
- Utilizado para análise de desempenho e investigação de operações degradadas.

> [!CAUTION] OBSERVAÇÃO: 
> - O Database Profiling é a ferramenta correta para análise de desempenho, não o Aggregation Pipeline, Shards, Mongodump ou MongoDB Compass.