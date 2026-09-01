# Gatilhos e Stored Procedures

## 1. Gatilhos (Triggers)
- Um gatilho é um bloco de código que é automaticamente executado (disparado) quando determinado evento de banco de dados ocorre.
- Na ocorrência do evento, uma ou mais condições são avaliadas e, se satisfeitas, uma ou mais ações são executadas.
- Sua finalidade principal é manter a consistência do banco de dados, automatizando regras de negócio ou auditoria.
- Um gatilho não pode ser chamado explicitamente por um usuário ou aplicação; ele só é executado em resposta ao evento definido.
- O evento disparador está sempre associado a operações de atualização de dados:
  - INSERT;
  - UPDATE;
  - DELETE.
- Não é possível definir gatilhos para o comando SELECT, pois consultas não modificam registros, e não há um evento de alteração a ser monitorado.

> [!CAUTION] OBSERVAÇÃO: 
> - O gatilho só é disparado por comandos que alteram dados (INSERT, UPDATE, DELETE). Comandos SELECT não disparam gatilhos, mesmo que executados com frequência.

### 1.1 Elementos do Gatilho
- Um gatilho é composto por três estruturas obrigatórias:
  - Evento: a operação que dispara o gatilho (INSERT, UPDATE ou DELETE);
  - Condição: avaliação que determina se a ação deve ser executada (opcional, mas comum);
  - Corpo (ação): o bloco de comandos que será executado quando o evento ocorrer e a condição for verdadeira.

### 1.2 Sintaxe Básica (Oracle PL/SQL)
- A sintaxe completa de um gatilho no Oracle, que é cobrada com frequência em provas, segue o modelo:

```sql
CREATE OR REPLACE TRIGGER nome_gatilho
BEFORE | AFTER
DELETE OR INSERT OR UPDATE OF coluna1, coluna2, ...
ON nome_da_tabela
REFERENCING OLD AS nome_antigo NEW AS nome_novo
FOR EACH ROW
WHEN condicao
DECLARE
   -- área de declaração de variáveis
BEGIN
   -- área de comandos (corpo do gatilho)
END;
```

- Explicação dos principais elementos:
  - `BEFORE | AFTER`: define se o gatilho será executado antes ou depois do evento;
  - `DELETE OR INSERT OR UPDATE OF`: especifica quais operações disparam o gatilho, podendo ser restritas a colunas específicas;
  - `ON nome_da_tabela`: tabela à qual o gatilho está associado;
  - `REFERENCING OLD AS ... NEW AS ...`: permite referenciar os valores antigos e novos dos registros afetados;
  - `FOR EACH ROW`: indica que o gatilho será executado para cada linha afetada (linha a linha);
  - `WHEN condicao`: condição adicional para execução do gatilho.

> [!TIP] DICAS: 
> - Em outros SGBDs, como SQL Server, a sintaxe é mais simples, mas a lógica é a mesma: evento, tabela e condições.
> - O Oracle é o mais cobrado em concursos devido à sua robustez e complexidade.

### 1.3 Cláusulas de Referência a Valores
- Dentro do corpo do gatilho, é possível acessar os valores antigos e novos dos atributos das linhas afetadas:
  - `:NEW.nome_atributo` – representa o novo valor que será (ou foi) atribuído ao campo, disponível em operações INSERT ou UPDATE;
  - `:OLD.nome_atributo` – representa o valor anterior do campo, disponível em operações DELETE ou UPDATE.

### 1.4 Predicados de Evento
- Em alguns SGBDs, como o Oracle, podem ser usados predicados para verificar qual operação disparou o gatilho:
  - `INSERTING` – retorna TRUE se o gatilho foi ativado por um INSERT;
  - `UPDATING` – retorna TRUE se foi ativado por um UPDATE;
  - `DELETING` – retorna TRUE se foi ativado por um DELETE.
- Esses predicados ajudam a escrever um único gatilho que trata diferentes eventos com lógicas distintas.

### 1.5 Exemplo Prático de Auditoria
- Um exemplo clássico de gatilho é manter uma tabela de auditoria de alterações salariais:
  - Toda vez que um UPDATE na tabela de salários ocorrer, um gatilho insere um registro em uma tabela de auditoria, gravando o usuário, a data e o valor antigo e novo.
- Outro exemplo comum é o controle de estoque:
  - Quando um item é vendido (INSERT em tabela de vendas), o gatilho subtrai a quantidade do estoque.
  - Se a venda for cancelada (DELETE), o gatilho repõe o estoque automaticamente.
- O código do gatilho de estoque, conforme mencionado, utiliza:
  - `BEFORE INSERT OR DELETE` – executa antes da inserção ou exclusão;
  - `FOR EACH ROW` – processa cada linha afetada;
  - `REFERENCING OLD AS antigo NEW AS novo` – para acessar as quantidades.
  - No corpo, usa `IF inserting THEN` para subtrair do estoque, e `ELSEIF deleting THEN` para adicionar de volta.

> [!CAUTION] OBSERVAÇÃO: 
> - O professor destaca que, atualmente, a prática de criar tabelas de auditoria via gatilho não é recomendada por questões de desempenho, podendo sobrecarregar o banco. Em aplicações modernas, esse tipo de log é feito por APIs ou camadas de aplicação.

