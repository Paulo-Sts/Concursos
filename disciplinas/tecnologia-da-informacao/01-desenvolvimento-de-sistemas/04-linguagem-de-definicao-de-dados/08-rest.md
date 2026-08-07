# REST

## 1. Arquiteturas de Referência
- Arquitetura de referência é um conjunto que impõe restrições ao desenvolvimento de software em organizações.
- Visa alcançar objetivos derivados de um estilo arquitetural específico.
- Cada arquitetura possui características próprias, vantagens e desvantagens.

### Tabela Comparativa de Arquiteturas
| ARQUITETURA | PRINCIPAIS CARACTERÍSTICAS | VANTAGENS | DESVANTAGENS |
|-------------|----------------------------|-----------|--------------|
| Monolítica | Aplicação única e indivisível | Simplicidade, fácil desenvolvimento | Escalabilidade e manutenção |
| Microserviços | Serviços pequenos e independentes, comunicação por APIs | Escalabilidade, flexibilidade tecnológica | Complexidade no gerenciamento, comunicação |
| MVC | Model, View e Controller | Separation of Concerns (SoC) | Pode ser complexo de implementar |
| REST | Recursos URIs, uso de operações HTTP | HTTP padrão, escalabilidade | Operações complexas, segurança |
| SOA | Serviços autônomos e reutilizáveis, mensagens | Reuso, integração entre sistemas | Complexidade na gestão e segurança |
| Cliente-Servidor | Lógica entre cliente (interface) e servidor (dados) | Centralização da lógica de negócios | Escalabilidade horizontal |
| Serverless | Executa código sob demanda sem gerenciamento de servidores | Escalabilidade automática, redução de custos operacionais | Dependência do provedor de nuvem, latência inicial |

> [!TIP] DICAS:
> - Microserviços são serviços pequenos e independentes que se comunicam por APIs.
> - Serverless reduz custos operacionais, mas gera dependência do provedor de nuvem.

## 2. Arquitetura REST
- REST (Representational State Transfer) é um estilo arquitetural para comunicação entre sistemas na web.
- Sucedeu o SOAP, que é uma notação complexa, robusta e burocrática que faz uso de XML.
- SOAP atualmente é restrito a nichos em que a segurança é primordial (ex.: hotelaria, sistemas de passagens aéreas).
- REST baseia-se em princípios de simplicidade, escalabilidade e interoperabilidade.

> [!CAUTION] OBSERVAÇÃO:
> - REST é um estilo arquitetural, NÃO um protocolo.
> - REST NÃO é dependente de protocolo HTTP para ser definido, embora seja mais comum com HTTP.

### 2.1 Principais Características do REST
- Stateless: cada requisição do cliente deve conter todas as informações necessárias para o servidor processar a solicitação.
- Cacheable: respostas do servidor podem ser armazenadas em cache para melhorar a performance.
- Interface uniforme: utiliza métodos HTTP padrão (GET, POST, PUT, DELETE).
- Recursos: cada recurso é identificado por um URI (Uniform Resource Identifier).
- Multiformatos: suporta JSON, XML, YAML, texto, embora o JSON seja o mais comum.

> [!CAUTION] OBSERVAÇÃO:
> - REST É stateless, ou seja, não mantém estado entre requisições.
> - REST É cacheable, permitindo armazenamento de respostas em cache.
> - REST NÃO utiliza arquitetura par-a-par (peer to peer / p2p).

### 2.2 JSON (JavaScript Object Notation)
- JSON é um formato de intercâmbio de dados leve e de fácil leitura.
- É utilizado para transmitir dados entre cliente e servidor em APIs RESTful.
- Estrutura:
  - Objetos delimitados por chaves: { }
  - Propriedades inseridas entre aspas duplas.
  - Listas delimitadas por colchetes: [ ]

> [!CAUTION] OBSERVAÇÃO:
> - JSON não é o único formato das mensagens REST, apesar de ser o mais utilizado.

## 3. Interface Uniforme – Métodos HTTP
- O cliente (browser) faz requisições HTTP.
- A REST API obtém informações do banco de dados e devolve por JSON ou XML.

