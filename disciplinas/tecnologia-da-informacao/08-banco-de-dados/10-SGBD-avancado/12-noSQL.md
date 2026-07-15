# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - NOSQL

## 1. NOSQL - CONCEITOS FUNDAMENTAIS

- **NoSQL** ("não SQL" ou "não relacional", posteriormente estendido para ***Not Only SQL* / Não Somente SQL**) é um termo genérico que representa os bancos de dados **não relacionais**.

- É um movimento que promove soluções de armazenamento de dados não relacionais.

- O NoSQL passou a atuar nas áreas em que os **modelos relacionais não são eficientes**.

### 1.1 Aplicações do NoSQL

O NoSQL é composto por diversas ferramentas que buscam resolver problemas como:

| Problema | Descrição |
|----------|-----------|
| **Grandes volumes de dados** | Muito usado em soluções de *big data*. |
| **Baixa latência** | Consultas que precisam retornar o dado rapidamente. |
| **Modelos flexíveis** | Armazenamento de dados semiestruturados, como documentos JSON. |

> ### 1.2 NoSQL x SQL
> - As tecnologias NoSQL **não têm como objetivo substituir** os bancos de dados relacionais, mas apenas propor soluções que em determinados cenários são mais adequadas.
> - É possível trabalhar com tecnologias NoSQL e bancos de dados relacionais dentro de uma **mesma aplicação**.
> - **RDBMS:** esquema explícito — permite ver a estrutura do dado sem ver o dado.
> - **NoSQL:** esquema implícito.

### 1.3 Onde Utilizar NoSQL?

- Em cenários nos quais os sistemas de banco de dados tradicionais **não são suficientes ou adequados** às necessidades específicas:
  - Baixa latência.
  - Grandes volumes de dados.
  - Escalabilidade.
  - Estruturas em que as **conexões entre os dados são tão importantes quanto o próprio dado**.

## 2. TIPOS DE BANCOS NOSQL

### 2.1 Chave-Valor (*Key-Value*)

- Armazena dados como um conjunto de **pares de chave-valor**.
- Uma chave funciona como um **identificador exclusivo**.
- A chave e os valores podem ser qualquer coisa, desde objetos simples até objetos compostos complexos.
- São **altamente particionáveis** e permitem **escalabilidade horizontal** que outros tipos de bancos não conseguem alcançar.

**Exemplos:** Redis, DynamoDB (AWS).

### 2.2 Documento (*Document Store*)

- Projetado para armazenar, recuperar e gerenciar **informações orientadas a documentos** (dados semiestruturados).
- É uma subclasse do armazenamento chave-valor.
- A diferença está na maneira como os dados são processados:
  - **Chave-valor:** dados são opacos ao banco.
  - **Documento:** sistema depende da estrutura interna do documento para extrair metadados e otimizações.

- Muitas soluções utilizam o padrão **JSON** para armazenamento.

**Exemplos:** MongoDB, DynamoDB, DocumentDB (Azure).

> ### 2.3 MongoDB - Analogia com Modelo Relacional
> - **Documento** → Registro (linha).
> - **Collection (coleção)** → Tabela.
> - **Índices** → os mesmos.
> - **Embedding e Linking** → JOIN.

### 2.4 Coluna (*Column Family* / Wide Column)

- Enquanto um banco relacional é otimizado para armazenar **linhas** (aplicativos transacionais), um banco colunar é otimizado para recuperação rápida de **colunas** (aplicativos analíticos).

- O armazenamento orientado a colunas reduz expressivamente os requisitos gerais de **entrada e saída de disco**.

**Exemplos:** Cassandra, HBase.

### 2.5 Grafo (*Graph*)

- Similar aos bancos de documentos, mas adiciona outra camada: o **relacionamento**.
- Permite ligar documentos para **acesso rápido**.
- Principais casos de uso:
  - Motores de recomendação.
  - Análise de rotas geográficas.
  - Redes sociais.

**Exemplos:** Neo4j.

### 2.6 Memória (*In-Memory*)

- Aplicativos que exigem tempos de resposta em **microssegundos**.
- Exemplos: placares de líderes (jogos), armazenamento de sessões, análises em tempo real.

**Exemplo:** Redis.

### 2.7 Pesquisa (*Search Engine*)

- Construídos para fornecer **visualizações e análises quase em tempo real** de dados gerados por máquina.
- Indexação, agregação e pesquisa de registros semiestruturados.
- Mecanismo de pesquisa de alta performance para **pesquisa de texto completo**.

## 3. BANCOS CLÁSSICOS DO MERCADO

| Banco | Modelo | Característica |
|-------|--------|----------------|
| **Redis** | Chave-Valor | Utiliza memória para alocação de dados. Ideal para **Cache**. |
| **MongoDB** | Documentos | Variação do chave-valor. Foco em grandes volumes. Ideal para aplicações web. **(Mais cobrado em provas)** . |
| **Neo4j** | Grafos | Ferramenta NoSQL mais madura. Usado em motores de recomendação e redes sociais. |
| **Cassandra** | Coluna / Chave-Valor | Implementação open source do BigTable com arquitetura distribuída do Dynamo. |

> ### 3.1 Observação sobre Classificações
> - As classificações podem variar conforme a fonte.
> - O Cassandra, por exemplo, pode ser classificado como chave-valor em algumas referências e como família de colunas em outras.
> - As bancas examinadoras costumam cobrar apenas: **chave-valor**, **documento** e **grafo**.

## 4. ESCALABILIDADE

| Tipo | Descrição | Uso |
|------|-----------|-----|
| **Vertical (*Scale Up*)** | Adicionar recursos em um **único nó** do sistema (mais memória, processador). | RDBMS é bom em escalabilidade vertical. |
| **Horizontal (*Scale Out*)** | Adicionar **mais nós** ao sistema. | NoSQL é bom em escalabilidade horizontal. |

