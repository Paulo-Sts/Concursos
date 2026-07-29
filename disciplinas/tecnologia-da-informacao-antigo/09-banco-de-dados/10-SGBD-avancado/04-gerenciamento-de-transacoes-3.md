# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - GERENCIAMENTO DE TRANSAÇÕES III

## 1. PROPRIEDADES ACID - APROFUNDAMENTO

### 1.1 Atomicidade

- Assegura que uma transação seja tratada como uma unidade indivisível.

- Todas as suas operações são executadas integralmente ou nenhuma delas ocorre.

- Garante que o banco de dados não fique em estado inconsistente.

- **Ou se faz tudo ou nada.**

### 1.2 Consistência

- Garante que a transação leve o banco de dados de um estado consistente para outro estado consistente.

- Respeita todas as regras e restrições definidas no banco de dados.

- **Sem problemas de integridade.**

### 1.3 Isolamento

- Assegura que transações concorrentes não interfiram umas nas outras.

- O resultado deve ser o mesmo como se elas fossem executadas sequencialmente.

- Garante que a transação seja encarada como uma unidade atômica de trabalho.

- Uma transação não deve influenciar as outras transações, evitando condições de erro.

### 1.4 Durabilidade

- Assegura que, uma vez confirmada a transação (*commit*), seus efeitos permanecem no banco.

- Mesmo em caso de falhas ou quedas do sistema, as alterações persistem.

- **Permanência da gravação no banco.**

> ### 1.5 ACID - Significado e Cobrança em Provas
> - **A**tomicidade: unidade indivisível de processamento.
> - **C**onsistência: banco de dados de um estado consistente para outro consistente.
> - **I**solamento: transações concorrentes não interferem entre si.
> - **D**urabilidade: efeitos de transações confirmadas persistem mesmo após falhas.
> - O acrônimo ACID é amplamente cobrado em concursos, especialmente em questões objetivas que exigem a correta associação de cada letra à sua definição.
> - As propriedades são interdependentes e complementares, trabalhando conjuntamente para garantir a correta execução e integridade dos dados.

## 2. PROBLEMAS DE CONCORRÊNCIA - APROFUNDAMENTO

### 2.1 Atualização Perdida (*Lost Update*)

- Ocorre quando duas transações acessam os mesmos dados de forma intercalada.

- Uma atualização realizada por uma transação é sobrescrita pela outra, resultando na perda da primeira modificação.

- Isso torna incorreto o valor de alguns itens do banco de dados.

### 2.2 Leitura Suja (*Dirty Read*) / Atualização Temporária

- Ocorre quando uma transação lê dados modificados por outra transação que ainda não foi confirmada (*commit*).

- Se a transação que modificou os dados falhar e for desfeita (*rollback*), o valor lido torna-se inválido.

- Ocorre quando duas transações que acessam os mesmos itens têm suas operações intercaladas de modo que isso torna incorreto o valor de alguns itens.

### 2.3 Leitura Não Repetitiva (*Non-Repeatable Read*)

- Ocorre quando uma transação lê um valor, este valor é alterado por outra transação, e ao ler novamente obtém um resultado diferente.

- A mesma consulta retorna resultados diferentes dentro da mesma transação.

### 2.4 Leitura Fantasma (*Phantom Read*)

- Ocorre quando, ao reler dados, uma transação percebe a presença de novos registros que não existiam na consulta anterior.

- Novos registros surgem devido a inserções feitas por outras transações.

> ### 2.5 Problemas Clássicos x Atualização Perdida
> - **Problemas clássicos:** leitura suja (*dirty read*), leitura não repetitiva (*non-repeatable read*) e leitura fantasma (*phantom read*).
> - A **atualização perdida** é um problema comum, mas não é considerada um problema clássico na literatura tradicional de banco de dados.
> - A leitura não repetitiva e a leitura fantasma se diferenciam porque:
>   - **Leitura não repetitiva:** um valor específico é alterado entre duas leituras.
>   - **Leitura fantasma:** novos registros aparecem em uma consulta repetida.

## 3. ESCALONAMENTOS - APROFUNDAMENTO

### 3.1 Definições

- **Plano (*Schedule*):** ordem de execução das operações das várias transações quando executadas concorrentemente de maneira intercalada.

- **Escalonamento Serial:** para cada transação T participante, todas as operações de T são executadas consecutivamente, ou seja, uma após a outra, sem sobreposição no tempo.

- **Escalonamento Serializável:** permite a execução concorrente das operações, desde que o resultado final seja equivalente a alguma sequência serial dessas transações.

- **Escalonamento Não Serial:** quando as operações são intercaladas entre as transações.

- **Escalonamento Não Serializável:** quando não é possível ordenar as ações das transações de forma a preservar a equivalência serial, comprometendo a integridade dos dados.

> ### 3.2 Distinção Importante para Provas
> - **Serial:** execução estritamente sequencial (uma transação completa antes da próxima começar).
> - **Serializável:** execução concorrente, mas com resultado equivalente a uma execução serial.
> - **Não serial:** execução intercalada (não sequencial), podendo ou não ser serializável.
> - **Não serializável:** execução intercalada que não produz resultado equivalente a nenhuma execução serial.

### 3.3 Classes de Isolamento

| Classe | Característica |
|--------|----------------|
| S.A. (Serial) | Execução estritamente sequencial das transações. |
| S.B. (Serializável) | Execução concorrente cujo resultado é equivalente a uma execução serial. |
| S.C. | Não garante equivalência serial e pode causar anomalias e inconsistências. |
| S.D. | Nível misto com comportamento próximo ao serial, permitindo certas interações. |

## 4. COMANDOS DE TRANSAÇÃO - APROFUNDAMENTO

