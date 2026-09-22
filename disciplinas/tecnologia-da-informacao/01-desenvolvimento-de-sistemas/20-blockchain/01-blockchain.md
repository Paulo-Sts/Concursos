# Blockchain e Tecnologias de Registro Distribuído

## 1. Conceitos Fundamentais
- Blockchain é um tipo de DLT (Distributed Ledger Technology) ⟶ tecnologia de registro distribuído.
- Funciona tecnicamente como um livro-razão digital, compartilhado e imutável.
- A rede opera no modelo P2P (Peer-to-Peer), o que garante a ausência de um ponto único de falha.
- A tecnologia elimina intermediários ao permitir que transações sejam validadas diretamente entre os participantes.
- Todo blockchain é classificado como uma DLT, entretanto, nem toda DLT constitui um blockchain.

## 1.1 Características Essenciais
- Descentralização: elimina a necessidade de uma autoridade central para a validação das transações.
- Imutabilidade: assegura que os registros não possam ser alterados ou excluídos após sua inserção na cadeia.
- Transparência: permite que participantes autorizados visualizem todo o histórico de transações por meio de exploradores de blocos.
- Segurança criptográfica: utiliza um sistema de chaves públicas e privadas para garantir o acesso e a integridade das informações.
- Natureza append-only: o sistema funciona apenas para adição de dados, sendo impossível atualizar ou deletar registros já confirmados.

> [!TIP] DICAS: 
> - Lembre-se: em provas de concurso, a verdade no blockchain não reside em um servidor central, mas na própria rede distribuída.

> [!CAUTION] OBSERVAÇÃO: 
> - O blockchain não é considerado uma tecnologia voltada à alta velocidade ou eficiência quando comparado a bancos de dados tradicionais, pois seu processo de validação é propositalmente lento.

## 2. Anatomia do Bloco
- A unidade atômica da tecnologia é o bloco, caracterizado como um contêiner de dados validado e selado.
- Os blocos são encadeados de forma sequencial, cronológica e linear.
- A estrutura básica de um bloco é dividida em duas partes: cabeçalho e corpo.

## 2.1 Cabeçalho (The Brain)
- Responsável pela integridade criptográfica do bloco, metadados e pelo mecanismo de consenso.
- Versão: campo que identifica o software e as regras de protocolo utilizadas.
- Timestamp: registro imutável que indica o momento exato da criação do bloco.
- Dificuldade (Target/nBits): define a complexidade do problema criptográfico a ser resolvido pelos mineradores.
- Hash anterior: ponteiro criptográfico que liga o bloco atual ao bloco pai, garantindo o encadeamento.
- Merkle Root: hash raiz que resume de forma eficiente e compacta todas as transações contidas no corpo do bloco.

## 2.2 Corpo (The Archive)
- Atua como o registro de dados brutos do sistema.
- Armazena a lista completa de transações validadas e seladas no bloco.
- Transação coinbase: registro especial que representa a criação de novas moedas e a recompensa do minerador.
- Pode conter o código de execução e o estado de contratos inteligentes.

## 2.3 O Papel do Hash
- Atua como uma impressão digital única que identifica o bloco e todo o seu conteúdo.
- Qualquer modificação mínima nos dados do bloco altera drasticamente o seu hash final.
- Efeito Avalanche: a alteração de um bloco compromete toda a cadeia subsequente, pois os hashes deixam de corresponder.
- Esta estrutura garante a detecção imediata de violações, pois a rede rejeita versões adulteradas que quebram a corrente.

## 3. Mecanismos de Consenso e Mineração
- Mineração é o processo de validação de transações para a inclusão de novos blocos na blockchain.
- Consenso refere-se à democracia algorítmica onde os participantes concordam sobre qual versão do histórico é a verdadeira.
- O consenso é a característica primordial responsável por garantir a segurança das transações na rede.

## 3.1 Proof of Work (PoW)
- Conhecido como o modelo industrial de mineração, sendo o padrão utilizado pelo Bitcoin.
- A segurança baseia-se no gasto de hardware e alto consumo de energia elétrica.
- Mineradores competem para encontrar um nonce que gere um hash de cabeçalho menor que o target.
- Inerentemente possui baixa escalabilidade, pois exige que todos os nós processem, validem e armazenem todas as transações.

## 3.2 Proof of Stake (PoS)
- Modelo econômico de validação que substitui a mineração tradicional, utilizado atualmente pelo Ethereum.
- O recurso de trabalho (energia) é substituído pelo capital bloqueado na rede (stake).
- Validadores são selecionados de forma pseudoaleatória para registrar blocos conforme a quantidade de moedas em aposta.
- Slashing: mecanismo de punição onde parte ou todo o capital do validador é confiscado em caso de comportamento malicioso.

| CARACTERÍSTICA | PROOF OF WORK (POW) | PROOF OF STAKE (POS) |
|---|---|---|
| Recurso base | Hardware e eletricidade | Capital bloqueado |
| Consumo de energia | Alto | Baixo |
| Segurança | Exógena (custo físico) | Endógena (recursos da rede) |
| Risco principal | Ataque de 51 por cento | Perda de fundos por slashing |

## 4. Contratos Inteligentes (Smart Contracts)
- São programas autoexecutáveis e imutáveis registrados diretamente na blockchain.
- Encapsulam lógicas de negócio: se certas condições são atendidas, uma ação é executada automaticamente.
- Operam sem a necessidade de intermediários, o que proporciona redução de custos e aumento na eficiência.
- Determinismo: dado um input específico, o código sempre produzirá o mesmo output.

## 4.1 Limitações e Riscos Técnicos
- GAS Fees: valor pago à rede para processar e executar as funções do contrato inteligente.
- Problema dos oráculos: dificuldade inerente em acessar informações verídicas do mundo externo sem comprometer a segurança.
- Vulnerabilidade permanente: bugs registrados no código tornam-se definitivos devido à imutabilidade da rede.

> [!CAUTION] OBSERVAÇÃO: 
> - O ataque de 51% é uma hipótese remota de comprometimento onde um agente controla a maioria do poder computacional e consegue alterar registros.