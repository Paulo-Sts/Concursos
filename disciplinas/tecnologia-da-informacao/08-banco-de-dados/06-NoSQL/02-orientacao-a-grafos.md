# Anotações

# NoSQL ORIENTADO A GRAFOS

## 1. Fundamentos do Modelo de Grafos

### 1.1 Estrutura e Conceitos Básicos

- **Grafo:** Estrutura de dados formada por **nós** (vértices) e **arestas** (arcos/relacionamentos).
- **Nós:** Representam elementos de dados ou entidades (Ex: "João", "Maria", "Parque", "Universidade").
- **Arestas:** Representam os **relacionamentos** entre os nós (Ex: "é amigo de", "estuda em", "gosta de").
- **Aplicação Analógica:** Muito utilizado em softwares de **mapas e logística**.
    - Nós = Pontos de interesse (cidades).
    - Arestas = Vias de ligação (distâncias).

> ### 1.1.1 Diferencial em Relação ao Modelo Relacional
- **Problema do SQL:** Representar grafos em tabelas relacionais exige a criação de tabelas artificiais para nós e arestas, utilizando chaves primárias e estrangeiras, o que dificulta a modelagem e a *performance* de consultas complexas de relacionamento.
- **Solução NoSQL:** Bancos de dados construídos especificamente para **armazenar, mapear e procurar relacionamentos** entre nós por meio de arestas de forma nativa.

### 1.2 Casos de Uso Específicos

- **Dados de Redes Sociais:** Representação de vínculos e conexões entre usuários.
- **Detecção de Fraudes:** Construção de redes de relacionamento entre pessoas e empresas (Ex: Sistema *Macros* da CGU) para identificar ilegalidades e formações de "aranhas" (grafos de inteligência).
- **Logística:** Cálculo de rotas e distâncias entre pontos.

### 1.3 Linguagem de Consulta: Gremlin

- **Definição:** Linguagem específica de domínio para **percorrer grafos**.
- **Funcionalidade:** Realiza consulta, análise e manipulação de gráficos.
- **Padrão:** Projeto de código aberto mantido pela **Apache TinkerPop**.
- **Observação (AOCP/2021):** A linguagem Gremlin pode percorrer bancos de dados de grafos que implementem o padrão ***Blueprints***.

## 2. Neo4j (O Principal SGBD de Grafos)

### 2.1 Características Gerais

- **Classificação:** Base de dados ***open-source*** baseada em grafos.
- **Diferencial (Propriedades):** **Respeita ACID** (Atomicidade, Consistência, Isolamento, Durabilidade) — diferentemente da maioria dos bancos NoSQL que seguem o modelo BASE.
- **Linguagem Nativa:** Utiliza a ***Cypher Query Language***.

### 2.2 Componentes Estruturais no Neo4j

- **Labels:** Rótulos que definem o tipo do nó (Ex: `:Ator`, `:Filme`).
- **Propriedades:** Atributos que definem as características de um nó ou relacionamento (Ex: `{nome: "Tom Hanks", anoNascimento: 1956}`).
- **Nós:** Instâncias das *Labels* com suas *Propriedades*.
- **Relacionamentos:** Conexões direcionadas entre os nós, que também podem conter propriedades.

### 2.3 Cypher Query Language (Principais Comandos)

| COMANDO | FUNÇÃO | SINTAXE/PADRÃO |
| :--- | :--- | :--- |
| **CREATE** | Cria nós e relacionamentos. | `CREATE (var:Label {prop: valor})` |
| **MATCH** | Pesquisa e retorna nós e relacionamentos. | `MATCH (a)-[r]->(b) WHERE ... RETURN ...` |
| **SET** | Altera propriedades de um nó ou relacionamento existente. | `MATCH ... SET ...` |
| **RETURN** | Retorna os resultados da consulta (em formato gráfico ou tabular). | `RETURN n.nome, r` |
| **DELETE** | Apaga nós e relacionamentos. | `MATCH ... DELETE ...` |
| **DETACH DELETE** | Apaga um nó e **todos os seus relacionamentos** associados. | `MATCH (n) DETACH DELETE n` |
| **REMOVE** | Remove propriedades específicas de um nó. | `MATCH ... REMOVE ...` |

