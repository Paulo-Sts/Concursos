# Arquitetura de Software

## 1. Conceito de Arquitetura de Software
- Permite que no desenvolvimento de projetos seja realizado o melhor uso possível do tempo e do código em sistemas atuais.
- Segundo a norma ISO/IEC/IEEE 42.010:2022, consiste na estrutura fundamental de um sistema composta por suas partes, relacionamentos internos e com o ambiente.
- Projetada especificamente para atender aos requisitos definidos para o sistema.
- Surgiu como resposta à crise do software na década de 1960, quando sistemas complexos tornaram-se difíceis e caros de manter.
- Consolidou-se como disciplina fundamental da engenharia de software na década de 1980 com foco em lógica de projeto para facilitar a manutenção.

## 2. Modelos de Arquitetura e Evolução Cronológica

### 2.1 Arquitetura Monolítica
- Surgiu em 1970 e consolidou-se em 1980 como a primeira abordagem estruturada para sistemas.
- Todas as funcionalidades como interface, lógica de negócios e acesso a dados são desenvolvidas juntas em um único arquivo executável.
- Caracteriza-se pela interdependência total entre as partes do sistema.

### 2.2 Arquitetura Cliente-Servidor
- Criada em 1980 com o intuito de distribuir a carga de trabalho para gerir recursos com eficiência.
- O cliente é responsável pela interação com o usuário e envio de solicitações.
- O servidor processa as requisições, executa a lógica de negócios e devolve os resultados ao cliente.

### 2.3 Arquitetura Orientada a Objetos
- Surgiu em 1980 visando imitar o mundo real para facilitar modularidade, reutilização e manutenção.
- Organiza o sistema em objetos que representam instâncias reais de classes.
- As classes funcionam como um molde ou formulário, enquanto os objetos são o preenchimento real desse molde.

### 2.4 Arquitetura MVC
- Surgiu em 1970 e consolidou-se em 1990 para dividir aplicações em três componentes distintos.
- Model ⟶ representa os dados e a lógica de negócios da aplicação;
- View ⟶ componente responsável por apresentar os dados ao usuário;
- Controller ⟶ atua como intermediário que recebe entradas do usuário e determina qual view exibir.

### 2.5 Arquitetura em Camadas
- Consolidada em 1990, organiza o software em níveis com objetivos específicos.
- Camada de Apresentação ⟶ interface e interação com o usuário final;
- Camada de Negócios ⟶ processamento de entradas e aplicação de regras e validações;
- Camada de Dados ⟶ gestão da persistência de informações e conexão com bancos de dados.

### 2.6 Arquitetura de Objetos Distribuídos
- Permite que objetos em sistemas e máquinas diferentes interajam como se estivessem no mesmo ambiente.
- Utiliza protocolos de comunicação e middleware específico como CORBA, RMI ou DCOM.

### 2.7 Arquitetura Peer-to-Peer
- Surgiu em 1990 e foca na distribuição de tarefas de forma descentralizada entre os participantes da rede.
- Todos os nós ou peers são iguais, atuando simultaneamente como clientes e servidores sem necessidade de um servidor central.

### 2.8 Arquitetura Orientada a Serviços (SOA)
- Surgiu em 2000 para permitir a interação de diferentes serviços distribuídos em plataformas distintas.
- Composta por serviços que se comunicam através de interfaces bem definidas e protocolos como HTTP.

### 2.9 Arquitetura Event-Driven
- Criada no ano 2000 para sistemas que precisam reagir rapidamente a mudanças de estado.
- O fluxo de trabalho é determinado por ocorrências significativas detectadas e tratadas pelo sistema.

### 2.10 Arquitetura Hexagonal
- Design de software independente de tecnologia e frameworks surgido em 2000.
- Núcleo ⟶ contém a lógica de negócio e regras de domínio;
- Ports ⟶ interfaces que definem a interação do núcleo com o exterior;
- Adapters ⟶ implementações que adaptam interfaces externas para o que o núcleo espera.

### 2.11 Arquitetura de Microsserviços
- Surgiu em 2010 para dividir aplicações monolíticas em serviços menores e focados em funções específicas.
- Cada serviço é independente e realiza a comunicação com os demais através de APIs.

### 2.12 Arquitetura Serverless
- Surgiu em 2010 para que desenvolvedores foquem apenas na lógica de negócios.
- A nuvem gerencia integralmente a escalabilidade, disponibilidade e manutenção dos servidores.

## 3. Resumo Cronológico de Arquiteturas e Padrões

| DÉCADA | TIPO DE ARQUITETURA OU PADRÃO | OBJETIVO PRINCIPAL |
|---|---|---|
| 1960 | Crise do software | Organizar código de fonte de maneira sustentável |
| 1970 | Monolítica e mvc | Simplificar desenvolvimento e organizar em componentes |
| 1980 | Cliente-servidor, objetos e camadas | Distribuir carga e facilitar reutilização de código |
| 1990 | Soap, p2p e objetos distribuídos | Comunicação entre plataformas e descentralização |
| 2000 | Soa, rest, eventos e hexagonal | Interação de serviços e independência tecnológica |
| 2010 | Microsserviços e serverless | Serviços independentes e gestão total por nuvem |

> [!TIP] DICAS: 
> - Para diferenciar Classe de Objeto: a Classe é o molde (ex: planta de uma casa) e o Objeto é a instância real (ex: a casa construída).
> - O SOAP e o REST não são arquiteturas, mas sim padrões de comunicação usados para transferência de dados entre aplicações.

> [!CAUTION] OBSERVAÇÃO: 
> - A arquitetura de microsserviços é frequentemente cobrada em provas de concurso em contraposição direta à arquitetura monolítica.
> - Na arquitetura monolítica, uma falha em uma funcionalidade pode comprometer o arquivo executável único do sistema.