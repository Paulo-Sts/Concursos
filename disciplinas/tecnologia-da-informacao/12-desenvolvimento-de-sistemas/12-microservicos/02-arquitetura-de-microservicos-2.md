# Microserviços – características Arquiteturais e Implementação

## 1. Natureza dos Microserviços

### 1.1 Características Arquiteturais Fundamentais
- Arquitetura baseada em serviços autônomos, cada um responsável por uma função específica.
- Baixo acoplamento: mudanças em um serviço não exigem alterações nos demais.
- Alta coesão: cada serviço concentra uma única responsabilidade bem definida.
- Visão conceitual: o sistema é formado por várias "peças" independentes que colaboram.

> [!TIP] DICAS: 
> - Lembre-se: baixo acoplamento + alta coesão são os pilares de uma boa arquitetura de microserviços.

### 1.2 Independência Estrutural
- Cada microsserviço possui código próprio, sem compartilhamento de base de código.
- Dados isolados: cada serviço gerencia seu próprio banco ou repositório.
- Ciclo de vida independente: desenvolvimento, testes e *deploy* ocorrem separadamente.
- Essa autonomia reduz dependências e facilita evolução contínua.

> [!CAUTION] OBSERVAÇÃO: 
> - O isolamento de dados é uma diferença crucial entre microserviços e SOA. Em SOA, o compartilhamento de banco é comum; em microserviços, cada serviço tem seu próprio banco.

## 2. Comunicação entre Serviços

### 2.1 Visão Geral
- Interação via APIs leves, como REST (HTTP) ou gRPC (alto desempenho).
- Alternativa assíncrona: mensageria com Kafka, RabbitMQ ou similares.
- Comunicação projetada para ser simples, padronizada e resiliente.
- O foco conceitual é permitir colaboração sem criar acoplamento rígido.

### 2.2 Comunicação Síncrona
- Baseada em REST ou gRPC, com chamadas diretas entre serviços.
- Simples de implementar e fácil de entender.
- Porém, cria cadeias de dependência: se um serviço falha, pode gerar cascata de falhas.
- Adequada para interações rápidas e de baixa latência.

### 2.3 Comunicação Assíncrona
- Feita por filas, tópicos e eventos, usando ferramentas como Kafka ou RabbitMQ.
- Serviços não precisam responder imediatamente: maior desacoplamento.
- Aumenta a resiliência, pois mensagens podem ser processadas mesmo com falhas temporárias.
- Ideal para fluxos *event-driven* e sistemas de alta disponibilidade.

| CARACTERÍSTICA | SINCRONA | ASSÍNCRONA |
|----------------|----------|------------|
| Exemplo de tecnologia | REST, gRPC | Kafka, RabbitMQ |
| Resposta | Imediata | Pode ser processada depois |
| Acoplamento | Maior | Menor |
| Resiliência | Menor (cascata de falhas) | Maior (filas retêm mensagens) |

## 3. Containers e Orquestração

### 3.1 Containers
- Containers (Docker, Podman) empacotam serviços com tudo que precisam para rodar.
- Garantem portabilidade, isolamento e consistência entre ambientes.
- Imagens imutáveis permitem consistência entre ambientes (desenvolvimento → teste → produção).

### 3.2 Orquestração com Kubernetes
- Gerencia *deploy*, escalabilidade, saúde e resiliência dos serviços.
- Essencial para operar microsserviços em larga escala com automação e confiabilidade.
- Permite infraestrutura elástica: serviços sob demanda, escalando horizontalmente conforme necessidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Kubernetes é o orquestrador de containers mais cobrado em concursos. Docker é o container mais comum, mas não faz orquestração sozinho.

## 4. Modelos de Implementação

### 4.1 Padronização Operacional
- Containers como principal forma de empacotamento: isolam dependências, garantem portabilidade e padronizam execução.
- Pipelines de CI/CD, versionamento e automação como base da entrega contínua.

### 4.2 Modelos Modernos de Execução

| MODELO | DESCRIÇÃO |
|--------|-----------|
| Containers orquestrados | Kubernetes como padrão de mercado para *deploy*, escalabilidade, *health checks* e resiliência |
| *Serverless* / FaaS | Execução sob demanda, ideal para serviços pequenos e altamente *event-driven* |
| *Service Mesh* (Istio, Linkerd) | Adiciona controle de tráfego, segurança e observabilidade sem alterar o código |
| *Edge* e Micro-VMs (Firecracker) | Isolamento mais forte com inicialização rápida, usado em ambientes de alta segurança |

> [!TIP] DICAS: 
> - *Serverless* não significa "sem servidor", mas sim que a infraestrutura é gerenciada automaticamente pelo provedor.
> - *Service Mesh* é uma camada de infraestrutura dedicada a gerenciar a comunicação entre serviços, sem alterar o código da aplicação.