# Arquitetura e Componentes do Kubernetes 2

## 1. Estrutura do Cluster
- Um cluster do Kubernetes consiste em um conjunto de máquinas, denominadas nós, que executam aplicações em contêineres.
- As máquinas que compõem o cluster podem ser de natureza física, virtual ou baseadas em nuvem.
- A organização do sistema fundamenta-se na distinção entre o Master node e os Worker nodes.

### 1.1 Master Node ou Control Plane
- O Master node atua como o centro de gerenciamento e controle para todo o cluster.
- Sua responsabilidade principal é gerenciar os componentes e assegurar que o cluster opere conforme o estado almejado da aplicação.
- A estrutura do Control Plane é composta por quatro elementos essenciais:
  - API Server;
  - Scheduler;
  - Controller Manager;
  - etcd.

### 1.2 Worker Nodes
- Os Worker nodes representam as máquinas de trabalho que realizam a execução efetiva dos contêineres.
- Cada nó de trabalho possui componentes destinados a assegurar que os contêineres operem adequadamente dentro de um pod.
- A coordenação entre o Master node e o Worker node é realizada através da troca de mensagens pela API.

## 2. Componentes da Camada de Gerenciamento
- Os módulos internos do Control Plane interagem para manter a orquestração do ambiente:
  - API Server: funciona como o ponto de entrada para as APIs do cluster, sendo responsável por processar e validar as solicitações;
  - Scheduler: observa os pods recém-criados e os distribui entre os nós trabalhadores disponíveis conforme as necessidades de consumo e configurações definidas;
  - Controller Manager: atua como o gerente geral do cluster, realizando o monitoramento e a manutenção do estado desejado;
  - etcd: repositório de dados do tipo chave-valor, caracterizado pela consistência e alta disponibilidade, que armazena as configurações e o estado geral do sistema.

## 3. Componentes do Nó de Trabalho
- A execução e a conectividade nos nós dependem de agentes específicos:
  - Kubelet: agente executado em cada nó do cluster que se comunica com o API Server e garante a execução dos contêineres em um pod;
  - Kube-proxy: componente responsável por cuidar da rede e do roteamento para os contêineres;
  - Docker: ferramenta utilizada em cada máquina para criar e gerenciar fisicamente os contêineres sob supervisão do kubelet.

## 4. Unidades de Trabalho e Implantação
- O pod é a menor unidade básica de implantação com a qual o Kubernetes trabalha.
- Pode ser compreendido como uma cápsula que agrupa um ou mais contêineres em um único nó.

### Tabela de Atribuições
| COMPONENTE | FUNÇÃO PRINCIPAL | LOCALIZAÇÃO |
|---|---|---|
| API SERVER | Entrada e validação de requisições | Master node |
| SCHEDULER | Alocação de pods em nós disponíveis | Master node |
| CONTROLLER MANAGER | Manutenção do estado do cluster | Master node |
| ETCD | Armazenamento de configurações | Master node |
| KUBELET | Gestão de containers no nó | Worker node |
| KUBE-PROXY | Roteamento de tráfego de rede | Worker node |

> [!TIP] DICAS: 
> - Pense na hierarquia de envio: Master node (decisão) ⟶ Worker node (execução).

> [!CAUTION] OBSERVAÇÃO: 
> - O etcd é um banco de dados chave-valor e não um banco de dados relacional comum.
> - O termo Control Plane refere-se ao conjunto de componentes que gerenciam o cluster, enquanto Worker node refere-se às máquinas que executam a carga de trabalho.
> - Uma pegadinha comum de prova é afirmar que o kubelet faz a distribuição dos pods; na verdade, quem distribui é o scheduler, enquanto o kubelet garante a execução no nó.