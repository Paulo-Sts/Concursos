# Anotações

# Blockchain II

## 1.1 Mineração e Validação

### 1.1.1 Conceito de Mineração
- A mineração é o processo de **validação das transações** para colocar um bloco dentro da blockchain.
- Para isso, é necessário haver um **consenso** entre todos os participantes da rede *peer-to-peer*.
- Como consequência da inclusão de um bloco, há **geração de novas moedas** (recompensa) entregue a quem venceu o processo de mineração.
- A mineração é o **mecanismo principal de segurança da rede** – uma vez que as transações entram na blockchain, garantem-se as propriedades de imutabilidade, transparência e descentralização.

> [!CAUTION] OBSERVAÇÃO
> **A mineração não serve apenas para criar novas moedas – sua função principal é validar transações e garantir a segurança da rede.**

### 1.1.2 O Ciclo da Mineração
1. Pegam-se as transações que estão no **pool de transações**.
2. Constrói-se um bloco candidato.
3. O *hash* é calculado.
4. Se for **maior que o *target***, altera-se o ***nonce***.
5. O ***nonce*** na função de *hash* gera um novo *hash*.
6. O *hash* deve ser **menor, em número, que o *target*** definido na construção do bloco candidato.
7. Quem achar o ***nonce*** primeiro resolve o problema criptográfico e ganha a chance de registrar o bloco.

### 1.1.3 Pools de Mineração
- **Pools de mineração:** grupos que trabalham cooperativamente para validar transações na blockchain, resolvendo cálculos complexos.
- Dividem, **proporcionalmente**, as recompensas de bloco entre si, de acordo com sua contribuição.

## 1.2 Mecanismos de Consenso

### 1.2.1 Proof of Work (PoW) – "Modelo Industrial"
**Contexto:** Bitcoin

- Para registrar um bloco, os mineradores ajustam um número arbitrário (***nonce***) repetidamente até encontrar um *hash* de cabeçalho **menor que o *target***.
- É um problema **computacionalmente difícil de resolver**, mas **trivial de verificar**.
- A segurança do PoW é baseada no **gasto energético e de hardware**.
- Exige investimento colossal em **eletricidade e chips ASICs** (especializados em mineração de Bitcoin).

**Ataque de 51%:**
- Quando uma pessoa controla **mais da metade** de todo o poder computacional global.
- Consegue **reescrever a história** da blockchain.

### 1.2.2 Proof of Stake (PoS) – "Modelo Econômico"
**Contexto:** Ethereum (migrou do PoW para o PoS)

- **Mudança de paradigma:** afasta-se da mineração e aproxima-se da **validação**.
- Substituição da **energia elétrica** (trabalho) pelo **capital bloqueado** (*stake*).
- É um **sorteio** para ver quem registra o bloco – não há competição computacional.

**Mecânica do Stake:**
1. Participantes bloqueiam criptomoedas como **"bond"** (aposta) – no Ethereum, são **32 ETH** para cada bilhete.
2. O protocolo seleciona **pseudoaleatoriamente** um validador – quem tem mais bilhetes tem mais chance.
3. Um **comitê** valida a proposta do bloco.
4. ***Slashing*:** se o indivíduo agir maliciosamente, **parte ou todo o seu *stake* é confiscado**.

> [!TIP] DICAS
> - **PoW:** baseado em hardware e eletricidade; segurança exógena (recursos do mundo real).
> - **PoS:** baseado em capital; segurança endógena (recursos da própria rede); consumo de energia baixo.

### 1.2.3 Quadro Comparativo – PoW x PoS

| ASPECTO | PROOF OF WORK (PoW) | PROOF OF STAKE (PoS) |
|---------|---------------------|----------------------|
| **Base** | Processamento/Hardware | Capital bloqueado (*stake*) |
| **Consumo de energia** | Alto | Baixo |
| **Recurso principal** | Eletricidade + chips ASICs | Moedas bloqueadas |
| **Risco** | Investimento em hardware | Perda de fundos (*slashing*) |
| **Segurança** | Exógena (mundo real) | Endógena (rede) |
| **Exemplo** | Bitcoin | Ethereum |

## 1.3 Smart Contracts (Contratos Inteligentes)

### 1.3.1 Conceito
- **Lógica programável e autoexecutável** registrada de forma imutável na blockchain.
- **Não é papel** – é código executável.
- Ao disparar um evento, executa **automaticamente** regras pré-definidas.
- Armazenados e replicados em **todos os nós** da rede.
- O **Ethereum** tem execução descentralizada por meio de *smart contracts*.

