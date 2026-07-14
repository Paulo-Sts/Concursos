# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO – ÁLGEBRA RELACIONAL II

## 1. OPERADORES DA TEORIA DOS CONJUNTOS

### 1.1 UNIÃO (U)

- O resultado da operação **R U S** é uma relação que inclui todas as tuplas que estão em R ou estão em S, ou em ambos R e S.

- **Tuplas duplicadas são eliminadas.**

- Difere do comando **UNION ALL** no SQL, que mantém os registros repetidos.

**Exemplo:**

| Professor | | Aluno | |
|-----------|---------|--------|---------|
| Nome | Idade | Nome | Idade |
| João | 50 | Pedro | 12 |
| Mateus | 35 | Henrique | 10 |
| Renata | 28 | Artur | 8 |
| Marcelo | 44 | Cecilia | 9 |

**Professor U Aluno:**

| Nome | Idade |
|------|-------|
| João | 50 |
| Mateus | 35 |
| Renata | 28 |
| Marcelo | 44 |
| Pedro | 12 |
| Henrique | 10 |
| Artur | 8 |
| Cecilia | 9 |

### 1.2 INTERSEÇÃO (∩)

- O resultado da operação **R ∩ S** é uma relação que inclui todas as tuplas que estão **tanto em R quanto em S**.

- Retorna apenas os elementos comuns entre dois conjuntos.

**Exemplo:**

| Professor | | Aluno | |
|-----------|---------|--------|---------|
| Nome | Sobrenome | Nome | Sobrenome |
| João | Pereira | Pedro | Silva |
| Mateus | Souza | Marcelo | Martins |
| Renata | Jardim | Artur | Aguiar |
| Marcelo | Martins | Cecilia | Alves |

**Professor ∩ Aluno:**

| Nome | Sobrenome |
|------|-----------|
| Marcelo | Martins |

> ### 1.3 Comparação entre INTERSEÇÃO e JUNÇÃO
> - A interseção apresenta comportamento semelhante ao da operação **JOIN**, pois também seleciona os dados coincidentes entre duas relações.
> - A diferença é que a interseção exige que os esquemas das relações sejam compatíveis (mesmos atributos), enquanto a junção pode atuar sobre atributos diferentes com condição de igualdade.

### 1.4 DIFERENÇA (–)

- O resultado da operação **R – S** é uma relação que inclui todas as tuplas que estão em R, **mas não estão em S**.

- **A ordem dos conjuntos afeta diretamente o resultado.**

**Exemplo:**

**Aluno – Professor** (alunos que não são professores):

| Nome | Sobrenome |
|------|-----------|
| Pedro | Silva |
| Artur | Aguiar |
| Cecilia | Alves |

**Professor – Aluno** (professores que não são alunos):

| Nome | Sobrenome |
|------|-----------|
| João | Pereira |
| Mateus | Souza |
| Renata | Jardim |

## 2. PRODUTO CARTESIANO (X)

- Também chamado de **PRODUTO CRUZADO** (*CROSS PRODUCT*) ou **JUNÇÃO CRUZADA** (*CROSS JOIN*).

- Combina tuplas de duas relações de forma **combinatória**.

- Cada tupla de uma relação será combinada com **todas** as tuplas da outra relação.

- Representação: **P = R (R1, R2, ..., RN) X S (S1, S2, ..., SM)**

- A relação resultante P possui os atributos de R e S: **P (R1, R2, ..., RN, S1, S2, ..., SM)**

### 2.1 Tuplas Falsas

- O produto cartesiano gera o que se denomina **tuplas falsas** — combinações de dados que não possuem correspondência lógica.

- Exemplo: se um funcionário trabalha no departamento TI, a combinação "Pedro - Jurídico" é uma tupla falsa.

- Para que um banco de dados relacional identifique registros com correspondência entre diferentes relações, torna-se necessário aplicar operações de **junção**.

- O **JOIN** em SQL é considerado custoso em termos de desempenho, pois se baseia, essencialmente, na execução de um **produto cartesiano seguido de uma seleção**.

> ### 2.2 Performance no SQL
> - `SELECT * FROM tabela1, tabela2` → produto cartesiano
> - Adicionar `WHERE` comparando chaves → seleção sobre o produto cartesiano
> - **INNER JOIN** é otimizado pelo SGBD, que reconhece chaves primárias e realiza a junção de forma mais eficiente.
> - Do ponto de vista teórico, o resultado é o mesmo; na prática, o desempenho difere significativamente com grandes volumes de dados.

## 3. OPERADOR DE JUNÇÃO – JOIN (⋈)

- Utilizado para combinar tuplas relacionadas de duas relações em uma única tupla.

- É um operador **binário**.

