# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - GERENCIAMENTO DE TRANSAÇÕES II

## 1. SERIABILIDADE DE ESCALONAMENTOS

- Seriabilidade de escalonamento refere-se à possibilidade de se executar transações em determinada ordem sem comprometer a consistência dos dados.

- Um escalonamento é dito **serial** quando, para todas as transações participantes, todas as operações de uma transação são executadas de forma consecutiva, ou seja, sem intercalação com operações de outras transações.

- No escalonamento serial, uma transação é executada integralmente antes do início da próxima, independentemente da ordem T1-T2 ou T2-T1.

- Um escalonamento é **não serial** quando as operações das transações são intercaladas.

- Um escalonamento S de N transações é considerado **serializável** quando é equivalente a algum escalonamento serial dessas mesmas N transações. Mesmo que o escalonamento não seja serial, pode ser considerado serializável se os resultados finais forem equivalentes aos de um escalonamento serial.

> ### 1.1 Equivalência de Escalonamentos
> - Dois escalonamentos são considerados **equivalentes em conflitos** quando a ordem das operações conflitantes é mantida em ambos.
> - Operações conflitantes são aquelas que acessam o mesmo item de dado e pelo menos uma delas é uma operação de escrita.

### 1.2 Análise dos Escalonamentos Exemplo (X=90, Y=90, N=3, M=2)

- **SA (Serial - T1 depois T2):** T1 executa completamente (X=87, Y=93), depois T2 executa (X=89). Resultado final: X=89, Y=93.

- **SB (Serial - T2 depois T1):** T2 executa completamente (X=92), depois T1 executa (X=89, Y=93). Resultado final: X=89, Y=93.

- **SC (Não serializável):** R1(X); R2(X); W1(X); W2(X); R1(Y); W1(Y). Resultado final: X=92, Y=93. A alteração na ordem das operações resultou em valores finais diferentes dos obtidos em escalonamentos seriais.

- **SD (Serializável):** T1 lê X (90), escreve X (87); T2 lê X (87), escreve X (89); T1 lê Y (90), escreve Y (93). Resultado final: X=89, Y=93. Embora as transações estejam entrelaçadas, a equivalência ao resultado de um escalonamento serial é mantida.

> ### 1.3 Conclusão sobre os Exemplos
> - **SA** é um escalonamento serial.
> - **SB** também é serial, embora a ordem das transações seja invertida em relação ao SA.
> - **SC** não é serializável, pois a mudança na ordem das operações leva a um resultado diferente.
> - **SD** é considerado serializável, pois o resultado final é equivalente ao de um escalonamento serial.

- Quando a alteração da ordem de execução entre transações não interfere no resultado final, o escalonamento é considerado serial ou serializável.

- No escalonamento SC, uma das transações realiza a leitura de uma variável que já havia sido modificada por outra transação. Essa interferência altera o valor lido e, por consequência, o resultado final, descaracterizando a serializabilidade.

## 2. CONTROLE DE CONCORRÊNCIA

- Para evitar inconsistências como as observadas no escalonamento SC, utiliza-se o **controle de concorrência**.

- O controle de concorrência pode ser implementado por meio de duas estratégias principais:

  - **Estratégia otimista.**

  - **Estratégia pessimista.**

### 2.1 Bloqueio (LOCK)

- A técnica mais comum para controle de concorrência é a aplicação de **bloqueios** nos itens de dados, impedindo que múltiplas transações acessem simultaneamente um mesmo recurso de forma conflitante.

- O bloqueio é denominado **LOCK** e consiste na associação de uma variável a um item de dado, descrevendo seu estado quanto à possibilidade de ser alterado.

- O bloqueio serve para sincronizar o acesso aos dados entre as transações concorrentes.

## 3. BLOQUEIO BINÁRIO

- O bloqueio binário admite apenas dois estados:

  - **Lock (bloqueado).**

  - **Unlock (desbloqueado).**

- **lock_item(X):** Bloqueia o item X.

- **unlock_item(X):** Desbloqueia o item X.

- O bloqueio binário impõe a **exclusão mútua** no item de dado. Se o item X for bloqueado por uma transação Ti, nenhuma outra transação Tj poderá acessar o item X até que a transação Ti o desbloqueie.

- O processo de espera coloca a transação Tj em uma **fila de espera** pelo item X até que este seja desbloqueado por Ti.

- A exclusão mútua determina que, se um item de dado X estiver bloqueado por uma transação T1, nenhuma outra transação poderá acessar esse item até que ele seja desbloqueado.

- Esse comportamento impede que ocorra, por exemplo, a situação observada no escalonamento SC, em que uma transação realiza leitura de um valor que já havia sido alterado por outra.

### 3.1 Estratégia Pessimista

- A estratégia que consiste em bloquear todos os recursos de dados utilizados por uma transação é denominada **estratégia pessimista**.

- O principal problema dessa estratégia é a formação de **filas de espera** no banco de dados, uma vez que as demais transações ficam impedidas de prosseguir até que os bloqueios sejam desfeitos.

- Considerando que os sistemas de banco de dados executam milhares de transações simultâneas, o acúmulo de bloqueios pode comprometer significativamente o desempenho, criando gargalos na execução.

## 4. BLOQUEIO MÚLTIPLO OU COMPARTILHADO/EXCLUSIVO

- Como alternativa mais eficiente, adota-se a estratégia de **bloqueio múltiplo**, também conhecida como bloqueio compartilhado/exclusivo ou leitura/escrita.

