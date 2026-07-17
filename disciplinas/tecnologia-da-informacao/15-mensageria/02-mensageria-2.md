# Anotações

# Mensageria II

## 1.1 RabbitMQ

### 1.1.1 Visão Geral
- Sistema de mensageria ***open-source*** distribuído que atua como um ***message broker*** (intermediário para mensagens).
- Possui versão comercial.
- Criado em **2007** na linguagem de programação **Erlang**.

### 1.1.2 Protocolos Suportados
- **AMQP** (*Advanced Message Queuing Protocol*).
- **MQTT** (*Message Queuing Telemetry Transport*).
- **STOMP** (*Simple (or Streaming) Text Oriented Messaging Protocol*).

### 1.1.3 Arquitetura do RabbitMQ
- O ***broker*** é formado pelo **Exchange + Queues**.
- O **Exchange** faz a ligação da mensagem com uma fila que esteja disponível.

### 1.1.4 Fluxo de Funcionamento
1. O **produtor** publica uma mensagem.
2. A mensagem entra no **Exchange**.
3. O **Exchange** roteia a mensagem para a **fila** disponível.
4. A **fila** armazena as mensagens (limitada apenas pelos limites de memória e disco do *host*).
5. O **consumidor** consome a mensagem da fila.

### 1.1.5 Tipos de Exchanges

| TIPO | DESCRIÇÃO |
|------|-----------|
| **Direct Exchange** | Entrega mensagens para uma fila de acordo com uma ***routing key*** |
| **Fanout Exchange** | Entrega mensagens em ***broadcast*** |
| **Topic Exchange** | Compara a ***routing key*** com um padrão; cada fila tem uma chave |
| **Header Exchange** | Utiliza o cabeçalho da mensagem para roteamento |

### 1.1.6 Características Importantes
- Permite a troca de mensagens de forma **assíncrona** (não síncrona).
- Suporta autenticação e autorização conectáveis.
- Suporta **LDAP** e **TLS**.
- Pode ser implantado em nuvens públicas e privadas.
- Pode ser implantado como **clusters** para alta disponibilidade.
- Pode ser **federado** em várias zonas e regiões de disponibilidade.
- Permite a escolha de um **mecanismo de persistência**.
- Porta padrão: **5672**.

> [!CAUTION] OBSERVAÇÃO
> **O RabbitMQ NÃO é exclusivo para Java!** Ele fornece APIs de cliente para diversas linguagens de programação, não apenas Java.

### 1.1.7 Componentes do RabbitMQ
- **Producer:** responsável por enviar mensagens para uma fila.
- **Consumer:** responsável por receber e processar mensagens.
- **Queue:** caixa postal interna que funciona como um grande *buffer* de mensagens.
- **Broker:** intermediário que gerencia as filas e exchanges.

## 1.2 ActiveMQ

### 1.2.1 Visão Geral
- ***Broker* de mensagens *open-source***.
- Versões: **Classic** e **Artemis**.
- Criado pela **Apache Software Foundation** e escrito em **Java**.
- Suporta **filas** e ***pub/sub***.
- Suporta diversos protocolos de mensageria: **OpenWire**, **STOMP**, **MQTT** e **AMQP**.

### 1.2.2 Características
- Grava registros e coleta métricas de mensagens e uso do armazenamento.
- Métricas de armazenamento: uso de memória e disco.
- Métricas de mensagens: número de mensagens aguardando, tempo médio de espera e mensagens expiradas.
- O monitoramento do ActiveMQ em uma máquina local é realizado por meio de uma **console web** acessada a partir de uma URL.

## 1.3 Comparativo – Kafka x RabbitMQ

| ASPECTO | APACHE KAFKA | RABBITMQ |
|---------|--------------|----------|
| **Modelo** | Log de eventos distribuído | Fila de mensagens tradicional |
| **Retenção de mensagens** | Permite retenção por período específico | Fila com consumo imediato |
| **Protocolos** | Próprio (Kafka Protocol) | AMQP, MQTT, STOMP |
| **Linguagem** | Scala/Java | Erlang |
| **Uso típico** | *Streaming* de eventos, alta vazão | Mensageria entre microsserviços |

