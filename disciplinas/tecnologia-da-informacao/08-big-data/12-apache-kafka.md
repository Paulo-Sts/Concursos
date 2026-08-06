# Apache Kafka

## 1. Fundamentos de Mensageria
- Apache Kafka é um sistema de streaming em tempo real que recebe e processa mensagens de forma assíncrona.
- Funciona como um mediador entre produtores (quem envia mensagens) e consumidores (quem processa os dados).
- O produtor e o consumidor são desacoplados, ou seja, atuam de forma independente.
- Exemplo: floricultura online no dia dos namorados - muitos pedidos simultâneos e poucos atendentes disponíveis.
- Kafka armazena os pedidos de maneira segura, íntegra e confiável, garantindo que sejam processados conforme a disponibilidade dos consumidores.

### 1.1 Importância do Servidor de Mensagens
- Em sistemas de e-commerce, as transações são persistidas em banco de dados em tempo real.
- Se o banco de dados estiver fora do ar, a transação não é concluída.
- Para evitar esse problema, instala-se um servidor de mensagens (Kafka) entre o cliente e o banco.
- As compras são gerenciadas por software intermediário, e as informações são depositadas no banco posteriormente.

### 1.2 Modelos de Mensageria
- Modelo em fila (Queue-based Model):
  - O produtor gera uma fila armazenada no broker (Kafka).
  - Os consumidores processam as mensagens em ordem de fila.
  - Se o consumidor 1 processa as mensagens 1 e 2, o consumidor 2 não tem acesso a elas.
- Modelo Pub/Sub (Publisher/Subscriber):
  - O usuário publica mensagens em um tópico.
  - Os assinantes (consumidores) têm acesso a todas as mensagens publicadas.
  - Exemplo: blogs, onde uma pessoa posta e várias pessoas leem.

## 2. Características da Mensageria
- Desacoplamento: produtor e consumidor atuam de forma independente.
- Durabilidade: as mensagens não correm risco de se perderem.
- Confiabilidade na entrega: garantia de que todas as mensagens serão lidas assíncronamente.
- Comunicação assíncrona: a mensagem é entregue quando o consumidor estiver disponível.
- Roteamento de mensagens: gerenciamento da distribuição entre os consumidores.
- Persistência de mensagens: as mensagens são armazenadas no broker.

> [!TIP] DICAS:
> - Desacoplamento e comunicação assíncrona são os pilares do Kafka.
> - A durabilidade é garantida pelo armazenamento no broker.

## 3. Apache Kafka: Visão Geral

### 3.1 Definição e Origem
- Projeto de código aberto mantido pela Apache Software Foundation.
- Originalmente desenvolvido pela LinkedIn.

### 3.2 Usos Principais
- Sistema de processamento de streams.
- Plataforma de mensagens distribuída.
- Sistema de armazenamento distribuído.
- Agregação de log (registros para auditoria posterior).

### 3.3 Papéis no Kafka
- Produtores: enviam mensagens para os tópicos do Kafka.
- Consumidores: leem mensagens de um ou mais tópicos.
- Consumidores podem se organizar em grupos para dividir a leitura, garantindo que cada mensagem seja processada uma única vez.

## 4. Estrutura de Armazenamento

### 4.1 Tópicos
- Categorias para organizar as mensagens.
- Similar a uma fila, mas com capacidades mais ricas.
- Um tópico pode ter múltiplos produtores e consumidores.
- Vários produtores podem enviar mensagens para o mesmo tópico.

### 4.2 Partições
- Cada tópico pode ser dividido em várias partições para aumentar a escalabilidade.
- As mensagens são entregues na ordem em que são produzidas dentro de cada partição.
- Partição é uma subdivisão do tópico.

### 4.3 Offset
- Posição que cada consumidor está consumindo na fila.
- A primeira mensagem recebe offset 0, a segunda offset 1, e assim sucessivamente.
- Produtores inserem mensagens no término de cada partição.
- Consumidores leem da esquerda para a direita.

> [!CAUTION] OBSERVAÇÃO:
> - As mensagens, uma vez escritas, são imutáveis, garantindo a integridade dos dados.
> - Broker é o Apache Kafka, local onde as mensagens são armazenadas e organizadas por tópicos e partições.

### 4.4 Esquema de Funcionamento
- Tópico: categoria das mensagens.
- Partições: divisões do tópico (cada uma é uma fila com mensagens armazenadas).
- Producer: produtor das mensagens.
- Consumer: consumidor das mensagens.
- Offset: posição de leitura do consumidor na fila.

## 5. Application Programming Interface (API)

### 5.1 Tipos de API
- Producer API: aplicativos que geram mensagens de dados para serem processadas.
- Consumer API: consumidor que retira mensagens de dentro do Kafka.
- Connector API: conectores para integração com bancos de dados e outros sistemas.
- Streams API: processamento de dados em tempo real.

> [!TIP] DICAS:
> - Producer API: produz mensagens e envia para o Kafka.
> - Consumer API: consome mensagens das partições do Kafka.
> - Streams API: processamento em tempo real sem mensageria.
> - Connector API: conexão com bases de dados.

## 6. Analogia para Compreensão
- Tópico: edição geral do jornal.
- Partições: cada seção do jornal.
- Produtores: jornalistas.
- Mensagem: notícia.
- Consumidores: leitores.

## 7. Componentes Arquitetônicos do Kafka

### 7.1 Relacionamento entre Componentes
- Os tópicos são divididos em partições.
- Um tópico pode ter diversos produtores e diversos consumidores.
- A imutabilidade das mensagens publicadas e consumidas garante que o dado não será alterado.
- O produtor define em qual partição a mensagem deve ser inserida.
- Os consumidores não recebem as mensagens necessariamente na ordem de envio, pois cada fila (partição) tem seu próprio rol de consumo.

### 7.2 Escalabilidade e Persistência
- Quando há necessidade de mais espaço de armazenamento, é necessário aumentar o cluster distribuído de brokers.
- Broker = Apache Kafka (onde as mensagens são armazenadas).