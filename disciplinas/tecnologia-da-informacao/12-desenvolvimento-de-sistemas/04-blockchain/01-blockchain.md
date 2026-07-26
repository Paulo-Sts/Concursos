# Blockchain (Conceitos, Mineração, Consenso e Smart Contracts)

## 1. Conceito Fundamental
- Blockchain é um tipo de DLT (Distributed Ledger Technology) – tecnologia de registro distribuído, também compreendida como um livro-razão digital.
- Consiste em um banco de dados descentralizado e distribuído, no qual múltiplos computadores (participantes da rede) mantêm cópias idênticas.
- Os blocos de dados são encadeados de forma sequencial e ligados criptograficamente por meio de funções hash.
- Todo blockchain é uma DLT, mas nem toda DLT constitui um blockchain.

> [!CAUTION] OBSERVAÇÃO: 
> - O blockchain NÃO é um banco de dados tradicional. É um tipo de DLT, com características próprias de descentralização, imutabilidade e transparência.

## 2. Características Fundamentais

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Descentralização | Rede opera em modelo P2P (Peer-to-Peer); sem ponto único de falha ou controle central. |
| Imutabilidade | Uma vez gravado, o dado não pode ser alterado ou deletado sem consenso da rede. |
| Transparência | Participantes com permissão podem visualizar todo o histórico de transações. |

### 2.1 Descentralização
- Elimina a necessidade de uma autoridade central para validar transações.
- A "verdade" não reside em um servidor central, mas na rede.
- Cada participante mantém uma cópia do ledger completo.

### 2.2 Imutabilidade
- Cada bloco contém o hash do bloco anterior.
- Qualquer alteração em um bloco compromete toda a cadeia subsequente (os hashes deixam de corresponder).
- Não é possível que a entidade que inseriu um registro o altere posteriormente, independentemente de justificativa.

### 2.3 Transparência
- Todas as transações são visíveis para todos os usuários com permissão.
- Ferramentas chamadas exploradores de blocos permitem visualização das transações registradas.
- O acesso ao conteúdo detalhado depende das chaves privadas correspondentes.

## 3. Estrutura do Bloco

### 3.1 Cabeçalho (Header) – "O Cérebro"
- Responsável pela integridade criptográfica, metadados e consenso. É aqui que ocorre a validação.

| CAMPO | DESCRIÇÃO |
|-------|-----------|
| Versão | Identificador do software utilizado. |
| Timestamp | Registro imutável do momento de criação (Unix time). |
| Dificuldade (Target/nBits) | Define a complexidade do problema criptográfico a ser resolvido. |
| Hash Anterior | Ponteiro para o bloco pai (garante o encadeamento). |
| Merkle Root | Hash raiz que resume criptograficamente todas as transações do bloco. |

### 3.2 Corpo (Body) – "O Arquivo"
- Contém a lista de transações registradas.
- Inclui transações do tipo coinbase (criação de novas unidades e recompensa ao minerador).
- Pode conter contratos inteligentes (smart contracts).

### 3.3 Merkle Root
- Hash raiz resultante da combinação hierárquica dos hashes das transações.
- Compactação: resume milhares de transações em uma única string de 32 bytes.
- Prova de inclusão: permite verificar se uma transação específica está no bloco sem baixar todo o histórico.

### 3.4 Hash
- Impressão digital criptográfica que identifica um bloco e todo o seu conteúdo.
- É único – qualquer alteração mínima no conteúdo altera drasticamente o hash (Efeito Avalanche).

### 3.5 Nonce
- Valor que os mineradores ajustam para tentar encontrar um hash válido para o bloco.

## 4. O Encadeamento (The Chain)
- Arquitetura de referência cruzada:
  - O Bloco 2 contém o hash do Bloco 1;
  - O Bloco 3 contém o hash do Bloco 2.
- Isso cria uma ordem cronológica e linear inquebrável.

### 4.1 Detecção de Violação
1. Ao alterar dados no Bloco A, o hash muda;
2. O Bloco B não reconhece mais o hash do Bloco A;
3. A corrente se quebra e a rede rejeita a versão adulterada.

