# Iso/Iec 27002:2022 - Controles Tecnológicos 2

## 1. Direitos de Acessos Privilegiados 8.2
- Convém restringir e gerenciar a atribuição e o uso de direitos de acessos privilegiados.
- Propósito: assegurar que apenas usuários, componentes de software e serviços autorizados recebam direitos de acessos privilegiados.
- A restrição é necessária para evitar problemas gerados por ações maliciosas ou por imperícia de usuários sem habilitação técnica.
- A gestão desses direitos é considerada essencial para a segurança da informação.

### 1.1 Orientação para Controle de Acessos Privilegiados
- Controlar a atribuição de direitos por meio de um processo de autorização em conformidade com a política específica de controle de acessos.
- Identificar usuários que necessitam de direitos privilegiados para cada sistema ou processo, como sistemas operacionais, bancos de dados e aplicações.
- Atribuir os direitos conforme a necessidade e seguindo o princípio de evento por evento, garantindo a competência necessária para a realização da atividade.
- Manter um registro de todos os privilégios alocados e um processo de autorização formal.
- Definir e implementar requisitos para o término ou revogação dos direitos de acesso privilegiado.
- Adotar medidas para que os usuários saibam quando estão operando em modo de acesso privilegiado, como o uso de identidades específicas ou interfaces de usuário distintas.
- Exemplo: o usuário João pode utilizar sua conta comum para tarefas rotineiras e a conta João_A para funções administrativas ⟶ uso de identificadores para diferenciar o nível de acesso.
- Implementar requisitos de autenticação mais rigorosos para acessos privilegiados, podendo exigir reautenticação ou reforço na autenticação antes da execução de tarefas.
- Analisar criticamente, de forma regular e após mudanças organizacionais, se os usuários ainda se qualificam para manter direitos privilegiados com base em suas funções e competências.
- Conceder acesso privilegiado temporário apenas pelo tempo necessário para implementar alterações ou manutenções aprovadas, em vez de concessões permanentes.
- Procedimento de quebre o vidro: refere-se ao acesso emergencial restrito a situações específicas, podendo ser automatizado por tecnologias de gerenciamento de acesso privilegiado.
- Registrar todo o acesso privilegiado ao sistema para permitir auditorias, identificando quem acessou, o horário e as ações realizadas.
- Proibir o compartilhamento de identidades privilegiadas entre várias pessoas, atribuindo a cada indivíduo uma identidade separada.
- Utilizar identidades privilegiadas exclusivamente para tarefas administrativas, não devendo ser usadas para atividades gerais do dia a dia, como e-mails ou navegação na web.

> [!CAUTION] OBSERVAÇÃO: 
> - O acesso privilegiado só deve ser concedido após a conclusão total do procedimento de autorização.
> - Mudanças organizacionais podem alterar funções e responsabilidades, tornando a revisão dos acessos uma atividade essencial.
> - O uso de identificadores genéricos é perigoso pois amplia a superfície de ataque, sendo contas tradicionalmente visadas por criminosos.
> - O papel exercido, e não a identidade em si, é o que determina a necessidade do direito de acesso privilegiado.

## 2. Dispositivos Endpoint do Usuário
- Estabelecer uma política específica sobre configuração segura e manuseio de dispositivos endpoint para proteger as informações neles armazenadas.
- Implementar limitações que permitam apenas a instalação de softwares homologados pela organização.
- Utilizar criptografia em dispositivos de armazenamento e manter procedimentos de backup regulares.
- Proibir o acesso irrestrito a redes públicas sem a devida proteção de um firewall pessoal.

### 2.1 Tratamento de Informações Sensíveis em Endpoints
- Informações extremamente sensíveis podem ser acessadas por meio de dispositivos endpoint, mas convém que não sejam armazenadas neles.
- Implementar medidas técnicas adicionais para evitar o armazenamento local, como a desativação de downloads para trabalho off-line.

> [!TIP] DICAS: 
> - A proteção de endpoints exige uma combinação de controle normativo (políticas) e controle lógico (criptografia e restrição de software) ⟶ segurança em camadas.