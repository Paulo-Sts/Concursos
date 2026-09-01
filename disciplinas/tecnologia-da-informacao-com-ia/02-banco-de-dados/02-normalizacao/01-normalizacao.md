# Banco de Dados - Normalização

## 1. Normalização
- Conjunto de técnicas aplicáveis a uma tabela para corrigir erros de projeto que resultam em anomalias de atualização.
- Processo consiste em analisar a relação para satisfazer requisitos cada vez mais rigorosos, por meio de formas normais mais elevadas.
- Objetivo principal: decomposição de esquemas para evitar anomalias de atualização (inclusão, exclusão e modificação).

## 2. Anomalias de Atualização
- Problemas decorrentes da implementação de bancos de dados não normalizados, com redundância de dados nas colunas das tabelas e dependências parciais e transitivas.
- Classificadas em três tipos:
  - Anomalias de inserção;
  - Anomalias de exclusão;
  - Anomalias de modificação.

> [!CAUTION] OBSERVAÇÃO: 
> - As anomalias de atualização ocorrem quando um projeto conceitual é transformado diretamente em uma tabela sem passar pelo processo de normalização.
> - A Segunda Forma Normal (2FN) elimina as dependências parciais.
> - A Terceira Forma Normal (3FN) elimina as dependências transitivas.

### 2.1 Anomalias de Inserção
- Ao incluir um registro, exige-se informações relativas a outra tabela.
- Exemplo: ao incluir um novo empregado, é necessário incluir todas as informações do departamento em que ele está alocado ou incluir valores nulos.

### 2.2 Anomalias de Exclusão
- Ao excluir um registro, dados relacionados a outra tabela também são excluídos.
- Exemplo: ao excluir a empregada Juliana, perdem-se todas as informações do Departamento Jurídico.

### 2.3 Anomalias de Modificação
- Ao alterar um dado em uma tabela, é preciso alterar as informações relacionadas em diversos outros registros da mesma tabela.
- Exemplo: ao alterar a sigla do departamento do empregado com CPF = 22, deve-se alterar também a sigla do departamento do empregado com CPF = 55.

## 3. Primeira Forma Normal (1FN)
- Definição formal de uma relação.
- A relação não pode conter atributos multivalorados, atributos compostos ou suas combinações.
- Uma relação R está na 1FN se não possuir grupos de repetição.
- Definição: uma relação está em 1FN se e somente se todos os seus atributos contêm apenas valores atômicos (simples e indivisíveis).

> [!TIP] DICAS: 
> - Durante o mapeamento do modelo entidade-relacionamento para o modelo relacional, é possível representar atributos multivalorados na fase conceitual, pois a notação do modelo entidade-relacionamento permite esse tipo de atributo.
> - Se o usuário deixar o atributo multivalorado, este será eliminado pela Primeira Forma Normal.

### 3.1 Exemplo de Atributo Multivalorado
- Tabela com localização multivalorada (departamento pode estar em mais de uma localidade):

| CODIGO | NOME | SIGLA | LOCALIZACAO |
|--------|------|-------|-------------|
| 1 | Financeiro | FIN | São Paulo, Rio de Janeiro |
| 2 | Tecnologia da Informação | TI | Salvador, Belo Horizonte |
| 3 | Recursos Humanos | RH | Recife, Vitória |
| 4 | Qualidade | QUA | Brasília |
| 5 | Auditoria | AUD | Porto Alegre |

### 3.2 Relação Após Aplicação da 1FN
- Para eliminar o atributo multivalorado, cria-se uma tabela separada para as localizações.

Tabela Departamento:  

| CODIGO | NOME | SIGLA |
|--------|------|-------|
| 1 | Financeiro | FIN |
| 2 | Tecnologia da Informação | TI |
| 3 | Recursos Humanos | RH |
| 4 | Qualidade | QUA |
| 5 | Auditoria | AUD |

Tabela Localização:  

| CODIGO | LOCALIZACAO |
|--------|-------------|
| 1 | São Paulo |
| 1 | Rio de Janeiro |
| 2 | Salvador |
| 2 | Belo Horizonte |
| 3 | Recife |
| 3 | Vitória |
| 4 | Brasília |
| 5 | Porto Alegre |

> [!CAUTION] OBSERVAÇÃO: 
> - As Formas Normais são restrições aplicadas com o objetivo de evitar inconsistências.
> - Após a aplicação da Primeira Forma Normal, constroem-se tabelas separadas para cada atributo multivalorado.

## 4. Dependência Funcional
- Pré-requisito para a 2FN e 3FN.
- A dependência funcional evita redundância de dados, inconsistências e perda de dados em operações de remoção ou alteração.
- Notação: X → Y (Y depende funcionalmente de X; ou X determina funcionalmente Y).

### 4.1 Tipos de Dependência Funcional
- Dependência Funcional Total;
- Dependência Funcional Parcial;
- Dependência Funcional Transitiva.

### 4.2 Dependência Funcional Total
- Em uma tabela relacional, uma coluna Y depende funcionalmente de uma coluna X quando, em todas as tuplas da tabela, para cada valor na coluna X, ocorre o mesmo valor na coluna Y.
- Está vinculada à semântica dos atributos do modelo de dados.
- Exemplo:

| CPF | NOME | DATANASCIMENTO |
|-----|------|----------------|
| 11 | João Pereira | 10/01/1980 |
| 22 | Ana de Carvalho | 01/01/1994 |
| 33 | Marta Ferreira | 05/01/1987 |
| 44 | Marcelo Albuquerque | 02/02/1982 |
| 55 | Maria da Silva | 10/01/1980 |
| 66 | Marcos Augusto | 02/02/1982 |
| 77 | Ana de Carvalho | 05/05/1990 |

  - Dependências funcionais identificadas:  
    - CPF → Nome (o CPF determina o Nome);
    - CPF → DataNascimento (o CPF determina a Data de Nascimento);
    - Nome não determina CPF;
    - DataNascimento não determina CPF.

### 4.3 Exemplo com Chave Composta
- Tabela Empregado_Projeto:  

| CPF | NOME | CODPROJ | NOMEPROJ | HORAS |
|-----|------|---------|----------|-------|
| 11 | João Pereira | 001 | Rodovia | 15 |
| 22 | Ana de Carvalho | 001 | Rodovia | 20 |
| 33 | Marta Ferreira | 001 | Rodovia | 10 |
| 11 | Marcelo Albuquerque | 002 | Ponte | 25 |
| 22 | Maria da Silva | 002 | Ponte | 20 |
| 33 | Marcos Augusto | 002 | Ponte | 30 |

  - Dependências funcionais:
    - DF1: CPF → Nome (o CPF determina o Nome);
    - DF2: CodProj → NomeProj (o Código do Projeto determina o Nome do Projeto);
    - DF3: {CPF, CodProj} → NomeProj (o CPF e o Código do Projeto determinam o Nome do Projeto).

### 4.4 Dependência Funcional Parcial
- Os atributos não chave de uma tabela dependem funcionalmente de parte da chave primária.
- Exemplo:
  - CPF → Nome (dependência parcial em relação à chave {CPF, CodProj});
  - Somente é possível determinar as horas por meio do CPF e do Código do Projeto, logo: {CPF, CodProj} → Horas.

> [!CAUTION] OBSERVAÇÃO: 
> - A dependência funcional parcial ocorre quando um atributo não chave depende de apenas uma parte da chave primária composta.
> - A dependência funcional parcial é eliminada pela Segunda Forma Normal.