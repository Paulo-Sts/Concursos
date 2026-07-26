# Interoperabilidade de Sistemas – SOA e Web Services

## 1. Interoperabilidade de Sistemas

### 1.1 Conceito
- Capacidade de diferentes sistemas, organizações ou dispositivos se comunicarem e trocarem informações de forma eficiente e padronizada.
- Middleware é a aplicação utilizada para realizar a intercomunicação entre sistemas.
- Antigamente, utilizavam-se bibliotecas específicas de consumo; atualmente, usa-se um barramento com entradas de solicitações baseadas no serviço desejado.

### 1.2 Camadas da Interoperabilidade
- Mensagens: base de toda comunicação; trabalhadas em camada de transporte específica.
  - Protocolos: HTTP, SMTP, IIOP;
  - Formato de empacotamento: XML;
  - Protocolo específico: SOAP.
- Camada de Serviços: disponibilização de funcionalidades externamente para consumo.
- Camada SOA: arquitetura efetivamente acessada pelo usuário.
- Barramento de Serviços: estrutura consumida via web services.

> [!TIP] DICAS:
> - A interoperabilidade não é apenas "acessar informações quando necessário" – é a comunicação padronizada entre sistemas.
> - Exemplo prático: Gov.br integra mais de 300 serviços em uma única plataforma.

## 2. SOA – Arquitetura Orientada a Serviços

### 2.1 Conceito
- Service Oriented Architecture: arquitetura que disponibiliza a estrutura computacional em formato que possibilita a conexão de entidades, softwares e pessoas sem acesso direto à base de dados.
- Estratégia que proclama a criação de todos os ativos de software via programação orientada a serviços.
- Serviços como componentes de software.
- Forma de arquitetura de sistemas distribuídos.

### 2.2 Vantagens da SOA
- Reutilização de software;
- Aumento da produtividade;
- Maior agilidade;
- Melhor alinhamento com o negócio;
- Melhor forma de vender arquitetura para negócio e TI.

### 2.3 Propriedades da SOA

| PROPRIEDADE | DESCRIÇÃO |
|-------------|-----------|
| Visão Lógica | Abstração lógica (programas, bds, processos de negócio); preocupa-se com o que o negócio oferece. |
| Mensagens de Orientação | Requisição ⟶ resposta entre agentes provedores e solicitantes; encapsulamento (agente não precisa saber como a implementação é feita). |
| Descrição de Orientação | Serviço descrito por metadados processáveis por máquina; contém apenas detalhes importantes expostos ao público. |
| Granularidade | Uso de pequeno número de operações com mensagens relativamente grandes e complexas. |
| Orientação de Rede | Tendência de uso, mas não requisito absoluto. |
| Plataforma Neutra | Mensagens enviadas em formato padronizado de plataforma neutra. |

> [!TIP] DICAS:
> - Encapsulamento: a "cápsula" protege os métodos/operações internas; a interface permite provocar o serviço via mensagens.
> - Plataforma neutra: o barramento não se importa com a tecnologia utilizada (Java, PHP, C#, Oracle, SQL) – apenas disponibiliza a resposta padronizada.

### 2.4 Princípios da SOA (Mnemônico: PaBaA VIRCa)

| PRINCÍPIO | DESCRIÇÃO |
|-----------|-----------|
| Padronização do contrato de serviço | Quais serviços serão prestados e quais mensagens podem ser enviadas para cada retorno. |
| Baixo acoplamento | Independência do serviço para ser utilizado em diferentes sistemas. |
| Abstração do serviço | Capacidade de extrair a vantagem do serviço. |
| Autonomia do serviço | Capacidade do serviço de funcionar sozinho. |
| Visibilidade do serviço | O serviço deve ser acessível externamente. |
| Independência do controle de estado | O serviço não pode depender de estar ocupado ou não para ser consumido. |
| Reusabilidade | Possibilidade de reutilizar o serviço em diferentes contextos. |
| Capacidade de composição | Possibilidade de utilizar diferentes serviços para compor um serviço único. |

### 2.5 Características da SOA (Mnemônico: A Ré IntePaCo)

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Acoplamento fraco | Independência entre serviços. |
| Reutilização | Reuso de componentes/serviços. |
| Interoperabilidade | Comunicação padronizada entre sistemas. |
| Padronização | Padrões definidos para contratos e mensagens. |
| Composição | Combinação de serviços para formar soluções maiores. |

> [!CAUTION] OBSERVAÇÃO:
> - Na SOA, os serviços devem possuir acoplamento fraco, não forte. O acoplamento fraco promove maior independência entre os recursos externos e facilita a reutilização.

### 2.6 Tabela Resumo – SOA

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Sigla | Service Oriented Architecture. |
| Objetivo | Disponibilizar funcionalidades sem acesso direto a dados. |
| Componentes | Serviços como componentes de software. |
| Comunicação | Baseada em mensagens (XML, SOAP). |
| Acoplamento | Fraco (independência entre serviços). |
| Princípios | PaBaA VIRCa. |
| Características | A Ré IntePaCo. |