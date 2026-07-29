# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO – BANCO DE DADOS DISTRIBUÍDO

## 1. BANCO DE DADOS DISTRIBUÍDO (BDD)

- É uma coleção de diversas bases de dados, interligadas **logicamente** mediante uma **rede de computadores**.

- O Sistema Gerenciador de Banco de Dados Distribuído (SGBDD) é o sistema de software que possibilita a gerência da base de dados distribuída e torna a **distribuição transparente para o usuário**.

- Com o advento da internet e do *cloud computing*, o banco de dados distribuído tradicional não é mais implementado da mesma forma.

- Os SGBDDs gerenciam transações dentro de uma rede, normalmente aplicativos que rodavam dentro de uma instituição.

### 1.1 Características de Sistemas Distribuídos

| Característica | Descrição |
|----------------|-----------|
| **Replicação** | O sistema mantém várias cópias idênticas da relação e armazena cada uma em um local diferente. |
| **Fragmentação** | O sistema divide a relação em vários fragmentos, armazenando-os em locais diferentes. |
| Dados armazenados em nós | Os dados são distribuídos entre diferentes nós da rede. |
| Processadores interconectados | Os processadores dos nós são interconectados através de rede de computadores. |
| Funcionalidades de SGBD | O sistema possui todas as funcionalidades de um SGBD. |

> ### 1.2 Implementação Atual
> - A estratégia de banco de dados distribuído representa a centralização da tecnologia de BD antes do advento de *cloud computing* e de bancos NoSQL.
> - Com a evolução tecnológica, os conceitos foram adaptados para arquiteturas modernas, mas os fundamentos ainda são cobrados em concursos.

## 2. VANTAGENS DOS SISTEMAS DISTRIBUÍDOS

- **Transparência na Gerência dos Dados Distribuídos, Fragmentados e Replicados:**
  - **Transparência de Fragmentação:** os usuários não precisam saber como uma relação foi fragmentada.
  - **Transparência de Replicação:** os usuários veem os objetos de dados como logicamente exclusivos.
  - **Transparência de Local:** os usuários não sabem o local físico dos dados.

- **Confiabilidade através de Transações Distribuídas.**

- **Aumento de Desempenho** — a aplicação não fica parada.

- **Facilidade de Expansão.**

## 3. FRAGMENTAÇÃO DE DADOS

- Uma relação R fragmentada é dividida em uma série de fragmentos **R1, R2, ..., Rn**.

- Os fragmentos contêm informação suficiente para permitir a **reconstrução da relação original R**.

> ### 3.1 Finalidade da Fragmentação
> - A fragmentação pode ser uma ótima solução para o gerenciamento da quantidade de registros.
> - Permite distribuir os dados de forma mais eficiente entre os nós.

### 3.2 Fragmentação Horizontal

- Uma relação R é particionada em uma série de subconjuntos, **R1, R2, ..., RN**.

- Cada **tupla** da relação R precisa pertencer a **pelo menos um** dos fragmentos.

- A relação original pode ser reconstruída quando necessário.

**Exemplo:** A tabela completa é dividida em partes, cada uma contendo um subconjunto das tuplas (linhas).

### 3.3 Fragmentação Vertical

- Envolve a definição de vários subconjuntos de **atributos**, **R1, R2, ..., RN**, do esquema R.

- R é formado pela **união** desses subconjuntos de atributos.

**Exemplo:**

| CPF (PK) | Nome | Curso | Endereço | Telefone |
|----------|------|-------|----------|----------|
| 12345 | João | Direito | Rua X | 111111 |
| 45678 | Maria | Odonto | Rua Y | 222222 |
| 78945 | José | Farmácia | Rua Z | 333333 |
| 99988 | Antônio | Medicina | Ruz W | 444444 |
| 55229 | Marta | Computação | Rua K | 555555 |

**Fragmento Vertical 1 (Dados Pessoais):**

| CPF (PK) | Nome | Curso |
|----------|------|-------|
| 12345 | João | Direito |
| 45678 | Maria | Odonto |
| 78945 | José | Farmácia |
| 99988 | Antônio | Medicina |
| 55229 | Marta | Computação |

**Fragmento Vertical 2 (Contato):**

| CPF (PK) | Endereço | Telefone |
|----------|----------|----------|
| 12345 | Rua X | 111111 |
| 45678 | Rua Y | 222222 |
| 78945 | Rua Z | 333333 |
| 99988 | Ruz W | 444444 |
| 55229 | Rua K | 555555 |

> ### 3.4 Diferença entre Fragmentação Horizontal e Vertical
> - **Fragmentação Horizontal:** divisão por **linhas** (tuplas) — subconjunto das tuplas especificado por condição sobre atributos.
> - **Fragmentação Vertical:** divisão por **colunas** (atributos) — mantém somente alguns atributos da relação.

## 4. COMMIT EM DUAS FASES (TWO-PHASE COMMIT - 2PC)

- Algoritmo frequentemente empregado para garantir que **todos os participantes de uma transação distribuída tenham conhecimento do seu desfecho**.

