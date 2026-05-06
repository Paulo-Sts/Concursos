# Anotações

# APACHE KAFKA

## 1. Conceito e Propósito do Apache Kafka

### 1.1 O que é Mensageria e o Papel do Kafka

- **Sistema de Mensageria:** Sistema que atua como intermediário na comunicação entre **produtores** (quem gera/envia a mensagem) e **consumidores** (quem recebe/processa a mensagem).
- **Apache Kafka:** Plataforma de código aberto de ***streaming*** de eventos distribuída. Funciona como um sistema de mensageria altamente escalável.
- **Objetivo:** Mediar a relação entre produtores e consumidores de dados de forma **desacoplada**, garantindo que as mensagens sejam armazenadas de forma segura, íntegra e durável até que os consumidores possam processá-las. A comunicação é **assíncrona**.

## 2. Arquitetura e Componentes Principais

### 2.1 Modelos de Mensageria

- **Modelo em Fila (*Queue-based*):** Os consumidores recebem as mensagens em uma fila; cada mensagem é processada por apenas um consumidor do grupo.
- **Modelo Pub/Sub (*Publish-Subscribe*):** Os produtores publicam mensagens em um tópico, e todos os consumidores que assinam aquele tópico podem receber as mensagens.

### 2.2 Componentes do Ecossistema Kafka

| COMPONENTE | DEFINIÇÃO |
| :--- | :--- |
| ***Broker*** | Um servidor Kafka que armazena as mensagens. Um *cluster* Kafka é composto por múltiplos *brokers*. Se precisar de mais espaço, adicionam-se novos *brokers*. |
| **Tópico (*Topic*)** | Categoria para onde as mensagens são enviadas. Funciona como uma fila. Um tópico pode ter múltiplos produtores e consumidores. |
| **Partição (*Partition*)** | Subdivisão de um tópico para aumentar o paralelismo e a escalabilidade. As mensagens em uma partição são **ordenadas** e imutáveis. |
| **Produtor (*Producer*)** | Aplicativo que envia (publica) mensagens para um tópico Kafka. |
| **Consumidor (*Consumer*)** | Aplicativo que lê (assina) mensagens de um ou mais tópicos. |
| ***Offset*** | Identificador único sequencial de uma mensagem dentro de uma partição. Marca a posição de leitura de cada consumidor. |
| **Grupo de Consumidores** | Conjunto de consumidores que cooperam para consumir as mensagens de um tópico, garantindo que cada mensagem seja processada uma única vez pelo grupo. |

### 2.3 Características das Mensagens e da Arquitetura

- **Imutabilidade:** Uma vez escritas em uma partição, as mensagens são **imutáveis** e não podem ser modificadas.
- **Ordenação:** As mensagens são entregues na ordem em que foram produzidas **dentro de cada partição**.
- **Durabilidade e Persistência:** As mensagens são armazenadas em disco de forma durável (o Kafka é um armazenamento distribuído), garantindo que não se percam.
- **APIs do Kafka (4 formas de interação):**
    1.  ***Producer API*:** Para enviar mensagens.
    2.  ***Consumer API*:** Para ler mensagens.
    3.  ***Connect API*:** Para integrar o Kafka com outras fontes de dados (ex: bancos de dados relacionais).
    4.  ***Streams API*:** Para processar os fluxos de eventos em tempo real.

## 3. Análise de Questões de Concurso

### 3.1 API de Integração com BD Relacionais (FGV/PGM – NITERÓI/2023)

- **Enunciado:** Mecanismos de integração com outros sistemas (captura de dados relacionais) são baseados em qual API?
- **Gabarito:** **B) Connect.**
- **Análise:** A **API Connect** é a interface específica do Kafka para criar conectores que integram o Kafka com sistemas externos, como bancos de dados.

### 3.2 Componentes Arquitetônicos (FGV/CÂMARA DOS DEPUTADOS/2023)

- **Enunciado:** "Os eventos no tópico são imutáveis, o que significa que não podem ser modificados depois de escritos."
- **Gabarito:** **C (Correta).**
- **Análise:** A imutabilidade do evento/mensagem é uma característica central do Kafka. Uma vez armazenado, o dado não se altera.

### 3.3 Expansão da Camada de Persistência (FGV/TCE – SP/2023)

- **Enunciado:** Para expandir o espaço de armazenamento e aumentar a escalabilidade, deve-se prover mais:
- **Gabarito:** **B) brokers.**
- **Análise:** Os *brokers* são os servidores que armazenam os dados. Expandir o *cluster* Kafka significa adicionar mais *brokers*, o que aumenta a capacidade de armazenamento e processamento.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (CESPE/SEFAZ-CE) | **C** | Kafka provê mensageria assíncrona com produtores e consumidores desacoplados. |
| **2** (CESPE/SERPRO) | **E** | O armazenamento durável é imprescindível no Kafka. |
| **3** (FGV/PGM – NITERÓI) | **B** | A API Connect é usada para integrar o Kafka com sistemas como bancos de dados. |
| **4** (FGV/CÂMARA DEPUTADOS) | **C** | Mensagens em um tópico são imutáveis. |
| **5** (FGV/TCE – SP) | **B** | Para persistência e escalabilidade, aumenta-se o número de *brokers*. |