- Essa técnica diferencia o acesso em dois modos:

  - **Compartilhado (leitura):** Permite que múltiplas transações acessem simultaneamente um item de dado para leitura, desde que nenhuma esteja tentando alterá-lo.

  - **Exclusivo (escrita):** Permite que apenas uma transação acesse o item de dado para gravação, impedindo que outras transações o leiam ou escrevam até que a operação seja concluída.

- Essa abordagem considera que a leitura de um dado inalterado não compromete a integridade da transação.

### 4.1 Operações do Bloqueio Múltiplo

- **Read Lock (bloqueio para leitura):** Bloqueia o item X para leitura, permitindo que outras transações também o leiam. Trata-se de um bloqueio compartilhado.

- **Write Lock (bloqueio para escrita):** Bloqueia o item X para gravação, impedindo qualquer outro tipo de acesso. Trata-se de um bloqueio exclusivo.

- **Unlock (desbloqueio):** Libera o item de dado, permitindo novos acessos.

### 4.2 Tabela de Bloqueios

- Para que esse tipo de controle funcione adequadamente, é necessária a utilização de uma **tabela de bloqueios**, que armazena as seguintes informações:

  - Nome do item de dado.

  - Tipo de bloqueio (*read lock* ou *write lock*).

  - Número de transações que estão realizando leitura.

  - Identificação das transações que possuem o bloqueio.

  - Fila de espera (quando aplicável).

> ### 4.3 Observação sobre a Fila de Espera
> - A fila de espera ocorre apenas em operações de escrita, pois múltiplas leituras podem ser feitas simultaneamente.
> - Se mais de uma transação tentar gravar no mesmo item, será necessário aguardar a liberação do bloqueio atual para que a próxima transação possa prosseguir.

## 5. BLOQUEIO EM DUAS FASES (TWO-PHASE LOCKING - 2PL)

- Para garantir que um escalonamento seja serializável, é necessário que as operações de bloqueio e desbloqueio obedeçam a determinadas regras.

- O protocolo de bloqueio em duas fases (*Two-Phase Locking* - 2PL) divide a transação em duas etapas:

  - **Fase de expansão (ou crescimento):** Todas as operações de bloqueio são emitidas.

  - **Fase de contração (ou encolhimento):** A partir da liberação do primeiro bloqueio, nenhum novo bloqueio pode ser adquirido.

- Portanto, **todas as operações de lock (*read* ou *write*) devem ocorrer antes da primeira operação de *unlock***.

- O 2PL é amplamente utilizado nos SGBDs para garantir a serializabilidade de transações.

- O 2PL assegura que o escalonamento produzido preserve a consistência dos dados.

## 6. NÍVEIS DE ISOLAMENTO

- Os SGBDs costumam adotar, por padrão, estratégias que impedem a leitura de dados não comitados. Essa configuração padrão é conhecida como ***Read Committed***, em que apenas valores efetivamente gravados no banco podem ser lidos por outras transações.

| Nível de Isolamento | O que permite | Problemas que evita |
|---------------------|---------------|---------------------|
| Read Uncommitted | Permite a leitura de dados ainda não comitados. | Não evita nenhum problema (leituras sujas, não repetíveis e fantasmas). |
| Read Committed | Permite apenas a leitura de dados comitados. | Evita leituras sujas, mas ainda permite leituras não repetíveis e fantasmas. |
| Repeatable Read | Garante que as mesmas leituras retornem os mesmos valores ao longo da transação. | Elimina leituras sujas e não repetíveis, mas ainda permite leituras fantasmas. |
| Serializable | Nível mais alto de isolamento. Transações completamente isoladas entre si. | Evita todos os tipos de anomalias e garante total serializabilidade. |

> ### 6.1 Relação com os Problemas de Concorrência
> - ***Read Uncommitted*:** Permite *Dirty Read*, *Non-repeatable Read* e *Phantom Read*.
> - ***Read Committed*:** Evita *Dirty Read*, mas permite *Non-repeatable Read* e *Phantom Read*.
> - ***Repeatable Read*:** Evita *Dirty Read* e *Non-repeatable Read*, mas permite *Phantom Read*.
> - ***Serializable*:** Evita todos os problemas (*Dirty Read*, *Non-repeatable Read* e *Phantom Read*).

## 7. RESUMO PARA CONCURSOS

- **Transações seriais:** T1 e T2, ou T2 e T1, produzem o mesmo resultado.

- **Transação serializável:** Apesar de não estar em ordem serial, é possível aplicar uma estratégia (como o 2PL) que torne sua execução equivalente a um escalonamento serial.

- O objetivo ideal é que as transações sejam **serializáveis**, de modo que sua execução não altere o resultado final, independentemente da ordem em que forem realizadas.

- O conceito **ACID** (Atomicidade, Consistência, Isolamento e Durabilidade) costuma ser cobrado de forma objetiva, sendo um conteúdo de assimilação simples.

> ### 7.1 Foco em Concursos
> - É fundamental compreender as estratégias de controle de concorrência, os tipos de leitura e os conceitos centrais sobre serialização de transações.
> - Na prática, é incomum que provas apresentem transações completas para análise, exceto em certames muito específicos da área de Tecnologia da Informação.
> - As questões abordam diretamente as estratégias de controle e os conceitos associados a:
>   - Leitura suja (*Dirty Read*).
>   - Leitura não repetível (*Non-repeatable Read*).
>   - Leitura fantasma (*Phantom Read*).
>   - Perda de atualização.
>   - Níveis de isolamento.
>   - Protocolo 2PL.