> [!CAUTION] OBSERVAÇÃO
> **"O código é a lei"** – após a implantação, o código não pode ser alterado (exceção: arquiteturas de *proxy*).

### 1.3.2 Anatomia Técnica
- Regras de validação.
- Funções.
- Eventos.
- Estado.

### 1.3.3 Ciclo de Vida
1. **Deploy:** implanta-se o *smart contract* na blockchain.
2. **Evento:** dispara a execução.
3. **Execução:** o código roda.
4. **Validação e registro:** o resultado é validado e registrado na blockchain.

### 1.3.4 Propriedades Fundamentais
- **Imutabilidade:** "o código é a lei" – não pode ser alterado após implantação.
- **Determinismo:** *input + código = output* (sempre o mesmo resultado para a mesma entrada).

### 1.3.5 Distinção: Blockchain x Smart Contract
- **Blockchain:** onde se guardam os dados.
- **Smart Contract:** armazena o **estado** (código) e define as **regras de transição de estado** – dada uma entrada, gera uma saída.

### 1.3.6 Aplicações dos Smart Contracts
- Finanças descentralizadas (*DeFi*).
- Tokens não fungíveis (NFTs).
- Cadeia de suprimentos.
- Governança e votação.
- Seguros (registro de apólices).
- Tokenização de ativos.

### 1.3.7 Limitações Técnicas
- **GAS Fees:** custo para executar *smart contracts* – paga-se um valor à rede.
- **Escalabilidade:** processamento por segundo é baixo (TPS – *transactions per second*).
- **Problema dos Oráculos:** a blockchain **não vê o mundo externo** – não consegue acessar dados externos nativamente (ex.: cotação do dólar).
- **Complexidade inerente:** dificulta a auditoria do código.

### 1.3.8 Riscos e Vulnerabilidades
- **Bug no código:** um *bug* registrado fica para sempre – não há "segunda versão" (sem técnicas específicas).
- **Overflow e Underflow:** problemas com limites numéricos.
- **Ataque de Reentrância:** um contrato chama outro contrato, e o segundo compromete o primeiro.
- **Falhas de validação** dos dados registrados.

> [!CAUTION] OBSERVAÇÃO
> **A blockchain não é insegura; o que pode ser inseguro é o código colocado lá dentro.**

## 1.4 Escalabilidade em Blockchains Públicas

- Blockchains públicas (Bitcoin, Ethereum) enfrentam desafios de escalabilidade – baixa taxa de TPS.
- **Razão técnica principal:** todos os nós da rede precisam **processar, validar e armazenar** todas as transações.
- **O tamanho do bloco** (que pode ser alterado) e o **PoW** (que é apenas um dos fatores) não são a razão principal da baixa escalabilidade – o gargalo fundamental é a exigência de que **todos os nós processem tudo**.

## 1.5 Tabela Resumo – Mineradores e Validadores

| ASPECTO | MINERADOR (PoW) | VALIDADOR (PoS) |
|---------|-----------------|-----------------|
| **Função** | Validar transações e encontrar blocos válidos | Validar propostas de bloco |
| **Recompensa** | Novas moedas + taxas | Taxas (e eventualmente novas moedas) |
| **Requisito** | Poder computacional | Capital bloqueado (*stake*) |
| **Risco** | Investimento em hardware | Perda do *stake* (*slashing*) |

---

# Questões de Fixação

## Questão 01
(IBFC/2024/POLÍCIA CIENTÍFICA-PR/PERITO OFICIAL CRIMINAL/ÁREA 3)

O minerador no universo do blockchain é responsável por:

a) oferecer serviços necessários, modernos, rápidos, seguros, com poucos custos, confiáveis e com conforto aos seus usuários.
b) validar as transações de uma blockchain, possuindo a função de encontrar os próximos blocos válidos na cadeia, para que as transações sejam inseridas nos blocos.
c) são responsáveis ainda por repassar os novos blocos aos demais nós-satélites (registradores e observadores), lembrando que todos os nós em uma rede Blockchain mantém uma cópia integral de todas as transações, ou blocos de transações (ledger).
d) o protótipo proposto para gerenciamento de portfólios de criptomoedas, apresentado neste trabalho.
e) responsável pelo avanço das tecnologias, a fim de se tornar um aliado para a proteção trabalhista, como mecanismo eficaz capaz de estabelecer medidas preventivas no combate ao trabalho escravo.

