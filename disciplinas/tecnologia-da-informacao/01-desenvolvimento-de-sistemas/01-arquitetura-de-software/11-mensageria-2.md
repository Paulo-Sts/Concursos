# Mensageria 2: RabbitMQ e ActiveMQ

## 1. RabbitMQ
- Sistema de mensageria de código aberto e distribuído que atua como um intermediário de mensagens (message broker).
- Desenvolvido originalmente em 2007 utilizando a linguagem de programação Erlang, possuindo também versões comerciais disponíveis.
- O funcionamento do broker é estruturado pela combinação entre o Exchange e as Queues (filas).
- Fluxo de processamento ⟶ o produtor publica uma mensagem que entra no Exchange, o qual realiza o roteamento para a fila disponível para que o consumidor realize a leitura.

### 1.1 Protocolos Suportados
- amqp (Advanced Message Queuing Protocol);
- mqtt (Message Queuing Telemetry Transport);
- stomp (Simple Text Oriented Messaging Protocol).

### 1.2 Tipos de Exchanges
- Direct Exchange ⟶ realiza a entrega de mensagens para uma fila específica de acordo com uma chave de roteamento (routing key);
- Fanout Exchange ⟶ entrega as mensagens em modo broadcast para todas as filas conectadas;
- Topic Exchange ⟶ compara a chave de roteamento com um padrão estabelecido para direcionar a mensagem;
- Header Exchange ⟶ utiliza as informações contidas no cabeçalho da mensagem para realizar o processo de roteamento.

> [!TIP] DICAS: 
> - A porta padrão de escuta para o RabbitMQ em uma instalação ideal é a 5672.
> - A fila (queue) funciona como uma caixa postal interna que atua como um buffer de mensagens, limitada pelos recursos de memória e disco do host.

> [!CAUTION] OBSERVAÇÃO: 
> - Pegadinha de prova ⟶ o RabbitMQ permite a troca de mensagens de forma assíncrona, sendo incorreto afirmar que o processo é síncrono ou em tempo real.
> - Embora suporte autenticação e autorização via ldap e tls, a ferramenta não é exclusiva para a linguagem java.
> - O sistema suporta a implantação em clusters para alta disponibilidade e pode ser federado em múltiplas zonas e regiões.

## 2. ActiveMQ
- Broker de mensagens de código aberto criado pela Apache Software Foundation e desenvolvido em linguagem Java.
- Disponibilizado nas versões Classic e Artemis, suportando tanto o modelo de filas quanto o modelo de publicação e assinatura (pub/sub).
- Suporta diversos protocolos de comunicação, incluindo OpenWire, STOMP, MQTT e AMQP.

### 2.1 Monitoramento e Métricas
- O sistema realiza a gravação de registros e coleta métricas de uso de armazenamento, como memória e disco.
- Fornece dados detalhados sobre as mensagens, incluindo o número de mensagens aguardando, tempo médio de espera e mensagens expiradas.
- O monitoramento do serviço em uma máquina local é realizado por meio de um console web acessado a partir de uma url.

## 3. Comparativo de Tecnologias de Mensageria
| FERRAMENTA | MODELO PRINCIPAL | CARACTERÍSTICA DE RETENÇÃO |
|---|---|---|
| Rabbitmq | Fila de mensagens tradicional | Foco no roteamento e entrega assíncrona |
| Activemq | Filas e pub/sub | Suporte a múltiplos protocolos e métricas de disco |
| Apache kafka | Log de eventos distribuído | Permite a retenção de mensagens por período específico |

> [!CAUTION] OBSERVAÇÃO: 
> - A principal diferença entre o Kafka e o RabbitMQ reside no modelo: o Kafka utiliza um log de eventos distribuído, enquanto o RabbitMQ baseia-se em uma arquitetura de fila tradicional.