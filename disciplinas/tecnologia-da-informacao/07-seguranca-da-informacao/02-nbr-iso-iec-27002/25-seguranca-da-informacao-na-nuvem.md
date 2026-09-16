# Segurança da Informação para Uso de Serviços em Nuvem (Controle 5.23)

## 1. Aspectos Gerais do Controle
- Trata-se de um controle preventivo.
- Propriedades de segurança da informação: confidencialidade, integridade e disponibilidade.
- Conceito de cibersegurança: proteger.
- Capacidade operacional: segurança nas relações com fornecedores.
- Domínios de segurança: governança, ecossistema e proteger.

## 2. Controle e Propósito

### 2.1 Controle
- Os processos de aquisição, uso, gestão e saída de serviços em nuvem devem ser estabelecidos de acordo com os requisitos de segurança da informação da organização.

### 2.2 Propósito
- Especificar e gerenciar a segurança da informação para o uso de serviços em nuvem.

## 3. Orientações para Implementação

### 3.1 Políticas e Comunicação
- A organização deve estabelecer e comunicar políticas específicas sobre o uso de serviços em nuvem para todas as partes interessadas.
- A organização deve definir e comunicar como pretende gerenciar riscos de segurança da informação associados ao uso de serviços em nuvem.
- Pode ser uma extensão da abordagem existente para serviços prestados por partes externas (ver controles 5.21 e 5.22).

### 3.2 Responsabilidade Compartilhada
- O uso de serviços em nuvem envolve responsabilidade compartilhada pela segurança da informação entre:
  - Provedor de serviços em nuvem;
  - Organização (cliente do serviço em nuvem).
- É essencial que as responsabilidades de ambas as partes sejam definidas e implementadas adequadamente.

> [!CAUTION] OBSERVAÇÃO: 
> - A responsabilidade não pode ser totalmente transferida ao cliente nem recair exclusivamente sobre o provedor.

### 3.3 O que a Organização Deve Definir
| ITEM | DESCRIÇÃO DA DEFINIÇÃO |
|---|---|
| A | Todos os requisitos relevantes de segurança da informação associados ao uso dos serviços em nuvem |
| B | Critérios de seleção de serviços em nuvem e escopo do uso |
| C | Papéis e responsabilidades relacionadas ao uso e gestão de serviços em nuvem |
| D | Quais controles de segurança são gerenciados pelo provedor e quais são gerenciados pela organização (cliente) |
| E | Como obter e utilizar recursos de segurança da informação fornecidos pelo provedor |
| F | Como obter garantia sobre controles de segurança implementados pelos provedores |
| G | Como gerenciar controles, interfaces e mudanças nos serviços quando a organização usa múltiplos serviços em nuvem (especialmente de diferentes provedores) |
| H | Procedimentos para tratamento de incidentes de segurança da informação relacionados ao uso de serviços em nuvem |
| I | Abordagem para monitorar, analisar criticamente e avaliar o uso contínuo de serviços em nuvem |
| J | Como alterar ou parar o uso de serviços em nuvem, incluindo estratégias de saída |

> [!TIP] DICAS: 
> - Interface é o meio pelo qual haverá interação dentro do provedor de serviços.
> - A estratégia de saída deve ser definida antes que as situações ocorram.

### 3.4 Análise Crítica de Contratos
- Os contratos de serviços em nuvem são muitas vezes predefinidos.
- A organização deve analisar criticamente os contratos com o provedor.
- Não se deve apenas aceitar o que for oferecido; é necessário observar se o que é oferecido está de acordo com a atividade da empresa.

> [!CAUTION] OBSERVAÇÃO: 
> - A norma recomenda análise crítica dos contratos, mesmo que sejam predefinidos.

### 3.5 Acordo de Serviço em Nuvem
- O acordo deve abordar os requisitos de confidencialidade, integridade, disponibilidade e manuseio de informações.
- Deve incluir objetivos apropriados de nível de serviço em nuvem e objetivos qualitativos de serviço em nuvem.

### 3.6 Avaliação de Riscos
- A organização deve realizar processos de avaliação de risco pertinentes para identificar riscos associados ao uso do serviço em nuvem.
- Quaisquer riscos residuais devem ser claramente identificados e aceitos pela gestão apropriada da organização.

> [!TIP] DICAS: 
> - O examinador elabora questões a partir dos itens estudados; recomenda-se a leitura repetida para fixação e memorização.

## 4. Disposições do Acordo entre Provedor e Cliente
| ITEM | DISPOSIÇÃO CONTRATUAL |
|---|---|
| A | Prover soluções baseadas em padrões aceitos de mercado para arquitetura e infraestrutura |
| B | Gerenciar controles de acesso dos serviços em nuvem que atendam aos requisitos da organização |
| C | Implementar soluções de monitoramento e proteção de malware |
| D | Tratar e armazenar informações sensíveis em locais aprovados (país ou região), dentro ou sujeito a jurisdição específica |
| E | Prover suporte dedicado em caso de incidente de segurança no ambiente do serviço em nuvem |
| F | Assegurar que os requisitos de segurança sejam atendidos caso os serviços sejam subcontratados (ou proibir a subcontratação) |
| G | Apoiar a organização na coleta de provas digitais, considerando leis e regulamentos para evidências digitais em diferentes jurisdições |
| H | Prover suporte e disponibilidade adequados dentro de prazo adequado, quando a organização quiser sair do serviço em nuvem |
| I | Prover o backup necessário de dados e informações de configuração, gerenciando-os com segurança |
| J | Fornecer e retornar informações como arquivos de configuração, código-fonte e dados que pertencem à organização, quando solicitado durante ou no término do serviço |

> [!TIP] DICAS: 
> - Malware = software malicioso.
> - Backup = cópia segura de dados.
> - Código-fonte = código dos programas.
> - Toda a arquitetura existente em nuvem deve ter o backup gerenciado.

## 5. Notificações sobre Mudanças
- A organização deve ser notificada pelo provedor sobre:
  - Alterações na infraestrutura técnica que afetam ou alteram a oferta do serviço em nuvem (ex.: realocação, reconfiguração ou alterações em hardware/software);
  - Tratamento ou armazenamento de informações em nova jurisdição geográfica ou legal;
  - Uso de provedores de serviços em nuvem por pares ou outros subcontratados (incluindo alterar partes existentes ou usar novas partes).