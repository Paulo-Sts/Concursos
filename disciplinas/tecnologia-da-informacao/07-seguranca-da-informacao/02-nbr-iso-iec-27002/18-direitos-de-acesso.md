# ISO/IEC 27002:2022 - Direitos de Acesso

## 1. Definição
- Os direitos de acesso às informações e outros ativos associados devem ser provisionados, analisados criticamente, modificados e removidos de acordo com a política de tema específico e regras da organização para o controle de acesso.

> [!TIP] DICAS: 
> - Provisionados significa disponibilizados.
> - Política de tema específico refere-se à política de controle de acesso.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA | CONCEITO DE SEGURANÇA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|---------------------------|----------------------|--------------------------|----------------------|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Propósito
- Assegurar que o acesso às informações e outros ativos associados esteja definido e autorizado de acordo com os requisitos do negócio.
- A definição e autorização precisa estar alinhada aos requisitos do negócio.
- São fornecidos os direitos de acesso às informações, bem como os ativos associados a essas informações, conforme os requisitos do negócio.

## 2. Orientações para Provisão e Revogação dos Direitos de Acesso
- A provisão/provisionamento é a entrega dos direitos de acesso.
- Também é possível revogar os direitos de acesso que foram dados.
- O processo de provisionamento para atribuição ou revogação de direitos de acesso físico e lógico concedidos à identidade autenticada de uma entidade deve incluir:

> [!CAUTION] OBSERVAÇÃO: 
> - Em questões de prova, as bancas já afirmaram que o direito de acesso físico e lógico são feitos de forma distinta, o que é incorreto, uma vez que os direitos de acesso físico e lógico são tratados no mesmo tema, no mesmo controle.

### 2.1 Orientações Específicas
- a) Obtenção de autorização do proprietário das informações e de outros ativos associados para o uso das informações e outros ativos associados. A aprovação separada dos direitos de acesso pela direção também pode ser apropriada.
- b) Consideração dos requisitos do negócio e as regras e política específica por tema da organização sobre controle de acesso.
- c) Consideração da segregação de funções, incluindo a segregação dos papéis de aprovação e implementação dos direitos de acesso e separação de papéis conflitantes.
  - Segregar funções é ter quem provisiona distinto de quem revoga e de quem autoriza.
  - A solicitação será feita por uma pessoa, o provisionamento por outra e a revogação por outra.
  - O conflito está em quem solicita o acesso e quem está implementando efetivamente o direito de acesso, uma vez que são papéis claramente conflitantes.
  - Quem solicita não pode ser a mesma pessoa que implementa.
  - São papéis conflitantes que demandam a segregação de funções.
- d) Garantia de que os direitos de acesso sejam removidos quando alguém não precisar acessar as informações e outros ativos associados, em particular assegurando que os direitos de acesso dos usuários que deixaram a organização sejam removidos em tempo hábil.
- e) Consideração da ação de direitos temporários de acesso por um período limitado e revogação deles na data de validade, em especial para pessoal temporário ou acesso temporário exigido pelo pessoal.
  - Na prática, relaciona-se a pessoas ou empresas que estão prestando um serviço terceirizado ou fazendo um projeto que tem tempo de início e fim definidos.
  - A essas pessoas que vão necessitar desses acessos, recomenda-se que esses direitos de acesso sejam concedidos de forma temporária, delimitando o início e o fim.
  - É muito comum haver pessoas estranhas à organização participando de alguns projetos e precisando desses acessos por esse período do projeto.
- f) Verificação de se o nível de acesso concedido está de acordo com as políticas específicas por tema sobre controle de acesso e é consistente com outros requisitos de segurança da informação, como a segregação de funções.
- g) Garantia de que os direitos de acesso sejam ativados (por exemplo, por prestadores de serviços) somente após a conclusão dos procedimentos de autorização bem sucedido.
  - Antes de ser concedido o acesso há todo um processo.
  - O controle de acesso se dá nesse processo de solicitação, autorização e implementação.
  - Não se pode pular etapas: após a solicitação, não se deve diretamente implementar, mas deve haver um processo de autorização onde se verifica se realmente aquela pessoa deve ter acesso ou não ao que está sendo solicitado.
  - É necessário que sejam adotados procedimentos para que haja uma autorização só depois da implementação do acesso efetivamente.
- h) Manutenção de um registro central dos direitos de acesso concedidos a um ID do usuário (lógico ou físico) para acessar informações e outros ativos associados.
  - O registro central armazenará as informações de todos os acessos que foram dados a um determinado usuário, um determinado ID.
  - Exemplo: josis.alves. Esse ID do usuário será armazenado em um registro central que pode ser um registro lógico, uma base de dados ou físico.
- i) Modificação dos direitos de acesso dos usuários que mudaram de função ou emprego.
  - A rotatividade pode se dar não apenas da organização para fora, mas também dentro da organização.
  - Exemplo: uma pessoa do setor de banco de dados que é transferida para o setor de governança de TI.
  - Esse movimento lateral é comum dentro das organizações e a norma trata da modificação dos direitos a cada movimento de uma função para outra.
