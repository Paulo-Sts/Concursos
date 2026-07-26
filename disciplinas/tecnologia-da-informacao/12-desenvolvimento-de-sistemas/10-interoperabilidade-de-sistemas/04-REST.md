# Interoperabilidade de Sistemas – SOA e Web Services 4

## 1. REST – Representation State Transfer
- REST (Representational State Transfer) é um estilo de arquitetura de sistemas de informações distribuídas.
- É um estilo de projetar aplicativos na WEB fracamente acoplados que contam com recursos nomeados em forma de URL, URI ou URN.
- REST não é um padrão ou protocolo, mas sim um estilo arquitetural – uma nova forma de pensar sobre HTTP.

> [!CAUTION] OBSERVAÇÃO:
> - REST não é um protocolo e não tem formato obrigatório – é um estilo arquitetural que define restrições para o design de sistemas distribuídos.

### 1.1 Recursos e Métodos HTTP
- URLs são substantivos (recursos);
- Métodos HTTP são verbos (ações sobre recursos).

| MÉTODO | DESCRIÇÃO |
|--------|-----------|
| GET | Obtém o estado atual do recurso identificado (busca recurso). |
| PUT | Atualiza um recurso existente. |
| POST | Cria um novo recurso. |
| DELETE | Elimina o recurso identificado. |

### 1.2 Princípios Fundamentais do REST

| PRINCÍPIO | DESCRIÇÃO |
|-----------|-----------|
| Qualquer informação disponível é um recurso | Tudo que pode ser nomeado é um recurso. |
| Todos os recursos devem ser identificados | Identificação via URI. |
| Hipermídia como máquina de estado da aplicação | Navegação baseada em links/hipertexto. |
| Interface uniforme | Métodos HTTP padronizados (GET, POST, PUT, DELETE). |
| Recursos com múltiplas representações | Suporte a XML, JSON, texto simples, etc. |
| Stateless | Não armazenamento de estado – cada requisição é independente. |

> [!TIP] DICAS:
> - O princípio stateless é um dos mais cobrados em provas – REST não mantém o estado da conexão ou da comunicação.
> - Uniformidade de API e facilidade no desenvolvimento são vantagens do REST.

### 1.3 Formatos de Representação de Recursos
- Não existe um padrão obrigatório – REST permite múltiplos formatos:
  - XML;
  - RSS/Atom – para publicação de feeds;
  - JSON – formato baseado em texto, simples, com economia de banda;
  - Texto simples.

> [!TIP] DICAS:
> - JSON tem ganhado destaque como substituto do XML por sua simplicidade, rapidez e menor consumo de banda.
> - REST é compatível com JSON, XML e texto simples – não é restrito a apenas um formato.

### 1.4 Os Três Pilares do REST para Criar um Web Service

| PILAR | DESCRIÇÃO |
|-------|-----------|
| Mime Type | Permite alterar as representações de um mesmo conteúdo sob perspectivas diferentes. |
| URL | Usada para identificar um recurso – cada recurso tem a sua própria. |
| Métodos HTTP | Responsáveis por provocar alterações nos recursos identificados pelas URLs. |

### 1.5 REST x SOAP – Comparativo

| ASPECTO | REST | SOAP |
|---------|------|------|
| Natureza | Estilo arquitetural. | Protocolo. |
| Formato | Múltiplos (JSON, XML, texto). | Exclusivamente XML. |
| Protocolo | Geralmente HTTP (não obrigatório). | HTTP, SMTP, FTP, etc. |
| Estado | Stateless (sem estado). | Pode ter estado. |
| Segurança | HTTPS (TLS). | WS-Security (padrão próprio). |
| Desempenho | Mais leve, menor overhead. | Mais pesado, maior overhead. |
| Largura de banda | Menor consumo. | Maior consumo. |
| Complexidade | Simples. | Complexa (WS-*, WSDL, etc.). |
| Acoplamento | Fraco. | Forte. |

> [!CAUTION] OBSERVAÇÕES CRÍTICAS (PEGADINHAS DE PROVA):
> - SOAP usa estritamente XML para suas mensagens; REST permite JSON, XML, texto simples e outros formatos.
> - REST não é mais seguro ou menos seguro que SOAP – ambos podem usar criptografia (HTTPS no REST; WS-Security no SOAP).
> - SOAP pode usar outros protocolos além de HTTP (SMTP, FTP) – REST geralmente usa HTTP.

#### 1.5.1 WS-Security
- Especificação utilizada exclusivamente no protocolo SOAP para segurança em web services.

### 1.6 Vantagens do REST
- Simplicidade e facilidade de uso;
- Uso de diferentes formatos de dados (não apenas XML);
- Alta performance e baixa latência – menos overhead de comunicação;
- Escalabilidade e facilidade de manutenção;
- Exige menos largura de banda e recursos.

### 1.7 Tabela Resumo – REST

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Definição | Estilo arquitetural para sistemas distribuídos. |
| Recursos | Identificados por URI/URL/URN. |
| Métodos | GET, POST, PUT, DELETE (verbos HTTP). |
| Formatos | XML, JSON, texto, RSS/Atom (múltiplos). |
| Estado | Stateless (sem estado). |
| Acoplamento | Fraco. |
| Princípios | Recursos, identificação, interface uniforme, múltiplas representações, stateless, hipermídia. |
| Vantagens | Simplicidade, desempenho, flexibilidade, escalabilidade. |