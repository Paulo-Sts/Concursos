# Interoperabilidade de Sistemas: SOA e Web Services 2

## 1. Infraestrutura de Web Service
- Tecnologia de integração de sistemas empregada prioritariamente em ambientes heterogêneos.
- Funciona como um barramento de consumo de serviços que viabiliza a integração entre diferentes plataformas.
- Permite a interação entre sistemas novos e sistemas legados, preservando o funcionamento do que já existe sem necessidade de redesenvolvimento.
- Representa a evolução natural de tecnologias de computação distribuída como CORBA, DCOM e RMI.
- Utiliza barramentos para simplificar a comunicação e eliminar desafios de integração direta entre linguagens de programação.
- Baseia-se em padrões abertos como XML, SOAP e REST para suportar a interoperabilidade entre máquinas sobre rede.

## 2. Padrão SOAP
- Simple Object Access Protocol: protocolo padrão para transmissão de dados na arquitetura de web services.
- Fornece uma estrutura de empacotamento para transportar documentos XML através de protocolos da internet como HTTP, SMTP e FTP.
- Caracteriza-se por ser independente de plataforma e auxiliar na interoperabilidade entre objetos e componentes distribuídos.
- Segue o modelo de requisição e resposta (request-response) típico do protocolo HTTP.

## 3. Componente UDDI
- Universal Description, Discovery and Integration: mecanismo de diretório conhecido como Service Registry ou registro de serviços.
- Atua como um catálogo que permite identificar o que um serviço oferece e como ele pode ser utilizado.
- Desempenha papel essencial na descoberta do local de acesso a um serviço e do caminho para consumi-lo.

### 3.1 Páginas do Registro UDDI
| COMPONENTE | TIPO DE INFORMAÇÃO | DESCRIÇÃO TÉCNICA |
|---|---|---|
| White pages | Páginas brancas | Endereço, contato e identificadores conhecidos |
| Yellow pages | Páginas amarelas | Categorizações industriais baseadas em taxonomia |
| Green pages | Páginas verdes | Informações técnicas e lista de serviços oferecidos |

## 4. Linguagem WSDL
- Web Services Description Language: notação baseada em XML utilizada para descrever detalhadamente um serviço.
- Especifica as operações que compõem o serviço e as definições dos formatos de entrada e saída de cada operação.

### 4.1 Definições do Documento WSDL
- Interface (O que) ⟶ especifica quais operações o serviço apoia e o formato das mensagens;
- Ligação ou Binding (Como) ⟶ mapeia uma interface abstrata para um conjunto concreto de protocolos técnicos;
- Serviço (Onde) ⟶ descreve a localização exata onde o web service pode ser encontrado.

### 4.2 Estrutura de um Documento WSDL
- Types ⟶ define os tipos de dados utilizados no serviço;
- Messages ⟶ define o formato das mensagens enviadas e recebidas;
- Port Types ⟶ descreve as operações suportadas pelo serviço;
- Binding ⟶ realiza o mapeamento de protocolos para os pontos de acesso;
- Services ⟶ representa os pontos de término onde o serviço é acessado.

## 5. Participantes e Papéis na Comunicação
- Provedor de Serviços (Service Provider) ⟶ servidor que cria, mantém e fornece os serviços, podendo armazenar arquivos WSDL;
- Consumidor de Serviços (Service Requestor) ⟶ cliente ou aplicação que realiza a solicitação de execução de um serviço;
- Registro de Serviços (Service Registry) ⟶ diretório que armazena os documentos de descrição e permite a localização de provedores.

> [!TIP] DICAS: 
> - O XML (eXtensible Markup Language) é a estrutura utilizada para armazenamento de dados semiestruturados organizada por etiquetas ou tags.
> - As fases da arquitetura SOAP seguem a sequência: Publish (publicar serviço no UDDI) ⟶ Find (pesquisar localização no UDDI) ⟶ Bind (efetivar o download do WSDL e conectar).

> [!CAUTION] OBSERVAÇÃO: 
> - Pegadinha de prova ⟶ o WSDL descreve as características e funcionalidades (o que o serviço faz), enquanto o UDDI trata da localização e descoberta (onde o serviço está).
> - O JSON pode substituir o XML em situações de interoperabilidade devido à sua simplicidade e velocidade, sendo comum em arquiteturas REST.
> - O registro de serviços em SOA não interfere na linguagem de programação utilizada nem garante a execução sequencial de transações.