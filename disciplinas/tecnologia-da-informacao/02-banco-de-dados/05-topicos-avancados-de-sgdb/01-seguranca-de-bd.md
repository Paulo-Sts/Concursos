# Segurança em Banco de Dados

## 1. Fundamentos da Segurança em Banco de Dados
- A segurança em banco de dados é tratada por meio de comandos pertencentes à Data Control Language (DCL), um subconjunto da linguagem SQL.
- Os comandos DCL foram incorporados ao SQL com o objetivo de oferecer mecanismos de controle de acesso aos dados armazenados.
- Os Sistemas de Gerenciamento de Banco de Dados (SGBDs) dispõem de técnicas que possibilitam restringir o acesso de usuários ou grupos de usuários a determinadas partes do banco de dados.
- O controle de acesso está diretamente relacionado ao conceito de visões (views) presente na arquitetura ANSI/SPARC.
- Os SGBDs possuem um subsistema específico de autorização e segurança, denominado mecanismo de segurança, responsável por assegurar que apenas usuários autorizados possam realizar determinadas operações sobre os dados.
- Com a criação de esquemas, é possível conceder ou revogar privilégios de acesso a usuários por meio dos comandos específicos da DCL.

### 1.1 Pilares da Segurança da Informação
- Confidencialidade (sigilo): assegura que usuários não tenham acesso a dados para os quais não possuem autorização.
  - Exemplo: um correntista não deve conseguir visualizar informações da conta bancária de outro correntista.
- Integridade: restringe a modificação de dados, garantindo que apenas usuários com permissão adequada possam alterar informações específicas.
  - Exemplo: um professor tem autorização para modificar as notas dos alunos, enquanto outros usuários não possuem esse privilégio.
- Disponibilidade: os dados devem estar acessíveis sempre que forem requisitados por usuários devidamente autorizados, garantindo que o banco de dados esteja operacional no momento da necessidade.

> [!CAUTION] OBSERVAÇÃO:
> - A classificação dos princípios da segurança da informação (confidencialidade, integridade e disponibilidade) é frequentemente abordada por bancas examinadoras e presente na literatura especializada, como nas obras de Navathe.

## 2. Mecanismos de Segurança e Políticas de Acesso
- Os mecanismos de segurança fazem parte de uma política de segurança que estabelece quais usuários possuem autorização para acessar o banco de dados, bem como suas respectivas finalidades.
- A política de segurança pode ser baseada em dois tipos principais de mecanismos: discricionários e obrigatórios (ou mandatórios).

### 2.1 Mecanismos Discricionários
- Permitem conceder privilégios a usuários específicos, como os modos de acesso a arquivos ou registros (leitura, inserção, exclusão e atualização).
- A concessão desses privilégios é feita caso a caso, conforme necessidade ou critério da administração do sistema.
- O controle de acesso discricionário é baseado na atribuição de privilégios específicos a usuários, sem a necessidade de agrupá-los em perfis ou níveis predefinidos.
- Permite a concessão e a revogação individual de permissões por meio dos comandos SQL GRANT (conceder) e REVOKE (revogar).
- Em geral, o criador de um objeto no banco de dados possui todos os privilégios sobre ele, sendo considerado seu "dono" (owner, dependendo do SGBD).
- O subsistema de segurança do SGBD mantém uma tabela interna de privilégios que registra quais usuários receberam ou perderam determinados acessos.

> [!TIP] DICAS:
> - O controle de acesso discricionário é suportado no SQL pelos comandos GRANT e REVOKE.
> - O criador de um objeto (tabela, visão, etc.) é automaticamente seu proprietário e detém todos os privilégios sobre ele.
> - A estrutura e a forma de acesso à tabela interna de privilégios variam conforme o banco de dados utilizado.

### 2.2 Mecanismos Obrigatórios (Mandatórios)
- Impõem regras de segurança baseadas em classificações atribuídas aos usuários.
- O acesso é definido por perfis preestabelecidos, de modo que, ao criar um usuário, associa-se a ele um grupo ou perfil de segurança.
- Este tipo de controle é mais rígido e segue uma estrutura previamente determinada pelo administrador do banco de dados.
- Ambos os mecanismos (discricionários e obrigatórios) podem ser implementados por meio dos comandos DCL.

## 3. Tipos de Controle de Acesso e Auditoria
- Controle de acesso: tem como objetivo impedir que usuários não autorizados acessem o banco de dados, utilizando mecanismos de autenticação que verificam as credenciais fornecidas no momento do login.
- Controle de login: refere-se ao registro das atividades realizadas por usuários autenticados, armazenadas em arquivos de log, permitindo rastrear ações executadas dentro do sistema.
- Controle de acesso aos logs: garante que apenas usuários com permissão específica possam visualizar ou manipular os registros de log, evitando que invasores ou usuários mal-intencionados apaguem evidências de suas atividades.

> [!CAUTION] OBSERVAÇÃO:
> - A segurança eficaz em bancos de dados exige não apenas a restrição ao acesso indevido, mas também o monitoramento das ações dos usuários autorizados e a proteção dos registros dessas ações.
> - Esses controles são fundamentais para a detecção de falhas, análise de incidentes e restauração de versões anteriores do banco de dados.