- j) Remoção ou ajuste dos direitos de acesso físico e lógico, que podem ser feitos por remoção, revogação ou substituição de chaves, informações de autenticação, cartões de identificação ou assinaturas.
- k) Manutenção de um registro de alterações nos direitos lógicos e físicos de acesso dos usuários.
  - É necessário que ocorra não apenas a concessão e a revogação, mas também um controle, podendo ser o mesmo controle, em que se registre e armazene as alterações dos direitos que o usuário teve ao longo do ciclo de vida da organização.
  - Exemplo: quando o usuário entrou, tinha determinada função e os direitos de permissão eram tais, depois trocou de função, então os direitos de permissão que lhe haviam sido concedidos foram revogados e foram dados outros.

> [!CAUTION] OBSERVAÇÃO: 
> - A revogação de direitos de acesso quando uma pessoa deixa de pertencer à organização gera um grande problema a esta.
> - Essa revogação de direitos de acesso é muito importante e crítica, é uma coisa sensível à organização, que deve ter um olhar mais atencioso para isso.

## 3. Análise Crítica dos Direitos de Acesso
- As análises críticas regulares dos direitos de acesso físico e lógico devem considerar o seguinte:
  - a) Direitos de acesso dos usuários após qualquer alteração dentro da mesma organização (por exemplo, mudança de emprego, promoção, rebaixamento) ou rescisão do emprego.
  - b) Autorizações para direitos de acesso privilegiados.

## 4. Consideração Antes de Alteração ou Rescisão do Emprego
- Os direitos de acesso de um usuário às informações e outros ativos associados devem ser analisados criticamente e ajustados ou removidos antes de qualquer alteração ou rescisão de emprego com base na avaliação de fatores de risco como:
  - a) Se a rescisão ou alteração é iniciada pelo usuário ou pela direção e o motivo da rescisão.
  - b) As responsabilidades atuais do usuário.
  - c) O valor dos ativos atualmente acessíveis.

## 5. Outras Informações

### 5.1 Funções de Acesso ao Usuário
- Deve ser considerado o estabelecimento de funções de acesso ao usuário com base nos requisitos de negócios que resumem uma série de direitos de acesso em perfis típicos de acesso ao usuário.
- Neste ponto, poderia ocorrer, por exemplo, a implementação do RBAC, que é um controle de acesso baseado em papéis/perfis.
- Havendo um perfil de gerente, a pessoa que receber o perfil de gerente terá associadas várias permissões, A, B, C, ou seja, ao ativo A, B e C.
- Esses direitos de acesso já ficam associados a um perfil.
- Caso alguém ingresse na organização para exercer a função de gerente, essas permissões já estarão associadas a esse perfil.
- Solicitações de acesso e análise crítica dos direitos de acesso são mais fáceis de gerenciar ao nível de tais funções do que no nível de direitos particulares.

> [!CAUTION] OBSERVAÇÃO: 
> - A granularidade menor é melhor do que a maior: quanto mais granular, com mais detalhes e direitos em particular, fica mais difícil/complexo de controlar.
> - Quando se insere em uma função os vários direitos de acesso, fica mais fácil controlar, porque não há essa maior granularidade, maior detalhamento, basta entregar a função para a pessoa, uma vez que os direitos que essa função tem já estão atrelados a ela.

### 5.2 Cláusulas Contratuais
- Deve ser dada consideração à inclusão de cláusulas em contratos de pessoal e contratos de serviços que especifique sanções se o acesso não autorizado for tentado por pessoal.

### 5.3 Riscos em Rescisão
- Em casos de rescisão iniciada pela direção, pessoas descontentes ou usuários de partes externas podem deliberadamente corromper informações ou sabotar os recursos de tratamento de informações.

> [!CAUTION] OBSERVAÇÃO: 
> - Quando a rescisão parte da direção e não do usuário, pode ser que ele esteja saindo da organização de forma descontente com essa situação, e a partir disso, de forma deliberada, comprometa as informações a que possui acesso ou sabote os recursos.
> - Em casos de pessoas que se demitem ou são demitidas, elas podem ser tentadas a coletar informações para uso futuro (atividade que não é legal e que pode causar prejuízo à organização).

### 5.4 Clonagem de Acessos
- A clonagem é uma maneira eficiente de as organizações atribuírem acesso aos usuários.
- No entanto, deve ser feito com cuidado com base em funções distintas identificadas pela organização, em vez de apenas clonar uma identidade com todos os direitos de acesso associados.
- Exemplo: João possui várias permissões: permissão à informação A e aos ativos B e C. O ID (identificação) é João. Diante da entrada de José, é feita uma clonagem, ou seja, uma cópia do ID de João e renomeada para José. Por ser um clone, José vai ter todas as permissões que João possuía.

> [!CAUTION] OBSERVAÇÃO: 
> - A clonagem tem um risco inerente de resultar em direitos excessivos de acesso à informação e outros ativos associados.
> - Pode ser que João tenha muitos acessos a que José não faz jus, considerando a função que desempenha.