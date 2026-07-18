# Anotações

# Mensageria

## 1.1 Conceito Geral

- Mensageria é a **troca de mensagens entre sistemas**.
- Permite o processamento em **tempo real** de grandes bases de dados.
- O serviço de mensageria **desacopla o produtor do consumidor**, garantindo que a produção não seja perdida, mesmo em grande escala temporária.

### 1.1.1 Benefícios do Desacoplamento

- O sistema produtor e o sistema consumidor **não precisam estar ativos simultaneamente**.
- O produtor pode enviar mensagens mesmo que o consumidor esteja indisponível.
- O consumidor pode processar mensagens em seu próprio ritmo.

## 1.2 Modelos de Mensageria

### 1.2.1 Modelo em Fila (*Queue-Based Model*)

- Cada mensagem produzida é consumida por **um único consumidor**.
- As mensagens são processadas na ordem em que chegam (FIFO – *First In, First Out*).
- Ideal para **distribuição de carga** entre múltiplos consumidores.

### 1.2.2 Modelo Pub/Sub (*Publish/Subscribe*)

- **Publicador** (*Publisher*): envia mensagens para um tópico sem conhecer os assinantes.
- **Assinante** (*Subscriber*): recebe mensagens de tópicos aos quais se inscreveu.
- Uma mensagem pode ser entregue a **múltiplos assinantes** simultaneamente.
- Ideal para **broadcast** de informações.

## 1.3 Características da Mensageria

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **Desacoplamento** | Produtor e consumidor não precisam se conhecer ou estar sincronizados |
| **Durabilidade** | Mensagens não são perdidas – ficam armazenadas na fila |
| **Confiabilidade na entrega** | Garantia de que a mensagem será entregue ao consumidor |
| **Roteamento de mensagens** | Balanceamento de carga entre diversos consumidores |
| **Comunicação assíncrona** | Produtor e consumidor não precisam estar ativos simultaneamente |
| **Persistência de mensagens** | Mensagens são armazenadas em algum local (fila, broker) |

### 1.3.1 Comunicação Síncrona x Assíncrona

- **Assíncrona:** partes não precisam estar ativas simultaneamente.
  - Exemplo: **WhatsApp**.
- **Síncrona:** partes precisam estar ativas simultaneamente em tempo real.
  - Exemplo: **ligação telefônica**.

## 1.4 Apache Kafka

### 1.4.1 Visão Geral

- Projeto de **código aberto** mantido pela Apache Software Foundation.
- Originalmente desenvolvido pela **LinkedIn**.
- Modelo de **log de eventos distribuído**, permitindo retenção de mensagens por um período específico.

### 1.4.2 Usos do Kafka

- **Sistema de processamento de *streams***.
- **Plataforma de mensagens distribuída** – faz o "meio de campo" entre o processamento e a fila de mensagens.
- **Sistema de armazenamento distribuído** – pode ser utilizado como banco de dados.
- **Agregação de *logs***.

### 1.4.3 Arquitetura do Kafka

- **Broker:** o local onde as mensagens ficam armazenadas.
- **Tópico (*Topic*):** conjuntos de mensagens com filas independentes.
- **Partição (*Partition*):** cada tópico é formado por partições com estrutura própria de mensagens.
- **Offset:** posição que um determinado consumidor ocupa dentro da partição.

### 1.4.4 APIs do Kafka

| API | DESCRIÇÃO |
|-----|-----------|
| **Producer API** | Produz a mensagem e envia para o *Kafka Cluster* |
| **Consumer API** | Aplicativos que vão receber as mensagens |
| **Streams API** | Processamento de fluxos de eventos |
| **Connector API** | Integração com bancos de dados para armazenamento das informações |

### 1.4.5 Relações entre Componentes

- **Tópico** → formado por **partições**.
- **Partição** → contém mensagens em ordem (com *offset*).
- **Consumidor** → tem seu posicionamento (*offset*) dentro da partição.
- **Broker** → servidor que armazena os dados.

### 1.4.6 Características Importantes

- **Eventos no tópico são imutáveis** – não podem ser modificados depois de escritos.
- O Kafka **não exige** armazenamento durável de fluxos de eventos, mas **pode tê-lo**.
- **Produtores e consumidores ficam desacoplados e agnósticos entre si** – podem usar tecnologias diferentes.

