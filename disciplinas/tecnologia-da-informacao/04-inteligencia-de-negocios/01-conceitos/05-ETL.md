# ETL

## 1. Definição de ETL
- É o processo responsável por extrair dados de diversas fontes, transformá-los conforme as regras de negócio e carregá-los em um Data Warehouse (DW) ou Data Mart.
- O processo integra dados de fontes heterogêneas de forma homogênea e concisa.
- É uma etapa fundamental em qualquer projeto de Business Intelligence (BI).

> [!CAUTION] OBSERVAÇÃO: 
> - O ETL é uma das fases mais longas e complexas de um projeto de DW, não se resumindo apenas à seleção de dados.

## 2. Etapas do Processo ETL

### 2.1 Extração
- É a primeira etapa do processo ETL.
- Consiste em obter e ler os dados provenientes dos sistemas OLTP (sistemas transacionais) e copiá-los para uma área temporária (staging area).
- Principais fontes de dados:
  - Bancos de dados relacionais;
  - Arquivos CSV;
  - Arquivos Excel;
  - Fontes recebidas via API;
  - Sistemas ERP e CRM;
  - Logs;
  - Sistemas Legados;
  - Fontes de dados externas.
- Tipos de extração:
  - Completa: realizada na primeira carga, quando todos os dados são extraídos.
  - Gradual (incremental): realizada nas cargas seguintes, extraindo apenas os dados novos ou alterados.
- O principal desafio da extração é determinar quais dados são necessários e que tipos de filtros devem ser aplicados.

> [!CAUTION] OBSERVAÇÃO: 
> - A extração é a etapa de obtenção de dados dos sistemas OLTP, não do Data Warehouse.

### 2.2 Transformação
- É a etapa mais longa do processo ETL.
- Realizada na Staging Area (área de preparação).
- Baseada nas regras de negócio definidas pela organização.

#### 2.2.1 Limpeza de Dados
- Envolve o tratamento de:
  - Ruídos;
  - Dados duplicados;
  - Erros de formatação;
  - Valores ausentes (dados incompletos);
  - Outliers (pontos fora da curva, como dados errados).

> [!CAUTION] OBSERVAÇÃO: 
> - Dado com incompletude é um dado faltante, não um dado fora do domínio do atributo.

#### 2.2.2 Padronização e Formatação
- Inclui a padronização de medidas e formatos.
- A normalização de dados busca deixar todos os dados na mesma escala.

#### 2.2.3 Transformações Relacionadas à Segurança
- Aplicação de regras de segurança e acesso aos dados.

#### 2.2.4 Filtragem e Seleção
- Seleção dos dados relevantes para o DW.

#### 2.2.5 Enriquecimento de Dados
- Os dados são buscados em outras fontes para complementar informações em uma tabela.

#### 2.2.6 Transformações de Dados
- Agregações (somas, médias, contagens);
- Cálculo de campos derivados;
- Transformação de tipos de dados;
- Discretização de atributos numéricos;
- Imputação de valores ausentes;
- Seleção de atributos relevantes;
- Verificação de cálculos inválidos;
- Tradução de valores codificados (ex: converter "1" para "Masculino" e "2" para "Feminino");
- Geração de chaves substitutas (surrogate keys).

> [!TIP] DICAS: 
> - A transformação é a etapa que consome mais tempo no ETL.

> [!CAUTION] OBSERVAÇÃO: 
> - As regras de negócio já existem, portanto o ETL não as define; ele apenas as aplica.

### 2.3 Carga
- É a etapa final do processo ETL.
- Consiste em inserir os dados transformados no Data Warehouse ou no Data Mart.
- Características da carga:
  - Pode ser realizada em lote (periódica) ou em tempo real (contínua).
  - Intervalo possível para carga periódica: 24 horas.
  - Envolve modelagem do esquema.
  - Carregamento inicial e atualizações incrementais.
  - Validação dos dados.
  - Avaliação da qualidade dos dados.
  - Indexação e otimização dos dados.

> [!CAUTION] OBSERVAÇÃO: 
> - A fase de carga insere os dados transformados no DW, não nos bancos de dados transacionais da empresa.

## 3. Staging Area (Área de Preparação)
- É uma área intermediária onde os dados coletados são armazenados antes de serem processados e transportados para o destino final.
- Localiza-se entre as fontes de dados e os destinos de dados (DW, Data Mart).
- Armazena os dados selecionados provenientes das diversas fontes para serem usados pelo processo de ETL.

> [!CAUTION] OBSERVAÇÃO: 
> - A transformação é realizada na Staging Area, que é uma área temporária de preparação.

## 4. Conceitos Fundamentais do ETL

### 4.1 Processo Sequencial
- As etapas de extração, transformação e carga não são realizadas simultaneamente (paralelamente), mas sim de forma sequencial.

### 4.2 Integração de Dados Heterogêneos
- O ETL é o processo utilizado para integrar bancos de dados heterogêneos.

### 4.3 Diferenciação do OLAP
- A análise multidimensional dos dados não é realizada na fase do ETL.
- As visões específicas de dados (análises multidimensionais) são geradas após o DW, nas operações OLAP.

> [!CAUTION] OBSERVAÇÃO: 
> - ETL não possui capacidades analíticas multidimensionais; isso é função do OLAP.

### 4.4 Metadados
- A ferramenta ETL não tem a função de gerar metadados.

> [!CAUTION] OBSERVAÇÃO: 
> - O ETL é um processo preparatório, não analítico. A análise dos dados ocorre nas etapas posteriores, como no OLAP.