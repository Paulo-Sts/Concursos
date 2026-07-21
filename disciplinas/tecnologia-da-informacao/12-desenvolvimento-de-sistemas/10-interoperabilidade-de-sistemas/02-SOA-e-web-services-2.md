# Anotações

# Interoperabilidade de Sistemas – SOA e Web Services II

## 1.1 Web Services – Visão Geral

- **Tecnologia de integração de sistemas** empregada principalmente em **ambientes heterogêneos**.
- Possibilita integração entre sistemas em **plataformas diferentes** e a interação entre **novos sistemas e sistemas legados**.
- Evolução de sistemas de computação distribuída (**CORBA, DCOM e RMI**).
- Permite que aplicações enviem e recebam dados em formato **XML**.
- Baseia-se nos padrões **SOAP** e **REST**.
- Sistema de software projetado para suportar a **interoperabilidade entre máquinas sobre rede** (definição do W3C).

> [!TIP] DICAS
> - **Web services** eliminam a necessidade de discussões aprofundadas sobre integração direta entre linguagens de programação – o uso de barramentos resolve grande parte dos desafios.
> - Exemplo prático: Gov.br integra sistemas do Ministério da Saúde, TSE, Detran, entre outros.

## 1.2 Participantes/Papéis no Web Service

| PAPEL | DESCRIÇÃO |
|-------|-----------|
| **Provedor de Serviços (*Service Provider*)** | Cria, mantém e fornece um ou mais serviços; pode armazenar arquivos WSDL |
| **Consumidor de Serviços (*Service Requester*)** | Solicita que o provedor execute um serviço específico; pode ser uma aplicação, sistema ou outro serviço |
| **Registro de Serviços (*Service Registry*)** | Diretório de serviços disponíveis na rede; armazena documentos de descrição de serviço (WSDL); implementado via **UDDI** |

### 1.2.1 Fluxo de Interação
1. Provedor **publica** o serviço no Registro (UDDI).
2. Consumidor **consulta** o Registro para encontrar o serviço.
3. Consumidor **consome** o serviço diretamente do Provedor.

## 1.3 SOAP – Simple Object Access Protocol

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Sigla** | *Simple Object Access Protocol* |
| **Função** | Estrutura de empacotamento padrão para transportar documentos XML através de protocolos da Internet (HTTP, SMTP, FTP) |
| **Formato** | Baseado em XML |
| **Modelo** | Segue o modelo **"Request-Response"** do HTTP |
| **Características** | Independente de plataforma; auxilia na interoperabilidade entre objetos e componentes distribuídos |

> [!TIP] DICAS
> - O SOAP é o **principal elemento do Web Service** – atua como protocolo intermediário responsável por organizar e transmitir mensagens XML entre sistemas.
> - **Não confundir:** SOAP = protocolo de transporte/empacotamento; WSDL = descrição do serviço.

## 1.4 WSDL – Web Services Description Language

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Sigla** | *Web Services Description Language* |
| **Função** | Descreve detalhadamente um Web Service; especifica as operações e o formato de entrada/saída de cada operação |
| **Formato** | Arquivo XML |
| **Definição W3C** | Notação XML para **descrever um serviço da web** |

### 1.4.1 Os Três Pontos do WSDL (Segundo Sommerville)

| PARTE | DESCRIÇÃO |
|-------|-----------|
| **"O quê" (Interface)** | Especifica quais operações o serviço suporta e define o formato das mensagens enviadas e recebidas |
| **"Como" (Ligação/Binding)** | Mapeia uma interface abstrata para um conjunto concreto de protocolos; detalhes técnicos de comunicação |
| **"Onde" (Serviço)** | Descreve onde localizar um Web Service (endereço/URI) |

### 1.4.2 Estrutura do Documento WSDL

| ELEMENTO | DESCRIÇÃO |
|----------|-----------|
| **Types** | Tipos de dados utilizados |
| **Messages** | Formato das mensagens |
| **Port Types** | Operações suportadas pelo serviço (interface) |
| **Binding** | Mapeamento de protocolos (como se comunicar) |
| **Services** | Representa um ou mais pontos de extremidade (*endpoints*) onde o WS pode ser acessado |

## 1.5 UDDI – Universal Description, Discovery and Integration

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Sigla** | *Universal Description, Discovery and Integration* |
| **Função** | Mecanismo de **registro de serviços** (*Service Registry*) – atende o cliente WS e o provedor WS |
| **Objetivo** | Publicação e localização de Web Services; permite descobrir **onde** o serviço está localizado e como consumi-lo |

### 1.5.1 Registros UDDI

| TIPO | DESCRIÇÃO |
|------|-----------|
| **White Pages (Páginas Brancas)** | Endereço, contato e identificadores conhecidos |
| **Yellow Pages (Páginas Amarelas)** | Categorizações industriais baseadas em padrão de taxonomia |
| **Green Pages (Páginas Verdes)** | Informações técnicas sobre os serviços expostos; lista completa dos serviços e descrição da forma de acesso |

> [!CAUTION] OBSERVAÇÃO
> **WSDL x UDDI:**
> - **WSDL** → descreve **o quê** o serviço faz (operações, formatos de mensagem).
> - **UDDI** → permite descobrir **onde** o serviço está localizado (endereço para consumo).

## 1.6 Comparativo – SOAP x WSDL x UDDI