## 1.5 Tabela Resumo – Kafka

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| **Broker** | Servidor que armazena as mensagens |
| **Tópico** | Categoria/agrupamento de mensagens |
| **Partição** | Divisão do tópico – cada uma com estrutura própria |
| **Offset** | Posição do consumidor dentro da partição |
| **Producer** | Quem envia mensagens |
| **Consumer** | Quem recebe mensagens |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/SEFAZ-CE/AUDITOR FISCAL DE TECNOLOGIA DA INFORMAÇÃO DA RECEITA ESTADUAL/2021)

Julgue o próximo item, relativos ao Apache Kafka e ao Kubernetes.

O Apache Kafka provê serviço de mensageria e integração de dados, de forma assíncrona, em que produtores e consumidores ficam desacoplados e agnósticos entre si.

**Gabarito:** C (Correto)

## Questão 02
(CESPE/CEBRASPE/SERPRO/ANALISTA/ESPECIALIZAÇÃO: TECNOLOGIA/2023)

Julgue o item subsequente, referentes a ferramentas de integração assíncrona e contêineres.

O Apache Kafka 3.4 é uma plataforma voltada para processar dados de eventos de streaming ou dados que não têm início ou fim distintos. Ele possui recursos de publicar (escrever) e assinar (ler) fluxos de eventos e de processar fluxos de eventos à medida que ocorrem; portanto, nessa plataforma, prescinde-se do armazenamento de fluxos de eventos de forma durável.

**Gabarito:** E (Errado) - O Kafka não **necessariamente** precisa de armazenamento durável, mas **pode tê-lo** – não se "prescinde" do armazenamento.

## Questão 03
(FGV/PGM/NITERÓI/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/2023)

O analista João implementou o PStream, um fluxo de tratamento de dados em tempo real, através do Apache Kafka. O PStream é alimentado pela captura em tempo real das alterações feitas em uma base de dados relacional. Para configurar esta captura de dados relacionais para o PStream, João recorreu aos mecanismos do Apache Kafka para integração com outros sistemas. Esses mecanismos de integração utilizados por João para integrar o Apache Kafka com outros sistemas são baseados na Application Programming Interface (API) do Apache Kafka:

a) Admin.
b) Connect.
c) Streams.
d) Producer.
e) Consumer.

**Gabarito:** b - A API responsável pela integração com bancos de dados e outros sistemas é a **Connector API**.

## Questão 04
(FGV/CÂMARA DOS DEPUTADOS/ANALISTA LEGISLATIVO/INFORMÁTICA LEGISLATIVA/TARDE/2023)

Apache Kafka é um sistema de mensageria altamente escalável, que usa tópicos e partições para enfileiramento de mensagens. Sobre os componentes arquitetônicos do Kafka, assinale a afirmativa correta.

a) As partições são divididas em tópicos que os consumidores assinam para receber mensagens.
b) Um tópico pode ter apenas um produtor que escreve eventos nele, porém pode ter muitos consumidores que o assinam.
c) Os eventos no tópico são imutáveis, o que significa que não podem ser modificados depois de escritos.
d) Os produtores atribuem uma chave a cada mensagem e o Kafka a armazena no tópico principal da partição mais vazia.
e) Os consumidores sempre recebem as mensagens na ordem em que foram enviadas.

**Gabarito:** c

## Questão 05
(FGV/TCE-SP/AGENTE DA FISCALIZAÇÃO/TI/2023)

A analista Lúcia administra o AKluster, o cluster do Apache Kafka no TCE SP. Lúcia constatou que o espaço disponível no AKluster para o armazenamento de streams de eventos está acabando. Para expandir a camada de persistência do AKluster, aumentando ainda a escalabilidade, Lúcia deve prover mais espaço de armazenamento ao Apache Kafka mediante novos:

a) topics.
b) brokers.
c) partitions.
d) producers.
e) replications.

**Gabarito:** b - Os dados são armazenados no **broker**.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | E |
| 03 | b |
| 04 | c |
| 05 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Júlio César Batista Leitão.*