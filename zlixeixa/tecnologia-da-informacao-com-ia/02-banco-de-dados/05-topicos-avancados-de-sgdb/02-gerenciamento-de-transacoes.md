# Gerenciamento de Transações

## 1. Transações
- Uma transação é uma unidade lógica de processamento, incluindo uma ou mais operações sobre um banco de dados.
- É formada por uma sequência de operações que precisam ser executadas integralmente ou desfeitas totalmente, com o objetivo de manter a consistência do banco de dados.
- As operações podem incluir inclusão, exclusão, modificação ou seleção de dados.
- A transação é uma unidade atômica de trabalho que ou é completada integralmente ou simplesmente não é realizada.
- Para fins de recuperação, o sistema precisa acompanhar o momento em que a transação se inicia, termina, é confirmada (commit) ou abortada.

## 2. Tipos de Falhas
- Falhas podem ocorrer em diferentes níveis e comprometer a execução correta das transações.
- Os principais tipos de falhas incluem:
  - Falha do computador: system crash ou colapso do sistema.
  - Erro de hardware, software ou rede.
  - Erro de transação ou de sistema, como overflow, divisão por zero, erros lógicos.
  - Erros locais ou condições de exceção detectados pela transação.
  - Condições de cancelamento, como dados não encontrados, saldo insuficiente ou exceções programadas.
  - Imposição do controle de concorrência, como bloqueios e situações de impasse (deadlocks).
  - Falha de disco, como quebra do cabeçote de leitura ou perda de blocos.
  - Problemas físicos ou catástrofes, como incêndio, falta de energia ou sabotagem.

## 3. Estados de uma Transação
- O diagrama de estados de uma transação ilustra as diferentes fases pelas quais ela pode passar durante sua execução.
- Os principais estados são:
  - Ativa: a transação está em execução.
  - Parcialmente confirmada: algumas operações foram concluídas, mas a transação ainda não foi totalmente confirmada.
  - Comitada: todas as operações foram concluídas com sucesso e as alterações são permanentes.
  - Falha: ocorreu um erro durante a execução, e a transação não pode prosseguir.
  - Abortada: a transação foi desfeita, e nenhuma alteração é mantida.
- Caso ocorra algum problema durante o processo, a transação entra em estado de falha e é abortada, ou seja, nenhuma operação é confirmada e todas são desfeitas.
- Durante a execução, pode haver confirmações parciais (partial commits) à medida que algumas operações são validadas. Ao final, se todas forem concluídas com sucesso, ocorre o commit, confirmando permanentemente as alterações no banco de dados.

## 4. Comandos de Transação
- Os comandos básicos para controle de transações são:
  - BEGIN_TRANSACTION: marca o início da execução da transação.
  - READ/WRITE: especifica operações de leitura e escrita nos itens do banco de dados.
  - END_TRANSACTION: finaliza a transação, marcando o fim das operações de leitura ou gravação.
  - COMMIT_TRANSACTION: sinaliza o final bem-sucedido da transação, confirmando as atualizações no banco de dados de forma permanente.
  - ROLLBACK (ABORT): sinaliza que a transação terminou sem sucesso, desfazendo todas as alterações realizadas.

### 4.1 Instruções de Controle
- As instruções de controle permitem maior flexibilidade no gerenciamento de transações:
  - COMMIT: finaliza a transação atual, tornando permanentes todas as alterações pendentes.
  - SAVEPOINT: marca um ponto de gravação dentro da transação atual, utilizado para dividir a transação em partes menores.
  - ROLLBACK TO SAVEPOINT: descarta o ponto de gravação especificado e todas as alterações realizadas após ele.
- O uso de SAVEPOINT e ROLLBACK TO SAVEPOINT permite maior controle sobre as operações, possibilitando desfazer apenas parte da transação em caso de erro.

> [!TIP] DICAS: 
> - Em provas, o foco principal está nos problemas de concorrência (como leitura suja e falta de serialização) e não apenas nos comandos básicos como commit e rollback.

### 4.2 Exemplo de Transação
- O exemplo a seguir ilustra o uso dos comandos de controle em uma transação prática:

```sql
INSERT INTO UNIDADE (ID_UNIDADE, NOME_UNIDADE, ID_UNIDADE_SUPERIOR) VALUES (10, 'DIRETORIA DE TECNOLOGIA DA INFORMAÇÃO', 5);
INSERT INTO UNIDADE (ID_UNIDADE, NOME_UNIDADE, ID_UNIDADE_SUPERIOR) VALUES (11, 'COORDENAÇÃO DE SISTEMAS', 10);
SAVEPOINT ponto1;
DELETE FROM EMPREGADO WHERE SALARIO < 1000;
ROLLBACK TO SAVEPOINT ponto1;
UPDATE EMPREGADO SET SALARIO = SALARIO * 1.05 WHERE ID_UNIDADE = 11;
COMMIT;
```

- Neste exemplo:
  - São inseridas duas unidades organizacionais: Diretoria de Tecnologia da Informação (unidade 10) e Coordenação de Sistemas (unidade 11).
  - Um savepoint chamado "ponto1" é criado.
  - Uma operação de exclusão de empregados com salário inferior a 1000 é realizada, mas é desfeita com o rollback to savepoint.
  - Em seguida, é feito um update para aumentar em 5% o salário dos empregados da unidade 11.
  - Ao final, um commit confirma as alterações permanentemente.
- O estado final do banco de dados refletirá apenas as inserções das unidades e o reajuste salarial, enquanto a exclusão será descartada.

