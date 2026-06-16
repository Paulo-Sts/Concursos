# Anotações – Banco de Dados – Evolução e Modelos de Dados

## 1. Evolução dos Bancos de Dados

### 1.1 Linha do tempo (visão geral)

| PERÍODO/ERA | MODELO/CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- | --- |
| **Sistemas de Arquivos** | Arquivos isolados | Programas e dados altamente acoplados; redundância não controlada; inconsistência. |
| **Modelo Hierárquico** | Estrutura em árvore (pai-filho) | Dados organizados hierarquicamente; cada registro filho tem um único pai. |
| **Modelo em Rede** | Estrutura em grafo | Baseado no modelo CODASYL/DBTG; permite relacionamentos muitos-para-muitos (um filho pode ter vários pais). |
| **Modelo Relacional** | Tabelas (relações) | Modelo mais utilizado atualmente; baseado em teoria de conjuntos; usa SQL como linguagem padrão. |
| **Modelo Orientado a Objetos (OO)** | Objetos com estado + comportamento | Surgiu com linguagens OO; permite objetos complexos e herança. |
| **Modelo Semântico** | Significado dos dados | Evolução para dar mais significado aos dados. |
| **BD "Inteligente"** | Hipermídia, IA, recuperação ampla | Big Data, NoSQL, aplicações em tempo real. |

> ### 1.1.1 Observação
> - O modelo **relacional** é o mais utilizado atualmente por ser o mais flexível e adequado para resolver os problemas de projeto e implementação de bases de dados.
> - O **NoSQL** surgiu como uma alternativa para grandes volumes de dados não estruturados, com maior escalabilidade horizontal.

## 2. Modelo Hierárquico

### 2.1 Características

- Os dados são estruturados em **forma de árvore** (hierarquia).
- Cada registro é uma coleção de **campos**; cada campo possui um **único valor**.
- Estrutura pai-filho: **um pai pode ter vários filhos**, mas **um filho tem um único pai**.
- Há **um único registro raiz** (topo da hierarquia).

### 2.2 Representação

```
        RAIZ (única)
       /    |    \
   Filho1 Filho2 Filho3
    /   \         /   \
 Neto1 Neto2    Neto3 Neto4
```

> ### 2.2.1 Regra do modelo hierárquico
> - **Raiz:** único nó sem pai.
> - **Folha:** nó sem filhos.
> - Um registro **raiz não participa como filho** em nenhum relacionamento.

## 3. Modelo em Rede

### 3.1 Características

- Baseado no modelo **CODASYL/DBTG** (Conference on Data Systems Languages / Data Base Task Group).
- Estrutura em **grafo** (não mais em árvore).
- Permite que um registro filho tenha **vários pais** (relacionamentos muitos-para-muitos).
- Usado principalmente em **sistemas de grande porte**.

### 3.2 Representação conceitual

```
    PaiA    PaiB    PaiC
      \      |      /
       \     |     /
        FilhoX (com vários pais)
```

> ### 3.2.1 Diferença fundamental
> - **Hierárquico:** filho tem UM pai (estrutura rígida).
> - **Rede:** filho pode ter VÁRIOS pais (mais flexível).

## 4. Modelo Relacional

### 4.1 Características

- Representa o banco de dados como uma **coleção de relações** (tabelas).
- Baseado em **teoria de conjuntos** (operações de união, interseção, etc.).
- Utiliza **SQL** (Structured Query Language) como linguagem padrão de comunicação.
- É o modelo mais utilizado atualmente por sua **flexibilidade** e **adequação** aos problemas de projeto e implementação.

### 4.2 Exemplo (Relação Médico x Especialidade)

**Tabela MÉDICO:**

| CRM_MÉDICO | NOME_MÉDICO | COD_ESPECIALIDADE |
| --- | --- | --- |
| 101-1 | JOHN | 001 |
| 102-2 | MARIA | 001 |
| 103-3 | JOSH | 002 |

**Tabela ESPECIALIDADE:**

| COD_ESPECIALIDADE | DESC_ESPECIALIDADE |
| --- | --- |
| 001 | ORTOPEDIA |
| 002 | ANESTESIA |

> ### 4.2.1 Terminologia (modelo relacional)
> - **Relação** ↔ Tabela
> - **Tupla** ↔ Linha (registro)
> - **Atributo** ↔ Coluna (campo)

## 5. Modelo Orientado a Objetos (OO)

### 5.1 Características

- Surgiu em decorrência das linguagens de programação orientadas a objetos e dos limites do modelo relacional para representar **objetos complexos**.
- Toda entidade do mundo real é representada por um **objeto**.
- Um objeto possui:
  - **Estado** (propriedades/atributos).
  - **Comportamento** (operações/métodos).

> ### 5.1.1 Encapsulamento
> - O usuário interage com os **métodos** do objeto (ex.: acelerar, frear) sem precisar conhecer os detalhes internos (ex.: funcionamento do motor).
> - O modelo de dados é a descrição formal da estrutura do BD: tipos de dados, relacionamentos e restrições.

