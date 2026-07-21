# Anotações

# Interoperabilidade de Sistemas – SOA e Web Services

## 1.1 Interoperabilidade de Sistemas

- **Conceito:** capacidade de diferentes sistemas, organizações ou dispositivos se **comunicarem e trocarem informações** de forma eficiente e padronizada.
- **Middleware:** aplicação utilizada para realizar a intercomunicação entre sistemas.
- Antigamente, utilizavam-se bibliotecas específicas de consumo; atualmente, usa-se um **barramento** com entradas de solicitações baseadas no serviço desejado.

### 1.1.1 Camadas da Interoperabilidade

1. **Mensagens:** base de toda comunicação; trabalhadas em camada de transporte específica.
   - Protocolos: HTTP, SMTP, IIOP.
   - Formato de empacotamento: XML.
   - Protocolo específico: **SOAP**.
2. **Camada de Serviços:** disponibilização de funcionalidades externamente para consumo.
3. **Camada SOA:** arquitetura efetivamente acessada pelo usuário.
4. **Barramento de Serviços:** estrutura consumida via *web services*.

> [!TIP] DICAS
> - A interoperabilidade **não** é apenas "acessar informações quando necessário" – é a **comunicação padronizada** entre sistemas.
> - Exemplo prático: Gov.br integra mais de **300 serviços** em uma única plataforma.

## 1.2 SOA – Arquitetura Orientada a Serviços

### 1.2.1 Conceito
- ***Service Oriented Architecture***: arquitetura que disponibiliza a estrutura computacional em formato que possibilita a conexão de entidades, softwares e pessoas **sem acesso direto à base de dados**.
- Estratégia que proclama a criação de todos os ativos de software via **programação orientada a serviços**.
- Serviços como **componentes de software**.
- Forma de **arquitetura de sistemas distribuídos**.

### 1.2.2 Vantagens da SOA
- **Reutilização de software.**
- **Aumento da produtividade.**
- **Maior agilidade.**
- **Melhor alinhamento com o negócio.**
- Melhor forma de vender arquitetura para negócio e TI.

## 1.3 Propriedades da SOA

| PROPRIEDADE | DESCRIÇÃO |
|-------------|-----------|
| **Visão Lógica** | Abstração lógica (programas, BDs, processos de negócio); preocupa-se com **O QUE** o negócio oferece |
| **Mensagens de Orientação** | Requisição → resposta entre agentes provedores e solicitantes; encapsulamento (agente não precisa saber como a implementação é feita) |
| **Descrição de Orientação** | Serviço descrito por **metadados processáveis por máquina**; contém apenas detalhes importantes expostos ao público |
| **Granularidade** | Uso de pequeno número de operações com mensagens relativamente grandes e complexas |
| **Orientação de Rede** | Tendência de uso, mas não requisito absoluto |
| **Plataforma Neutra** | Mensagens enviadas em formato padronizado de plataforma neutra |

> [!TIP] DICAS
> - **Encapsulamento:** a "cápsula" protege os métodos/operações internas; a interface permite provocar o serviço via mensagens.
> - **Plataforma neutra:** o barramento não se importa com a tecnologia utilizada (Java, PHP, C#, Oracle, SQL) – apenas disponibiliza a resposta padronizada.

## 1.4 Princípios da SOA (Mnemônico: PaBaA VIRCa)

| PRINCÍPIO | DESCRIÇÃO |
|-----------|-----------|
| **P**adronização do contrato de serviço | Quais serviços serão prestados e quais mensagens podem ser enviadas para cada retorno |
| **B**aixo acoplamento | Independência do serviço para ser utilizado em diferentes sistemas |
| **A**bstração do serviço | Capacidade de extrair a vantagem do serviço |
| **A**utonomia do serviço | Capacidade do serviço de funcionar sozinho |
| **V**isibilidade do serviço | O serviço deve ser acessível externamente |
| **I**ndependência do controle de estado | O serviço não pode depender de estar ocupado ou não para ser consumido |
| **R**eusabilidade | Possibilidade de reutilizar o serviço em diferentes contextos |
| **C**apacidade de composição | Possibilidade de utilizar diferentes serviços para compor um serviço único |

## 1.5 Características da SOA (Mnemônico: A Ré IntePaCo)

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **A**coplamento fraco | Independência entre serviços |
| **R**eutilização | Reuso de componentes/serviços |
| **Inte**roperabilidade | Comunicação padronizada entre sistemas |
| **Pa**dronização | Padrões definidos para contratos e mensagens |
| **Co**mposição | Combinação de serviços para formar soluções maiores |

> [!CAUTION] OBSERVAÇÃO
> **Na SOA, os serviços devem possuir ACOPLAMENTO FRACO, não forte.** O acoplamento fraco promove maior independência entre os recursos externos e facilita a reutilização.

## 1.6 Tabela Resumo – SOA

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Sigla** | Service Oriented Architecture |
| **Objetivo** | Disponibilizar funcionalidades sem acesso direto a dados |
| **Componentes** | Serviços como componentes de software |
| **Comunicação** | Baseada em mensagens (XML, SOAP) |
| **Acoplamento** | Fraco (independência entre serviços) |
| **Princípios** | PaBaA VIRCa |
| **Características** | A Ré IntePaCo |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2024/TCE-AC/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/ÁREA: SISTEMAS DE INFORMAÇÃO)

Julgue o próximo item, relativo a arquitetura de software. A interoperabilidade de sistemas é a capacidade de acessar informações de aplicações quando necessário, independentemente de onde elas estejam armazenadas ou de como sejam processadas.

**Gabarito:** E (Errado) - A interoperabilidade é a capacidade de diferentes sistemas se **comunicarem e trocarem informações** de forma padronizada, não apenas "acessar informações".

## Questão 02
(CESPE/CEBRASPE/2024/TCE-AC/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/ÁREA: SISTEMAS DE INFORMAÇÃO)

Julgue o próximo item, relativo à arquitetura de software.

Na arquitetura orientada a serviços (SOA), os serviços devem possuir acoplamento forte, de modo a se obter maior segurança na comunicação entre os serviços, promovendo uma maior dependência entre os recursos externos.

**Gabarito:** E (Errado) - Na SOA, os serviços devem possuir **acoplamento fraco**, promovendo maior independência entre os recursos.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | E |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Gabriel Ferreira Pacheco.*