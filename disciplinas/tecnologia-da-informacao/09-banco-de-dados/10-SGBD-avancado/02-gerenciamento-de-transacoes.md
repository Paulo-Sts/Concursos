# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - GERENCIAMENTO DE TRANSAÇÕES

## 1. TRANSAÇÕES

- Transação é uma unidade lógica de processamento, incluindo uma ou mais operações sobre um banco de dados.

- É formada por sequência de operações que precisam ser executadas integralmente ou desfeitas totalmente, com o objetivo de manter a consistência do BD.

- As operações podem incluir inclusão, exclusão, modificação ou seleção.

- Transação é uma unidade atômica de trabalho que ou é completada integralmente ou simplesmente não é realizada.

- Para fins de recuperação, o sistema precisa acompanhar o momento em que a transação se inicia, termina e é confirmada (*commit*) ou abortada.

### 1.1 Comandos e Instruções

- **BEGIN_TRANSACTION (INICIAR TRANSAÇÃO):** Marca o início da execução da transação.

- **READ/WRITE:** Especifica operações de leitura/escrita nos itens de banco de dados.

- **END_TRANSACTION (Finalizar a transação):** Especifica que operações de leitura ou gravação terminaram e marca o final da execução da transação.

- **COMMIT_TRANSACTION (Confirmar Transação):** Sinaliza o final bem-sucedido da transação, de modo que quaisquer atualizações executadas pela transação podem ser seguramente confirmadas (*commited*) para o BD e não serão desfeitas.

- **ROLLBACK (ABORT):** Sinaliza que a transação terminou sem sucesso, de modo que quaisquer alterações ou efeitos devem ser desfeitos.

### 1.2 Instruções de Controle

- **COMMIT:** Finaliza a transação atual tornando permanentes todas as alterações de dados pendentes.

- **SAVEPOINT:** Marca um ponto de gravação dentro da transação atual, sendo utilizado para dividir uma transação em partes menores.

- **ROLLBACK [TO SAVEPOINT]:** ROLLBACK finaliza a transação atual, descartando todas as alterações de dados pendentes. ROLLBACK TO SAVEPOINT descarta o ponto de gravação determinado e as alterações seguintes a ele.

### 1.3 Exemplo Prático

```
1. INSERT INTO UNIDADE (ID_UNIDADE, NOME_UNIDADE, ID_UNIDADE_SUPERIOR) VALUES (10, 'DIRETORIA DE TECNOLOGIA DA INFORMAÇÃO', 5);
2. INSERT INTO UNIDADE (ID_UNIDADE, NOME_UNIDADE, ID_UNIDADE_SUPERIOR) VALUES (11, 'COORDENAÇÃO DE SISTEMAS', 10);
3. SAVEPOINT ponto1;
4. DELETE FROM EMPREGADO WHERE SALARIO < 1000;
5. ROLLBACK TO SAVEPOINT ponto1;
6. UPDATE EMPREGADO SET SALARIO = SALARIO * 1.05 WHERE ID_UNIDADE = 11;
7. COMMIT;
```

- Neste exemplo, as duas inserções são mantidas.

- O *savepoint* "ponto1" é criado após as inserções.

- O comando DELETE é executado, mas depois desfeito pelo ROLLBACK TO SAVEPOINT.

- O UPDATE é executado e, junto com as inserções, é confirmado pelo COMMIT.

- O estado final do banco de dados refletirá apenas as inserções das duas unidades e o reajuste salarial dos empregados da unidade 11. A operação de exclusão terá sido descartada devido ao uso do *rollback*.

> ### 1.3.1 Autocommit
> - Alguns SGBDs permitem a configuração do modo de *autocommit*, no qual as operações são automaticamente confirmadas sem a necessidade de um comando explícito de *commit*.
> - Em outros SGBDs, é necessário incluir explicitamente o comando *commit* ao final da transação. A ausência desse comando impede que as alterações sejam efetivamente gravadas no banco de dados.
> - Essa diferença de comportamento depende da configuração e da implementação específica de cada SGBD.

## 2. DIAGRAMA DE ESTADOS DE UMA TRANSAÇÃO

- **Ativa:** Estado inicial, enquanto a transação está em execução.

- **Parcialmente Confirmada (Partial Commit):** Após a execução da última operação, mas antes da confirmação definitiva.

- **Comitada (Committed):** Após a confirmação bem-sucedida da transação.

- **Falha (Failed):** Quando a transação não pode prosseguir devido a um erro.

- **Abortada (Aborted):** Após a transação ser desfeita (*rollback*) e o BD retornar ao estado anterior.

> ### 2.1 Fluxo
> - Caso ocorra algum problema durante o processo, a transação entra em estado de falha e é abortada.
> - Durante a execução, pode haver confirmações parciais (*partial commits*), à medida que algumas operações são validadas.
> - Ao final, se todas as operações forem concluídas com sucesso, ocorre o *commit*, confirmando permanentemente as alterações no banco de dados.

## 3. PROPRIEDADES DE UMA TRANSAÇÃO (ACID)

- **ATOMICIDADE:** Uma transação é uma unidade atômica de processamento; ou é realizada integralmente ou não é realizada. Todas as operações contidas nela devem ser concluídas integralmente; caso ocorra alguma falha, nenhuma modificação é mantida, e o banco de dados retorna ao estado anterior à transação.

