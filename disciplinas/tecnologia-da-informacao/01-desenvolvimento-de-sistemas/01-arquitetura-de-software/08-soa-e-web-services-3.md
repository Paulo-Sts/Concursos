# Interoperabilidade de Sistemas: SOA e Web Services 3

## 1. Fases da Arquitetura SOAP
- O funcionamento do consumo de Web Services é estruturado em etapas fundamentais que envolvem diferentes papéis e participantes.
- Essas etapas relacionam-se diretamente com o protocolo SOAP na implementação do serviço.

### 1.1 Registro e Publicação do Web Service
- Também conhecida como fase de Publish;
- Consiste na divulgação do Web Service juntamente com seus descritores WSDL;
- O registro ocorre em um diretório denominado UDDI;
- O endereço de disponibilização no UDDI é identificado como URI (Uniform Resource Identifier).

### 1.2 Obtenção de Informações sobre o Web Service
- Fase denominada Find;
- Realizada por meio de recursos de pesquisa e localização dentro do UDDI;
- Permite o acesso ao arquivo WSDL que contém as descrições necessárias para o consumo eficiente do serviço.

### 1.3 Conexão e Execução do Serviço
- Fase denominada Bind;
- Envolve o download do arquivo WSDL, que pode estar no UDDI ou diretamente no provedor;
- O cliente realiza chamadas ao serviço utilizando solicitações em formato XML enviadas por meio da URI;
- O provedor processa a requisição e o cliente recebe a resposta no formato solicitado para produzir o resultado final.

> [!TIP] DICAS: 
> - As fases seguem a sequência lógica: Publish (publicar) ⟶ Find (pesquisar) ⟶ Bind (conectar e consumir).

## 2. Formas de Envio de Mensagem
- O fluxo de comunicação entre cliente e provedor baseia-se no modelo de requisição e resposta.

### 2.1 One-way Messaging
- Modelo de envio unilateral;
- O cliente envia uma solicitação sem esperar por uma resposta do serviço;
- Utilizado para operações que apenas disparam a execução de uma tarefa sem necessidade de retorno.

### 2.2 Request-response Messaging
- Modelo de envio bilateral;
- O cliente solicita uma tarefa, o serviço executa o processamento e gera um arquivo XML de resposta.

> [!CAUTION] OBSERVAÇÃO: 
> - Para consumir um Web Service, é obrigatório conhecer previamente o seu endereço (URI) para o envio da solicitação.

## 3. Estrutura da Mensagem SOAP
- Uma mensagem SOAP é um documento XML simples composto por elementos organizados hierarquicamente.

### 3.1 Elementos do Documento SOAP
- Envelope: elemento raiz obrigatório que identifica o documento XML como uma mensagem SOAP;
- Header: elemento opcional que contém informações de cabeçalho e deve ser o primeiro dentro do Envelope;
- Body: elemento obrigatório que transporta as informações reais de chamadas e respostas;
- Fault: elemento opcional utilizado para reportar erros e informações de status da transação.

### 3.2 Detalhamento do Elemento Fault
| COMPONENTE | DESCRIÇÃO DO ERRO |
|---|---|
| < faultcode > | Código para identificar a falha |
| < faultstring > | Explicação legível da falha |
| < faultactor > | Informação sobre o motivo do acontecimento da falha |
| < detail > | Informações específicas relacionadas à falha |

## 4. Linguagem XML
- Extensible Markup Language: linguagem de marcação extensível recomendada pelo W3C.
- Funciona como uma linguagem de acesso a dados semiestruturada, sendo menos restritiva que tabelas relacionais.

### 4.1 Características Técnicas
- Projetada para ser autodescritiva e independente de software ou hardware no transporte de informações;
- Utiliza etiquetas (tags) para definir os dados, onde o texto entre elas representa o conteúdo em si;
- É Case Sensitive ⟶ diferencia rigorosamente letras maiúsculas de minúsculas nas tags;
- Exige que as tags estejam aninhadas corretamente e possuam um único elemento raiz.

### 4.2 Diferenças entre XML e HTML
- O XML foi projetado para transporte e armazenamento de dados; enquanto o HTML foca na exibição e estrutura de páginas web;
- As tags do HTML são predefinidas; no XML, o desenvolvedor pode criar qualquer marcador necessário conforme a demanda;
- O XML atua de forma complementar ao HTML em sistemas onde o trânsito de dados é necessário.

### 4.3 Componentes de um Documento XML
- Declaração: identificação padrão recomendada pelo W3C (ex: <?xml version=”1.0”?>);
- Comentário: delimitado pela sintaxe <!- comentário -->;
- Esquema ou DTD: contém as regras e definições sobre os elementos permitidos no documento;
- Elementos: compostos por uma tag inicial, conteúdo e tag final;
- Atributos: forma de anexar dados extras a um elemento no formato nome-valor (name-value).

### 4.4 XSL Transformations
- Conhecido como XSLT, é uma linguagem usada para criar documentos que definem a apresentação de arquivos XML;
- Atua de forma semelhante ao CSS para o HTML, determinando como o navegador apresenta os dados;
- Importante: o documento XSL não altera o conteúdo original do arquivo XML.

> [!CAUTION] OBSERVAÇÃO: 
> - Um XML é considerado Bem Formado quando todas as tags abertas são fechadas, não há sobreposição e existe exatamente um elemento raiz.

## 5. Relações entre Protocolos e Ferramentas
| PROTOCOLO | PAPEL NA INTEROPERABILIDADE |
|---|---|
| HTTP | Responsável por transportar mensagens entre as aplicações |
| SOAP | Responsável por codificar as mensagens no formato XML |
| WSDL | Responsável por descrever a interface do Web Service |
| UDDI | Centraliza a informação para publicação e descoberta de serviços |
| URI | Endereço para localização do Web Service e do WSDL |

> [!CAUTION] OBSERVAÇÃO: 
> - Em questões de prova, o termo name é geralmente um atributo, enquanto termos como mensagem ou message são tags que delimitam elementos.