## 1.4 Tabela Resumo – RabbitMQ

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| **Broker** | Exchange + Queues |
| **Exchange** | Roteia mensagens para filas |
| **Queue** | Armazena mensagens (buffer) |
| **Producer** | Envia mensagens |
| **Consumer** | Recebe e processa mensagens |
| **Porta padrão** | 5672 |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/CNJ/ANALISTA JUDICIÁRIO/APOIO ESPECIALIZADO/ESPECIALIDADE: ANALISTA DE SISTEMAS/2024)

A respeito da plataforma digital do Poder Judiciário brasileiro (PDPJ-Br), julgue o item a seguir.

A solução RabbitMQ para a troca de mensagens entre serviços, utilizada na PDPJ-Br, permite a troca de mensagens de forma síncrona e em tempo real.

**Gabarito:** E (Errado) - O RabbitMQ permite a troca de mensagens de forma **assíncrona**.

## Questão 02
(FCC/TRT/19ª REGIÃO (AL)/TÉCNICO JUDICIÁRIO/APOIO ESPECIALIZADO ESPECIALIDADE: TECNOLOGIA DA INFORMAÇÃO/2027)

Internamente à Plataforma Digital do Poder Judiciário PDPJ-Br, é encorajado que os serviços se comuniquem entre si por meio de troca de mensagens, fazendo uso de um Message Broker. No caso da PDPJ, utiliza-se para isso a solução open source conhecida como

a) Keycloak.
b) Kubernetes.
c) RabbitMQ.
d) TIBCO Enterprise Message Service.
e) RabbitMB.

**Gabarito:** c

## Questão 03
(FCC/TRT – 17ª REGIÃO (ES)/TÉCNICO JUDICIÁRIO/APOIO ESPECIALIZADO ESPECIALIDADE: TECNOLOGIA DA INFORMAÇÃO/2022)

Um Técnico fez a instalação padrão do RabbitMQ em um computador, em condições ideais. O RabbitMQ escutará, na porta padrão

a) 3306.
b) 8081.
c) 1575.
d) 8080.
e) 5672.

**Gabarito:** e - A porta padrão do RabbitMQ é **5672**.

## Questão 04
(FCC/TRT-23ª REGIÃO-MT/TÉCNICO JUDICIÁRIO/APOIO/TECNOLOGIA DA INFORMAÇÃO/2022)

RabbitMQ é um message broker escrito em Java que

a) suporta apenas o protocolo de mensagens AMQP para atender aos requisitos de alta disponibilidade e escalabilidade.
b) não permite escolher um mecanismo de persistência, mas oferece opções para personalizar a segurança para autenticação e autorização.
c) suporta autenticação e autorização conectáveis, suporta LDAP e TLS e pode ser implantado em nuvens públicas e privadas.
d) pode ser implantado como clusters para alta disponibilidade e alta taxa de transferência, mas não pode ser federado em várias zonas e regiões de disponibilidade.
e) fornece APIs de cliente somente para a plataforma Java e frameworks relacionados.

**Gabarito:** c

## Questão 05
(FCC/TRT-5ª REGIÃO (BA)/ANALISTA JUDICIÁRIO/TECNOLOGIA DA INFORMAÇÃO/2022)

No RabbitMQ, o nome dado a uma caixa postal interna que funciona como um grande buffer de mensagem limitado apenas pelos limites de memória e disco do host é

a) producer.
b) queue.
c) consumer.
d) broker.
e) Storage.

**Gabarito:** b - As mensagens são guardadas nas **filas**.

