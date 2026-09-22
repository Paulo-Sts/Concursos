# Harbor e Gerenciamento de Imagens de Contêiner

## 1. Conceito e Finalidade do Harbor
- O Harbor é uma ferramenta de código aberto utilizada para o armazenamento e o gerenciamento seguro de imagens de contêineres.
- Atua como um registro (registry) que permite organizar os binários e as dependências das aplicações de forma escalável.
- Funciona como uma alternativa ao Docker Hub e a outros registros privados, sendo amplamente adotado em órgãos públicos e grandes organizações.
- Diferencia-se de orquestradores como o Kubernetes, focando estritamente na custódia e na integridade das imagens antes da sua execução.

### 1.1 Casos de Uso e Aplicações
- Empresas que necessitam de um repositório privado para garantir a segurança e a soberania de suas imagens;
- Equipes de devops que buscam soluções self-hosted para reduzir custos operacionais com serviços pagos de terceiros;
- Ambientes de orquestração que exigem integração nativa com helm charts e ferramentas de assinatura digital;
- Organizações que demandam auditoria rigorosa e conformidade no gerenciamento do ciclo de vida das aplicações conteinerizadas.

### 1.2 Principais Recursos e Características
- Registro privado e seguro que elimina a dependência exclusiva de registros públicos como o Docker Hub;
- Controle de acesso baseado em funções (rbac) para a definição granular de permissões por usuários ou grupos;
- Replicação entre registros para garantir a sincronização automática e a alta disponibilidade dos ativos em diferentes locais;
- Suporte a multi-inquilino (multi-tenant) e interface de usuário baseada em web ou interface de programação de aplicativos extensível.

> [!TIP] DICAS: 
> - O Harbor é uma solução de registro self-hosted que foca na segurança da informação e na governança antes do lançamento dos contêineres ⟶ essencial para ambientes corporativos e governamentais.

## 2. Segurança e Integridade
- O Harbor implementa múltiplas camadas de proteção para garantir a confiabilidade dos artefatos de software.
- O escaneamento de vulnerabilidades é realizado através da integração com ferramentas externas consagradas como Trivy e Clair.
- A assinatura de imagens, utilizando o componente Notary, garante a autenticidade e a integridade do conteúdo armazenado.
- O sistema realiza a validação de conteúdo para assegurar que as imagens não foram alteradas por terceiros não autorizados durante o armazenamento.

## 3. Arquitetura e Componentes Internos
- A estrutura do Harbor é composta por diversos serviços que interagem para prover um ecossistema de registro confiável.
- Os consumidores do sistema são divididos entre usuários humanos, que acessam via interface gráfica ou api, e orquestradores de contêineres que buscam as imagens.
- O roteamento de api é o componente responsável por gerenciar e encaminhar solicitações de upload, download e tarefas de automação.
- O Job Service executa tarefas assíncronas essenciais para a manutenção, como a limpeza de registros antigos e a replicação de dados entre instâncias.

### 3.1 Comparação entre Harbor e Docker Hub
| CARACTERÍSTICA | HARBOR | DOCKER HUB |
|---|---|---|
| Registro privado | Sim (gratuito) | Apenas em contas pagas |
| Escaneamento de vulnerabilidades | Sim (detalhado via trivy e clair) | Sim (mas limitado na versão gratuita) |
| Controle de acesso (rbac) | Sim (controle detalhado por funções) | Não possui rbac nativo |
| Replicação entre registros | Sim (sincronização automática) | Não disponível |
| Assinatura de imagens | Sim (via notary) | Não disponível |
| Integração com kubernetes | Sim | Sim |

> [!CAUTION] OBSERVAÇÃO: 
> - O Harbor não realiza a orquestração de contêineres nem o monitoramento de métricas de hardware como cpu ou memória das aplicações em execução.
> - Diferente do que algumas pegadinhas de prova sugerem, as imagens não são armazenadas exclusivamente em bancos de dados sql.
> - O Pod Scheduler e o Load Balancer Service não são componentes internos do Harbor, mas sim funções desempenhadas por orquestradores como o Kubernetes.