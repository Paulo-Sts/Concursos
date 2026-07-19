# Anotações

# Conceitos Fundamentais de Dados

## 1.1 O que São Dados?

- **Dados:** representações simbólicas de informações; podem ser processadas ou analisadas para extrair significado.
- Exemplos: números, palavras, medidas, observações ou descrições de coisas.
- Dados alimentam processos analíticos, algoritmos de *machine learning*, permitem tomada de decisões e execução de operações.

> [!TIP] DICAS
> - O valor **37,5** isoladamente é um **dado**.
> - Ao afirmar que 37,5 representa a **temperatura corporal**, tem-se uma **informação**.
> - Ao afirmar que 37,5 indica **ausência de febre**, tem-se um **conhecimento**.
> - A **sabedoria** resulta da consolidação e padronização de vários conhecimentos, orientando a tomada de decisão.

### 1.1.1 Dado x Informação x Conhecimento x Sabedoria (DIKW)

| NÍVEL | DESCRIÇÃO | EXEMPLO |
|-------|-----------|---------|
| **Dado** | Representação simbólica bruta | 37,5 |
| **Informação** | Dado processado/interpretado | Temperatura corporal = 37,5 |
| **Conhecimento** | Informação aplicada em contexto | 37,5 = ausência de febre |
| **Sabedoria** | Consolidação de conhecimentos para decisão | Protocolo de conduta para febre |

## 1.2 Processos Geradores de Dados

- Qualquer sistema ou mecanismo que **cria ou coleta dados**.
- Podem ser **manuais** ou **automatizados**.
- Exemplos:
  - **Sensores IoT:** capturam dados do ambiente físico (temperatura, pressão).
  - **Transações Financeiras:** sistemas de pagamento/compras registram informações.
  - **Redes Sociais:** geram dados sobre interações humanas (postagens, curtidas, comentários).
  - **Sistemas Corporativos:** ERPs, CRMs geram dados a partir de transações empresariais.

## 1.3 Tipos de Dados – Quantitativos x Qualitativos

### 1.3.1 Dados Quantitativos (Numéricos)
- Podem ser **medidos e expressos numericamente**.

| SUBTIPO | DESCRIÇÃO | EXEMPLOS |
|---------|-----------|----------|
| **Contínuos** | Valores no conjunto dos números reais; intervalo infinito de possibilidades | Altura, peso, temperatura |
| **Discretos** | Valores contáveis e inteiros | Número de filhos, quantidade de itens |

### 1.3.2 Dados Qualitativos (Categóricos)
- Dados **descritivos** que não possuem representação numérica direta.

| SUBTIPO | DESCRIÇÃO | EXEMPLOS |
|---------|-----------|----------|
| **Nominais** | Categorias **sem ordem** implícita | Cor dos olhos, sexo, transação fraudulenta/não fraudulenta |
| **Ordinais** | Categorias com **ordem implícita** | Nível de escolaridade, classificação de altura (baixa/média/alta) |

> [!CAUTION] OBSERVAÇÃO
> **Em atributos ordinais, não é possível quantificar a diferença entre os valores.** Exemplo: fundamental, médio, superior – é possível ordenar, mas não faz sentido realizar operações matemáticas entre esses níveis.

## 1.4 Tipos de Dados – Quanto à Estrutura

| TIPO | DESCRIÇÃO | EXEMPLOS |
|------|-----------|----------|
| **Estruturados** | Organizados em tabelas com colunas e linhas; esquema pré-definido | Bancos de dados relacionais, planilhas (CSV, XLSX) |
| **Semiestruturados** | Não seguem tabela rígida, mas têm alguma estrutura | XML, JSON, documentos NoSQL |
| **Não Estruturados** | Sem estrutura pré-definida; formato binário/bruto | Texto livre, imagens, vídeos, áudios, publicações em redes sociais |

### 1.4.1 Características Importantes

- **Dados estruturados:**
  - Extração de informações por consultas SQL (ex.: `SELECT`).
  - Atributos e campos definidos por um **esquema** (ex.: `CREATE TABLE`).
  - Dados de um mesmo registro possuem relação entre si.

