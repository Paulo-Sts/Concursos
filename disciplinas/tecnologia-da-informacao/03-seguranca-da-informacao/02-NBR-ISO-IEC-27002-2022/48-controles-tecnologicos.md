# Iso/Iec 27002:2022 - Controles Tecnológicos

## 1. Dispositivos Endpoint do Usuário 8.1
- Convém que as informações armazenadas, tratadas ou acessíveis por meio de dispositivos endpoint do usuário sejam protegidas.
- O propósito deste controle é proteger informações contra os riscos introduzidos pelo uso desses dispositivos, abrangendo a proteção à estação de trabalho do funcionário onde os dados são processados.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Proteção da informação; Gestão de ativos | Proteção |

### 1.1 Orientação Geral
- Convém que a organização estabeleça uma política específica por tema sobre configuração segura e manuseio de dispositivos endpoint do usuário.
- A Política de Segurança da Informação (PSI) é a norma máxima, e as políticas específicas, como a de proteção de estação de trabalho, estão subordinadas a ela.
- A política deve ser efetivamente comunicada a todo o pessoal relevante para garantir que o controle não seja apenas formal, mas eficiente na prática.
- Aspectos que a política deve considerar:
  - Tipo de informação e nível de classificação que os dispositivos podem manusear ou armazenar;
  - Registro de dispositivos para controle de localização e responsabilidade;
  - Requisitos para proteção física do hardware;
  - Restrição da instalação de software, permitindo apenas aplicativos homologados pela organização;
  - Requisitos para versões de software e ativação de atualizações automáticas;
  - Regras de conexão com redes externas, incluindo o uso de firewall pessoal e servidores proxy;
  - Controles de acesso, criptografia do dispositivo de armazenamento e proteção contra malware;
  - Capacidade de desativação, exclusão ou bloqueio remotos e realização de backups;
  - Uso de dispositivos removíveis e possibilidade de desativação de portas físicas como USB;
  - Uso de capacidade de particionamento para separar com segurança informações da organização de outros ativos.

> [!TIP] DICAS: 
> - A restrição de instalação de softwares pode ser implementada tecnicamente via Active Directory (AD), mas deve estar prevista formalmente na política específica para garantir o respaldo normativo ⟶ controle lógico apoiado por controle documental.

### 1.2 Responsabilidade do Usuário
- Convém que os usuários estejam cientes dos requisitos de segurança e de suas responsabilidades individuais na proteção dos dispositivos.
- Orientações recomendadas aos usuários:
  - Encerrar sessões ativas e finalizar serviços quando não forem mais necessários;
  - Proteger o dispositivo contra uso não autorizado mediante controles físicos (fechaduras) e lógicos (senhas);
  - Jamais deixar dispositivos contendo informações importantes ou críticas sem supervisão ou monitoramento;
  - Utilizar cuidados especiais em locais públicos, como o uso de filtros de tela de privacidade para evitar que pessoas leiam informações por trás do usuário;
  - Proteger fisicamente os dispositivos contra roubo em locais de transporte, hotéis ou centros de conferência.

> [!CAUTION] OBSERVAÇÃO: 
> - A norma considera inadmissível deixar equipamentos sem vigilância em locais comuns, mesmo que protegidos por senha. Além disso, o risco de visualização indevida (shoulder surfing) em transportes públicos não é irrelevante; a proteção deve ser aplicada ativamente.

### 1.3 Uso de Dispositivos Pessoais
- Quando a organização permite o BYOD (Bring Your Own Device), diretrizes adicionais devem ser observadas.
- Implementação de software que permita a separação clara entre o uso pessoal e o empresarial no mesmo dispositivo.
- Fornecimento de acesso à informação condicionado ao reconhecimento formal das funções e responsabilidades de segurança pelo usuário.
- Garantia de que a organização possa realizar a limpeza remota de dados (wipe) em caso de perda, roubo ou descontinuidade da autorização de uso;
- Previsão de políticas para evitar disputas sobre direitos de propriedade intelectual desenvolvidos em equipamentos privados;
- Consideração de limitações legais no acesso a equipamentos de propriedade privada durante investigações ou verificações de segurança.

### 1.4 Conexões sem Fio e Outras Informações
- Estabelecer procedimentos para a configuração segura de conexões sem fio, desativando protocolos vulneráveis.
- Utilizar largura de banda apropriada para garantir que cópias de segurança e atualizações de software sejam concluídas com sucesso.
- Considerar que o backup em dispositivos endpoint pode falhar por limitações de rede ou porque o dispositivo não está conectado no momento agendado.
- Observar que em portas USB-C a desativação total pode não ser possível se a porta for essencial para fornecimento de energia ou saída de monitor.