# Anotações

# MONGODB (Banco de Dados Orientado a Documentos)

## 1. Características Fundamentais do MongoDB

### 1.1 Definição e Arquitetura Básica

- **Classificação:** Banco de dados **NoSQL** orientado a **documentos**.
- **Código:** ***Open-source*** escrito em **C++**.
- **Multiplataforma:** Compatível com diversos sistemas operacionais.
- **Formato de Dados:** Utiliza ***BSON*** (Binary JSON), um formato binário do JSON que organiza os dados em **pares de chave-valor**.
    - Vantagem do BSON: Armazenamento binário ocupa menos espaço e é mais rápido para extração de informações.

### 1.2 Estrutura Hierárquica (Conceitos)

| CONCEITO MONGODB | EQUIVALENTE NO MODELO RELACIONAL |
| :--- | :--- |
| **Base de Dados (*Database*)** | Base de Dados / *Schema* |
| **Coleção (*Collection*)** | **Tabela** |
| **Documento (*Document*)** | **Linha / Registro** |

- **Documento:** Conjunto de pares **chave-valor** com **esquema dinâmico** (*schema-less*).
- **Flexibilidade de Esquema (FGV/2022):**
    - **I - Número de Campos:** **ERRADO**. Documentos de uma mesma coleção **NÃO** precisam possuir o mesmo número de campos.
    - **II - Tipo de Dados:** **CERTO**. Um campo (ex: `date`) pode ter diferentes tipos de dados em documentos diferentes (ex: *string* em um, *Date object* em outro).
    - **III - Validação de Esquema:** **CERTO**. O MongoDB oferece capacidade de validar esquemas durante operações de inserção e atualização (embora não seja obrigatório).

### 1.3 Recursos Avançados

- **Consultas *Ad Hoc*:** Permite expressões regulares, recuperação de documentos inteiros, partes de documentos e amostras randômicas.
- **Indexação:** Permite indexação de documentos e de campos específicos para melhorar a *performance* das consultas.
    - **Sintaxe de Criação (AOCP/2020):** `db.collection.createIndex({<fieldname>: (1|-1)})`
    - `1` = Índice Ascendente; `-1` = Índice Descendente.
- **Replicação (Alta Disponibilidade):**
    - Utiliza o modelo **Primário-Secundário** (*Primary-Secondary*).
    - **Primário (*Primary*):** Único nó que recebe **operações de gravação (escrita)**.
    - **Secundário (*Secondary*):** Réplicas que aceitam **operações de leitura**.
    - **Failover:** Se o primário falhar, um secundário assume automaticamente o posto.

## 2. Ferramentas e Utilitários do Ecossistema MongoDB

| FERRAMENTA | FUNÇÃO PRINCIPAL |
| :--- | :--- |
| **Mongosh** | ***Shell*** interativo do MongoDB. Interface de linha de comando para executar consultas e comandos administrativos. |
| **Mongodump** | Utilitário para criar ***backups*** (cópias de segurança) binários do banco de dados. |
| **MongoDB Database Profiler** | Coleta informações detalhadas sobre as operações executadas em uma instância. Usado para **análise de desempenho** e *debugging*. |

## 3. Comandos Essenciais (CRUD e Administração)

### 3.1 Gerenciamento de Bases de Dados

| COMANDO | DESCRIÇÃO |
| :--- | :--- |
| `show dbs` | Lista todos os bancos de dados presentes no servidor. |
| `use [nome-do-banco]` | Seleciona/Cria um banco de dados para uso. |
| `db` | Exibe o nome do banco de dados atualmente em uso. |
| `db.dropDatabase()` | Apaga o banco de dados atualmente selecionado. |

### 3.2 Gerenciamento de Coleções

| COMANDO | DESCRIÇÃO |
| :--- | :--- |
| `show collections` | Lista as coleções do banco de dados atual. |
| `db.createCollection("nome")` | Cria uma nova coleção explicitamente. |
| `db.nome_colecao.drop()` | Apaga uma coleção. |

### 3.3 Manipulação de Documentos (CRUD)