### 4.1 COMMIT

- Utilizado para finalizar uma transação com sucesso.

- Torna permanentes todas as alterações de dados pendentes.

- A transação só é considerada finalizada após o *commit* ou *rollback*.

### 4.2 ROLLBACK

- Utilizado para desfazer todas as operações realizadas por uma transação que tenha falhado.

- A transação é revertida ao seu estado inicial.

- Garante que nenhuma alteração parcial permaneça no banco de dados.

- Mecanismo essencial para restaurar estados anteriores em situações de erro.

> ### 4.3 Finalização de Transações
> - **COMMIT:** finaliza com sucesso, confirmando as alterações.
> - **ROLLBACK:** finaliza com falha, desfazendo todas as alterações.
> - Os comandos *commit* e *rollback* são utilizados para finalizar uma transação.
> - A finalização da transação ocorre somente após o *commit* ou o *rollback*, assegurando a integridade e consistência dos dados.

## 5. BLOQUEIOS E CONTROLE DE CONCORRÊNCIA

### 5.1 Finalidade dos Bloqueios

- O bloqueio de dados é um mecanismo fundamental para controlar o acesso concorrente às tabelas em bancos de dados.

- Previne conflitos em consultas simultâneas realizadas por diferentes usuários ou aplicações.

- O bloqueio é gerado para contornar o conflito de consulta simultânea de tabelas.

### 5.2 Tipos de Bloqueio

- **Bloqueio Binário:** apenas dois estados (bloqueado/desbloqueado), com exclusão mútua.

- **Bloqueio Compartilhado (*Read Lock*):** permite múltiplas leituras simultâneas.

- **Bloqueio Exclusivo (*Write Lock*):** permite apenas uma transação por vez para escrita.

## 6. CLASSIFICAÇÃO DE TRANSAÇÕES

### 6.1 Quanto às Operações

- **Transação somente leitura (*Read-Only Transaction*):** inclui apenas operações de consulta (*SELECT*).

- **Transação de leitura e escrita (*Read-Write Transaction*):** inclui operações de inserção, deleção, modificação e consulta.

> ### 6.2 Definição de Transação
> - Transações em banco de dados incluem uma ou mais operações de acesso ao banco de dados.
> - Compreendem inserções, deleções, modificações e até operações de recuperação de dados, ou seja, de consulta.
> - Se as operações contidas em uma transação incluem somente consultas, a transação é denominada **read-only transaction**.
> - Caso contrário, a transação é denominada **read-write transaction**.

## 7. QUESTÕES COMENTADAS

### Questão 01 (2018/IADES/APEX)

**ACID significa: atomicidade, consistência, isolamento e durabilidade.**

**Gabarito: a**

### Questão 02 (2017/CESPE/TRF)

**A propriedade que garante que as transações não sejam afetadas pelo funcionamento umas das outras é o ISOLAMENTO, não a atomicidade.**

**Gabarito: E**

### Questão 03 (2017/FCC/DPE-RS)

**Durabilidade:** após uma transação ter sido finalizada com sucesso, suas alterações no banco de dados tornam-se persistentes, mesmo se houver queda ou falha do sistema.

**Gabarito: b**

### Questão 04 (2013/UFC)

**"Se uma transação é concluída com sucesso, então seus efeitos são persistidos" → Durabilidade.**

**"Ou todas as ações da transação acontecem, ou nenhuma delas acontece" → Atomicidade.**

**Gabarito: a**

### Questão 05 (2018/FADESP/BANPARÁ)

**Consistência:** sem problemas de integridade.

**Atomicidade:** em uma transação ou se faz tudo ou nada.

**Gabarito: b**

### Questão 06 (2010/CESPE/BANCO DA AMAZÔNIA)

**O isolamento de uma transação é uma propriedade que garante que a transação seja encarada como uma unidade atômica de trabalho: ou todas as suas modificações de dados são executadas ou nenhuma delas é executada.**

**Gabarito: C**

> ### Observação sobre a Questão 06
> - A banca associou o conceito de "unidade atômica de trabalho" ao isolamento, embora essa definição esteja mais diretamente ligada à atomicidade.
> - O isolamento foca em manter a separação entre transações concorrentes.
> - As propriedades são interdependentes e complementares, o que pode gerar confusão em provas quando as definições são apresentadas de forma integrada.

### Questão 07 (2014/CESPE/TJ/SE)

**Os comandos commit e rollback são utilizados para finalizar uma transação.**

**Gabarito: C**

### Questão 08 (CESPE/2022/PETROBRAS)

**O bloqueio de um banco de dados é gerado para contornar o conflito de consulta simultânea de tabelas por um usuário do aplicativo desenvolvido.**

**Gabarito: E** (embora a banca tenha considerado errado por conta de aspectos técnicos adicionais)

> ### Análise da Questão 08
> - A banca considerou a assertiva incorreta porque a afirmação é muito simplificada.
> - Existem diversos tipos e níveis de bloqueios (binário, compartilhado, exclusivo).
> - A herança de bloqueios ocorre no nível das operações sobre os dados, garantindo um gerenciamento adequado da concorrência.

### Questão 09 (FEPESE/2022/UDESC)

**Afirmativa 1:** correta - transações incluem uma ou mais operações de acesso ao banco.

**Afirmativa 2:** correta - read-only transaction e read-write transaction.

**Afirmativa 3:** incorreta - o acrônimo correto é ACID, não APCID.

**Gabarito: b**

### Questão 10 (2021/UFES)

**O problema descrito é a atualização perdida (*lost update*).**

**Gabarito: e**

### Questão 11 (IADES/2019/AL-GO)

**Quando todas as operações de T são executadas consecutivamente, o plano é chamado de serial.**

**Gabarito: c**