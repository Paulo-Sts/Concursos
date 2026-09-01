# Itil 4 Práticas 7

## 1. Gerenciamento de Requisição de Serviço
- O propósito desta prática é apoiar a qualidade acordada de um serviço através do tratamento eficaz de solicitações pré-definidas e iniciadas pelo usuário.
- Requisição de serviço é uma solicitação que inicia uma ação de serviço acordada como parte normal da prestação de serviços.
- Qualquer serviço de TI pode ser requisitado via central de serviço e deve ser monitorado.
- Exemplos comuns incluem solicitações de usuários à central de serviços para ações padronizadas.

> [!CAUTION] OBSERVAÇÃO: 
> - Implantações de baixo risco (pré-autorizadas) não requerem uma requisição de serviço por parte do usuário para sua execução.

## 2. Validação e Teste de Serviço
- Esta prática visa garantir que produtos e serviços novos ou modificados atendam aos requisitos definidos pela organização.
- Foca no estabelecimento de critérios de aceitação para as práticas de implantação e gerenciamento de liberações.
- A verificação do cumprimento desses critérios é realizada obrigatoriamente por meio de testes.

### 2.1 Tipos de Testes no Gerenciamento de Serviços
- Os testes são divididos em categorias funcionais e não funcionais para cobrir utilidade e garantia.

| CATEGORIA | TIPOS DE TESTES |
|---|---|
| Testes de utilidade ou funcionais | Unitário, sistema, integração e regressão |
| Testes de garantia ou não funcionais | Desempenho, capacidade, segurança, conformidade e operacional |

> [!TIP] DICAS: 
> - O termo Shift Left refere-se à realização da validação do serviço nos estágios iniciais do ciclo de vida para confirmar se o design atende aos requisitos.

## 3. Gerenciamento de Implantação
- O propósito é mover componentes novos ou modificados (hardware, software, documentação ou processos) para ambientes de produção.
- Pode atuar também na movimentação de componentes para ambientes de testes ou homologação antes da liberação final.

### 3.1 Abordagens de Implantação
- Existem diferentes estratégias para realizar a movimentação de componentes para os ambientes ativos.

| ABORDAGEM | DEFINIÇÃO |
|---|---|
| Em fases (Phased Deployment) | Liberação gradual que utiliza feedbacks para diminuir riscos e impactos |
| Entrega contínua (Continuous Delivery) | Processo de disponibilização constante de componentes |
| Big bang | Implantação de todos os componentes de uma única vez, apresentando maior risco |
| Por pull (Pull Deployment) | Ação de implantação realizada por iniciativa do próprio usuário |

> [!CAUTION] OBSERVAÇÃO: 
> - O gerenciamento de implantação é classificado estritamente como uma prática de gerenciamento técnico.

## 4. Gerenciamento de Infraestrutura e Plataforma
- Esta prática supervisiona a infraestrutura e as plataformas tecnológicas utilizadas pela organização.
- Permite o monitoramento de tecnologias próprias ou de prestadores de serviços, incluindo soluções como chatbots e inteligência artificial.
- O escopo abrange sistemas operacionais, aplicativos de desktop e middleware.

### 4.1 Modelos de Computação em Nuvem
- A prática deve estar preparada para gerenciar os diferentes modelos de entrega e implantação de serviços em nuvem.

| TIPO DE MODELO | CLASSIFICAÇÕES |
|---|---|
| Modelos de serviço | SaaS (software), PaaS (plataforma) e IaaS (infraestrutura) |
| Modelos de implantação | Nuvem privada, pública, comunitária e híbrida |

> [!CAUTION] OBSERVAÇÃO: 
> - O gerenciamento de infraestrutura e plataforma é uma prática de gerenciamento técnico.

## 5. Desenvolvimento e Gerenciamento de Software
- O propósito é garantir que aplicativos atendam às necessidades das partes interessadas em funcionalidade, confiabilidade e conformidade.
- As duas abordagens principais aceitas são o método cascata (tradicional) e os métodos ágeis.
- O ciclo de vida de um serviço gerenciado nesta prática inclui diversas etapas ⟶ ideação, desenho, desenvolvimento, teste, entrega, operação e retirada.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora essencial para a entrega de serviços, esta é classificada como uma prática de gerenciamento técnico da ITIL 4.