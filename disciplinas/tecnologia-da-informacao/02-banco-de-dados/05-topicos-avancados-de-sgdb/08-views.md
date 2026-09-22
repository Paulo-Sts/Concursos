# Views

## 1. Conceito e Definição de Visões
- Uma visão (view), na terminologia SQL, pode ser definida como uma relação única que é derivada de outras tabelas ou visões previamente definidas.
- A view é uma ferramenta utilizada para reforçar a segurança em bancos de dados, permitindo ocultar partes das tabelas e restringir o acesso a determinadas informações.
- Por meio dela, é possível criar visões específicas que podem ser acessadas pelos usuários conforme suas permissões.
- Uma view não existe necessariamente na forma física – ela é considerada uma tabela virtual.
- As tabelas utilizadas na definição da visão são chamadas de tabelas definidoras de visão.
- Quando é definida uma view, o SGBD armazena a definição da view propriamente dita, em vez do resultado (result set) da consulta.
- Sempre que a view aparece em uma consulta, ela é substituída pela expressão da consulta armazenada.
- Uma visão sempre está atualizada. Se modificarmos as tuplas nas tabelas definidoras da view, a view deve refletir automaticamente tais alterações.

### 1.1 Operações em Views
- Há limitação em relação às operações de atualização (DML) que podem ser aplicadas.
- Não há limitação em relação às operações de consulta (SELECT).

### 1.2 Sintaxe de Criação e Remoção
- A definição de uma view em SQL é feita através do comando `create view`:
  ```sql
  CREATE VIEW V AS <EXPRESSÃO DE CONSULTA>
  ```
  - «expressão de consulta» é qualquer expressão de consulta SQL válida;
  - O nome da view é representado por v.
- Para remover uma view, utiliza-se o comando:
  ```sql
  DROP VIEW <NOME DA VIEW>
  ```

> [!TIP] DICAS: 
> - A view não armazena dados, apenas a definição da consulta.
> - Como é uma tabela virtual, seu conteúdo é sempre o resultado da execução da consulta no momento do acesso.

## 2. Criação de Views a Partir de uma Tabela
- É possível criar uma view utilizando os nomes de campos da tabela original ou renomeando-os.

### 2.1 Exemplo: Produtos com Estoque Zerado
- Tabela base: Produtos

| NOME_PROD | NOME_CATEG | NÍVEL_ESTOQUE | UNID |
|-----------|------------|---------------|------|
| Café | Mercearia | 10 | KG |
| Açúcar | Mercearia | 05 | KG |
| Sabão em Pó | Limpeza | 0 | KG |
| Vinho | Bebidas | 8750 | ML |
| Refrigerante | Bebidas | 122 | L |

- Consulta SQL para selecionar os produtos com estoque zerado:
  ```sql
  SELECT NOME_PROD, NOME_CATEG, NÍVEL_ESTOQUE, UNID
  FROM PRODUTO
  WHERE NÍVEL_ESTOQUE=0;
  ```

#### 2.1.1 Usando os Nomes dos Campos da Tabela
- Criação da view:
  ```sql
  CREATE VIEW vw_estoque_zerado AS
  SELECT nome_prod, nome_categ, nível_estoque, unid
  FROM produto
  WHERE nível_estoque=0;
  ```

