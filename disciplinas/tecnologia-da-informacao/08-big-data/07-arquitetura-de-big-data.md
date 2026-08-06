# Arquitetura de Big Data

## 1. Conceito De Big Data
- Big data refere-se a grandes bases de dados que incluem dados não estruturados, semiestruturados e estruturados (com presença de tabelas).
- Suas principais características são variedade, volume e velocidade.

## 2. Arquitetura De Big Data
- A arquitetura inicia com as fontes de dados, que podem seguir dois caminhos principais: processamento em batch (lote) e processamento em tempo real.
- O objetivo final é realizar ciência de dados, ou seja, gerar conhecimento a partir da grande base de dados.

### 2.1 Fontes De Dados
- Bancos de dados relacionais.
- Arquivos diversos, como logs de servidores.
- Internet das Coisas (IoT): dados produzidos por dispositivos conectados à internet, como celulares, geladeiras, sensores de temperatura.

### 2.2 Armazenamento De Dados
- Repositórios de arquivos distribuídos em vários nós.
- NoSQL.
- Data Lake: uma grande estrutura de dados que armazena dados brutos em seu formato nativo.

### 2.3 Processamento Em Lote (Batch)
- Envolve pré-processamento de dados, como agregações e filtragens.
- Ocorre em períodos determinados.
- Ferramentas comuns: Hive, Pig, Map-Reduce, programas em Python.
- Nesse momento, os dados são retirados do Data Lake e encaminhados para a base de modelagem ou pré-modelagem.

### 2.4 Processamento Em Tempo Real
- Envolve a captura e ingestão de mensagens em tempo real.
- Utiliza um repositório de ingestão (buffer) para armazenamento temporário.
- Processamento de fluxo com pré-processamento, filtragem e agregação.
- Os dados processados são armazenados em formato estruturado para serem consumidos por ferramentas de analytics.

> [!CAUTION] OBSERVAÇÃO:
> - O processamento em tempo real prioriza a velocidade em detrimento da confiabilidade dos dados.

### 2.5 Orquestração
- Consiste na automatização dos fluxos de trabalho de todo o processo.

## 3. Variações De Arquitetura

### 3.1 Arquitetura Lambda
- Possui dois caminhos simultâneos:
  - Caminho quente: dados são enviados para análise do cliente em tempo real.
  - Caminho frio: processamento em lote com uma camada intermediária de serviços que prepara os dados para o cliente.
- Consome mais recursos por manter dois processamentos simultâneos.

### 3.2 Arquitetura Kappa
- Possui um único caminho, simplificando o processamento.
- É o caminho mais rápido para chegar ao analytics em tempo real.
- Os dados principais são processados em lote antes de serem enviados ao cliente.

## 4. Papéis Dos Envolvidos Em Projetos De Big Data

### 4.1 Engenheiro De Big Data
- Engenheiro de dados com foco específico em big data.
- Responsável pela infraestrutura.
- Implementa a arquitetura de big data.

## 5. Big Data Em Relação A Outras Disciplinas
- Banco de dados.
- Aprendizado de máquina.
- Business Intelligence.
- Computação em nuvem.
- Estatística.
- Engenharia de software.
- Relaciona-se com todas as áreas de conhecimento.