# Anotações – Banco de Dados – Avaliação de Modelos de Dados

## 1. Modelos de Dados (Revisão)

- **Modelo de dados:** representação abstrata que organiza elementos de dados.
- **Principais tipos:**

| MODELO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Relacional** | Dados organizados em tabelas inter-relacionadas por chaves primárias e estrangeiras. | Oracle, PostgreSQL, MySQL. |
| **Dimensional** | Dados organizados em tabelas **fato** e **dimensões**, reduzindo junções a apenas um nível. | Data Warehouses (Star Schema, Snowflake). |
| **Documentos** | Estrutura flexível (ex.: JSON), permite aninhamento de documentos. | MongoDB, CouchDB. |
| **Grafos** | Dados organizados como nós e arestas para representar relacionamentos complexos. | Neo4j. |

> ### 1.1 Limitação do modelo relacional
> - O modelo relacional apresentou limitações ao lidar com **grandes volumes de dados** devido à lentidão nas junções (joins).
> - Como solução, adotou-se o **modelo dimensional** (tabelas fato e dimensões) para reduzir a complexidade das consultas.

## 2. Avaliação de Modelos de Dados

### 2.1 Conceito

- **Avaliação de modelos de dados:** atividade objetiva que verifica a qualidade e a adequação de um modelo de dados.
- **Características:**
  - Deve ser feita por **quem não fez o modelo** (visão externa e imparcial).
  - **Não garante a qualidade sozinha** – a qualidade do modelo vai além da avaliação.
  - Pode ser feita em um **ciclo PDCA** (melhoria contínua).
  - Deve acontecer também em **processos ágeis** – a avaliação não é dispensável.

### 2.2 Ciclo PDCA na Avaliação de Modelos

| ETAPA | DESCRIÇÃO |
| --- | --- |
| **Plan (Planejar)** | Planejar como será feita a avaliação do modelo. |
| **Do (Executar)** | Executar a avaliação do modelo de dados. |
| **Check (Verificar)** | Verificar os resultados da avaliação, identificando possíveis melhorias. |
| **Act (Agir)** | Implementar as correções necessárias no modelo. |

> ### 2.2.1 Atenção (questão CESPE)
> - A qualidade **não é apenas controlada** – ela **deve ser planejada**.
> - O ciclo PDCA integra planejamento e controle da qualidade.

### 2.3 Aspectos Principais da Avaliação

| ASPECTO | DESCRIÇÃO |
| --- | --- |
| **Correção** | Identificar se há erros no modelo. |
| **Consistência** | Uniformidade na formatação dos dados (ex.: mesmo tipo de dado representado de forma igual em diferentes tabelas). |
| **Completude** | Verificar se todos os dados essenciais estão presentes. |
| **Normalização** | Assegurar que os dados estejam na mesma escala (evitar redundâncias). |
| **Extensibilidade** | Flexibilidade e capacidade de expansão do modelo. |
| **Conformidade com padrões** | Verificar se o modelo segue os padrões de codificação da organização. |
| **Validação da integridade** | Garantir a integridade dos dados (ex.: chaves, restrições). |
| **Documentação** | A documentação serve como base para a avaliação. |

### 2.4 Técnicas e Ferramentas

| TÉCNICA / FERRAMENTA | DESCRIÇÃO |
| --- | --- |
| **Ferramentas de modelagem de dados** | Softwares para criar e visualizar modelos (ex.: ERwin, PowerDesigner). |
| **Ferramentas de análise de dados** | Ferramentas para validar e testar os dados (ex.: SQL, ETL). |
| **Revisão por pares** | Outra pessoa revisa o modelo (visão externa). |
| **Simulação** | Preencher tabelas com dados simulados para verificar inconsistências. |
| **Validação com dados reais** | Testar o modelo com dados reais para verificar seu comportamento. |

## 3. Questões de Concurso Comentadas

### 3.1 (CESPE/CEBRASPE/2023/DATAPREV – Analista/Engenheiro de Dados)

**Item:** "A aplicação do ciclo PDCA nos processos de construção e avaliação de modelos de dados implica que a qualidade será controlada, em vez de planejada."

**Gabarito: Errado (E).**

**Comentário:** A qualidade **deve ser planejada**, e o ciclo PDCA é fundamental tanto no planejamento quanto no controle da qualidade.

### 3.2 (CESPE/CEBRASPE/2023/DATAPREV – Analista/Engenheiro de Dados)

**Item:** "A avaliação de modelos de dados deve ser uma atividade formal que compreenda a elaboração de laudos técnicos que registrem observações, ressalvas e eventuais erros encontrados durante a verificação da modelagem."

**Gabarito: Certo (C).**

**Comentário:** A avaliação formal registra erros e observações, integrando a melhoria contínua dos modelos.

### 3.3 (CESPE/CEBRASPE/2023/DATAPREV – Analista/Engenheiro de Dados)

**Item:** "No desenvolvimento ágil, a etapa de avaliação de modelos se torna dispensável, pois o desenvolvimento de software é feito de forma mais rápida."

**Gabarito: Errado (E).**

**Comentário:** A avaliação de modelos **não é dispensável** em processos ágeis – deve ser mantida como parte da qualidade.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/DATAPREV/2023) | E |
| 02 (CESPE/DATAPREV/2023) | C |
| 03 (CESPE/DATAPREV/2023) | E |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Modelo de dados** | Representação abstrata que organiza elementos de dados. |
| **Avaliação de modelo** | Atividade objetiva para verificar qualidade e adequação do modelo. |
| **PDCA** | Ciclo de melhoria contínua: Plan, Do, Check, Act. |
| **Correção** | Identificação de erros no modelo. |
| **Consistência** | Uniformidade na formatação dos dados. |
| **Completude** | Presença de todos os dados essenciais. |
| **Extensibilidade** | Flexibilidade e capacidade de expansão. |
| **Revisão por pares** | Avaliação feita por outra pessoa. |
| **Simulação** | Teste com dados fictícios para verificar inconsistências. |
| **Desenvolvimento ágil** | Avaliação de modelos não é dispensável. |

---

*Material complementar à aula "Banco de Dados – Avaliação de Modelos de Dados" (professor Vitor Kessler/Gran Concursos).*