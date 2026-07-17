# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - GATILHOS E STORED PROCEDURES

## 1. GATILHOS (TRIGGERS)

- Um gatilho (*trigger*) é disparado quando determinado **evento de Banco de Dados** ocorre.

- Na ocorrência de determinado evento, uma ou mais **condições** são avaliadas e uma ou mais **ações** são executadas.

- É utilizado para **manter a consistência** do banco de dados.

- **Um gatilho não pode ser chamado explicitamente** — ele é executado automaticamente quando o evento ocorre.

### 1.1 Estrutura do Gatilho

É composto por três elementos:

| Elemento | Descrição |
|----------|-----------|
| **Evento** | Operação que dispara o gatilho (INSERT, UPDATE, DELETE). |
| **Condição** | Avaliada para determinar se a ação deve ser executada. |
| **Corpo (Ação)** | Comandos executados quando o evento ocorre e a condição é satisfeita. |

> ### 1.2 Eventos que Disparam Gatilhos
> - O evento dispara uma regra associada a operações de atualização do BD:
>   - **INSERT**
>   - **UPDATE**
>   - **DELETE**
> - **Não é possível definir gatilhos com SELECT**, pois, nesses casos, os registros não são modificados.

### 1.3 Exemplo Prático de Uso

- Um exemplo prático de aplicação onde o gatilho é muito utilizado é uma **tabela de salário** na qual se coloca um gatilho para saber quem atualizou o salário.

- Toda vez que houver UPDATE de salário, envia-se um dado para uma **tabela de auditoria**, gravando o usuário que fez a alteração e qual foi a modificação.

> ### 1.4 Boa Prática
> - Hoje em dia, fazer tabela de auditoria via gatilho **não é considerada uma boa prática**, pois sobrecarrega o banco de dados.
> - Atualmente, isso é feito via API ou gravação de *log* na aplicação.

### 1.5 Cláusulas de Referência

| Cláusula | Descrição |
|----------|-----------|
| **:NEW.nome_atributo** | Representa o **novo valor** para o campo que está sendo alterado por um comando INSERT ou UPDATE. |
| **:OLD.nome_atributo** | Representa o **valor anterior** de um campo que está sendo alterado por comando DELETE ou UPDATE. |

### 1.6 Predicados

Retornam **TRUE** se o gatilho foi ativado por:

- **INSERTING** — ativado por INSERT.
- **UPDATING** — ativado por UPDATE.
- **DELETING** — ativado por DELETE.

### 1.7 Sintaxe (PL/SQL - Oracle)

```sql
CREATE OR REPLACE TRIGGER trg_estoque
BEFORE INSERT OR DELETE OF qtde ON item_venda
REFERENCING OLD AS antigo NEW AS novo
FOR EACH ROW
BEGIN
    IF inserting THEN
        UPDATE produto SET estoque = estoque - :novo.qtde;
    ELSIF deleting THEN
        UPDATE produto SET estoque = estoque + :old.qtde;
    END IF;
END;
```

> ### 1.8 Explicação do Exemplo
> - O gatilho controla o **estoque** automaticamente.
> - Quando há uma nova venda (INSERT), subtrai-se do estoque.
> - Quando a venda é cancelada (DELETE), o item volta para o estoque.
> - O gatilho faz isso de forma **automática** e **transparente** para a aplicação.

### 1.9 Habilitar, Desabilitar e Remover um Gatilho

| Comando | Descrição |
|---------|-----------|
| `ALTER TRIGGER <nome> ENABLE;` | Habilita o gatilho (volta a funcionar). |
| `ALTER TRIGGER <nome> DISABLE;` | Desabilita o gatilho (para de funcionar, mas não o apaga). |
| `DROP TRIGGER <nome>;` | Remove o gatilho permanentemente. |

## 2. STORED PROCEDURES

