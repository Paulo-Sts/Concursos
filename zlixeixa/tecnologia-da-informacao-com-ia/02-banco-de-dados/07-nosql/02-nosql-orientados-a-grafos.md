# NoSQL Orientados a Grafos

## 1. Conceitos Fundamentais de Grafos

### 1.1 Estrutura de um Grafo
- Grafo é uma estrutura computacional formada por nós e arestas.
- Nós representam pontos do gráfico que contêm alguma informação.
- Arestas são ligações entre os nós.
- Exemplo prático: em redes sociais, João e Maria são nós; a amizade entre eles é uma aresta.

### 1.2 Utilização de Grafos
- Mapas: pontos de interesse são nós; vias são arestas com distâncias associadas.
- Redes sociais: representação de vínculos entre usuários.
- Detecção de fraudes: montagem de "aranhas" com informações interligadas.
- Logística: cálculo de distâncias entre cidades.

### 1.3 Armazenamento em Bancos Relacionais vs NoSQL
- Em bancos relacionais, seria necessário criar tabelas separadas para nós e arestas com chaves primárias.
- Modelo relacional torna difícil representar a simplicidade de nós e arestas.
- Bancos NoSQL orientados a grafos são especificamente construídos para trabalhar com nós, arestas e grafos.

> [!TIP] DICAS:
> - A analogia do mapa ajuda a entender o conceito: pontos de interesse (nós) conectados por vias (arestas);
> - Lembre-se que cada aresta pode ter propriedades, como distância no exemplo do mapa.

> [!CAUTION] OBSERVAÇÃO:
> - A principal vantagem do banco de dados orientado a grafos é sua capacidade nativa de lidar com relacionamentos complexos, eliminando a necessidade de JOINs.

## 2. Modelo Orientado a Grafos

### 2.1 Características Principais
- Armazenam, mapeiam e procuram relacionamentos entre nós por meio de arestas.
- Nós são elementos de dados.
- Arestas são relacionamentos.

### 2.2 Casos de Uso
- Dados de redes sociais.
- Detecção de fraudes.
- Logística.

### 2.3 Exemplo Prático
- Zoumana gosta de correr no parque.
- O parque está localizado na Universidade do Texas, onde Zoumana estuda.
- Este cenário pode ser representado como: Zoumana ⟶ gosta ⟶ Parque ⟶ localizado em ⟶ Universidade do Texas ⟶ estuda ⟶ Zoumana.

### 2.4 Sistema Macros
- Sistema da CGU (Controladoria-Geral da União).
- Construía uma rede de relacionamento entre pessoas.
- Utilizado para detecção de fraudes e ilegalidades envolvendo pessoas e empresas.

## 3. Linguagens de Consulta para Grafos

### 3.1 Gremlin
- Linguagem específica para percorrer grafos.
- Realiza consulta, análise e manipulação de gráficos.
- Projeto de código aberto mantido pela TinkerPop.
- Segue o padrão Blueprints para grafos de propriedades.

> [!TIP] DICAS:
> - Gremlin é como uma linguagem de navegação para grafos: você "anda" pelos nós seguindo as arestas;
> - O padrão Blueprints do Gremlin permite que a mesma consulta funcione em diferentes bancos de grafos.

## 4. Neo4j

### 4.1 Características Gerais
- Banco de dados open-source baseado em grafos.
- Respeita ACID (Atomicidade, Consistência, Isolamento, Durabilidade).
- Utiliza Cypher Query Language como linguagem de consulta.

### 4.2 Componentes do Neo4j
- Labels: nome/nomenclatura do nó.
- Propriedades: atributos que definem cada nó.
- Nós: elementos de dados.
- Relacionamentos: conexões entre os diversos nós.

### 4.3 Exemplo de Estrutura
- Nó do tipo ator: propriedades como nome e ano de nascimento.
- Nó do tipo filme: propriedades como título e data de lançamento.
- Relacionamentos entre atores e filmes montam o grafo.

### 4.4 Cypher Query Language
- Linguagem de programação para realizar operações em grafos.
- Permite declarar o que se deseja selecionar, inserir, atualizar ou excluir.
- Possui palavras básicas para operações específicas.

> [!TIP] DICAS:
> - Neo4j é o banco de grafos mais cobrado em concursos;
> - A sintaxe do Cypher é visual e intuitiva: (nó) - [RELACIONAMENTO] -> (outro nó);
> - A consulta MATCH (diretor-dirigiu) - Forrest Gump retorna quem dirigiu o filme.

### 4.5 Principais Cláusulas Cypher

#### 4.5.1 MATCH
- Faz pesquisa e retorna nós e relacionamentos.
- Segue o padrão: (um nó) - [relacionado] -> (com outro nó).
- Permite especificar os padrões que o Neo4j irá procurar.
- Pode ser combinada com WHERE para definir critérios específicos.

#### 4.5.2 CREATE
- Cria nós e relacionamentos.

#### 4.5.3 SET
- Muda as propriedades existentes.

#### 4.5.4 RETURN
- Retorna as consultas feitas com o MATCH.

#### 4.5.5 DELETE
- Apaga nós e relacionamentos.

#### 4.5.6 DETACH DELETE
- Apaga um nó e seus relacionamentos simultaneamente.

#### 4.5.7 REMOVE
- Remove propriedades específicas.

> [!CAUTION] OBSERVAÇÃO:
> - DETACH DELETE é diferente de DELETE: o primeiro remove o nó e todas as suas conexões de uma vez;
> - DELETE isolado só remove o nó se ele não tiver relacionamentos, exigindo antes a remoção das arestas.

## 5. Exemplos de Consultas Cypher

### 5.1 Criação de Nós
```
CREATE (ul:Usuário {Nome: "Usuário 1", Id: 1})
CREATE (u2:Usuário {Nome: "Usuário 2", Id: 2})
CREATE (ml:ModuloSistema {Nome: "Compras"})
CREATE (m2:ModuloSistema {Nome: "Financeiro"})
```

### 5.2 Criação de Relacionamentos
```
CREATE (ul)-[r1:PossuíAcesso {NívelAcesso: "escrita"}]->(ml)
CREATE (ul)-[r2:PossuíAcesso {NívelAcesso: "leitura"}]->(ml)
CREATE (u2)-[r3:PossuíAcesso {NívelAcesso: "administrador"}]->(ml)
CREATE (u2)-[r4:PossuíAcesso {NívelAcesso: "escrita"}]->(m2)
```

### 5.3 Consulta de Dados
```
MATCH (u:Usuário), (m:ModuloSistema) RETURN *
```

### 5.4 Consulta com Relacionamento
```
MATCH (a:Estado), (b:Municipio)
WHERE a.ibge = b.uf
CREATE (a)<-[r:pertence]- (b)
RETURN r, b.nome, a.nome
```

> [!TIP] DICAS:
> - O MATCH retorna todos os padrões encontrados no banco;
> - A consulta RETURN * retorna tudo que foi encontrado no MATCH;
> - Neo4j apresenta resultados em formato gráfico ou tabela.

> [!CAUTION] OBSERVAÇÃO:
> - Banco de dados relacional = tabelas com linhas e colunas, não confundir com grafos;
> - Grafos são a estrutura nativa para redes sociais e relacionamentos complexos.