> [!TIP] DICAS: 
> - O saldo das carteiras NÃO é armazenado diretamente nos blocos. O saldo é calculado a partir do histórico de transações registradas ao longo da cadeia.
> - A segurança e a confiabilidade do blockchain não dependem de uma terceira parte mediadora.

## 5. Mineração e Validação

### 5.1 Conceito de Mineração
- A mineração é o processo de validação das transações para colocar um bloco dentro da blockchain.
- Para isso, é necessário haver um consenso entre todos os participantes da rede peer-to-peer.
- Como consequência da inclusão de um bloco, há geração de novas moedas (recompensa) entregue a quem venceu o processo de mineração.
- A mineração é o mecanismo principal de segurança da rede – uma vez que as transações entram na blockchain, garantem-se as propriedades de imutabilidade, transparência e descentralização.

> [!CAUTION] OBSERVAÇÃO: 
> - A mineração não serve apenas para criar novas moedas – sua função principal é validar transações e garantir a segurança da rede.

### 5.2 O Ciclo da Mineração
1. Pegam-se as transações que estão no pool de transações;
2. Constrói-se um bloco candidato;
3. O hash é calculado;
4. Se for maior que o target, altera-se o nonce;
5. O nonce na função de hash gera um novo hash;
6. O hash deve ser menor, em número, que o target definido na construção do bloco candidato;
7. Quem achar o nonce primeiro resolve o problema criptográfico e ganha a chance de registrar o bloco.

### 5.3 Pools de Mineração
- Pools de mineração: grupos que trabalham cooperativamente para validar transações na blockchain, resolvendo cálculos complexos.
- Dividem, proporcionalmente, as recompensas de bloco entre si, de acordo com sua contribuição.

## 6. Mecanismos de Consenso

### 6.1 Proof of Work (PoW) – "Modelo Industrial"
- Contexto: Bitcoin
- Para registrar um bloco, os mineradores ajustam um número arbitrário (nonce) repetidamente até encontrar um hash de cabeçalho menor que o target.
- É um problema computacionalmente difícil de resolver, mas trivial de verificar.
- A segurança do PoW é baseada no gasto energético e de hardware.
- Exige investimento colossal em eletricidade e chips ASICs (especializados em mineração de Bitcoin).
- Ataque de 51%:
  - Quando uma pessoa controla mais da metade de todo o poder computacional global.
  - Consegue reescrever a história da blockchain.

### 6.2 Proof of Stake (PoS) – "Modelo Econômico"
- Contexto: Ethereum (migrou do PoW para o PoS)
- Mudança de paradigma: afasta-se da mineração e aproxima-se da validação.
- Substituição da energia elétrica (trabalho) pelo capital bloqueado (stake).
- É um sorteio para ver quem registra o bloco – não há competição computacional.

- Mecânica do Stake:
  1. Participantes bloqueiam criptomoedas como "bond" (aposta) – no Ethereum, são 32 ETH para cada bilhete;
  2. O protocolo seleciona pseudoaleatoriamente um validador – quem tem mais bilhetes tem mais chance;
  3. Um comitê valida a proposta do bloco;
  4. Slashing: se o indivíduo agir maliciosamente, parte ou todo o seu stake é confiscado.

> [!TIP] DICAS: 
> - PoW: baseado em hardware e eletricidade; segurança exógena (recursos do mundo real).
> - PoS: baseado em capital; segurança endógena (recursos da própria rede); consumo de energia baixo.

### 6.3 Quadro Comparativo – PoW x PoS

| ASPECTO | PROOF OF WORK (PoW) | PROOF OF STAKE (PoS) |
|---------|---------------------|----------------------|
| Base | Processamento/Hardware. | Capital bloqueado (stake). |
| Consumo de energia | Alto. | Baixo. |
| Recurso principal | Eletricidade + chips ASICs. | Moedas bloqueadas. |
| Risco | Investimento em hardware. | Perda de fundos (slashing). |
| Segurança | Exógena (mundo real). | Endógena (rede). |
| Exemplo | Bitcoin. | Ethereum. |

## 7. Smart Contracts (Contratos Inteligentes)

### 7.1 Conceito
- Lógica programável e autoexecutável registrada de forma imutável na blockchain.
- Não é papel – é código executável.
- Ao disparar um evento, executa automaticamente regras pré-definidas.
- Armazenados e replicados em todos os nós da rede.
- O Ethereum tem execução descentralizada por meio de smart contracts.

