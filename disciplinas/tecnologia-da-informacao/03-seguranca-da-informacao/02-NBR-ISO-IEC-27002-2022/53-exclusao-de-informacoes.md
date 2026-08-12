# Iso/Iec 27002:2022 - Controles Tecnológicos 6

## 1. Exclusão de Informações
- Convém que as informações armazenadas em sistemas de informação, dispositivos ou em qualquer outra mídia de armazenamento sejam excluídas quando não forem mais necessárias.
- Propósito: evitar a exposição desnecessária de informações sensíveis e estar em compliance com requisitos legais, estatutários, regulamentares e contratuais para a exclusão de informações.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade | Proteger | Proteção da informação; Legal e compliance | Proteção |

### 1.1 Orientação para Exclusão
- Convém que informações sensíveis não sejam mantidas por mais tempo do que é necessário para reduzir o risco de divulgação indesejável.
- Selecionar um método de exclusão (ex.: sobrescrito eletrônico ou eliminação criptográfica) de acordo com os requisitos de negócios e leis.
- Registrar os resultados da exclusão como evidência e obter evidências de exclusão ao usar fornecedores de serviços externos.
- Configurar sistemas para destruir informações com segurança quando não forem mais necessárias, como após períodos definidos ou por solicitação.
- Excluir versões obsoletas, cópias e arquivos temporários onde quer que estejam localizados.
- Utilizar software de exclusão aprovado e seguro para exclusão permanente, garantindo que as informações não possam ser recuperadas por ferramentas forenses.
- Usar mecanismos de descarte apropriados para o tipo de mídia, como a desmagnetização de discos rígidos e meios magnéticos.
- Verificar se o método de exclusão fornecido por provedores de serviços em nuvem é aceitável para a organização.
- Automatizar os processos de exclusão de acordo com as políticas específicas por tema.

> [!CAUTION] OBSERVAÇÃO: 
> - Dependendo da sensibilidade das informações excluídas, os logs podem rastrear ou verificar se esses processos de exclusão efetivamente aconteceram.

## 2. Mascaramento de Dados
- Convém que o mascaramento de dados seja usado de acordo com a política de controle de acesso e requisitos de negócios ou legais.
- Propósito: limitar a exposição de dados confidenciais, incluindo dados pessoais (DP), e cumprir obrigações regulamentares.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade | Proteger | Proteção da informação | Proteção |

### 2.1 Técnicas de Ocultação
- Considerar o uso de técnicas como mascaramento de dados, pseudonimização ou anonimização para proteger dados sensíveis.
- Técnicas de pseudonimização ou anonimização podem ocultar dados pessoais ou sensíveis e desconectar a ligação entre o dado e a identidade do titular.
- A anonimização altera irreversivelmente o dado de tal forma que o titular não pode mais ser identificado direta ou indiretamente.
- A pseudonimização substitui informações de identificação por um pseudônimo, permitindo a identificação apenas com o conhecimento do algoritmo (informação adicional).

> [!CAUTION] OBSERVAÇÃO: 
> - Embora a pseudonimização seja mais fraca que a anonimização, os conjuntos de dados resultantes podem ser mais úteis em pesquisas estatísticas. Convém que as informações adicionais para reidentificação sejam mantidas separadas e protegidas.

## 3. Prevenção de Vazamento de Dados
- Convém aplicar medidas de prevenção a sistemas, redes e quaisquer outros dispositivos que tratem, armazenem ou transmitam informações sensíveis.
- Propósito: detectar e prevenir a divulgação e extração não autorizadas de informações por indivíduos ou sistemas.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo; Detectivo | Confidencialidade | Proteger; Detectar | Proteção da informação | Proteção; Defesa |

### 3.1 Redução do Risco de Vazamento
- Identificar e classificar informações para proteger contra vazamentos (ex.: informações pessoais, modelos de preços e projetos).
- Monitorar canais de vazamento como e-mails, transferências de arquivos, dispositivos móveis e dispositivos de armazenamento portáteis.
- Agir de modo a evitar que informações vazem, como colocar em quarentena e-mails contendo informações sensíveis.

## 4. Backup das Informações
- Convém que cópias de backup de informações, software e sistemas sejam mantidas e testadas regularmente.
- Propósito: permitir a recuperação da perda de dados ou sistemas.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Corretivo | Integridade; Disponibilidade | Recuperar | Continuidade | Proteção |

## 5. Redundância dos Recursos de Tratamento de Informações
- Implementar os recursos de tratamento de informações com redundância suficiente para atender aos requisitos de disponibilidade.
- Propósito: assegurar o funcionamento contínuo dos recursos de tratamento de informações.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Disponibilidade | Proteger | Continuidade; Gestão de ativos | Proteção; Resiliência |

### 5.1 Orientação para Redundância
- Identificar os requisitos para a disponibilidade de serviços de negócios e sistemas de informação.
- Projetar e implementar a arquitetura de sistemas com redundância adequada para atender aos requisitos identificados.

> [!CAUTION] OBSERVAÇÃO: 
> - O usuário é considerado o elo fraco do sistema.
> - A proteção contra malware deve ser apoiada por software de detecção e reparo, conscientização dos usuários, listas de bloqueio e gestão de vulnerabilidades.
> - É necessário manter planos de continuidade de negócios voltados à recuperação de ataques de malware ⟶ eventos de malware podem causar indisponibilidade significativa.
> - Configurações de hardware, software, serviços e redes devem ser estabelecidas, documentadas, monitoradas e analisadas criticamente para garantir o funcionamento correto.