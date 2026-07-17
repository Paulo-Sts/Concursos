# Anotações

# Blockchain

## 1.1 Conceito Fundamental

- **Blockchain** é um tipo de **DLT** (*Distributed Ledger Technology*) – tecnologia de registro distribuído, também compreendida como um **livro-razão digital**.
- Consiste em um **banco de dados descentralizado e distribuído**, no qual múltiplos computadores (participantes da rede) mantêm cópias idênticas.
- Os blocos de dados são encadeados de forma **sequencial** e ligados **criptograficamente** por meio de funções *hash*.
- Todo blockchain é uma DLT, mas **nem toda DLT constitui um blockchain**.

> [!CAUTION] OBSERVAÇÃO
> **O blockchain NÃO é um banco de dados tradicional.** É um tipo de DLT, com características próprias de descentralização, imutabilidade e transparência.

## 1.2 Características Fundamentais

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **Descentralização** | Rede opera em modelo P2P (*Peer-to-Peer*); sem ponto único de falha ou controle central |
| **Imutabilidade** | Uma vez gravado, o dado não pode ser alterado ou deletado sem consenso da rede |
| **Transparência** | Participantes com permissão podem visualizar todo o histórico de transações |

### 1.2.1 Descentralização
- Elimina a necessidade de uma **autoridade central** para validar transações.
- A "verdade" não reside em um servidor central, mas na **rede**.
- Cada participante mantém uma cópia do *ledger* completo.

### 1.2.2 Imutabilidade
- Cada bloco contém o *hash* do bloco anterior.
- Qualquer alteração em um bloco compromete toda a cadeia subsequente (os *hashes* deixam de corresponder).
- **Não é possível** que a entidade que inseriu um registro o altere posteriormente, independentemente de justificativa.

### 1.2.3 Transparência
- Todas as transações são **visíveis para todos os usuários com permissão**.
- Ferramentas chamadas **exploradores de blocos** permitem visualização das transações registradas.
- O acesso ao conteúdo detalhado depende das **chaves privadas** correspondentes.

## 1.3 Estrutura do Bloco

### 1.3.1 Cabeçalho (*Header*) – "O Cérebro"
Responsável pela **integridade criptográfica, metadados e consenso**. É aqui que ocorre a **validação**.

| CAMPO | DESCRIÇÃO |
|-------|-----------|
| **Versão** | Identificador do software utilizado |
| **Timestamp** | Registro imutável do momento de criação (Unix time) |
| **Dificuldade (Target/nBits)** | Define a complexidade do problema criptográfico a ser resolvido |
| **Hash Anterior** | Ponteiro para o bloco pai (garante o encadeamento) |
| **Merkle Root** | Hash raiz que resume criptograficamente todas as transações do bloco |

### 1.3.2 Corpo (*Body*) – "O Arquivo"
- Contém a **lista de transações** registradas.
- Inclui transações do tipo ***coinbase*** (criação de novas unidades e recompensa ao minerador).
- Pode conter **contratos inteligentes** (*smart contracts*).

### 1.3.3 Merkle Root
- **Hash raiz** resultante da combinação hierárquica dos *hashes* das transações.
- **Compactação:** resume milhares de transações em uma única *string* de 32 *bytes*.
- **Prova de inclusão:** permite verificar se uma transação específica está no bloco sem baixar todo o histórico.

### 1.3.4 Hash
- **Impressão digital criptográfica** que identifica um bloco e todo o seu conteúdo.
- É **único** – qualquer alteração mínima no conteúdo altera drasticamente o *hash* (**Efeito Avalanche**).

### 1.3.5 Nonce
- Valor que os mineradores ajustam para tentar encontrar um *hash* válido para o bloco.

## 1.4 O Encadeamento (*The Chain*)

- **Arquitetura de referência cruzada:**
  - O Bloco 2 contém o *hash* do Bloco 1.
  - O Bloco 3 contém o *hash* do Bloco 2.
- Isso cria uma **ordem cronológica e linear inquebrável**.

