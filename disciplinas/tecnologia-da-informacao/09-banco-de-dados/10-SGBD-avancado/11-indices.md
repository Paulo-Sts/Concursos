# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO – ÍNDICE

## 1. ÍNDICES - CONCEITOS FUNDAMENTAIS

- No contexto da estrutura de dados, um índice é uma **referência associada a uma chave**, utilizada para fins de **otimização**, permitindo uma localização mais rápida de um registro quando se é feita uma consulta.

- O índice em um banco de dados é semelhante ao **índice de um livro**: caso seja necessário chegar a um determinado ponto, ao observar o índice é possível chegar ao ponto buscado mais rapidamente.

- É uma estrutura que possibilita acesso a um item indexado desde que a busca tenha complexidade **inferior à complexidade linear** (podendo ser logarítmica ou constante).

> ### 1.1 Quando o Índice é Utilizado
> - O índice **apenas será utilizado se acelerar o acesso**.
> - Caso seja mais rápida a busca de forma linear, **não deve ser utilizado o índice**.
> - Exemplo: para chegar à página 1 de um livro, não é necessário utilizar o índice.

### 1.2 Características Principais

- No contexto de banco de dados, um índice é uma estrutura (ou arquivo) auxiliar associado a uma tabela.

- Tem a função de **acelerar o tempo de acesso** às linhas de uma tabela, criando ponteiros para os dados armazenados em colunas específicas.

- O banco de dados utiliza o índice de forma semelhante ao **índice remissivo** de um livro: verifica um assunto determinado no índice e em seguida localiza a sua posição em uma determinada página.

- Em uma tabela normalizada, todas as tabelas possuem uma **chave primária** que é um índice, servindo para uma pesquisa pelo menos linear.

### 1.3 Considerações sobre Índices

| Aspecto | Consideração |
|---------|--------------|
| **Atualizações frequentes** | O índice também precisa ser atualizado. Escolher campos cuja atualização faça sentido. |
| **Muitos índices** | A criação de vários índices demanda estruturas paralelas que precisarão ser atualizadas, tornando a consulta mais lenta. |
| **Overhead** | Índices geram custo de armazenamento e manutenção. |

> ### 1.4 Índices em SGBDs
> - Os SGBDs possuem funcionalidades que indicam onde seria bom criar um índice ou eliminar um.
> - Com o tempo, índices podem ter suas características modificadas, tornando-se inadequados ao campo indexado.
> - O **SQL Server** possui um esquema de indexação simplório, por isso não costuma ser cobrado em provas.
> - O **Oracle** possui uma estrutura de índice mais complexa, sendo mais cobrado.

## 2. CLASSIFICAÇÃO DOS ÍNDICES

### 2.1 Quanto à Quantidade de Colunas

| Tipo | Descrição |
|------|-----------|
| **Índice Simples** | Faz referência a uma **única coluna**. |
| **Índice Composto** | Faz referência a **mais de uma coluna**. |

### 2.2 Quanto à Densidade

| Tipo | Descrição |
|------|-----------|
| **Índice Denso** | Possui uma entrada para **cada registro** no arquivo de dados. |
| **Índice Esparso** | O total de entradas no índice será igual ao **número de blocos** do arquivo de dados. |

### 2.3 Quanto à Localização

| Tipo | Descrição |
|------|-----------|
| **Índice Interno** | A chave está contida **dentro da tabela**. Ex.: chave primária em uma tabela se torna um índice. |
| **Índice Externo** | Existe uma **tabela de chaves separada** que associa ponteiros a registros de uma tabela. |

> ### 2.4 Observação sobre Índices Internos x Externos
> - A classificação como índice interno ou externo depende da **implementação do SGBD**.
> - Não se sabe se o MySQL possui uma estrutura separada ou não, mas quando se cria, já é associado um índice àquela estrutura.

## 3. ÍNDICE PRIMÁRIO

- O **índice primário** é um arquivo ordenado cujos registros são de tamanho fixo com dois campos:
  1. **Chave** — mesmo tipo de dado do campo de chave de ordenação (chave primária) do arquivo de dados.
  2. **Ponteiro** — aponta para um bloco de disco (endereço de bloco).

- Associado a uma **chave primária** (*Primary Key*) de um arquivo.

- Normalmente, os SGBDs implementam a chave primária como um índice.

**Estrutura do Índice Primário:**

| Chave (Índice) | Ponteiro |
|----------------|----------|
| 1 | → Registro 1 |
| 2 | → Registro 2 |
| 3 | → Registro 3 |
| ... | ... |
| N | → Registro N |

**Arquivo de Dados:**
| ID | Nome |
|----|------|
| 1 | Maria |
| 2 | Ana |
| 3 | Paulo |
| 4 | Rodrigo |
| 5 | Carlos |

## 4. ÍNDICE DE AGRUPAMENTO

- Quando os registros de arquivo são **fisicamente ordenados** em um **campo não chave** (que não tem um valor distinto para cada registro), esse campo é chamado de **campo de agrupamento**.

- O arquivo de dados é chamado de **arquivo agrupado**.

- Serve para **agilizar a recuperação de todos os registros que têm o mesmo valor** para o campo de agrupamento.