### 1.6 Habilitar, Desabilitar e Remover um Gatilho
- Para controlar a execução de um gatilho sem apagá-lo, usam-se os comandos:
  - `ALTER TRIGGER nome_gatilho ENABLE;` – reativa o gatilho;
  - `ALTER TRIGGER nome_gatilho DISABLE;` – desativa temporariamente, mantendo a definição.
- Para remover permanentemente o gatilho do banco:
  - `DROP TRIGGER nome_gatilho;`

> [!TIP] DICAS: 
> - Desabilitar (DISABLE) é útil quando se deseja realizar uma carga massiva de dados sem disparar os gatilhos, evitando lentidão. Após a carga, reabilita-se (ENABLE).
> - O comando DROP é definitivo; a definição do gatilho é perdida.

## 2. Stored Procedures
- Stored Procedure (procedimento armazenado) é um segmento de código SQL e comandos procedurais que fica armazenado no servidor de banco de dados.
- Pode ser chamado por triggers, por outras procedures ou por aplicações externas (escritas em C#, Java, PHP, etc.).
- Cada SGBD possui sua própria linguagem procedural:
  - Oracle: PL/SQL;
  - PostgreSQL: PL/pgSQL (antigamente só Function, hoje também Procedure);
  - SQL Server: Transact-SQL (T-SQL);
  - MySQL: linguagem procedural própria (similar a PL/SQL).

> [!CAUTION] OBSERVAÇÃO: 
> - A distinção entre Function e Procedure é que a Function retorna um valor (normalmente escalar ou tabela), enquanto a Procedure executa um bloco de comandos e pode retornar valores por meio de parâmetros OUT. O termo "procedimento armazenado" é genérico e pode abranger ambos.

### 2.1 Vantagens das Stored Procedures
- Melhoria de performance:
  - A procedure é compilada uma vez e armazenada no banco, reduzindo o tempo de execução de comandos repetidos.
- Redução do tráfego de dados entre aplicação e banco:
  - A aplicação envia apenas a chamada da procedure, não uma sequência de comandos SQL.
- Reutilização:
  - Uma mesma procedure pode ser utilizada por diferentes aplicações, centralizando a lógica de negócio.

### 2.2 Declaração e Chamada
- Para declarar uma procedure, é comum alterar o delimitador para evitar que o ponto e vírgula dentro do corpo encerre o comando prematuramente.
- Exemplo com MySQL:
```sql
DELIMITER $$
CREATE PROCEDURE selecionarTodosProdutos()
BEGIN
    SELECT * FROM PRODUTO;
END $$
DELIMITER ;
```

- A chamada da procedure é feita com o comando:
  - `CALL nome_da_procedure(parametros);`

> [!TIP] DICAS: 
> - O delimitador é alterado para `$$` ou `//` para permitir que o ponto e vírgula seja usado dentro do corpo da procedure. Depois, restaura-se o delimitador para ponto e vírgula.

### 2.3 Variáveis em Stored Procedures
- Dentro do corpo da procedure, podem ser declaradas variáveis locais.
- A declaração é feita na seção de declaração (após `DECLARE` ou no início do bloco `BEGIN`).
- A atribuição de valores pode ser feita com `SET` ou `SELECT ... INTO`.

### 2.4 Parâmetros em Stored Procedures
- As procedures podem receber parâmetros, que são classificados em três modos:

| MODO | DESCRIÇÃO |
|------|-----------|
| IN   | Parâmetro de entrada. O valor é passado pela aplicação para a procedure. É o modo padrão (caso não seja especificado, assume IN). |
| OUT  | Parâmetro de saída. A procedure atribui um valor a esse parâmetro, que é retornado à aplicação. |
| INOUT| Parâmetro de entrada e saída. A aplicação passa um valor, a procedure pode modificá-lo e retornar o novo valor. |

- Exemplo de uso:
  - Parâmetro IN para filtrar dados (ex.: código do produto).
  - Parâmetro OUT para retornar o total de registros ou um valor calculado.
  - Parâmetro INOUT para atualizar uma variável que serve como contador ou acumulador.

> [!CAUTION] OBSERVAÇÃO: 
> - O modo padrão é IN, e não OUT, como destaca o professor. Isso é uma pegadinha comum em provas.
> - Parâmetros OUT são usados para retornar valores, não para entrada.
> - Parâmetros IN são usados para passar valores para a procedure.
> - Uma procedure pode não ter nenhum parâmetro.

### 2.5 Observações sobre Sintaxe e Comandos
- O comando `LIMIT` (MySQL) é usado para restringir o número de linhas retornadas, como em `SELECT * FROM PRODUTO LIMIT 100`, que traz apenas os 100 primeiros produtos.
- As stored procedures podem chamar outras stored procedures, permitindo modularidade.
- Além de comandos SQL, a procedure pode conter estruturas condicionais (IF, CASE), laços (LOOP, WHILE), declaração de variáveis, etc., ou seja, não se restringe apenas a comandos SQL padronizados.

> [!TIP] DICAS: 
> - Uma característica importante: stored procedures podem retornar um valor de status (código de erro ou sucesso), indicando se a execução foi bem-sucedida ou falhou.
> - Elas também podem aumentar a segurança, pois o acesso aos dados pode ser controlado por meio das procedures, sem dar permissões diretas sobre as tabelas.