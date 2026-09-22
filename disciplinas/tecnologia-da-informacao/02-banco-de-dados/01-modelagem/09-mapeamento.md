# Banco de Dados - Mapeamento

## 1. Conceitos Iniciais de Projeto de Banco de Dados
- O projeto conceitual visa representar as necessidades dos usuários.
- O projeto lógico define como os dados serão efetivamente armazenados, com foco na consistência dos dados.
- O projeto físico inclui comandos SQL para criar o banco, além de questões relacionadas a índices, espaço em memória e outros aspectos gerenciados pelo SGBD.
- A estratégia de banco de dados distribuído (BDD) existe, mas com as evoluções tecnológicas, seu uso diminuiu.

## 2. Modelo Lógico Relacional
- A notação do modelo relacional é textual e segue a estrutura: NOME_DA_RELACAO (atributo1, atributo2, ...).
- Os atributos sublinhados representam a chave primária da relação.

### 2.1 Exemplo de Modelo Lógico
- Médico (CRM, Nome, Endereco, Telefone).
- Paciente (CPF, Nome, Endereco, Telefone).
- Exame (Codigo, Nome, Resultado, Cod_consulta).
- Consulta (Codigo, Observacao).

## 3. Objetivos do Mapeamento ER-Relacional
- Elaborar um modelo lógico com boa performance em relação às requisições ao banco de dados.
- Construir um modelo que simplifique o desenvolvimento e a manutenção de sistemas.

### 3.1 Regras Básicas para o Modelo Lógico
- Evitar o uso de junções (joins), pois elas geram produto cartesiano e podem consumir espaço desnecessário.
  - Observação: algumas junções são necessárias; o objetivo é evitá-las para não prejudicar a performance.
- Reduzir o número de chaves primárias (PKs), já que elas criam estruturas paralelas (índices) que ocupam memória e podem tornar a tabela mais lenta.
  - Exemplo: em bancos NoSQL, o dado é normalizado e não se preocupa tanto com a consistência; o campo "médico" pode ser autoincrementado, dispensando uma chave primária.
- Evitar campos opcionais, pois eles geram muitos campos vazios que ocupam espaço em memória.
  - Observação: campo vazio é diferente de nulo; o valor nulo não ocupa espaço.
  - Exemplo: não criar campos para data de nascimento e idade simultaneamente, pois a idade é derivada da data de nascimento.

> [!CAUTION] OBSERVAÇÃO: 
> - A regra de evitar junções busca otimizar a performance, mas elas não são eliminadas por completo, apenas evitadas quando possível.
> - A redução de chaves primárias visa economizar memória e melhorar a velocidade da tabela.
> - Campos opcionais devem ser evitados para não desperdiçar espaço, lembrando que nulos não ocupam espaço, mas campos vazios sim.

## 4. Mapeamento ER-Relacional
- O mapeamento converte o modelo entidade-relacionamento (ER) para o modelo relacional.
- Os principais elementos a serem mapeados são:
  - Entidades fortes.
  - Atributos multivalorados.
  - Entidades fracas.
  - Relacionamentos (1:1, 1:N, M:N, N-ários).
  - Generalizações/Especializações.

### 4.1 Estratégias de Mapeamento
- Tabela própria: cria-se uma tabela separada para representar o elemento.
- Adição de coluna: adiciona-se uma coluna à tabela existente.
- Fusão de tabelas: combina duas tabelas em uma única.
  - Observação: a fusão de tabelas é a estratégia mais rara.

## 5. Entidades Fortes e Fracas
- Entidade forte: possui chave própria e não depende de outra entidade para existir.
  - Exemplo: CPF como chave primária.
- Entidade fraca: não possui chave própria e depende de uma entidade forte.
  - O mapeamento de uma entidade fraca deve incluir um atributo da entidade forte (chave estrangeira) para associá-los.
  - Exemplo: dependente precisa ser associado ao empregado.

### 5.1 Atributos e Chaves
- Atributo simples: valor único e atômico.
- Atributo chave: identifica unicamente uma ocorrência da entidade.
- Atributo multivalorado: pode ter mais de um valor; para evitar repetições, cria-se uma tabela separada.
  - Exemplo: Telefone (atributo multivalorado) deve ser armazenado em uma tabela própria vinculada ao CPF do cliente.