#### 2.1.2 Alterando os Nomes dos Campos
- É possível criar uma view renomeando os campos da tabela, conforme o padrão SQL.
- Exemplo:
  ```sql
  CREATE VIEW vw_estoque_zerado (produto, categoria, estoque, unidade) AS
  SELECT nome_prod, nome_categ, nível_estoque, unid
  FROM produto
  WHERE nível_estoque=0;
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - No Oracle, especialmente no caso das views materializadas, existem algumas diferenças em relação à sintaxe de renomeação de campos. A view materializada é uma cópia física dos dados, não se limitando a uma simples consulta armazenada, sendo indicada para cenários em que há problemas de desempenho.

## 3. Criação de Views a Partir de Outra View
- Exemplo: Criar uma view dos produtos de limpeza com estoque zerado:
  ```sql
  CREATE VIEW vw_estoque_zerado_limpeza AS
  SELECT nome_prod, nome_categ, nível_estoque, unid
  FROM vw_estoque_zerado
  WHERE nome_categ = 'LIMPEZA';
  ```

## 4. Criação de Views com Filtros (Exemplo: Transações Suspeitas)
- Tabela base: Transações

| NOME | DT_TR | VAL_TR | TP_TR |
|------|-------|--------|-------|
| João | 10/01 | R$ 2.000,00 | C |
| Maria | 10/01 | R$ 250.000,00 | C |
| João | 15/01 | R$ 150,00 | D |
| João | 15/01 | R$ 580.000,00 | D |
| Maria | 15/01 | R$ 300,00 | C |
| Renata | 10/01 | R$ 600.000,00 | D |
| Marcos | 15/01 | R$ 550,00 | C |
| Miguel | 15/01 | R$ 1.800.000,00 | C |
| Renata | 20/01 | R$ 250.000,00 | D |
| Marcos | 20/01 | R$ 45,00 | C |
| Miguel | 22/01 | R$ 35,00 | C |

- Criação de uma view para clientes com saques suspeitos (acima de R$ 200K):
  ```sql
  CREATE VIEW vw_transacoes_suspeitas AS
  SELECT nome, dt_tr, val_tr, tp_tr
  FROM transacoes
  WHERE valor>200000 and tipo = 'D';
  ```
- Ou com renomeação de campos:
  ```sql
  CREATE VIEW vw_transacoes_suspeitas (cliente, data, valor, tipo) AS
  SELECT nome, dt_tr, val_tr, tp_tr
  FROM transacoes
  WHERE valor>200000 and tipo = 'D';
  ```

- Consulta sobre a view para saques suspeitos no dia 15/01:
  ```sql
  SELECT cliente, valor
  FROM vw_transacoes_suspeitas
  WHERE data='15/01';
  ```

## 5. Criação de Views a Partir de Várias Tabelas (Junção)
- Tabelas base: Empréstimo e Tomador

| NUM_EMP | NUM_AGENCIA | VALOR |
|---------|-------------|-------|
| e15 | Asa Sul | R$ 2.000 |
| e16 | Asa Norte | R$ 5.000 |
| e17 | Águas Claras | R$ 4.000 |
| e18 | Asa Sul | R$ 7.000 |
| e19 | Lago Sul | R$ 6.000 |

| NOME_CLIENTE | NUM_EMP |
|--------------|---------|
| João | e15 |
| Maria | e16 |
| Marcos | e17 |
| João | e18 |
| Maria | e19 |

- Criação da view com junção entre as duas tabelas:
  ```sql
  CREATE VIEW vw_info_emprestimo AS
  SELECT nome_cliente, valor
  FROM emprestimo, tomador
  WHERE tomador.num_emp = emprestimo.num_emp;
  ```
- Consulta filtrando por valor maior que 5000:
  ```sql
  SELECT * FROM vw_info_emprestimo
  WHERE valor > 5000;
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - Quando é realizado um SELECT envolvendo duas tabelas sem uma condição explícita de junção, ocorre um cruzamento de dados (produto cartesiano). Esse processo tende a ser menos performático, pois força o cruzamento completo entre os registros das tabelas.

## 6. Atualização de Views (DML)
- A atualização de views representa a atualização das tabelas definidoras da view a partir de comandos DML na própria view (update, insert e delete).
- Embora seja algo possível, a atualização de views pode acarretar diversos problemas de consistência de dados.

### 6.1 Problemas com Insert em Views
- Ao criar uma view, é possível ocultar determinados campos da tabela original.
- Ao realizar um comando de INSERT sobre essa view, os campos ocultos não são atualizados, o que pode gerar problemas de consistência nos dados (ex: campos obrigatórios que ficam com valor nulo).
- Exemplo com a tabela Produtos:

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Café | Mercearia | R$ 7,90 | KG |
| Açúcar | Mercearia | R$ 5,90 | 5 KG |
| Sabão em Pó | Limpeza | R$ 9,90 | KG |
| Vinho | Bebidas | R$ 79,90 | 750 ML |
| Refrigerante | Bebidas | R$ 6,90 | 2 L |

- Criação de uma view que oculta o campo PREÇO:
  ```sql
  CREATE VIEW vw_produto_bebida AS
  SELECT produto, categoria, unidade
  FROM produto WHERE categoria = 'BEBIDAS';
  ```
- Inserção de um novo produto via view:
  ```sql
  INSERT INTO vw_produto_bebida
  VALUES ('SUCO DE UVA', 'BEBIDAS', '1L');
  ```
- Resultado na tabela Produtos:

| NOME | CATEGORIA | PREÇO | UNIDADE |
|------|-----------|-------|---------|
| Café | Mercearia | R$ 7,90 | KG |
| Açúcar | Mercearia | R$ 5,90 | 5 KG |
| Sabão em Pó | Limpeza | R$ 9,90 | KG |
| Vinho | Bebidas | R$ 79,90 | 750 ML |
| Refrigerante | Bebidas | R$ 6,90 | 2 L |
| Suco de Uva | Bebidas | Null | 1L |

- Observa-se que o campo PREÇO ficou com valor nulo, o que pode ser um problema de consistência.

