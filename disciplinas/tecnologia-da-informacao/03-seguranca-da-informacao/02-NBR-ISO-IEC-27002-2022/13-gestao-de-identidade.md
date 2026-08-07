# ISO/IEC 27002:2022 - Gestão de Identidade

## 1. Definição
- O controle 5.16 define as diretrizes para gerenciar o ciclo de vida das identidades, visando permitir o acesso autorizado e prevenir acessos não autorizados a informações e ativos.

| TIPO DE CONTROLE | PROPRIEDADES DA SEGURANÇA | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade, integridade e disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Etapas para Gestão de Acesso e Identidade
- O processo de fornecer ou revogar o acesso a informações e ativos associados é geralmente realizado em várias etapas:
  - Confirmação dos requisitos de negócios para que uma identidade seja estabelecida;
  - Verificação da identidade de uma entidade antes de alocá-la como uma identidade lógica;
  - Estabelecimento formal da identidade;
  - Configuração e ativação da identidade, incluindo os serviços de autenticação iniciais;
  - Fornecimento ou revogação de direitos de acesso específicos baseados em autorização ou decisões de direito.

### 1.2 Diretrizes de Implementação e Manutenção
- As identidades devem ser desativadas ou removidas em tempo hábil caso não sejam mais necessárias, como quando entidades associadas são excluídas ou o colaborador deixa a organização;
- Dentro de um domínio específico, convém que uma única identidade seja mapeada para uma única entidade para evitar identidades duplicadas;
- Devem ser mantidos registros detalhados de todos os eventos significativos sobre o uso e a gestão de identidades e informações de autenticação;
- A organização deve possuir processos de apoio para lidar com alterações em informações de identidade, o que pode incluir a reverificação de documentos.

### 1.3 Identidades de Terceiros
- Ao utilizar identidades fornecidas por terceiros, como credenciais de mídias sociais, a organização deve assegurar o nível de confiança necessário;
- É necessário que quaisquer riscos associados a essas identidades externas sejam conhecidos e devidamente tratados por meio de controles de autenticação.

> [!TIP] DICAS: 
> - Entidades não são apenas seres humanos; elas podem ser físicas ou lógicas, abrangendo também equipamentos ou sistemas que necessitem de acesso aos ativos da organização.

> [!CAUTION] OBSERVAÇÃO: 
> - Pegadinha: Identidades atribuídas a várias pessoas (compartilhadas) são permitidas apenas se houver necessidade de negócio ou operacional, sendo obrigatoriamente sujeitas a aprovação e documentação dedicada.
> - A revogação de acessos deve ocorrer prontamente não apenas no desligamento, mas também em mudanças de papel/função do usuário dentro da empresa.