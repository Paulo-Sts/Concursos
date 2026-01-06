# Computação em Nuvem

## 1. Definição (conforme NIST)
- Modelo que permite acesso ubíquo, conveniente e sob demanda a um pool compartilhado de recursos de computação configuráveis (ex: redes, servidores, armazenamento, aplicações).
- Os recursos podem ser provisionados e liberados com mínimo esforço de gestão.

## 2. Características Essenciais (NIST SP 800-145)
- Autosserviço sob demanda: o cliente pode provisionar recursos unilateralmente, sem interação humana com o provedor.
- Acesso amplo à rede: recursos acessíveis por rede via mecanismos padrão, de diversas plataformas (móveis, laptops, etc.).
- Pool de recursos (agrupamento): recursos multi-tenant, alocados dinamicamente. O cliente não conhece a localização exata.
- Rápida elasticidade: recursos podem ser alocados/liberados rapidamente, muitas vezes automaticamente, para escalar conforme demanda.
- Serviço medido: uso dos recursos é monitorado, controlado e reportado automaticamente (pay-per-use).

## 3. Modelos de Serviço (Modelos de Negócio)

#### 3.1 IaaS (Infrastructure as a Service)
- Fornece infraestrutura básica: processamento, armazenamento, redes.
- Cliente controla sistemas operacionais, aplicações e tem controle limitado sobre componentes de rede.
- Exemplos: AWS EC2, Google Compute Engine.

#### 3.2 PaaS (Platform as a Service)
- Fornece ambiente para desenvolvimento, teste e implantação de aplicações.
- Cliente controla as aplicações e configurações do ambiente de hospedagem.
- Não gerencia infraestrutura subjacente (rede, servidores, SO, armazenamento).
- Exemplos: Google App Engine, Microsoft Azure App Services.

#### 3.3 SaaS (Software as a Service)
- Fornece aplicações completas rodando na infraestrutura do provedor.
- Acessadas via navegador ou interface.
- Cliente não gerencia nada da infraestrutura, apenas usa o software.
- Exemplos: Google Workspace, Microsoft Office 365, Salesforce.

## 4. Outros Modelos de Serviço (XaaS)
- CaaS (Container as a Service): gerencia e implanta contêineres (ex: Docker).
- DaaS (Desktop as a Service): fornece desktops virtuais.
- DBaaS (Database as a Service): banco de dados gerenciado na nuvem.
- FaaS (Function as a Service) / Serverless: execução de funções sem gerenciar infraestrutura.
- BaaS (Backup as a Service): backup gerenciado na nuvem.
- SECaaS (Security as a Service): segurança gerenciada (firewall, antivírus).
- CaaS (Communication as a Service): soluções de comunicação (VoIP, videoconferência).

## 5. Benefícios da Computação em Nuvem
- Redução de custos: elimina investimento inicial alto em hardware/software; paga-se pelo uso.
- Escalabilidade: capacidade de aumentar/reduzir recursos conforme demanda.
- Elasticidade: ajuste automático e em tempo real dos recursos.
- Alta disponibilidade: dados replicados em múltiplos data centers.
- Flexibilidade e agilidade: provisionamento rápido de recursos.
- Produtividade: foco no negócio, não na infraestrutura.
- Confiabilidade e segurança: provedores usam infraestrutura de ponta e equipes especializadas.

## 6. Diferença entre Escalabilidade e Elasticidade
- Escalabilidade: capacidade do sistema de lidar com crescimento/redução de demanda, geralmente de forma planejada. Pode ser:
  - Horizontal: adicionar mais nós/servidores ao pool.
  - Vertical: aumentar capacidade de um nó/servidor existente (mais CPU, RAM).
- Elasticidade: capacidade de ajustar recursos automaticamente e em tempo real conforme flutuações de demanda. É dinâmica e automática.

## 7. Modelos de Implantação (não confundir com modelos de serviço)
- Nuvem pública: recursos compartilhados entre múltiplos clientes (multi-tenant). Ex: AWS, Azure, Google Cloud.
- Nuvem privada: infraestrutura exclusiva para uma organização.
- Nuvem híbrida: combinação de nuvens pública e privada, com orquestração entre elas.
- Nuvem comunitária: compartilhada por várias organizações com interesses comuns.

## 8. Observações para Provas
- Conhecer as 5 características essenciais do NIST.
- Diferenciar claramente IaaS, PaaS e SaaS (o que o cliente gerencia em cada).
- Não confundir escalabilidade (planejada) com elasticidade (automática e em tempo real).
- Identificar exemplos de cada modelo de serviço.
- Saber que multi-tenant é característica de nuvem pública/pool de recursos.
- Reconhecer outros modelos XaaS, especialmente CaaS, FaaS, SECaaS, BaaS.
- Em questões, "serviço medido" = medição automática do uso para cobrança.
- "Autosserviço sob demanda" = cliente provisiona recursos sozinho, sem contato com provedor.