> [!CAUTION] OBSERVAÇÃO: 
> - A ausência do commit impede que as alterações sejam efetivamente gravadas no banco de dados, dependendo da configuração do SGBD.
> - Alguns SGBDs possuem o modo autocommit ativado por padrão, confirmando as operações automaticamente.
> - Neste exemplo, o rollback to savepoint descartou a exclusão, mas manteve as inserções e o update, que foram confirmados no commit final.

## 5. Propriedades ACID
- As transações em bancos de dados devem respeitar um conjunto de propriedades conhecido pelo acrônimo ACID, que assegura a execução correta, segura e confiável.
- As propriedades são:
  - Atomicidade: a transação é uma unidade atômica de processamento, ou seja, ou é realizada integralmente ou não é realizada. Em caso de falha, nenhuma modificação é mantida, e o banco retorna ao estado anterior.
  - Consistência: a transação leva o banco de dados de um estado consistente para outro estado consistente, respeitando todas as regras e restrições estabelecidas.
  - Isolamento: a execução de uma transação não deve sofrer interferência de outras transações concorrentes. O sistema deve garantir que o resultado final seja equivalente ao que ocorreria se cada transação fosse executada sequencialmente.
  - Durabilidade (persistência): após a confirmação de uma transação (commit), seus efeitos se tornam permanentes, mesmo em caso de falhas, quedas de energia ou reinicializações do sistema.

## 6. Transações Concorrentes
- O controle de transações concorrentes é um dos principais desafios dos SGBDs, pois transações simultâneas podem gerar conflitos e inconsistências se não forem adequadamente gerenciadas.
- Um modelo simplificado utiliza duas operações básicas:
  - read_item(X): lê um item X do banco de dados e o transfere para uma variável X na memória.
  - write_item(X): escreve o valor de uma variável X da memória de volta para o item X no banco de dados.
- A simultaneidade dessas operações pode gerar conflitos, que são classificados em problemas clássicos.

### 6.1 Problemas Clássicos de Concorrência
- Os principais problemas causados por transações concorrentes são:
  - Perda de atualização: ocorre quando duas transações modificam o mesmo dado e a alteração feita por uma é sobrescrita pela outra.
  - Atualização temporária (leitura suja): ocorre quando uma transação lê dados modificados por outra transação que ainda não foi confirmada (commit). Se a segunda transação for desfeita (rollback), os dados lidos tornam-se inválidos.
  - Leitura não repetitiva: ocorre quando uma transação lê o mesmo dado mais de uma vez e obtém valores diferentes devido a alterações feitas por outra transação já confirmada.
  - Leitura fantasma: ocorre quando, ao repetir uma consulta, surgem registros adicionais que antes não estavam presentes, devido a inserções feitas por outra transação.

#### 6.1.1 Perda de Atualização
- O problema ocorre quando duas transações concorrentes manipulam a mesma variável X.
- Ambas as transações leem o mesmo valor inicial de X.
- Ao gravarem suas alterações, uma delas sobrescreve a atualização feita pela outra, resultando na perda da primeira modificação.
- Exemplo: T1 lê X, atualiza para X - N; T2 lê X, atualiza para X + N. Após T1 gravar X - N, T2 grava X + N, sobrescrevendo a atualização de T1.
- O valor final armazenado corresponde apenas à alteração de T2, e a modificação de T1 é perdida.

#### 6.1.2 Leitura Suja (Dirty Read)
- Ocorre quando uma transação lê um valor que foi modificado por outra transação ainda não confirmada.
- Se a transação que modificou o dado falhar e for desfeita, o valor lido torna-se inválido, comprometendo a integridade da primeira transação.
- Esse problema pode levar a inconsistências no processamento, pois os dados lidos são temporários e podem ser revertidos.

#### 6.1.3 Leitura Não Repetitiva (Non-repeatable Read)
- Ocorre quando uma transação lê um valor X e, posteriormente, ao reler esse mesmo valor, obtém uma versão alterada por outra transação já confirmada.
- A primeira leitura retorna um valor inicial, enquanto a segunda reflete uma modificação feita por outra transação.
- Isso gera inconsistência, pois o dado lido não se mantém estável durante a execução da transação.

#### 6.1.4 Leitura Fantasma (Phantom Read)
- Ocorre quando uma transação realiza uma consulta e, em seguida, outra transação insere ou modifica registros que atendem ao mesmo critério da consulta original.
- Quando a primeira transação repete a consulta, novos registros (fantasmas) aparecem.
- Diferentemente da leitura não repetitiva, que envolve a alteração de um valor específico, a leitura fantasma envolve o surgimento de novos registros.
- Esse problema afeta a integridade das consultas repetidas, pois os resultados mudam inesperadamente.

### 6.2 Resumo dos Problemas Clássicos
| PROBLEMA | DESCRIÇÃO |
|----------|-----------|
| Dirty read (leitura suja) | Leitura de dados ainda não confirmados (não comitados). |
| Non-repeatable read (leitura não repetitiva) | A mesma consulta retorna resultados diferentes dentro da mesma transação. |
| Phantom read (leitura fantasma) | Uma transação vê registros que não existiam em uma leitura anterior. |

> [!TIP] DICAS: 
> - A leitura suja envolve dados não comitados; a leitura não repetitiva envolve dados já comitados que foram alterados; a leitura fantasma envolve o surgimento de novos registros.
> - Esses problemas são cobrados com frequência em provas, sendo essenciais para compreender o comportamento correto das transações em ambientes concorrentes.

> [!CAUTION] OBSERVAÇÃO: 
> - A perda de atualização também é um problema clássico, embora não esteja na tabela, sendo igualmente importante.
> - Os SGBDs modernos implementam estratégias eficazes para evitar esses problemas, tornando sua ocorrência rara em sistemas bem configurados.
> - O estudo desses conceitos é fundamental para resolver problemas de concorrência e é amplamente cobrado em concursos e certificações.