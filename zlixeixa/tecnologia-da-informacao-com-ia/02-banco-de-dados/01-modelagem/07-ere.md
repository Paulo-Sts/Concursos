# Modelo Entidade-Relacionamento Estendido (ERE)

## 1. Modelo Entidade-Relacionamento Estendido (Ere)
- Surgiu da necessidade de compatibilizar o modelo entidade-relacionamento com a orientação a objetos, abarcando melhor o desenvolvimento orientado a objetos.
- Inclui conceitos adicionais de modelagem semântica de dados, onde o dado possui um nível de significado.
- Utilizado na modelagem de aplicações com requisitos mais complexos de banco de dados.
- Exemplos de aplicações:
  - Projetos de engenharia (CAD/CAM);
  - Sistemas de informações geográficas (SIG);
  - Sistemas multimídia (áudio, vídeo, imagens).

### 1.1 Modelagem Semântica de Dados
- Traz significado aos dados, incorporando conceitos da orientação a objetos.
- Conceitos incorporados:
  - Classe;
  - Superclasse;
  - Subclasse;
  - Herança;
  - Hierarquia;
  - Agregação;
  - Generalização;
  - Especialização.

> [!TIP] DICAS:
> - A Cesgranrio tem cobrado este assunto em provas de concurso.

## 2. Generalização E Especialização
- A generalização sobe no nível de abstração (de baixo para cima).
- A especialização traz o detalhamento, tornando o conceito mais específico (de cima para baixo).

### 2.1 Generalização (Abstração)
- Processo de reversão de abstração que suprime as diferenças entre diversos tipos de entidades, identificando suas características comuns para generalizar em uma única superclasse.
- Exemplo: pessoa física e pessoa jurídica possuem atributos comuns (telefone e endereço); esses atributos são agrupados em uma superclasse "pessoa".
- Entidades especializadas com atributos comuns são convertidas em uma entidade única que possui esses elementos comuns.

### 2.2 Especialização
- Processo de definição de um conjunto de entidades de baixo nível (subclasses) a partir de entidades de alto nível (superclasse).
- As subclasses são formadas por características próprias que as distinguem das demais subclasses.
- Os atributos comuns a todas as subclasses são atributos da superclasse.
- Subclasses podem participar de relacionamentos específicos.

#### 2.2.1 O Processo De Especialização Permite
- Definir um conjunto de subclasses de um tipo de entidade;
- Estabelecer atributos específicos adicionais em cada subclasse;
- Estabelecer relacionamentos específicos entre as subclasses e outras entidades do modelo.

> [!CAUTION] OBSERVAÇÃO:
> - De cima para baixo: especialização.
> - De baixo para cima: generalização.

## 3. Superclasse E Subclasse
- Subclasse: é mais específica que a classe e decorre do agrupamento de entidades em subgrupos de um determinado tipo.
- Um relacionamento superclasse/subclasse é chamado de relacionamento É-UM (IS-A).
- Exemplo: um engenheiro É-UM empregado; um médico É-UM empregado.
- Uma instância da subclasse também é uma instância da superclasse.
- Exemplo: se João é um engenheiro, João é um empregado.

### 3.1 Herança
- A subclasse herda os atributos da superclasse, bem como os relacionamentos em que a superclasse participa.
- Todo membro de uma subclasse também é membro da superclasse.
- Exemplo: o professor é empregado, logo, possui atributos de empregado (CPF, nome, endereço, graduação, títulos).
- O membro da superclasse pode não ser membro das subclasses.
- Exemplo: o empregado que não é médico, não é professor e também não é engenheiro.
- O membro da superclasse pode ser membro de várias subclasses.
- Exemplo: João tem mestrado em engenharia de software e graduação em medicina, logo, faz parte de várias subclasses.

## 4. Restrições Em Generalização E Especialização

### 4.1 Subclasses Mutuamente Exclusivas (Disjoint)
- Um membro de uma superclasse deve ser membro no máximo de uma única subclasse.
- Representado pela letra "d" (disjoint).
- Exemplo: o empregado será médico, engenheiro ou advogado, ou apenas empregado, sem pertencer a nenhuma das subclasses.
- Exemplo prático: exclusão mútua – uma pessoa não pode ser pessoa física e pessoa jurídica ao mesmo tempo.

### 4.2 Subclasses Que Se Sobrepoem (Overlapping)
- Um membro de uma superclasse pode ser membro de mais de uma subclasse.
- Exemplo: João é médico, engenheiro e advogado simultaneamente.
- Exemplo prático: sobreposição – um empregado pode ser secretário e vigilante ao mesmo tempo, acumulando funções.

### 4.3 Restrições De Completude

#### 4.3.1 Total
- Cada entidade de uma superclasse deve ser membro de alguma subclasse na especialização.
- Representada por dois traços paralelos.
- Exemplo: uma disciplina deve escolher se é da graduação ou da pós-graduação; essa escolha é obrigatória.

#### 4.3.2 Parcial
- Uma entidade da superclasse não precisa ser membro de nenhuma das subclasses.
- Representada por apenas um traço.

> [!TIP] DICAS:
> - Disjoint (d): um ou outro, mutuamente exclusivos.
> - Overlapping: pode ser mais de um.

## 5. Agregação
- O modelo entidade-relacionamento tradicional não permite expressar relacionamentos entre relacionamentos; o modelo ERE torna esse relacionamento visível.
- Agregação é uma abstração em que relacionamentos são tratados como entidades de nível superior.
- Na orientação a objetos, a agregação é formada por partes independentes que se reúnem para formar o todo.
- Exemplo: a meia existe sem a gaveta.
- Composição: o todo é composto por partes que só funcionam com ele.
- Exemplo: as peças do computador não funcionam sem ele.
- No esquema conceitual empresarial com UML, o funcionário trabalha em um departamento; o departamento possui um gerente; o dependente pode existir sem o funcionário; o funcionário pode trabalhar em um ou mais projetos.
- É possível fazer um esquema conceitual ou lógico com UML.

> [!CAUTION] OBSERVAÇÃO:
> - A agregação é uma abstração que permite que relacionamentos sejam vistos como entidades de nível superior.
> - Ao derivar para o modelo relacional, a representação se torna mais simples.