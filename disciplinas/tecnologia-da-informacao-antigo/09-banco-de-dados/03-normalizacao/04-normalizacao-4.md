# Anotações – Banco de Dados – Normalização 4FN e 5FN

## 1. Dependência Multivalorada (Multideterminação)

### 1.1 Conceito

- Ocorre quando um atributo **A** determina **um conjunto de valores** para outro atributo **B**, independentemente dos demais atributos da relação.
- **Notação:** `A →→ B` (lê-se: "A multidetermina B").
- Em uma dependência multivalorada, o atributo **A** não determina um único valor para **B**, mas **um conjunto** de valores.

### 1.2 Exemplo clássico (Empregado – Projeto – Dependente)

**Tabela não normalizada:**

| Empregado | Projeto | Dependente |
| --- | --- | --- |
| João | Reforma Estádio | João Jr. |
| João | Reforma Estádio | Joana |
| Juliana | Reforma Estádio | Renato |
| Juliana | Reforma Estádio | Carla |
| Juliana | Construção de Ponte | Renato |
| Juliana | Construção de Ponte | Carla |

**Dependências multivaloradas:**
- `Empregado →→ Projeto` (um empregado pode trabalhar em vários projetos)
- `Empregado →→ Dependente` (um empregado pode ter vários dependentes)

> ### 1.2.1 Problema
> - A tabela apresenta **redundância** significativa: cada combinação de empregado, projeto e dependente é repetida para cada associação.
> - A tabela pode estar na **3FN**, mas ainda contém dependências multivaloradas.

## 2. Quarta Forma Normal (4FN)

### 2.1 Definição

- Uma relação está na **4FN** se:
  1. Estiver na **3FN**.
  2. **Não contiver dependências multivaloradas** (a não ser que sejam triviais).

### 2.2 Exemplo – Sistema de Biblioteca (Livro, Estante, Autor)

**Tabela LOCALIZACAO (não normalizada para 4FN):**

| Estante | ISBN | Autor |
| --- | --- | --- |
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

**Dependência multivalorada:** `ISBN →→ Autor` (um ISBN pode ter vários autores).

### 2.3 Decomposição para 4FN

**Esquema original (3FN, mas com dependência multivalorada):**
```
LOCALIZACAO (Estante, ISBN, Autor)
```

**Decomposição para 4FN:**

```
LOCALIZACAO (Estante, ISBN)
AUTORIA (ISBN, CodAutor)
```

**Tabelas resultantes:**

**LOCALIZACAO:**
| Estante | ISBN |
| --- | --- |
| E1 | L1 |
| E1 | L2 |
| E2 | L1 |
| E3 | L2 |

**AUTORIA:**
| ISBN | CodAutor |
| --- | --- |
| L1 | A1 |
| L1 | A2 |
| L2 | A7 |
| L2 | A8 |
| L2 | A9 |

- A tabela `AUTORIA` permite que um livro (`ISBN`) tenha **múltiplos autores** sem repetir informações da localização.
- A dependência multivalorada foi eliminada.

> ### 2.3.1 Esquema completo para 4FN (exemplo da biblioteca)
> ```
> ESTANTE (NumEst, Capacidade)
> LIVRO (ISBN, Titulo, Ano)
> AUTOR (CodAutor, Nome)
> LOCALIZACAO (NumEst, ISBN)
> AUTORIA (ISBN, CodAutor)
> ```

## 3. Dependência de Junção e Quinta Forma Normal (5FN)

### 3.1 Conceito de Dependência de Junção

- Uma relação apresenta **dependência de junção** quando **não pode ser decomposta em duas projeções sem perda**, mas pode ser decomposta em **três ou mais** projeções.
- O problema é que a junção de duas tabelas pode gerar **tuplas espúrias** (que não existiam na relação original).

### 3.2 Definição de 5FN

- Uma relação está na **5FN** se:
  1. Toda **dependência de junção** em R for **resultado de chaves candidatas** de R.
  2. A decomposição da relação deve permitir **reconstrução sem perda** a partir de **três ou mais** projeções.

### 3.3 Exemplo clássico (Vendedor – Montadora – Produto)

**Tabela R (Vendedor, Montadora, Produto):**

| Vendedor | Montadora | Produto |
| --- | --- | --- |
| João | Ford | Carro |
| João | Ford | Caminhão |
| João | GM | Carro |
| João | GM | Caminhão |
| Carlos | Ford | Carro |