- A operação de **JOIN** é uma combinação das operações **PRODUTO CARTESIANO e SELEÇÃO**:

  **R ⋈ <condição de junção> S**

- Representação alternativa:

  1. FUNC_DEP ← Funcionário X Departamento
  2. σ COD = COD_DEP (FUNC_DEP)

- A junção é, portanto, um produto cartesiano acrescido de uma seleção.

**Exemplo:**

| Funcionário | | Departamento | |
|-------------|------|--------------|-----|
| Nome | Cod_Dep | Cod | Sigla |
| Pedro | 1 | 1 | TI |
| Henrique | 1 | 2 | JUR |
| Artur | 2 | 3 | FIN |
| Cecilia | 3 | | |

**Funcionário ⋈ Cod = Cod_Dep Departamento:**

| Nome | Cod_Dep | Cod | Sigla |
|------|---------|-----|-------|
| Pedro | 1 | 1 | TI |
| Henrique | 1 | 1 | TI |
| Artur | 2 | 2 | JUR |
| Cecilia | 3 | 3 | FIN |

- O resultado passa a ter sentido, representando apenas as combinações válidas entre os dados das relações.

- Caso se deseje eliminar colunas específicas, pode-se aplicar uma **projeção**.

## 4. RESUMO DOS SÍMBOLOS

| Símbolo | Operação | Tipo |
|---------|----------|------|
| σ | Seleção | Unário |
| π | Projeção | Unário |
| ρ | Renomeação | Unário |
| U | União | Binário |
| ∩ | Interseção | Binário |
| – | Diferença | Binário |
| X | Produto Cartesiano | Binário |
| ⋈ | Junção | Binário |

> ### 4.1 Correspondência com SQL
> - `SELECT C FROM S` → **PROJEÇÃO** (π) do atributo C na relação S
> - `WHERE` → **SELEÇÃO** (σ), filtrando registros conforme condição especificada
> - `FROM T1, T2` → **PRODUTO CARTESIANO** (X)

## 5. QUESTÕES COMENTADAS

### Questão 01 (CESGRANRIO/PETROBRAS/2018)

**Análise:** A questão apresenta uma figura com duas relações e o resultado final com apenas "Fusca" e "Opala".

- Resultado final com apenas uma coluna → **PROJEÇÃO** (π)
- Valores não se repetem → seleção adequada aplicada após cruzamento
- Alternativa correta: **πC((σB>25(S)) ⋈ A=G T)**

**Gabarito: b**

### Questão 02 (CESGRANRIO/LIQUIGÁS/2012)

**O número de tuplas resultante de uma operação de projeção sobre uma relação R é sempre igual ou menor que o número de tuplas de R.**

**Justificativa:** Ao projetar apenas alguns atributos, registros duplicados podem ser eliminados, reduzindo a quantidade de tuplas.

**Gabarito: a**

### Questão 03 (UFRPE/2016)

**Análise das afirmativas:**

1. ❌ União elimina duplicatas (não mantém)
2. ✅ Projeção produz nova relação com alguns atributos
3. ✅ Junção produz combinações que satisfazem condição
4. ✅ Produto cartesiano combina toda tupla de R com toda tupla de S

**Gabarito: e** (2, 3 e 4 apenas)

### Questão 04 (CESGRANRIO/PETROBRAS/2014)

**Obter as Placas dos VEICULOS com Ano = 2011 e Valor < 9000.**

- Solicitação da placa → **PROJEÇÃO** (π) sobre o atributo "Placa"
- Condições "ano = 2011" e "valor < 9000" → **SELEÇÃO** (σ)

**Expressão correta: πPlaca (σAno = 2011 AND Valor < 9000 (VEICULO))**

**Gabarito: d**

### Questão 05 (CESGRANRIO/PETROBRAS/2012)

**Classificação das operações:**
- **Project (projeção):** unária (atua sobre uma relação)
- **Union (união):** binária (atua sobre duas relações)
- **Select (seleção):** unária (atua sobre uma relação)

**Gabarito: d** (unária, binária, unária)

## 6. OBSERVAÇÕES PARA CONCURSOS

- As operações mais cobradas em concursos são: **UNIÃO, INTERSEÇÃO, DIFERENÇA, PRODUTO CARTESIANO, SELEÇÃO, PROJEÇÃO e JUNÇÃO**.

- Eventualmente, concursos militares podem apresentar operações não abordadas neste conteúdo (como **DIVISÃO**), mas a regra geral segue as operações principais.

- Os mesmos tópicos costumam ser cobrados repetidamente ao longo dos anos.

- A quantidade de questões sobre álgebra relacional não é extensa, o que possibilita a resolução de todas.

- Recomenda-se resolver algumas durante o processo de aprendizagem e reservar outras para a etapa de revisão.