> [!CAUTION] OBSERVAÇÃO: 
> - "O código é a lei" – após a implantação, o código não pode ser alterado (exceção: arquiteturas de proxy).

### 7.2 Anatomia Técnica
- Regras de validação;
- Funções;
- Eventos;
- Estado.

### 7.3 Ciclo de Vida
1. Deploy: implanta-se o smart contract na blockchain;
2. Evento: dispara a execução;
3. Execução: o código roda;
4. Validação e registro: o resultado é validado e registrado na blockchain.

### 7.4 Propriedades Fundamentais
- Imutabilidade: "o código é a lei" – não pode ser alterado após implantação;
- Determinismo: input + código = output (sempre o mesmo resultado para a mesma entrada).

### 7.5 Distinção: Blockchain x Smart Contract
- Blockchain: onde se guardam os dados;
- Smart Contract: armazena o estado (código) e define as regras de transição de estado – dada uma entrada, gera uma saída.

### 7.6 Aplicações dos Smart Contracts
- Finanças descentralizadas (DeFi);
- Tokens não fungíveis (NFTs);
- Cadeia de suprimentos;
- Governança e votação;
- Seguros (registro de apólices);
- Tokenização de ativos.

### 7.7 Limitações Técnicas
- GAS Fees: custo para executar smart contracts – paga-se um valor à rede;
- Escalabilidade: processamento por segundo é baixo (TPS – transactions per second);
- Problema dos Oráculos: a blockchain não vê o mundo externo – não consegue acessar dados externos nativamente (ex.: cotação do dólar);
- Complexidade inerente: dificulta a auditoria do código.

### 7.8 Riscos e Vulnerabilidades
- Bug no código: um bug registrado fica para sempre – não há "segunda versão" (sem técnicas específicas);
- Overflow e Underflow: problemas com limites numéricos;
- Ataque de Reentrância: um contrato chama outro contrato, e o segundo compromete o primeiro;
- Falhas de validação dos dados registrados.

> [!CAUTION] OBSERVAÇÃO: 
> - A blockchain não é insegura; o que pode ser inseguro é o código colocado lá dentro.

## 8. Escalabilidade em Blockchains Públicas
- Blockchains públicas (Bitcoin, Ethereum) enfrentam desafios de escalabilidade – baixa taxa de TPS.
- Razão técnica principal: todos os nós da rede precisam processar, validar e armazenar todas as transações.
- O tamanho do bloco (que pode ser alterado) e o PoW (que é apenas um dos fatores) não são a razão principal da baixa escalabilidade – o gargalo fundamental é a exigência de que todos os nós processem tudo.

## 9. Blockchain x DLT

| ASPECTO | DLT | BLOCKCHAIN |
|---------|-----|------------|
| Conceito | Conjunto de tecnologias de registro distribuído. | Implementação específica de DLT. |
| Estrutura | Pode variar. | Dados organizados em blocos encadeados. |
| Relação | — | Todo blockchain é uma DLT. |

> [!CAUTION] OBSERVAÇÃO: 
> - Nem toda DLT é um blockchain.

## 10. Tabela Resumo – Mineradores e Validadores

| ASPECTO | MINERADOR (PoW) | VALIDADOR (PoS) |
|---------|-----------------|-----------------|
| Função | Validar transações e encontrar blocos válidos. | Validar propostas de bloco. |
| Recompensa | Novas moedas + taxas. | Taxas (e eventualmente novas moedas). |
| Requisito | Poder computacional. | Capital bloqueado (stake). |
| Risco | Investimento em hardware. | Perda do stake (slashing). |

## 11. Tabela Resumo – Blockchain

| ASPECTO | CARACTERÍSTICA |
|---------|----------------|
| Tipo | DLT (Distributed Ledger Technology). |
| Estrutura | Cadeia linear de blocos. |
| Componentes | Cabeçalho (validação) + Corpo (transações). |
| Segurança | Criptografia + consenso distribuído. |
| Principais características | Descentralização; imutabilidade; transparência. |
| Chaves | Sistema de chaves públicas e privadas. |
| Validação | Consenso da rede (não depende de terceiros). |