## 4. Administrador de Banco de Dados (DBA)
- A implementação dos mecanismos de segurança em banco de dados é de responsabilidade do Administrador de Banco de Dados (DBA).
- O DBA atua diretamente na proteção e manutenção da integridade do sistema, diferentemente do Analista de Dados, cujo foco está na modelagem e análise das informações.

### 4.1 Principais Atribuições do DBA
- Classificar usuários e dados conforme a política de segurança da organização.
- Definir e aplicar regras de acesso ao banco de dados.
- Atribuir e revogar privilégios conforme os perfis definidos.
- Estabelecer níveis de segurança, criando grupos de usuários vinculados a políticas obrigatórias de acesso.

> [!CAUTION] OBSERVAÇÃO:
> - O DBA é o profissional responsável pela segurança geral do banco de dados, sendo a principal referência técnica em situações de falha ou indisponibilidade do sistema.

## 5. Comando GRANT
- O comando GRANT no SQL é utilizado para conceder privilégios específicos a usuários sobre determinados objetos do banco de dados, como tabelas e visões.
- Assegura que apenas solicitações feitas por usuários com os devidos privilégios sejam permitidas.
- Permite definir quais permissões serão atribuídas a quais usuários.

### 5.1 Principais Privilégios do Comando GRANT
- SELECT: autoriza a leitura dos dados de todas as colunas de uma tabela.
- INSERT (coluna): permite a inserção de tuplas com valores não nulos ou diferentes do valor padrão (default) na coluna especificada.
- DELETE: permite a exclusão de registros de uma tabela.
- REFERENCES (coluna): autoriza a definição de chaves estrangeiras que fazem referência à coluna especificada.

### 5.2 Cláusula WITH GRANT OPTION
- Permite que o usuário beneficiado repasse os mesmos privilégios a outros usuários.
- Sem essa opção, o usuário pode utilizar o privilégio concedido apenas para si, mas não pode repassá-lo.
- Exemplo: se um usuário recebe permissão de SELECT em uma tabela, ele poderá realizar consultas, mas não poderá conceder essa permissão a terceiros, a menos que o privilégio tenha sido concedido com o WITH GRANT OPTION.

> [!CAUTION] OBSERVAÇÃO:
> - Esta funcionalidade é útil em ambientes onde a delegação de privilégios é necessária, mas deve ser utilizada com cautela, uma vez que amplia a cadeia de concessão de acessos dentro do banco de dados.

### 5.3 Exemplos de Uso do GRANT
- Exemplo 1: concessão sem opção de repasse
  - GRANT INSERT, DELETE ON Funcionários, Departamento TO João;
  - Neste caso, João recebe os privilégios de inserção e exclusão, mas não poderá repassá-los a outros usuários, pois a cláusula WITH GRANT OPTION não foi incluída.
- Exemplo 2: concessão com opção de repasse
  - GRANT SELECT ON Funcionários, Departamento TO Joana WITH GRANT OPTION;
  - Joana recebe o privilégio de leitura com a possibilidade de repassá-lo a outros usuários.
  - Joana pode executar: GRANT SELECT ON Funcionários TO Marcos;
- Exemplo 3: privilégio restrito a coluna específica
  - Um usuário pode receber permissão para modificar apenas o campo salário na tabela Funcionário, com privilégio restrito de atualização para essa coluna específica.

> [!TIP] DICAS:
> - A sintaxe do comando GRANT é semelhante entre os principais SGBDs, mas detalhes de implementação podem variar.
> - Em contextos de concursos, recomenda-se verificar o SGBD especificado no edital, pois alguns bancos apresentam sistemas de privilégios mais detalhados ou personalizados.

## 6. Comando REVOKE
- O comando REVOKE é utilizado para revogar privilégios concedidos anteriormente.
- Utilizado quando é necessário remover o privilégio ou apenas a opção de concedê-lo (GRANT OPTION).
- Exemplo de uso: quando um usuário começa a repassar permissões indevidamente, torna-se necessário retirar essa capacidade para controlar o acesso.

### 6.1 Sintaxe e Cláusulas do REVOKE
- Permite revogar privilégios ou a opção de concessão sobre um objeto para usuários específicos.
- Pode ser utilizado com as cláusulas RESTRICT ou CASCADE.

### 6.2 Funcionamento da Cláusula CASCADE
- A revogação com a opção CASCADE remove automaticamente os privilégios do usuário que os recebeu e também de todos os usuários que receberam privilégios por meio dele.
- Exemplo: se João concedeu à Maria o privilégio SELECT na tabela Funcionário com a opção de repassar (GRANT OPTION), e Maria concedeu o mesmo privilégio à Renata, a revogação feita por João com a opção CASCADE removerá automaticamente os privilégios de Maria e Renata.
- Caso Renata tivesse recebido a permissão diretamente de João, essa revogação não afetaria seu acesso.

> [!TIP] DICAS:
> - O mecanismo CASCADE é importante para facilitar o controle de permissões em ambientes onde múltiplos usuários têm autorização para conceder privilégios.
> - Evita a necessidade de revogar manualmente permissões de cada usuário individualmente.
> - Existem variações na implementação do comando REVOKE entre diferentes SGBDs.

> [!CAUTION] OBSERVAÇÃO:
> - Os comandos GRANT e REVOKE são fundamentais para o entendimento do controle de acesso discricionário, sendo frequentemente cobrados em provas.
> - Embora os conceitos sejam comuns aos principais sistemas SQL, detalhes de implementação e nomenclaturas específicas podem variar conforme o SGBD.