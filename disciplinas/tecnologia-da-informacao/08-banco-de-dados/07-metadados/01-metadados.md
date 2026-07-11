# Anotações – Banco de Dados – Metadados

## 1. Conceito de Metadados

- **Metadados** são **dados que descrevem outros dados**.
- Fornecem **contexto** e **informações estruturais** sobre os dados, permitindo sua correta interpretação, organização e recuperação.
- São essenciais para a **compreensão, localização, acesso e gestão** de recursos informacionais.

> ### 1.1 Exemplos cotidianos
> - **Biblioteca:** autor, título, área de conhecimento, ano de publicação – metadados que ajudam a encontrar um livro.
> - **Questões de concurso:** banca, disciplina, tipo (certo/errado, múltipla escolha).
> - **Imagem JPEG:** nome do arquivo, autor, data de criação.
> - **Tabela de banco de dados:** nome da tabela, nome das colunas, tipos de dados (ex.: `int`, `varchar`).

## 2. Funções dos Metadados

| FUNÇÃO | DESCRIÇÃO |
| --- | --- |
| **Descrição** | Descrevem o conteúdo, a estrutura e as características do dado. |
| **Identificação** | Permitem identificar e diferenciar recursos informacionais. |
| **Localização** | Indicam onde o dado está armazenado (ex.: URL, caminho de arquivo). |
| **Recuperação** | Facilitam a busca e o acesso à informação (ex.: indexação, palavras-chave). |
| **Organização** | Estruturam dados em categorias e relações. |
| **Preservação** | Registram informações sobre formato, versão, acesso e armazenamento. |
| **Gestão** | Auxiliam no gerenciamento de recursos (ex.: data de criação, modificação, permissões). |

> ### 2.1 Metadados em sistemas de recuperação
> - Sistemas que utilizam metadados podem recuperar informações com base nas **descrições dos campos** dos metadados.
> - Exemplo: em uma página web, metadados podem incluir a URL, permitindo a localização do objeto digital.

## 3. Metadados e Dados Estruturados vs. Semiestruturados

| TIPO DE DADO | REPRESENTAÇÃO DE METADADOS |
| --- | --- |
| **Dados estruturados (tabelas)** | Nome da tabela, nome dos campos, tipos de dados, restrições. |
| **Dados semiestruturados (JSON, XML)** | Tags (XML) ou pares chave-valor (JSON) que descrevem propriedades. |
| **Dados não estruturados** | Metadados separados (ex.: nome do arquivo, data, autor). |

> ### 3.1 Exemplo em JSON
> ```json
> {
>   "Nome": "Victor",
>   "Disciplinas": ["Banco de Dados", "Big Data"]
> }
> ```
> - As chaves ("Nome", "Disciplinas") são metadados que descrevem os valores.

## 4. Padrões de Metadados

- **Dublin Core:** padrão internacional para descrição de recursos digitais.
- **MARC:** padrão para descrição bibliográfica em bibliotecas.
- **Metadados seguem padrões** para garantir consistência e interoperabilidade.

## 5. Características dos Metadados (questão FUNDATEC)

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Descrição** | Metadados descrevem o recurso informacional, não apenas condições físicas. |
| **Padronização** | Observam padrões internacionais (ex.: Dublin Core) para sintaxe e semântica. |
| **Preservação e acesso** | Incluem informações sobre armazenamento, preservação e uso. |
| **Autodescrição** | Criam documentação que auxilia no gerenciamento dos recursos. |

## 6. Importância dos Metadados

- **Facilitam o compartilhamento** da informação.
- **Auxiliam na gestão da informação** (versão, acesso, localização).
- **Tornam ferramentas de busca mais efetivas**, especialmente em bibliotecas digitais.
- **Permitem a padronização** e a **indexação** de dados.

## 7. Questões de Concurso Comentadas

### 7.1 (IDECAN/2023/SEFAZ-RR – Administrador de BD)

**Item:** "Principal forma de acesso às informações em bibliotecas digitais."

**Gabarito: e) metadados.**

### 7.2 (CESPE/CEBRASPE/2024/CAPES – Analista/Biblioteconomia)