**Exemplo:**
| Funcionário | Nº Departamento |
|-------------|-----------------|
| João | 1 |
| Maria | 2 |
| Pedro | 1 |
| Ana | 3 |
| Carlos | 2 |

**Índice de Agrupamento:**
| Chave (Departamento) | Ponteiro |
|----------------------|----------|
| 1 | → Registros com Depto 1 |
| 2 | → Registros com Depto 2 |
| 3 | → Registros com Depto 3 |

> ### 4.1 Diferença entre Índice Primário e Índice de Agrupamento
> - **Índice Primário:** chave é **única** (chave primária) — uma entrada por registro.
> - **Índice de Agrupamento:** campo de agrupamento **não é único** — uma entrada por valor distinto.

## 5. ÍNDICE SECUNDÁRIO

- Podem ser definidos sobre atributos da tabela.
- Normalmente são:
  - **Chave (sem valores repetidos)** — ex.: CPF em uma tabela de funcionários.
  - **Não chave (com valores repetidos)** — ex.: cargo, departamento.

- Proporciona **caminhos alternativos** de acesso aos dados, além da chave primária.

> ### 5.1 Índice Secundário x Índice Primário
> - O índice secundário é criado **além** do índice primário já existente na tabela.
> - Permite consultas eficientes por campos que não são a chave primária.

## 6. ÍNDICE MULTINÍVEL

- O esquema multinível pode ser usado em **qualquer tipo de índice** — primário, de agrupamento ou secundário.

- O objetivo é **reduzir a parte do índice** que a pesquisa seguirá.

**Estrutura:**

```
Nível Secundário (Topo)
         ↓
Nível Primário (Base)
         ↓
Arquivo de Dados
```

> ### 6.1 Vantagem do Índice Multinível
> - Para encontrar o registro 85:
>   - **Busca linear:** 85 leituras (uma por registro).
>   - **Índice multinível:** 3 leituras (uma no nível secundário, uma no nível primário, uma no arquivo de dados).
> - O índice multinível é semelhante ao índice de um livro, que possui um nível macro e um nível mais detalhado.

## 7. ÍNDICE B-TREE

- A árvore é **balanceada**.

- Possui ponteiro de nó de árvore e ponteiro de árvore nulo (que não possui nenhum valor).

- Organiza os registros de forma que o nó central está no meio dos registros.

- A árvore faz **balanceamentos** para manter a eficiência.

**Vantagem:** com poucos saltos (leitura de nós) é possível chegar ao registro desejado, ao contrário da pesquisa sequencial que percorre todos os registros.

> ### 7.1 Relação com SGBDs
> - Existem SGBDs em que o padrão de índice é a árvore B-Tree.
> - O índice B-Tree pode ser cobrado como:
>   - *Tuning* de segurança.
>   - Otimização de desempenho.
>   - Índice propriamente dito.

## 8. RESUMO DOS TIPOS DE ÍNDICES

| Tipo | Descrição | Chave |
|------|-----------|-------|
| **Primário** | Índice sobre chave primária | Única |
| **Agrupamento** | Índice sobre campo de agrupamento (não chave) | Repetida |
| **Secundário** | Índice sobre outro campo da tabela | Única ou repetida |
| **Multinível** | Vários níveis de índice para reduzir busca | Qualquer |
| **B-Tree** | Árvore balanceada | Qualquer |

## 9. QUESTÕES COMENTADAS

### Questão 01 (CESPE/TJ-AM/2019)

**Afirmação:** "Em sistema gerenciador de banco de dados, os índices são estruturas que permitem agilizar a busca dos registros no disco."

**Análise:** Correta. Um índice, quando bem aplicado, proporciona agilidade na busca de registros no disco em que o arquivo se encontra.

**Gabarito: C** (certo)

### Questão 02 (INSTITUTO AOCP/PRODEB/2018)

**Estruturas de dados auxiliares utilizadas para acesso aos registros.**

**Gabarito: c** (Índices)

### Questão 03 (FAURGS/TJ-RS/2018)

**Tipo de índice utilizado para agilizar a recuperação de todos os registros que têm o mesmo valor para um dado campo.**

**Análise:**
- **Agrupamento:** agiliza recuperação de todos os registros com mesmo valor — ✅
- **Secundário:** caminho alternativo de acesso.
- **Primário:** associado à chave primária.
- **Multinível:** reduz parte do índice percorrida.
- **B-Tree:** árvore balanceada, não organiza todos do mesmo valor diretamente.

**Gabarito: a** (De agrupamento)

## 10. RESUMO PARA CONCURSOS

### 10.1 Conceitos Essenciais

- Índice = estrutura auxiliar para **otimização de consultas**.

- Utilizado **apenas se acelerar** a busca.

- **Chave primária** já é um índice por padrão.

- Índices geram **overhead** em operações de escrita (INSERT, UPDATE, DELETE).

### 10.2 Tipos de Índices - Destaque para Provas

| Tipo | Característica-chave |
|------|---------------------|
| **Primário** | Associado à chave primária. |
| **Agrupamento** | Registros fisicamente ordenados por campo não chave. |
| **Secundário** | Caminho alternativo de acesso. |
| **Multinível** | Reduz o percurso no índice. |
| **B-Tree** | Árvore balanceada. |

### 10.3 Densidade

- **Denso:** entrada para cada registro.
- **Esparso:** entrada para cada bloco.