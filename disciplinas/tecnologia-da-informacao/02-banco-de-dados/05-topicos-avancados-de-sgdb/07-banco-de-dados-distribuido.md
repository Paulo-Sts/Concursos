# Banco de Dados Distribuído

## 1. Conceitos Fundamentais

### 1.1 Banco de Dados Distribuído
- É uma coleção de diversas bases de dados, interligadas logicamente mediante uma rede de computadores.
- Representa uma estratégia clássica de banco de dados relacional anterior ao advento de cloud computing e bancos NoSQL.
- O sistema de banco de dados distribuído faz integração via rede de computadores, com centralização da tecnologia de BD.

### 1.2 Sistema Gerenciador de Banco de Dados Distribuído
- É o sistema de software que possibilita a gerência da base de dados distribuída e torna a distribuição transparente para o usuário.

### 1.3 Características dos Sistemas Distribuídos
- Dados armazenados em nós.
- Processadores dos nós interconectados através de rede de computadores.
- O sistema possui todas as funcionalidades de um SGBD.
- Replicação: o sistema mantém várias cópias idênticas da relação e armazena cada uma em um local diferente.
- Fragmentação: o sistema divide a relação em vários fragmentos, armazenando-os em um local diferente.

> [!CAUTION] OBSERVAÇÃO: 
> - Com o advento da internet e do cloud computing, o banco de dados distribuídos não é mais implementado da forma tradicional.
> - Os Sistemas de Gerência de Bancos de Dados Distribuídos gerenciam transações dentro de uma rede, normalmente aplicativos que rodavam dentro de uma instituição.

## 2. Vantagens dos Sistemas Distribuídos
- Transparência na Gerência dos Dados Distribuídos, Fragmentados e Replicados.
- Transparência de Fragmentação: os usuários não precisam saber como uma relação foi fragmentada.
- Transparência de Replicação: os usuários veem os objetos de dados como logicamente exclusivos.
- Transparência de Local: os usuários não sabem o local físico dos dados.
- Confiabilidade através de Transações Distribuídas.
- Aumento de Desempenho: a aplicação não fica parada.
- Facilidade de Expansão.

> [!TIP] DICAS: 
> - A replicação proporciona maior disponibilidade, menor problema de concorrência e maior sobrecarga na atualização de réplicas.
> - Uma desvantagem do commit distribuído é a complexidade da transação.

## 3. Fragmentação de Dados

### 3.1 Conceito Geral
- Uma relação R fragmentada é dividida em uma série de fragmentos R1, R2, ... Rn.
- Os fragmentos contêm informação suficiente para permitir a reconstrução da relação original R.
- Existem dois esquemas diferentes para fragmentar uma relação: Fragmentação Horizontal e Fragmentação Vertical.

### 3.2 Fragmentação Horizontal
- Uma relação R é particionada em uma série de subconjuntos, R1, R2, ..., RN.
- Cada tupla da relação R precisa pertencer a pelo menos um dos fragmentos.
- A relação original pode ser reconstruída quando necessário.
- A fragmentação horizontal de uma relação é um subconjunto das tuplas que pertencem a um fragmento especificado por uma condição sobre um ou mais atributos da relação.

> [!TIP] DICAS: 
> - A fragmentação pode ser uma ótima solução para a quantidade de registros.

### 3.3 Fragmentação Vertical
- Envolve a definição de vários subconjuntos de atributos, R1, R2, ..., RN, do esquema R.
- R é formado pela união desses subconjuntos.
- A fragmentação vertical divide uma relação segundo seus atributos, mantendo somente alguns atributos da relação.

### 3.4 Exemplo de Fragmentação

| CPF(PK) | NOME | CURSO | ENDERECO | TELEFONE |
|---------|------|-------|----------|----------|
| 12345 | João | Direito | Rua X | 111111 |
| 45678 | Maria | Odonto | Rua Y | 222222 |
| 78945 | José | Farmácia | Rua Z | 333333 |
| 99988 | Antônio | Medicina | Ruz W | 444444 |
| 55229 | Marta | Computação | Rua K | 555555 |

Fragmentação Horizontal (exemplo: separação por curso):

| CPF(PK) | NOME | CURSO | ENDERECO | TELEFONE |
|---------|------|-------|----------|----------|
| 12345 | João | Direito | Rua X | 111111 |
| 45678 | Maria | Odonto | Rua Y | 222222 |
| 78945 | José | Farmácia | Rua Z | 333333 |

| CPF(PK) | NOME | CURSO | ENDERECO | TELEFONE |
|---------|------|-------|----------|----------|
| 99988 | Antônio | Medicina | Ruz W | 444444 |
| 55229 | Marta | Computação | Rua K | 555555 |

Fragmentação Vertical:

| CPF(PK) | NOME | CURSO |
|---------|------|-------|
| 12345 | João | Direito |
| 45678 | Maria | Odonto |
| 78945 | José | Farmácia |
| 99988 | Antônio | Medicina |
| 55229 | Marta | Computação |

| CPF(PK) | ENDERECO | TELEFONE |
|---------|----------|----------|
| 12345 | Rua X | 111111 |
| 45678 | Rua Y | 222222 |
| 78945 | Rua Z | 333333 |
| 99988 | Ruz W | 444444 |
| 55229 | Rua K | 555555 |

## 4. Commit em Duas Fases (Two-Phase Commit - 2PC)

### 4.1 Primeira Fase (Fase de Preparação)
- Os nós participantes da transação informam ao coordenador que já concluíram sua tarefa.
- O coordenador envia uma mensagem "preparar para commit".
- Cada nó grava em disco os registros de log e informações necessárias para recuperação local.
- Cada nó envia um sinal "OK" ao coordenador se tudo estiver certo; caso contrário, envia "não OK".
- Na ausência de uma resposta, o coordenador considera o nó "não OK".

### 4.2 Segunda Fase (Fase de Commit ou Rollback)
- Se todos os nós respondem "OK": a transação é realizada com sucesso e o coordenador envia um sinal "commit" para todos os nós.
- Caso contrário (algum nó responde "não OK"): a transação falha e o coordenador envia uma mensagem para "rollback".
- No rollback, a transação será desfeita utilizando-se os arquivos de log.

> [!TIP] DICAS: 
> - O Two-Phase Commit é um algoritmo frequentemente empregado para garantir que todos os participantes de uma transação distribuída tenham conhecimento do seu desfecho.
> - O Two-Phase Commit também é conhecido como atualização adiada.

> [!CAUTION] OBSERVAÇÃO: 
> - O coordenador não é responsável por gerenciar os bloqueios entre transações concorrentes; essa responsabilidade é do próprio SGBD.
> - O sistema pode se recuperar de uma falha em um link de comunicação que conecta sites, mesmo em caso de particionamento da rede.
> - Em um esquema que usa um site primário sem site de backup, caso o nó primário falhe, todas as transações em execução precisam ser abortadas.