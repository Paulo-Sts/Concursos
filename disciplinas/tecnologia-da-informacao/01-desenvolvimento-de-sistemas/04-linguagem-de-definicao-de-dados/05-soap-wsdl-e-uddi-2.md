# Tecnologias XML: SOAP, WSDL e UDDI 2

## 1. SOAP (Simple Object Access Protocol)
- Protocolo utilizado para troca de mensagens entre aplicações, codificando as mensagens em formato XML.
- Responsável por transportar mensagens entre aplicações, geralmente utilizando o protocolo HTTP.
- Estrutura de uma mensagem SOAP:
  - `<soap:Body>`: Tag que contém os dados da requisição ou resposta propriamente dita.
  - `<soap:Header>`: Tag que contém informações adicionais, como autenticação e metadados.
  - `<soap:Fault>`: Tag utilizada para informar erros na comunicação.

### 1.1 Exemplo de Mensagem SOAP
- Requisição enviada ao servidor para obter dados de um processo:
  ```xml
  <soap:Body>
    <m:GetProcesso xmlns:m="https://www.tjsc.jus.br/processo">
      <m:NumeroProcesso>20120385259</m:NumeroProcesso>
    </m:GetProcesso>
  </soap:Body>
  ```
- A tag `<soap:Body>` é obrigatória para realizar requisições SOAP.

> [!TIP] DICAS:
> - `<soap:Body>` é a tag que faz a requisição dos dados. É o elemento central de qualquer mensagem SOAP.
> - `<soap:Fault>` é usado exclusivamente para tratamento de erros, indicando falhas na comunicação.

## 2. WSDL (Web Services Description Language)
- Linguagem baseada em XML usada para descrever serviços web e como acessá-los.
- Especifica a localização do serviço e as operações (métodos) que o serviço expõe.
- Facilita a comunicação entre diferentes aplicações ao descrever como se conectar e interagir com os serviços.

### 2.1 Estrutura de um Documento WSDL
- Os documentos WSDL devem conter os seguintes elementos principais:

| ELEMENTO | FUNÇÃO |
|----------|--------|
| Types | Define os tipos de dados usados nas mensagens (geralmente utilizando XML Schema). |
| Message | Define a estrutura de dados de cada mensagem, especificando as partes que a compõem. |
| PortType | Define o conjunto abstrato de operações (métodos) que o serviço implementa. |
| Binding | Especifica como as mensagens são formatadas e transmitidas, utilizando o protocolo SOAP. |
| Service | Define o endereço (endpoint) onde o serviço pode ser acessado na rede. |

#### 2.1.1 Definitions
- Elemento raiz de qualquer documento WSDL.
- Contém todas as definições do serviço, incluindo tipos, mensagens, portTypes, bindings e informações de serviço.
- Define os namespaces utilizados no documento, como o namespace WSDL, SOAP e XML Schema.
- `xmlns:tns`: Define o namespace específico do serviço.
- `targetNamespace`: Qualifica os elementos definidos pelo usuário no WSDL.

#### 2.1.2 Types
- Contém definições de tipos de dados utilizados pelas mensagens do serviço.
- As definições são expressas usando XML Schema (`<xsd:schema>`).
- Exemplo: Define elementos como `FilmRequest` e `FilmResponse`, representando solicitação e resposta.

#### 2.1.3 Message
- Define a estrutura de dados de uma mensagem SOAP.
- Cada mensagem pode conter várias partes (`<part>`), que representam partes individuais da mensagem.
- Exemplo: `FilmRequestMessage` (solicitação) e `FilmDetailsMessage` (resposta).
- Cada `<part>` refere-se aos elementos definidos em `<types>`.

#### 2.1.4 PortType
- Define uma coleção de operações que podem ser realizadas e as mensagens envolvidas.
- Conecta as mensagens de entrada (`input`) e saída (`output`) para cada operação.
- Exemplo: Operação `GetFilmDetails` que especifica mensagem de entrada e de saída.
- É o elemento que define o conjunto abstrato de operações implementadas por um serviço.

> [!TIP] DICAS:
> - Para definir o conjunto abstrato de operações de um serviço, o elemento correto é `<portType>`.
> - O `<portType>` é a interface do serviço, conectando as mensagens às operações.