### 1.4.1 Detecção de Violação
1. Ao alterar dados no Bloco A, o *hash* muda.
2. O Bloco B não reconhece mais o *hash* do Bloco A.
3. A corrente se quebra e a **rede rejeita a versão adulterada**.

> [!TIP] DICAS
> - **O saldo das carteiras NÃO é armazenado diretamente nos blocos.** O saldo é **calculado** a partir do histórico de transações registradas ao longo da cadeia.
> - A segurança e a confiabilidade do blockchain **não dependem** de uma terceira parte mediadora.

## 1.5 Ataque de 51%
- Agente que controla **mais de 50% dos nós da rede** pode alterar registros.
- Possibilidade **remota**, mas tecnicamente viável.
- Por isso, **não se pode afirmar que blockchains são absolutamente imunes a falhas**.

## 1.6 Blockchain x DLT

| ASPECTO | DLT | BLOCKCHAIN |
|---------|-----|------------|
| **Conceito** | Conjunto de tecnologias de registro distribuído | Implementação específica de DLT |
| **Estrutura** | Pode variar | Dados organizados em blocos encadeados |
| **Relação** | Todo blockchain é uma DLT | Nem toda DLT é um blockchain |

## 1.7 Tabela Resumo – Blockchain

| ASPECTO | CARACTERÍSTICA |
|---------|----------------|
| **Tipo** | DLT (*Distributed Ledger Technology*) |
| **Estrutura** | Cadeia linear de blocos |
| **Componentes** | Cabeçalho (validação) + Corpo (transações) |
| **Segurança** | Criptografia + consenso distribuído |
| **Principais características** | Descentralização; imutabilidade; transparência |
| **Chaves** | Sistema de chaves públicas e privadas |
| **Validação** | Consenso da rede (não depende de terceiros) |

---

# Questões de Fixação

## Questão 01
(QUADRIX/2023/CRO SC/TÉCNICO EM INFORMÁTICA)

No que diz respeito às novas tecnologias, julgue o item.

A tecnologia Blockchain baseia-se no conceito de DLT (Distributed Ledger Technology) – um livro-razão distribuído.

**Gabarito:** C (Correto)

## Questão 02
(FUNCERN/2025/IF PE/PROFESSOR EBTT/SISTEMAS DIGITAIS E SEGURANÇA DE DADOS)

A tecnologia blockchain vem ganhando popularidade em virtude de sua aplicação nas redes utilizadas por criptomoedas, como o Bitcoin. A respeito dessa tecnologia, é correto afirmar que as blockchains

a) não sofrem com problemas de insegurança.
b) são muito rápidas e eficientes.
c) garantem a integridade dos dados, mas não garantem a imutabilidade.
d) são bancos de dados tradicionais distribuídos.
e) são tipos de Distributed Ledger Technology.

**Gabarito:** e

## Questão 03
(CESGRANRIO/2024/BNB/ANALISTA BANCÁRIO)

O blockchain é uma tecnologia de registro distribuído que facilita o armazenamento, a validação e o rastreamento de informações em um "livro contábil" eletrônico.

A tecnologia do blockchain é caracterizada por registros

a) centralizados e privados.
b) acessíveis a não-membros da rede autorizada.
c) mutáveis e reversíveis.
d) ocultos aos demais membros da rede autorizada.
e) cronológicos, imutáveis e transparentes.

**Gabarito:** e

## Questão 04
(FGV/2024/TJ MT/ANALISTA JUDICIÁRIO/TECNOLOGIA DA INFORMAÇÃO)

A Blockchain é uma tecnologia conhecida por sua segurança e transparência. Uma de suas principais características é a descentralização, que elimina a necessidade de uma autoridade central para validar as transações.

Um conceito diretamente relacionado a essa característica da Blockchain é o de

a) Contratos Inteligentes.
b) Mineração de Dados.
c) Machine Learning.
d) Tokens de Utilidade.
e) Livro-razão distribuído.

**Gabarito:** e

## Questão 05
(CESGRANRIO/2023/BANCO DO BRASIL/AGENTE DE TECNOLOGIA/MICRORREGIÃO 158/TI)