> ### 2.3.1 Detalhamento do Comando MATCH
- **Padrão de Navegação:** Utiliza a notação ASCII-art para representar o grafo.
    - `(Nó de Origem) - [Relacionamento] -> (Nó de Destino)`
    - Exemplo: `MATCH (diretor)-[:DIRIGIU]->(filme {titulo: 'Forrest Gump'}) RETURN diretor.nome`
- **Função:** A cláusula `MATCH` permite especificar os padrões que o Neo4j irá procurar no banco de dados (Cespe/2022).

### 2.4 Exemplo Prático Analisado (Modelagem de Acessos)

- **Criação de Nós:**
    - `CREATE (u1:Usuario {Nome: "Usuário 1", Id: 1})`
    - `CREATE (m1:ModuloSistema {Nome: "Compras"})`
- **Criação de Relacionamentos (Arestas) com Propriedades:**
    - `CREATE (u1)-[r1:PossuiAcesso {NivelAcesso: "escrita"}]->(m1)`
    - `CREATE (u2)-[r3:PossuiAcesso {NivelAcesso: "administrador"}]->(m1)`
- **Consulta:**
    - `MATCH (u:Usuario), (m:ModuloSistema) RETURN *`
    - **Resultado:** O Neo4j retorna uma **representação gráfica** ou uma **tabela** com os nós e relacionamentos encontrados.

## 3. Análise de Questões de Concurso (Revisão por Assertiva)

### 3.1 Caracterização do Tipo de Banco (FGV/IBGE 2017)

- **Situação:** Ilustração de relações entre colegas e interesses.
- **Conclusão:** O tipo de banco NoSQL que utiliza estruturas de **vértices e arestas** é o **Grafo**.

### 3.2 Erro Comum: Par Chave-Valor (Cespe/FUNPRESP 2016)

- **Afirmativa:** "Em um banco NoSQL do tipo grafo, cada arco é definido por um identificador único e expresso como um par Chave-Valor."
- **Análise:** **ERRADO**. Embora um relacionamento tenha um identificador, a estrutura de um grafo é baseada em **Nós e Arestas** com propriedades, não no modelo estrito de *Chave-Valor* (que é outro tipo de NoSQL, como Redis).

### 3.3 Erro Comum: Representação Tabular (Cespe/Petrobras 2022)

- **Afirmativa:** "Em um banco de dados gráfico, um objeto do mundo real é representado como uma tabela..."
- **Análise:** **ERRADO**. A descrição é a de um **banco de dados relacional** (tabela, linha, chave primária numérica). No modelo de grafos, o objeto é um **Nó**.

### 3.4 Interpretação de Código Cypher (Cespe/CEBRASPE 2022)

- **Cenário:** Criação de Estados e Municípios, relacionamento `[:pertence]`.
- **Retorno:** O resultado de uma consulta `MATCH... RETURN` no Neo4j pode ser exibido como **tabela** ou **grafo**.
- **Observação do Professor:** A sintaxe exata deve ser observada; a figura do material de apoio mostrou uma tabela com a coluna de relacionamento (`r`), confirmando que a saída não é apenas gráfica.

### 3.5 Questão Discursiva/Interpretação (Cespe/ANP 2022)

- **Afirmativa:** "A cláusula MATCH permite especificar os padrões que o Neo4j irá procurar no banco de dados."
- **Análise:** **CERTO**. É a definição funcional do comando de consulta.

## 4. Gabarito das Questões de Grafos

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (FGV 2017) | **C** (Grafo) | Vértices e arestas definem o modelo de grafos. |
| **2** (Cespe 2016) | **E** | Arco não é definido estritamente como par Chave-Valor. |
| **3** (AOCP 2021) | **C** | Gremlin é linguagem para percorrer grafos (padrão Blueprints). |
| **4** (Cespe 2022) | **E** | Objeto do mundo real = Nó (não tabela/linha). |
| **5** (Cesgranrio 2021) | **D** (Graph Oriented) | Estrutura de vértices (O) e arestas (R). |
| **6** (Cebraspe 2022) | **E** | O resultado do código não corresponde exatamente à figura proposta no comando. |
| **7** (Cespe 2022) | **E** | Questão de interpretação de consulta Cypher. |
| **8** (Cespe 2021) | **C** | Cypher permite declarar seleção, inserção, atualização e exclusão. |
| **9** (Cespe 2022) | **C** | MATCH especifica os padrões de busca. |