# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO – VIEWS

## 1. VIEWS (VISÕES) - CONCEITOS FUNDAMENTAIS

- Uma **view** (visão), na terminologia SQL, pode ser definida como uma **relação única** que é derivada de outras tabelas ou visões previamente definidas.

- É uma ferramenta utilizada para **reforçar a segurança** em bancos de dados, permitindo ocultar partes das tabelas e restringir o acesso a determinadas informações.

- Por meio dela, é possível criar visões específicas que podem ser acessadas pelos usuários conforme suas permissões.

- As tabelas utilizadas na definição da visão são chamadas de **tabelas definidoras de visão**.

### 1.1 Características Principais

- Uma view **não existe necessariamente na forma física** — é considerada uma **tabela virtual**.

- Quando é definida uma view, o SGBD armazena a **definição** da view propriamente dita, em vez do resultado (*result set*) da consulta.

- Sempre que a view aparece em uma consulta, ela é **substituída pela expressão da consulta armazenada**.

- Uma visão **sempre está atualizada**. Se modificarmos as tuplas nas tabelas definidoras da view, a view deve refletir automaticamente tais alterações.

### 1.2 Limitações e Permissões

| Operação | Permissão |
|----------|-----------|
| **Consulta (SELECT)** | ✅ Sem limitação |
| **Atualização (INSERT/UPDATE/DELETE)** | ⚠️ Com limitações |

> ### 1.3 Regra do Modelo Relacional
> - Uma das regras do modelo relacional permite a atualização de dados por meio de views.
> - Embora essa prática não seja recomendada em muitos casos, normalmente é possível realizar atualizações quando a view se baseia em uma **única tabela**.

## 2. COMANDOS BÁSICOS

### 2.1 CREATE VIEW

**Sintaxe básica:**
```sql
CREATE VIEW v AS <EXPRESSÃO DE CONSULTA>
```
- `v` é o nome da view.
- `expressão de consulta` é qualquer expressão SQL válida.

**Exemplo:**
```sql
CREATE VIEW vw_estoque_zerado AS
SELECT nome_prod, nome_categ, nivel_estoque, unid
FROM produto
WHERE nivel_estoque = 0;
```

### 2.2 Renomeando Campos na View

```sql
CREATE VIEW vw_estoque_zerado (produto, categoria, estoque, unidade) AS
SELECT nome_prod, nome_categ, nivel_estoque, unid
FROM produto
WHERE nivel_estoque = 0;
```

### 2.3 View a partir de outra View

```sql
CREATE VIEW vw_estoque_zerado_limpeza AS
SELECT nome_prod, nome_categ, nivel_estoque, unid
FROM vw_estoque_zerado
WHERE nome_categ = 'LIMPEZA';
```

### 2.4 DROP VIEW

```sql
DROP VIEW <nome da view>;
```

## 3. TIPOS DE VIEWS

### 3.1 View Simples

- Recupera linhas de uma **única tabela base**.
- **Não contém funções de agregação**.
- Pode aceitar operações DML (INSERT, UPDATE, DELETE).

**Exemplo:**
```sql
CREATE VIEW vw_funcionario AS
SELECT nome, matricula
FROM tfuncionario;
```

### 3.2 View Complexa

- Baseada em **múltiplas tabelas** (JOINs).
- Pode conter **funções de agregação**.
- **Não aceita operações DML** (não é atualizável).

**Exemplo:**
```sql
CREATE VIEW v_funcionario AS
SELECT nome, matricula, nomeDepartamento
FROM tfuncionario E, tdepartamento D
WHERE D.TIDEPARTAMENTO_ID = E.TFUNCIONARIO_ID;
```

> ### 3.3 View Simples x View Complexa - Resumo
> - **View Simples:** uma tabela, sem funções de agregação → aceita DML.
> - **View Complexa:** múltiplas tabelas, com funções de agregação → NÃO aceita DML.

## 4. ATUALIZAÇÃO DE VIEWS

- A atualização de views representa a atualização das **tabelas definidoras** da view a partir de comandos DML na própria view (INSERT, UPDATE, DELETE).

- Embora seja possível, a atualização de views pode acarretar diversos **problemas de consistência de dados**.

### 4.1 WITH CHECK OPTION

- Cláusula que pode ser adicionada ao final da definição da view.

- Se uma tupla inserida na view **não satisfizer a condição da cláusula WHERE**, a inserção é **rejeitada** pelo SGBD.

**Exemplo:**
```sql
CREATE VIEW vw_produto_bebida AS
SELECT produto, categoria, unidade
FROM produto
WHERE categoria = 'BEBIDAS'
WITH CHECK OPTION;
```

### 4.2 Condições para View ser Atualizável

Uma view é atualizável se:

- A chave primária (PK) ou outra chave candidata estiver presente na lista de atributos.
- A cláusula FROM possui **apenas uma relação**.
- A cláusula SELECT possui **apenas atributos da relação** (não possui expressões, funções agregadas ou especificação DISTINCT).
- Os atributos não listados na view podem ser definidos como **nulos**.
- A consulta **não possui** cláusula GROUP BY ou HAVING.

### 4.3 Views NÃO Atualizáveis

- Views definidas em **múltiplas tabelas** (JOINs).
- Views com uso de **funções de agregação** (SUM, AVG, COUNT, etc.).
- Views com **GROUP BY** ou **HAVING**.
- Views com **DISTINCT**.

