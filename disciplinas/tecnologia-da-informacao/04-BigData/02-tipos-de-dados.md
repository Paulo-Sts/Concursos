# Anotações

# TIPOS DE DADOS EM BIG DATA

## 1. Classificação dos Dados

### 1.1 Dados Estruturados

- **Definição:** Informações organizadas em um **formato fixo e padronizado**, armazenadas em tabelas com **linhas e colunas**.
- **Modelo:** Seguem um **esquema rígido** e predefinido (campos, tipos de dados, restrições de integridade, chaves primárias e estrangeiras).
- **Armazenamento:** **Bancos de dados relacionais** (SQL).
- **Vantagens:** Fácil armazenamento, busca e consulta com linguagens como SQL. Alta integridade e consistência.
- **Exemplos:** Registros de vendas, cadastros de clientes, planilhas.

### 1.2 Dados Não Estruturados

- **Definição:** Informações que **não possuem formato fixo ou modelo predefinido**, dificultando o armazenamento e a análise por sistemas tradicionais.
- **Armazenamento:** Sistemas de arquivos distribuídos, ***data lakes*** e repositórios multimídia.
- **Características:** Representam o maior desafio para processamento. Exigem técnicas como **mineração de texto, processamento de linguagem natural (PLN) e visão computacional**.
- **Exemplos:** Imagens, vídeos, áudios, textos livres (e-mails, posts em redes sociais).

### 1.3 Dados Semiestruturados

- **Definição:** Possuem **alguma organização ou marcação**, mas **não seguem o modelo rígido** das tabelas. É uma categoria intermediária.
- **Características:** Estrutura **flexível e adaptável**. Utilizam metadados (dados que descrevem o dado) e formatos de marcação ou pares chave-valor.
- **Armazenamento:** Arquivos em formatos flexíveis ou **bancos NoSQL** (especialmente os orientados a documentos).
- **Exemplos:** Arquivos **XML** (com tags de marcação) e **JSON** (pares de chave e valor).

## 2. Tabela Comparativa dos Tipos de Dados

| CARACTERÍSTICA | DADOS ESTRUTURADOS | DADOS SEMIESTRUTURADOS | DADOS NÃO ESTRUTURADOS |
| :--- | :--- | :--- | :--- |
| **Formato** | Tabelas (linhas x colunas). | Marcadores (tags), pares chave-valor. | Texto livre, multimídia, binário. |
| **Esquema** | **Rígido e predefinido**. | **Flexível e adaptável**. | **Sem esquema fixo**. |
| **Armazenamento Típico** | Bancos Relacionais (SQL). | Bancos NoSQL (Documentos). | *Data Lakes*, sistemas de arquivos, NoSQL. |
| **Facilidade de Análise** | **Fácil** (via SQL). | Média (requer bibliotecas/parsers). | **Difícil** (exige IA, PLN, etc.). |
| **Exemplos** | Planilhas, cadastros (CPF, nome). | XML, JSON, logs de sistema. | Imagens, vídeos, áudios, posts. |

## 3. Análise de Questões de Concurso

### 3.1 Big Data e Diversidade de Dados (INSTITUTO AOCP/SANESUL/2025)

- **Enunciado:** Identificar a afirmativa correta sobre dados estruturados e não estruturados.
- **Gabarito:** **D**. Dados estruturados têm formato rígido e organizado; não estruturados incluem imagens, vídeos e textos sem formato fixo.
- **Análise:** Esta alternativa descreve corretamente a diferença fundamental. É errado afirmar que ambos são armazenados da mesma forma, que estruturados não requerem esquema, ou que não estruturados são mais fáceis de processar.

### 3.2 Exemplos por Tipo de Dado (CESPE/TSE/2024)

- **Enunciado:** "Documentos de uma empresa e postagens nas redes sociais são exemplos de dados estruturados."
- **Gabarito:** **ERRADO.**
- **Análise:** Ambos são exemplos clássicos de dados **não estruturados**, pois consistem em texto livre, imagens e vídeos sem um formato de tabela rígido.

### 3.3 Dados Não Estruturados em Bancos Relacionais (CESPE/TCE-AC/2024)

- **Enunciado:** "Assim como os dados estruturados, os dados não estruturados também podem ser armazenados em bancos de dados relacionais."
- **Gabarito:** **ERRADO**. (Considerado pela banca).
- **Análise:** Embora existam discussões técnicas, o entendimento da banca é que, para os fins de arquitetura de Big Data, bancos relacionais tradicionais não são o local adequado para dados não estruturados. O local ideal são os *Data Lakes*.

### 3.4 Dados Semiestruturados (CESPE/CTI/2024)

- **Enunciado:** "Os dados [...] são considerados semiestruturados quando possuem uma estrutura não homogênea, como arquivos XML e JSON."
- **Gabarito:** **CERTO.**
- **Análise:** "Estrutura não homogênea" é uma forma de descrever um esquema flexível que não é o rígido de uma tabela. É uma definição válida para dados semiestruturados.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (AOCP/SANESUL) | **D** | Dados estruturados (rígido) vs. Não estruturados (imagens/vídeos). |
| **02** (CESPE/EMBRAPA) | **E** | Big Data lida com dados **não estruturados** também. |
| **03** (SELECON/SENAPPEN) | **D** | XML é um exemplo de dado semiestruturado. |
| **04** (IDCAP/IPJB) | **D** | II (NoSQL) e III (não-estruturados exigem técnicas) corretas. |
| **05** (CESPE/TSE) | **E** | Documentos e posts são dados **não estruturados**. |
| **06** (CESPE/TC-DF) | **C** | Big Data são dados não estruturados também, mas não apenas. |
| **07** (CESPE/TC-DF) | **C** | Dados podem ser não estruturados por ineficiência da modelagem tabular. |
| **08** (CESPE/TCE-AC) | **E** | Dados não estruturados **não** são tipicamente de bancos relacionais. |
| **09** (IDHTEC/Itapissuma) | **D** | Big Data processa volumes massivos para *insights* rápidos. |
| **10** (IBFC/CORREIOS) | **A** | Imagens são um elemento de dados não estruturados. |
| **11** (CESPE/CTI) | **C** | XML e JSON são semiestruturados com estrutura não homogênea. |
| **12** (FGV/Caraguatatuba) | **D** | I e II corretas; III errada (não-estruturados são suportados por bancos). |
| **13** (CETREDE/Caucaia) | **D** | Vantagem dos estruturados: fáceis de consultar com SQL. |