**Gabarito:** b

## Questão 02
(CESGRANRIO/2023/BANCO DO BRASIL/ESCRITURÁRIO/AGENTE COMERCIAL - PROVA A)

Existem grupos que trabalham cooperativamente para validar as transações na Blockchain, por meio da solução de cálculos complexos, e que concordam em dividir, proporcionalmente, recompensas de bloco entre eles, de acordo com sua contribuição nesse trabalho.

Tais grupos são denominados

a) grupos de data lake.
b) redes de extração.
c) cooperativas de blocos.
d) pools de mineração.
e) pools de distribuição.

**Gabarito:** d

## Questão 03
(CESGRANRIO/2024/CAIXA/TÉCNICO BANCÁRIO NOVO)

A mineração de Bitcoin é um processo complexo, que envolve muitos competidores, demanda grande capacidade computacional e enorme gasto de energia elétrica.

Esse processo de mineração consiste em

a) emitir novos Bitcoins, garantindo a crescente expansão da oferta da moeda.
b) validar os registros eletrônicos das transações no blockchain.
c) controlar a quantidade de Bitcoins emitidos para sustentar o valor da moeda.
d) alterar os registros eletrônicos prévios no blockchain, em troca de recompensa.
e) disputar a compra de Bitcoins na emissão a cotações menores do que as do mercado.

**Gabarito:** b

## Questão 04
(CESPE/CEBRASPE/2023/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/PERFIL: SEGURANÇA DA INFORMAÇÃO E PROTEÇÃO DE DADOS)

Considerando conceitos e padrões criptográficos, conceitos de blockchain e detecção, resposta, tratamento e recuperação de incidentes cibernéticos, julgue o item subsequente.

Blockchain é um livro-razão distribuído ponto a ponto, protegido por criptografia, apenas anexado, praticamente imutável, que pode ser atualizado apenas por consenso das partes ou com o acordo entre elas.

**Gabarito:** C (Correto) - *Append-only* significa que só é possível adicionar dados, mas não atualizar dados existentes.

## Questão 05
(CESPE/CEBRASPE/2025/BDMG/ANALISTA DE DESENVOLVIMENTO/SISTEMAS, ARQUITETURA E SOLUÇÃO DE DADOS)

Julgue o próximo item, a respeito de blockchain e inteligência artificial.

Um dos recursos do blockchain é o consenso, no qual novas transações financeiras só podem ser registradas quando a maioria dos participantes der o seu consentimento.

**Gabarito:** C (Correto)

## Questão 06
(FGV/2025/AL-AM/ANALISTA LEGISLATIVO/PROGRAMADOR)

A Assembleia está avaliando o uso de uma blockchain privada para o registro imutável de seus Atos Oficiais. Uma das características fundamentais que confere segurança a essa tecnologia é a imutabilidade dos registros.

Assinale a combinação de mecanismos técnicos que garante a imutabilidade dos dados em uma blockchain após a criação de um bloco.

a) Proof-of-Stake (PoS) e chaves simétricas.
b) Criptografia assimétrica (RSA) e Web of Trust.
c) Função Hash Criptográfica para encadeamento e Mecanismo de Consenso para validação distribuída.
d) Smart Contracts e Gossip Protocol.
e) Criptografia de ponta a ponta e Rate Limiting.

**Gabarito:** c

## Questão 07
(CESPE/CEBRASPE/2025/BANRISUL/TÉCNICO EM TECNOLOGIA DA INFORMAÇÃO II/TRANSFORMAÇÃO DIGITAL E GESTÃO DE TI)

A característica do blockchain responsável por garantir a segurança das transações é conhecida como

a) eficiência.
b) registro.
c) transparência.
d) consenso.
e) descentralização.

**Gabarito:** d

## Questão 08
(FGV/2025/AL-AM/ANALISTA LEGISLATIVO/PROGRAMADOR)

Apesar das vantagens de imutabilidade e descentralização, as blockchains públicas como Bitcoin ou Ethereum enfrentam desafios significativos de escalabilidade, manifestados pela baixa taxa de transações por segundo (TPS).

A principal razão técnica pela qual as blockchains públicas, baseadas em algoritmos de consenso como Proof-of-Work (PoW), têm inerentemente baixa escalabilidade é

a) o uso de criptografia simétrica no payload das transações.
b) a exigência de que todos os nodes na rede processem, validem e armazenem todas as transações.
c) a limitação física do tamanho do bloco.
d) a ausência de Smart Contracts na maioria das blockchains de primeira geração.
e) o baixo custo computacional para minerar novos blocos (PoW).