| COMPONENTE | FUNÇÃO |
|------------|--------|
| **SOAP** | Protocolo de transporte/empacotamento de mensagens XML |
| **WSDL** | Descreve as operações e a interface do serviço (o quê, como, onde) |
| **UDDI** | Registro/diretório para publicação e descoberta de serviços (onde encontrar) |

## 1.7 Tabela Resumo – Web Services

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Tecnologia** | Integração de sistemas em ambientes heterogêneos |
| **Base** | XML (formato de mensagens) |
| **Padrões** | SOAP (protocolo) e REST (abordagem) |
| **Descrição** | WSDL (notação XML para descrever o serviço) |
| **Registro** | UDDI (diretório para publicar e descobrir serviços) |
| **Participantes** | Provedor, Consumidor, Registro |

---

# Questões de Fixação

## Questão 03
(IV/UFG/2024/TJ-GO/ANALISTA JUDICIÁRIO/ÁREA ESPECIALIZADA/ANALISTA DE SISTEMAS)

O W3C (World Wide Web Consortium), organização responsável pelo desenvolvimento de padrões e diretrizes para web, descreve a WSDL como sendo uma notação XML para

a) descrever um serviço da web.
b) permitir a intercomunicação de processos.
c) compartilhar dados na web.
d) viabilizar a troca de mensagens cliente/servidor.

**Gabarito:** a

## Questão 04
(CESPE/CEBRASPE/2024/CAGEPA/PB/ANALISTA DE SISTEMAS/SISTEMAS DE TI)

UDDI normalmente é usado com outros padrões nos serviços web. Para descrever interfaces para os serviços web, o UDDI é utilizado com

a) WSDL.
b) JSON.
c) XML.
d) SOAP.
e) REST.

**Gabarito:** a - O UDDI é utilizado com **WSDL** para descrever as interfaces dos serviços.

## Questão 05
(CESGRANRIO/2024/BANCO DA AMAZÔNIA/TÉCNICO CIENTÍFICO/TECNOLOGIA DA INFORMAÇÃO)

Um arquiteto de software está projetando uma solução baseada em Arquitetura Orientada a Serviços (SOA) para integrar vários sistemas de uma grande empresa. Ele explicou que, para facilitar a descoberta e a comunicação entre os serviços, será utilizado um registro de serviços. Diante desse contexto, um registro de serviços em SOA é usado para

a) armazenar os dados persistentes de cada serviço.
b) garantir a execução sequencial de transações entre serviços.
c) garantir que todos os serviços utilizem a mesma linguagem de programação.
d) monitorar a performance dos serviços em tempo real.
e) registrar, descobrir e permitir o consumo dinâmico de serviços.

**Gabarito:** e

## Questão 06
(IV/UFG/2024/PREFEITURA DE RIO BRANCO/AC/ANALISTA DE SISTEMAS/ESPECIALIZAÇÃO EM GESTÃO DE SISTEMAS COMPUTACIONAIS)

A sigla SOA significa Services Oriented Architecture, ou arquitetura orientada a serviços. SOA é um tipo de design de software que torna os componentes reutilizáveis usando interfaces de serviços com uma linguagem de comunicação comum em uma rede. A arquitetura orientada a serviços integra os componentes de software implantados e mantidos separadamente, permitindo que eles se comuniquem e trabalhem juntos para formar aplicações que funcionam em sistemas diferentes. Na arquitetura orientada a serviços, o broker de serviços ou registro de serviços é

a) um provedor de serviços que cria serviços web e os oferece para um registro de serviços. Ele é responsável por cadastrar o serviço e publicá-lo.
b) responsável por oferecer informações solicitadas sobre o serviço. O Broker é sempre privado.
c) um provedor de serviços que cria serviços web e os oferece para um registro de serviços. Ele é responsável por apenas publicar o serviço.
d) responsável por oferecer informações solicitadas sobre o serviço. O broker pode ser público ou privado.

**Gabarito:** d - O *broker* de serviços oferece informações sobre o serviço quando solicitado; pode ser público ou privado.

## Questão 07
(IBADE/2024/SES-MG/ESPECIALISTA EM POLÍTICAS E GESTÃO DA SAÚDE/ÁREA DE TI)

Universal Description, Discovery and Integration (UDDI) é um padrão para publicação e localização de web services pelo uso de consultas (queries) baseadas, respectivamente, em:

a) WS-Security e HTTP.
b) WSDL e SMTP.
c) XML e WS-Policy.
d) SOAP e XML.
e) JMS e SOAP.

**Gabarito:** d - O UDDI utiliza **SOAP** para consultas e **XML** como formato de dados.

## Questão 08
(FGV/2024/MF/AUDITOR FEDERAL DE FINANÇAS E CONTROLE/ÁREA DE TECNOLOGIA DA INFORMAÇÃO (OPERAÇÃO E INFRAESTRUTURA)/MANHÃ)

Organizações em todo o mundo frequentemente utilizam Web Services e fazem amplo uso de especificações de padrões de interoperabilidade baseados em XML para implementar uma Arquitetura Orientada a Serviços (SOA). De acordo com esses padrões, a notação XML para descrição de webservices, como acessá-lo e quais operações estão disponíveis é

a) SOAP.
b) REST.
c) WSDL.
d) XSLT.
e) YAML.

**Gabarito:** c

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 03 | a |
| 04 | a |
| 05 | e |
| 06 | d |
| 07 | d |
| 08 | c |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Gabriel Ferreira Pacheco.*