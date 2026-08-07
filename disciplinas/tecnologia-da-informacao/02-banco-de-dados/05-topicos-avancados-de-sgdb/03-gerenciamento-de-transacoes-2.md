# Gerenciamento de Transações 2

## 1. Seriabilidade de Escalonamentos
- A seriabilidade de escalonamento refere-se à possibilidade de executar transações em uma ordem que não comprometa a consistência dos dados.
- Um escalonamento é serial quando todas as operações de uma transação são executadas de forma consecutiva, sem intercalação com operações de outras transações.
  - Exemplo: Escalonamento SA (T1 seguida de T2) e SB (T2 seguida de T1).
  - No exemplo do arquivo, com X=90, Y=90, N=3, M=2, ambos os escalonamentos seriais resultam em X=89 e Y=93.
- Se a alteração da ordem das transações modificar o resultado final, o escalonamento é classificado como não serial.
- Um escalonamento S de N transações é considerado serializável quando é equivalente a algum escalonamento serial dessas mesmas N transações.
  - A equivalência, neste contexto, significa que a ordem das operações conflitantes é mantida, gerando o mesmo resultado final.

### 1.1 Análise de Escalonamentos
- O escalonamento SC, com a sequência R1(X); R2(X); W1(X); W2(X); R1(Y); W1(Y), resulta em X=92 e Y=93.
  - Este resultado é diferente dos escalonamentos seriais (SA e SB), portanto, SC não é serializável.
- O escalonamento SD, com a sequência de ações entrelaçadas, resulta em X=89 e Y=93.
  - Este resultado é idêntico ao dos escalonamentos seriais, portanto, SD é serializável.
- A análise da serializabilidade verifica se a execução paralela de transações mantém a consistência do banco de dados, assegurando que o resultado seja equivalente ao de uma execução estritamente sequencial.

## 2. Controle de Concorrência
- Para garantir a serializabilidade e evitar inconsistências como as vistas no escalonamento SC, são adotados mecanismos de controle de concorrência.
- As duas principais estratégias de controle de concorrência são a otimista e a pessimista.
- A técnica mais comum é a aplicação de bloqueios (LOCK) nos itens de dados, que sincroniza o acesso entre as transações concorrentes.

### 2.1 Bloqueio Binário
- O bloqueio binário admite apenas dois estados para um item de dado: bloqueado (LOCK) ou desbloqueado (UNLOCK).
- Opera com o princípio de exclusão mútua: se um item X for bloqueado por uma transação Ti, nenhuma outra transação Tj poderá acessá-lo até que Ti o desbloqueie.
  - Transações que tentarem acessar um item bloqueado entram em uma fila de espera.
- Exemplo de Aplicação:
  - T1: LOCK(Y), read(Y), UNLOCK(Y), LOCK(X), read(X), UNLOCK(X).
  - T2: LOCK(X), read(X), write(X), UNLOCK(X), LOCK(Y), read(Y), write(Y), UNLOCK(Y).
- A principal desvantagem da estratégia pessimista (bloqueio binário) é a formação de filas de espera, o que pode comprometer o desempenho do sistema devido a gargalos.

### 2.2 Bloqueio Múltiplo ou Compartilhado/Exclusivo
- Esta estratégia diferencia os bloqueios em dois modos para maior eficiência:
  - Compartilhado (Read Lock): Permite que múltiplas transações leiam simultaneamente um item.
  - Exclusivo (Write Lock): Permite que apenas uma transação escreva em um item, bloqueando qualquer outro acesso.
- A estratégia considera que a leitura simultânea de dados inalterados não compromete a integridade.
- As operações são: read_lock(X), write_lock(X) e unlock(X).
- A implementação utiliza uma tabela de bloqueios que armazena:
  - Nome do item;
  - Tipo de bloqueio (read ou write);
  - Número de transações em leitura;
  - Identificação das transações com bloqueio;
  - Fila de espera.

| OPERAÇÃO | DESCRIÇÃO | CARACTERÍSTICA |
|----------|-----------|----------------|
| Read Lock (Leitura) | Bloqueia o item para leitura | Compartilhado |
| Write Lock (Escrita) | Bloqueia o item para escrita | Exclusivo |

> [!TIP] DICAS: 
> - Múltiplas leituras são permitidas simultaneamente. A fila de espera ocorre principalmente em operações de escrita.

## 3. Bloqueio em Duas Fases (Two-Phase Locking - 2PL)
- O protocolo de bloqueio em duas fases é amplamente utilizado em SGBDs para garantir a serializabilidade.
- A transação é dividida em duas fases:
  - Fase de expansão (crescimento): Todas as operações de bloqueio (lock) são emitidas.
  - Fase de contração (encolhimento): A partir da liberação do primeiro bloqueio (unlock), nenhum novo bloqueio pode ser adquirido.
- A regra fundamental do 2PL é: todas as operações de lock (read ou write) devem ocorrer antes da primeira operação de unlock.

## 4. Níveis de Isolamento
- Os SGBDs adotam configurações padrão para controlar a visibilidade dos dados entre transações, definindo os níveis de isolamento.
- O nível padrão mais comum é o Read Committed, que impede a leitura de dados não comitados.
- Os níveis de isolamento e suas características são:

| NÍVEL DE ISOLAMENTO | DESCRIÇÃO | ANOMALIAS PERMITIDAS |
|---------------------|-----------|----------------------|
| Read Uncommitted | Permite leitura de dados não comitados | Leitura suja, não repetível e fantasma |
| Read Committed | Permite apenas leitura de dados comitados | Leitura não repetível e fantasma |
| Repeatable Read | Garante que as mesmas leituras retornem os mesmos valores | Leitura fantasma |
| Serializable | Transações completamente isoladas; total serializabilidade | Nenhuma |

> [!CAUTION] OBSERVAÇÃO: 
> - O nível Serializable é o ideal, pois garante que a execução das transações seja equivalente a um escalonamento serial, independentemente da ordem.

## 5. Conceitos de Leitura
- Leitura Suja (Dirty Read): Ocorre quando uma transação lê dados que foram escritos por outra transação que ainda não foi confirmada (commit).
- Leitura Não Repetível (Non-repeatable Read): Ocorre quando uma transação lê o mesmo dado duas vezes e obtém valores diferentes, pois outra transação o modificou entre as leituras.
- Leitura Fantasma (Phantom Read): Ocorre quando uma transação reexecuta uma consulta e obtém um conjunto diferente de linhas, devido a operações de inserção ou exclusão realizadas por outra transação.

## 6. Conceito ACID
- Atomicidade: Garante que uma transação seja executada por completo ou não seja executada (tudo ou nada).
- Consistência: Garante que a transação leve o banco de dados de um estado consistente a outro.
- Isolamento: Garante que a execução de uma transação seja isolada de outras transações concorrentes.
- Durabilidade: Garante que, após o commit, as alterações de uma transação sejam permanentes, mesmo em caso de falha no sistema.

> [!TIP] DICAS: 
> - Os conceitos de leitura suja, não repetível e fantasma, juntamente com o ACID, são tópicos frequentemente cobrados em provas. Entender a relação entre os níveis de isolamento e quais anomalias eles previnem é crucial para a resolução de questões.