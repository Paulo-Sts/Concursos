# Banco de Dados - Projeto de Bd

## 1. Características Gerais dos Sistemas de Bancos de Dados (SBDs)
- Os SGBDs (Sistemas de Gerenciamento de Bancos de Dados) possuem características fundamentais que os diferenciam de sistemas de arquivos tradicionais.

### 1.1 Natureza Autodescritiva
- O SGBD armazena uma definição completa das restrições e estruturas do banco de dados em um local chamado catálogo.
- As informações do catálogo são conhecidas como metadados, que são dados sobre os dados.
- A função principal dos metadados é garantir a natureza autodescritiva do banco, descrevendo automaticamente o que está armazenado.

### 1.2 Independência entre Programas e Dados
- O sistema é responsável por gerenciar as regras de negócio, enquanto o banco de dados cuida exclusivamente do armazenamento e da gestão dos dados.

### 1.3 Abstração de Dados e Modelagem Conceitual
- Um modelo de dados é utilizado para esconder detalhes de armazenamento, fornecendo ao usuário uma representação conceitual dos dados.
- O modelo de dados serve como uma abstração de alto nível da informação.

### 1.4 Múltiplas Visões
- Cada usuário ou grupo de usuários pode acessar diferentes visões do banco de dados, que descrevem apenas os dados de seu interesse.

### 1.5 Controle de Redundância
- O sistema evita a replicação indevida de dados.
- A redundância permitida é controlada e visa a alta disponibilidade, garantindo que, em caso de falha, os dados possam ser acessados por outra via.

### 1.6 Controle de Concorrência
- É um mecanismo para garantir a consistência dos dados durante o acesso simultâneo.
- O isolamento é uma propriedade fundamental, assegurando que transações concorrentes não interfiram umas nas outras.

### 1.7 Segurança
- O SGBD fornece mecanismos para restringir o acesso não autorizado aos dados, como autenticação de usuários, uso de senhas e comandos para conceder ou remover privilégios.
- É possível criar perfis e grupos de usuários com determinadas permissões.

### 1.8 Backup e Recovery
- O sistema oferece recursos para realizar cópias de segurança (backup) e para recuperar o banco de dados em caso de falhas de hardware ou software.

### 1.9 Múltiplas Interfaces
- Os SGBDs disponibilizam diferentes tipos de interfaces para atender a diversos perfis de usuários, como interfaces de linha de comando (CLI) e interfaces gráficas (GUI).

### 1.10 Manutenção de Restrições de Integridade
- O SGBD possui a capacidade de definir e impor restrições de integridade sobre os dados armazenados, garantindo a sua validade e consistência.

## 2. Arquitetura de 3 Níveis – ANSI/SPARC
- A arquitetura ANSI/SPARC foi concebida na década de 1970 para orientar a implementação dos SGBDs, incorporando as características de independência e abstração de dados.
- O próprio SGBD implementa essa arquitetura.
- A arquitetura é composta por três níveis:

### 2.1 Nível Externo (ou de Visão)
- Corresponde ao nível mais alto de abstração e contém os esquemas externos, que são as visões personalizadas dos dados para cada grupo de usuário.
- Cada esquema externo descreve apenas a parte do banco de dados que interessa a um determinado grupo, permitindo o trabalho paralelo e isolado.

### 2.2 Nível Conceitual
- É o nível de abstração intermediário que descreve a estrutura completa de todo o banco de dados para a comunidade de usuários.
- Este esquema conceitual esconde os detalhes de armazenamento físico e mostra as entidades, tipos de dados, relacionamentos, operações dos usuários e restrições.

### 2.3 Nível Interno
- É o nível de abstração mais baixo, que descreve a estrutura de armazenamento físico dos dados.
- Utiliza um modelo de dados físico para definir detalhes sobre o armazenamento e os caminhos de acesso, como a localização dos arquivos e a criação de índices.

#### 2.3.1 Independência Lógica e Física
- A arquitetura ANSI/SPARC garante a independência entre os níveis:
- Independência Lógica: A capacidade de modificar o esquema conceitual sem afetar os programas de aplicação ou os esquemas externos.
- Independência Física: A capacidade de modificar o esquema interno (ex.: mudar a localização dos arquivos de dados, criar novos índices) sem afetar os esquemas conceitual e externo.

> [!CAUTION] OBSERVAÇÃO: 
> - A arquitetura ANSI/SPARC é considerada uma arquitetura genérica e teórica, servindo como padrão de referência para os SGBDs.

## 3. Projeto de Banco de Dados
- O desenvolvimento de um banco de dados segue um processo estruturado com etapas distintas.

### 3.1 Coleta e Análise de Requisitos
- Nesta etapa inicial, os projetistas entrevistam os usuários para compreender e documentar seus requisitos de dados e funcionais.

### 3.2 Projeto Conceitual
- O objetivo é criar um esquema conceitual do banco de dados.
- Este esquema é uma descrição concisa e de alto nível dos requisitos de dados, incluindo tipos de entidades, relacionamentos e restrições.
- O esquema conceitual é independente do SGBD. Um exemplo comum de modelo é o Modelo Entidade-Relacionamento (MER).
- A etapa de projeto conceitual gera o esquema conceitual.

### 3.3 Projeto Lógico
- Nesta fase, o modelo conceitual é mapeado para um modelo de dados lógico, como o modelo relacional, orientado a objetos ou relacional-objeto.
- O esquema lógico é dependente do paradigma de dados (ex.: relacional), mas é independente do SGBD específico.
- Por exemplo, um projeto lógico relacional pode ser implementado em qualquer SGBD relacional.
- A etapa de projeto lógico gera o esquema lógico.

### 3.4 Projeto Físico
- Esta etapa define as estruturas de armazenamento físico para um SGBD específico.
- Inclui a definição da organização dos registros físicos, a criação de índices e a alocação de espaço.
- O esquema físico é dependente do SGBD escolhido.
- A etapa de projeto físico gera o esquema físico.

### 3.5 Implementação e Aplicações
- O esquema físico é implementado em um SGBD específico.
- As aplicações (programas) são desenvolvidas com base nos requisitos funcionais e nas especificações de transações.

> [!TIP] DICAS: 
> - É crucial entender a terminologia correta para cada fase do projeto. No nível conceitual, fala-se em entidades e relacionamentos. No nível lógico, em relações e atributos. No nível físico, em tabelas. As bancas, especialmente a Cespe, podem não respeitar essa distinção rigorosamente, mas o conhecimento correto é fundamental para resolver questões de alto nível.

### Tabela de Nomenclatura por Nível de Projeto
| NÍVEL DE PROJETO | TERMINOLOGIA DO ESQUEMA | DESCRIÇÃO |
|------------------|-------------------------|-----------|
| Conceitual | Entidade / Relacionamento | Descrição de alto nível, independente de SGBD (ex.: MER). |
| Lógico | Relação / Atributo | Mapeamento para um modelo de dados (ex.: Relacional). Independente do SGBD, mas dependente do paradigma. |
| Físico | Tabela | Definição de estruturas de armazenamento, índices, etc. É dependente do SGBD específico. |