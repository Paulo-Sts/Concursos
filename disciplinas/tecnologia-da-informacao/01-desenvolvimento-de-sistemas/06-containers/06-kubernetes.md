# Kubernetes

## 1. Introdução ao Kubernetes
- O Kubernetes é uma plataforma de código aberto, portável e extensiva voltada para o gerenciamento de cargas de trabalho e serviços distribuídos em contêineres.
- Sua principal função consiste na automatização da gestão de contêineres, incluindo a atualização de versões de aplicativos e a substituição automática de instâncias antigas por novas.
- A ferramenta foi originalmente desenvolvida pelo Google e atualmente é mantida pela Cloud Native Computing Foundation.
- O sistema facilita tanto a configuração declarativa quanto a automação de processos em larga escala.

### 1.1 Portabilidade e Ambientes
- A solução apresenta alta portabilidade, podendo ser executada em diversos cenários operacionais:
  - Ambientes on-premise;
  - Nuvem pública (GCP, AWS);
  - Ambientes híbridos;
  - Laptops pessoais.

> [!TIP] DICAS: 
> - O Kubernetes foca na orquestração e escalabilidade, enquanto o Docker foca na criação e manipulação das imagens.

## 2. Recursos e Funcionalidades Principais
- A orquestração realizada pela plataforma abrange diversos aspectos críticos da infraestrutura:
  - Descoberta de serviço e balanceamento de carga;
  - Lançamentos e reversões automatizadas em caso de falhas;
  - Autocorreção ou autocura para recuperação de falhas sem interferência externa;
  - Gerenciamento de segredos e configurações.

### 2.1 Orquestração de Armazenamento
- O Kubernetes permite a montagem automática de sistemas de armazenamento de escolha do usuário.
- O suporte inclui diferentes modalidades de persistência de dados:
  - Armazenamento local;
  - Provedores de nuvem pública;
  - Armazenamento de rede como NFS, iSCSI, Gluster, Ceph ou Cinder.

### 2.2 Gerenciamento de Segredos e Configurações
- A plataforma facilita a criação e atualização de Secrets e configurações da aplicação.
- O gerenciamento ocorre sem a necessidade de reconstruir a imagem do contêiner e sem expor credenciais na configuração da aplicação.

## 3. Unidades de Trabalho e Conceitos Estruturais
- O pod representa a menor unidade de trabalho dentro do ecossistema do Kubernetes.
- Um pod é composto por um ou mais contêineres que funcionam de forma conjunta.
- Os contêineres dentro de um mesmo pod compartilham os recursos de rede e o mesmo endereço IP.

| COMPONENTE | DESCRIÇÃO |
|---|---|
| POD | Menor unidade composta por um ou mais contêineres |
| NAMESPACE | Divisão virtual de um cluster para organizar recursos |
| TELEMETRIA | Medição de desempenho e atividades para monitoramento |
| SECRETS | Dados sensíveis de autenticação mantidos criptografados |

> [!CAUTION] OBSERVAÇÃO: 
> - O Kubernetes pode operar sem a utilização do Docker, suportando outros motores de execução como o CRIO e o Containerd.

## 4. Integração com DevOps e Fluxos de Implantação
- A ferramenta oferece suporte às equipes de DevOps através da automação da implantação e do gerenciamento.
- A integração com fluxos de CI/CD permite o lançamento contínuo de novas versões e o dimensionamento automático dos serviços.
- O uso de contêineres resolve conflitos entre equipes de desenvolvimento e operação ao garantir que o mesmo ambiente seja utilizado em todas as etapas ⟶ desenvolvimento, homologação e produção.