- **CONSISTÊNCIA:** Uma transação é consistente se levar o banco de dados de um estado consistente para outro estado também consistente. A transação deve levar o banco de um estado consistente para outro também consistente, sem gerar dados inválidos.

- **ISOLAMENTO:** A execução de uma transação não deve sofrer interferência de quaisquer outras transações que estejam sendo executadas concorrentemente. Mesmo com múltiplas transações em execução, o sistema deve garantir que o resultado final seja equivalente ao que ocorreria se cada uma fosse executada de forma sequencial.

- **DURABILIDADE (persistência):** As alterações aplicadas ao banco de dados, por meio de uma transação confirmada, devem persistir no banco de dados, não sendo perdidas por nenhuma falha. Os dados confirmados permanecem armazenados de forma segura e não se perdem.

> ### 3.1 Importância para Concursos
> - As propriedades ACID são essenciais para garantir a integridade das transações em bancos de dados e são frequentemente cobradas em concursos e certificações de TI.
> - O cumprimento das propriedades ACID é essencial para manter a integridade e a confiabilidade dos dados em sistemas transacionais e representa um dos pilares da segurança em bancos de dados relacionais.

## 4. TIPOS DE FALHAS

- **Falha do computador (*System Crash*):** Colapso do Sistema. Erro de Hardware, Software ou Rede.

- **Erro de Transação ou de sistema:** Overflow, Divisão por Zero, erros lógicos. Erros locais ou condições de exceção detectados pela transação. Condições de cancelamento. Exemplo: Dados não encontrados, saldo insuficiente, exceções programadas.

- **Imposição do controle de concorrência:** Bloqueios, situações de impasse (*Deadlocks*).

- **Falha de Disco:** Quebra do cabeçote de leitura, perda de blocos.

- **Problemas Físicos ou Catástrofes:** Incêndio, Falta de energia, sabotagem.

## 5. TRANSAÇÕES CONCORRENTES

### 5.1 Modelo Simplificado

- **read_item (X):** Lê um item X do BD e transfere para uma variável X de memória.

- **write_item (X):** Escreve o valor de uma variável X de memória em um item X do BD.

- A simultaneidade dessas operações pode gerar conflitos e inconsistências se não for devidamente controlada.

### 5.2 Problemas Causados por Transações Concorrentes

- **Perda de atualização:** Quando duas transações modificam o mesmo dado, e a alteração feita por uma delas é sobrescrita pela outra. Uma transação pode salvar um valor, que é posteriormente substituído pela outra transação, resultando na perda da primeira modificação realizada.

- **Atualização temporária (ou leitura suja - *Dirty Read*):** Quando uma transação lê dados modificados por outra transação que ainda não foi confirmada (*commit*). Se essa segunda transação falhar e for desfeita (*rollback*), o valor lido inicialmente pela primeira transação torna-se inválido.

- **Leitura não repetitiva (*Non-repeatable Read*):** Quando uma transação lê o mesmo dado mais de uma vez e obtém valores diferentes devido à interferência de outra transação. A primeira leitura retorna um valor inicial, enquanto a segunda leitura reflete uma modificação feita por outra transação.

- **Leitura fantasma (*Phantom Read*):** Quando, ao repetir uma consulta, surgem registros adicionais que antes não estavam presentes, devido à inserção de novos dados por outra transação. Diferentemente da leitura não repetitiva, em que uma variável é alterada, na leitura fantasma surgem novos registros que não existiam na consulta inicial.

### 5.3 Problemas Clássicos - Resumo

| Problema | O que é |
|----------|---------|
| Dirty Read | Leitura de dados ainda não confirmados (não comitados). |
| Non-repeatable Read | A mesma consulta retorna resultados diferentes dentro da mesma transação. |
| Phantom Read | Uma transação vê registros que não existiam em uma leitura anterior. |

> ### 5.3.1 Observações do Professor
> - A leitura fantasma é menos comum em provas e concursos, mas é importante entender que representa a inconsistência causada pela aparição inesperada de novos dados durante a execução de uma transação.
> - No estudo sobre gerenciamento de transações, é comum que as questões abordem problemas relacionados à execução concorrente, como leitura suja e falta de serialização, e não apenas comandos como *commit* e *rollback*.
> - Esses temas são frequentemente cobrados em avaliações, sendo essenciais para compreender o comportamento correto das transações em ambientes concorrentes.

## 6. CONTROLE DE CONCORRÊNCIA

- Os problemas surgem na ausência de mecanismos adequados de controle de concorrência nas transações.

- Para solucioná-los, utilizam-se técnicas de controle, como o escalonamento de transações, que garante que as operações sejam executadas de forma a preservar a integridade dos dados.

- Embora as transações possam parecer ocorrer simultaneamente, na prática o processador executa as operações sequencialmente, o que permite controlar o acesso concorrente.

- Os comandos básicos relacionados às transações incluem o *commit*, que confirma as alterações, e o *rollback*, que desfaz operações. Também existem pontos de salvamento (*savepoints*) para marcar estados intermediários.

- Esses comandos fazem parte da linguagem de manipulação de transações (DTL - *Data Transaction Language*).