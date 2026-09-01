# Hadoop

## 1. Conceito
- O Apache Hadoop é um framework open source desenvolvido para armazenar e processar grandes volumes de dados de forma distribuída e escalável.
- Foi criado para lidar com os desafios do Big Data, permitindo trabalhar com dados muito maiores do que caberiam em um único servidor, dividindo a carga entre vários nós de um cluster.
- O nome Hadoop faz referência a um elefante de brinquedo do filho do criador, simbolizando a marca do projeto.
- O Hadoop permite armazenar dados distribuindo-os em um cluster de computadores e processá-los de forma paralela, em que cada nó do cluster processa uma parte da requisição (ex.: transformação de dados categóricos em dados numéricos).
- É considerado um framework porque engloba vários sistemas e é parte de um ecossistema mais amplo.
- O funcionamento básico envolve a divisão dos dados em pedaços, processo chamado de stripping ou sharding, distribuindo cada parte em diferentes nós do cluster.
- Para garantir a segurança dos dados em caso de falha de algum nó, cada pedaço é replicado em múltiplos nós, assegurando tolerância a falhas, conforme o teorema CAP (consistência, disponibilidade e tolerância a partições).
- Dessa forma, não é necessário realizar backup adicional, pois a replicação interna do cluster garante a integridade e disponibilidade dos dados.

> [!TIP] DICAS: 
> - O Hadoop é um framework open source para armazenamento e processamento distribuído de Big Data, com escalabilidade horizontal.

> [!CAUTION] OBSERVAÇÃO: 
> - Não se deve confundir Hadoop com um banco de dados relacional. Ele é um sistema de arquivos e processamento distribuído.

## 2. Características
- Escalabilidade horizontal: adiciona-se mais máquinas para aumentar capacidade.
- Tolerância a falhas: dados replicados em múltiplos nós (padrão de três cópias).
- Flexibilidade: suporta múltiplos tipos de dados (estruturados, semiestruturados e não estruturados).
- Baixo custo: utiliza hardware commodity e software livre.
- Permite construir clusters de máquinas de baixo custo, em que a adição de novos nós aumenta proporcionalmente a capacidade de processamento.
- Funciona normalmente como infraestrutura de base de um data lake.

> [!CAUTION] OBSERVAÇÃO: 
> - O Hadoop possui alta latência, pois é um sistema de processamento em lote (batch), não sendo adequado para aplicações em tempo real.

## 3. Vantagens
- Armazena e processa petabytes de dados.
- Distribuição e paralelismo aumentam desempenho.
- Amplo ecossistema para diferentes necessidades.
- Altamente escalável e adaptável.
- Para processamento em tempo real, o Apache Spark se destaca, podendo operar sobre os dados armazenados no HDFS (Hadoop Distributed File System).

## 4. Desvantagens
- Latência alta em análises de tempo real (MapReduce é batch-oriented).
- Curva de aprendizado alta.
- Requer configuração e manutenção complexas.
- Necessidade de grandes volumes para justificar o uso.

> [!CAUTION] OBSERVAÇÃO: 
> - O Hadoop é indicado para projetos de Big Data e não para armazenamento de dados simples ou pequenos volumes.

## 5. Hdfs (Hadoop Distributed File System)
- É o sistema de arquivos distribuído do ecossistema Hadoop.
- Projetado para armazenar grandes volumes de dados em clusters de servidores, dividindo-os em blocos e distribuindo-os entre diferentes nós com replicação para garantir tolerância a falhas.
- Inspirado no sistema de arquivos do Google (Google File System – GFS).
- Adota um modelo mestre-escravo:
  - NameNode (nó mestre): gerencia a estrutura do sistema de arquivos, incluindo metadados como nomes de arquivos, pastas, permissões e localização dos blocos.
  - DataNodes (nós escravos): realizam o armazenamento efetivo dos dados, divididos em blocos e distribuídos entre os nós do cluster, com replicação padrão de três cópias.
- O HDFS permite alta tolerância a falhas: se um ou dois DataNodes forem perdidos, os dados permanecem disponíveis; caso o NameNode primário falhe, um Secondary NameNode assume suas funções.
- É otimizado para processamento em lote (batch) de grandes volumes de dados, sendo adequado para Big Data, mas não indicado para processamento em tempo real.
- A estrutura distribuída possibilita que os dados sejam paralelizados e processados de forma eficiente, com gerenciamento centralizado dos metadados e armazenamento físico distribuído nos DataNodes.

> [!TIP] DICAS: 
> - A função do HDFS é armazenar grandes volumes de dados de forma distribuída e tolerante a falhas.

### 5.1 Características do Hdfs
- Alta tolerância a falhas: perda de um DataNode não compromete o arquivo, pois existem cópias em outros nós.
- Escalabilidade horizontal: é possível adicionar novos nós para expandir capacidade.
- Acesso sequencial: ideal para processamento em lote (batch).
- Suporte a diversos formatos de dados.

### 5.2 Arquitetura do Hdfs
- Baseado em um modelo mestre-escravo:
  - NameNode (Mestre):
    - Gerencia a estrutura do sistema de arquivos (metadados), como nomes de arquivos, diretórios, permissões e localização dos blocos.
    - Não armazena dados reais, apenas informações sobre onde eles estão.
  - DataNodes (Escravos):
    - Armazenam efetivamente os blocos de dados.
    - Executam operações de leitura e gravação sob comando do NameNode.

### 5.3 Funcionamento do Hdfs
- Divisão em blocos: arquivos são quebrados em blocos de tamanho fixo (padrão: 128 MB ou 256 MB).
- Replicação: cada bloco é replicado (padrão: 3 cópias) em diferentes nós para garantir disponibilidade.
- Leitura: o cliente consulta o NameNode, que informa quais DataNodes possuem os blocos.
- Escrita: o cliente envia o bloco para um DataNode, que replica para os demais conforme a política de replicação.

> [!CAUTION] OBSERVAÇÃO: 
> - Não é necessário aprofundamento em comandos específicos do NameNode para fins de estudo conceitual, sendo suficiente compreender a estrutura, a função das ferramentas e a lógica de replicação e distribuição de dados.