# Spring Cloud Zuul 8

## 1. Spring Cloud
- Conjunto de ferramentas que fornece soluções para desafios comuns em sistemas distribuídos e arquiteturas de microsserviços.
- Facilita a implementação de padrões como configuração distribuída, descoberta de serviços, roteamento inteligente, balanceamento de carga e tolerância a falhas.
- A arquitetura de microsserviços diminui o acoplamento entre módulos e permite escalar o desenvolvimento do time.
- Na arquitetura monolítica, o erro de um módulo pode transbordar para outros, tornando o sistema mais lento conforme cresce.
- Na arquitetura de microsserviços, cada módulo é um serviço independente, e o erro de um não afeta os demais.
- A resiliência dos serviços é um desafio crítico em microsserviços.

> [!TIP] DICAS: 
> - Spring Cloud resolve problemas de sistemas distribuídos, como descoberta de serviços, roteamento e resiliência.
> - Microsserviços permitem times dedicados por serviço, beneficiando a gestão.

## 2. Spring Cloud Netflix
- Subprojeto do Spring Cloud que implementa tecnologias para microsserviços.

### 2.1 Componentes do Spring Cloud Netflix
| COMPONENTE | FUNÇÃO |
|---|---|
| Eureka | Servidor de descoberta de serviços para registro e obtenção de nomes lógicos |
| Zuul | API Gateway para roteamento de requisições e segurança |
| Hystrix | Implementação do padrão Circuit Breaker para tolerância a falhas |
| Ribbon | Balanceamento de carga entre múltiplos nós de um serviço |
| Feign | Comunicação síncrona ou assíncrona entre serviços |
| Turbine | Coleta de métricas e monitoramento |

### 2.2 Detalhamento dos Componentes
- Eureka:
  - Serve como servidor de descoberta de serviços.
  - Serviços podem se registrar e obter um nome lógico.
- Hystrix:
  - Implementa o padrão Circuit Breaker.
  - Verifica a disponibilidade programada dos serviços.
  - Se um serviço ficar indisponível, os demais não caem junto.
- Ribbon:
  - Permite subir mais nós de um determinado serviço.
  - Realiza balanceamento de carga sem perder chamadas dos outros serviços.
- Feign:
  - Cuida das comunicações interserviços.
  - Suporta chamadas síncronas e assíncronas.
- Turbine:
  - Responsável por métricas e monitoramento dos serviços.

> [!CAUTION] OBSERVAÇÃO: 
> - Os componentes do Spring Cloud Netflix são frequentemente cobrados em provas, principalmente Eureka, Zuul e Hystrix.

## 3. Spring Cloud Netflix Zuul
- Servidor de borda (Edge Server) que fornece roteamento dinâmico, monitoramento, resiliência e segurança para aplicações baseadas em microsserviços.
- Atua como um API Gateway, sendo o ponto único de entrada para todas as requisições externas.
- Direciona as requisições para os serviços internos apropriados.

### 3.1 Principais Características
- Roteamento Dinâmico:
  - Redireciona solicitações para diferentes serviços com base em regras configuráveis.
- Filtros Pré- e Pós-Processamento:
  - Permite a execução de lógica personalizada antes e depois do processamento de uma requisição.
- Monitoramento e Métricas:
  - Oferece insights sobre o tráfego e desempenho das requisições.
- Segurança:
  - Implementa autenticação, autorização e outras políticas de segurança em um único ponto.

### 3.2 Configurando o Zuul
- Passo 1: Criar um projeto Spring Boot com a dependência spring-cloud-starter-netflix-zuul.
- Passo 2: Anotar a classe principal com @EnableZuulProxy para habilitar o Zuul Proxy.
- Passo 3: Configurar as propriedades no arquivo application.properties.

> [!TIP] DICAS: 
> - A anotação correta para habilitar o Zuul Proxy é @EnableZuulProxy.
> - Uma vez adicionada a dependência no gerenciamento de dependências, todas as configurações necessárias são baixadas automaticamente.

### 3.3 Funcionamento do Roteamento
- Todas as requisições passam pelo Zuul.
- O Zuul redireciona para os serviços internos apropriados.
- Todas as respostas retornam passando novamente pelo Zuul.

### 3.4 Segurança com Zuul
- Autenticação e Autorização:
  - Verificação de tokens JWT.
  - Validação de credenciais.
- Limitação de Taxa (Rate Limiting):
  - Controle do número de requisições por cliente.
- Filtragem de Conteúdo:
  - Bloqueio de requisições maliciosas ou inadequadas.

## 4. Integração e Implantação Contínuas (CI/CD)
- Integração Contínua (CI):
  - Desenvolvedores são incentivados a fazer pequenos ajustes de código.
  - Mesclagem do código na ramificação principal.
  - Validação usando testes automatizados a cada commit ou push.
- Entrega Contínua (CD):
  - Após a bateria de testes e integração ao repositório.
  - Deploy automatizado em um ambiente específico.
  - Garantia de entrega contínua.

> [!TIP] DICAS: 
> - CI = testes automatizados a cada commit/push.
> - CD = deploy automatizado após os testes.
> - Zuul e Eureka são ferramentas para microsserviços, não para pipelines de CI/CD.

## 5. Conceitos-Chave para Provas
- Zuul = API Gateway = Edge Server = Ponto único de entrada para requisições externas.
- Eureka = Service Discovery = Registro e descoberta de serviços.
- Hystrix = Circuit Breaker = Tolerância a falhas.
- @EnableZuulProxy = anotação para habilitar o Zuul em uma aplicação Spring Boot.

> [!CAUTION] OBSERVAÇÃO: 
> - Não confundir Zuul (API Gateway) com Eureka (Service Discovery) ou Hystrix (Circuit Breaker).
> - Apache Tomcat é um servidor de aplicação Java, não tem relação com descoberta de serviços ou API Gateway.
> - Swagger é utilizado para documentação de APIs, não para segurança ou roteamento.