No sistema financeiro contemporâneo, o uso de tecnologias blockchain é considerado revolucionário, porque

a) possibilita o armazenamento e compartilhamento de dados de forma distribuída, criptografada e sem a intermediação de terceiros.
b) envolve múltiplos intermediários financeiros, mas mantém a centralização das informações em apenas um deles.
c) permite a quebra do sigilo inerente às transações financeiras.
d) elimina as práticas ilegais em curso nas transações financeiras, por meio do uso de linguagem criptografada.
e) privilegia a linguagem analógica, em detrimento da digital.

**Gabarito:** a

## Questão 06
(CESPE CEBRASPE/2023/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/DESENVOLVIMENTO DE SOFTWARE)

Acerca de blockchain, conceitos de inteligência artificial, arquitetura hexagonal e gestão de conteúdo, julgue o item a seguir. A garantia de segurança e confiabilidade de um blockchain é feita por meio de uma terceira parte mediadora, cuja confiabilidade é publicamente aceita.

**Gabarito:** E (Errado) - A segurança e a confiabilidade do blockchain **não dependem** de terceira parte mediadora.

## Questão 07
(FGV/2025/CPRM/ANALISTA EM GEOCIÊNCIAS/ARQUIVOLOGIA)

A blockchain é uma tecnologia de registro distribuído que funciona como um livro-razão digital, descentralizado e imutável. Cada informação registrada é organizada em blocos encadeados por meio de criptografia, de forma que, uma vez inserida, não pode ser alterada sem que se modifiquem todos os blocos subsequentes.

Assinale a opção que indica uma característica específica da blockchain.

a) Depende de uma autoridade central para validar transações e garantir a integridade dos dados.
b) Assegura a rastreabilidade completa das operações de registrado na cadeia.
c) Autoriza a edição retroativa de informações desde que haja consenso entre usuários.
d) Apresenta incompatibilidade com aplicações institucionais, pois depende de redes abertas e anônimas.
e) Garante a preservação sistêmica de documentos, substituindo as práticas tradicionais de custódia.

**Gabarito:** b

## Questão 08
(CESPE CEBRASPE/2025/BDMG/ANALISTA DE DESENVOLVIMENTO/SISTEMAS, ARQUITETURA E SOLUÇÃO DE DADOS)

Considerando as tendências de mercado, julgue o item que se segue. Na tecnologia blockchain, as partes podem fazer inserções e consultas, sem a necessidade de replicação entre elas.

**Gabarito:** E (Errado) - Não é possível realizar inserções ou consultas sem replicação entre os participantes.

## Questão 09
(CESPE CEBRASPE/2025/BDMG/ANALISTA DE DESENVOLVIMENTO – SISTEMAS, ARQUITETURA E SOLUÇÃO DE DADOS)

Considerando as tendências de mercado, julgue o item que se segue.

Nas aplicações que usam blockchain, a entidade que inseriu um registro pode alterá-lo, sem necessidade de consentimento de outra parte, desde que devidamente justificado.

**Gabarito:** E (Errado) - Não é possível alterar um registro após sua inserção, em razão da **imutabilidade**.

## Questão 10
(CESPE CEBRASPE/2024/CNJ/TÉCNICO JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: PROGRAMAÇÃO DE SISTEMAS)

No que se refere a blockchain, julgue o próximo item.

Na rede de blockchain, todas as transações são visíveis para todos os usuários com permissão, e todos os envolvidos podem ter uma cópia do ledger completo.

**Gabarito:** C (Correto)

## Questão 11
(CESPE CEBRASPE/2024/CNJ/TÉCNICO JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: PROGRAMAÇÃO DE SISTEMAS)

No que se refere a blockchain, julgue o próximo item.

O blockchain não possui uma autoridade centralizada para supervisionar as atividades, pois se baseia em princípios de criptografia, descentralização e consenso para garantir a confiança nas transações.

**Gabarito:** C (Correto)

## Questão 12
(CESGRANRIO/2024/CAIXA/TÉCNICO BANCÁRIO NOVO/RIO GRANDE DO SUL)

