# Banco de Dados - Normalização 3

## 1. Dependência Multivalorada
- A dependência multivalorada ocorre quando um atributo A1 de R determina um conjunto finito de valores para os outros atributos A2, ..., An de R.
- Representação: A ⟶⟶ B (A multidetermina B ou B é multidependente de A).
- Um valor do atributo determinante identifica repetidas vezes um conjunto de valores na coluna dependente.
- Exemplo clássico: empregados, projetos e dependentes.
  - O empregado multidetermina os dependentes e, simultaneamente, multidetermina os projetos.
  - Juliana aparece associada ao projeto “Reforma de Estádio” com diferentes dependentes, e também ao projeto “Construção de Ponte”, novamente com um dependente.
  - Empregado ⟶⟶ Dependente
  - Empregado ⟶⟶ Projeto

| EMPREGADO | PROJETO | DEPENDENTE |
|-----------|---------|------------|
| João | Reforma Estádio | João Jr. |
| João | Reforma Estádio | Joana |
| Juliana | Reforma Estádio | Renato |
| Juliana | Reforma Estádio | Carla |
| Juliana | Construção de ponte | Renato |
| Juliana | Construção de ponte | Carla |

> [!TIP] DICAS: 
> - A dependência multivalorada é representada por uma seta dupla (⟶⟶), diferentemente da dependência funcional que usa seta simples (⟶).
> - O mesmo valor do determinante aparece repetido para cada valor do dependente.

> [!CAUTION] OBSERVAÇÃO: 
> - Esse tipo de estrutura pode causar crescimento excessivo da tabela, resultando em redundâncias.

## 2. Quarta Forma Normal (4FN)
- Uma relação está na 4FN quando, além de estar na 3FN, não contém dependências multivaloradas.
- O objetivo da 4FN é eliminar dependências multivaloradas por meio da decomposição da tabela em estruturas mais adequadas.
- Exemplo: sistema de biblioteca com livros, autores, localização e estantes.
  - ISBN L1 determina múltiplos autores (A1, A2).
  - ISBN L2 determina autores (A7, A8, A9).
  - ISBN (L1) ⟶ Autor = {A1, A2}
  - ISBN (L2) ⟶ Autor = {A7, A8, A9}
  - Configura-se uma multideterminação: ISBN ⟶⟶ Autor.

| ESTANTE | ISBN | AUTOR |
|---------|------|-------|
| E1 | L1 | A1 |
| E1 | L1 | A2 |
| E1 | L2 | A7 |
| E1 | L2 | A8 |
| E1 | L2 | A9 |
| E2 | L1 | A1 |
| E2 | L1 | A2 |
| E3 | L2 | A7 |
| E3 | L2 | A8 |
| E3 | L2 | A9 |

### 2.1 Estrutura Normalizada Até 3FN
- 3FN:
  - Estante (NumEst, Capacidade)
  - Livro (ISBN, Título, Ano)
  - Autor (CodAutor, Nome)
  - Localização (NumEst, ISBN, CodAutor)
- DF Multivalorada presente: ISBN ⟶⟶ Autor

### 2.2 Estrutura Normalizada em 4FN
- 4FN:
  - Estante (NumEst, Capacidade)
  - Livro (ISBN, Título, Ano)
  - Autor (CodAutor, Nome)
  - Localizacao (NumEst, ISBN)
  - Autoria (ISBN, CodAutor)

| LOCALIZACAO | | AUTORIA | |
|-------------|-|---------|-|
| ESTANTE | ISBN | ISBN | AUTOR |
| E1 | L1 | L1 | A1 |
| E1 | L2 | L1 | A2 |
| E2 | L1 | L2 | A7 |
| E3 | L2 | L2 | A8 |
| | | L2 | A9 |

> [!TIP] DICAS: 
> - A solução para a 4FN é criar uma nova tabela que represente a relação multivalorada (ex.: Autoria).
> - Elimina-se a redundância ao separar a localização (estante + ISBN) da autoria (ISBN + autor).