**Problema:**
- A relação **não pode ser decomposta em duas projeções sem perda** (ex.: `VENDEDOR_MONTADORA` e `VENDEDOR_PRODUTO`).
- Se fizermos a junção dessas duas projeções, aparecerão combinações que não existiam no original (tuplas espúrias).

**Decomposição em três projeções (solução para 5FN):**

**VENDEDOR_MONTADORA:**
| Vendedor | Montadora |
| --- | --- |
| João | Ford |
| João | GM |
| Carlos | Ford |
| Marcos | Honda |

**VENDEDOR_PRODUTO:**
| Vendedor | Produto |
| --- | --- |
| João | Carro |
| João | Caminhão |
| Carlos | Carro |
| Marcos | SUV |
| Marcos | Carro |

**MONTADORA_PRODUTO:**
| Montadora | Produto |
| --- | --- |
| Ford | Carro |
| Ford | Caminhão |
| GM | Carro |
| GM | Caminhão |
| Honda | SUV |
| Honda | Carro |

- Com essas **três** tabelas, é possível **reconstruir** a relação original sem perda de dados (e sem tuplas espúrias).
- A 5FN é alcançada quando toda dependência de junção é baseada em chaves candidatas.

> ### 3.3.1 Projeção (Álgebra Relacional)
> - **Seleção (`SELECT *`):** recupera todas as colunas de uma tabela (com ou sem filtro).
> - **Projeção (`SELECT coluna1, coluna2`):** recupera apenas colunas específicas.

## 4. Esquema Resumo das Formas Normais

| FORMA NORMAL | CRITÉRIO | O QUE ELIMINA / EXIGE |
| --- | --- | --- |
| **1FN** | Valores atômicos | Atributos multivalorados, compostos e grupos de repetição |
| **2FN** | 1FN + dependência total da PK | Dependência funcional **parcial** |
| **3FN** | 2FN + dependência direta da PK | Dependência funcional **transitiva** |
| **FNBC** | 3FN + todo determinante é superchave | Dependências funcionais com determinante não superchave |
| **4FN** | 3FN + sem dependências multivaloradas | Dependências multivaloradas (multideterminação) |
| **5FN** | Toda dependência de junção é baseada em chaves | Dependências de junção que geram tuplas espúrias |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/2018/IPHAN – Analista)

**Item:** "Uma relação está na quarta forma normal (4FN) quando o conteúdo do registro não pode ser mais reconstruído (efetuar join) a partir de outros registros menores extraídos desse registro considerado."

**Gabarito: Errado (E)**.

**Comentário:** A 4FN elimina **dependências multivaloradas**. A reconstrução sem perda por `join` refere-se à **5FN**.

### 5.2 (INSTITUTO AOCP/2016/IPHAN – Analista de TI)

**Item:** "Uma tabela está na 4FN quando, além de estar na 3FN,"

**Gabarito:** **a) não contém dependências multivolaradas.**

### 5.3 (COSEAC/UFF/2015 – Técnico de TI)

**Correspondência entre formas normais e definições:**

| DEFINIÇÃO | FORMA NORMAL |
| --- | --- |
| Seus únicos determinantes são chaves candidatas | FNBC |
| Não contém tabelas aninhadas | 1FN |
| Evitar dependências parciais | 2FN |
| Combater a dependência de junção | 5FN |
| Evitar dependências transitivas | 3FN |

**Gabarito:** **b) 4, 1, 2, 5, 3**.

### 5.4 (FGV/2025/TCE-RR – Analista Administrativo)

**Item:** "As formas normais que buscam eliminar novos conceitos de dependência funcional que são extensões e especializações do conceito original são:"

**Gabarito:** **d) 4FN e 5FN**.

**Comentário:** 4FN e 5FN são extensões que lidam com **dependências multivaloradas** e **dependências de junção**, respectivamente – conceitos mais específicos que vão além das dependências funcionais tradicionais.

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/2018) | E |
| 02 (AOCP/2016) | a |
| 03 (COSEAC/2015) | b |
| 04 (FGV/2025) | d |

---

*Material complementar à aula "Banco de Dados – Normalização 4FN e 5FN" (professor Washington Henrique Almeida, Gran Concursos).*