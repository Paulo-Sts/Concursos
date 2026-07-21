# Anotações

# Interoperabilidade de Sistemas – SOA e Web Services IV

## 1.1 REST – Representation State Transfer

### 1.1.1 Conceito
- **REST** (*Representational State Transfer*) – estilo de arquitetura de sistemas de informações distribuídas.
- Estilo de projetar aplicativos na WEB **fracamente acoplados** que contam com recursos nomeados em forma de:
  - **URL** (Localizador Uniforme de Recursos)
  - **URI** (Identificador Uniforme de Recursos)
  - **URN** (Nome de Recurso Uniforme)
- REST **não é** um padrão ou protocolo, mas sim um **estilo arquitetural** – uma nova forma de pensar sobre HTTP.

> [!CAUTION] OBSERVAÇÃO
> **REST não é um protocolo e não tem formato obrigatório** – é um estilo arquitetural que define restrições para o design de sistemas distribuídos.

### 1.1.2 Recursos e Métodos HTTP
- **URLs são substantivos** (recursos).
- **Métodos HTTP são verbos** (ações sobre recursos).

| MÉTODO | DESCRIÇÃO |
|--------|-----------|
| **GET** | Obtém o estado atual do recurso identificado (busca recurso) |
| **PUT** | Atualiza um recurso existente |
| **POST** | Cria um novo recurso |
| **DELETE** | Elimina o recurso identificado |

### 1.1.3 Princípios do REST

| PRINCÍPIO | DESCRIÇÃO |
|-----------|-----------|
| **Qualquer informação disponível é um recurso** | Tudo que pode ser nomeado é um recurso |
| **Todos os recursos devem ser identificados** | Identificação via URI |
| **Hipermídia como máquina de estado da aplicação** | Navegação baseada em links/hipertexto |
| **Interface uniforme** | Métodos HTTP padronizados (GET, POST, PUT, DELETE) |
| **Recursos com múltiplas representações** | Suporte a XML, JSON, texto simples, etc. |
| **Stateless** | Não armazenamento de estado – cada requisição é independente |

> [!TIP] DICAS
> - O princípio **stateless** é um dos mais cobrados em provas – REST não mantém o estado da conexão ou da comunicação.
> - **Uniformidade de API** e **facilidade no desenvolvimento** são vantagens do REST.

### 1.1.4 Formatos de Representação de Recursos
- Não existe um padrão obrigatório – REST permite múltiplos formatos:
  - **XML**.
  - **RSS/Atom** – para publicação de *feeds*.
  - **JSON** – formato baseado em texto, simples, com economia de banda.
  - **Texto simples**.

> [!TIP] DICAS
> - **JSON tem ganhado destaque** como substituto do XML por sua simplicidade, rapidez e menor consumo de banda.
> - REST **é compatível com JSON, XML e texto simples** – não é restrito a apenas um formato.

### 1.1.5 Os Três Pilares do REST para Criar um Web Service

| PILAR | DESCRIÇÃO |
|-------|-----------|
| **Mime Type** | Permite alterar as representações de um mesmo conteúdo sob perspectivas diferentes |
| **URL** | Usada para identificar um recurso – cada recurso tem a sua própria |
| **Métodos HTTP** | Responsáveis por provocar alterações nos recursos identificados pelas URLs |

## 1.2 REST x SOAP – Comparativo

| ASPECTO | REST | SOAP |
|---------|------|------|
| **Natureza** | Estilo arquitetural | Protocolo |
| **Formato** | Múltiplos (JSON, XML, texto) | Exclusivamente XML |
| **Protocolo** | Geralmente HTTP (não obrigatório) | HTTP, SMTP, FTP, etc. |
| **Estado** | Stateless (sem estado) | Pode ter estado |
| **Segurança** | HTTPS (TLS) | WS-Security (padrão próprio) |
| **Desempenho** | Mais leve, menor overhead | Mais pesado, maior overhead |
| **Largura de banda** | Menor consumo | Maior consumo |
| **Complexidade** | Simples | Complexa (WS-*, WSDL, etc.) |
| **Acoplamento** | Fraco | Forte |

> [!CAUTION] OBSERVAÇÃO
> - **SOAP usa estritamente XML** para suas mensagens; REST permite JSON, XML, texto simples e outros formatos.
> - **REST não é mais seguro ou menos seguro que SOAP** – ambos podem usar criptografia (HTTPS no REST; WS-Security no SOAP).
> - **SOAP pode usar outros protocolos além de HTTP** (SMTP, FTP) – REST geralmente usa HTTP.

### 1.2.1 WS-Security
- Especificação utilizada **exclusivamente no protocolo SOAP** para segurança em web services.

## 1.3 Vantagens do REST
- **Simplicidade e facilidade de uso.**
- **Uso de diferentes formatos de dados** (não apenas XML).
- **Alta performance e baixa latência** – menos *overhead* de comunicação.
- **Escalabilidade e facilidade de manutenção.**
- **Exige menos largura de banda e recursos.**

## 1.4 Tabela Resumo – REST

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Definição** | Estilo arquitetural para sistemas distribuídos |
| **Recursos** | Identificados por URI/URL/URN |
| **Métodos** | GET, POST, PUT, DELETE (verbos HTTP) |
| **Formatos** | XML, JSON, texto, RSS/Atom (múltiplos) |
| **Estado** | Stateless (sem estado) |
| **Acoplamento** | Fraco |
| **Princípios** | Recursos, identificação, interface uniforme, múltiplas representações, stateless, hipermídia |
| **Vantagens** | Simplicidade, desempenho, flexibilidade, escalabilidade |