### 3.1 Métodos HTTP
- GET (READ): recupera dados do servidor; usado para ler informações, sem modificar o estado do recurso.
- POST (CREATE): envia dados ao servidor para criar um novo recurso; usado para adicionar novas informações.
- PUT (UPDATE): atualiza dados existentes no servidor; usado para modificar informações de um recurso específico.
- DELETE: remove dados do servidor; usado para deletar um recurso específico.

> [!TIP] DICAS:
> - GET é utilizado para leitura de informações.
> - POST é utilizado para criação de novos recursos.
> - PUT é utilizado para atualização de recursos existentes.
> - DELETE é utilizado para remoção de recursos.

### 3.2 Exemplos de Requisições REST com JSON

#### 3.2.1 POST (Criação)
- Requisição POST para o recurso "/tarefas" seguida pelo protocolo HTTP/1.1.
- Host: api.exemplo.com/tarefas.
- Corpo da requisição em JSON:
  ```json
  {
    "titulo": "Pagar Creche",
    "completed": false
  }
  ```

#### 3.2.2 GET (Leitura)
- Requisição GET é mais simples, apenas solicitando o recurso.
- Resposta em JSON:
  ```json
  [
    {
      "id": 1,
      "titulo": "Pagar Creche",
      "completed": false
    }
  ]
  ```

#### 3.2.3 PUT (Atualização)
- Requisição PUT semelhante ao POST, mas atualiza o recurso.
- Corpo da requisição descreve o conteúdo atualizado:
  ```json
  {
    "titulo": "Pagar Creche",
    "completed": true
  }
  ```

#### 3.2.4 DELETE (Remoção)
- Requisição DELETE indica o que será deletado:
  ```
  DELETE /tarefas/1 HTTP/1.1
  Host: api.exemplo.com
  ```
- A API pode retornar uma mensagem de sucesso.

> [!TIP] DICAS:
> - Em REST, os recursos são identificados por URIs (ex.: /tarefas/1).
> - A depender do verbo utilizado (POST ou PUT), a requisição pode ter um corpo.

## 4. Conceitos Cobrados em Provas

### 4.1 Afirmações Corretas sobre REST
- Serviços REST são stateless: cada solicitação deve conter todas as informações necessárias para ser compreendida pelo servidor.
- REST é independente do protocolo de transporte, podendo ser implementado com HTTP, SMTP ou JMS (embora HTTP seja o mais comum).
- REST é um estilo arquitetural que promove a interoperabilidade entre sistemas.
- Cada aplicação em REST é um conjunto de recursos sobre os quais podemos realizar ações.
- Os formatos utilizados em REST podem ser JSON, XML ou YAML.

### 4.2 Afirmações Incorretas sobre REST
- REST NÃO é um protocolo para troca de mensagens entre componentes de uma aplicação web.
- REST NÃO utiliza SOAP e XML como protocolo.
- REST NÃO utiliza arquitetura par-a-par (p2p).
- REST NÃO mantém informações de estado entre requisições.
- REST NÃO deixa de usar cache no cliente (é cacheable).
- Em REST, os conectores NÃO precisam reter o estado das aplicações entre as requisições.

> [!CAUTION] OBSERVAÇÃO:
> - A afirmativa "REST utiliza SOAP e XML" está incorreta, pois REST utiliza JSON e HTTP.
> - A afirmativa "REST utiliza recurso não identificável" está incorreta, pois os recursos devem ser identificados por URI.
> - A afirmativa "REST consiste em estilo baseado em complexa interação cliente/servidor" está incorreta, pois as interações são simples.
> - REST É stateless, portanto não mantém estado entre requisições.

### 4.3 Características do REST
- Utiliza os métodos HTTP: GET, POST, PUT e DELETE.
- Pode ser utilizado para implementar WebServices de baixo overhead (baixo consumo de recursos computacionais).
- Todo recurso REST deve conter uma URI (identificador único).

### 4.4 Exemplo Prático de Chamada REST
- Para saber o saldo de um cliente bancário identificado como cliente 23232, a chamada REST seria:
  ```
  http://app.banco.com/contascorrentes/saldo/cliente/23232
  ```
- A chamada REST faz uso de HTTP e o recurso é indicado em um endereço (URI).