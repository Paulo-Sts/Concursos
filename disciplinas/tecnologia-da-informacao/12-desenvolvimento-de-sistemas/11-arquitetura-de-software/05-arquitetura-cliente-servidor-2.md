# Arquitetura Cliente-Servidor 2

## 1. Comunicação Cliente-Servidor

### 1.1 Modelo Solicitação-Resposta
- A interação entre cliente e servidor é baseada no modelo solicitação-resposta.
- Funcionamento: o cliente envia uma solicitação, o servidor a recebe e a processa, executa uma lógica de negócios e devolve uma resposta ao usuário.
- A comunicação pode ocorrer de duas formas: síncrona ou assíncrona.

### 1.2 Comunicação Síncrona
- O cliente envia uma solicitação ao servidor e aguarda uma resposta antes de continuar outras operações.
- O usuário fica com as ações bloqueadas até que a próxima etapa seja desbloqueada.
- A comunicação síncrona depende de uma resposta para prosseguir.
- Exemplo: requisição *HTTP GET* para carregar uma página na internet. Não é possível interagir com o site até que a interface do usuário seja carregada.

### 1.3 Comunicação Assíncrona
- O usuário envia uma solicitação para o servidor, que pode demorar para devolver uma resposta, mas o usuário não fica impossibilitado de realizar outras operações no sistema.
- Solicitações assíncronas são ideais para operações que podem levar algum tempo para serem processadas ou cuja resposta não seja necessária de forma imediata.
- Exemplo: AJAX (*Asynchronous JavaScript and XML*). Partes de uma página na internet são carregadas sem que seja necessário recarregá-la por inteiro, permitindo que o usuário continue realizando outras ações.

> [!CAUTION] OBSERVAÇÃO: 
> Na comunicação síncrona, o cliente aguarda a resposta do servidor e fica bloqueado. Na comunicação assíncrona, o cliente continua suas operações enquanto aguarda a resposta.

## 2 Arquitetura Multicamadas (*N-Tier*)

### 2.1 Definição
- Também conhecida como arquitetura em camadas.
- Trata-se de uma extensão da arquitetura cliente-servidor, em que a aplicação é dividida em várias camadas.
- É evoluída, podendo ser utilizada de forma independente da arquitetura cliente-servidor.

### 2.2 Arquitetura 2-Tier (Duas Camadas)
- Cliente (interface do usuário).
- Servidor (processamento e lógica de negócios).
- Na 2-Tier, a parte de processamento da lógica de negócios pode ficar na parte de interface do usuário ou na parte de dados.

### 2.3 Arquitetura 3-Tier (Três Camadas)
- É a forma mais comum de separação de projetos, porque cada camada detém uma responsabilidade específica.

| CAMADA | RESPONSABILIDADE |
|--------|------------------|
| Apresentação | Interage com o usuário (aquilo que o usuário vê) |
| Negócios | Processa as regras do negócio; garante que as solicitações do usuário estejam de acordo com o que o sistema espera receber |
| Dados | Gerencia o acesso e a manipulação de dados |

### 2.4 Arquitetura N-Tier (Múltiplas Camadas)
- Possui as três camadas básicas e uma ou mais camadas auxiliares.
- Exemplos de camadas adicionais:
  - Camada de Serviço (API RESTful, microsserviços).
  - Camada de Integração (conectores API).
  - Camada de Cache (Redis, HTTP).

### 2.5 Arquitetura 4-Tier (Quatro Camadas)
- Cliente (acesso/navegação) ⟶ Servidor Web (apresentação) ⟶ Servidor de Aplicações (lógica/negócios) ⟶ Servidor de Banco de Dados (dados).

| ORDEM | CAMADA | SERVIDOR CORRESPONDENTE |
|-------|--------|-------------------------|
| I | Acesso/navegação | Clientes (*browsers*) |
| II | Dados | Servidor de Banco de Dados |
| III | Apresentação | Servidor Web |
| IV | Lógica/Negócios | Servidor de Aplicações |

> [!TIP] DICAS: 
> Na arquitetura 4-Tier, a ordem correta é: Cliente ⟶ Servidor Web (apresentação) ⟶ Servidor de Aplicações (lógica) ⟶ Servidor de Banco de Dados (dados).

> [!CAUTION] OBSERVAÇÃO: 
> Na arquitetura C/S multicamada, a mesma aplicação pode atuar simultaneamente como servidor e como cliente para outras aplicações. Exemplo: a Camada de Lógica de Negócios atua como servidor para o cliente, mas como cliente para a Camada de Dados.

## 3. Redes *Peer-to-Peer* (P2P)

### 3.1 Definição
- Redes de computadores em que cada nó atua, simultaneamente, como cliente e servidor.
- Permite comunicação direta entre os nós da rede.
- Surgem como uma proposta de descentralização do monopólio de processamento funcional, fazendo com que sistemas sirvam a outros sistemas, dando a cada estação as mesmas responsabilidades e capacidades dentro da rede.

### 3.2 Características

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Descentralização | Não há necessidade de um servidor central, porque cada nó funciona como cliente e como servidor |
| Igualdade entre os nós | Todos os nós possuem as mesmas capacidades, podendo agir como cliente e como servidor |
| Escalabilidade | Facilita a evolução do sistema |
| Redundância | Dados replicados em vários nós, garantindo disponibilidade mesmo em caso de falha |
| Autonomia | Cada nó opera de forma independente e se adapta, dinamicamente, às mudanças e condições da rede |
| Independência | Cada nó pode operar de forma independente |

> [!CAUTION] OBSERVAÇÃO: 
> Enquanto na arquitetura cliente-servidor a dependência do servidor central é uma desvantagem (se o servidor cai, o sistema para), nas redes P2P não existe esse risco, pois todos os nós podem atuar como servidores.

