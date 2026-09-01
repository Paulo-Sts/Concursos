# Business Intelligence

## 1. Conceito
- Business intelligence é um processo inteligente de coleta, organização, análise, compartilhamento e monitoração de dados que, depois de processados, geram informações para o suporte e para a tomada de decisões no ambiente de negócios.
- Conjunto de processos, tecnologias e ferramentas que auxiliam as organizações a obter insights significativos a partir de seus dados.
- Permite a tomada de decisões baseada em informações.
- Ajuda a converter decisões em ações.
- Utilizado em diversas áreas e setores, incluindo vendas, marketing, finanças, recursos humanos, operações e logística.

### 1.1 Componentes do BI
- Combina arquiteturas, ferramentas, bases de dados, ferramentas analíticas, aplicativos e metodologias.

> [!TIP] DICAS: 
> - BI não é um software específico; é um conjunto de processos e ferramentas.
> - O Power BI é um exemplo de software usado para montar o Business Intelligence.
> - BI não é um conjunto de relatórios preparados pelos executivos; é o processo que gera esses relatórios.

> [!CAUTION] OBSERVAÇÃO: 
> - O usuário primário do BI é o gerente (nível gerencial).
> - O operacional tem a função de inserir dados nos bancos de dados transacionais, não de utilizar diretamente o BI.

## 2. Tecnologias Relacionadas ao BI
- ETL: significa extrair, transformar e carregar. Processo de extração de dados de fontes diversas, transformação e carga no data warehouse.
- OLAP: tecnologia para análise de dados multidimensionais, permitindo navegar pelo cubo de dados.
- DW (data warehouse): armazém de dados onde ficam todos os dados de forma organizada e modelada.
- Data mart: subconjunto do data warehouse, focado em um departamento ou área específica.
- Modelagem dimensional: base para construir um DW, com tabela fato e tabelas dimensão.

### 2.1 Tabela Fato e Tabelas Dimensão
- Tabela fato: guarda o principal do negócio que está sendo analisado, contendo medidas, números, valores e chaves para as tabelas dimensão.
- Tabelas dimensão: descrevem o fato, fornecendo contexto para as medidas (ex.: tempo, produto, cliente, localização).

### 2.2 Evolução do BI
- Evoluiu ao longo dos anos, incorporando tecnologias como big data, analytics avançada, inteligência artificial e machine learning.
- Existe uma integração cada vez maior dos processos de inteligência de negócios com os processos de aprendizado de máquina.

> [!CAUTION] OBSERVAÇÃO: 
> - O DW não é o BI; é apenas um dos componentes onde os dados são armazenados.
> - DW é o local onde são guardados os dados, enquanto BI é o processo de transformar esses dados em informações para decisão.

## 3. Os Três Caminhos para Obter Informações de Bases de Dados
- Três formas de extrair informações de dados:
  - SQL: consulta direta no banco de dados. Porém, não é suficiente para tirar todas as informações precisas para decisões estratégicas.
  - BI: montar um sistema de business intelligence.
  - IA/machine learning: jogar os dados no aprendizado de máquina para extrair conhecimento.

### 3.1 Fluxo OLTP para OLAP
- Bases transacionais (OLTP): onde são feitas as transações dentro dos bancos de dados que estão em produção.
- Processo: tira-se do OLTP e passa para o OLAP, para a análise.
- No OLAP: os dados são tratados, são resolvidos os problemas de integração de dados.
- Depois segue para o DW: no DW são feitas operações OLAP para navegar pelo cubo de dados.
- O processo de modelagem deve ter antes um data set, um conjunto de dados especialmente montado para colocar dentro do modelo de aprendizado de máquina.

> [!TIP] DICAS: 
> - Exemplo de fontes de dados: bancos de dados internos, sistemas de gestão empresarial, planilhas, mídias sociais, dispositivos móveis e fontes externas (ex.: API de órgãos governamentais).
> - SQL é insuficiente para decisões estratégicas porque não integra dados de múltiplas fontes e não permite análises complexas.

> [!CAUTION] OBSERVAÇÃO: 
> - BI não é atualizado em tempo real, via de regra. O nível gerencial se atenta ao BI, enquanto os bancos transacionais ficam em operação contínua.

## 4. Objetivos do BI
- Coletar: coleta de dados de diversas fontes, internas e externas.
- Organizar: os dados são transformados em uma data staging área e armazenados em um data warehouse ou data mart.
- Analisar: aplicação de técnicas estatísticas, modelagem de dados e algoritmos de mineração de dados para identificar padrões, tendências e correlações.
- Visualizar: criação de dashboards interativos, relatórios personalizados e visualizações de dados (gráficos) para facilitar a compreensão e interpretação dos resultados.
- Permitir acesso interativo aos dados e fornecer aos analistas de negócios, por meio da manipulação desses dados, a capacidade de realizar a análise adequada.
- Transformar dados brutos em informações, criando conhecimento para permitir uma melhor tomada de decisão dos gestores e ajudá-los a converter essas decisões em ação.

### 4.1 Processo do BI
- Dados ⟶ Informações ⟶ Decisões ⟶ Ações.

## 5. Desafios na Construção de uma Solução de BI
- Integração de dados de diferentes fontes.
- Qualidade dos dados.
- Criação de uma cultura organizacional baseada em dados.
- Falta de conhecimento técnico em ferramentas de business intelligence.

> [!TIP] DICAS: 
> - O BI se refere a deixar de tomar decisões por sentimento e passar a tomar decisões baseadas em dados e padrões.
> - Por meio do BI, é possível proporcionar a descoberta de padrões de dados, sem a tendenciosidade e a limitação da análise baseada exclusivamente na intuição humana.

> [!CAUTION] OBSERVAÇÃO: 
> - Quem define o pedido de compra é o cliente, não o BI.
> - O BI estrutura os dados do negócio para auxiliar na tomada de decisão, mas não define operações diretamente.
> - O recurso de BI não favorece a evolução dos dados inseridos em SQL.

## 6. Principais Características do BI
- Processo de recolhimento e tratamento de informações que apoiarão a gestão de um negócio.
- Possibilita acesso interativo a dados.
- Permite a manipulação de dados e realização de análises apropriadas por gestores e analistas.
- Transformação de dados em informações, decisões e ações.
- Cria conhecimento para melhor tomada de decisão.

> [!CAUTION] OBSERVAÇÃO: 
> - O principal objetivo do BI é possibilitar acesso interativo a dados, não não-interativo (somente leitura).