# Banco de Dados - Relacionamentos

## 1. Conceito de Relacionamento
- Relacionamento é uma associação entre entidades que representa um fato do mundo real.
- Quando um atributo de uma entidade A refere-se a um atributo da entidade B, diz-se que existe um relacionamento entre A e B.
- Exemplo: a entidade Funcionário e a entidade Departamento se associam por meio do relacionamento "Trabalha para", que vincula cada funcionário ao seu respectivo departamento.
- Na representação dos conjuntos, um exemplo prático é: o empregado 1 trabalha para o departamento 1, registrando-se o par (e1, d1).

> [!CAUTION] OBSERVAÇÃO:
> - O professor destaca que, atualmente, projetos conceituais são menos utilizados, partindo-se diretamente para o modelo relacional. Contudo, esse conteúdo ainda é cobrado em concursos públicos, sendo fundamental saber interpretar os modelos.

## 2. Grau dos Relacionamentos
- O grau de um relacionamento é definido pelo número de entidades participantes.

### 2.1 Relacionamento Binário (Grau 2)
- Envolve duas entidades.
- Exemplo: o relacionamento "Cursa" envolve as entidades Aluno e Disciplina.

### 2.2 Relacionamento Ternário (Grau 3)
- Envolve três entidades.
- Exemplo: o relacionamento "Fornece" envolve as entidades Fornecedor, Projeto e Peça.
- Observação importante: relacionamentos com mais de três entidades (quaternários, etc.) são raros devido à complexidade das chaves e ao impacto na performance. O mais comum e recomendado é o uso de relacionamentos binários.

## 3. Relacionamento Recursivo
- É aquele em que o relacionamento associa instâncias da mesma entidade, ou seja, a entidade se relaciona com ela mesma.
- Nesse contexto, surge o conceito de papel, que define a função que uma ocorrência da entidade desempenha em uma ocorrência do relacionamento.
- Exemplo: um funcionário pode ser gerente de outro funcionário, sendo que ambos são da mesma entidade Funcionário, com papéis distintos (gerente e subordinado).

## 4. Restrição de Cardinalidade
- Determina o número máximo de instâncias de relacionamento nas quais uma entidade pode participar.
- Os tipos básicos de cardinalidade são:

| TIPO | DESCRIÇÃO |
|------|-----------|
| M:n (muitos-para-muitos) | Uma entidade a está associada a várias (zero ou mais) entidades de b, e uma entidade de b está associada a várias (zero ou mais) entidades de a. |
| 1:n (um-para-muitos) | Uma entidade a está associada a várias (zero ou mais) entidades de b, mas uma entidade de b está associada a, no máximo, uma entidade de a. |
| 1:1 (um-para-um) | Uma entidade a está associada a, no máximo, uma entidade de b, e uma entidade de b está associada a, no máximo, uma entidade de a. |

### 4.1 Representação das Restrições de Cardinalidade
- Exemplos práticos:
  - 1:1 - Um funcionário gerencia um departamento, e um departamento é gerenciado por um funcionário.
  - 1:N - Um funcionário trabalha em um departamento, e um departamento pode ter N funcionários trabalhando nele.
  - M:N - Um médico consulta muitos pacientes, e um paciente pode ser consultado por muitos médicos.

### 4.2 Restrição de Cardinalidade Mínima e Máxima
- Envolve associar um par de números inteiros (min, max) a cada participação de uma entidade em um relacionamento.
- A representação é feita com pares (min, max):
  - (1,1) e (1,1): um funcionário gerencia no mínimo e no máximo um departamento; um departamento tem no mínimo e no máximo um funcionário gerenciando.
  - (1,1) e (0,n): um funcionário trabalha para no mínimo e no máximo um departamento; um departamento pode ter no mínimo zero e no máximo N funcionários.
  - (0,n) e (1,2): um médico atende no mínimo zero e no máximo N pacientes; um paciente é consultado por no mínimo 1 e no máximo 2 médicos.

> [!TIP] DICAS:
> - A cardinalidade mínima zero indica que a participação da entidade no relacionamento é opcional.
> - A cardinalidade máxima N indica que não há limite superior para o número de participações.

## 5. Entidade Fraca
- É um tipo de entidade que não possui identificação própria, ou seja, não tem atributos que a identifiquem de forma única.
- Está sempre associada a uma entidade forte por meio de um relacionamento identificador.
- Exemplo: um funcionário que possui dependentes. Todo dependente, ao ser cadastrado, está automaticamente associado a um funcionário, dependendo dele para existir.
- Características:
  - Dependência de existência e dependência de identificador.
  - Chave primária da entidade fraca é composta pela chave primária da entidade forte mais sua chave parcial própria.
  - Exemplo prático: ao cadastrar um dependente, o CPF do funcionário ao qual ele está relacionado também é registrado, compondo a chave primária.

## 6. Atributo de Relacionamento
- É um atributo cujo valor é determinado pela combinação das entidades participantes em uma instância do relacionamento.
- Exemplo: em um relacionamento entre Médico, Paciente e Consulta, o atributo "Data" pertence ao relacionamento, pois sua existência depende da instância específica da consulta.
- Detalhe importante: a data deve fazer parte da chave do relacionamento. Caso contrário, poderá haver conflito de chave primária, pois um mesmo médico poderia realizar várias consultas com o mesmo paciente em datas diferentes.

> [!CAUTION] OBSERVAÇÃO:
> - O professor ressalta que, em muitos sistemas, atributos como CRM e CPF são chaves primárias, mas a data também deve ser incorporada à chave para garantir a unicidade do registro de consultas.

## 7. Notação James Martin
- Essa notação é uma alternativa ao diagrama entidade-relacionamento tradicional, com as seguintes características:
  - Relacionamentos são representados por linhas entre as entidades.
  - Apenas relacionamentos binários são permitidos (não suporta ternários).
  - A cardinalidade é representada de forma gráfica:
    - O símbolo mais próximo do retângulo (entidade) indica a cardinalidade máxima.
    - O símbolo mais distante indica a cardinalidade mínima.
- Exemplo de leitura: o empregado deve fazer parte de no mínimo 1 e no máximo 1 departamento; um departamento pode ter muitos empregados ou nenhum empregado.

> [!TIP] DICAS:
> - Essa notação é cobrada em concursos, especialmente para interpretação de diagramas e cardinalidade. Fique atento à posição dos símbolos para identificar corretamente as cardinalidades mínima e máxima.

## 8. Considerações Finais para Provas
- A implementação de relacionamentos muitos-para-muitos (M:N) exige a criação de uma terceira tabela (tabela de associação) com chave composta, formada pelas chaves primárias das duas tabelas envolvidas.
- Essa regra é essencial para a correta normalização e funcionamento do banco de dados relacional.

> [!TIP] DICAS:
> - Em questões de concurso, sempre verifique se a alternativa menciona a criação de uma nova tabela para o relacionamento M:N.
> - A chave primária dessa nova tabela é composta pelas chaves primárias das entidades participantes, garantindo a unicidade de cada associação.