### 3.3 Tipos de Rede P2P

#### 3.3.1 Estruturadas
- Possuem uma estrutura de dados bem definida, como o DHT (*Distributed Hash Table*), para organizar e localizar recursos de forma eficiente.
- Cada nó detém uma chave única.
- A localização e recuperação de informações são fáceis por meio da chave única de cada nó.

#### 3.3.2 Não Estruturadas
- Não possuem uma estrutura predefinida para a organização dos nós.
- A localização é feita por meio de algoritmos de busca.
- A solicitação de recurso é enviada para todos os nós vizinhos aos quais o nó específico esteja solicitando.

#### 3.3.3 Híbridas
- Possuem características tanto das redes estruturadas quanto das não estruturadas.

### 3.4 Comparação: Cliente-Servidor x P2P

| CARACTERÍSTICA | CLIENTE-SERVIDOR | PEER-TO-PEER (P2P) |
|----------------|------------------|---------------------|
| Servidor central | Sim | Não |
| Papel dos nós | Cliente ou servidor | Ambos (cliente e servidor) |
| Dependência | Alta (se o servidor cai, o sistema para) | Baixa (redundância) |
| Centralização | Centralizada | Descentralizada |
| Exemplo | Aplicações *web*, bancos de dados | Torrent, redes de compartilhamento |

## 4. Questões de Fixação

### Questão 04
(2021/SELECON/EMGEPRON/ANALISTA TÉCNICO-SEGURANÇA DA INFORMAÇÃO) A arquitetura cliente/servidor é aquela na qual o processamento da informação é dividido em módulos ou processos distintos. Um processo é responsável pela manutenção da informação (servidor), enquanto outro é responsável pela obtenção dos dados (cliente). Neste contexto, a figura abaixo ilustra a arquitetura em 4 camadas, por meio da qual o cliente informa a URL por meio do *browser* e o servidor de aplicações analisa a requisição do usuário, determina de que forma os dados serão utilizados, acessa os serviços e devolve uma resposta.

As aplicações são:
I – Acesso – navegação por meio de *browsers*.
II – Dados – com todas as informações necessárias.
III – Apresentação – onde serão feitas as alterações de interface.
IV – Lógica – onde serão feitas as alterações nas regras do negócio, quando necessárias.

Se a aplicação em I corresponde a Clientes, as demais em II, III e IV correspondem, respectivamente, aos servidores:

a) de Banco de Dados, Web e de Aplicações
b) de Banco de Dados, de Aplicações e Web
c) de Aplicações, de Banco de Dados e Web
d) de Aplicações, Web e de Banco de Dados

Gabarito: A.
- II (Dados) ⟶ Servidor de Banco de Dados.
- III (Apresentação) ⟶ Servidor Web.
- IV (Lógica) ⟶ Servidor de Aplicações.

### Questão 05
(2021/CESPE-CEBRASPE/PG-DF/TÉCNICO JURÍDICO - TECNOLOGIA E INFORMAÇÃO) A respeito da arquitetura cliente/servidor (C/S) em multicamadas, julgue o item subsequente. Na arquitetura C/S multicamada, a mesma aplicação pode atuar simultaneamente como servidor e como cliente para outras aplicações.

Gabarito: Certo (C). A Camada de Lógica de Negócios atua como servidor para o cliente, mas como cliente para a Camada de Dados.

### Questão 06
(2022/IESES/SAP-SC/INSTRUTOR DE INFORMÁTICA) Sobre os Conceitos da arquitetura cliente-servidor, assinale a alternativa correta.

I – A arquitetura cliente servidor é uma arquitetura de aplicação distribuída, ou seja, na rede existem os fornecedores de recursos ou serviços a rede, que são chamados de servidores, e existem os requerentes dos recursos ou serviços, denominados clientes.
II – O cliente não compartilha nenhum de seus recursos com o servidor, mas, no entanto, ele solicita alguma função do servidor, sendo ele, o cliente, responsável por iniciar a comunicação com o servidor, enquanto o mesmo aguarda requisições de entrada.
III – A sobrecarga de servidores é um problema real, apesar de a capacidade dos servidores ter aumentado consideravelmente na última década.
IV – As redes P2P surgem como uma proposta de descentralização do monopólio de processamento funcional, fazendo com que sistemas sirvam a outros sistemas, dando a cada estação as mesmas responsabilidades e capacidades dentro da rede.

a) Apenas as assertivas I, II e III são corretas.
b) Apenas as assertivas I, III e IV são corretas.
c) Apenas as assertivas I e III são corretas.
d) Apenas as assertivas II e IV são corretas.
e) As assertivas I, II, III e IV são corretas.

Gabarito: E. Todas as assertivas estão corretas.
- I: define corretamente o papel do cliente e do servidor.
- II: define como funciona a solicitação do cliente para o servidor.
- III: sobrecarga de servidores é um problema real, mesmo com o aumento da capacidade.
- IV: as redes P2P servem para descentralizar o processamento, dando a cada nó as mesmas responsabilidades e capacidades.

### GABARITO OFICIAL

| QUESTÃO | GABARITO |
|---------|----------|
| 04 | A |
| 05 | C |
| 06 | E |

> [!TIP] DICAS: 
> - Comunicação síncrona: cliente aguarda resposta (bloqueado).
> - Comunicação assíncrona: cliente não aguarda resposta (não bloqueado).
> - 3-Tier: Apresentação - Negócios - Dados.
> - 4-Tier: Cliente ⟶ Web (apresentação) ⟶ Aplicação (lógica) ⟶ Banco de Dados.
> - P2P: cada nó é cliente e servidor simultaneamente; descentralizado; redundante.