### 4.1 Primeira Fase (Fase de Preparação)

- Os nós participantes da transação informam ao **coordenador** que já concluíram sua tarefa.

- O coordenador envia uma mensagem **"preparar para commit"**.

- Cada nó gravará em disco os registros de **log** e informações necessárias para recuperação local.

- Na sequência, envia um sinal **"OK"** ao coordenador, caso contrário envia um sinal **"não OK"**.

- Na ausência de uma resposta, o coordenador considera o nó **"não OK"**.

### 4.2 Segunda Fase (Fase de Commit ou Rollback)

| Condição | Ação do Coordenador |
|----------|---------------------|
| Todos os nós respondem "OK" | Envia sinal **"commit"** para todos os nós — transação realizada com sucesso. |
| Pelo menos um nó responde "não OK" | Envia sinal **"rollback"** para todos os nós — transação falha. |

- No caso de *rollback*, a transação será desfeita utilizando-se os **arquivos de log**.

> ### 4.3 Two-Phase Commit x Atualização Adiada
> - O *Two-Phase Commit* também é conhecido como **atualização adiada**.
> - Técnica de recuperação que posterça qualquer atualização real do banco de dados em disco até que uma transação atinja seu ponto de confirmação (*commit*).
> - A transação força a gravação do *log* em disco antes de gravar as atualizações no banco de dados.

## 5. QUESTÕES COMENTADAS

### Questão 01 (FCC/INFRAERO/2011)

**Análise das afirmativas:**

| Item | Análise |
|------|---------|
| I | ✅ Uma mesma tabela pode ser armazenada em mais de um servidor para aumentar a disponibilidade e o paralelismo. |
| II | ✅ A localização das réplicas deve considerar os locais e usuários que acessam os dados replicados com maior frequência. |
| III | ✅ Na fragmentação horizontal, cada fragmento contém um subconjunto das tuplas da relação completa e cada tupla precisa ser armazenada em pelo menos um servidor. |
| IV | ❌ Na fragmentação vertical, **os atributos** são distribuídos, não as tuplas. |

**Gabarito: c** (I, II e III)

### Questão 02 (FCC/DPE-RS/2017)

**Características da replicação de tabelas:**

| Característica | Efeito |
|----------------|--------|
| **Maior disponibilidade** | Vantagem da replicação |
| **Menor problema de concorrência** | Vantagem da replicação |
| **Maior sobrecarga na atualização de réplicas** | Desvantagem da replicação |

**Gabarito: e** (maior disponibilidade, menor problema de concorrência e maior sobrecarga na atualização de réplicas)

> ### Análise da Questão 02
> - A replicação proporciona **maior disponibilidade** porque os dados estão em múltiplos locais.
> - Proporciona **menor problema de concorrência** porque as leituras podem ser distribuídas entre as réplicas.
> - Causa **maior sobrecarga na atualização** porque todas as réplicas precisam ser atualizadas.

### Questão 03 (CESPE/MEC/2011)

**Análise do item:**

A fragmentação **horizontal** divide uma relação segundo seus atributos — **INCORRETO**

A fragmentação **vertical** de uma relação é um subconjunto das tuplas — **INCORRETO**

- ✅ **Fragmentação Vertical:** divide uma relação segundo seus **atributos**, mantendo somente alguns atributos da relação.
- ✅ **Fragmentação Horizontal:** subconjunto das **tuplas** que pertencem a um fragmento especificado por uma condição sobre um ou mais atributos da relação.

**Gabarito: E** (errado)

### Questão 04 (FGV/TJ-DFT/2022)

**Algoritmo empregado para garantir que todos os participantes de uma transação distribuída tenham conhecimento do seu desfecho:**

**Gabarito: e** (Two-phase commit)

### Questão 05 (FUNDATEC/BRDE/2023)

**Técnica de recuperação que posterça qualquer atualização real do banco de dados em disco até que uma transação atinja seu ponto de confirmação (commit):**

- O *Two-phase commit* também é conhecido como **atualização adiada**.

**Gabarito: c** (Atualização Adiada)

### Questão 06 (FUNDATEC/PROCERGS/2023)

**Análise das assertivas:**

| Item | Análise |
|------|---------|
| I | ❌ O coordenador **não** é responsável por gerenciar os bloqueios entre transações concorrentes. O gerenciamento dos bloqueios é feito pelo próprio SGBD. |
| II | ❌ O sistema **pode** se recuperar de uma falha em um link de comunicação que conecta sites caso haja um particionamento da rede. |
| III | ✅ Em um esquema que usa um site primário sem site de backup, caso o nodo primário falhe, todas as transações em execução precisam ser abortadas. |

**Gabarito: a** (Apenas III)

> ### Análise da Questão 06
> - O coordenador é responsável por coordenar apenas o **commit**, não os bloqueios.
> - O sistema pode se recuperar de falhas de comunicação, mesmo com particionamento de rede.
> - Sem site de backup, a falha do nodo primário força o abortamento de todas as transações em execução.