# Microsoft SDL (Security Development Lifecycle)

## 1. Definição
- Processo de garantia de segurança focado no desenvolvimento e operação de software seguro.
- O SDL fornece requisitos de segurança detalhados e mensuráveis para desenvolvedores e engenheiros reduzirem o número e a gravidade das vulnerabilidades nos produtos e serviços da Microsoft.
- Incorpora:
  - Requisitos de segurança abrangentes;
  - Ferramentas específicas de tecnologias;
  - Processos obrigatórios no desenvolvimento e no funcionamento dos produtos. 

## 2. Governança e Arquitetura Zero Trust (Design and code ⟶ Build ⟶ Deploy ⟶ Run)
- Parte do pressuposto da confiança zero, onde todos precisam caminhar conforme os requisitos de segurança, tanto na arquitetura quanto na governança, sem depositar a confiança em outros.    
- Cada etapa do processo avalia os riscos associados ao seu término, para que possa seguir para a etapa seguinte.
- O gate (verificação entre etapas) apresentará uma lista de verificação que precisará ser conferida e aprovada antes de continuar para a etapa seguinte. 
- Exemplo: 
  - Para sair da etapa de design e codificação é preciso fazer análise estática do código;
  - Para entrar na construção é preciso realizar análise binária antes.
- Independentemente da forma como o usuário irá acessar o sistema, seja pela nuvem ou de forma instalada no computador do cliente, haverá um processo de execução monitorado.

## 3. Práticas
- Estabelecer padrões de segurança, métricas e governança.
- Exigir o uso de recursos, linguagens e frameworks de segurança comprovados.
- Realizar revisão de design de segurança e modelagem de ameaças.
- Definir e usar padrões de criptografia.
- Proteger a cadeia de suprimentos de software.
- Proteger o ambiente de engenharia.
- Realizar testes de segurança (SAST, DAST, SCA, entre outros).
- Garantir a segurança da plataforma operacional.
- Implementar monitoramento e resposta de segurança.
- Fornecer treinamento em segurança.

## 4. Componentes (Training ⟶ Requirements ⟶ Design ⟶ Implementacion ⟶ Verification ⟶ Release ⟶ Response)

### 4.1 Training
- Todos os funcionários da Microsoft são obrigados a concluir a formação geral de segurança e sensibilização para a privacidade, bem como formação específica relacionada com a sua função.
- A formação inicial é fornecida aos novos colaboradores após a contratação e é necessária formação anual de atualização em todo o seu emprego na Microsoft.
- Os programadores e engenheiros também devem participar na formação específica de funções para mantê-los informados sobre as noções básicas de segurança e tendências recentes no desenvolvimento seguro.
- Todos os funcionários como estagiários, funcionários contingentes, subcontratados e terceiros também são encorajados e fornecidos com a oportunidade de procurar formação avançada de segurança e privacidade.

### 4.2 Requeriments
- Cada produto, serviço e funcionalidade que a Microsoft desenvolve começa com requisitos de segurança e privacidade claramente definidos; são a base de aplicações seguras e
informam o seu design.
- As equipes de desenvolvimento definem estes requisitos com base em fatores como o tipo de dados que o produto irá processar, ameaças conhecidas, melhores práticas, regulamentos e requisitos do setor e lições aprendidas com incidentes anteriores. Uma vez definidos, os requisitos são claramente documentados e controlados.
- O desenvolvimento de software é um processo contínuo, o que significa que os requisitos de segurança e privacidade associados mudam ao longo do ciclo de vida do produto para
refletir as alterações na funcionalidade e no panorama das ameaças.

### 4.3 Design
- Em design será feita a modelagem de ameaça (threat modeling). Será definido o planejamento inicial, depois será feita a diagramação com o design para identificar e mitigar
as ameaças e, por último, validar o modelo.
- O modelo irá evitar que as ameaças passem pelo design do produto, do sistema.
- Ciclo: Definição ⟶ Diagramação ⟶ Identificação ⟶ Mitigação ⟶ Validação 

### 4.4 Implementation
- Fase em que será feita a codificação.
- A implementação começa com os programadores escrevendo o código de acordo com o plano que criaram nas duas fases anteriores.
- A Microsoft fornece aos programadores um conjunto de ferramentas de desenvolvimento seguras para implementar eficazmente todos os requisitos de segurança, privacidade e função do software que concebem.
- Estas ferramentas incluem compiladores, ambientes de desenvolvimento seguros e verificações de segurança incorporadas.

### 4.5 Verification
- Análise de código estático (SAST).
- Análise binária.
- Scanner de credenciais e segredos (verificar se no código fonte estão expostos segredos como senhas, urls, etc. Itens importantes que não podem ficar expostos para que não seja possível uma pessoa fazer a engenharia reversa utilizando as credenciais de acesso daquele programa).
- Análise de encriptação.
- Teste fuzz: Será exposto um sistema às entradas nos limites de buff para ver como o sistema se comporta.
- Validação da configuração.
- Governança de Componentes (CG), podendo utilizar SCA para verificar se os componentes são seguros.

### 4.6 Release
- Lançamento em anéis:
  - Cadência 0: A equipe de desenvolvimento responsável pelo serviço ou funcionalidade;
  - Anel 1: Todos os funcionários da Microsoft;
  - Anel 2: Usuários fora da Microsoft que tenham configurado a sua organização ou usuários específicos que estejam no canal de lançamento direcionado. Como se fosse um teste beta;
  - Anel 3: Lançamento padrão mundial em sub fases.

### 4.7 Response
- Todos os serviços Microsoft são amplamente registados e monitorados após o lançamento, identificando potenciais incidentes de segurança através de um sistema centralizado de monitoramento quase em tempo real.

> [!TIP] DICAS: 
> - O conserto de vulnerabilidades via DAST costuma ser mais caro do que as descobertas no início do ciclo de desenvolvimento.