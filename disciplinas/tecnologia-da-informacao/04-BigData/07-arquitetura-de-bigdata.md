# Anotações

# ARQUITETURA DE BIG DATA

## 1. Componentes da Arquitetura de Big Data

### 1.1 Visão Geral do Fluxo

- Uma arquitetura de Big Data é a estrutura que organiza o fluxo de dados desde a sua origem (fontes) até a geração de valor (análise e tomada de decisão).
- A jornada dos dados passa por etapas de **ingestão**, **armazenamento**, **processamento** e **consumo**, podendo seguir dois caminhos distintos que se complementam: processamento **em lote (*Batch*)** e processamento **em tempo real (*Streaming*)**.

### 1.2 Componentes Essenciais

- **Fontes de Dados:** Origem de tudo. Inclui bancos de dados relacionais, arquivos de log, dispositivos de IoT (celulares, sensores, geladeiras conectadas) e redes sociais.

- **Ingestão de Dados:** A camada responsável por capturar os dados.
    - **Em Lote (*Batch*):** Captura periódica de grandes volumes.
    - **Em Tempo Real (*Streaming*):** Captura contínua e incremental, com baixíssima latência. Utiliza um *buffer* (repositório de ingestão) para gerenciar o fluxo.

- **Armazenamento de Dados:**
    - **Repositórios Distribuídos:** *Data Lakes*, sistemas de arquivos em *cluster* (HDFS).
    - **Bancos NoSQL:** Para dados flexíveis e de alta performance.

- **Processamento de Dados:** É o momento em que se tira do Data Lake e prepara-se para a modelagem.
    - **Processamento em Lote:** Envolve pré-processamento, agregações e filtragens em períodos determinados. Ferramentas: **Hive, Pig, MapReduce**, programas em Python.
    - **Processamento de Fluxo (*Streaming*):** Pré-processamento, filtragem e agregação de dados capturados em tempo real.

- **Armazenamento de Dados Analíticos:** Os dados, já processados, são armazenados em formato estruturado para serem consumidos por ferramentas de *Analytics*.

- **Análise e Relatórios:** A camada final, onde ocorre a geração de resultados, *insights* e visualizações para a tomada de decisão.

- **Orquestração:** A camada que automatiza e coordena todos os fluxos de trabalho do pipeline, garantindo que as tarefas ocorram na ordem e no tempo corretos.

## 2. Arquiteturas de Processamento: Lambda e Kappa

Estas são duas variações arquiteturais famosas que definem como os processamentos em lote e em tempo real se integram.

| CARACTERÍSTICA | ARQUITETURA LAMBDA | ARQUITETURA KAPPA |
| :--- | :--- | :--- |
| **Objetivo** | Conciliar processamento em lote e em tempo real em dois caminhos paralelos. | Simplificar a arquitetura fundindo os dois caminhos em um único fluxo de *streaming*. |
| **Camadas** | **Camada Quente (*Speed Layer*):** Processamento em *streaming* para resultados imediatos. **Camada Fria (*Batch Layer*):** Processamento em lote para resultados precisos e históricos. | Uma única camada onde todo o fluxo é tratado como um *stream*, inclusive os reprocessamentos históricos. |
| **Complexidade** | **Alta**. Manter e sincronizar duas camadas é complexo e consome mais recursos. | **Simplificada e mais enxuta**, por ter apenas um caminho. |

## 3. Papéis e Relação com Outras Disciplinas

### 3.1 Principais Papéis

- **Engenheiro de Big Data:** Profissional focado na implementação da arquitetura. É o responsável pela infraestrutura, ingestão e garantia do fluxo de dados.

### 3.2 Big Data como Disciplina Integradora

- O Big Data não é uma área isolada, mas se relaciona intrinsecamente com várias outras disciplinas para gerar valor:
    - **Banco de Dados:** Para modelagem e armazenamento.
    - **Aprendizado de Máquina (*Machine Learning*):** Para extrair padrões e fazer previsões.
    - **Business Intelligence (BI):** Para visualização e apoio à decisão.
    - **Computação em Nuvem (*Cloud Computing*):** Para prover a infraestrutura escalável.
    - **Estatística:** Para fundamentar as análises.
    - **Engenharia de Software:** Para construir sistemas robustos e de qualidade.