> [!CAUTION] OBSERVAÇÃO: 
> - Uma dúvida frequente refere-se à transição da 3FN para a 4FN. Embora a 3FN elimine dependências funcionais transitivas, ainda pode haver o problema de multideterminação.
> - Na 3FN, não há atributo que dependa simultaneamente da chave primária e de outro atributo, mas ainda se observa o problema de multideterminação.
> - A 4FN resolve esse caso específico, eliminando a existência de dependência em relação às chaves candidatas.

## 3. Quinta Forma Normal (5FN)
- Uma relação está na 5FN se, e somente se, toda dependência de junção em R for resultado de chaves candidatas de R.
- Existem relações que não podem ser decompostas em duas projeções sem perda, mas podem ser decompostas em três ou mais.
- O principal desafio da 5FN está nas junções: ao realizar junções entre relações, obtêm-se novas relações que não estavam presentes originalmente.
- A decomposição sem perda refere-se à possibilidade de recuperar integralmente as relações originais, sem a exclusão de quaisquer dados.
- A 5FN pressupõe que já tenham sido atendidas as exigências da 3FN e da 4FN.
- Exemplo: relação R (Vendedor, Montadora, Produto).
  - Um vendedor pode trabalhar para várias montadoras e vende vários produtos.
  - Uma montadora pode ter vários vendedores e vende vários produtos.
  - Relação R não pode ser decomposta em duas projeções sem perda (Dependência de Junção - DJ).

### 3.1 Relação Original R
| VENDEDOR | MONTADORA | PRODUTO |
|----------|-----------|---------|
| João | Ford | Carro |
| João | Ford | Caminhão |
| João | GM | Carro |
| João | GM | Caminhão |
| Carlos | Ford | Carro |

### 3.2 Decomposição Incorreta (Não Satisfaz 5FN)
- Não é possível retornar às relações originais apenas por meio de duas decomposições.
- VENDEDOR_MONTADORA + VENDEDOR_PRODUTO não recompoem R integralmente.

| VENDEDOR_MONTADORA | | VENDEDOR_PRODUTO | |
|--------------------|-|------------------|-|
| VENDEDOR | MONTADORA | VENDEDOR | PRODUTO |
| João | Ford | João | Carro |
| João | GM | João | Caminhão |
| Carlos | Ford | Carlos | Carro |
| Marcos | Honda | Marcos | SUV |
| | | Marcos | Carro |

### 3.3 Decomposição Correta (Satisfaz 5FN)
- A solução consiste em decompor a relação R em três relações:
  - Vendedor_Montadora
  - Vendedor_Produto
  - Montadora_Produto
- A partir dessas três, é possível recompor a relação R de forma íntegra, sem perda de dados.

| VENDEDOR_MONTADORA | | VENDEDOR_PRODUTO | | MONTADORA_PRODUTO | |
|--------------------|-|------------------|-|-------------------|-|
| VENDEDOR | MONTADORA | VENDEDOR | PRODUTO | MONTADORA | PRODUTO |
| João | Ford | João | Carro | Ford | Carro |
| João | GM | João | Caminhão | Ford | Caminhão |
| Carlos | Ford | Carlos | Carro | GM | Carro |
| Marcos | Honda | Marcos | SUV | GM | Caminhão |
| | | Marcos | Carro | Honda | SUV |
| | | | | Honda | Carro |

> [!TIP] DICAS: 
> - A 5FN exige decomposição em três ou mais projeções para garantir a recomposição sem perdas.
> - A projeção na álgebra relacional seleciona apenas parte dos atributos (ex.: SELECT coluna A, coluna B). A seleção recupera todos os atributos (ex.: SELECT *).

## 4. Esquema Resumo das Formas Normais
- 1FN: Todos atributos são atômicos (não contém tabelas aninhadas).
- 2FN: Não há dependências funcionais parciais.
- 3FN: Não há dependências funcionais transitivas.
- FNBC: Todos os determinantes são chaves candidatas.
- 4FN: Não há dependências multivaloradas.
- 5FN: Toda dependência de junção é baseada em chaves (decomposição sem perda).

> [!CAUTION] OBSERVAÇÃO: 
> - A 4FN e a 5FN são extensões de casos específicos e, por esse motivo, sua aplicação prática é rara.
> - As formas normais que buscam eliminar novos conceitos de dependência funcional que são extensões e especializações do conceito original são 4FN e 5FN.
> - A FNBC exige que todos os determinantes sejam chaves candidatas.