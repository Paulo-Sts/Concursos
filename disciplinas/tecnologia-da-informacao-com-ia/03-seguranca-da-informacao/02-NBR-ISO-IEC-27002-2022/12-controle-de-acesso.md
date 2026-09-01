# ISO/IEC 27002:2022 - Controle de Acesso

## 1. Definição
- O controle 5.15 determina que as regras para o acesso físico e lógico a informações e ativos devem ser estabelecidas e implementadas conforme requisitos de segurança e de negócios.

| TIPO DE CONTROLE | PROPRIEDADES DA SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade, integridade e disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Abrangência e Propósito
- O propósito deste controle é assegurar o acesso autorizado e evitar o acesso não autorizado a informações e ativos associados;
- O controle não se limita a apenas uma modalidade, englobando obrigatoriamente tanto o acesso físico quanto o acesso lógico;
- O acesso físico envolve a entrada em ambientes críticos como datacenters ou salas de armazenamento de ativos de tecnologia;
- O acesso lógico refere-se às permissões concedidas em sistemas, dispositivos, roteadores, switches e pastas em servidores de arquivos.

> [!CAUTION] OBSERVAÇÃO: 
> - Pegadinha da banca: O examinador pode tentar induzir ao erro afirmando que o controle de acesso se restringe apenas ao meio físico ou apenas ao meio lógico. A norma exige ambos.

### 1.2 Responsabilidades e Políticas
- Compete ao proprietário da informação ou do ativo definir os requisitos de concessão de acesso para colaboradores e equipes;
- Deve ser definida uma política específica por tema sobre controle de acesso, que precisa ser comunicada a todas as partes interessadas;
- A política deve determinar quais entidades requerem cada tipo de acesso aos ativos.

### 1.3 Conceito de Entidade
- O conceito de entidade é abrangente e não se limita a seres humanos;
- Entidades podem ser pessoas autorizadas, outros sistemas (via interoperabilidade ou APIs), servidores, máquinas ou hosts específicos;
- Para simplificar o gerenciamento, podem ser atribuídas funções específicas a grupos de entidades, como profissionais de uma mesma área técnica.

## 2. Princípios de Implementação

### 2.1 Necessidade de Conhecer e de Uso
- O princípio da necessidade de conhecer dita que uma entidade só deve ter acesso às informações necessárias para a execução de suas tarefas;
- Deve-se avaliar se a entidade realmente possui a necessidade factual de conhecer a informação antes da concessão ⟶ exemplo: verificar se um estagiário precisa acessar pastas confidenciais;
- O princípio da necessidade de uso restringe o acesso à infraestrutura de tecnologia apenas quando existe uma necessidade clara.

### 2.2 Segregação de Funções
- Funções conflitantes devem ser segregadas para evitar o comprometimento da imparcialidade e da transparência;
- No âmbito do controle de acesso, as funções de solicitação, autorização e administração devem ser exercidas por pessoas distintas.

### 2.3 Gestão do Ciclo de Vida de Acesso
- O controle deve abranger a concessão de acessos a novos ingressantes na organização;
- Deve ocorrer o ajuste imediato de permissões quando um colaborador muda de função, removendo a necessidade de conhecer ativos da função anterior;
- É mandatória a revogação e o cancelamento de todos os acessos quando a pessoa deixa de integrar a organização;
- Todos os registros de concessão, alteração e revogação devem ser devidamente mantidos.

### 2.4 Restrições ao Acesso Privilegiado
- Mesmo em acessos privilegiados, devem ser aplicadas restrições rigorosas;
- Um exemplo crítico é o acesso a servidores de logs ⟶ permitir a alteração de registros de auditoria representa um risco elevado para investigações e conformidade.

## 3. Aspectos Operacionais e Granularidade
- Deve haver consistência entre os direitos de acesso e a classificação da informação ⟶ o nível de sigilo da pessoa deve ser compatível com a classificação da informação;
- Os direitos de acesso devem ser consistentes com os requisitos de segurança do perímetro físico, como em casos de técnicos terceirizados em datacenters;
- Regras de controle de acesso podem incluir elementos dinâmicos, como a avaliação de acessos passados ou valores específicos do ambiente.

### 3.1 Granularidade e Custos
- A granularidade refere-se ao nível de detalhamento do controle, podendo variar de redes inteiras até campos de dados específicos;
- Alta granularidade indica maior nível de detalhe ⟶ baixa granularidade indica menor detalhamento;
- Regras mais fortes e maior granularidade normalmente elevam os custos de implementação e manutenção.

> [!TIP] DICAS: 
> - A norma ISO 27002:2022 não especifica ou enumera métodos técnicos de autenticação como MFA ou SSO para o controle físico, focando nas diretrizes de política e requisitos.
> - A análise crítica do processo de aprovação de acessos deve ser realizada de forma regular e periódica para garantir a conformidade com o negócio.