Um desenvolvedor foi contratado por uma empresa de inovação e, no seu primeiro dia de trabalho, foi alocado em uma equipe que estava desenvolvendo a blockchain de um banco. Ao ser questionado por um de seus colegas de trabalho sobre as características dessa tecnologia, esse desenvolvedor respondeu que blockchain

a) utiliza chaves simétricas para garantir a segurança e a privacidade das transações.
b) é sempre pública e, por isso, permite que qualquer pessoa veja todas as transações realizadas na rede.
c) é uma tecnologia centralizada, onde todos os dados são armazenados em um único servidor central para garantir a segurança.
d) é uma tecnologia projetada exclusivamente para armazenar contratos inteligentes e, por isso, não pode ser usada para transações financeiras.
e) apresenta como um de seus benefícios a imutabilidade dos dados, o que significa que, uma vez registrados, os dados não podem ser alterados ou excluídos.

**Gabarito:** e

## Questão 13
(CESPE CEBRASPE/2025/BDMG/ANALISTA DE DESENVOLVIMENTO/SISTEMAS, ARQUITETURA E SOLUÇÃO DE DADOS)

Julgue o próximo item, a respeito de blockchain e inteligência artificial.

Em blockchain, ledger é um banco de dados distribuído, no qual os participantes podem inserir novas transações e alterar e excluir transações já registradas.

**Gabarito:** E (Errado) - O *ledger* permite inserir novas transações, mas **não permite alterar ou excluir** transações já registradas.

## Questão 14
(CESPE CEBRASPE/2025/EMBRAPA/PESQUISADOR/ÁREA: CIÊNCIAS EXATAS E DA TERRA/SUBÁREA: GEOPROCESSAMENTO)

A respeito de tecnologias emergentes para a agricultura sustentável, julgue o item a seguir. As tecnologias blockchain ainda são ferramentas limitadas na tecnologia de precisão, porque interferências externas dos usuários podem enfraquecer a segurança do sistema por meio da descentralização dos dados.

**Gabarito:** E (Errado) - A descentralização **não enfraquece** a segurança do sistema; pelo contrário, é uma das características que fortalecem a segurança.

## Questão 15
(FGV/2025/DPE RO/ANALISTA PROGRAMADOR/CLASSE B)

A infraestrutura blockchain mantém cadeias de blocos, que representam a construção básica na infraestrutura. Estes blocos são constituídos de cabeçalho e corpo.

No cabeçalho de um bloco o componente (OU ESTRUTURA DE CAMPO) Nbits representa

a) o hash criptográfico do bloco anterior na cadeia.
b) um campo que representa a dificuldade de mineração.
c) uma estrutura de dados usada para resumir todas as transações no bloco de forma eficiente e segura.
d) uma marca temporal que indica quando o bloco foi minerado.
e) um valor que os mineradores ajustam para tentar encontrar um hash válido para o bloco.

**Gabarito:** b - O campo **nBits** representa a **dificuldade de mineração**.

## Questão 16
(FGV/2024/DATAPREV/ATI/DESENVOLVIMENTO DE SOFTWARE)

Em um sistema de blockchain tradicional, cada bloco armazena informações importantes para garantir a integridade e a validação das transações. Considerando a estrutura de blockchains públicas como Bitcoin e Ethereum, o elemento que não é armazenado diretamente em um bloco

a) é o Hash do bloco anterior.
b) são as Assinaturas digitais das transações.
c) é o Registro de saldo das carteiras participantes.
d) é o Timestamp (carimbo de tempo).
e) são os Dados das transações.

**Gabarito:** c - O **saldo das carteiras** não é armazenado diretamente nos blocos; é **calculado** a partir do histórico de transações.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | e |
| 03 | e |
| 04 | e |
| 05 | a |
| 06 | E |
| 07 | b |
| 08 | E |
| 09 | E |
| 10 | C |
| 11 | C |
| 12 | e |
| 13 | E |
| 14 | E |
| 15 | b |
| 16 | c |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Alexandre Kessler De Almeida.*