- Atributo composto: pode ser dividido em partes menores (ex.: endereço).
- Atributo chave parcial: utilizado em entidades fracas para identificar a ocorrência dentro do conjunto da entidade forte.

> [!TIP] DICAS: 
> - Em bancos relacionais, dados repetidos não são permitidos; por isso, atributos multivalorados são tratados com tabelas separadas.
> - A chave parcial, combinada com a chave da entidade forte, forma a chave primária da entidade fraca.

## 6. Auto-Relacionamento
- Ocorre quando uma entidade se relaciona com ela mesma.
- No mapeamento, aceita-se campos nulos para aqueles registros que não possuem um relacionamento com outro da mesma entidade.
  - Exemplo: órgãos públicos onde um órgão pode ter um superior (auto-relacionamento). O órgão que não possui superior (ex.: Supremo Tribunal Federal) terá o campo nulo.

## 7. Relacionamentos 1:1
- Em relacionamentos um-para-um, a fusão de tabelas é comum, mas depende da cardinalidade.
  - Exemplo: país e constituição (cada país tem apenas uma constituição). A constituição pode ser adicionada como coluna na tabela do país.
- Caso o relacionamento seja opcional (0,1) para ambos os lados, é possível adicionar uma coluna com a chave estrangeira em uma das tabelas, permitindo valores nulos.
  - Exemplo: Homem e Mulher (casamento). Pode-se adicionar CodEsposa na tabela HOMEM ou CodMarido na tabela MULHER, com valores nulos para quem não é casado.

### 7.1 Opções para Mapeamento 1:1
- Opção 1:
  - Homem (CodHomem, NomeHomem, CodEsposa).
  - Mulher (CodMulher, NomeMulher).
  - Neste caso, CodEsposa na tabela Homem é a chave estrangeira para a tabela Mulher. Homens não casados terão o campo nulo.
- Opção 2:
  - Homem (CodHomem, NomeHomem).
  - Mulher (CodMulher, NomeMulher, CodMarido).
  - Aqui, CodMarido na tabela Mulher é a chave estrangeira para a tabela Homem. Mulheres não casadas terão o campo nulo.

> [!TIP] DICAS: 
> - Ao optar por uma das opções, é importante considerar qual lado terá mais registros nulos para otimizar o espaço.
> - Em relacionamentos 1:1 com opcionalidade, os campos que podem ser nulos devem ser identificados para garantir a integridade.

## 8. Exemplo Prático com Departamentos
- Tabela Departamento: CodDep, Sigla, Local, CodGerente.
- Tabela Empregado: CodEmp, Nome, etc.
- A chave estrangeira CodGerente na tabela Departamento referencia CodEmp na tabela Empregado.
- Isso permite identificar quem gerencia cada departamento.

### 8.1 Tabelas do Exemplo
| CODEMP | NOME       |
|--------|------------|
| 1      | João       |
| 2      | Antônio    |
| 3      | Juliana    |
| 4      | Priscila   |
| 5      | Vinícius   |
| 6      | Renata     |
| 7      | Maurício   |
| 8      | Marcelo    |

| CODDEP | SIGLA | LOCAL         | CODCERENTE |
|--------|-------|---------------|------------|
| 10     | DTI   | Recife        | 1          |
| 20     | DENG  | São Paulo     | 3          |
| 30     | DJUR  | Porto Alegre  | 7          |
| 40     | DFIN  | Brasília      | 6          |
| 50     | DAUD  | Vitória       | 4          |

- Gerenciamento:
  - DTI – João.
  - DENG – Juliana.
  - DJUR – Maurício.
  - DFIN – Renata.
  - DAUD – Priscila.

> [!CAUTION] OBSERVAÇÃO: 
> - O uso de chaves estrangeiras para representar relacionamentos é essencial no modelo relacional.
> - A escolha entre adicionar coluna, criar tabela própria ou fundir tabelas depende da cardinalidade e das regras de negócio.
> - A fusão de tabelas é rara e geralmente aplicada em relacionamentos 1:1 com obrigatoriedade total.