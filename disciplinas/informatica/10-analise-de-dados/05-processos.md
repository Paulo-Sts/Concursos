# Processos ETL, DW e Modelagem Multidimensional

## 1. Processos ETL (Extract, Transform, Load)

#### Extract (extrair)
- Extração de dados de diversas bases transacionais (OLTP).
- Bases transacionais: sistemas de cadastro, consulta, etc.
- Pode incluir staging area (área de preparação), não obrigatória.

#### Staging area
- Área intermediária para preparação dos dados.
- Objetivos:
  - Padronização, sincronização, definição de relevância.
  - Preservar dados de fontes voláteis e assíncronas.
  - Manter características originais sem transformação.
- Atributos-chave: volatilidade, representatividade, velocidade.

#### Transform (transformar)
- Dados são compilados, convertidos, reformatados e limpos.
- Depende da qualidade dos dados de origem e requisitos de negócio.
- Palavras-chave: limpeza, conversão, padronização, unificação, formatação, classificação, filtragem.
- Pode gerar ODS/DDS (Operational Data Store / Dynamic Data Store).

#### ODS/DDS
- Repositório de dados operacionais/dinâmicos.
- Características:
  - Uso de chaves de negócio.
  - Alta granularidade.
  - Informação consistente.
  - Não exige normalização.
  - Base voltada à leitura.

#### Load (carregar)
- Dados são carregados para o destino (DW, Data Mart, etc.).
- Pode ser feito em massa ou registro a registro.
- Objetivo: alimentar sistemas OLAP.

## 2. Data Warehouse (DW)
- Repositório centralizado de dados históricos e analíticos.
- Objetivo: apoiar a tomada de decisão.
- Características:
  - Orientado a assuntos.
  - Integrado (diversas fontes).
  - Não volátil (dados não são alterados).
  - Variável no tempo (atualizações periódicas).
  - Histórico de dados.

#### EDW (Enterprise Data Warehouse)
- DW corporativo que centraliza dados de toda a organização.

#### Diferenças entre DW e banco de dados transacional
- BD Transacional: operacional, volátil, focado em transações.
- DW: analítico, não volátil, focado em consulta e análise.

## 3. Data Mart (DM)
- Subconjunto do DW, focado em uma área específica (ex.: vendas, marketing).
- Departamentalizado.

#### Abordagens de criação
- **Top-down (Inmon):** cria-se primeiro o DW, depois os DMs.
- **Bottom-up (Kimball):** cria-se DMs primeiro, depois consolida-se em DW.

## 4. Modelagem multidimensional
- Técnica de projeto lógico para DW.
- Contrasta com modelagem entidade-relacionamento.
- Objetivo: otimizar consultas (não transações).
- Baixa normalização.

#### Componentes
- **Tabela Fato:** contém métricas (valores quantitativos).
- **Tabelas Dimensão:** contêm descrições qualitativas.
- Relacionamento: N:1 entre fato e dimensão.

#### Esquemas
- **Esquema Estrela (Star Schema):**
  - Uma tabela fato + várias dimensões.
  - Baixa normalização → maior redundância → mais espaço.
  - Maior agilidade na recuperação de dados.
- **Esquema Floco de Neve (Snowflake Schema):**
  - Tabelas dimensão normalizadas (até 3FN).
  - Menor redundância → menos espaço.
  - Menor agilidade (mais joins).

#### Dimensão degenerada
- Dimensão inserida como coluna na tabela fato (não em tabela dimensão).

## 5. Operações multidimensionais (OLAP)

#### Pivot (Rotação)
- Mudança de perspectiva: troca linhas por colunas.

#### Slice (Fatiamento)
- Restrição dos dados a um valor fixo em uma dimensão.

#### Dice (Corte)
- Restrição em duas ou mais dimensões, criando um subcubo.

#### Drill Down
- Aumenta o nível de detalhe → diminui a granularidade.

#### Roll Up / Drill Up
- Diminui o nível de detalhe → aumenta a granularidade.

#### Drill Through
- Mudança para outra dimensão sem hierarquia.
- Ou busca de granularidade além da existente no cubo.

#### Drill Across
- Consulta que envolve múltiplos cubos com dimensões em comum.
- Ou pulo de nível intermediário dentro da mesma dimensão.

## 6. Considerações finais
- ETL: processo de extrair, transformar e carregar dados.
- DW: repositório central para análise histórica.
- DM: visão departamental do DW.
- Modelagem multidimensional: foco em consulta, com tabelas fato e dimensão.
- Operações OLAP: permitem análise flexível e multidimensional dos dados.