**Item:** "Os metadados contêm informações relativas tanto à natureza bibliográfica do objeto quanto à localização onde é possível encontrá-lo."

**Gabarito: Certo (C).**

### 7.3 (INSTITUTO CONSULPLAN/2023/MPE-MG – Analista/Biblioteconomia)

**Afirmativas sobre metadados:**

- ( ) Mesma função dos elementos de descrição em catálogos. **(V)**
- ( ) Atributos que identificam e representam um recurso informacional. **(V)**
- ( ) Pontos de acesso aos recursos informacionais. **(V)**
- ( ) Variam conforme o recurso, domínio e necessidades dos usuários. **(V)**

**Gabarito: d) V, V, V, V.**

### 7.4 (CESPE/CEBRASPE/2023/TJ-ES – Analista/Biblioteconomia)

**Item:** "Metadados representam as características de um objeto digital por meio de uma descrição longa e subjetiva do conteúdo de um documento."

**Gabarito: Errado (E).**

**Comentário:** Metadados são **objetivos e específicos**, não longos e subjetivos.

### 7.5 (CESPE/CEBRASPE/2023/TJ-ES – Analista/Biblioteconomia)

**Item:** "Sistemas que utilizam metadados podem recuperar informações pelas descrições realizadas em seus campos."

**Gabarito: Certo (C).**

### 7.6 (QUADRIX/2023/CRB – Bibliotecário Fiscal)

**Item:** "Os metadados são utilizados com o objetivo de facilitar o compartilhamento da informação, auxiliar na gestão da informação e tornar as ferramentas de busca mais efetivas."

**Gabarito: Certo (C).**

### 7.7 (FUNDATEC/2022/SPGG-RS – Analista Bibliotecário)

**Item:** "O principal objetivo dos metadados é registrar e organizar de forma estruturada os dados, visando à padronização e fácil recuperação."

**Gabarito: c) Metadados – padronização.**

### 7.8 (FUNDATEC/2022/SPGG-RS – Analista Bibliotecário)

**Características dos metadados:**
- I – Descrição pormenorizada das condições físicas **(F)** – metadados descrevem o recurso, não apenas condições físicas.
- II – Observância de padrões internacionais **(V)**
- III – Informação sobre armazenagem, preservação, acesso **(V)**
- IV – Autodescrição e documentação para gerenciamento **(V)**

**Gabarito: d) Apenas II, III e IV.**

### 7.9 (CESPE/CEBRASPE/2021/PF – Escrivão)

**Item:** "A função do metadado de arquivo é descrever o destino final do arquivo definido pelo emissor."

**Gabarito: Errado (E).**

**Comentário:** Metadados vão além – incluem localização, conteúdo, formato, etc.

### 7.10 (CESPE/CEBRASPE/2020/MPE-CE – Analista/Biblioteconomia)

**Item:** "Os metadados descrevem, explicam, localizam e facilitam a recuperação de um recurso informacional, permitindo que esse recurso esteja acessível futuramente."

**Gabarito: Certo (C).**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (IDECAN/2023) | e |
| 02 (CESPE/CAPES/2024) | C |
| 03 (CONSULPLAN/2023) | d |
| 04 (CESPE/TJ-ES/2023) | E |
| 05 (CESPE/TJ-ES/2023) | C |
| 06 (QUADRIX/2023) | C |
| 07 (FUNDATEC/2022) | c |
| 08 (FUNDATEC/2022) | d |
| 09 (CESPE/PF/2021) | E |
| 10 (CESPE/MPE-CE/2020) | C |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Metadados** | Dados que descrevem outros dados. |
| **Funções** | Descrever, identificar, localizar, recuperar, organizar, preservar, gerenciar. |
| **Exemplos** | Autor, título, data, formato, URL, nome da tabela, tipo de dado. |
| **Padrões** | Dublin Core, MARC. |
| **Características** | Objetivos, específicos, padronizados, variam conforme o domínio. |
| **Dados estruturados** | Metadados = esquema (nomes de tabelas/colunas, tipos). |
| **Dados semiestruturados** | Metadados = tags (XML) ou chaves (JSON). |

---

*Material complementar à aula "Banco de Dados – Metadados" (professor Vitor Kessler/Gran Concursos).*