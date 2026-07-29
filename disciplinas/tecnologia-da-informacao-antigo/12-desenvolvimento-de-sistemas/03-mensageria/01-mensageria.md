# Mensageria e Ferramentas (Kafka, RabbitMQ, ActiveMQ)

## 1. Conceito Geral

### 1.1 Definição
- Mensageria é a troca de mensagens entre sistemas.
- Permite o processamento em tempo real de grandes bases de dados.
- O serviço de mensageria desacopla o produtor do consumidor, garantindo que a produção não seja perdida, mesmo em grande escala temporária.

### 1.2 Benefícios do Desacoplamento
- O sistema produtor e o sistema consumidor não precisam estar ativos simultaneamente;
- O produtor pode enviar mensagens mesmo que o consumidor esteja indisponível;
- O consumidor pode processar mensagens em seu próprio ritmo.

## 2. Modelos de Mensageria

### 2.1 Modelo em Fila (Queue-Based Model)
- Cada mensagem produzida é consumida por um único consumidor.
- As mensagens são processadas na ordem em que chegam (FIFO – First In, First Out).
- Ideal para distribuição de carga entre múltiplos consumidores.

### 2.2 Modelo Pub/Sub (Publish/Subscribe)
- Publicador (Publisher): envia mensagens para um tópico sem conhecer os assinantes;
- Assinante (Subscriber): recebe mensagens de tópicos aos quais se inscreveu;
- Uma mensagem pode ser entregue a múltiplos assinantes simultaneamente;
- Ideal para broadcast de informações.

## 3. Características da Mensageria

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Desacoplamento | Produtor e consumidor não precisam se conhecer ou estar sincronizados. |
| Durabilidade | Mensagens não são perdidas – ficam armazenadas na fila. |
| Confiabilidade na entrega | Garantia de que a mensagem será entregue ao consumidor. |
| Roteamento de mensagens | Balanceamento de carga entre diversos consumidores. |
| Comunicação assíncrona | Produtor e consumidor não precisam estar ativos simultaneamente. |
| Persistência de mensagens | Mensagens são armazenadas em algum local (fila, broker). |

### 3.1 Comunicação Síncrona x Assíncrona

| ASPECTO | SÍNCRONA | ASSÍNCRONA |
|---------|----------|------------|
| Definição | Partes precisam estar ativas simultaneamente em tempo real. | Partes não precisam estar ativas simultaneamente. |
| Exemplo | Ligação telefônica. | WhatsApp. |
| Relação com mensageria | Não é o foco da mensageria. | É o modelo utilizado pela mensageria. |

> [!TIP] DICAS: 
> - Mensageria é, por definição, uma forma de comunicação assíncrona.
> - O desacoplamento entre produtor e consumidor é o que permite a assincronicidade.

## 4. Apache Kafka

### 4.1 Visão Geral e Histórico
- Projeto de código aberto mantido pela Apache Software Foundation.
- Originalmente desenvolvido pela LinkedIn.
- Modelo de log de eventos distribuído, permitindo retenção de mensagens por um período específico.

### 4.2 Usos do Kafka
- Sistema de processamento de streams;
- Plataforma de mensagens distribuída – faz o "meio de campo" entre o processamento e a fila de mensagens;
- Sistema de armazenamento distribuído – pode ser utilizado como banco de dados;
- Agregação de logs.

### 4.3 Arquitetura do Kafka

#### 4.3.1 Componentes

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| Broker | O local onde as mensagens ficam armazenadas (servidor). |
| Tópico (Topic) | Conjuntos de mensagens com filas independentes. |
| Partição (Partition) | Cada tópico é formado por partições com estrutura própria de mensagens. |
| Offset | Posição que um determinado consumidor ocupa dentro da partição. |

#### 4.3.2 Relações entre Componentes
- Tópico → formado por partições;
- Partição → contém mensagens em ordem (com offset);
- Consumidor → tem seu posicionamento (offset) dentro da partição;
- Broker → servidor que armazena os dados.

### 4.4 APIs do Kafka

| API | DESCRIÇÃO |
|-----|-----------|
| Producer API | Produz a mensagem e envia para o Kafka Cluster. |
| Consumer API | Aplicativos que vão receber as mensagens. |
| Streams API | Processamento de fluxos de eventos. |
| Connector API | Integração com bancos de dados para armazenamento das informações. |

> [!TIP] DICAS: 
> - A Connector API é a responsável pela integração com bancos de dados e outros sistemas.

### 4.5 Características Importantes do Kafka
- Eventos no tópico são imutáveis – não podem ser modificados depois de escritos;
- O Kafka não exige armazenamento durável de fluxos de eventos, mas pode tê-lo;
- Produtores e consumidores ficam desacoplados e agnósticos entre si – podem usar tecnologias diferentes.

