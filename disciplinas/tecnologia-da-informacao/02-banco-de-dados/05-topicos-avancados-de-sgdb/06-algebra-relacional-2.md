# Álgebra Relacional 2

## 1. Operadores De Teoria Dos Conjuntos
- São operações binárias que incorporam elementos de duas relações, baseando-se nos conceitos da teoria de conjuntos.
- As operações mais cobradas em concursos são: união, interseção e diferença.

### 1.1 União
- O resultado da operação de união, representada por R U S, é uma relação que inclui todas as tuplas que estão em R ou estão em S, ou em ambos.
- Tuplas duplicadas são eliminadas.
- Exemplo: Listar o nome e a idade de todos os alunos e professores.
- Explicação: A operação combina os dados de duas relações (professores e alunos). Se houvesse registros com o mesmo nome e idade em ambas as tabelas, eles seriam eliminados no resultado final.
- O comportamento difere do comando `UNION ALL` no SQL, que mantém os registros repetidos.

### 1.2 Interseção
- O resultado da operação de interseção, representada por R ∩ S, é uma relação que inclui todas as tuplas que estão tanto em R quanto em S.
- É necessária uma compatibilidade de atributos para identificar registros coincidentes.
- Exemplo: Listar os alunos e professores que possuem o mesmo nome e sobrenome.
- Explicação: A interseção encontra os elementos comuns entre dois conjuntos. Em termos de resultado, apresenta comportamento semelhante ao da operação `JOIN`, pois seleciona os dados coincidentes entre duas relações.

### 1.3 Diferença
- O resultado da operação de diferença, representada por R – S, é uma relação que inclui todas as tuplas que estão em R, mas não estão em S.
- A ordem dos conjuntos afeta diretamente o resultado da operação.
- Exemplo: Listar os alunos que não tenham nome e sobrenome iguais aos de algum professor.
- Explicação: Ao aplicar “aluno menos professor”, o resultado conterá todos os alunos, exceto aqueles que também são professores. Se a ordem for invertida (“professor menos aluno”), o resultado trará todos os professores, exceto os que também são alunos.

> [!CAUTION] OBSERVAÇÃO: 
> - A ordem dos conjuntos na operação de diferença altera o resultado final. É um ponto de atenção comum em provas.

## 2. Produto Cartesiano
- O produto cartesiano, também chamado de produto cruzado (cross product) ou junção cruzada (cross join), é representado por X.
- É uma operação binária que combina tuplas de duas relações de forma combinatória.
- Cada tupla de uma relação é combinada com todas as tuplas da outra relação, gerando tuplas com os atributos de ambas.
- Representação: P = R (R1, R2,…, RN) X S (S1, S2,…, SM), resultando em uma relação P com os atributos (R1, R2,…, RN, S1, S2,…, SM).
- Explicação: Cada registro da primeira relação é emparelhado com todos os registros da segunda relação.
- Esse processo gera "tuplas falsas", ou seja, combinações de dados que não possuem correspondência lógica.
- Para que o banco de dados identifique registros com correspondência real, é necessário aplicar operações de junção.
- Em SQL, a operação `SELECT * FROM tabela1, tabela2` corresponde diretamente ao produto cartesiano.

> [!CAUTION] OBSERVAÇÃO: 
> - O produto cartesiano gera muitas combinações, incluindo as que não fazem sentido (tuplas falsas). Ele é a base para a operação de junção.

## 3. Operador De Junção
- A operação de junção, representada por |X|, é utilizada para combinar tuplas relacionadas de duas relações em uma única tupla.
- É um operador binário que combina as operações de produto cartesiano e seleção.
- A condição de junção define quais combinações são válidas.
- Exemplo: `FUNC_DEP ← Funcionário X Departamento` e `σCOD=COD_DEP (FUNC_DEP)`.
- A forma de representar uma junção é `R |X| <condição de junção> S`.
- Explicação: A junção filtra o produto cartesiano, mantendo apenas as tuplas com correspondência nas chaves (ex: código do funcionário = código do departamento), gerando apenas combinações válidas.
- A operação `JOIN` em SQL é considerada custosa em termos de desempenho, pois se baseia na execução de um produto cartesiano seguido de uma seleção, embora os SGBDs otimizem sua execução, sendo mais eficiente que a abordagem manual de `SELECT FROM` com `WHERE`.

### 3.1 Desempenho e Aplicação
- A aplicação do `INNER JOIN` é otimizada pelo SGBD, resultando em um desempenho prático superior ao uso de produto cartesiano seguido de seleção, especialmente em tabelas com grande volume de registros.
- Embora o resultado teórico na álgebra relacional seja o mesmo, a performance prática difere significativamente.

> [!TIP] DICAS: 
> - A junção é o uso prático do produto cartesiano. Toda junção começa com um produto cartesiano e aplica uma seleção.

### Tabela
| NOME | COD_DEP |
|------|---------|
| Pedro | 1 |
| Henrique | 1 |
| Artur | 2 |
| Cecilia | 3 |

| COD | SIGLA |
|-----|-------|
| 1 | TI |
| 2 | JUR |
| 3 | FIN |

| NOME_F | COD_DEP | COD | SIGLA |
|--------|---------|-----|-------|
| Pedro | 1 | 1 | TI |
| Henrique | 1 | 1 | TI |
| Artur | 2 | 2 | JUR |
| Cecilia | 3 | 3 | FIN |

## 4. Simbologia Da Álgebra Relacional
- É essencial conhecer os símbolos principais, pois são frequentemente cobrados em concursos.
- π (pi): Representa a operação de projeção. Utilizada para selecionar colunas específicas de uma relação. Em SQL, corresponde ao `SELECT` de atributos (ex: `SELECT C FROM S`).
- σ (sigma): Representa a operação de seleção. Utilizada para filtrar tuplas com base em uma condição. Em SQL, corresponde à cláusula `WHERE`.
- A operação de renomeação (rename) é representada por uma seta (⟶) e é utilizada para dar um novo nome a uma relação ou atributo.

> [!CAUTION] OBSERVAÇÃO: 
> - Apesar da palavra "SELECT" no SQL, na álgebra relacional, o "SELECT" (com `WHERE`) é uma operação de seleção (σ), enquanto a projeção (π) é a escolha das colunas.

## 5. Classificação Das Operações
- As operações na álgebra relacional podem ser classificadas quanto ao número de relações sobre as quais atuam.
- Unárias: Operam sobre uma única relação.
  - Projeção (π);
  - Seleção (σ).
- Binárias: Operam sobre duas relações.
  - União (U);
  - Interseção (∩);
  - Diferença (-);
  - Produto Cartesiano (X);
  - Junção (|X|).

## 6. Conceitos Chave Sobre Operações
- Projeção: Produz uma nova relação com alguns dos atributos da relação original. O número de tuplas resultantes é sempre igual ou menor que o número original, pois a projeção elimina duplicatas.
- União: Retorna o conjunto de tuplas presentes em R ou S ou em ambas. Duplicatas são eliminadas.
- Junção: Produz todas as combinações de tuplas, de duas relações, que satisfazem a condição de junção.
- Produto Cartesiano: Combina toda tupla de R com toda tupla de S, resultando em uma relação com todas as combinações possíveis.