# Ingestão de Dados e Pipeline

## 1. Ingestão de Dados
- Processo de coletar e importar dados de diversas fontes para um sistema de armazenamento ou processamento, como data lakes, data warehouses ou plataformas de big data.
- Objetivo: garantir que os dados de múltiplas origens estejam centralizados e disponíveis para análise, relatórios e aplicações.
- É considerado um dos tópicos mais relevantes dentro do estudo de big data.
- Em alguns casos, a ingestão pode ser direcionada para plataformas maiores de big data que não necessariamente utilizam o conceito de data lake.

### 1.1 Fontes Comuns
- Bancos de dados (sql, nosql);
- Apis e serviços web;
- Arquivos (csv, xml, json);
- Streams de eventos (kafka);
- Sistemas corporativos (erp, crm);
- Sensores e dispositivos iot.

### 1.2 Etapas da Ingestão
- Conexão às fontes de dados: identificação e configuração de acessos.
- Captura dos dados: extração dos dados de origem, em tempo real ou em lote.
- Transporte: envio seguro e eficiente para o destino.
- Armazenamento inicial: gravação no destino (data lake, dw, sistema analítico).
- Transformação preliminar (opcional): limpeza ou padronização básica antes do uso, para organizar e avaliar a qualidade dos dados.
- A proteção dos dados durante o transporte pode ser garantida por meio de vpns, especialmente quando trafegam pela internet.
- O armazenamento pode ocorrer em um data lake ou em sistemas analíticos.
- O processo básico, chamado de ingestão bruta ou clássica, consiste em simplesmente transferir os dados da fonte para o destino sem alterações.
- A escolha por realizar ou não transformações iniciais depende do objetivo do processo.

> [!TIP] DICAS: 
> - Ingestão bruta = transferência direta dos dados da fonte para o destino, sem alterações.

> [!CAUTION] OBSERVAÇÃO: 
> - A transformação preliminar é opcional e serve para facilitar o uso posterior dos dados, mas não é obrigatória em todas as abordagens.

### 1.3 Tipos de Ingestão

#### 1.3.1 Batch Ingestion (Ingestão em Lote)
- Processa grandes volumes de dados em intervalos programados.
- Vantagens:
  - Otimiza recursos;
  - Adequado para análises históricas.
- Desvantagens:
  - Dados não ficam disponíveis imediatamente (latência).
- Exemplo: atualização diária de dados de vendas em um data warehouse.
- Geralmente utiliza clusters de computadores, como no hdfs.
- Os dados são extraídos em horários específicos (ex.: à noite) e transferidos de forma periódica.
- Está associada ao processamento de grandes volumes de dados em intervalos programados, evitando impacto no ambiente de produção.

#### 1.3.2 Streaming Ingestion (Ingestão Contínua)
- Processa dados incrementalmente à medida que chegam.
- Vantagens:
  - Baixa latência;
  - Ideal para decisões em tempo real.
- Desvantagens:
  - Exige maior capacidade de processamento e sistemas especializados;
  - Possível inconsistência de dados em sistemas distribuídos.
- Exemplo: processamento de dados de sensores iot ou transações financeiras em tempo real.
- Consiste no envio imediato dos dados ao destino conforme eles são gerados.
- Em situações de busca por informações, pode ocorrer perda de qualidade devido a dados temporariamente desatualizados.
- O processamento de dados provenientes de diferentes fontes (ex.: câmeras de vigilância, transações financeiras) exige soluções específicas, sendo a ingestão contínua a abordagem adequada.

### 1.4 Ferramentas de Ingestão
- Batch:
  - Apache sqoop (extração de dados de sistemas relacionais);
  - Talend (conhecido desde meados de 2005 a 2007);
  - Pentaho data integration (etl e mineração de dados).
- Streaming:
  - Apache kafka;
  - Apache flume;
  - Aws kinesis (solução da amazon);
  - Apache nifi.
- Nuvem:
  - Azure data factory;
  - Google dataflow;
  - Aws glue.
- No processamento em tempo real, o apache kafka é uma das ferramentas mais conhecidas, atuando com produtores, broker (armazena dados em filas organizadas em tópicos) e consumidores.
- Quanto mais consumidores disponíveis, mais rapidamente a fila do broker é processada.

