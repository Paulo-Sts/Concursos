# Modelo Entidade-Relacionamento (MER)

## 1. Definição e Objetivos do Mer
- É um modelo conceitual de alto-nível, projetado para ser compreensível aos usuários comuns.
- Técnica utilizada para criar modelos conceituais de banco de dados.
- Criado por Peter Chen, publicado em um artigo de 1976 (The Entity-Relationship Model).
- Serve como um guia antes da implementação de um banco de dados, oferecendo uma visão clara e estruturada das entidades e seus relacionamentos.
- O projeto conceitual inicia com a definição do modelo, utilizando a notação padrão do MER.
- Os requisitos funcionais se transformam em requisitos de dados, permitindo o mapeamento da estrutura da base de dados, incluindo restrições, semântica e relacionamentos.
- Objetivos do projeto conceitual:
  - Estrutura da base de dados;
  - Restrições;
  - Semântica;
  - Relacionamentos;
  - Descrição clara, não ambígua e padronizada.

> [!CAUTION] OBSERVAÇÃO:
> - A modelagem deve ser clara e sem ambiguidade, pois qualquer ambiguidade pode gerar inconsistências.
> - É importante notar que o campo de banco de dados é complexo, com diferentes fontes e abordagens, o que pode gerar confusão, especialmente para os estudantes.

### 1.1 Etapas do Desenvolvimento de um Banco de Dados
- Projeto conceitual: resulta na definição do modelo Entidade-Relacionamento (MER), representação abstrata do sistema com entidades e relacionamentos.
- Projeto lógico: define as chaves necessárias para garantir a consistência e aplica a normalização das tabelas.
- Projeto físico: modelo conceitual é transformado em SQL, e o Sistema de Gerenciamento de Banco de Dados (SGBD) controla as estruturas utilizadas.

## 2. Notações do Mer
- Existem duas notações clássicas na modelagem entidade-relacionamento.

### 2.1 Notação de Peter Chen
- Entidades representadas por retângulos.
- Relacionamentos representados por losangos.
- Atributo chave representado por um campo preenchido (ausência de preenchimento indica atributo comum).
- Inclui conceitos como atributo derivado, atributo multivalorado, dependência, cardinalidade e especialização.

### 2.2 Notação de James Martin
- Entidades representadas por retângulos.
- Relacionamentos indicados por linhas.
- Representação da cardinalidade pelo "pé de galinha" (formato que se assemelha ao pé desse animal).

> [!TIP] DICAS:
> - Notação de Peter Chen é a mais comum em questões de concurso quando há referência a losangos.
> - Notação de James Martin é facilmente reconhecida pelo "pé de galinha" (cardinalidade).
> - Conhecer ambas as notações é essencial, pois bancas examinadoras podem utilizar variações ou combinações.

### 2.3 Variações e Notações Adicionais
- Bancas de concurso frequentemente não especificam qual notação será utilizada.
- Algumas utilizam versões derivadas das anotações clássicas.
- Exemplo de aplicação: concursos recentes (como do Senado Federal) empregaram notação não tradicional, gerando confusão.
- Outras notações derivadas existem, como a utilizada pelo modelo do governo dos Estados Unidos.

## 3. Mer e Der
- O Modelo ER (Entidade-Relacionamento) é representado de forma gráfica por um Diagrama Entidade Relacionamento (DER).
- DER representa um problema como um conjunto de entidades e relacionamentos entre estas entidades.
- Modelo: estrutura conceitual genérica, com estrutura padronizada e notações próprias.
- Diagrama: representação gráfica desse modelo.
- A lógica é similar à da Engenharia de Software.

> [!CAUTION] OBSERVAÇÃO:
> - Deve-se atentar para a correta distinção entre as siglas DER e MER. DER refere-se ao Diagrama de Entidade e Relacionamento, e não ao Departamento de Estradas de Rodagem.

### 3.1 Exemplo Prático (Navathe)
- Diagrama com entidades: empregado, dependentes, departamento e projetos.
- Empregado possui dependentes, trabalha em um departamento, e este controla projetos.
- Empregado pode assumir função de supervisor (supervisiona outro empregado).
- Cada dependente vinculado a um único empregado.
- Introduz o conceito de entidade forte e entidade fraca.

