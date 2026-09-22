# NoSQL Orientados a Colunas e a Chaves-Valor

## 1. NoSQL Orientado a Colunas
- O modelo orientado a colunas armazena os dados como uma coleção de colunas conhecida como família.
- Diferente dos bancos relacionais, as linhas não precisam ter as mesmas colunas.
- Cada coluna é tratada separadamente (consultada, lida ou agregada de forma independente).
- As colunas que possuem subcolunas são agrupadas em um grande bloco.
- Em bancos tradicionais, um endereço estaria em uma tabela separada com chave estrangeira, enquanto no NoSQL orientado a colunas há uma única tabela com colunas subdivididas.

### 1.1 Aplicações Recomendadas
- O modelo orientado a colunas é recomendado para:
  - Business Intelligence (BI);
  - Analytics;
  - Processamento de Big Data.

### 1.2 Apache Cassandra
- É um sistema open-source criado originalmente para o Facebook.
- Utiliza pares de chave-valor e tabelas.
- As linhas de uma tabela (ou família de colunas) podem conter uma quantidade variável de colunas.
- Utiliza a Cassandra Query Language (CQL) como linguagem de consulta.
- O shell para executar comandos CQL é o cqlsh, que funciona como interface do SGBD.

### 1.3 Cassandra Query Language (CQL)
- Tabelas possuem esquemas definidos.
- Tabelas estão localizadas em keyspaces.
- Keyspaces possuem opções que são aplicadas a todas as tabelas contidas nele.

#### 1.3.1 Comandos para Keyspace
- Para criar um keyspace: `CREATE KEYSPACE nome_keyspace`
- Para selecionar: `USE KEYSPACE nome_keyspace`
- Para alterar: `ALTER KEYSPACE nome_keyspace`
- Para apagar: `DROP KEYSPACE nome_keyspace`

#### 1.3.2 Consultas Básicas
- O comando SELECT é utilizado para recuperar resultados dentro da tabela.
- É possível retornar o formato JSON utilizando comandos específicos.
- O WHERE restringe a consulta a critérios específicos.
- É permitido realizar operações de comparação (maior/menor) em colunas de data.
- A função COUNT(*) conta a quantidade total de registros em uma tabela.

> [!TIP] DICAS: 
> - O Cassandra é considerado flexível justamente porque permite alterações no esquema a qualquer momento, diferentemente dos bancos relacionais tradicionais.
> - No Cassandra, o Keyspace equivale ao "esquema" (base de dados) de um banco relacional, contendo as tabelas em seu interior.

### 1.4 Tipos Definidos pelo Usuário (UDTs)
- O Cassandra permite a criação de tipos personalizados pelo desenvolvedor, chamados de User Defined Types (UDTs).
- Esses tipos são criados com o comando: CREATE TYPE.
- Um exemplo de UDT para endereço seria: `CREATE TYPE endereco (rua text, cidade text, num int, complemento text)`.

## 2. NoSQL Orientado a Chave-Valor
- Cada item do banco de dados é armazenado como um par de chave e valor.
- A estrutura básica é uma tabela com duas colunas: uma para a chave e outra para o valor.
- O valor pode ser de qualquer tipo: número, texto, imagem, documento, entre outros.
- Este modelo é considerado schema-less, ou seja, não possui esquema rígido.
- Utiliza uma tabela hash com chaves únicas apontando para cada valor.

### 2.1 Exemplo de Funcionamento
| CHAVE | VALOR |
|-------|-------|
| 123   | R$ 1.000,00 |
| 456   | R$ 2.500,00 |
| 789   | R$ 3.200,00 |

- No exemplo, cada CPF (chave) possui um valor de dinheiro associado (valor).
- Cada item do banco de dados é representado por um par chave-valor.

### 2.2 Aplicações Recomendadas
- O modelo chave-valor é recomendado para:
  - Acelerar a performance de aplicativos com cache;
  - Armazenar dados pessoais de usuários;
  - Gerenciar sessões em jogos online;
  - Implementar dicionários e coleções.

### 2.3 Características de Consistência
- A consistência em bancos chave-valor é aplicável apenas às operações em uma única chave.
- As operações possíveis são obtenção, gravação ou exclusão em uma única chave.
- A garantia de consistência fica restrita à operação na chave específica, não abrangendo o banco como um todo.

> [!CAUTION] OBSERVAÇÃO: 
> - Bancos de dados orientados a chave-valor são estruturalmente simples: uma chave e um valor associado.
> - Não há chave multidimensional no modelo chave-valor puro, pois a chave é unidimensional e direta.
> - Do ponto de vista de API, o banco chave-valor é o mais fácil de utilizar, sendo considerado equivalente a uma tabela hash simples.