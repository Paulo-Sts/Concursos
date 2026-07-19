# Projeto de Banco de Dados 

## 1. Características da Tecnologia de Bancos de Dados

| CARACTERÍSTICA | DESCRIÇÃO |
|---|---|
| Natureza "auto descritiva" | O SGBD armazena uma definição completa das restrições e estruturas do banco de dados no catálogo (metadados). Os metadados têm a função autodescritiva – descrevem automaticamente o que há no banco. |
| Independência entre programas e dados | O sistema cuida das regras de negócio; o banco de dados cuida dos dados. Programas e dados são separados. |
| Abstração de dados | Um modelo de dados é usado para esconder detalhes de armazenamento, apresentando ao usuário uma representação conceitual dos dados. |
| Múltiplas visões | Cada usuário pode acessar diferentes visões do banco de dados, descrevendo apenas os dados de seu interesse. |
| Controle de redundância | A redundância é controlada, não indevida. Visa alta disponibilidade (dados replicados para recuperação em caso de falha). |
| Controle de concorrência | Garante a consistência dos dados quando múltiplas transações acessam o banco simultaneamente. Relaciona-se com o isolamento (propriedade ACID). |
| Segurança | Restrição de acesso não autorizado. O SGBD provê mecanismos de autenticação, permissões, perfis e grupos de usuários. |
| Backup e recovery | Possibilidade de cópia de segurança e recuperação de falhas de hardware e software. |
| Múltiplas interfaces | Diferentes tipos de usuários podem interagir via linha de comando, GUI (interface gráfica), etc. |
| Manutenção de restrições de integridade | Capacidade de definir e impor restrições (ex.: chave primária, chave estrangeira, NOT NULL). |

### 1.1 Redundância Controlada
- A redundância não é mais um problema, como nos sistemas de arquivos tradicionais.
- É usada estrategicamente para garantir alta disponibilidade e recuperação em caso de falhas.

## 2. Arquitetura ANSI/SPARC (3 Níveis)
- Proposta nos anos 1970 como padrão para implementação de SGBDs.
- Divide o sistema em três níveis de abstração:
  - Nível 1 (Externo ou de visão): Inclui os esquemas externos (visões de usuário). Cada visão descreve a parte do banco de dados que interessa a um determinado grupo de usuários. 
  - Nível 2 (Conceitual): Descreve a estrutura de todo o banco de dados para a comunidade usuária. Esconde detalhes de armazenamento físico. Mostra entidades, tipos de dados, relacionamentos, restrições.
  - Nível 3 (Interno ou físico): Descreve a estrutura de armazenamento físico. Utiliza um modelo de dados físico para definir detalhes sobre armazenamento e trajetos de acesso (índices, arquivos, etc.).

### 2.1 Independência de dados (na arquitetura ANSI/SPARC)

#### Independência Lógica
- Mudança no esquema conceitual não afeta os programas de aplicação ou o esquema externo. 
- Alteração na estrutura do banco de dados (ex.: adicionar uma coluna) sem afetar as visões existentes.

#### Independência Física
- Modificação no esquema físico não afeta o esquema conceitual nem o externo. 
- Mudança na localização dos datafiles ou criação de um novo índice.

## 3. Etapas do Projeto de Banco de Dados

### 3.1 Visão Geral do Processo

| ETAPA | DESCRIÇÃO | DEPENDÊNCIA |
|---|---|---|
| Coleta e análise de requisitos | Projetistas entrevistam usuários para compreender e documentar seus requisitos de dados. | Independente de SGBD. |
| Projeto conceitual | Criação do esquema conceitual (ex.: Modelo Entidade-Relacionamento – MER). Descreve entidades, relacionamentos e restrições. | Independente de SGBD. |
| Projeto lógico | Mapeamento do modelo conceitual para o modelo do SGBD (ex.: relacional, OO, relacional-objeto). | Dependente do modelo de dados (paradigma), mas independente do SGBD específico (ex.: pode ser implementado em qualquer banco relacional). |
| Projeto físico | Define estruturas de armazenamento, organização de registros físicos, criação de índices, espaço alocado, etc. | Dependente do SGBD específico. |

#### 3.1.1 Esquema Conceitual
- Descrição concisa dos requisitos de dados dos usuários.
- Inclui descrições de: entidades, relacionamentos, restrições e tipos de entidades.
- Independente de SGBD.
- Exemplo: MER (Modelo Entidade-Relacionamento).

#### 3.1.2 Esquema Lógico
- Mapeamento do modelo conceitual para o modelo de dados do SGBD (ex.: relacional).
- Dependente do modelo de dados (ex.: relacional, orientado a objetos, etc.).
- Independente do SGBD específico, pode ser implementado em qualquer banco que suporte o modelo escolhido.

#### 3.1.3 Esquema Físico
- Define estruturas de armazenamento, índices, alocação de espaço, etc.
- Dependente do SGBD específico (ex.: Oracle, MySQL, SQL Server).

### 3.2 Nomenclatura por Nível 

| NÍVEL                       | TERMINOLOGIA USADA                 |
|-----------------------------|------------------------------------|
| Projeto conceitual          | Entidade, relacionamento, atributo |
| Projeto lógico (relacional) | Relação, tupla, atributo           |
| Projeto físico              | Tabela, linha, coluna              |