## 4. Entidade
- É uma "coisa" do mundo real com existência independente.
- Pode ser um objeto com existência física ou conceitual.
- Exemplos de existência física: carro, casa, pessoa.
- Exemplos de existência conceitual: empresa, serviço, consulta.
- Representada por um retângulo contendo o nome da entidade.
- Descrita por propriedades particulares (atributos).

### 4.1 Equivalência de Termos nas Diferentes Fases
- Modelo conceitual: utiliza-se "entidade".
- Modelo lógico: utiliza-se "relação".
- Modelo físico: utiliza-se "tabela".

> [!TIP] DICAS:
> - Conhecer essa equivalência é relevante, pois algumas bancas examinadoras costumam misturar os termos.
> - O conceito de entidade forte e entidade fraca: entidade fraca é aquela cuja existência depende logicamente da existência de outra entidade (exemplo: "dependente" depende do "empregado").

## 5. Instâncias e Esquemas

### 5.1 Instância
- É a coleção de dados armazenados no BD em um determinado momento.
- Chamado de extensão do BD.
- Sofre alterações constantemente (a cada operação de inserção, exclusão ou atualização, configura-se uma nova instância).
- Pode ser comparada a uma "fotografia" do banco de dados em um dado instante.

### 5.2 Esquema
- É uma descrição do BD, incluindo as entidades e os relacionamentos entre estas.
- Também chamado de intenção do BD.
- Não sofre alterações com frequência.
- Representa a organização do banco de dados, incluindo estrutura das tabelas e seus relacionamentos.

> [!TIP] DICAS:
> - Embora as denominações "extensão" e "intenção" sejam mais antigas e pouco cobradas atualmente, podem aparecer em provas de concursos.
> - Convém evitar o uso incorreto de terminologias, como chamar diretamente as relações do banco de "SGBD" (SGBD é o software responsável pela gestão do banco).

## 6. Atributo
- É uma propriedade que descreve uma característica particular de uma entidade.
- Caracteriza uma entidade ou um relacionamento.
- Exemplo: entidade Aluno possui atributos CPF, Nome, Matrícula, Telefone, Endereço, Sexo e Data de Nascimento.
- Exemplo: entidade Automóvel possui atributos Placa, Chassi, Cor, Modelo, Marca e Ano.

> [!TIP] DICAS:
> - Os relacionamentos também podem possuir atributos (exemplo: relacionamento Consulta, entre Médico e Paciente, possui o atributo Data).
> - Esse aspecto é frequentemente cobrado em questões de concursos.

### 6.1 Atributos Simples (Atômicos) ou Compostos
- Atributo Simples: indivisíveis, não podem ser decompostos em atributos mais básicos. São considerados atributos atômicos.
  - Exemplos: sexo, peso, cor.
  - Armazenam apenas um valor por vez para uma instância da entidade.
- Atributo Composto: divisíveis, podem ser decompostos em atributos mais básicos.
  - Exemplo: Endereço pode ser dividido em logradouro, bairro, CEP, complemento.
  - Exemplo: Nome pode ser dividido em primeiro_nome e sobrenome (comum em sistemas baseados em estruturas americanas).

### 6.2 Atributos Monovalorados ou Multivalorados
- Atributo Monovalorado: possui um único valor para uma instância da entidade.
- Atributo Multivalorado: possui múltiplos valores para uma instância da entidade.
  - Exemplo: telefone de contato (pode armazenar dois ou mais números).
  - Exemplo: localização de um departamento (pode estar associado a várias localizações distintas).

### 6.3 Atributos Armazenados ou Derivados
- Atributo Armazenado: é armazenado no Banco de Dados.
- Atributo Derivado: pode ser obtido a partir de outros atributos ou de entidades relacionadas.
  - Exemplo: idade pode ser calculada a partir da Data de Nascimento.
  - Exemplo: total de alunos pode ser calculado a partir da entidade turma.

> [!CAUTION] OBSERVAÇÃO:
> - No nível conceitual, busca-se representar de forma abstrata e compreensível as informações relevantes para os usuários, sem se preocupar com detalhes técnicos do armazenamento físico.
> - Atributos multivalorados não existem fisicamente nos bancos de dados, mas são permitidos no modelo conceitual para facilitar a comunicação com o usuário.
> - Isso não viola a Primeira Forma Normal, pois se trata apenas de uma representação conceitual.
> - Tanto atributos multivalorados quanto derivados são permitidos no modelo conceitual, pois cumprem a função de representar a estrutura lógica da informação sem interferir nas regras do modelo físico.

