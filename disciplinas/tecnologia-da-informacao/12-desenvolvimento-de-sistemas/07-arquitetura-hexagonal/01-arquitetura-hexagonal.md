# Anotações

# Arquitetura Hexagonal (Ports and Adapters)

## 1.1 Visão Geral

- **Arquitetura de Portas e Adaptadores** (*Ports and Adapters Architecture*).
- Criada em **2005** por **Alistair Cockburn**.
- É uma abordagem de *design* de software cujo principal objetivo é **isolar o núcleo da aplicação das dependências externas**.
- Estruturada em torno de **3 conceitos principais**:
  - **Núcleo da Aplicação** (*Application Core*);
  - **Portas** (*Ports*);
  - **Adaptadores** (*Adapters*).

> [!TIP] DICAS
> - A arquitetura hexagonal também é chamada de **Arquitetura de Portas e Adaptadores**.
> - O nome "hexagonal" não significa que há seis lados obrigatórios – é uma referência à flexibilidade de comunicação do núcleo com o mundo externo.

## 1.2 Núcleo da Aplicação (*Core*)

- É o **coração do sistema**, responsável pela **lógica de negócios**.
- É **independente das dependências externas** (bancos de dados, APIs, interfaces de usuário).
- Por ser independente, pode ser **testado e mantido** sem se preocupar com a infraestrutura.
- Pode ser **reutilizado** em diferentes contextos: aplicações *web*, APIs, aplicativos móveis.

### 1.2.1 Componentes do Núcleo

**1. Classes de Domínio (*Domain Classes*):**
- Representam os principais conceitos do negócio (ex.: **Pedido**, **Cliente**, **Produto**).
- Encapsulam os **dados** e a **lógica** diretamente relacionados a esses conceitos.
- Cada classe é responsável por manter o **estado** e a **integridade** de um conceito do negócio.
- Exemplo: a classe `Pedido` pode ter atributos como `itens`, `data`, `valorTotal` e métodos como `calcularTotal()` e `aplicarDesconto()`.

**2. Serviços de Domínio (*Domain Services*):**
- Classes que contêm **lógica de negócios complexa** ou que **coordenam operações** entre várias classes de domínio.
- Quando a lógica não pertence a uma única classe de domínio ou envolve múltiplas classes, ela é colocada em um serviço de domínio.
- Exemplo: um serviço `ProcessarPagamento` pode coordenar a interação entre `Pedido`, `Cliente` e um `Sistema de Pagamento`, verificando saldo, aplicando pagamento e atualizando status.

**3. Regras de Negócios e Lógica (*Business Rules and Logic*):**
- Métodos e operações que implementam a **lógica específica do negócio** dentro das classes de domínio e serviços de domínio.
- Garantem que as operações estejam de acordo com as regras do negócio (cálculos, validações, transformações de dados).
- Exemplo: o método `calcularTotal()` em uma classe `Pedido` aplica regras de negócio para calcular o valor total, considerando preços, descontos, impostos, etc.

> [!CAUTION] OBSERVAÇÃO
> **As classes de domínio NÃO devem ser responsáveis pelo armazenamento de dados ou pelas tecnologias usadas para esse fim.** Elas são responsáveis apenas pela lógica de negócio.

## 1.3 Portas (*Ports*)

- São **interfaces** que definem **como** vai ser a comunicação entre o núcleo da aplicação e o mundo externo.
- Permitem que a aplicação interaja com diferentes tecnologias **sem que o núcleo precise saber dos detalhes** sobre elas.

### 1.3.1 Tipos de Portas

| TIPO | DESCRIÇÃO | EXEMPLO |
|------|-----------|---------|
| **Portas Primárias (*Inbound Ports*)** | Interfaces que permitem a **entrada** de dados e comandos no núcleo da aplicação | Operações de "fazer pedido" ou "calcular preço" |
| **Portas Secundárias (*Outbound Ports*)** | Interfaces que permitem que o núcleo **envie dados ou solicite operações** a sistemas externos | Operações de "salvar pedido" ou "consultar estoque" |

## 1.4 Adaptadores (*Adapters*)

- **Conectam** o núcleo da aplicação com tecnologias externas (banco de dados, APIs, interface de usuário).
- Fazem a **tradução** das chamadas do núcleo para as tecnologias externas e vice-versa.
- Caso haja necessidade de **mudança de tecnologias**, só é preciso modificar o **adaptador correspondente**.
- Graças aos adaptadores, o núcleo da aplicação pode ser **independente**, facilitando manutenção e evolução.

### 1.4.1 Tipos de Adaptadores

| TIPO | DESCRIÇÃO | EXEMPLO |
|------|-----------|---------|
| **Adaptadores Primários (*Inbound Adapters*)** | Conectam a interface de usuário ao núcleo da aplicação | Controlador HTTP – recebe solicitação *web* e transforma em chamada de método no núcleo |
| **Adaptadores Secundários (*Outbound Adapters*)** | Conectam o núcleo da aplicação a tecnologias externas | Implementação de repositório que grava dados em um banco SQL |

## 1.5 Relação entre os Componentes

| COMPONENTE | TIPO | FUNÇÃO |
|------------|------|--------|
| **Núcleo** | — | Lógica de negócios (independente de infraestrutura) |
| **Porta Primária** | *Inbound* | Interface de entrada para o núcleo |
| **Adaptador Primário** | *Inbound* | Converte solicitações externas em chamadas ao núcleo |
| **Porta Secundária** | *Outbound* | Interface de saída para sistemas externos |
| **Adaptador Secundário** | *Outbound* | Converte chamadas do núcleo em operações em tecnologias externas |