## 5. ARQUITETURA E PROPRIEDADES

### 5.1 ACID x BASE

| Propriedade | ACID (Relacional) | BASE (NoSQL) |
|-------------|-------------------|--------------|
| Consistência | Forte | Fraca |
| Isolamento | Foco em isolamento | Foco em disponibilidade |
| Commit | Concentra-se em commit | Melhor esforço |
| Transações | Transações aninhadas | Respostas aproximadas |
| Disponibilidade | Conservador (pessimista) | Agressivo (otimista) |
| Evolução | Difícil | Mais fácil |

**BASE significa:**

| Letra | Significado | Descrição |
|-------|-------------|-----------|
| **BA** | *Basically Available* | Disponibilidade é prioridade. |
| **S** | *Soft State* | Não precisa ser consistente o tempo todo. |
| **E** | *Eventually Consistent* | Consistente em momento indeterminado. |

> ### 5.2 Comparação
> - O banco relacional é bom nas características **ACID**.
> - O NoSQL é bom nas propriedades **BASE**.
> - RDBMS = forte consistência, foco em isolamento, transações aninhadas.
> - NoSQL = disponibilidade, respostas aproximadas, evolução mais fácil.

## 6. TEOREMA DE CAP

O Teorema de CAP afirma que em um sistema distribuído é **impossível garantir simultaneamente as três propriedades**:

| Propriedade | Descrição |
|-------------|-----------|
| **Consistency (Consistência)** | Uma vez escrito o registro, este fica disponível para ser utilizado imediatamente. Ex.: MongoDB é bom em consistência. |
| **Availability (Disponibilidade)** | Sistema permanece ativo durante um determinado período. Tolerante a falhas de software e hardware. |
| **Partition Tolerance (Tolerância ao Particionamento)** | Capacidade de um sistema continuar operando mesmo depois de uma falha na rede. |

> ### 6.1 Regra do Teorema de CAP
> - Um sistema distribuído pode garantir **no máximo duas** das três propriedades.
> - **CA:** Consistência + Disponibilidade (sacrifica tolerância a particionamento).
> - **CP:** Consistência + Tolerância a Particionamento (sacrifica disponibilidade).
> - **AP:** Disponibilidade + Tolerância a Particionamento (sacrifica consistência).

## 7. QUESTÕES COMENTADAS

### Questão 01 (CCV-UFC/2019)

**Análise das alternativas:**

| Alternativa | Análise |
|-------------|---------|
| a) Não podem ser indexados | ❌ NoSQL **podem** ser indexados. |
| b) São relacionais | ❌ NoSQL são **não relacionais**. |
| c) Esquema fixo | ❌ NoSQL não exige esquema fixo (esquema implícito). |
| d) Firebird, SQLite, Access | ❌ Estes são relacionais, não NoSQL. |
| e) Diversos modelos | ✅ Documento, grafo, chave-valor, memória, pesquisa. |

**Gabarito: e**

### Questão 02 (CESPE/TJ-SE/2014)

**Afirmação:** "Bancos NoSQL orientados a documentos são apropriados para o armazenamento de dados semiestruturados."

**Análise:** Correto. Documentos (ex.: JSON) têm estrutura flexível, sem colunas predefinidas.

**Gabarito: C**

### Questão 03 (CESGRANRIO/BB/2018)

**Análise das alternativas:**

| Alternativa | Análise |
|-------------|---------|
| a) Não utilização de SQL | ❌ NoSQL = *Not Only SQL* (não somente SQL). |
| b) Renúncia ao BASE | ❌ NoSQL é baseado em BASE. |
| c) Aumento de escalabilidade e desempenho | ✅ Correto. |
| d) Facilidade de normalização | ❌ Normalização não é foco do NoSQL. |
| e) Implementação simultânea das três propriedades do CAP | ❌ É impossível garantir as três simultaneamente. |

**Gabarito: c**

### Questão 04 (CEBRASPE/SERPRO/2021)

**Afirmação:** "Uma coleção e um documento, no MongoDB, são equivalentes à tabela e à linha, no Modelo Relacional de Dados."

**Análise:** Correto. A analogia é:
- **Collection** → Tabela.
- **Document** → Registro (linha).

**Gabarito: C**

## 8. RESUMO PARA CONCURSOS

### 8.1 Principais Tipos e Exemplos

| Tipo | Exemplos | Uso Principal |
|------|----------|---------------|
| **Chave-Valor** | Redis, DynamoDB | Cache, armazenamento simples |
| **Documento** | MongoDB, DocumentDB | Aplicações web, dados semiestruturados |
| **Coluna** | Cassandra, HBase | Big data, aplicações analíticas |
| **Grafo** | Neo4j | Redes sociais, recomendações, rotas |

### 8.2 Diferenças entre SQL e NoSQL

| Característica | SQL (Relacional) | NoSQL |
|----------------|------------------|-------|
| Esquema | Fixo (explícito) | Flexível (implícito) |
| Escalabilidade | Vertical (*Scale Up*) | Horizontal (*Scale Out*) |
| Consistência | Forte (ACID) | Fraca (BASE) |
| Exemplos | Oracle, PostgreSQL, SQL Server | MongoDB, Redis, Cassandra |

### 8.3 Teorema de CAP e BASE

- **CAP:** Consistência, Disponibilidade, Tolerância a Particionamento — escolher duas.
- **BASE:** *Basically Available, Soft State, Eventually Consistent* — filosofia do NoSQL.
- **ACID vs BASE:** RDBMS = ACID (forte consistência); NoSQL = BASE (disponibilidade).