## Questão 06
(IBFC/TRF – 5ª REGIÃO/TÉCNICO JUDICIÁRIO/ÁREA DE APOIO ESPECIALIZADO/ESPECIALIDADE: DESENVOLVIMENTO DE SISTEMAS/2024)

Sobre RabbitMQ, analise as afirmativas abaixo e dê valores Verdadeiro (V) ou Falso (F).

I. ( ) RabbitMQ é um middleware de mensageria open-source que implementa o protocolo Advanced Message Queuing Protocol (AMQP).

II. ( ) O RabbitMQ é exclusivo para a linguagem de programação Java, não oferecendo suporte a outras linguagens de programação.

III. ( ) No RabbitMQ, os produtores são responsáveis por enviar mensagens para uma fila, enquanto os consumidores as recebem e processam.

Assinale a alternativa que apresenta a sequência correta de cima para baixo.

a) F – F – F.
b) F – V – F.
c) V – F – V.
d) V – V – V.

**Gabarito:** c - A afirmativa II é falsa, pois o RabbitMQ **não é exclusivo para Java**.

## Questão 07
(CESPE/CEBRASPE/AGER/MATO GROSSO/ANALISTA REGULADOR/CIÊNCIAS DA COMPUTAÇÃO E OU SISTEMAS DE INFORMAÇÃO/2023)

Assinale a opção que apresenta exemplos de serviços de mensagem em que há agentes que publicam, conhecidos como publishers, e agentes que leem, conhecidos como consumers.

a) RabbitMQ e Kafka.
b) XML-HTTP Request.
c) ZooKeeper e WSDL.
d) SOAP e Ionic.
e) Data lake e Spark.

**Gabarito:** a

## Questão 08
(UFMT/PREFEITURA DE CÁCERES – MT/ANALISTA DE SISTEMAS/2024)

Ao considerar a arquitetura de sistemas de mensageria, qual afirmativa apresenta a diferença entre Apache Kafka e RabbitMQ?

a) Ambos Kafka e RabbitMQ utilizam o modelo de filas, mas Kafka prioriza a entrega garantida e a ordem das mensagens, enquanto RabbitMQ enfatiza a escalabilidade horizontal.
b) RabbitMQ é mais adequado para ambientes de alta latência, em que a consistência imediata é crucial, enquanto Kafka é projetado para otimizar a entrega assíncrona em grande escala.
c) Kafka e RabbitMQ são intercambiáveis em termos de modelo de mensagens, e a escolha entre eles é baseada apenas na preferência do desenvolvedor em relação à linguagem de programação.
d) Kafka segue um modelo de log de eventos distribuído, permitindo a retenção de mensagens por um período específico, enquanto RabbitMQ utiliza uma fila de mensagens tradicional.

**Gabarito:** d

## Questão 09
(FUNDATEC/IF-SC/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/2023)

Um servidor de mensageria é um tipo de servidor que recebe e responde a requests, tem seus próprios recursos e é executado em um ambiente específico. O _____ grava registros e coleta métricas de mensagens e uso do armazenamento. As métricas de armazenamento incluem uso de memória e disco. As métricas de mensagens incluem o número de mensagens aguardando, o tempo médio de espera e as mensagens expiradas. Assinale a alternativa que preenche corretamente a lacuna do trecho acima.

a) RGW.
b) ActiveMQ.
c) Minio.
d) Memcached.
e) Redis.

**Gabarito:** b

## Questão 10
(CESPE/CEBRASPE/SEPLAG-CE/ANALISTA DE GESTÃO PÚBLICA/CIÊNCIA DA COMPUTAÇÃO/2024)

No que se refere a ferramentas de integração assíncronas, julgue o item a seguir.

O monitoramento do serviço ActiveMQ em uma máquina local é realizado por meio de uma console web acessada a partir de uma URL.

**Gabarito:** C (Correto)

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | c |
| 03 | e |
| 04 | c |
| 05 | b |
| 06 | c |
| 07 | a |
| 08 | d |
| 09 | b |
| 10 | C |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*