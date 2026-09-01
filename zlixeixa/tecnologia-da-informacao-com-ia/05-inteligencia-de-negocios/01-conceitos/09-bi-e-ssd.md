# Business Intelligence e Sistemas de Apoio à Decisão

## 1. Business Intelligence

### 1.1 Definição e Objetivo
- O Business Intelligence é um conjunto de processos, tecnologias e ferramentas que auxiliam as organizações a obter insights significativos a partir de seus dados.
- Permite a tomada de decisões baseada em informações e dados.
- Ajuda a converter decisões em ações.
- É utilizado em diversas áreas e setores: vendas, marketing, finanças, recursos humanos, operações e logística.

### 1.2 Evolução Tecnológica
- O BI evoluiu ao longo dos anos, incorporando tecnologias como:
  - Big data;
  - Analytics avançada;
  - Inteligência artificial;
  - Machine learning.

### 1.3 Processo do BI
- O processo de tomada de decisão se inicia com as fontes de dados.
- Os dados são extraídos para a staging área.
- São transformados em um modelo dimensional (com a tabela fática das dimensões).
- São carregados em um Data Warehouse ou Data Mart.
- Operações OLAP formam um Sistema de Suporte à Decisão ou Dashboard.
- A distribuição e o compartilhamento fazem parte do processo.
- É necessário cuidado com a segurança e a governança de dados.
- A governança mantém os dados organizados e com boa qualidade.

> [!TIP] DICAS:
> - O BI não é mandatório para tomada de decisão baseada em dados, embora seja amplamente utilizado.
> - A governança de dados é essencial para manter a qualidade e organização das informações.

> [!CAUTION] OBSERVAÇÃO:
> - O BI não se limita apenas à coleta de dados; envolve todo o ciclo, desde a extração até a visualização e compartilhamento.

## 2. Data Warehouse

### 2.1 Características Fundamentais
- O Data Warehouse é um conjunto de dados com as seguintes características:
  - Orientado por assunto;
  - Integrado;
  - Variável com o tempo;
  - Não volátil.

### 2.2 Detalhamento das Características
- Orientado por assunto: os dados são organizados em torno de temas principais da empresa.
- Integrado: os dados são consistentes e padronizados, mesmo vindos de fontes diferentes.
- Variável com o tempo: os dados são inseridos em um processo contínuo, permitindo análise histórica.
- Não volátil: os dados armazenados no DW não são alterados ou removidos.

### 2.3 Níveis Organizacionais e Data Warehouse
- O DW contém dados sumarizados necessários para a gestão de processos de negócios e para o planejamento da empresa.
- É adequado para os níveis gerencial e estratégico.
- O nível operacional utiliza dados detalhados para transações diárias, não sendo o foco principal do DW.

### 2.4 Data Mart
- O Data Mart é um sistema de suporte à decisão que incorpora um subconjunto de dados da empresa.
- É localizado em funções ou atividades específicas da organização.
- Representa uma parte do Data Warehouse, focada em áreas específicas.

### 2.5 Processo ETL
- ETL significa Extração, Transformação e Carregamento.
- É utilizado na etapa de coleta de dados para o Data Warehouse.
- Na transformação, são tratadas as inconsistências entre dados oriundos de sistemas transacionais distintos.

> [!TIP] DICAS:
> - A característica "não volátil" do DW é uma pegadinha comum em provas: os dados não são alterados após armazenados.
> - O DW é orientado por assunto, não por transações.
> - Data Mart é um "subconjunto" do Data Warehouse, focado em um departamento ou área específica.

> [!CAUTION] OBSERVAÇÃO:
> - As consultas no Data Warehouse não são executadas nos provedores de informação originais, pois os dados passam por processo de tratamento.
> - O DW não deve conter apenas dados internos; dados externos complementam as análises estratégicas.

## 3. Sistemas de Apoio à Decisão

### 3.1 Definição e Objetivo
- São ferramentas tecnológicas e conceituais projetadas para auxiliar indivíduos e organizações no processo de tomada de decisão.
- Fornecem informações relevantes, análises, modelos, interfaces amigáveis e ferramentas interativas.
- Resolvem problemas não estruturados.
- Finalidades:
  - Melhorar a qualidade das decisões;
  - Aumentar a eficiência e eficácia do processo de decisão;
  - Reduzir a incerteza e o risco envolvidos.

### 3.2 Características dos SSD
- Combinam dados e modelos analíticos sofisticados.
- Possuem interface amigável para apoiar a tomada de decisão.
- Permitem fácil execução de análises de sensibilidade.
- Apoiam decisões interdependentes.
- Utilizam servidores OLAP e Data Marts.

### 3.3 Problemas Estruturados vs Não Estruturados

| TIPO | CARACTERÍSTICAS | EXEMPLOS |
|------|-----------------|----------|
| Estruturados | Definição clara; processos bem estabelecidos; soluções previamente determinadas; ocorrem de maneira repetitiva e previsível | Cálculos matemáticos; cotações de preços; agendamento de recursos; fórmulas financeiras |
| Não estruturados | Falta de clareza na definição; soluções e métodos de resolução não definidos; únicos e complexos; envolvem elementos subjetivos e informações incertas | Desenvolvimento de estratégias de negócios; resolução de conflitos interpessoais; design de produtos inovadores; previsão de tendências de mercado |

### 3.4 Tomada de Decisão
- Problemas estruturados não necessitam de sistemas de apoio à decisão.
- Problemas não estruturados exigem julgamento humano, intuição e criatividade.
- A tomada de decisão não é realizada apenas baseada na intuição humana, mas a partir de um sistema de apoio alimentado por dados.
- Os SSD auxiliam os tomadores de decisão, não os substituem.

### 3.5 Análise de Sensibilidade
- É o estudo do impacto que as mudanças em uma ou mais partes de um modelo têm em outras partes ou no resultado.
- Avalia uma variável e a sensibilização do cenário diante dessa variação.
- É extremamente valiosa nos Sistemas de Suporte à Decisão.

### 3.6 Interatividade
- O SSD é interativo, permitindo acesso interativo aos dados.
- Oferece operações OLAP, dashboards e gráficos interativos.

### 3.7 Níveis Organizacionais e SSD
- No nível estratégico, os DSS utilizam dados internos da própria empresa, complementados por dados externos do mercado onde a empresa atua.
- Os sistemas de apoio à decisão podem ser utilizados tanto no nível gerencial quanto no estratégico.

### 3.8 Processo de Tomada de Decisão
- Inicia-se com a coleta de dados.
- Passa pela análise dos dados.
- Realiza a visualização dos dados.
- Conclui com a tomada de decisão propriamente dita.

> [!TIP] DICAS:
> - O SSD é voltado para problemas não estruturados, jamais para problemas estruturados.
> - A análise de sensibilidade é uma ferramenta valiosa nos SSD, permitindo avaliar impactos de mudanças.
> - Os SSD são interativos, não apenas sistemas de leitura de dados.
> - No nível estratégico, o SSD utiliza dados internos E externos, complementando as análises.
> - A árvore de decisão com abordagem de predição é utilizada em sistemas de suporte à decisão.

> [!CAUTION] OBSERVAÇÃO:
> - O SSD não substitui o tomador de decisão; apenas o auxilia no processo.
> - O OLAP não é o mesmo que OLTP: OLAP é analítico, enquanto OLTP é transacional.
> - O Data Lake com dados não estruturados não pode ser considerado um sistema de suporte à decisão.
> - Os SSD não automatizam completamente o processo de decisão, pois exigem participação humana.
> - Aplicações de SSD são encontradas nas mais diversificadas áreas, não apenas no comércio eletrônico.