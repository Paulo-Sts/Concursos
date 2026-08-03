# Itil 4 Práticas 6

## 1. Central de Serviço
- O central de serviço deve atuar como um ponto de entrada único entre o provedor de serviços e o usuário.
- Representa o ponto de contato único para todos os usuários da organização.
- Propósito principal: capturar a demanda para resolução de incidentes e solicitações de serviço.
- Os usuários podem acessar a central por diversos meios de comunicação:
  - WhatsApp;
  - E-mail;
  - Telefone.
- O trabalho da central de serviço é pautado por procedimentos operacionais, não devendo atuar na arquitetura de soluções.
- A atuação baseia-se em scripts e bases de conhecimento que contêm problemas conhecidos para a resolução célere de incidentes.
- No fluxo de atendimento, o agente realiza a classificação inicial do incidente e pode indicar uma solução previamente definida.

### 1.1 Níveis de Atendimento e Tecnologia
- A prestação do serviço pode ocorrer em diferentes níveis de profundidade:
  - Primeiro nível ⟶ atendimento prestado de forma remota;
  - Segundo nível ⟶ atendimento prestado de forma presencial.
- A central utiliza diversas tecnologias para suportar suas atividades e aumentar a eficiência.

| TECNOLOGIA | FUNÇÃO NA CENTRAL |
|---|---|
| Sistemas inteligentes | Automação e suporte à decisão |
| Base de conhecimento | Consulta de procedimentos e erros conhecidos |
| Acesso remoto | Suporte técnico à distância |
| Monitoramento | Acompanhamento da saúde dos serviços |
| Gestão de força de trabalho | Planejamento de recursos e pessoal |
| Integração telefonia | Distribuição automática de chamados |

### 1.2 Melhoria e Cadeia de Valor
- Para lidar com aumentos de carga de trabalho e melhorar a eficiência, a central deve focar em automação e otimização.
- A implementação de automações para perguntas frequentes (FAQs) e categorias de problemas comuns alivia a carga da equipe e aumenta a satisfação do usuário.
- As etapas de triagem são fundamentais para compreender as causas dos incidentes antes do encaminhamento.
- Na cadeia de valor do serviço, a central de serviço não possui envolvimento com a atividade de planejar.

> [!TIP] DICAS: 
> - A central de serviço busca a solução de problemas da forma mais célere possível, focando no nível operacional e não no planejamento de longo prazo.

> [!CAUTION] OBSERVAÇÃO: 
> - A central de serviço é uma prática de gerenciamento de serviço, e não uma função isolada como em versões anteriores da ITIL.

## 2. Gerenciamento de Nível de Serviço
- O propósito desta prática é estabelecer metas claras para os níveis de serviço baseadas nos objetivos de negócio.
- Garante que a entrega dos serviços seja avaliada, monitorada e gerenciada em relação a essas metas.
- Nível de serviço é definido como uma ou mais métricas que determinam a qualidade de serviço esperada ou alcançada.

### 2.1 Acordo de Nível de Serviço e Operacional
- O Acordo de Nível de Serviço (SLA) é um contrato documentado entre o provedor e o cliente que identifica os serviços necessários e o nível esperado.
- O SLA deve ser alinhado e definido junto ao cliente final.
- Acordo de Nível Operacional (OLA) é o instrumento que garante, na prática, que os objetivos do SLA sejam cumpridos.

### 2.2 Utilidade e Garantia no Nível de Serviço
- O gerenciamento de nível de serviço deve equilibrar as expectativas do cliente quanto ao que o serviço entrega e como ele se comporta.
- A garantia assegura que um serviço atenda aos requisitos acordados de disponibilidade e desempenho.
- Estabelecer o SLA baseando-se estritamente em quesitos de negócios é a meta principal desta fase do projeto.

| CONCEITO | DEFINIÇÃO SIMPLIFICADA | FOCO |
|---|---|---|
| Utilidade | O que o serviço faz | Funcionalidade e adequação à finalidade |
| Garantia | Como o serviço se desempenha | Performance, comportamento e adequação ao uso |

> [!CAUTION] OBSERVAÇÃO: 
> - É comum em provas a troca de conceitos entre práticas. A definição de metas claras é responsabilidade do gerenciamento de nível de serviço, enquanto a identificação de riscos em novas versões é responsabilidade do gerenciamento de riscos.
> - A gestão de liberações não é responsável por gerenciar acordos de nível de serviço; essa é uma atribuição exclusiva da prática de gerenciamento de nível de serviço.