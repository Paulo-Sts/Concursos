# Anotações – Banco de Dados – Normalização – Exercícios (Questões Comentadas)

## 1. Síntese das Formas Normais (Revisão)

| FORMA NORMAL | CRITÉRIO | O QUE ELIMINA |
| --- | --- | --- |
| **1FN** | Valores atômicos | Atributos multivalorados, compostos e grupos de repetição |
| **2FN** | 1FN + dependência total da PK | Dependência funcional **parcial** (atributo não chave depende de parte da PK) |
| **3FN** | 2FN + dependência direta da PK | Dependência funcional **transitiva** (atributo não chave depende de outro atributo não chave) |
| **FNBC** | 3FN + todo determinante é superchave | Dependências funcionais com determinante não superchave |

> ### 1.1 Relação entre as formas normais
> - **Toda FNBC está na 3FN**, mas **nem toda 3FN está na FNBC**.
> - **Toda 3FN está na 2FN**, mas **nem toda 2FN está na 3FN**.
> - **Toda 2FN está na 1FN**, mas **nem toda 1FN está na 2FN**.

## 2. Questões de Concurso Comentadas

### 2.1 (FCC/2014/TJ-AP – Analista Judiciário)

**Item:** "I – A tabela não contém dependências transitivas (3FN). II – A tabela não contém dependências parciais (2FN)."

**Gabarito:** **c) 3FN e 2FN**.

**Comentário:**
- **3FN** elimina dependências **transitivas**.
- **2FN** elimina dependências **parciais**.

### 2.2 (FCC/2011/TRT-19ª – Analista Judiciário)

**Item:** "Para uma tabela estar na FNBC, ela:"

**Gabarito:** **c) também está normalizada na 3FN**.

**Comentário:** A FNBC é mais restritiva que a 3FN. Toda tabela em FNBC também está em 3FN (e em 2FN e em 1FN).

### 2.3 (FCC/2017/DPE-RS – Analista Judiciário – Banco de Dados)

**Item:** "Uma tabela está na segunda forma normal pois, além de estar na primeira forma normal:"

**Gabarito:** **b) cada atributo não chave da tabela é dependente de todos os atributos da chave primária da tabela.**

**Comentário:** A 2FN exige que todo atributo não chave dependa **totalmente** da chave primária (não pode haver dependência parcial).

### 2.4 (CESPE/2017/TRF-1ª – Analista Judiciário)

**Item:** "Em uma tabela na segunda forma normal, todos os atributos não chave são dependentes da chave primária."

**Gabarito:** **Certo (C)**.

**Comentário:** A 2FN exige dependência total da chave primária; se a chave for composta, deve depender de toda a chave, não de parte dela.

### 2.5 (CESPE/2018/EBSERH – Analista)

**Item:** "Em normalização, a primeira forma normal é caracterizada por uma tabela com a existência obrigatória de uma chave primária e uma chave estrangeira."

**Gabarito:** **Errado (E)**.

**Comentário:** A 1FN exige **valores atômicos** – não há obrigatoriedade de chave primária ou chave estrangeira. Esses são conceitos de integridade, não da 1FN.

### 2.6 (FCC/2018/DPE-AM – Analista de Banco de Dados)

**Item:** "Uma tabela de um banco de dados relacional está na primeira forma normal se:"

**Gabarito:** **d) os domínios de todos os atributos dessa tabela forem atômicos.**

**Comentário:** A 1FN exige que todos os atributos tenham valores atômicos (indivisíveis).

### 2.7 (CESPE/2018/STM – Técnico Judiciário)

**Item:** "Uma tabela estará na segunda forma normal (2FN) quando, além de estar na terceira forma normal (3FN), ela contiver dependências funcionais parciais."

**Gabarito:** **Errado (E)**.

**Comentário:** A 2FN **elimina** dependências parciais. Além disso, a 2FN é anterior à 3FN (2FN → 3FN), não o contrário.

### 2.8 (SUGEP-UFRPE/2018 – Técnico de TI)

**Item:** "O processo de normalização que requer que os atributos dependam unicamente da chave primária (e não apenas de parte dela) é a:"

**Gabarito:** **b) Segunda forma normal**.

**Comentário:** A 2FN elimina dependências parciais, exigindo que atributos não chave dependam da **chave primária completa**.

### 2.9 (CESGRANRIO/2018/BANCO DO BRASIL – Escriturário)

**Item:** "Uma tabela que esteja na:"

**Gabarito:** **c) Terceira forma normal não pode conter dependências funcionais parciais.**

**Comentário (do professor):** A terceira forma normal elimina dependências **transitivas**, mas a 3FN **também não pode conter dependências parciais**, porque está na 2FN (e a 2FN elimina dependências parciais). A questão considerou essa como a "menos errada".

### 2.10 (CESPE/CEBRASPE/2025/TRF-6ª – Técnico Judiciário)

**Item:** "Para que uma tabela esteja em BCNF, todos os atributos devem depender unicamente da chave primária, ignorando o impacto de dependências funcionais provenientes de outras superchaves ou chaves candidatas."

**Gabarito:** **Errado (E)**.

**Comentário:** A FNBC exige que **todo determinante seja superchave** – isso inclui **todas as chaves candidatas**, não apenas a chave primária. Não se pode ignorar outras superchaves.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FCC/2014) | c |
| 02 (FCC/2011) | c |
| 03 (FCC/2017) | b |
| 04 (CESPE/2017) | C |
| 05 (CESPE/2018/EBSERH) | E |
| 06 (FCC/2018) | d |
| 07 (CESPE/2018/STM) | E |
| 08 (SUGEP-UFRPE/2018) | b |
| 09 (CESGRANRIO/2018) | c |
| 10 (CESPE/2025) | E |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO | GABARITO RELACIONADO |
| --- | --- | --- |
| **1FN** | Valores atômicos | Questões 5 e 6 |
| **2FN** | Dependência total da PK (elimina dependência parcial) | Questões 1, 3, 4, 8 e 9 |
| **3FN** | Elimina dependência transitiva | Questões 1, 2, 7 e 9 |
| **FNBC** | Todo determinante é superchave (inclui chaves candidatas) | Questões 2 e 10 |

---

*Material complementar à aula "Banco de Dados – Normalização – Exercícios" (professor Washington Henrique Almeida, Gran Concursos).*