| OPERAÇÃO | COMANDO E EXEMPLO |
| :--- | :--- |
| **Inserir** | `db.posts.insertOne({ title: "Título", category: "News" })` |
| **Consultar** | `db.posts.find({category: "News"})` |
| **Formatar Saída** | `db.posts.find().pretty()` |
| **Contar** | `db.collection.count()` |
| **Valores Distintos** | `db.fornecedores.distinct("pais")` |
| **Atualizar** | `db.minhacolecao.update({‘content’: ‘mongodb’}, {$set:{‘content’: ‘mongodb para concursos’}})` |
| **Remover** | `db.dados.remove({"mail": "james@brown.org"})` |

> ### 3.3.1 Observação sobre Inserção e Flexibilidade (FUNDATEC/2020)
- **Cenário:** Inserção de dois documentos na coleção `cidades`:
    1. `{ id: 1, descricao: "Fortaleza" }`
    2. `{ id: 1, descricao: "Fortaleza", uf: "CE" }`
- **Resultado da consulta `db.cidades.find({})`:**
    - Retornará **DOIS (2) documentos**.
    - O campo `id` não é uma chave primária implícita (a menos que se use `_id` ou se crie um índice único).
    - Documentos na mesma coleção **não precisam** ter os mesmos campos.

## 4. Análise de Questões Específicas (Pegadinhas Recorrentes)

### 4.1 Linguagem de Consulta

- **Mito:** É possível usar SQL como linguagem principal no MongoDB.
- **Realidade (IF SUL/2021):** Utiliza-se a **API nativa do MongoDB** (funções JavaScript como `find()`, `insertOne()`). **Não** se usa SQL padrão para consultas.

### 4.2 Replicação e Escrita (TRT-8/2022)

- **Arquitetura Padrão:**
    - **Aplicação Cliente ->** Conecta para **Escrita** apenas no nó **PRIMARY**.
    - **Aplicação Cliente ->** Pode ser configurada para **Leitura** no **PRIMARY** ou nos **SECONDARY**.
- **Assertiva Correta:** "O PRIMARY é o único membro no conjunto de réplicas que recebe operações de gravação."

### 4.3 Equivalência Estrutural (SERPRO/2021)

- **Afirmativa:** "Uma coleção e um documento, no MongoDB, são equivalentes à tabela e à linha, no Modelo Relacional de Dados."
- **Análise:** **CERTO**. A correspondência exata é:
    - *Database* = Banco de Dados.
    - *Collection* = Tabela.
    - *Document* = Linha/Registro.

## 5. Gabarito das Questões MongoDB

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (IBADE 2019) | **D** | MongoDB é NoSQL. |
| **2** (BFC 2021) | **B** | MongoDB e NoSQL (considerando NoSQL como categoria). |
| **3** (FUNDATEC 2022) | **B** | Orientado a documentos (JSON/XML). |
| **4** (FGV 2017) | **D** | MongoDB usa BSON (JSON-like). |
| **5** (CESPE 2022) | **E** | Documentos não precisam ter os mesmos elementos. |
| **6** (IF SUL 2021) | **B** (I e II) | I (BSON), II (Não há tabelas/chaves). III é falsa (Linha = Documento). |
| **7** (IF SUL 2021) | **D** | Não utiliza SQL como linguagem de consulta. |
| **8** (AOCP 2020) | **A** | `db.collection.createIndex({<fieldname>: (1|-1)})` |
| **9** (FCC 2019) | **A** | `show dbs` (listar) e `mongodump` (backup). |
| **10** (CESPE 2022) | **A** | *Database Profiling* coleta informações de desempenho. |
| **11** (FUNDATEC 2020) | **E** | Dois documentos são mostrados; não há restrição de esquema. |
| **12** (AOCP 2020) | **A** | Projeção é expressa em pares `key:value`. |
| **13** (FGV 2022) | **A** | `db.funcionarios.find({})` retorna todos os documentos. |
| **14** (FGV 2022) | **D** (II e III) | II (tipos diferentes), III (validação possível). I é falsa. |
| **15** (CESPE 2021) | **C** | Coleção = Tabela; Documento = Linha. |
| **16** (FGV 2021) | **C** | `pretty()` formata a saída. |
| **17** (CESPE 2022) | **A** | Apenas o PRIMARY recebe gravação. |
| **18** (AOCP 2020) | **B** | `count()` conta documentos. |
| **19** (CESPE 2022) | **E** | MongoDB não usa tabelas/colunas como estrutura principal. |
| **20** (CESGRANRIO 2021) | **E** | `db.fornecedores.distinct("pais")` retorna valores únicos. |