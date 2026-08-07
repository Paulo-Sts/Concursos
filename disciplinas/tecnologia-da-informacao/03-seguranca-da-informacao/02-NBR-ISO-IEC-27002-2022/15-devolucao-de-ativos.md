# ISO/IEC 27002:2022 - Devolução de Ativos

## 1. Definição
- Controle de natureza preventiva que abrange as três dimensões da tríade da segurança da informação: confidencialidade, integridade e disponibilidade.
- O conceito de segurança cibernética associado a este controle envolve proteção, capacidades operacionais, gestão de ativos e domínio de segurança.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA | CONCEITOS DE SEGURANÇA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|---------------------------|------------------------|--------------------------|-----------------------|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de ativos | Proteção |

### 1.1 Controle
- Todos os ativos da organização que estiverem em posse de pessoas ou partes interessadas devem ser restituídos quando houver alteração ou término do vínculo contratual.

### 1.2 Propósito
- Proteger os ativos da organização como parte do processo de mudança ou encerramento da contratação ou acordo.

### 1.3 Orientações para Implementação

#### 1.3.1 Formalização da Devolução
- A devolução dos ativos deve ser formalizada por meio de documento que registre a devolução dos ativos que estavam sob posse do indivíduo.
- O documento deve listar os ativos devolvidos, tais como estações de trabalho utilizadas em regime de teletrabalho.
- A formalização garante que ativos da organização não sejam perdidos durante processos de mudança ou desligamento.

> [!CAUTION] OBSERVAÇÃO:
> - A formalização se aplica tanto a ativos físicos quanto a ativos eletrônicos, não havendo distinção quanto à natureza do ativo para fins de devolução.

#### 1.3.2 Equipamentos Pessoais e Informações
- Quando o pessoal ou partes interessadas comprarem equipamentos da organização ou utilizarem seus próprios equipamentos pessoais, procedimentos devem ser seguidos para:
  - Assegurar que todas as informações relevantes sejam rastreadas e transferidas para a organização;
  - Garantir a exclusão segura das informações do equipamento (ver 7.14).
- Nestes casos, o ativo relevante não é o equipamento, mas sim a informação.
- A orientação também se aplica a equipamentos adquiridos pela organização e posteriormente vendidos a terceiros, devendo-se assegurar:
  - Rastreamento das informações;
  - Transferência das informações;
  - Exclusão segura das informações antes da alienação.

> [!CAUTION] OBSERVAÇÃO:
> - Quando informações da organização forem armazenadas ou processadas em dispositivos pessoais de colaboradores, deve-se garantir que sejam devidamente transferidas para a organização e excluídas com segurança do equipamento. Nenhum dado corporativo deve permanecer com o colaborador após o encerramento do contrato.

#### 1.3.3 Transferência de Conhecimento
- Quando o pessoal e outras partes interessadas tiverem conhecimento importante das operações em andamento, essas informações devem ser documentadas e transferidas para a organização.

#### 1.3.4 Período de Aviso Prévio
- Durante o período de aviso prévio e posteriormente, a organização deve impedir a cópia não autorizada de informações relevantes (ex.: propriedade intelectual) pelo pessoal sob aviso de rescisão.

> [!CAUTION] OBSERVAÇÃO:
> - O período de aviso prévio representa risco relevante, pois se trata de um possível cenário de atuação de um insider (pessoa interna à organização que, por insatisfação ou por estar ciente da própria demissão, pode agir de forma prejudicial). Tal risco também pode surgir quando o indivíduo esperava reconhecimento ou promoção que não ocorreu.
> - Caso o controle de acesso não esteja configurado adequadamente, o indivíduo pode copiar arquivos ou acessá-los indevidamente durante esse período.

### 1.4 Ativos Sujeitos à Devolução
- A organização deve identificar e documentar claramente todas as informações e outros ativos associados a serem devolvidos, incluindo:

  - Dispositivos endpoint do usuário: estação de trabalho, composta por computador, teclado, mouse e demais dispositivos utilizados;
  - Dispositivos de armazenamento portáteis: discos externos, pen drives (embora atualmente seja mais comum o uso de serviços de armazenamento em nuvem);
  - Equipamentos especializados;
  - Hardware de autenticação: chaves mecânicas, tokens físicos, smartcards para sistemas de informação, sites e arquivos físicos;
  - Cópias físicas de informações.

> [!TIP] DICAS:
> - A norma menciona dispositivos de armazenamento portáteis, razão pela qual essa informação deve ser mantida, inclusive para fins de prova, ainda que o uso de nuvem seja mais comum atualmente.
> - Ativos tangíveis (tokens, smart cards, chaves de acesso) e intangíveis (informações, conhecimento) devem ser devolvidos à organização.

### 1.5 Informações de Ativos Não Pertencentes à Organização
- Pode ser difícil devolver informações sobre ativos que não pertencem à organização.
- Nestes casos, é necessário restringir o uso de informações utilizando outros controles de segurança da informação, como:
  - Gestão de direitos de acesso (5.18);
  - Uso de criptografia (8.24).

> [!CAUTION] OBSERVAÇÃO:
> - Sendo ativo, possui valor para a organização, e a norma não estabelece distinção quanto ao valor para fins de devolução.