#### 2.1.5 Binding
- Especifica os detalhes técnicos de como as mensagens são formatadas e transmitidas.
- Conecta o `<portType>` ao protocolo SOAP.
- Define que as mensagens são transmitidas via HTTP e utilizando o estilo de documento literal.

#### 2.1.6 Service
- Define os pontos de extremidade (endereços) onde os serviços web estão disponíveis.
- Exemplo: `FilmService` com um endpoint específico (`soap:address`).
- O `<binding>` é associado ao serviço para especificar como as mensagens SOAP são enviadas e recebidas.
- A ordem de definição é primeiro o `<service>` e depois o `<binding>`.

### 2.2 Tipos de Operação no WSDL
- As operações descritas no WSDL podem ser de diferentes tipos, dependendo da troca de mensagens.

| TIPO DE OPERAÇÃO | DESCRIÇÃO |
|------------------|-----------|
| One-Way | O serviço recebe uma mensagem (input), mas não retorna resposta. |
| Request-Response | O serviço recebe uma requisição (input) e retorna uma resposta (output). |
| Solicit-Response | O serviço envia uma solicitação e aguarda uma resposta. |
| Notification | O serviço envia uma mensagem sem aguardar resposta. |
| Binding | Não é um tipo de operação, mas sim uma definição de vínculo técnico. |

#### 2.2.1 Exemplo de Operação Request-Response
- Recorte de WSDL com operação do tipo request-response:
  ```xml
  <message name="getProcessoRequest">
    <part name="processo" type="xs:string"/>
  </message>
  <message name="getProcessoResponse">
    <part name="numero" type="xs:string"/>
  </message>
  <portType name="ServicoProcesso">
    <operation name="getProcesso">
      <input message="getProcessoRequest"/>
      <output message="getProcessoResponse"/>
    </operation>
  </portType>
  ```
- A operação `getProcesso` possui entrada e saída, caracterizando o tipo request-response.

#### 2.2.2 Exemplo de Operação One-Way
- Quando a operação possui apenas o elemento `<input>`, sem `<output>`, ela é do tipo one-way.
- O serviço recebe a mensagem, mas não retorna nenhuma resposta.

> [!TIP] DICAS:
> - Operação one-way: apenas entrada, sem resposta.
> - Operação request-response: entrada e saída. É o tipo mais comum em serviços web.

## 3. UDDI (Universal Description, Discovery, and Integration)
- Protocolo padrão para publicar e descobrir informações sobre serviços web.
- Funciona como um diretório centralizado para empresas e seus serviços, facilitando a integração entre sistemas.
- Faz a inversão das dependências: ao invés de depender diretamente dos prestadores, o cliente depende do UDDI.

### 3.1 Componentes do UDDI
- O UDDI é organizado em três tipos de páginas, cada uma com uma finalidade específica:

| PÁGINA | FUNÇÃO |
|--------|--------|
| White Pages (Páginas Brancas) | Contêm informações sobre a instituição (corporação) que fornece o serviço, como nome, descrição e detalhes de contato. |
| Yellow Pages (Páginas Amarelas) | Organizam serviços em categorias baseadas em padrões industriais ou tipos de serviço. Fornecem classificação do serviço ou negócios com base em taxonomias padronizadas. |
| Green Pages (Páginas Verdes) | Detalham informações técnicas sobre os serviços oferecidos, incluindo descrições de acesso e processos de interação. Descrevem como acessar um serviço, com informações sobre os meios de ligação (binding). |

> [!TIP] DICAS:
> - Páginas Brancas: informações da empresa (quem fornece).
> - Páginas Amarelas: categorias e classificação do serviço.
> - Páginas Verdes: detalhes técnicos de acesso (como consumir o serviço).

> [!CAUTION] OBSERVAÇÃO:
> - REST não utiliza UDDI para descoberta de serviços. REST utiliza mecanismos como XML, JSON e HTML.
> - SOAP e WSDL são padrões associados a serviços web baseados em XML.
> - UDDI é um diretório, não um protocolo de transporte ou descrição.