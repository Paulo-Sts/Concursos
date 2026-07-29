# Evolução e Modelos de Dados

## 1. Evolução dos Bancos de Dados

### 1.1 Linha do Tempo (visão geral)

| PERÍODO/ERA | MODELO/CARACTERÍSTICA | DESCRIÇÃO |
|---|---|---|
| Sistemas de Arquivos | Arquivos isolados | Programas e dados altamente acoplados; redundância não controlada; inconsistência. |
| Modelo Hierárquico | Estrutura em árvore (pai-filho) | Dados organizados hierarquicamente; cada registro filho tem um único pai. |
| Modelo em Rede | Estrutura em grafo | Baseado no modelo CODASYL/DBTG; permite relacionamentos muitos-para-muitos (um filho pode ter vários pais). |
| Modelo Relacional | Tabelas (relações) | Modelo mais utilizado atualmente; baseado em teoria de conjuntos; usa SQL como linguagem padrão. |
| Modelo Orientado a Objetos (OO) | Objetos com estado + comportamento | Surgiu com linguagens OO; permite objetos complexos e herança. |
| Modelo Semântico | Significado dos dados | Evolução para dar mais significado aos dados. |
| BD "Inteligente" | Hipermídia, IA, recuperação ampla | Big Data, NoSQL, aplicações em tempo real. |

> [!CAUTION] Observação:
> - O modelo relacional é o mais utilizado atualmente por ser o mais flexível e adequado para resolver os problemas de projeto e implementação de bases de dados.
> - O NoSQL surgiu como uma alternativa para grandes volumes de dados não estruturados, com maior escalabilidade horizontal.

## 2. Modelo Hierárquico

### 2.1 Características
- Os dados são estruturados em forma de árvore (hierarquia).
- Cada registro é uma coleção de campos; cada campo possui um único valor.
- Estrutura pai-filho: um pai pode ter vários filhos, mas um filho tem um único pai.
- Há um único registro raiz (topo da hierarquia).

### 2.2 Representação

```
        RAIZ (única)
       /    |    \
   Filho1 Filho2 Filho3
    /   \         /   \
 Neto1 Neto2    Neto3 Neto4
```

#### 2.2.1 Regra do Modelo Hierárquico
- Raiz: único nó sem pai.
- Folha: nó sem filhos.
- Um registro raiz não participa como filho em nenhum relacionamento.

## 3. Modelo em Rede

### 3.1 Características
- Baseado no modelo CODASYL/DBTG (Conference on Data Systems Languages / Data Base Task Group).
- Estrutura em grafo (não mais em árvore).
- Permite que um registro filho tenha vários pais (relacionamentos muitos-para-muitos).
- Usado principalmente em sistemas de grande porte.

### 3.2 Representação

```
    PaiA    PaiB    PaiC
      \      |      /
       \     |     /
        FilhoX (com vários pais)
```

#### 3.2.1 Diferença Fundamental
- Hierárquico: filho tem UM pai (estrutura rígida).
- Rede: filho pode ter VÁRIOS pais (mais flexível).

## 4. Modelo Relacional

### 4.1 Características
- Representa o banco de dados como uma coleção de relações (tabelas).
- Baseado em teoria de conjuntos (operações de união, interseção, etc.).
- Utiliza SQL (Structured Query Language) como linguagem padrão de comunicação.
- É o modelo mais utilizado atualmente por sua flexibilidade e adequação aos problemas de projeto e implementação.

Exemplo: (Relação Médico x Especialidade)

Tabela MÉDICO:

| CRM_MÉDICO | NOME_MÉDICO | COD_ESPECIALIDADE |
|---|---|---|
| 101-1 | JOHN | 001 |
| 102-2 | MARIA | 001 |
| 103-3 | JOSH | 002 |

Tabela ESPECIALIDADE:

| COD_ESPECIALIDADE | DESC_ESPECIALIDADE |
|---|---|
| 001 | ORTOPEDIA |
| 002 | ANESTESIA |

#### 4.2.1 Terminologia (modelo relacional)
- Relação ↔ Tabela
- Tupla ↔ Linha (registro)
- Atributo ↔ Coluna (campo)

## 5. Modelo Orientado a Objetos (OO)

### 5.1 Características
- Surgiu em decorrência das linguagens de programação orientadas a objetos e dos limites do modelo relacional para representar objetos complexos.
- Toda entidade do mundo real é representada por um objeto.
- Um objeto possui:
  - Estado (propriedades/atributos).
  - Comportamento (operações/métodos).

#### 5.1.1 Encapsulamento
- O usuário interage com os métodos do objeto (ex.: acelerar, frear) sem precisar conhecer os detalhes internos (ex.: funcionamento do motor).
- O modelo de dados é a descrição formal da estrutura do BD: tipos de dados, relacionamentos e restrições.

### 5.2 Objetos complexos
- Um objeto pode conter outros objetos como atributos.
- Suporta herança (reuso de estruturas e comportamentos).

Exemplo (definição de tipo no modelo OO):

```sql
define type FUNCIONARIO tuple (
    nome: string,
    cpf: string,
    datanasc: Data,
    endereco: string,
    sexo: char,
    salario: float,
    supervisor: FUNCIONARIO,   -- objeto complexo (outro funcionário)
    dept: DEPARTAMENTO         -- objeto complexo
);
```

#### 5.2.1 Observação
- `supervisor` é do tipo `FUNCIONARIO` (objeto dentro de objeto).
- `dept` é do tipo `DEPARTAMENTO` (outro objeto complexo).

## 6. NoSQL (Not Only SQL)

### 6.1 Características
- Conjunto de abordagens para armazenamento que não seguem o modelo relacional tradicional.
- Permite maior escalabilidade horizontal e flexibilidade para lidar com grandes volumes de dados não estruturados.
- Não requer esquemas fixos (schema-less), ideal para aplicações dinâmicas e distribuídas.

### 6.2 Classificação (principais modelos NoSQL)

| TIPO        | DESCRIÇÃO                                      | EXEMPLOS         |
|-------------|------------------------------------------------|------------------|
| Documentos  | Dados armazenados como documentos (JSON, BSON) | MongoDB, CouchDB |
| Chave-Valor | Armazenamento simples de pares chave-valor     | Redis, DynamoDB  |
| Colunas     | Dados organizados por colunas, não por linhas  | Cassandra, HBase |
| Grafos      | Ênfase em relacionamentos entre entidades      | Neo4j, OrientDB  |

### 6.3 Aplicações típicas
- Big Data.
- IoT (Internet das Coisas).
- Redes sociais.
- Aplicações em tempo real.
