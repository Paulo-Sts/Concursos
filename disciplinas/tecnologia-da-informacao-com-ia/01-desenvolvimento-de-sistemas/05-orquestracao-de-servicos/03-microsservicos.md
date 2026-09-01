# Arquitetura de Microsserviços

## 1. Definição e Organização
- Organiza uma aplicação como um conjunto de serviços pequenos, independentes e especializados.
- Cada serviço é responsável por uma função específica do negócio.
- A estrutura baseia-se na descentralização ⟶ no modelo monolítico há um banco de dados único, enquanto nos microsserviços cada serviço possui sua própria base de dados.
- Frequentemente utiliza um API Gateway como ponto de entrada para gerenciar a comunicação com o cliente.

## 2. Características Principais

### 2.1 Independência Operacional
- Cada microsserviço pode ser atualizado, corrigido ou substituído sem interromper o restante do sistema.
- Esta característica reduz significativamente os riscos de deploy e facilita a implementação de entregas contínuas.
- Favorece a evolução incremental da aplicação e permite uma rápida adaptação a mudanças de requisitos.
- O conceito central reside na autonomia dos serviços como um mecanismo para gerar agilidade organizacional.

### 2.2 Escalabilidade Granular
- Permite escalar apenas o serviço que apresenta maior demanda de recursos em um dado momento, evitando o desperdício de infraestrutura.
- Proporciona um ajuste fino de recursos por serviço:
  - CPU;
  - Memória;
  - Quantidade de réplicas.
- É o suporte ideal para cenários de negócios que possuem cargas de trabalho desbalanceadas entre as diferentes funcionalidades.
- Resulta em maior eficiência operacional e otimização do uso da infraestrutura.

### 2.3 Resiliência e Robustez
- As falhas permanecem isoladas ⟶ um serviço com problema técnico não compromete a integridade de todo o sistema.
- A arquitetura utiliza estratégias específicas para reforçar a resiliência:
  - Timeouts;
  - Retries;
  - Circuit breakers.
- Distribui os riscos de falhas e eleva a disponibilidade geral da plataforma.
- A tolerância a falhas é considerada uma propriedade estrutural inerente a este modelo arquitetural.

### 2.4 Automação e Observabilidade
- Apresenta uma forte dependência de processos de CI/CD, utilização de containers e orquestradores como o Kubernetes.
- A automação garante a consistência, a velocidade e a repetibilidade necessária para as entregas.
- A observabilidade integrada é essencial para entender o comportamento do sistema distribuído através de:
  - Logs;
  - Métricas;
  - Tracing distribuído.
- Estes elementos garantem a segurança e a previsibilidade em ambientes operacionais complexos.

> [!TIP] DICAS: 
> - Lembre-se que a principal diferença visual cobrada em provas entre Monólito e Microsserviços é a quantidade de bancos de dados: um no monólito e vários nos microsserviços.
> - A autonomia é o que permite que cada microsserviço seja escrito em uma linguagem de programação diferente, o que chamamos de poliglotismo tecnológico.

> [!CAUTION] OBSERVAÇÃO: 
> - Fique atento: embora os microsserviços aumentem a resiliência e a escalabilidade, eles também aumentam a complexidade operacional de rede e monitoramento.
> - O conceito de independência operacional é o que garante que o sistema não precise ser "derrubado" para que uma nova versão de uma pequena funcionalidade entre no ar.