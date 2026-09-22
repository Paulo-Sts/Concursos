# Ciclo de Vida dos Dados

## 1. Definição
- Compreende as etapas fundamentais para transformar dados brutos em conhecimento estratégico no contexto da ciência de dados.
- Coleta: obtenção de informações de diversas fontes para gerar conhecimento.
- Tratamento: adequação dos dados ao modelo de análise, incluindo transformações de tipos e limpeza.
- Armazenamento: guarda das informações em sistemas seguros e acessíveis como hds ou sistemas de arquivos distribuídos.
- Integração: unificação de informações de fontes distintas para assegurar que todas as variáveis necessárias estejam reunidas.
- Recuperação: extração das informações para uso, geralmente realizada por meio de consultas sql ou apis.

| ETAPA | DESCRIÇÃO |
|---|---|
| Coleta | Obtenção de informações brutas |
| Tratamento | Limpeza e preparação para modelagem |
| Armazenamento | Repositório físico ou em nuvem |
| Integração | Unificação de fontes variadas |
| Recuperação | Extração eficiente para análise |

> [!TIP] DICAS: 
> - O fluxo do ciclo de vida segue a lógica: Coleta ⟶ Tratamento ⟶ Armazenamento ⟶ Integração ⟶ Recuperação.

## 2. Coleta e Fontes de Dados
- Fontes primárias: dados coletados diretamente por meio de entrevistas, formulários ou sensores de ti.
- Fontes secundárias: informações previamente coletadas e organizadas em bancos de dados públicos, redes sociais ou registros administrativos.
- Estratégias de coleta automática: uso de apis e web scraping para a extração de dados de páginas da web.
- Sensores e iot: geração constante de informações em tempo real por dispositivos conectados, como os utilizados em carros autônomos.

> [!CAUTION] OBSERVAÇÃO: 
> - A qualidade dos dados é um desafio crítico desde a coleta, exigindo verificação de integridade e confiabilidade das informações.
> - A conformidade com a lgpd é obrigatória no tratamento de dados pessoais, exigindo consentimento para evitar práticas ilegais.

## 3. Tratamento e Limpeza de Dados
- Processo essencial para a preparação dos dados visando precisão e consistência na etapa de modelagem.
- Limpeza: correção de erros, remoção de duplicidades e preenchimento ou exclusão de dados ausentes.
- Outliers: remoção de valores fora da curva para evitar que pontos discrepantes influenciem a precisão de modelos como a regressão linear.
- Mascaramento e anonimização: procedimentos realizados para garantir a privacidade de informações sensíveis conforme a lei.
- Rotulagem: identificação de categorias ou palavras-chave, sendo fundamental para o treinamento em processamento de linguagem natural.

| TÉCNICA | FUNÇÃO |
|---|---|
| Limpeza | Corrigir erros e duplicidades |
| Anonimização | Garantir privacidade (lgpd) |
| Rotulagem | Categorizar para nlp |

> [!TIP] DICAS: 
> - A ausência de dados pode comprometer a execução de algoritmos, como árvores de decisão, que não operam com informações incompletas.

## 4. Transformação e Redução de Dados
- Mudança de tipo: conversão de dados numéricos em categóricos (ex.: altura para baixo/médio/alto) ou variáveis categóricas em numéricas.
- One-hot encoding: criação de variáveis separadas para cada categoria de um dado original.
- Mudança de escala: uso de normalização ou padronização para que variáveis de diferentes magnitudes tenham a mesma importância no modelo.
- Redução de dimensionalidade: diminuição do número de atributos (colunas) mantendo as variáveis mais relevantes, como na acp (análise de componentes principais).
- Enriquecimento: busca de dados em fontes externas para complementar bases que possuem informações faltantes ou de baixa qualidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Redes neurais artificiais exigem obrigatoriamente entradas numéricas e um bom desempenho depende de dados na mesma faixa de escala.

## 5. Validação e Ferramentas de Análise
- Visualização: uso de histogramas e box plots para verificar a distribuição dos valores e identificar outliers.
- Gráficos de dispersão: utilizados para avaliar a existência de correlação entre as variáveis.
- Tecnologias principais: python (uso da biblioteca pandas e estruturas de dataframe) e r (popular para modelagem estatística avançada).

## 6. Integração e Armazenamento Avançado
- ETL (Extração, Transformação e Carga): os dados são extraídos para uma área intermediária onde ocorrem a limpeza e o tratamento antes da carga final.
- ELT (Extração, Carregamento e Transformação): variação onde a transformação dos dados ocorre após o carregamento no repositório final.
- Data Warehouse: repositório que organiza os dados em modelos dimensionais (tabelas fato e dimensão) para suporte à análise.
- Data Mart: versão segmentada e focada em um conjunto específico de dados derivada do data warehouse.
- Data Lake: repositório não estruturado para grandes volumes de dados (big data) sem necessidade de pré-processamento imediato.
- ODS (Operational Data Store): banco de dados consolidado voltado para operações em tempo real, sem as características dimensionais do warehouse.

| REPOSITÓRIO | CARACTERÍSTICA |
|---|---|
| Data warehouse | Modelo dimensional para análise |
| Data lake | Armazenamento de dados brutos |
| Ods | Operacional e tempo real |

> [!CAUTION] OBSERVAÇÃO: 
> - No processo de etl, a deduplicação e a validação dos dados ocorrem obrigatoriamente na fase de transformação e não no carregamento.