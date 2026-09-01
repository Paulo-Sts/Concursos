# ISO/IEC 27002:2022 - Informações de Autenticação

## 1. Definição

### Tabela
| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|------------------------------------------|--------------------------------------|--------------------------|-----------------------|
| Preventivo       | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Controle
- A alocação e a gestão de informações de autenticação devem ser controladas por uma gestão de processo.
- Inclui aconselhar o pessoal sobre o manuseio adequado das informações de autenticação.

### 1.2 Propósito
- Assegurar a autenticação adequada da entidade e evitar falhas nos processos de autenticação.

### 1.3 Orientações para Alocação de Informações de Autenticação
- O processo de alocação e gestão deve assegurar:

  - Senhas pessoais ou PIN gerados automaticamente durante os processos de inscrição como informações temporárias de autenticação secreta não devem ser fáceis de adivinhar.
  - Devem ser únicas para cada pessoa.
  - Os usuários devem ser obrigados a alterá-las após o primeiro uso.

> [!CAUTION] OBSERVAÇÃO: 
> - Sistemas que geram uma senha padrão para todos os novos usuários representam um risco significativo.
> - Alguém de posse do nome do usuário e conhecimento da senha padrão pode acessar o sistema antes do usuário legítimo.
> - As senhas temporárias devem ser: únicas, aleatórias e descartadas após a primeira atribuição.

#### 1.3.1 Procedimentos de Verificação
- Procedimentos devem ser estabelecidos para verificar a identidade de um usuário antes de fornecer informações novas, de substituição ou de autenticação temporária.

#### 1.3.2 Transmissão Segura
- Informações de autenticação, incluindo temporárias, devem ser transmitidas aos usuários de forma segura.
- Exemplo: por meio de um canal autenticado e protegido.
- O uso de mensagens eletrônicas desprotegidas (texto claro) deve ser evitado.

#### 1.3.3 Confirmação de Recebimento
- Usuários devem reconhecer o recebimento das informações de autenticação.

#### 1.3.4 Alteração de Senhas-Padrão
- Informações de autenticação-padrão conforme predefinidas ou fornecidas pelos fornecedores devem ser alteradas imediatamente após a instalação de sistemas ou softwares.

> [!TIP] DICAS: 
> - Aplicável a equipamentos como switches, roteadores e qualquer dispositivo que venha com senha padrão de fábrica.
> - A alteração imediata é uma boa prática de segurança fundamental.

#### 1.3.5 Registro de Eventos
- Registros de eventos significativos relativos à alocação e gestão de informações de autenticação devem ser mantidos.
- A confidencialidade desses registros deve ser assegurada.
- O método de registro deve ser aprovado.
- Exemplo: utilizando uma ferramenta de cofre de senha aprovada.

### 1.4 Responsabilidades do Usuário
- Qualquer pessoa com acesso ou usando informações de autenticação deve ser avisada para assegurar que:

#### 1.4.1 Sigilo das Informações
- Informações de autenticação secreta, como senhas, são mantidas em sigilo.
- Informações de autenticação secreta pessoal não são compartilhadas com ninguém.
- Informações de autenticação utilizadas no contexto de identidades vinculadas a múltiplos usuários ou vinculadas a entidades não pessoais são compartilhadas exclusivamente com pessoas autorizadas.

> [!CAUTION] OBSERVAÇÃO: 
> - O compartilhamento de senhas pessoais não é aceitável, mesmo entre colegas de equipe ou do mesmo departamento.

#### 1.4.2 Comprometimento de Informações
- Informações de autenticação afetadas ou comprometidas devem ser alteradas imediatamente após a notificação ou qualquer outra indicação de comprometimento.

#### 1.4.3 Critérios para Senhas Fortes
- Quando senhas são usadas como informações de autenticação, senhas fortes de acordo com as melhores práticas recomendadas devem ser selecionadas.
- Critérios:
  - As senhas não se baseiam em qualquer coisa que outra pessoa possa facilmente adivinhar ou obter.
  - Exemplo: nomes, números de telefone e datas de nascimento.
  - As senhas não são baseadas em palavras de dicionário ou combinações delas.
  - Usar frases de senha fáceis de lembrar.
  - Tentar incluir caracteres alfanuméricos e especiais.
  - As senhas têm um comprimento mínimo.

> [!TIP] DICAS: 
> - Senhas muito complexas podem dificultar a memorização pelo usuário.
> - O equilíbrio entre complexidade e memorabilidade é importante.
> - Frases de senha são uma alternativa recomendada.

#### 1.4.4 Uso de Senhas em Serviços Distintos
- As mesmas senhas não são usadas em serviços e sistemas distintos.

> [!CAUTION] OBSERVAÇÃO: 
> - O reuso de senhas em diferentes sistemas corporativos não é aceitável, mesmo que a senha atenda a critérios mínimos de complexidade.

#### 1.4.5 Inclusão em Termos de Emprego
- A obrigação de seguir essas regras também deve ser incluída em termos e condições de emprego.
- Relacionado ao controle 6.2 da norma.