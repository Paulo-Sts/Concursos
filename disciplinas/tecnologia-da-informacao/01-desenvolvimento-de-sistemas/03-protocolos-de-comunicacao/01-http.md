# Arquitetura Tcp/Ip – Camada de Aplicação – Protocolo Http

## 1. Protocolo Http – Hypertext Transfer Protocol
- Trata-se de um protocolo pertencente à camada de aplicação da arquitetura TCP/IP.
- Atua como um conjunto de regras para a troca de arquivos como textos, imagens, sons e vídeos na world wide web.
- Utiliza a porta 80 como padrão no servidor quando não há uso de segurança via TLS.
- O protocolo utiliza a linguagem HTML para comunicação, embora utilize comandos próprios que não pertencem ao HTML para interagir com o servidor.
- As mensagens possuem um formato similar ao utilizado pelo Internet Mail e pelo Multipurpose Internet Mail Extensions (MIME).
- As referências de recursos são identificadas pelo Uniform Resource Identifier (URI), podendo ser uma localização (URL) ou um nome (URN).

> [!CAUTION] OBSERVAÇÃO:
> - O uso do protocolo TCP nas versões 1 e 2 do HTTP é fundamental para garantir a confirmação da entrega das informações, evitando o carregamento incompleto de páginas.

## 2. Versões do Protocolo Http
- O HTTP nas versões 1 e 2 opera sobre o protocolo TCP, com segurança opcional via HTTPS.
- No HTTP/1.x, as mensagens são trocadas em formato de código legível (texto), informando dados como host, porta e user agent.
- O HTTP/2 introduz a comunicação em formato binário em vez de texto.
- O HTTP/3 baseia-se no protocolo QUIC, que utiliza UDP em vez de TCP.
- Diferente das versões anteriores, o HTTP/3 estabelece conexão segura de forma obrigatória através do TLS 1.3.

## 3. Protocolo Quic vs. Protocolo Tcp
| ASPECTO | TCP | QUIC |
|---|---|---|
| Base | Protocolo próprio | Executado sobre udp |
| Handshake | 1-3 rtts | 1 rtt (round-trip time) |
| Handshake de reconexão | 1-3 rtts | 0 rtt (round-trip time) |
| Criptografia | Tls opcional | Tls 1.3 integrado |
| Mudança de rede | Mudança ip - reconexão necessária | Conexão mantida via connection id |

> [!TIP] DICAS:
> - O protocolo QUIC foi desenvolvido pela Google em 2012 e padronizado pelo IETF por meio da RFC 9000 em 2021.

## 4. Modelo Cliente-Servidor e Stateless
- O HTTP opera seguindo o padrão de requisição (request) e resposta (response).
- É um protocolo stateless, o que significa que o servidor não armazena o estado entre interações de forma nativa.
- Cada comunicação é independente, sendo iniciada e encerrada sem manter uma conexão contínua entre as partes.
- Para que informações de estado sejam retidas, é necessário o uso de recursos adicionais como cookies ou sessões.
- O fluxo básico de solicitação consiste em:
  - Cliente faz conexão com o host através de uma URL;
  - Usuário aceita a conexão;
  - Cliente envia o request para o documento;
  - Servidor busca o documento e emite a resposta;
  - Conexão é finalizada após a emissão completa.

## 5. Estrutura da Mensagem Http

### 5.1 Elementos da Requisição
- Linha inicial (start line) contendo o método (verbo), o alvo da requisição e a versão do protocolo.
- Cabeçalhos (headers) opcionais que descrevem a requisição ou o corpo da mensagem.
- Linha em branco (empty line) utilizada para separar os metadados do corpo da mensagem.
- Corpo (body) contendo os dados da requisição, comum em métodos como POST.

### 5.2 Elementos da Resposta
- Linha de status contendo a versão do protocolo, um código de status numérico e um texto explicativo.
- Cabeçalhos de resposta especificando detalhes do servidor e do conteúdo.
- Linha em branco para separação.
- Corpo da resposta contendo o recurso solicitado, frequentemente em formato HTML.

## 6. Métodos ou Verbos Http
- GET ⟶ solicita ao servidor o envio de um recurso específico.
- HEAD ⟶ solicita apenas o cabeçalho do recurso, sem o corpo da mensagem.
- PUT ⟶ permite que um cliente autorizado armazene ou modifique um recurso no servidor.
- POST ⟶ envia dados, como formulários, para que o servidor os processe.
- DELETE ⟶ permite a remoção de um recurso específico no servidor por cliente autorizado.
- OPTIONS ⟶ utilizado para descrever as opções de comunicação para o recurso alvo.
- CONNECT ⟶ estabelece um túnel para o servidor identificado pelo recurso de destino.

## 7. Códigos de Status Http
- Os códigos são formados por três dígitos que indicam o resultado da tentativa de satisfazer o pedido.
- 1xx (Informational) ⟶ indica que a requisição foi recebida e o processo continua;
- 2xx (Success) ⟶ indica que a ação foi recebida, compreendida e aceita com sucesso;
- 3xx (Redirection) ⟶ indica que novas ações devem ser tomadas para completar a requisição;
- 4xx (Client Error) ⟶ indica erro na sintaxe da requisição ou que ela não pode ser atendida;
- 5xx (Server Error) ⟶ indica que o servidor falhou ao processar uma requisição aparentemente válida.

### 7.1 Exemplos de Códigos Comuns
- 200 ⟶ OK;
- 201 ⟶ Created;
- 304 ⟶ Not Modified;
- 400 ⟶ Bad Request;
- 403 ⟶ Forbidden;
- 404 ⟶ Not Found;
- 500 ⟶ Internal Server Error.

> [!CAUTION] OBSERVAÇÃO:
> - A porta 8080 é frequentemente utilizada como uma alternativa (http-alt) à porta 80 padrão, podendo ser empregada em conexões com proxy ou servidores de cache.