> ### 4.4 Problema de Inserção com Join
> - Quando uma view envolve mais de uma tabela com JOINs, **não é possível realizar inserções** por meio dela.
> - A atualização de dados por meio de uma view só é viável quando ela representa **integralmente uma única tabela**.
> - Ao realizar INSERT em uma view que oculta campos, os campos ocultos não são atualizados, gerando inconsistência.

## 5. VIEWS MATERIALIZADAS

- Alguns SGBDs permitem **armazenar as relações resultantes** de uma view.

- Se as relações reais usadas na definição da view mudarem, a view permanece atualizada (manutenção de view).

### 5.1 Diferença entre View e View Materializada

| Característica | View Comum | View Materializada |
|----------------|------------|-------------------|
| Armazenamento | Apenas a definição (consulta) | Cópia física dos dados |
| Atualização | Sempre atualizada (consulta em tempo real) | Atualizada conforme configuração |
| Desempenho | Consulta executada no momento do SELECT | Dados pré-computados, mais rápida para leitura |

> ### 5.2 Observações sobre Views Materializadas
> - A view materializada **não faz parte do padrão SQL** — é uma extensão implementada por alguns SGBDs (ex.: Oracle).
> - A decisão de uso envolve análise de **custo-benefício**:
>   - Tempo de resposta (mais rápida para leitura).
>   - Custo de armazenamento.
>   - Overhead adicional de atualizações.

### 5.3 Sintaxe (Oracle e outros SGBDs)

```sql
CREATE MATERIALIZED VIEW biologo_vw AS
SELECT nome, endereco, telefone
FROM funcionario
WHERE codigo_biologo = 674;
```

## 6. QUESTÕES COMENTADAS

### Questão 01 (UFC/2019)

**Análise das alternativas:**

| Alternativa | Análise |
|-------------|---------|
| a) É necessário stored procedure | ❌ Falso — não é necessário. |
| b) Permite apenas uma tabela | ❌ Falso — permite múltiplas tabelas. |
| c) Objetivo é melhorar desempenho | ❌ Falso — objetivo principal é segurança, não desempenho. |
| d) SGBD mantém views atualizadas | ✅ Correto — o SGBD é responsável por manter as views atualizadas. |
| e) Desvantagem é espaço consumido | ❌ Falso — views comuns não ocupam espaço físico. |

**Gabarito: d**

### Questão 02 (CESPE/FUB/2018)

**Afirmação:** "Uma view materializada armazena apenas a consulta que define e apresenta o resultado sempre atualizado."

**Análise:** A view materializada armazena **cópia física dos dados**, não apenas a consulta.

**Gabarito: E** (errado)

### Questão 03 (CESPE/TCE-MG/2018)

**Análise dos itens:**

| Item | Análise |
|------|---------|
| I | ❌ Visões complexas **NÃO** podem utilizar DML para manipulação. |
| II | ✅ Visões fazem referência a tabelas, sem armazenar linhas. |
| III | ✅ Visões complexas podem conter funções. |
| IV | ❌ Visões e tabelas temporárias **NÃO** são equivalentes. |

**Gabarito: c** (II e III)

### Questão 04 (QUADRIX/CFBIO/2018)

**Análise:** O código apresentado cria uma view comum (sem MATERIALIZED). Para view materializada, seria necessário `CREATE MATERIALIZED VIEW`.

**Gabarito: E** (errado)

### Questão 05 (CCV-UFS/2014)

**Descrição:** "tabela virtual, sem armazenar informações, não existe como entidade independente na base física."

**Gabarito: c** (visão/view)

### Questão 06 (CESPE/STJ/2018)

**Afirmação:** "A diferença entre materialized view e view comum é que a primeira é armazenada em cache como tabela física, enquanto a segunda existe apenas virtualmente."

**Gabarito: C** (certo)

### Questão 07 (CESPE/TCE-PE/2017)

**Afirmação:** "Uma view armazena os dados em uma tabela física do banco de dados, visando tornar ágeis as consultas."

**Análise:** View comum **NÃO** armazena dados fisicamente. Essa é uma característica das views materializadas.

**Gabarito: E** (errado)

### Questão 08 (CESPE/MEC/2015)

**Afirmação:** "View é um objeto que permite implementar segurança, omitindo dados irrelevantes. No entanto, não é permitido criar uma view com base na definição de outra view."

**Análise:** É **permitido** criar uma view com base na definição de outra view.

**Gabarito: E** (errado)

### Questão 09 (FUNDEP/UFV/2017)

**Sintaxe correta para criar uma view:**

```sql
CREATE VIEW vcli AS SELECT nomes FROM CLIENTES
```

**Gabarito: a**

## 7. RESUMO PARA CONCURSOS

### 7.1 Principais Características das Views

- **Tabela virtual** — não armazena dados fisicamente.
- **Segurança** — principal objetivo, oculta dados de usuários.
- **Sempre atualizada** — reflete alterações nas tabelas base.
- **Atualização** — permitida apenas em views simples (uma tabela, sem agregação).
- **WITH CHECK OPTION** — garante que inserções respeitem a condição WHERE.

### 7.2 Comparação: View x View Materializada

| Característica | View | View Materializada |
|----------------|------|-------------------|
| Armazenamento físico | Não | Sim |
| Objetivo principal | Segurança | Desempenho |
| Atualização automática | Sim (consulta em tempo real) | Depende da configuração |
| Padrão SQL | Sim | Não (extensão) |

### 7.3 View Complexa x View Simples

- **Simples:** uma tabela, sem agregação → permite DML.
- **Complexa:** múltiplas tabelas, com agregação → NÃO permite DML.