# Computação em Nuvem e AWS

## 1. Infraestrutura como Código (IaC)
- Transforma infraestrutura em código, permitindo gerenciamento automatizado e consistente.
- Usa arquivos de configuração que podem ser executados em qualquer provedor de nuvem.
- Princípios:
  - Automatização
  - Consistência e padronização
  - Controle de versão
  - Documentação viva
  - Reutilização e compartilhamento
- Benefícios:
  - Eficiência operacional
  - Redução de erros
  - Rapidez na implantação
  - Escalabilidade automática
  - Recuperação de desastres
  - Melhoria no monitoramento

## 2. Aplicações Nativas em Nuvem
- Aplicações desenvolvidas especificamente para a nuvem.
- Características:
  - Projetadas para aproveitar as vantagens da computação em nuvem
  - Arquitetura baseada em microsserviços e contêineres
  - Serviços com baixo acoplamento e independentes
  - Adoção de práticas DevOps
  - Stateless (não guardam estado)
  - API-First (acessadas via API)

## 3. Modelo Serverless (FaaS e BaaS)

#### 3.1 Function as a Service (FaaS)
- Modelo de execução orientado a eventos.
- Desenvolvedor escreve funções que são executadas sob demanda.
- Não há gerenciamento de servidores.
- Contêineres efêmeros, sem estado, acionados por eventos.
- Pagamento baseado no consumo.

#### 3.2 Backend as a Service (BaaS)
- Oferece serviços de back-end pré-configurados.
- Desenvolvedor foca no front-end.
- Exemplos de serviços:
  - Autenticação de usuários
  - Bancos de dados
  - Notificações push
  - Armazenamento de arquivos

#### 3.3 Vantagens do Serverless
- Aumento da produtividade dos desenvolvedores
- Redução de custos operacionais
- Gerenciamento simplificado de infraestrutura
- Escalabilidade automática
- Alta disponibilidade

#### 3.4 Desvantagens do Serverless
- Limitações de tempo de execução
- Cold starts (início mais lento na primeira execução)
- Baixa flexibilidade e personalização
- Dependência do fornecedor
- Custos de migração entre provedores

## 4. Bancos de Dados em Nuvem
- Banco de dados implantado, entregue e acessado na nuvem.
- Oferecido como DBaaS (Database as a Service).
- Tipos:
  - Relacionais (SQL Server, Oracle, MySQL, PostgreSQL)
  - Não relacionais (MongoDB, Redis, Cassandra)

#### 4.1 Modelos de Gerenciamento
- Autogerenciado: organização gerencia o banco na infraestrutura da nuvem.
- Automatizado: usa APIs para operações, mas mantém controle sobre servidores.
- Gerenciado: provedor gerencia provisionamento, escalabilidade, backup e segurança.
- Autônomo: usa automação e machine learning para gerenciamento "hands-free".

#### 4.2 Vantagens
- Redução de custos operacionais e TCO
- Agilidade e escalabilidade melhoradas
- Segurança dos dados
- Confiabilidade (SLAs)
- Acesso global e colaboração

#### 4.3 Desvantagens
- Dependência do fornecedor
- Dificuldade de integração com outros sistemas
- Migrações complexas e demoradas
- Possibilidade de subestimar custos
- Riscos de segurança na nuvem

## 5. Principais Serviços AWS

#### 5.1 Analytics
- Amazon Athena: consulta interativa em dados no S3 usando SQL.
- Amazon Redshift: data warehouse gerenciado para análise em larga escala.
- Amazon EMR: processamento de grandes volumes de dados com Hadoop.
- AWS Glue: serviço de ETL gerenciado.
- Amazon Kinesis: processamento e análise de dados em tempo real.

#### 5.2 Application Integration
- Amazon SQS: serviço de fila para troca assíncrona de mensagens.
- Amazon SNS: serviço de notificação push.
- AWS Step Functions: orquestração de fluxos de trabalho.
- Amazon EventBridge: roteamento de eventos em tempo real.

#### 5.3 Compute
- Amazon EC2: servidores virtuais escaláveis.
- AWS Lambda: execução de código sem servidor (FaaS).
- AWS Elastic Beanstalk: implantação e escalonamento automático de aplicações web.

#### 5.4 Containers
- Amazon ECS: orquestração de contêineres Docker gerenciada.
- Amazon EKS: serviço gerenciado de Kubernetes.
- AWS Fargate: execução de contêineres sem gerenciamento de servidores.
- Amazon ECR: repositório de imagens de contêineres.

#### 5.5 Database
- Amazon RDS: banco de dados relacional gerenciado.
- Amazon DynamoDB: banco de dados NoSQL gerenciado.
- Amazon Aurora: banco de dados relacional otimizado.
- Amazon DocumentDB: compatível com MongoDB.
- Amazon Neptune: banco de dados de grafos.

#### 5.6 Storage
- Amazon S3: armazenamento de objetos escalável.
- Amazon EBS: armazenamento em blocos para instâncias EC2.
- Amazon EFS: armazenamento de arquivos gerenciado.
- Amazon S3 Glacier: armazenamento de arquivamento de baixo custo.

#### 5.7 Security
- AWS IAM: gerenciamento de identidades e acessos.
- AWS KMS: gerenciamento de chaves de criptografia.
- Amazon GuardDuty: detecção de ameaças.
- AWS WAF: firewall de aplicação web.
- Amazon Macie: proteção de dados sensíveis.

#### 5.8 Management & Governance
- AWS CloudFormation: infraestrutura como código (IaC).
- AWS CloudTrail: auditoria de atividades da API.
- AWS Config: rastreamento de configurações de recursos.
- AWS Systems Manager: automação e manutenção de infraestrutura.

## 6. Conceitos Importantes
- Microsserviços: serviços pequenos, independentes e bem definidos.
- Contêineres: ambientes leves e isolados para execução de aplicações.
- Escalabilidade: capacidade de ajustar recursos conforme a demanda.
- Pay-as-you-go: modelo de pagamento baseado no consumo.
- Alta disponibilidade: garantia de funcionamento contínuo do serviço.
- Recuperação de desastres: capacidade de restaurar operações após falhas.