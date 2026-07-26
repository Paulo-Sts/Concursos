# Interoperabilidade de Sistemas – SOA e Web Services 2

## 1. Web Services – Visão Geral

### 1.1 Conceito
- Tecnologia de integração de sistemas empregada principalmente em ambientes heterogêneos.
- Possibilita integração entre sistemas em plataformas diferentes e a interação entre novos sistemas e sistemas legados.
- Evolução de sistemas de computação distribuída (CORBA, DCOM e RMI).
- Permite que aplicações enviem e recebam dados em formato XML.
- Baseia-se nos padrões SOAP e REST.
- Sistema de software projetado para suportar a interoperabilidade entre máquinas sobre rede (definição do W3C).

> [!TIP] DICAS:
> - Web services eliminam a necessidade de discussões aprofundadas sobre integração direta entre linguagens de programação – o uso de barramentos resolve grande parte dos desafios.
> - Exemplo prático: Gov.br integra sistemas do Ministério da Saúde, TSE, Detran, entre outros.

## 2. Participantes/Papéis no Web Service

| PAPEL | DESCRIÇÃO |
|-------|-----------|
| Provedor de Serviços (Service Provider) | Cria, mantém e fornece um ou mais serviços; pode armazenar arquivos WSDL. |
| Consumidor de Serviços (Service Requester) | Solicita que o provedor execute um serviço específico; pode ser uma aplicação, sistema ou outro serviço. |
| Registro de Serviços (Service Registry) | Diretório de serviços disponíveis na rede; armazena documentos de descrição de serviço (WSDL); implementado via UDDI. |

### 2.1 Fluxo de Interação
1. Provedor publica o serviço no Registro (UDDI);
2. Consumidor consulta o Registro para encontrar o serviço;
3. Consumidor consome o serviço diretamente do Provedor.

## 3. SOAP – Simple Object Access Protocol

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Sigla | Simple Object Access Protocol. |
| Função | Estrutura de empacotamento padrão para transportar documentos XML através de protocolos da Internet (HTTP, SMTP, FTP). |
| Formato | Baseado em XML. |
| Modelo | Segue o modelo "Request-Response" do HTTP. |
| Características | Independente de plataforma; auxilia na interoperabilidade entre objetos e componentes distribuídos. |

> [!TIP] DICAS:
> - O SOAP é o principal elemento do Web Service – atua como protocolo intermediário responsável por organizar e transmitir mensagens XML entre sistemas.
> - Não confundir: SOAP = protocolo de transporte/empacotamento; WSDL = descrição do serviço.

## 4. WSDL – Web Services Description Language

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Sigla | Web Services Description Language. |
| Função | Descreve detalhadamente um Web Service; especifica as operações e o formato de entrada/saída de cada operação. |
| Formato | Arquivo XML. |
| Definição W3C | Notação XML para descrever um serviço da web. |

### 4.1 Os Três Pontos do WSDL (Segundo Sommerville)

| PARTE | DESCRIÇÃO |
|-------|-----------|
| "O quê" (Interface) | Especifica quais operações o serviço suporta e define o formato das mensagens enviadas e recebidas. |
| "Como" (Ligação/Binding) | Mapeia uma interface abstrata para um conjunto concreto de protocolos; detalhes técnicos de comunicação. |
| "Onde" (Serviço) | Descreve onde localizar um Web Service (endereço/URI). |

### 4.2 Estrutura do Documento WSDL

| ELEMENTO | DESCRIÇÃO |
|----------|-----------|
| Types | Tipos de dados utilizados. |
| Messages | Formato das mensagens. |
| Port Types | Operações suportadas pelo serviço (interface). |
| Binding | Mapeamento de protocolos (como se comunicar). |
| Services | Representa um ou mais pontos de extremidade (endpoints) onde o WS pode ser acessado. |

## 5. UDDI – Universal Description, Discovery and Integration

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Sigla | Universal Description, Discovery and Integration. |
| Função | Mecanismo de registro de serviços (Service Registry) – atende o cliente WS e o provedor WS. |
| Objetivo | Publicação e localização de Web Services; permite descobrir onde o serviço está localizado e como consumi-lo. |

### 5.1 Registros UDDI

| TIPO | DESCRIÇÃO |
|------|-----------|
| White Pages (Páginas Brancas) | Endereço, contato e identificadores conhecidos. |
| Yellow Pages (Páginas Amarelas) | Categorizações industriais baseadas em padrão de taxonomia. |
| Green Pages (Páginas Verdes) | Informações técnicas sobre os serviços expostos; lista completa dos serviços e descrição da forma de acesso. |

> [!CAUTION] OBSERVAÇÃO:
> - WSDL x UDDI:
>   - WSDL → descreve o quê o serviço faz (operações, formatos de mensagem);
>   - UDDI → permite descobrir onde o serviço está localizado (endereço para consumo).

## 6. Comparativo – SOAP x WSDL x UDDI

| COMPONENTE | FUNÇÃO |
|------------|--------|
| SOAP | Protocolo de transporte/empacotamento de mensagens XML. |
| WSDL | Descreve as operações e a interface do serviço (o quê, como, onde). |
| UDDI | Registro/diretório para publicação e descoberta de serviços (onde encontrar). |

## 7. Tabela Resumo – Web Services

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Tecnologia | Integração de sistemas em ambientes heterogêneos. |
| Base | XML (formato de mensagens). |
| Padrões | SOAP (protocolo) e REST (abordagem). |
| Descrição | WSDL (notação XML para descrever o serviço). |
| Registro | UDDI (diretório para publicar e descobrir serviços). |
| Participantes | Provedor, Consumidor, Registro. |