### 6.4 Atributos Complexos e Valores Nulos
- Atributo Complexo: pode ser composto e multivalorado ao mesmo tempo.
  - Exemplo: Endereço é composto, e uma pessoa pode possuir mais de um endereço.
- Valores Nulos: uma entidade pode não possuir valor para determinado atributo, por não ser aplicável.
  - Exemplo: número do Certificado de Reservista do servidor (pode não ser aplicável para mulheres).
  - Valor nulo também pode ser utilizado quando não se sabe o valor de um atributo.

## 7. Domínio de Valores de um Atributo
- Cada atributo de um tipo de entidade está vinculado a um conjunto de valores, ou domínio de valores.
- Especifica os valores permitidos para aquele atributo para cada instância de entidade.
- Exemplo: domínio do atributo endereço é uma cadeia de caracteres.
- Exemplo: domínio do atributo ano do veículo numa concessionária de seminovos será um número inteiro compreendido entre 2000 e 2020.

> [!TIP] DICAS:
> - A definição de restrições de domínio de valor é importante para evitar inconsistências no banco de dados.
> - Ao aplicar essas restrições, assegura-se que apenas dados válidos sejam registrados.

## 8. Atributo Chave
- Atributo Chave (identificador): atributo que identifica unicamente cada instância de uma entidade.
- Os valores do atributo chave são únicos.
- Exemplos: Nº de Prontuário do Paciente, Chassi do Veículo.
- Chave Composta: chave formada por mais de um atributo, onde a combinação dos valores torna única cada instância.
  - Exemplo: CPF_PACIENTE + CRM_MÉDICO + DATA_CONSULTA identificam unicamente instância da entidade Consulta.
  - Uma consulta pode ser realizada por um paciente e um médico diferentes em datas distintas.

## 9. Superchave
- Qualquer conjunto de um ou mais atributos cujos valores são distintos para cada instância de entidade.
- Subconjunto de atributos da entidade que identifique unicamente cada instância.
- Combinação de valores não se repete para a superchave.
- Exemplo: Aluno = {Nome, Idade, Curso, Matrícula, CPF}
  - SC01 (Aluno) = {Nome, Curso, Matrícula}
  - SC02 (Aluno) = {Idade, Nome, CPF}

> [!TIP] DICAS:
> - Chave é uma superchave da qual não se pode excluir nenhum atributo e ainda preservar a propriedade de identificação única.
> - Chave é uma superchave de cardinalidade mínima.
> - O conceito de superchave é importante no processo de normalização para evitar repetições indesejadas.

## 10. Chave Candidata
- Superchave com conjunto mínimo de atributos.
- Pode existir mais de uma chave para uma mesma entidade.
- Cada uma delas é chamada de chave candidata.
- Exemplo: Aluno = {Nome, Idade, Curso, Matrícula, CPF}
  - CH1(Aluno) = {Matrícula}
  - CH2(Aluno) = {CPF}
- Exemplo: Departamento = {CÓDIGO, NOME, SIGLA, LOCALIZACAO}
  - CH1 (Departamento) = {CÓDIGO}
  - CH2 (Departamento) = {NOME}

## 11. Chave Primária
- Chave candidata que foi escolhida no projeto do BD para identificar unicamente as instâncias de determinada entidade.
- É a chave escolhida entre as chaves candidatas.
- É a mais utilizada para busca de informações em relação à entidade.
- Exemplo: CH(Aluno) = {Matrícula} e CH (Departamento) = {CÓDIGO}.
- O atributo CPF seria uma chave alternativa ou secundária.

## 12. Representação de Atributos
- Atributo Simples: representação básica.
- Atributo Chave: pode ser representado de duas formas (todo preenchido ou sublinhado, dependendo da notação).
- Atributo Derivado: calculado a partir de outros dados (exemplo: total de funcionários, derivado da contagem de registros na entidade de funcionários).
- Atributo Multivalorado: múltiplos valores para uma mesma instância, representado por um anel na notação.
- Atributo Composto: formado por múltiplos atributos.
- Atributo Chave Parcial: relacionado a entidades fracas, representado de forma específica.

> [!TIP] DICAS:
> - No modelo conceitual, o atributo chave pode ser representado de duas formas: todo preenchido ou sublinhado.
> - Atributo derivado é aquele que é calculado a partir de outros dados.
> - Atributo multivalorado pode ter múltiplos valores para uma mesma instância (representado por um anel na notação).