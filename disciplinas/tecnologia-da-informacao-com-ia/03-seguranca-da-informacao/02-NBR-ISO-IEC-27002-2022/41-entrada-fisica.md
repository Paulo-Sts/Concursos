# ISO/IEC 27002:2022 Controles Físicos II

## 1. Entrada Física
- Controle: convém que as áreas seguras sejam protegidas por controles de entrada e pontos de acesso apropriados.
- Propósito: assegurar que ocorra apenas acesso físico autorizado às informações da organização e outros ativos associados.
- Primeira barreira: a entrada física constitui a primeira barreira de proteção existente em um local.
- Orientação geral: convém que pontos de acesso, como áreas de entrega e carregamento, sejam controlados e isolados dos recursos de tratamento da informação.
- Diretrizes de acesso:
  - Restringir o acesso aos locais e edifícios apenas ao pessoal autorizado;
  - Incluir no processo de gestão o fornecimento, análise crítica periódica, atualização e revogação das autorizações;
  - Manter e monitorar livro de registro físico ou trilha de auditoria eletrônica de todos os acessos;
  - Proteger registros e informações de autenticação sensíveis;
  - Implementar mecanismos técnicos como cartões de acesso, biometria ou autenticação de dois fatores (cartão e PIN);
  - Considerar o uso de portas duplas de segurança para acesso a áreas sensíveis;
  - Implantar área de recepção monitorada por pessoal ou outros meios.
- Gestão de pessoal e terceiros:
  - Inspecionar pertences pessoais na entrada e saída, observando a legislação local;
  - Requerer o uso visível de identificação por todo o pessoal e partes interessadas;
  - Notificar imediatamente o pessoal de segurança sobre visitantes não acompanhados ou sem identificação;
  - Diferenciar funcionários, fornecedores e visitantes por meio de crachás distinguíveis;
  - Conceder acesso restrito a fornecedores apenas quando necessário, sob autorização e monitoramento;
  - Reforçar as medidas de segurança física quando a probabilidade de incidentes aumentar.
- Pontos críticos e chaves:
  - Dar atenção especial a edifícios que detêm ativos de várias organizações;
  - Proteger saídas de emergência e outros pontos contra acesso não autorizado;
  - Implementar processo de gerenciamento de chaves físicas e informações de autenticação (códigos e combinações);
  - Realizar auditoria anual de chaves e controlar o acesso ao local de armazenamento das mesmas.

### 1.1 Atributos do Controle 7.2
| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade, integridade e disponibilidade | Proteger | Segurança física e gestão de identidade e acesso | Proteção |

### 1.2 Orientações para Visitantes
- Autenticar a identidade dos visitantes por meios apropriados;
- Registrar formalmente a data e a hora de entrada e saída;
- Permitir acesso apenas para fins específicos e autorizados;
- Fornecer instruções sobre requisitos de segurança e procedimentos de emergência;
- Supervisionar todos os visitantes, exceto se houver uma exceção explícita.

### 1.3 Áreas de Entrega e Carregamento
- Restringir o acesso da área exterior apenas ao pessoal identificado e autorizado;
- Projetar as áreas para que o carregamento ocorra sem dar acesso ao restante do edifício;
- Proteger as portas externas quando as portas das áreas restritas estiverem abertas;
- Inspecionar entregas para detecção de explosivos, produtos químicos ou materiais perigosos antes do transporte interno;
- Registrar as entradas conforme os procedimentos de gestão de ativos;
- Segregar fisicamente, sempre que possível, as remessas de entrada e saída;
- Inspecionar materiais recebidos para evidenciar possíveis adulterações no caminho.

> [!TIP] DICAS: 
> - Barreiras Iniciais ⟶ implemente catracas, tokens, senhas ou crachás para assegurar a camada inicial de proteção física.
> - Identificação ⟶ o uso de crachás não é apenas para identificação, mas serve para que qualquer pessoa identifique um estranho no ambiente e reporte ao pessoal de segurança.

> [!CAUTION] OBSERVAÇÃO: 
> - O pessoal de segurança citado na norma refere-se à segurança patrimonial e das instalações, não devendo ser confundido com a equipe de segurança da informação.
> - A inspeção de materiais recebidos quanto a adulterações é responsabilidade da organização, independentemente das obrigações do fornecedor.
> - Portas de saída de emergência devem ser monitoradas e testadas para garantir que o nível de resistência do perímetro não seja comprometido.

## 2. Segurança de Escritórios, Salas e Instalações
- Controle: convém que seja projetada e implementada segurança física para escritórios, salas e instalações.
- Propósito: evitar acesso físico não autorizado, danos e interferências nas informações e ativos associados.
- Localização: convém que as instalações-chave sejam posicionadas de modo a evitar o acesso do público.
- Discrição: convém assegurar que os edifícios sejam discretos, com indicação mínima de seu propósito e sem letreiros evidentes sobre atividades de tratamento de informações.
- Proteção visual e sonora: projetar as instalações para impedir que informações ou atividades confidenciais sejam vistas ou ouvidas da parte externa.
- Blindagem: convém considerar o uso de blindagem eletromagnética conforme a necessidade e o nível de criticidade.
- Restrição de informações de localização: não disponibilizar online listas de pessoas, guias telefônicos internos ou mapas que identifiquem facilmente locais de tratamento de informações confidenciais.

### 2.1 Atributos do Controle 7.3
| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade, integridade e disponibilidade | Proteger | Segurança física e gestão de ativos | Proteção |

> [!CAUTION] OBSERVAÇÃO: 
> - Indicar a presença de atividades de segurança da informação em placas externas é uma prática que vai contra a norma, pois compromete o sigilo necessário sobre os locais críticos.
> - A publicação de guias internos e listas de funcionários de forma irrestrita online facilita o mapeamento de vulnerabilidades por agentes externos.
> - O design das salas deve garantir que conversas e telas não sejam captadas por quem está do lado de fora do perímetro seguro.