---

# Questões de Fixação

## Questão 11
(CESGRANRIO/2024/CAIXA/TÉCNICO BANCÁRIO NOVO/TECNOLOGIA DA INFORMAÇÃO/RIO GRANDE DO SUL)

Em uma empresa de comércio eletrônico, a equipe de desenvolvimento está buscando maneiras de integrar os sistemas de pedidos, de inventário e de pagamento. O gerente de projetos sugere o uso do padrão REST para facilitar essa integração, por ser considerado uma abordagem eficaz e robusta para projetar Interfaces de Programação de Aplicativos (API) que permitem a comunicação entre sistemas distribuídos na web.

Uma das características do padrão REST é a de ser um(a)

a) Conjunto de ferramentas utilizado para testar a performance de aplicativos web.
b) Protocolo de comunicação utilizado para transferência de arquivos entre servidores.
c) Framework utilizado para criar interfaces gráficas de usuário.
d) Estilo arquitetônico que define um conjunto de restrições para o design de sistemas distribuídos.
e) Linguagem de programação utilizada para desenvolver aplicativos web.

**Gabarito:** d

## Questão 12
(CESGRANRIO/2024/BANCO DA AMAZÔNIA/TÉCNICO CIENTÍFICO/TECNOLOGIA DA INFORMAÇÃO)

Um desenvolvedor está projetando um sistema de comunicação entre serviços web e precisa escolher entre SOAP e REST. As características necessárias para o sistema incluem: simplicidade e facilidade de uso; uso de diferentes formatos de dados (não apenas XML); alta performance e baixa latência; e escalabilidade e facilidade de manutenção.

Com base nesses requisitos, um argumento para a escolha correta entre SOAP e REST é que se deve usar

a) REST porque ele oferece melhor suporte para transações complexas e segurança avançada, com apoio de WSDL, além de ser mais escalável e fácil de manter.
b) REST porque ele é baseado em HTTP e permite a comunicação através de diferentes formatos de dados, como XML, JSON e texto simples, sendo mais simples e fácil de usar.
c) SOAP porque ele é baseado em HTML5, usa comandos GET e faz transferência de dados rápida por IPv6.
d) SOAP porque, por ser baseado em JSON e IPv6, é mais leve e oferece melhor performance e baixa latência em comparação com REST.
e) SOAP porque ele permite de forma direta o uso de diferentes formatos de dados como XML, JSON e YAML, além de ser mais simples e fácil de usar por executar com SMTP.

**Gabarito:** b

## Questão 13
(FGV/2024/PREFEITURA DE NOVA IGUAÇU/RJ/AUDITOR FISCAL DO TESOURO MUNICIPAL)

No desenvolvimento de aplicações modernas, o uso de web services é fundamental para a comunicação entre diferentes sistemas de software. Uma das escolhas que um desenvolvedor deve fazer é entre REST e SOAP. Considerando os padrões e práticas atuais, a afirmativa correta sobre REST e SOAP é:

a) REST exige menos largura de banda e recursos, pois usa menos overhead de comunicação.
b) REST suporta apenas o protocolo HTTP, enquanto SOAP pode usar outros protocolos, como SMTP e FTP.
c) REST não é compatível com o formato JSON, favorecendo exclusivamente o uso de XML.
d) REST é um protocolo mais antigo, por isso é mais compatível com sistemas legados.
e) REST e SOAP têm o mesmo desempenho e eficiência em redes com alta latência.

**Gabarito:** a

## Questão 14
(NC-UFPR/2024/UFPR/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

Sobre arquitetura orientada a serviços, é correto afirmar:

a) No cenário em que a TI atuava de forma reativa, período anterior ao da SOA, os serviços eram gerados com fraco acoplamento.
b) A palavra-chave para tratar do projeto, da implementação e da implantação de serviços, por meio da SOA, é o barramento de serviço, também chamado service bus ou enterprise service bus (ESB).
c) Quando o provedor publica os serviços, são gerados registros no padrão universal, chamado WSDL.
d) Quando um sistema deseja consumir algum serviço, ele busca no WSDL.
e) SOAP e REST são padrões de descobrimento que definem as informações sobre os serviços.

**Gabarito:** b

## Questão 15
(FGV/2024/INPE/TECNOLOGISTA JÚNIOR I/ESPECIFICAÇÕES DE REDE/ANÁLISE DE ACESSOS, INFORMAÇÕES E REQUISITOS DE SEGURANÇA/INSTALAÇÃO E ADMINISTRAÇÃO DE EQUIPAMENTOS)

As abordagens REST e SOAP possuem o objetivo de permitir a comunicação entre aplicações web. Com relação ao seu emprego para transmissão de dados, analise as afirmativas a seguir e assinale (V) para a verdadeira e (F) para a falsa.

( ) A transmissão de dados via SOAP é considerada mais segura que via RESTful API's, visto que REST não permite criptografia.
( ) SOAP usa estritamente o formato XML para suas mensagens, enquanto REST permite JSON apenas.
( ) A especificação WS-Security é utilizada exclusivamente no protocolo SOAP.

As afirmativas são, respectivamente:

a) F – V – V.
b) F – V – F.
c) V – F – F.
d) F – F – F.
e) F – F – V.

**Gabarito:** e

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 11 | d |
| 12 | b |
| 13 | a |
| 14 | b |
| 15 | e |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Gabriel Ferreira Pacheco.*