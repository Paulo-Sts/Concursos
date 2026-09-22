# Características e Implementação de Microsserviços

## 1. Natureza dos Microsserviços
- Baseia-se em serviços autônomos onde cada um é responsável por uma função de negócio específica.
- Baixo acoplamento ⟶ alterações em um serviço não exigem modificações nos demais.
- Alta coesão ⟶ cada unidade concentra uma única responsabilidade bem delimitada.
- Visão conceitual de um sistema composto por peças independentes que colaboram entre si.

### 1.1 Independência Estrutural e Operacional
- Cada microsserviço possui código próprio sem compartilhamento de base de código com outros serviços.
- Dados isolados ⟶ cada serviço gerencia seu próprio banco de dados ou repositório de informações.
- Ciclo de vida independente abrangendo as fases de desenvolvimento, testes e implantação.
- Operação e evolução independentes permitindo o deploy de um serviço sem afetar o sistema global.
- Escalabilidade granular ⟶ apenas os serviços com maior demanda recebem mais recursos.
- Flexibilidade tecnológica permitindo o uso de diferentes linguagens, frameworks e bancos de dados.

> [!CAUTION] OBSERVAÇÃO: 
> - A autonomia e o isolamento de dados são os pilares que reduzem as dependências e facilitam a evolução contínua da arquitetura.

## 2. Comunicação entre Serviços
- Interação realizada através de interfaces de programação de aplicações (APIs) leves ou mensageria.
- Foco em permitir a colaboração dos serviços sem criar acoplamento rígido entre eles.

### 2.1 Comunicação Síncrona
- Baseada em protocolos como REST (HTTP) ou gRPC para alto desempenho.
- Caracteriza-se por chamadas diretas entre os serviços.
- Implementação simples e de fácil compreensão didática.
- Cria cadeias de dependência ⟶ uma falha em um serviço pode gerar uma cascata de falhas no sistema.
- Recomendada para interações que exigem rapidez e baixa latência.

### 2.2 Comunicação Assíncrona
- Utiliza filas, tópicos e eventos com ferramentas como Kafka ou RabbitMQ.
- Proporciona maior desacoplamento pois os serviços não precisam responder imediatamente.
- Aumenta a resiliência do sistema permitindo que mensagens sejam processadas mesmo após falhas temporárias.
- Modelo ideal para fluxos orientados a eventos e sistemas que exigem alta disponibilidade.

## 3. Modelos de Implementação e Operação
- Utilização de containers e orquestradores para gerenciar a complexidade do ambiente.

### 3.1 Containers e Orquestração
- Containers como Docker ou Podman empacotam o serviço com todas as suas dependências.
- Garantem portabilidade, isolamento e consistência entre diferentes ambientes de execução.
- Orquestradores como o Kubernetes gerenciam o deploy, a escalabilidade, a saúde e a resiliência.
- Uso de imagens imutáveis para assegurar a paridade entre ambientes de desenvolvimento e produção.

### 3.2 Tecnologias Modernas de Execução
- Serverless ou Functions-as-a-Service para execução sob demanda de serviços pequenos.
- Service Mesh ⟶ adiciona controle de tráfego, segurança e observabilidade sem alterar o código fonte.
- Edge e Micro-VMs oferecem isolamento forte e inicialização rápida para alta segurança.
- Infraestrutura elástica permitindo que os serviços escalem horizontalmente conforme a necessidade.

> [!TIP] DICAS: 
> - O uso de containers é a principal forma de empacotamento em microsserviços por padronizar a execução.
> - A automação através de pipelines de CI/CD é a base fundamental para a entrega contínua nesta arquitetura.