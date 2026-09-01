# Rancher e Gerenciamento de Kubernetes

## 1. Introdução e Propósito
- O Rancher é uma ferramenta de gerenciamento de Kubernetes projetada para implantar e executar clusters em qualquer provedor de nuvem ou infraestrutura local.
- A plataforma centraliza a autenticação e o controle de acesso baseado em funções (rbac) para todos os clusters gerenciados.
- Permite que administradores globais controlem o acesso aos recursos a partir de um único local centralizado.
- Fornece uma interface de usuário intuitiva para que engenheiros de devops gerenciem suas cargas de trabalho.

### 1.1 Problemas Solucionados pelo Rancher
- Gestão fragmentada ⟶ elimina a necessidade de usar ferramentas diferentes para gerenciar clusters em nuvens distintas.
- Falta de consistência ⟶ resolve dificuldades na gestão de múltiplos ambientes através de uma visão unificada.
- Monitoramento ⟶ cria uma visão centralizada do estado de saúde dos clusters e das aplicações.

## 2. Arquitetura e Componentes Técnicos
- O Rancher API Server detém a totalidade dos comandos que podem ser utilizados dentro da plataforma.
- O gerenciamento de usuários suporta provedores de autenticação externos, como Active Directory ou GitHub.
- A gestão de projetos permite agrupar múltiplos namespaces e aplicar políticas de controle de acesso de forma coletiva.
- A entrega contínua é realizada via Fleet, que automatiza a implantação de aplicações a partir de repositórios git.
- A ferramenta integra o Istio como malha de serviços (service mesh) para conectar e proteger microsserviços de forma integrada.

### 2.1 Visibilidade e Infraestrutura
- O rastreamento de nós permite o provisionamento dinâmico de novos nós e armazenamento persistente na nuvem.
- A visibilidade do cluster inclui o registro de logs e integração com ferramentas populares.
- O monitoramento do estado dos processos e componentes do Kubernetes é realizado através da integração com o Prometheus.

## 3. Conceitos Fundamentais da Plataforma
| COMPONENTE | DESCRIÇÃO |
|---|---|
| AMBIENTE | Espaço lógico que agrupa hosts, stacks, serviços, contêineres e volumes |
| STACK | Grupo de serviços inter-relacionados gerenciados como uma única unidade |
| CONTÊINER | Unidade de execução de aplicações que encapsula dependências em ambiente isolado |
| HOST | Máquina física ou virtual onde os contêineres são efetivamente executados |
| NAMESPACE | Divisão virtual de um cluster para organizar recursos de forma isolada |
| PROJETO | Entidade que agrupa múltiplos namespaces dentro de um cluster kubernetes |

- O ambiente pode possuir sua própria configuração de rede, segurança e políticas de acesso.
- As stacks podem ser definidas através de templates, como os fornecidos por Helm Charts, para garantir implantações consistentes.
- O host representa a infraestrutura subjacente para as operações do Kubernetes e Docker dentro do ambiente.

> [!CAUTION] OBSERVAÇÃO: 
> - O conceito de Projeto é uma exclusividade do Rancher e não existe nativamente dentro do Kubernetes.

## 4. Comandos e Interface de Linha de Comando
- O Rancher CLI permite interagir com a plataforma e gerenciar os recursos através de comandos de texto.
- A listagem de recursos utiliza os seguintes padrões:
  - ps: exibe os serviços com nomes, imagens, estado e nível de escala;
  - ps -c: lista especificamente os contêineres que estão rodando no ambiente;
  - hosts: exibe os ativos e máquinas vinculadas ao gerenciador.

### 4.1 Principais Instruções Operacionais
- O gerenciamento do ciclo de vida dos recursos utiliza comandos padronizados:
  - Start ou activate: utilizado para iniciar ou ativar serviços, contêineres ou hosts;
  - Stop ou deactivate: interrompe ou desativa a execução dos recursos selecionados;
  - Inspect: exibe detalhes técnicos profundos de serviços, volumes ou ambientes;
  - Scale: define a quantidade de contêineres que devem ser executados para um determinado serviço.

## 5. Infraestrutura para Alta Disponibilidade
- O K3s consiste em uma variação leve e altamente disponível do Kubernetes utilizada em contextos específicos.
- A instalação recomendada do Rancher em um cluster K3s de alta disponibilidade exige:
  - Dois nós Linux, geralmente configurados como máquinas virtuais;
  - Um banco de dados externo do tipo relacional, com recomendação de uso do MySQL;
  - Um balanceador de carga para direcionar o tráfego entre os nós da infraestrutura;
  - Um registro de DNS para mapear a URL de acesso ao servidor.

> [!TIP] DICAS: 
> - Em questões de prova, o comando correto para listar templates de catálogo via CLI é rancher catalog ls.
> - Embora seja uma ferramenta de nicho, o Rancher está ganhando relevância crescente em concursos da área de tecnologia da informação.