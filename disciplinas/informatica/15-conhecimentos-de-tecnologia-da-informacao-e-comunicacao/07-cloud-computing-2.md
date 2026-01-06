# Modelos de Implantação, Pagamento e Arquitetura de Nuvem

## 1. Modelos de Implantação (Nuvem)

#### 1.1 Nuvem Privada
- Infraestrutura provisionada para uso exclusivo de uma única organização.
- Pode ser gerenciada pela própria organização ou por terceiro.
- Pode estar localizada dentro (*on premises*) ou fora (*off premises*) da organização.
- Foco em segurança e controle; custo geralmente mais alto.

#### 1.2 Nuvem Pública
- Infraestrutura provisionada para uso aberto pelo público geral.
- Recursos compartilhados (modelo multi-tenant).
- Sempre gerenciada e operada por provedor externo (ex: AWS, Azure, Google Cloud).
- Existe apenas nas instalações do provedor.
- Maior escalabilidade e custo baseado no uso.

#### 1.3 Nuvem Comunitária
- Infraestrutura compartilhada por um grupo de organizações com interesses comuns (ex: missão, segurança, conformidade).
- Pode ser gerenciada por uma ou mais organizações da comunidade ou por terceiro.
- Pode ser *on premises* ou *off premises*.

#### 1.4 Nuvem Híbrida
- Combinação de duas ou mais nuvens (privada, pública, comunitária) que permanecem entidades separadas, mas interligadas.
- Permite portabilidade de dados e aplicações.
- Exemplo: *cloud bursting* (usar nuvem pública para picos de demanda).
- Dados sensíveis em nuvem privada; não sensíveis em nuvem pública.

## 2. Modelos de Pagamento

#### 2.1 Pay-As-You-Go (PAYG)
- Paga-se apenas pelos recursos consumidos (ex: CPU, armazenamento, banda).
- Máxima flexibilidade; custo variável.
- Comum em IaaS e PaaS.

#### 2.2 Assinatura/Tarifa Fixa
- Taxa fixa periódica (mensal/anual).
- Comum em SaaS.

#### 2.3 Modelo Gratuito com Limites
- Camada básica gratuita com limites.
- Upgrade para plano pago além do limite.

#### 2.4 Licenciamento Baseado em Usuário
- Preço baseado no número de usuários com acesso.
- Comum em software empresarial (SaaS).

#### 2.5 Reserva de Recursos
- Reserva de recursos com antecedência (planejamento).
- Geralmente mais barato que PAYG.
- Adequado para cargas previsíveis.

## 3. Componentes da Arquitetura em Nuvem

#### 3.1 Região
- Área geográfica onde um provedor mantém infraestrutura (ex: São Paulo, Frankfurt).
- Fatores de escolha: proximidade do usuário (latência), conformidade legal (ex: LGPD), custo, disponibilidade de serviços.

#### 3.2 Zonas de Disponibilidade (AZ)
- Conjunto de data centers isolados dentro de uma região.
- Possuem alimentação, refrigeração e rede independentes.
- Objetivo: tolerância a falhas e alta disponibilidade.
- Se uma AZ falha, outras continuam operando.

#### 3.3 Data Center
- Instalação física com servidores, armazenamento, rede, refrigeração, energia redundante, segurança física e cibernética.

#### 3.4 Camadas da Arquitetura
- Front-end: interface do usuário (portais, dashboards).
- Back-end: servidores, armazenamento, redes, balanceamento de carga, bancos de dados.
- Camada de virtualização: hipervisores (máquinas virtuais) e contêineres.
- Camada de gerenciamento: automação, orquestração, monitoramento, segurança.
- Camada de serviço: entrega dos serviços (IaaS, PaaS, SaaS).

## 4. Observações para Provas
- Diferenciar modelos de implantação (pública, privada, híbrida, comunitária) de modelos de serviço (IaaS, PaaS, SaaS).
- Nuvem privada pode ser gerenciada por terceiro; não precisa estar dentro da organização.
- Nuvem pública é sempre multi-tenant e gerenciada pelo provedor.
- Nuvem híbrida requer interoperabilidade entre nuvens distintas.
- PAYG é o modelo de pagamento mais comum, especialmente para IaaS.
- Regiões são escolhidas por fatores como latência, conformidade e custo.
- Zonas de disponibilidade oferecem isolamento de falhas dentro de uma região.
- Data centers são a infraestrutura física; AZs são conjuntos logicamente isolados de data centers.
- Front-end é a interface do usuário; back-end contém a infraestrutura e lógica de gerenciamento.