- **Dados não estruturados:**
  - Não permitem consultas SQL tradicionais.
  - Requerem tecnologias como **inteligência artificial** para reconhecimento de padrões.
  - O simples armazenamento em um campo de banco de dados relacional **não** os torna estruturados.

> [!TIP] DICAS
> - **Planilhas eletrônicas** (linhas e colunas) → dados **estruturados**.
> - **Arquivos XML e JSON** → dados **semiestruturados**.
> - **Textos livres, imagens, vídeos, áudios, redes sociais** → dados **não estruturados**.
> - **Linguagens de programação (código-fonte)** → dados **não estruturados**.

## 1.5 Tabela Resumo – Dados

| ASPECTO | ESTRUTURADOS | SEMIESTRUTURADOS | NÃO ESTRUTURADOS |
|---------|--------------|------------------|------------------|
| **Formato** | Tabelas (linhas/colunas) | Tags, pares chave-valor | Bruto/binário |
| **Esquema** | Fixo/pré-definido | Flexível | Inexistente |
| **Consulta** | SQL (SELECT) | Consultas NoSQL | IA/ML para extração |
| **Exemplos** | BD relacionais, planilhas | XML, JSON | Textos, imagens, vídeos, áudio |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/FUB/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/2023)

A respeito de dados e informações, julgue os itens que se seguem. Quando ocorre o tratamento de um ou mais dados, é gerada a informação, a qual constitui conhecimento quando aplicada em determinado contexto.

**Gabarito:** C (Correto)

## Questão 02
(CESPE/CEBRASPE/SECONT/AUDITOR DO ESTADO/ÁREA TECNOLOGIA DA INFORMAÇÃO/2022)

Com relação a dado, informação e conhecimento, julgue os itens subsecutivos.

Os termos CÉU e AZUL, quando utilizados separadamente, representam dados, enquanto a expressão CÉU É AZUL representa uma informação.

**Gabarito:** C (Correto)

## Questão 03
(CESPE/CEBRASPE/TCE RJ/ANALISTA DE CONTROLE EXTERNO/ÁREA ORGANIZACIONAL/TECNOLOGIA DA INFORMAÇÃO/2022)

Julgue os itens a seguir, referentes à informação e a dados, estruturados e não estruturados.

A informação normalmente envolve a participação humana na sua estruturação e na busca do seu significado, enquanto os dados são mais facilmente obtidos e quantificados por máquinas.

**Gabarito:** C (Correto)

## Questão 04
(CESPE/CEBRASPE/MINISTÉRIO DA ECONOMIA/TECNOLOGIA DA INFORMAÇÃO/CIÊNCIA DE DADOS/2020)

Acerca de conceitos, premissas e aplicações de big data, julgue o item subsequente.

Um atributo é denominado ordinal quando as variáveis podem ser colocadas em ordem, mas não é possível quantificar a diferença entre os resultados.

**Gabarito:** C (Correto)

## Questão 05
(CESPE/CEBRASPE/SERPRO/ANALISTA/ESPECIALIZAÇÃO: CIÊNCIA DE DADOS/2021)

Julgue o item subsequente relativo a conceitos de ingestão de dados estruturados, semiestruturados, não estruturados e em streaming.

Os dados não estruturados constam de bancos de dados relacionais que são eminentemente pesquisáveis tanto por meio de consultas realizadas por humanos quanto por meio daquelas realizadas por algoritmos que usam tipos de dados e nomes de campos, como alfabéticos ou numéricos, moeda ou data.

**Gabarito:** E (Errado) - Essas características correspondem a dados **estruturados**, não não estruturados.

## Questão 06
(CESPE/CEBRASPE/TCE-RJ/ANALISTA DE CONTROLE EXTERNO/2022)

Julgue o item a seguir, referente à informação e a dados, estruturados e não estruturados.

No contexto de Big Data, os dados em formato de textos longos, de vídeos ou de imagens são considerados dados estruturados, quando armazenados em um campo de um banco de dados relacional.

**Gabarito:** E (Errado) - O simples armazenamento em um campo de banco de dados relacional **não** torna os dados estruturados; eles permanecem não estruturados.

