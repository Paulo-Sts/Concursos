# Kubernetes 3

## 1. Workloads e Cargas de Trabalho
- As cargas de trabalho, denominadas workloads, representam as diferentes formas de executar e gerenciar aplicações dentro do cluster.
- Existem diversas categorias de objetos que organizam a execução dos contêineres de acordo com a necessidade de disponibilidade e persistência.
- O sistema permite a configuração de objetos que automatizam a substituição, o escalonamento e a atualização de instâncias de software.

### 1.1 Pods
- O pod consiste na menor unidade de implantação e computação gerenciável dentro do ecossistema Kubernetes.
- Representa um conjunto de um ou mais contêineres que são tratados como uma única unidade operacional e lógica.
- Os contêineres pertencentes ao mesmo pod compartilham obrigatoriamente os recursos de armazenamento e a infraestrutura de rede.
- Cada pod recebe um endereço ip único dentro do cluster, o qual é compartilhado por todos os contêineres internos daquela unidade.
- Possuem natureza efêmera, significando que podem ser destruídos e substituídos por novas instâncias automaticamente se falharem ou forem removidos.

> [!TIP] DICAS: 
> - Em provas de concurso, memorize que o Pod é a menor unidade que pode ser escalada horizontalmente para aumentar a redundância.

### 1.2 ReplicaSet e Deployment
- O ReplicaSet tem a função de assegurar que um número especificado de réplicas de um pod esteja em execução em qualquer momento.
- Atua na substituição automática de pods falhos ou mortos para manter a resiliência e a quantidade desejada de instâncias.
- O Deployment fornece uma maneira declarativa de gerenciar aplicações, coordenando a criação e a atualização de ReplicaSets e pods.
- Facilita a execução de operações críticas como atualizações contínuas (rolling updates) e reversões de versão (rollbacks).
- Permite que novas versões de aplicativos sejam implantadas sem a necessidade de tempo de inatividade significativo para o serviço.

### 1.3 StatefulSet e DaemonSet
- O StatefulSet é utilizado para gerenciar aplicações que exigem persistência de dados e uma ordenação de estado específica.
- Garante que os pods mantenham identificadores estáveis ao longo do tempo e sejam criados ou destruídos em uma ordem predefinida.
- É o objeto ideal para a execução de bancos de dados e sistemas de cache distribuído no cluster.
- O DaemonSet assegura que uma cópia de um pod específico seja executada em todos os nós do cluster, ou em nós selecionados.
- Sua aplicação típica envolve o monitoramento de nós, a coleta de logs do sistema e a execução de agentes de rede.

### 1.4 Job e CronJob
- O Job cria pods com a finalidade de executar tarefas específicas que devem ser processadas até a conclusão com sucesso.
- Garante que um número determinado de pods termine suas funções antes de encerrar a carga de trabalho.
- É indicado para trabalhos realizados em lote e tarefas que possuem curta duração.
- O CronJob permite realizar o agendamento de Jobs para que sejam executados periodicamente conforme um cronograma.
- Utilizado para automatizar tarefas recorrentes como a geração de relatórios, execução de backups e manutenção de sistemas.

### 1.5 Comparativo de Objetos Workload
| WORKLOAD | CARACTERÍSTICA PRINCIPAL | FINALIDADE TÍPICA |
|---|---|---|
| POD | Unidade básica de execução | Encapsular containers |
| REPLICASET | Garantia de quantidade | Manter réplicas ativas |
| DEPLOYMENT | Gestão declarativa | Atualizações e rollbacks |
| STATEFULSET | Persistência e ordem | Bancos de dados |
| DAEMONSET | Execução em cada nó | Logs e monitoramento |
| JOB | Execução de tarefa única | Processamento em lote |
| CRONJOB | Execução agendada | Backups e rotinas |

> [!CAUTION] OBSERVAÇÃO: 
> - Um pod sempre será executado em um único nó, independentemente de ser uma máquina física ou virtual, não podendo ser fragmentado entre múltiplos nós ⟶ cada contêiner interno rodará no mesmo host.
> - Embora o pod contenha contêineres, ele é considerado a unidade mínima, e não o contêiner isoladamente.
> - A responsabilidade de criar e atualizar instâncias de um aplicativo conteinerizado recai sobre o objeto Deployment.