### 5.2 Objetos complexos

- Um objeto pode conter **outros objetos** como atributos.
- Suporta **herança** (reuso de estruturas e comportamentos).

**Exemplo (definição de tipo no modelo OO):**

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

> ### 5.2.1 Observação
> - `supervisor` é do tipo `FUNCIONARIO` (objeto dentro de objeto).
> - `dept` é do tipo `DEPARTAMENTO` (outro objeto complexo).

## 6. NoSQL (Not Only SQL)

### 6.1 Características

- Conjunto de abordagens para armazenamento que **não seguem o modelo relacional** tradicional.
- Permite **maior escalabilidade horizontal** e **flexibilidade** para lidar com grandes volumes de dados **não estruturados**.
- **Não requer esquemas fixos** (schema-less), ideal para aplicações dinâmicas e distribuídas.

### 6.2 Classificação (principais modelos NoSQL)

| TIPO | DESCRIÇÃO | EXEMPLOS |
| --- | --- | --- |
| **Documentos** | Dados armazenados como documentos (JSON, BSON) | MongoDB, CouchDB |
| **Chave-Valor** | Armazenamento simples de pares chave-valor | Redis, DynamoDB |
| **Colunas** | Dados organizados por colunas, não por linhas | Cassandra, HBase |
| **Grafos** | Ênfase em relacionamentos entre entidades | Neo4j, OrientDB |

### 6.3 Aplicações típicas

- Big Data.
- IoT (Internet das Coisas).
- Redes sociais.
- Aplicações em tempo real.

## 7. Questões de Concurso Comentadas

### 7.1 (VUNESP/2019/CÂMARA DE PIRACICABA – Administrador de Rede)

**Item sobre modelo hierárquico:** "é correto afirmar que:"

- a) Incorreto: um registro pode ser pai de **vários** filhos.
- b) Incorreto: um registro pai pode ter **inúmeros** filhos.
- c) Incorreto: a raiz pode ter **vários** filhos.
- d) **Correto:** a raiz **não participa como filho** em nenhum relacionamento.
- e) Incorreto: campos podem ter diversos tipos.

**Gabarito: d) um registro do tipo raiz não participa como registro filho em qualquer relacionamento.**

### 7.2 (IBFC/2019/EMDEC – Analista de TI Jr.)

**Item:** "Oracle, PostgreSQL, MySQL, Firebird e SQLServer são todos considerados, tecnicamente, como sendo um modelo de dados _____."

**Gabarito: d) Relacional**.

### 7.3 (CESPE/2019/MPC-PA – Analista Ministerial)

**Item:** "modelo de dados caracterizado por organizar os dados em uma estrutura do tipo árvore, na qual cada registro tem um único 'pai' e é classificado em uma ordem específica."

**Gabarito: d) hierárquico**.

### 7.4 (VUNESP/2023/DPE-SP – Agente de Defensoria)

**Item:** "em um modelo hierárquico, há um único registro do tipo raiz."

**Gabarito: a) há um único registro do tipo raiz.**

### 7.5 (FUNDATEC/2025/PREFEITURA DE TANGARÁ DA SERRA – Técnico)

**Item correto:** "O modelo hierárquico organiza dados em árvores de registros."

**Gabarito: d)**.

### 7.6 (IBADE/2024/PREFEITURA DE JARU – Analista de Sistemas)

**Item:** "Qual tipo de banco de dados seria mais adequado para grandes volumes de dados, com desempenho otimizado e escalabilidade?"

**Gabarito: b) Banco de Dados NoSQL**.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (VUNESP/2019) | d |
| 02 (IBFC/2019) | d |
| 03 (CESPE/2019) | d |
| 04 (VUNESP/2023) | a |
| 05 (FUNDATEC/2025) | d |
| 06 (IBADE/2024) | b |

---

## Síntese para Revisão Rápida

| MODELO | ESTRUTURA | RELACIONAMENTO | EXEMPLO DE SGBD |
| --- | --- | --- | --- |
| **Hierárquico** | Árvore | Um pai → vários filhos; filho → um pai | IMS (IBM) |
| **Rede** | Grafo | Um filho pode ter vários pais (muitos-para-muitos) | Modelo CODASYL/DBTG |
| **Relacional** | Tabelas (relações) | Chaves primárias e estrangeiras | Oracle, PostgreSQL, MySQL, SQL Server |
| **Orientado a Objetos** | Objetos (estado + comportamento) | Herança, objetos complexos | ObjectDB, db4o |
| **NoSQL** | Documentos, chave-valor, colunas, grafos | Schema-less, escalabilidade horizontal | MongoDB, Redis, Cassandra, Neo4j |

---

*Material baseado na aula do professor Washington Henrique Almeida (Gran Concursos).*