## 1.6 Vantagens da Arquitetura Hexagonal

- **Tolerância em relação às mudanças:** o núcleo não é afetado por alterações em tecnologias externas.
- **Elevada manutenibilidade:** as partes do sistema são isoladas e independentes.
- **Facilidade de testes:** o núcleo pode ser testado sem dependências externas (uso de *mocks*).
- **Reusabilidade:** o núcleo pode ser reutilizado em diferentes contextos (web, API, mobile).

> [!TIP] DICAS
> - **Porta ≠ Adaptador.** A porta é a **interface**; o adaptador é a **implementação concreta** que conecta a porta a uma tecnologia externa.
> - A arquitetura hexagonal **não** impõe que o núcleo seja responsável por persistência ou tecnologias externas.

## 1.7 Tabela Resumo – Arquitetura Hexagonal

| COMPONENTE | DESCRIÇÃO | RESPONSABILIDADE |
|------------|-----------|------------------|
| **Núcleo** | Lógica de negócios | Classes de domínio, serviços de domínio, regras de negócio |
| **Portas Primárias** | Interfaces de entrada (*inbound*) | Definem como o mundo externo acessa o núcleo |
| **Portas Secundárias** | Interfaces de saída (*outbound*) | Definem como o núcleo acessa o mundo externo |
| **Adaptadores Primários** | Implementações de entrada | Conectam UI/API ao núcleo (ex.: controladores HTTP) |
| **Adaptadores Secundários** | Implementações de saída | Conectam o núcleo a DB/APIs externas (ex.: repositórios) |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2022/BANRISUL/DESENVOLVIMENTO DE SISTEMAS)

A respeito de tecnologias de integração, julgue o próximo item. Em uma arquitetura hexagonal, as classes de domínio independem das classes de infraestrutura, tecnologias e sistemas externos.

**Gabarito:** C (Correto)

## Questão 02
(FGV/2024/CGM DE BELO HORIZONTE - MG/AUDITOR INTERNO - CIÊNCIA DA COMPUTAÇÃO – MANHÃ)

Assinale a opção que indica as vantagens que a adoção das arquiteturas do tipo hexagonal apresenta para o desenvolvimento de aplicações Java.

a) Tolerância em relação às mudanças, elevada manutenibilidade e facilidade de testes.
b) Tolerância a falhas nas cargas das classes, elevada integração com diversas plataformas tecnológicas e facilidade de fusão de dados semi-estruturados.
c) Tolerância em relação às constantes variações tecnológicas, elevada reusabilidade de dados e amplo suporte ao versionamento de códigos fonte.
d) Tolerância em relação às constantes alterações entre os times de desenvolvedores, elevada rastreabilidade do projeto de software e baixo repúdio aos testes de funções e códigos executados por terceiros.

**Gabarito:** a

## Questão 03
(CESPE/CEBRASPE/2023/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO - PERFIL: DESENVOLVIMENTO DE SOFTWARE)

Acerca de blockchain, conceitos de inteligência artificial, arquitetura hexagonal e gestão de conteúdo, julgue o item a seguir. Em uma arquitetura hexagonal, como as classes de domínio estão relacionadas ao negócio do sistema e seus dados, elas devem ser responsáveis pelo armazenamento de dados e as tecnologias usadas para esse fim.

**Gabarito:** E (Errado) - As classes de domínio **não** devem ser responsáveis pelo armazenamento de dados ou pelas tecnologias usadas para esse fim. Essa é uma responsabilidade dos **adaptadores secundários**.

## Questão 04
(FGV/2024/CGE-PB/AUDITOR DE CONTAS PÚBLICAS - AUDITORIA DE TECNOLOGIA DA INFORMAÇÃO)

A analista Joana está desenvolvendo a aplicação ParaibaCerta. Joana implementou o modelo e o repositório da camada de persistência, mas ainda não escolheu qual banco de dados irá utilizar. Joana também implementou um teste automatizado para determinado fluxo da interface gráfica da ParaibaCerta. À luz da arquitetura hexagonal, ao implementar o repositório da camada de persistência e o teste automatizado, Joana adicionou à ParaibaCerta, respectivamente:

a) uma porta primária e uma porta secundária.
b) uma porta primária e um adaptador primário.
c) uma porta secundária e um adaptador primário.
d) um adaptador secundário e uma porta secundária.
e) um adaptador primário e um adaptador secundário.

**Gabarito:** c - O repositório da camada de persistência é um **adaptador secundário**; o teste automatizado da interface gráfica é um **adaptador primário**.

## Questão 05
(FGV/2023/TCE-SP/AGENTE DA FISCALIZAÇÃO – TI)

O analista Marcos desenvolveu um novo frontend para a aplicação TCEDigital, a fim de modernizar a experiência do usuário. O backend da TCEDigital é exposto por meio de uma Application Programming Interface (API) web. O novo frontend desenvolvido por Marcos utiliza a API web do backend já existente e não exige a desativação do frontend antigo, com ambos coexistindo ao mesmo tempo. À luz da arquitetura hexagonal, Marcos adicionou à TCEDigital um(a):

a) aplicação.
b) porta primária.
c) porta secundária.
d) adaptador primário.
e) adaptador secundário.

**Gabarito:** d - O novo *frontend* é um **adaptador primário** (*inbound*), pois conecta a interface de usuário ao núcleo da aplicação.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | a |
| 03 | E |
| 04 | c |
| 05 | d |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pela professora Ana Júlia B. Souza.*