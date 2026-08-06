# Mensageria e Apache Kafka

## 1. Fundamentos da Mensageria
- Sistemas de mensageria são baseados na troca de mensagens entre diferentes sistemas para atender à necessidade de processamento de grandes bases de dados em tempo real.
- O serviço de mensageria tem como função primordial o desacoplamento entre o produtor da informação e o seu respectivo consumidor.
- Essa arquitetura oferece a garantia de que os dados produzidos não sejam perdidos, mesmo quando a produção ocorre em grande escala temporária.
- Exemplo didático ⟶ em sistemas de e-commerce, a adição de um servidor de mensagens evita que os registros de pedidos sejam inseridos diretamente no banco de dados, criando uma fila gerenciada.

> [!TIP] DICAS: 
> - A mensageria permite a integração entre sistemas com tecnologias distintas (ex: sistema em tecnologia x conversando com tecnologia y) de forma agnóstica.

## 2. Modelos de Mensageria
- A organização do fluxo de dados pode seguir diferentes padrões de distribuição conforme o objetivo do sistema.

### 2.1 Modelo em Fila
- Conhecido como queue-based model, caracteriza-se por permitir que cada mensagem produzida seja consumida por apenas um único consumidor.

### 2.2 Modelo Pub/Sub
- Modelo de publicação e assinatura onde cada subscritor de um tópico de mensagens possui sua própria fila independente.
- Nesse formato, todos os consumidores inscritos no tópico têm acesso à totalidade das mensagens disponibilizadas.

## 3. Características Técnicas e Funcionais
- Desacoplamento ⟶ separação entre as responsabilidades de quem produz e quem consome o dado;
- Durabilidade ⟶ armazenamento das mensagens em sistemas intermediários para evitar perdas;
- Confiabilidade na entrega ⟶ processos que garantem que a mensagem chegue ao destino;
- Roteamento de mensagens ⟶ capacidade de direcionar os dados e realizar o balanceamento de carga entre os diversos consumidores de acordo com a capacidade de processamento;
- Comunicação assíncrona ⟶ as interações não ocorrem em tempo real, permitindo que o sistema continue operando enquanto aguarda o processamento, semelhante ao whatsapp;
- Persistência ⟶ utilização da fila como um sistema de armazenamento para as mensagens em trânsito.

## 4. Plataforma Apache Kafka
- Trata-se de um projeto de código aberto da Apache Software Foundation, originalmente desenvolvido pela empresa LinkedIn.
- Opera como um modelo de log de eventos distribuído que permite a retenção de mensagens por períodos determinados.
- É amplamente utilizado como sistema de processamento de streams, plataforma de mensagens distribuída e sistema de armazenamento distribuído.

### 4.1 Arquitetura e Componentes do Kafka
- Broker ⟶ local físico ou lógico onde as mensagens ficam efetivamente armazenadas no sistema;
- Tópicos ⟶ conjuntos de mensagens organizados em filas independentes onde o produtor lança seus dados;
- Partições ⟶ subdivisões de um tópico que possuem sua própria estrutura de mensagens;
- Offset ⟶ marcador que identifica a posição ou sequencial de uma mensagem que um consumidor está lendo em determinado momento.

### 4.2 Interfaces de Programação (API)
- Producer API ⟶ responsável por produzir a mensagem e encaminhá-la para o kafka cluster;
- Consumer API ⟶ utilizada por aplicativos que recebem e processam as mensagens;
- Streams API ⟶ focada no tratamento de fluxos de dados em tempo real;
- Connector API ⟶ utilizada para integração com outros sistemas, como bancos de dados, para armazenamento ou captura de informações.

## 5. Comparativo de Elementos Arquitetônicos
| COMPONENTE | FUNÇÃO NO SISTEMA | CARACTERÍSTICA PRINCIPAL |
|---|---|---|
| PRODUTOR | Gerar e enviar eventos | Pode haver mais de um para o mesmo tópico |
| BROKER | Camada de persistência | Armazena os streams de eventos |
| TÓPICO | Agrupamento lógico | Formado por diversas partições |
| CONSUMIDOR | Ler e processar eventos | Localizado através do offset na partição |

> [!CAUTION] OBSERVAÇÃO: 
> - Em provas de concurso, destaque que o Apache Kafka provê integração assíncrona onde produtores e consumidores são totalmente desacoplados.
> - Importante ⟶ as mensagens ou eventos registrados em um tópico são imutáveis, o que significa que não podem ser alterados após a escrita.
> - O Apache Kafka pode reter mensagens por um período específico, mas não prescinde obrigatoriamente do armazenamento durável para processar fluxos de eventos.