### 6.2 Views com Junção (Múltiplas Tabelas)
- Na prática, quando uma view envolve mais de uma tabela com JOINs ou resulta em um produto cartesiano, não é possível realizar inserções por meio dela.
- Exemplo de tentativa de insert em uma view com junção:
  ```sql
  INSERT INTO vw_info_emprestimo
  VALUES ('Renata', 5000);
  ```
- Neste caso, a operação falha ou gera inconsistências, pois os dados precisariam ser inseridos em duas tabelas simultaneamente (Empréstimo e Tomador).
- Resultado inconsistente na tabela Empréstimo:

| NUM_EMP | NUM_AGENCIA | VALOR |
|---------|-------------|-------|
| e15 | Asa Sul | R$ 2.000 |
| e16 | Asa Norte | R$ 5.000 |
| e17 | Águas Claras | R$ 4.000 |
| e18 | Asa Sul | R$ 7.000 |
| e19 | Lago Sul | R$ 6.000 |
| Null | Null | R$ 5.000 |

- Resultado inconsistente na tabela Tomador:

| NOME_CLIENTE | NUM_EMP |
|--------------|---------|
| João | e15 |
| Maria | e16 |
| Marcos | e17 |
| João | e18 |
| Maria | e19 |
| Renata | Null |

> [!CAUTION] OBSERVAÇÃO: 
> - A atualização de dados por meio de uma view só é viável quando ela representa integralmente uma única tabela (view simples), permitindo a execução do comando INSERT, desde que sejam respeitadas as regras do banco de dados.

### 6.3 With Check Option
- As Views podem ser definidas com uma cláusula `WITH CHECK OPTION` no final da definição da view.
- Dessa forma, se uma tupla inserida na view não satisfizer a condição da cláusula WHERE da view, a inserção é rejeitada pelo SGBD.
- Exemplo:
  ```sql
  CREATE VIEW vw_produto_bebida AS
  SELECT produto, categoria, unidade
  FROM produto WHERE categoria='BEBIDAS'
  WITH CHECK OPTION;
  ```

### 6.4 Condições para uma View Ser Atualizável
- Uma View é atualizável se:
  - A PK ou outra chave candidata estiver presente na lista de atributos;
  - A cláusula FROM possui apenas uma relação;
  - A cláusula SELECT possui apenas atributos da relação. Não possui expressões, agregadas ou especificação distinct;
  - Os atributos não listados na view podem ser definidos como nulos;
  - A consulta não possui cláusula group by ou having.
- O comando INSERT não é permitido quando a view utiliza cláusulas como GROUP BY, pois, nesse caso, os dados apresentados resultam de agregações e não correspondem diretamente aos registros da tabela original.

- Não são atualizáveis:
  - Views definidas em múltiplas tabelas (Joins);
  - Views com uso de funções de agregação.

### 6.5 Tipos de Views
- View Simples: Uma view simples recupera linhas de uma única tabela base, não contém funções grupo e pode aceitar operações DML.
- Exemplo:
```sql
CREATE VIEW vw_funcionario AS
SELECT nome, matricula FROM tfuncionario;
```

- View Complexa: Envolve mais de uma tabela ou funções de agregação. Não pode aceitar operações DML.
- Exemplo:
```sql
CREATE VIEW vw_funcionario AS
SELECT nome, matricula, nomeDepartamento
FROM tfuncionario E, tdepartamento D
WHERE D.TIDEPARTAMENTO_ID = E.TFUNCTIONARIO_ID;
```

## 7. Views Materializadas
- Alguns SGBDs permitem armazenar as relações resultantes de uma view, de modo que, se as relações reais usadas na definição da view mudarem, a view permaneça atualizada. São chamadas de views materializadas.
- O processo de manter a view atualizada é chamado de manutenção de view.
- Basicamente a diferença é que a view realiza a consulta no momento que o usuário faz uma consulta nela, enquanto a materialized view realiza a consulta no momento em que uma das tabelas consultadas é atualizada (ou em intervalos definidos).
- A decisão de uso de views materializadas envolve a análise de custo-benefício:
  - Tempo de resposta;
  - Custo de Armazenamento e Overhead adicional de atualizações.
- A view materializada não faz parte do padrão SQL, sendo uma extensão implementada por alguns SGBDs.

> [!TIP] DICAS: 
> - Em situações em que as consultas envolvem dados com atualizações constantes e é necessário obter informações em tempo real, o uso de views materializadas deve ser cuidadosamente avaliado devido ao custo de manutenção.

> [!CAUTION] OBSERVAÇÃO: 
> - A view materializada cria uma cópia física dos dados.
> - Diferentemente da view comum, a materialized view não executa a consulta a cada acesso, o que pode melhorar o desempenho, mas exige espaço de armazenamento e processamento para ser mantida atualizada.
> - Cuidado com a confusão: a view comum não armazena dados e sempre consulta as tabelas base. A view materializada armazena os dados, podendo estar desatualizada se não for mantida.