> [!TIP] DICAS: 
> - Kafka: produtor ⟶ broker (tópicos) ⟶ consumidor.
> - Quanto mais consumidores, mais rápido o processamento da fila.

## 2. Pipeline de Dados
- Conjunto organizado de etapas e processos que coletam, processam, transformam e entregam dados desde as fontes até o consumo final.
- É como uma linha de produção para dados, garantindo que eles fluam de forma contínua, controlada e confiável.
- O pipeline de dados é definido como a arquitetura completa de big data, composta por etapas organizadas que conduzem as informações desde a fonte até o consumo final.
- O fluxo do pipeline inicia com a ingestão, seguida pelo armazenamento, transformação, novo armazenamento dos dados transformados e, por fim, processamento analítico que os converte em informações utilizáveis.
- A automação desse fluxo caracteriza o pipeline como um conjunto estruturado de processos.

### 2.1 Componentes do Pipeline

#### 2.1.1 Ingestão de Dados
- Captura de dados de fontes diversas (batch ou streaming).
- Ferramentas: apache kafka, aws kinesis, apache nifi.

#### 2.1.2 Armazenamento Bruto
- Depósito inicial dos dados no formato original (data lake, hdfs, nuvem).
- Tecnologias: amazon s3, azure data lake, google cloud storage.

#### 2.1.3 Processamento e Transformação
- Limpeza, enriquecimento, padronização e aplicação de regras de negócio.
- Pode ser em lote (batch) ou em tempo real (streaming).
- Ferramentas: apache spark (processamento em tempo real), flink (lote e tempo real), beam.
- A transformação inclui operações como limpeza, enriquecimento, padronização, normalização e aplicação de regras de negócio.

#### 2.1.4 Armazenamento Estruturado
- Dados processados vão para um repositório otimizado para consultas.
- Tecnologias: data warehouse (snowflake, bigquery, redshift).
- Os dados são inicialmente enviados para um data lake, transformados e organizados em um dataset estruturado, podendo ser carregados em um data warehouse para maior eficiência no armazenamento e análise.

#### 2.1.5 Consumo e Visualização
- Aplicações analíticas, dashboards e relatórios.
- Ferramentas: tableau, power bi, grafana, kibana.

#### 2.1.6 Orquestração e Automação
- Coordenação das tarefas do pipeline, garantindo execução na ordem certa.
- Ferramentas: apache airflow, luigi, aws step functions.

#### 2.1.7 Monitoramento e Governança
- Rastreamento de desempenho, qualidade e segurança dos dados.
- Envolve políticas de acesso, auditoria e conformidade (lgpd, gdpr).
- A governança envolve a avaliação contínua do pipeline, verificando se ele ainda está funcionando adequadamente, quem tem acesso aos dados e se as regras de proteção de dados pessoais estão sendo respeitadas.

### 2.2 Tipos de Pipeline
- Batch pipeline: processa grandes blocos de dados em intervalos programados.
- Streaming pipeline: processa eventos em tempo real, com baixa latência.
- Lambda architecture: combina batch + streaming para maior flexibilidade.
- Kappa architecture: foca apenas em pipelines de streaming simplificados, mas permite recuperar dados em lotes durante o processo.

### 2.3 Benefícios do Pipeline
- Escalabilidade: suporta crescimento no volume de dados sem perda de desempenho, bastando replicar o processo em diferentes infraestruturas.
- Automação: reduz esforço manual e erros humanos, evitando a dependência de intervenção manual.
- Consistência: mesmas regras e formatos aplicados em todo o processo a cada execução.
- Agilidade: dados ficam disponíveis rapidamente para análise, eliminando a necessidade de reinvenção a cada rodada e diminuindo o tempo de análise.

> [!CAUTION] OBSERVAÇÃO: 
> - O pipeline não se limita a uma única estrutura simples, mas é composto por várias etapas interligadas que formam um sistema organizado.
> - O pipeline refina e limpa os dados brutos por meio da transformação, facilitando sua utilização no consumo final.
> - Na etapa de ingestão, os dados são coletados de diversas fontes e transportados para um armazenamento centralizado, comumente chamado de data lake.