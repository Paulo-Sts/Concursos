# Data Lake

## 1. Conceito e Definição
- Repositório centralizado que permite armazenar grandes volumes de dados em seu formato bruto (raw data).
- Os dados podem ser estruturados, semiestruturados ou não estruturados.
- Diferentemente do Data Warehouse, que armazena dados já estruturados e otimizados para consultas, o Data Lake aceita dados sem pré-processamento.

### 1.1 Schema-on-Read x Schema-on-Write
- Schema-on-read: a estruturação e organização dos dados ocorre no momento da leitura.
  - Os dados são ingeridos exatamente como se encontram na origem.
  - A estrutura é aplicada apenas quando os dados são acessados para análise.
- Schema-on-write: os dados são transformados e estruturados antes de serem gravados (característico do Data Warehouse).
  - Ocorre o processo de ETL (Extração, Transformação e Carga).
  - Os dados são organizados em um modelo geralmente dimensional.

### 1.2 Tipos de Dados no Data Lake
- Dados estruturados: tabelas, bancos de dados relacionais.
- Dados semiestruturados: JSON, XML, arquivos com tags e marcadores.
- Dados não estruturados: vídeos, áudios, imagens, documentos de texto.

> [!CAUTION] OBSERVAÇÃO:
> - O Data Lake não guarda apenas dados não estruturados; comporta qualquer tipo de dado.
> - Afirmações que limitam o Data Lake a um único tipo de dado são incorretas.

## 2. Características Principais
- Armazenamento de qualquer tipo de dado (estruturado, semiestruturado e não estruturado).
- Escalabilidade: crescimento conforme a demanda, geralmente em ambientes de nuvem.
- Baixo custo de armazenamento: uso de hardware commodity ou soluções de nuvem com pagamento por uso.
- Flexibilidade: não exige esquema pré-definido para ingestão de dados.
- Integração: conexão com diversas fontes de dados, internas e externas.

### 2.1 Escalabilidade Horizontal
- Funciona por meio de diversos computadores interligados em rede.
- Cada computador contribui com capacidade de armazenamento.
- Um nó central faz a gestão, enquanto os nós de dados armazenam as informações.
- Caso os discos rígidos estejam cheios, basta adicionar outro computador à rede.
- Solução de baixo custo e fácil gerenciamento comparado ao Data Warehouse.

### 2.2 Hardware Commodity e Nuvem
- Hardware commodity: computadores comuns, de baixo custo.
- Nuvem: Amazon Web Services, Microsoft Azure, Google Cloud.
- Modelo de pagamento proporcional ao consumo.

## 3. Arquitetura
- Ingestão: dados coletados de múltiplas fontes e enviados ao Data Lake.
  - Pode ocorrer em lote (batch) ou em tempo real (streaming).
- Armazenamento: dados permanecem em formato original até serem necessários para análise.
- Processamento: tratamento e modelagem ocorrem na leitura (schema-on-read).
  - Inclui limpeza, transformação e modelagem.
- Consumo: cientistas e analistas de dados acessam para criar modelos, relatórios e análises.

> [!TIP] DICAS:
> - Big Data não se limita ao armazenamento, mas envolve todo o processo, desde a ingestão até o processamento e uso final.
> - O dado armazenado sem processamento não gera valor; o processamento resulta na geração de datasets.

## 4. Vantagens
- Alta flexibilidade para diferentes tipos de análise (diferente do Data Warehouse, restrito a dashboards e consultas OLAP).
- Armazenamento de dados históricos completos, sem perda de detalhes.
- Suporte para Big Data Analytics, aprendizado de máquina e inteligência artificial.

## 5. Desafios
- Governança de dados: sem controle adequado, o Data Lake pode virar um "Data Swamp" (depósito caótico).
- Segurança: necessidade de políticas de acesso, criptografia e auditoria.
- Qualidade da informação: dados brutos podem conter inconsistências ou redundâncias.

> [!CAUTION] OBSERVAÇÃO:
> - A governança é essencial para garantir a utilidade, integridade e segurança dos dados.
> - Sem organização adequada, o Data Lake corre o risco de se tornar um ambiente descontrolado, comprometendo a segurança e possibilitando vazamentos de informações.

## 6. Tecnologias
- On-premises (local): Hadoop Distributed File System (HDFS).
- Nuvem:
  - Amazon S3.
  - Azure Data Lake Storage.
  - Google Cloud Storage.

## 7. Comparativo Data Lake x Data Warehouse
| CARACTERÍSTICA | DATA LAKE | DATA WAREHOUSE |
|----------------|-----------|----------------|
| Tipo de dado | Estruturados, semiestruturados e não estruturados | Principalmente estruturados |
| Processamento | Schema-on-read (estruturação na leitura) | Schema-on-write (estruturação na escrita) |
| Processo | ELT (Extração, Carga e Transformação) | ETL (Extração, Transformação e Carga) |
| Custo | Baixo (hardware commodity) | Elevado |
| Flexibilidade | Alta | Baixa/moderada |
| Finalidade | Análises avançadas, IA, machine learning | Dashboards, consultas operacionais OLAP |