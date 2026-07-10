# Anotações

# ETL X ELT (EXTRAÇÃO, TRANSFORMAÇÃO E CARGA)

## 1. Definição dos Processos

### 1.1 ETL (Extract, Transform, Load)

- **Conceito:** Processo tradicional de integração de dados. Os dados são **Extraídos** das fontes, **Transformados** em uma área intermediária (*staging*) e, por fim, **Carregados** no destino (normalmente um Data Warehouse).
- **Pilar:** É um dos pilares da engenharia de dados e do processo de Business Intelligence (BI). O dado só fica disponível no final do processo.
- **Etapas:**
    1.  **Extração (*Extract*):** Obter dados de múltiplas fontes (bancos relacionais, NoSQL, arquivos CSV/JSON/XML, APIs, sensores).
    2.  **Transformação (*Transform*):** Converter dados brutos em formato padronizado e confiável (limpeza, remoção de duplicatas, padronização de formatos, enriquecimento, aplicação de regras de negócio).
    3.  **Carga (*Load*):** Armazenar os dados transformados no sistema de destino (carga total ou incremental).

### 1.2 ELT (Extract, Load, Transform)

- **Conceito:** Variação moderna do ETL, impulsionada pelo Big Data e pela computação em nuvem. Os dados são **Extraídos** e **Carregados** diretamente no repositório de destino (como um Data Lake) em seu formato bruto. A **Transformação** ocorre **depois**, sob demanda, usando o poder de processamento do próprio destino.
- **Diferencial:** A ordem das etapas é invertida; os dados brutos ficam disponíveis antes da transformação.

## 2. Tabela Comparativa: ETL vs. ELT

| CARACTERÍSTICA | ETL | ELT |
| :--- | :--- | :--- |
| **Ordem das Etapas** | Extrair -> Transformar -> Carregar | Extrair -> Carregar -> Transformar |
| **Local da Transformação** | Servidor intermediário / ferramenta ETL. | **No próprio sistema de destino** (Data Lake/Cloud DW). |
| **Indicado para** | Data Warehouses tradicionais, dados estruturados. | **Big Data**, nuvem, grandes volumes, dados não estruturados/semiestruturados. |
| **Tempo de Carga Inicial** | **Maior** (a transformação ocorre antes). | **Menor** (dados vão brutos para o destino). |
| **Flexibilidade** | Menor (transforma antes, limitando reuso). | **Maior** (dados brutos disponíveis para múltiplas análises). |
| **Vantagem Principal** | **Qualidade** dos dados garantida no destino. | **Agilidade** na ingestão e **flexibilidade** analítica. |
| **Desvantagem Principal** | Tempo maior para disponibilizar os dados. | Risco de *Data Swamp* sem governança. |

## 3. Vantagens e Desvantagens

### 3.1 ETL

- **Vantagens:** Garante alta qualidade dos dados no destino, menor carga no sistema de destino, mais adequado para DWs tradicionais, controle centralizado.
- **Desvantagens:** Maior latência, menos flexível para análises *ad hoc*, necessita de infraestrutura intermediária.

### 3.2 ELT

- **Vantagens:** Agilidade na ingestão, alta flexibilidade analítica, escalabilidade, menor dependência de infraestrutura intermediária.
- **Desvantagens:** Maior consumo de armazenamento (guarda o bruto e o transformado), risco de virar um *Data Swamp* sem governança, maior carga no sistema de destino, qualidade inicial dos dados mais baixa.

## 4. Análise de Questões de Concurso

### 4.1 Destino do ETL (CESPE/ANTT/2024)

- **Enunciado:** "Em ETL, o armazenamento de dados pode ser feito em bancos de dados ou em data warehouse, **mas não em data lakes**..."
- **Gabarito:** **ERRADO**.
- **Análise:** O ETL **pode sim** carregar dados em um Data Lake. Embora o processo ELT seja o mais característico do Data Lake, o ETL também pode ser usado para alimentá-lo.

### 4.2 Ordem das Etapas do ELT (FGV/S. José dos Campos/2024)

- **Enunciado:** "( ) O ELT transforma dados no trânsito. ( ) O ETL não transforma nenhum dado no trânsito."
- **Gabarito:** **B (F – F – V).**
- **Análise:** Ambas as afirmativas são falsas. Quem transforma dados "no trânsito" (em área intermediária) é o **ETL**. No **ELT**, a transformação é no destino, e não em trânsito. A terceira afirmativa está correta, pois no ELT o destino é frequentemente um Data Lake.

### 4.3 Eficiência do ELT (FGV/DATAPREV/2024)

- **Enunciado:** "ELT é mais eficiente em cenários onde o volume de dados é pequeno..."
- **Gabarito:** **ERRADO** (a afirmativa é incorreta).
- **Análise:** O ELT é mais eficiente e escalável para cenários de **grandes volumes** de dados (Big Data), onde o poder de processamento do destino é massivo. Para dados pequenos, o ETL tradicional é perfeitamente adequado.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESPE/EMBRAPA) | **C** | ETL também carrega dados em um Data Lake. |
| **02** (CESPE/ANATEL) | **E** | O ELT não exige maior definição de regras (a transformação é posterior). |
| **03** (CESPE/ANTT) | **E** | ETL pode sim carregar dados em um Data Lake. |
| **04** (CESPE/TSE) | **E** | No ETL, os dados são transformados **antes** do carregamento. |
| **05** (CESPE/SEPLAG-CE) | **C** | ETL para dados estruturados, ELT para dados semi e não estruturados. |
| **06** (FGV/S. José Campos) | **B** | F, F, V. ELT não transforma no trânsito; ETL transforma no trânsito. |
| **07** (FGV/DATAPREV) | **D** | ELT é mais eficiente para **grandes** volumes de dados. |
| **08** (CESPE/TCE-AC) | **E** | ETL e ELT possuem diferenciação entre os processos. |