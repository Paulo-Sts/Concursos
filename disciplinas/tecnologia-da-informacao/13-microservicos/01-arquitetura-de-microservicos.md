# Arquitetura de Microserviços

## 1. Conceito fundamental

### 1.1 Definição de Microserviços
- Organiza uma aplicação como um conjunto de serviços pequenos, independentes e especializados, cada um responsável por uma função específica do negócio.
- Diferentemente da arquitetura monolítica, os microserviços são desenvolvidos, implantados e escalados de forma autônoma.

> [!TIP] DICAS: 
> Pense em microserviços como "pequenos sistemas" que conversam entre si para formar uma aplicação completa.

## 2. Características Principais dos Microserviços

### 2.1 Independência Operacional
- Cada microserviço pode ser atualizado, corrigido ou substituído sem interromper o restante do sistema.
- Essa independência reduz riscos de *deploy* e facilita entregas contínuas.
- A arquitetura favorece evolução incremental e rápida adaptação a mudanças.
- Conceito central: autonomia como mecanismo de agilidade.

> [!TIP] DICAS: 
> A independência operacional é o que permite times diferentes trabalharem em serviços distintos sem conflitos.

### 2.2 Escalabilidade Granular
- A arquitetura permite escalar apenas o serviço que demanda mais recursos, evitando desperdício.
- Escalabilidade fina: CPU, memória e réplicas ajustadas por serviço.
- Suporte ideal para cenários com cargas desbalanceadas entre funcionalidades.
- Resultado: eficiência operacional e melhor uso da infraestrutura.

> [!CAUTION] OBSERVAÇÃO: 
> Na arquitetura monolítica, escala-se a aplicação inteira. Em microserviços, escala-se apenas o serviço necessário.

### 2.3 Resiliência e Robustez
- Falhas ficam isoladas: um serviço com problema não compromete todo o sistema.
- Estratégias como *timeouts*, *retries* e *circuit breakers* reforçam a resiliência.
- A arquitetura distribui riscos e aumenta a disponibilidade geral.
- Conceito-chave: tolerância a falhas como propriedade estrutural.

> [!CAUTION] OBSERVAÇÃO: 
> Se um microsserviço cair, os demais continuam funcionando. Isso é uma das grandes vantagens sobre o monolito.

### 2.4 Automação e Observabilidade
- Forte dependência de CI/CD, *containers* e orquestração (como Kubernetes).
- Automação garante consistência, velocidade e repetibilidade nas entregas.
- Observabilidade integrada: *logs*, métricas e *tracing* distribuído permitem entender o comportamento do sistema.
- Essencial para operar ambientes distribuídos com segurança e previsibilidade.

> [!TIP] DICAS: 
> *Tracing* distribuído é uma técnica para rastrear requisições que passam por múltiplos microsserviços.

## 3. Comparação: Microserviços x SOA

| CARACTERÍSTICA | MICROSSERVIÇOS | SOA |
|----------------|----------------|-----|
| Tamanho dos serviços | Pequenos e focados em uma função específica | Grandes e orientados a processos de negócio |
| Compartilhamento | Evita compartilhamento de código e banco | Compartilha banco e componentes via ESB |
| Comunicação | Leve (HTTP/REST, mensageria) | Frequentemente usa ESB (*Enterprise Service Bus*) |
| Governança | Descentralizada (cada time decide) | Centralizada |
| Implantação | Independente por serviço | Geralmente integrada |

> [!CAUTION] OBSERVAÇÃO: 
> SOA e microserviços não são a mesma coisa. O principal diferencial é que microserviços têm independência total e comunicação mais leve, enquanto SOA costuma depender de um barramento (*ESB*).

## 4. Quadro-resumo das Características

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Independência operacional | Serviços atualizados sem afetar os demais |
| Escalabilidade granular | Escala apenas o serviço necessário |
| Resiliência e robustez | Falhas ficam isoladas e não derrubam o todo |
| Automação e observabilidade | CI/CD, containers, *logs*, métricas e *tracing* |