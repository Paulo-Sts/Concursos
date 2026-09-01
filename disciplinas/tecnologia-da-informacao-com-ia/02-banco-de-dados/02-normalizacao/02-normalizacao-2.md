# Banco de Dados - Normalização 2

## 1. Segunda Forma Normal (2FN)
- Uma relação está na segunda forma normal se estiver na primeira forma normal e se todo atributo não chave possuir dependência funcional total em relação à chave primária da relação.
- O problema da 2FN ocorre quando há dependências funcionais parciais, ou seja, atributos não chave que dependem de apenas parte da chave primária composta.
- Exemplo de dependências funcionais parciais em uma tabela de empregados:
  - CodProjeto ⟶ NomeProj;
  - CPF ⟶ NomeEmp.
- Para resolver, deve-se criar tabelas separadas para cada entidade, eliminando as dependências parciais.

### 1.1 Exemplo Prático de 2FN
- Tabela original com problema:
  - ID Aluno;
  - ID Curso;
  - Nome Aluno;
  - Nome Curso;
  - Professor.
- Dependência problemática:
  - Nome Aluno depende apenas de ID Aluno, mas está na mesma tabela que Nome Curso e Professor, que dependem de ID Curso.
- Solução: criar tabelas separadas para alunos e cursos.

### Tabela Original (Não 2FN)
| ID ALUNO | ID CURSO | NOME ALUNO | NOME CURSO | PROFESSOR |
|----------|----------|------------|------------|-----------|

### Tabelas Normalizadas (2FN)
| ID ALUNO | NOME ALUNO |
|----------|------------|

| ID CURSO | NOME CURSO | PROFESSOR |
|----------|------------|-----------|

| ID ALUNO | ID CURSO |
|----------|----------|

## 2. Dependência Funcional Transitiva
- Na dependência funcional transitiva, um atributo C é dependente funcional transitivo de A se:
  - C é funcionalmente dependente de B;
  - B é funcionalmente dependente de A;
  - Todas as dependências ocorrem na mesma relação.
- Essa dependência causa redundância e anomalias na atualização dos dados.

## 3. Terceira Forma Normal (3FN)
- Uma relação está na terceira forma normal se e somente se estiver na segunda forma normal e nenhum atributo não chave for transitivamente dependente da chave.
- O problema da 3FN ocorre quando um atributo não chave depende de outro atributo não chave, que por sua vez depende da chave primária.
- Exemplo de dependência funcional transitiva:
  - NumPedido determina CodVendedor;
  - CodVendedor determina NomeVendedor.
- Solução: criar uma tabela exclusiva para o vendedor, evitando a dependência dupla.

### 3.1 Exemplo Prático de 3FN
- Tabela Pedido com problema de transitividade:
  - NumPedido (chave primária);
  - CodVendedor;
  - NomeVendedor.
- Dependência transitiva:
  - NumPedido ⟶ CodVendedor ⟶ NomeVendedor.
- Solução: separar em duas tabelas, uma para pedidos e outra para vendedores.

## 4. Forma Normal de Boyce Codd (FNBC)
- Uma relação está na Forma Normal de Boyce Codd se, para toda dependência funcional do tipo X ⟶ Y, X é uma superchave.
- A FNBC é mais restritiva que a terceira forma normal e surgiu diante dos casos não resolvidos por essa forma.
- Toda relação que está na FNBC também está na 3FN, mas nem toda relação que está na 3FN está na FNBC.
- Na FNBC, a dependência se dá em relação à superchave, e não somente à chave primária.
- Em alguns casos, é necessário criar outras tabelas para diminuir a quantidade de duplas envolvidas no join e o cruzamento de informações.

### 4.1 Superchave
- Uma superchave SK de uma relação R é um conjunto de atributos de R que identificam unicamente cada tupla da relação.
- Duas tuplas distintas de R não podem possuir o mesmo valor de SK.
- Chave primária é a superchave de cardinalidade mínima, ou seja, com menor número de atributos.

### 4.2 Classificação de Chaves
- Chaves simples: contêm somente um atributo.
- Chaves compostas: contêm mais de um atributo.
- Chaves superpostas: quando pelo menos uma delas é composta e entre elas existe pelo menos um atributo em comum.
- Chaves disjuntas: quando entre elas não existe superposição.

### 4.3 Exemplo Prático de FNBC
- Tabela Leciona, com relação entre alunos, disciplinas e instrutores:
  - Aluno;
  - Disciplina;
  - Instrutor.
- Chave Candidata: {Aluno, Disciplina}.
- Dependências Funcionais:
  - {Aluno, Disciplina} determina Instrutor;
  - Instrutor determina Disciplina.
- Problema: Instrutor determina Disciplina, mas Instrutor não é superchave.
- Solução: dividir a tabela para atender à FNBC.

### Tabela Leciona (Não FNBC)
| ALUNO | DISCIPLINA | INSTRUTOR |
|-------|------------|-----------|

### 4.4 Exemplo de Chaves Superpostas
- Tabela Cliente com as seguintes características:
  - Chave Primária: {Cliente, Agência}.
  - Chave Candidata: {Cliente, Gerente}.
- Dependências funcionais:
  - {Cliente, Agência} ⟶ Gerente;
  - {Cliente, Gerente} ⟶ Agência;
  - Gerente ⟶ Agência.
- Problema: Gerente determina Agência, mas Gerente não é superchave.
- Na FNBC, a tabela deve ser dividida para eliminar essa dependência.

### Tabela Cliente (Não FNBC)
| CLIENTE | AGÊNCIA | GERENTE |
|---------|---------|---------|

> [!CAUTION] OBSERVAÇÃO:
> - A FNBC é menos cobrada pelas bancas em comparação com as demais formas normais.
> - Para simplificar, é possível definir que uma tabela está em FNBC se e somente se todos os determinantes são chaves candidatas.
> - Na FNBC, a dependência se dá em relação ao conjunto de chaves que determinam a relação, e não somente à chave primária.

> [!TIP] DICAS:
> - Para identificar se uma tabela está na 2FN, verifique se existe dependência parcial de atributos não chave em relação à chave primária.
> - Para identificar se uma tabela está na 3FN, verifique se existe dependência transitiva entre atributos não chave.
> - Para identificar se uma tabela está na FNBC, verifique se todos os determinantes são superchaves ou chaves candidatas.
> - A FNBC não deve ser confundida com a quarta forma normal.