## Questão 07
(INSTITUTO CONSULPLAN/MPE-MG/ANALISTA/ÁREA: TECNOLOGIA DA INFORMAÇÃO/GESTÃO DE PROJETOS DE TI/2023)

Dado é a representação utilizada para gerar uma informação. Um dado pode ser estruturado ou não estruturado. Em relação às diferenças entre dados estruturados e dados não estruturados, marque V para as afirmativas verdadeiras e F para as falsas.

( ) Em dados estruturados, dados de um mesmo registro possuem relação entre eles.
( ) Textos, documentos, banco de dados, redes sociais, imagens, vídeos e áudios são exemplos de dados não estruturados.
( ) Dados estruturados permitem que tipos de dados diferentes das estruturas preestabelecidas sejam carregados.
( ) Em dados estruturados, atributos e campos são definidos por um esquema.

A sequência está correta em

a) F, V, V, F.
b) V, V, V, V.
c) V, F, F, V.
d) F, F, F, F.

**Gabarito:** c

## Questão 08
(CESPE/CEBRASPE/SEPLAN-RR/ANALISTA DE PLANEJAMENTO E ORÇAMENTO APO/ÁREA TECNOLOGIA DA INFORMAÇÃO/2023)

Com base nos conceitos de dados estruturados e não estruturados, de análise exploratória de dados e de dados abertos, julgue os itens seguintes. Dados de redes sociais são exemplos de dados não estruturados.

**Gabarito:** C (Correto)

## Questão 09
(FUNDATEC/BRDES/ANALISTA/ÁREA: CIÊNCIA DE DADOS/2023)

Assinale a alternativa que contém um exemplo de dados não estruturados.

a) Dados extraídos de uma rede social de um banco podem ser classificadas em polaridades como positivas ou negativas, ou agrupadas por similaridade de assunto.
b) Um sistema bancário armazena dados sobre seus clientes, sobre suas respectivas contas bancárias e sobre as transações executadas sobre tais contas.
c) Funcionários de um departamento de recursos humanos observam os candidatos a uma vaga de emprego e fazem anotações sobre as suas atitudes durante a realização de atividades de um processo de seleção.
d) Uma empresa deseja lançar um novo produto e, para isso, realiza pesquisas sobre sua aceitação com um conjunto específico de pessoas que representa o público-alvo.
e) Uma corrida de Fórmula 1 na qual se medem os tempos que cada piloto gasta para chegar em diferentes trechos de um circuito.

**Gabarito:** a

## Questão 10
(CESPE/CEBRASPE/DPE RO/ANALISTA DA DEFENSORIA PÚBLICA/ÁREA: REDES E COMUNICAÇÃO DE DADOS/2022)

As fontes de dados não estruturados incluem

a) a planilha eletrônica.
b) a rede social.
c) a linguagem de programação.
d) o arquivo XML.
e) o banco de dados.

**Gabarito:** b

## Questão 11
(IBADE/SES-MG/ESPECIALISTA EM POLÍTICAS E GESTÃO DA SAÚDE/ÁREA: TI/2022)

Os dados constantes em uma planilha eletrônica, organizados em linhas e colunas, são chamados dados:

a) alinhados.
b) estruturados.
c) indexados.
d) relacionados.
e) descriminados.

**Gabarito:** b

## Questão 12
(CONSULPLAN/MPE PA/ANALISTA DE SISTEMAS/ÁREA: SUPORTE À REDE DE COMPUTADORES/2022)

Dados são um conjunto de fatos em estado bruto que podem ser utilizados para tomadas de decisão. Os dados podem ser divididos entre estruturados e não estruturados. Sobre os dados estruturados, assinale a afirmativa correta.

a) Mensagens de e-mail são dados estruturados.
b) Dados estruturados são organizados em linhas e colunas.
c) Dados estruturados são armazenados em arquivos no formato "TXT".
d) Mecanismos de busca possuem dificuldade para pesquisar dados estruturados.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | C |
| 03 | C |
| 04 | C |
| 05 | E |
| 06 | E |
| 07 | c |
| 08 | C |
| 09 | a |
| 10 | b |
| 11 | b |
| 12 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*