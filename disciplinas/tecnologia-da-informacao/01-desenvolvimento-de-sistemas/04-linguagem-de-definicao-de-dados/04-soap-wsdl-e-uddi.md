# Tecnologias XML: SOAP, WSDL e UDDI

## 1. Contexto Geral das Tecnologias
- SOAP, WSDL e UDDI são recursos empregados na comunicação entre sistemas, especialmente sistemas web.
- Atualmente, essas tecnologias foram eclipsadas pela arquitetura REST, que oferece maior flexibilidade.
- A diferença fundamental entre SOAP e REST está na complexidade e rigidez do SOAP versus a flexibilidade do REST.
- O SOAP oferece vantagens em segurança e controle de chamadas, sendo adequado para setores com requisitos rigorosos (ex.: hotelaria e transporte aéreo).

## 2. SOAP (Simple Object Access Protocol)
- Protocolo baseado em XML usado para trocar informações entre computadores em uma rede, incluindo a internet.
- Desenvolvido na década de 90 para preencher a lacuna dos web services utilizando XML.
- Apesar do nome "Simple", o protocolo não é simples e envolve considerável complexidade.

### 2.1 Razões para usar SOAP
- Interoperabilidade: facilita a comunicação entre aplicações desenvolvidas em diferentes linguagens e plataformas, pois é padronizado.
- Segurança: suporta ampla gama de protocolos de segurança, tornando-o adequado para transações confidenciais.

### 2.2 Componentes de uma mensagem SOAP
- Envelope: elemento raiz que define a estrutura da mensagem SOAP (obrigatório).
- Header: contém informações de cabeçalho aplicáveis a todas as mensagens, como autenticação, transações e instruções de processamento (opcional).
- Body: coração da mensagem, contendo informações específicas da chamada de função, como parâmetros de métodos e valores (obrigatório).
- Fault: utilizado para fornecer informações sobre erros ocorridos durante o processamento (opcional).

### 2.3 Exemplo prático de requisição SOAP
```xml
<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:m="http://www.example.org/filmService">
  <soap:Header>
    <m:Authentication>
      <m:Token>12345abcdeTOKEN</m:Token>
    </m:Authentication>
  </soap:Header>
  <soap:Body>
    <m:GetFilmDetails>
      <m:Title>Cidade de Deus</m:Title>
    </m:GetFilmDetails>
  </soap:Body>
</soap:Envelope>
```
- O namespace "soap" refere-se ao universo de tags do SOAP.
- O namespace "m" é próprio do serviço (ex.: serviço de filmes), não relacionado ao SOAP.
- O header é utilizado para autenticação, passando um token do cliente para validação.
- No body, solicita-se detalhes de um filme com título "Cidade de Deus".

### 2.4 Exemplo de resposta SOAP
```xml
<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <m:GetFilmDetailsResponse xmlns:m="http://www.example.org/filmService">
      <m:Title>Cidade de Deus</m:Title>
      <m:Director>Fernando Meirelles</m:Director>
      <m:Year>2002</m:Year>
      <m:Genre>Drama, Crime</m:Genre>
    </m:GetFilmDetailsResponse>
  </soap:Body>
</soap:Envelope>
```
- A resposta contém apenas dois elementos SOAP: envelope e body (header está ausente).
- Dentro do body, os detalhes do serviço são indicados pela tag M (própria do serviço).

### 2.5 Exemplo com Fault (erro)
- Requisição para um filme inexistente, como "Tropa de Elite 3".
- A resposta SOAP inclui o elemento Fault no body.

> [!TIP] DICAS:
> - O elemento Header é opcional, enquanto o Body é obrigatório em toda mensagem SOAP.
> - O elemento Fault só pode aparecer uma vez em cada mensagem.
> - O Fault é composto por fault code, fault string (descrição do erro em linguagem acessível) e detail (para tags específicas do serviço).

### 2.6 Estrutura do Fault
- fault code: código do erro.
- fault string: descrição textual do erro.
- detail: permite uso de tags específicas do serviço para detalhar o erro (ex.: indicar que o filme não está disponível na base de dados).

## 3. SOAP vs REST
- SOAP é um protocolo de comunicação com regras predefinidas (forte acoplamento).
- REST é um estilo arquitetural baseado em padrões da web (flexível).

| CARACTERÍSTICA | SOAP | REST |
|----------------|------|------|
| Baseado em | Protocolo | Padrões da web (HTTP) |
| Segurança | Suporta WS-Security | Usa HTTPS |
| Acoplamento | Forte (contratos rigorosos) | Frouxo (facilidade de evolução) |
| Formato de mensagem | Estritamente XML | Flexível (XML, JSON, HTML, etc.) |

- SOAP utiliza WS-Security, enquanto REST utiliza HTTPS (mas o SOAP também pode operar com HTTPS).
- REST oferece maior flexibilidade de formatos (XML, JSON, HTML, RSS, etc.).
- SOAP trabalha estritamente com XML.
- No REST, erros são tratados por códigos HTTP padronizados (ex.: 404, 500).
- No SOAP, o controle de erros é mais flexível devido ao elemento Fault.

## 4. WSDL (Web Services Description Language)
- Linguagem baseada em XML para descrever serviços web e como acessá-los.
- Define o contrato de serviço, incluindo métodos disponíveis, parâmetros e tipos de dados de retorno.
- SOAP utiliza WSDL para descrever a interface pública de serviços web.
- Funciona como uma descrição abrangente da API de um serviço.
- Permite que clientes saibam como formatar requisições e interpretar respostas.

## 5. UDDI (Universal Description, Discovery and Integration)
- Padrão para publicar e descobrir informações sobre serviços web.
- Funciona como um diretório centralizado para serviços web.
- Empresas podem registrar e procurar serviços web.
- SOAP se integra com UDDI, permitindo que serviços descritos em WSDL sejam encontrados e utilizados por clientes em todo o mundo.
- Facilita a integração e interoperabilidade entre diferentes sistemas e organizações.

## 6. SOA (Service Oriented Architecture)
- Arquitetura orientada a serviços, um estilo arquitetural para criar serviços web que interagem entre si.
- Pode ser implementada tanto com REST quanto com SOAP.
- Geralmente envolve uma tecnologia de backbone que coordena a comunicação entre os serviços.
- Inverte o controle: requisições são feitas ao backbone, que localiza o serviço correspondente.

> [!CAUTION] OBSERVAÇÃO:
> - UDDI é um repositório de descoberta de serviços, não um protocolo de segurança.
> - DTD (Document Type Definition) valida e descreve a estrutura do XML; sua evolução é o XSD.
> - WSDL não é uma linguagem para transformações sobre mensagens SOAP, mas sim para descrever serviços.