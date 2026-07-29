# Arquitetura Hexagonal (Ports and Adapters)

## 1. Visão Geral

### 1.1 Definição e Origem
- Arquitetura de Portas e Adaptadores (Ports and Adapters Architecture).
- Criada em 2005 por Alistair Cockburn.
- É uma abordagem de design de software cujo principal objetivo é isolar o núcleo da aplicação das dependências externas.
- Estruturada em torno de 3 conceitos principais:
  - Núcleo da Aplicação (Application Core);
  - Portas (Ports);
  - Adaptadores (Adapters).

> [!TIP] DICAS:
> - A arquitetura hexagonal também é chamada de Arquitetura de Portas e Adaptadores.
> - O nome "hexagonal" não significa que há seis lados obrigatórios – é uma referência à flexibilidade de comunicação do núcleo com o mundo externo.

## 2. Núcleo da Aplicação (Core)

### 2.1 Definição
- É o coração do sistema, responsável pela lógica de negócios.
- É independente das dependências externas (bancos de dados, APIs, interfaces de usuário).
- Por ser independente, pode ser testado e mantido sem se preocupar com a infraestrutura.
- Pode ser reutilizado em diferentes contextos: aplicações web, APIs, aplicativos móveis.

### 2.2 Componentes do Núcleo

#### 2.2.1 Classes de Domínio (Domain Classes)
- Representam os principais conceitos do negócio (ex.: Pedido, Cliente, Produto).
- Encapsulam os dados e a lógica diretamente relacionados a esses conceitos.
- Cada classe é responsável por manter o estado e a integridade de um conceito do negócio.
- Exemplo: a classe `Pedido` pode ter atributos como `itens`, `data`, `valorTotal` e métodos como `calcularTotal()` e `aplicarDesconto()`.

#### 2.2.2 Serviços de Domínio (Domain Services)
- Classes que contêm lógica de negócios complexa ou que coordenam operações entre várias classes de domínio.
- Quando a lógica não pertence a uma única classe de domínio ou envolve múltiplas classes, ela é colocada em um serviço de domínio.
- Exemplo: um serviço `ProcessarPagamento` pode coordenar a interação entre `Pedido`, `Cliente` e um `Sistema de Pagamento`, verificando saldo, aplicando pagamento e atualizando status.

#### 2.2.3 Regras de Negócios e Lógica (Business Rules and Logic)
- Métodos e operações que implementam a lógica específica do negócio dentro das classes de domínio e serviços de domínio.
- Garantem que as operações estejam de acordo com as regras do negócio (cálculos, validações, transformações de dados).
- Exemplo: o método `calcularTotal()` em uma classe `Pedido` aplica regras de negócio para calcular o valor total, considerando preços, descontos, impostos, etc.

> [!CAUTION] OBSERVAÇÃO:
> - As classes de domínio NÃO devem ser responsáveis pelo armazenamento de dados ou pelas tecnologias usadas para esse fim. Elas são responsáveis apenas pela lógica de negócio.

## 3. Portas (Ports)

### 3.1 Definição
- São interfaces que definem como vai ser a comunicação entre o núcleo da aplicação e o mundo externo.
- Permitem que a aplicação interaja com diferentes tecnologias sem que o núcleo precise saber dos detalhes sobre elas.

### 3.2 Tipos de Portas

| TIPO | DESCRIÇÃO | EXEMPLO |
|------|-----------|---------|
| Portas Primárias (Inbound Ports) | Interfaces que permitem a entrada de dados e comandos no núcleo da aplicação. | Operações de "fazer pedido" ou "calcular preço". |
| Portas Secundárias (Outbound Ports) | Interfaces que permitem que o núcleo envie dados ou solicite operações a sistemas externos. | Operações de "salvar pedido" ou "consultar estoque". |

## 4. Adaptadores (Adapters)

### 4.1 Definição
- Conectam o núcleo da aplicação com tecnologias externas (banco de dados, APIs, interface de usuário).
- Fazem a tradução das chamadas do núcleo para as tecnologias externas e vice-versa.
- Caso haja necessidade de mudança de tecnologias, só é preciso modificar o adaptador correspondente.
- Graças aos adaptadores, o núcleo da aplicação pode ser independente, facilitando manutenção e evolução.

### 4.2 Tipos de Adaptadores

| TIPO | DESCRIÇÃO | EXEMPLO |
|------|-----------|---------|
| Adaptadores Primários (Inbound Adapters) | Conectam a interface de usuário ao núcleo da aplicação. | Controlador HTTP – recebe solicitação web e transforma em chamada de método no núcleo. |
| Adaptadores Secundários (Outbound Adapters) | Conectam o núcleo da aplicação a tecnologias externas. | Implementação de repositório que grava dados em um banco SQL. |

## 5. Relação entre os Componentes

| COMPONENTE | TIPO | FUNÇÃO |
|------------|------|--------|
| Núcleo | — | Lógica de negócios (independente de infraestrutura). |
| Porta Primária | Inbound | Interface de entrada para o núcleo. |
| Adaptador Primário | Inbound | Converte solicitações externas em chamadas ao núcleo. |
| Porta Secundária | Outbound | Interface de saída para sistemas externos. |
| Adaptador Secundário | Outbound | Converte chamadas do núcleo em operações em tecnologias externas. |

> [!TIP] DICAS:
> - Porta ≠ Adaptador. A porta é a interface; o adaptador é a implementação concreta que conecta a porta a uma tecnologia externa.
> - A arquitetura hexagonal não impõe que o núcleo seja responsável por persistência ou tecnologias externas.

## 6. Vantagens da Arquitetura Hexagonal
- Tolerância em relação às mudanças: o núcleo não é afetado por alterações em tecnologias externas;
- Elevada manutenibilidade: as partes do sistema são isoladas e independentes;
- Facilidade de testes: o núcleo pode ser testado sem dependências externas (uso de mocks);
- Reusabilidade: o núcleo pode ser reutilizado em diferentes contextos (web, API, mobile).

## 7. Tabela Resumo – Arquitetura Hexagonal

| COMPONENTE | DESCRIÇÃO | RESPONSABILIDADE |
|------------|-----------|------------------|
| Núcleo | Lógica de negócios. | Classes de domínio, serviços de domínio, regras de negócio. |
| Portas Primárias | Interfaces de entrada (inbound). | Definem como o mundo externo acessa o núcleo. |
| Portas Secundárias | Interfaces de saída (outbound). | Definem como o núcleo acessa o mundo externo. |
| Adaptadores Primários | Implementações de entrada. | Conectam UI/API ao núcleo (ex.: controladores HTTP). |
| Adaptadores Secundários | Implementações de saída. | Conectam o núcleo a DB/APIs externas (ex.: repositórios). |
