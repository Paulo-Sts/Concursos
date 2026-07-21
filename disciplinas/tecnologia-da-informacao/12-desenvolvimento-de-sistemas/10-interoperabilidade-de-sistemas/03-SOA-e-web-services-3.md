# Anotações

# Interoperabilidade de Sistemas – SOA e Web Services III

## 1.1 Fases da Arquitetura SOAP

### 1.1.1 Etapas do Processo de Web Services

| FASE | DESCRIÇÃO |
|------|-----------|
| **Publish (Publicar)** | Divulgação do Web Service com seus descritores (WSDL); registro no diretório **UDDI**; endereço de disponibilização = **URI** (*Uniform Resource Identifier*) |
| **Find (Encontrar)** | Obtenção de informações sobre o WS via recursos de pesquisa e localização no UDDI |
| **Bind (Vincular)** | Efetivação do download do WSDL (pode estar no UDDI ou no provedor); envio de solicitação XML via URI; recebimento de resposta XML |

### 1.1.2 Detalhamento do Bind

- **Envio de solicitação XML:** cliente realiza chamadas ao WS usando solicitações XML via URI.
- **Recebimento de resposta XML:** recebe resposta via URI, processa e produz o resultado.

> [!TIP] DICAS
> - O fluxo central é: **requisição → resposta**.
> - O cliente sempre envia a solicitação ao provedor, que processa a requisição e retorna a resposta.

## 1.2 Formas de Envio de Mensagem

| TIPO | DESCRIÇÃO |
|------|-----------|
| ***One-way messaging*** (Unilateral) | Envio unilateral – cliente envia solicitação sem esperar por resposta (ex.: solicitação de execução de tarefa sem retorno) |
| ***Request-response messaging*** (Bilateral) | Cliente solicita, WS executa o processamento, gera arquivo XML e envia ao cliente que solicitou (ex.: validação de CPF/CNPJ) |

## 1.3 Estrutura da Mensagem SOAP

Uma mensagem SOAP é um documento XML simples que contém os seguintes elementos:

| ELEMENTO | DESCRIÇÃO |
|----------|-----------|
| **Envelope** | Identifica o documento XML como uma mensagem SOAP; **obrigatório**; elemento raiz |
| **Header** | Contém informações de cabeçalho; **opcional**; quando utilizado, deve ser o primeiro elemento dentro do Envelope |
| **Body** | Contém as informações de chamadas e respostas; **obrigatório** |
| **Fault** | Contém erros e informações de status; **opcional** |

### 1.3.1 Subelementos do Fault

| SUBELEMENTO | DESCRIÇÃO |
|-------------|-----------|
| `faultcode` | Código para identificar o Fault |
| `faultstring` | Explicação legível da falha |
| `faultactor` | Informação sobre por que a falha aconteceu |
| `detail` | Informações específicas relacionadas à falha |

## 1.4 XML – Extensible Markup Language

### 1.4.1 Características Gerais

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **Sigla** | *Extensible Markup Language* |
| **Status** | Recomendação W3C |
| **Função** | Linguagem de **acesso a dados**; transporte e armazenamento de dados |
| **Estrutura** | Semiestruturada – respeita regras como tags bem formadas, mas menos restritiva que tabelas relacionais |
| **Auto descritivo** | Tags indicam o significado dos dados |

### 1.4.2 XML x HTML

| ASPECTO | XML | HTML |
|---------|-----|------|
| **Objetivo** | Transporte e armazenamento de dados | Exibição de dados (apresentação) |
| **Tags** | Não são pré-definidas (extensível) | Pré-definidas |
| **Relacionamento** | XML complementa o HTML | HTML exibe dados |

### 1.4.3 Regras do XML Bem Formado

1. Todas as tags abertas devem ser **devidamente fechadas**.
2. **Não há sobreposição de tags** (aninhamento correto).
3. Existe **um e somente um elemento raiz**.
4. As tags são ***case sensitive*** (diferenciam maiúsculas de minúsculas).
5. Os atributos devem estar **entre aspas**.

### 1.4.4 Componentes de um Documento XML

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| **Declaração** | Entrada padrão de identificação recomendada pela W3C (`<?xml version="1.0"?>`) |
| **Comentário** | `<!-- comentário -->` |
| **Esquema/DTD** | Contém regras sobre os elementos do documento |
| **Elementos** | Tag inicial + tag final com conteúdo entre elas; pode conter dados ou outros elementos |
| **Elemento Raiz** | Elemento principal que contém todos os outros elementos |
| **Atributos** | Pares "nome-valor" para anexar dados a um elemento; declarados na DTD |

### 1.4.5 XSLT – Extensible Stylesheet Language for Transformation

- Linguagem de marcação XML usada para criar documentos XSL.
- Define a **apresentação** dos documentos XML nos *browsers* e outros aplicativos.
- **Não altera** o documento XML original – apenas determina como ele é apresentado (similar ao CSS para HTML).

> [!TIP] DICAS
> - **XML:** dados e transporte.
> - **HTML:** apresentação.
> - **XSLT:** transformação/apresentação do XML (como CSS para HTML).

## 1.5 Relações entre Componentes

| COMPONENTE | FUNÇÃO |
|------------|--------|
| **HTTP** | Responsável por **transportar** mensagens entre aplicações |
| **SOAP** | Responsável por **codificar** as mensagens em formato XML; transporta informações do WS |
| **WSDL** | Responsável por **descrever** a interface do Web Service |
| **UDDI** | Responsável por **centralizar** informações de WS, possibilitando publicação e descoberta |
| **URI** | Endereço do WS e WSDL |

## 1.6 Tabela Resumo – Fases e Componentes

| FASES | COMPONENTES ENVOLVIDOS |
|-------|------------------------|
| **Publish** (Publicar) | Provedor → UDDI (WSDL, URI) |
| **Find** (Encontrar) | Consumidor → UDDI (busca pelo WS) |
| **Bind** (Vincular/Consumir) | Consumidor ↔ Provedor (SOAP/XML via HTTP) |

---

# Questões de Fixação

## Questão 01
(GAMA CONSULT/CÂMARA DE ALTO PARAÍSO - RO / AGENTE ADMINISTRATIVO/2014)

Leia a afirmação a seguir: Computadores são utilizados meramente para mostrar a informação na tela, ou seja, decodificar as marcações de cores, posição e links, codificadas através das linguagens ______ ou ______. Essas linguagens, também são chamadas de linguagens de marcação". Nesse contexto, assinale a alternativa que preenche melhor a lacuna acima:

a) CTRL ou XLM.
b) CSS ou BBCode.
c) HTML ou XML.
d) Markdown ou BBCode.

**Gabarito:** c - As principais linguagens de marcação são **HTML** e **XML**.

## Questão 02
(CESPE/CEBRASPE/2024/TCE-AC/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO - ÁREA: SISTEMAS DE INFORMAÇÃO)

Com base no código XML precedente, julgue o próximo item. No código apresentado, o termo name é um elemento e o termo message é uma tag.

**Gabarito:** C (Correto) - *Name* é um atributo; *message* é uma tag (delimita elementos). A questão avalia a compreensão da estrutura XML.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | c |
| 02 | C |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Gabriel Ferreira Pacheco.*