- *Stored Procedure* (SP) é um segmento da SQL declarativa utilizada para **armazenar dentro do banco de dados** funcionalidades que podem ser chamadas a partir de:
  - Gatilhos (*triggers*).
  - Outras SPs.
  - Aplicações (C#, Java, PHP, etc.).

- Cada banco tem sua própria linguagem:
  - **PLPGSQL** (PostgreSQL).
  - **Transact-SQL** (Microsoft SQL Server).
  - **PL/SQL** (Oracle).
  - **MySQL** (linguagem própria).

### 2.1 Diferença entre Function e Stored Procedure

| Característica | Function | Stored Procedure |
|----------------|----------|------------------|
| Retorno | **Sempre retorna um valor** | Pode ou não retornar valor |
| Uso em SELECT | Pode ser usada em consultas | Não pode ser usada em consultas |
| Parâmetros | IN (entrada) | IN, OUT, INOUT |

> ### 2.2 Observação
> - Falar em **procedimento armazenado** é mais amplo — pode se referir tanto a FUNCTION quanto a STORED PROCEDURE.
> - Em versões anteriores do PostgreSQL não havia o nome PROCEDURE, apenas FUNCTION.

### 2.3 Vantagens das Stored Procedures

| Vantagem | Descrição |
|----------|-----------|
| **Melhoria da performance** | A SP é **compilada e armazenada** no banco de dados. |
| **Redução do tráfego** | A aplicação faz apenas a **chamada** da SP, não enviando múltiplos comandos SQL. |
| **Reutilização** | Um procedimento pode ser utilizado em **diversas aplicações**. |
| **Segurança** | Pode restringir acesso direto às tabelas, permitindo apenas execução da SP. |

### 2.4 Declaração e Chamada

**Declaração (MySQL):**
```sql
DELIMITER $$
CREATE PROCEDURE selecionarTodosProdutos()
BEGIN
    SELECT * FROM PRODUTO;
END $$
DELIMITER ;
```

**Chamada:**
```sql
CALL selecionarTodosProdutos();
```

> ### 2.5 Delimitador
> - O delimitador é usado para que o script não pare ao encontrar ponto e vírgula dentro do corpo da procedure.
> - Muda-se o delimitador para `$$`, roda-se todo o script e depois volta para ponto e vírgula.

### 2.6 Variáveis em Stored Procedure

**Declaração de variável:**
```sql
DECLARE nome_variavel tipo;
```

**Atribuição de valor:**
```sql
SET nome_variavel = valor;
```

### 2.7 Parâmetros em Stored Procedure

| Modo | Descrição |
|------|-----------|
| **IN** | Parâmetro de **entrada**. Valor passado para a procedure. |
| **OUT** | Parâmetro de **saída**. Valor retornado pela procedure. |
| **INOUT** | Parâmetro de **entrada e saída**. Valor passado e modificado pela procedure. |

**Exemplo com parâmetro IN:**
```sql
CREATE PROCEDURE buscarProdutos(IN limite INT)
BEGIN
    SELECT * FROM PRODUTO LIMIT limite;
END;
```

**Exemplo com parâmetro OUT:**
```sql
CREATE PROCEDURE contarProdutos(OUT total INT)
BEGIN
    SELECT COUNT(*) INTO total FROM PRODUTO;
END;
```

## 3. QUESTÕES COMENTADAS

### Questão 01 (FCC/DPE-AM/2018)

**As três estruturas que compõem um gatilho são: evento, condição e ação.**

**Gabarito: d**

### Questão 02 (FCC/DPE-RS/2018)

**Função básica de um gatilho: executar comandos previamente declarados quando da ocorrência de um evento no banco de dados.**

**Gabarito: d**

### Questão 03 (FCC/TST/2012)

**O disparo de um gatilho ocorre em decorrência de operações de exclusão, modificação ou inserção de um registro em uma tabela.**

**Gabarito: b**

### Questão 04 (FCC/TRT-19/2011)

**Análise das alternativas sobre modos de parâmetros em PL/SQL:**

| Alternativa | Análise |
|-------------|---------|
| a) Default é OUT | ❌ Default é **IN**. |
| b) Três modos: IN, OUT e INOUT | ✅ Correto. |
| c) IN retorna valor | ❌ IN é para **entrada**, não retorno. |
| d) OUT passa valor para procedure | ❌ OUT é para **retorno**. |
| e) Deve ter pelo menos um IN e um OUT | ❌ Procedure **pode não ter parâmetros**. |

**Gabarito: b**

> ### Modos de Parâmetros - Resumo
> - **IN (default):** entrada — passa valor para a procedure.
> - **OUT:** saída — retorna valor da procedure.
> - **INOUT:** entrada e saída — passa e retorna valor.

### Questão 05 (FCC/DPE-SP/2010)

**Característica que NÃO é de stored procedure: utilizar somente comandos SQL padronizados.**

**Análise:** A SP possui linguagem de programação associada, com declaração de variáveis, passagem de parâmetros, etc. **Não se usa apenas comandos SQL padronizados.**

**Gabarito: b**

### Questão 06 (QUADRIX/CRO-PR/2016)

**Conceito descrito: coleção de comandos SQL para otimização, encapsula tarefas repetitivas, aceita parâmetros de entrada e retorna valor de status.**

**Gabarito: e** (Stored Procedures)

### Questão 07 (VUNESP/URBANISMO/2014)

**Stored procedures representam programas armazenados no servidor de banco de dados.**

**Gabarito: e**

## 4. COMPARAÇÃO ENTRE GATILHOS E STORED PROCEDURES

| Característica | Trigger | Stored Procedure |
|----------------|---------|------------------|
| Disparo | **Automático** (evento no BD) | **Explícito** (chamada manual) |
| Chamada | Não pode ser chamada explicitamente | Chamada via `CALL` ou aplicação |
| Parâmetros | Não aceita parâmetros | Aceita IN, OUT, INOUT |
| Eventos | INSERT, UPDATE, DELETE | Qualquer operação |
| Retorno | Não retorna valor | Pode retornar valor (OUT) |
| Uso principal | Manter consistência, auditoria | Reutilização de código, performance |