**Gabarito:** b

## Questão 09
(FGV/2025/SEFAZ-RS/AUDITOR DO ESTADO/MANHÃ)

Blockchain é uma tecnologia emergente com o potencial de revolucionar diversos setores. Atualmente, existem diversas plataformas blockchain que são os softwares que permitem construir e executar aplicações descentralizadas.

Com relação aos contratos inteligentes, avalie se as afirmativas a seguir são verdadeiras (V) ou falsas (F).

( ) São programas executados sobre uma plataforma blockchain e encapsulam a lógica de negócios a ser executada quando certas condições são atendidas.

( ) Estão disponíveis em todas as plataformas blockchain e se tornaram um recurso padrão devido à flexibilidade e ao poder que ele fornece para aplicativos executados na Web3.

( ) São contêineres descentralizados que realizam as provas de trabalho para a geração de novos blocos encadeados a partir de um bloco gênesis.

As afirmativas são, respectivamente,

a) V – F – V.
b) F – V – V.
c) V – F – F.
d) F – F – V.
e) V – V – F.

**Gabarito:** c

## Questão 10
(FGV/2024/CÂMARA DOS DEPUTADOS/ANALISTA LEGISLATIVO/CONSULTORIA/CONSULTOR LEGISLATIVO/ÁREA XIV/REAPLICAÇÃO)

Considerando os contratos inteligentes em blockchain, assinale a afirmação correta.

a) Contratos inteligentes não são vinculativos quando estabelecidos, mas meramente orientativos; embora apresentem potencial para simplificar e agilizar transações, a discussão em torno do seu reconhecimento legal e validação permanece como um ponto central de debate no âmbito jurídico.
b) Contratos inteligentes são autoexecutáveis e operam sem a necessidade de intermediários; no contexto desse procedimento, os acordos formalizados são registrados em uma blockchain, garantindo transparência, segurança e imutabilidade, proporcionando uma redução de custos e um aumento na eficiência.
c) A execução de contratos inteligentes pode ser alterada manualmente e de forma livre após sua implementação.
d) Contratos inteligentes são exclusivamente usados em transações financeiras.
e) Blockchain é uma tecnologia de registro centralizada e imutável que permite o armazenamento de dados e informações de forma segura e distribuída; o que o diferencia de bancos de dados ou softwares convencionais é sua resistência à adulteração, uma vez que a alteração de dados em um bloco requer a manipulação de todos os blocos anteriores.

**Gabarito:** b

## Questão 11
(FURB/2024/CÂMARA DE BRUSQUE/SC/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

O conceito de “contratos inteligentes” (Smart Contracts) na Blockchain refere-se a:

a) Algoritmos de consenso que garantem a criação de blocos em sistemas descentralizados.
b) Ferramentas que utilizam criptografia para proteger dados sensíveis em contratos físicos.
c) Programas autoexecutáveis que operam dentro da Blockchain e garantem a execução automática de termos de um contrato sem a necessidade de intermediários.
d) Contratos eletrônicos assinados com tokens que podem ser trocados em redes sociais.
e) Aplicativos que utilizam a computação em nuvem para armazenar e processar contratos legais, via assinaturas digitais.

**Gabarito:** c

## Questão 12
(FGV/2024/MF/AUDITOR FEDERAL DE FINANÇAS E CONTROLE/ÁREA DE TECNOLOGIA DA INFORMAÇÃO (TRANSFORMAÇÃO DIGITAL)/MANHÃ)

Em sistemas de blockchain que interagem com o mundo real, uma questão fundamental surge quando contratos inteligentes necessitam de dados externos para executar suas funções. Essa questão representa um desafio significativo na integração confiável de informações fora da blockchain. O nome dado ao problema que descreve a dificuldade inerente em acessar informações verídicas e atualizadas do mundo externo, sem comprometer a segurança e a descentralização do sistema blockchain é

a) dupla despesa.
b) ataque de 51%.
c) oráculo.
d) volatilidade.
e) escalabilidade.

**Gabarito:** c - O **problema do oráculo** refere-se à dificuldade de acessar informações do mundo externo sem comprometer a segurança e a descentralização.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | b |
| 02 | d |
| 03 | b |
| 04 | C |
| 05 | C |
| 06 | c |
| 07 | d |
| 08 | b |
| 09 | c |
| 10 | b |
| 11 | c |
| 12 | c |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Alexandre Kessler De Almeida.*