> [!CAUTION] OBSERVAÇÃO: 
> - Eventos no tópico são imutáveis – não podem ser modificados.
> - O Kafka pode ter armazenamento durável, mas não é obrigatório – depende da configuração.

## 5. RabbitMQ

### 5.1 Visão Geral
- Sistema de mensageria open-source distribuído que atua como um message broker (intermediário para mensagens).
- Possui versão comercial.
- Criado em 2007 na linguagem de programação Erlang.

### 5.2 Protocolos Suportados
- AMQP (Advanced Message Queuing Protocol);
- MQTT (Message Queuing Telemetry Transport);
- STOMP (Simple (or Streaming) Text Oriented Messaging Protocol).

### 5.3 Arquitetura do RabbitMQ
- O broker é formado pelo Exchange + Queues.
- O Exchange faz a ligação da mensagem com uma fila que esteja disponível.

### 5.4 Fluxo de Funcionamento
1. O produtor publica uma mensagem;
2. A mensagem entra no Exchange;
3. O Exchange roteia a mensagem para a fila disponível;
4. A fila armazena as mensagens (limitada apenas pelos limites de memória e disco do host);
5. O consumidor consome a mensagem da fila.

### 5.5 Tipos de Exchanges

| TIPO | DESCRIÇÃO |
|------|-----------|
| Direct Exchange | Entrega mensagens para uma fila de acordo com uma routing key. |
| Fanout Exchange | Entrega mensagens em broadcast. |
| Topic Exchange | Compara a routing key com um padrão; cada fila tem uma chave. |
| Header Exchange | Utiliza o cabeçalho da mensagem para roteamento. |

### 5.6 Características Importantes
- Permite a troca de mensagens de forma assíncrona (não síncrona);
- Suporta autenticação e autorização conectáveis;
- Suporta LDAP e TLS;
- Pode ser implantado em nuvens públicas e privadas;
- Pode ser implantado como clusters para alta disponibilidade;
- Pode ser federado em várias zonas e regiões de disponibilidade;
- Permite a escolha de um mecanismo de persistência;
- Porta padrão: 5672.

> [!CAUTION] OBSERVAÇÃO: 
> - O RabbitMQ NÃO é exclusivo para Java! Ele fornece APIs de cliente para diversas linguagens de programação, não apenas Java.

### 5.7 Componentes do RabbitMQ

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| Producer | Responsável por enviar mensagens para uma fila. |
| Consumer | Responsável por receber e processar mensagens. |
| Queue | Caixa postal interna que funciona como um grande buffer de mensagens. |
| Broker | Intermediário que gerencia as filas e exchanges. |

## 6. ActiveMQ

### 6.1 Visão Geral
- Broker de mensagens open-source.
- Versões: Classic e Artemis.
- Criado pela Apache Software Foundation e escrito em Java.
- Suporta filas e pub/sub.
- Suporta diversos protocolos de mensageria: OpenWire, STOMP, MQTT e AMQP.

### 6.2 Características
- Grava registros e coleta métricas de mensagens e uso do armazenamento;
- Métricas de armazenamento: uso de memória e disco;
- Métricas de mensagens: número de mensagens aguardando, tempo médio de espera e mensagens expiradas;
- O monitoramento do ActiveMQ em uma máquina local é realizado por meio de uma console web acessada a partir de uma URL.

## 7. Comparativo – Kafka x RabbitMQ

| ASPECTO | APACHE KAFKA | RABBITMQ |
|---------|--------------|----------|
| Modelo | Log de eventos distribuído. | Fila de mensagens tradicional. |
| Retenção de mensagens | Permite retenção por período específico. | Fila com consumo imediato. |
| Protocolos | Próprio (Kafka Protocol). | AMQP, MQTT, STOMP. |
| Linguagem | Scala/Java. | Erlang. |
| Padrão de consumo | Pull (consumidor puxa). | Push (broker empurra). |
| Caso de uso típico | Streaming de eventos, alta vazão. | Mensageria entre microsserviços. |

## 8. Tabela Resumo – Kafka

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| Broker | Servidor que armazena as mensagens. |
| Tópico | Categoria/agrupamento de mensagens. |
| Partição | Divisão do tópico – cada uma com estrutura própria. |
| Offset | Posição do consumidor dentro da partição. |
| Producer | Quem envia mensagens. |
| Consumer | Quem recebe mensagens. |

## 9. Tabela Resumo – RabbitMQ

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| Broker | Exchange + Queues. |
| Exchange | Roteia mensagens para filas. |
| Queue | Armazena mensagens (buffer). |
| Producer | Envia mensagens. |
| Consumer | Recebe e processa mensagens. |
| Porta padrão | 5672. |