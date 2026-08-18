# Caderno de Erros

## 1. Conceitos

##### (FGV/2022/SEFAZ-AM/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO DA FAZENDA ESTADUAL/TARDE) Assinale a opção que apresenta os principais componentes da arquitetura de um sistema de BI.
a. Data lake, big data e dashboard.  
b. Data mart, análise de negócio e dashboard.  
c. Data mart, extração-transformação-carga e interfaces do usuário.  
d. Data warehouse, análise de negócio, business process management e interfaces do usuário.  
e. Data warehouse, extração-transformação-carga, ciência de dados, business process management e dashboard.  

- Os principais componentes da arquitetura de um sistema de BI são data warehouse, análise de negócio, business process management e interfaces do usuário.
- Resposta: D

##### (CESPE/CEBRASPE/2021/MPE-AP/ANALISTA MINISTERIAL - TECNOLOGIA DA INFORMAÇÃO) Em um sistema de BI, a coleção de ferramentas utilizada como componente para manipular, minerar e analisar os dados no DW (data warehouse) denomina-se
a. OLAP (online analytical processing).  
b. BPM (Business Performance Management).  
c. Análise de Negócio.  
d. Dashboard.
e. Processamento de Transações.  

- Em um sistema de BI, a coleção de ferramentas utilizada como componente para manipular, minerar e analisar os dados no DW denomina-se Análise de Negócio.
- Resposta: C

#####  (FCC/SEFAZ-BA/AUDITOR FISCAL/ADMINISTRAÇÃO, FINANÇAS E CONTROLE INTERNO/PROVA II/2019) Nos sistemas transacionais, os dados sofrem diversas alterações como inclusão, alteração e exclusão. Antes de serem carregados no ambiente de um Data Warehouse, os dados são filtrados e limpos, de forma a gerarem informação útil. Após esta etapa, esses dados:
a. ficam disponíveis para a mineração em tempo real, pois tais dados são constantemente atualizados a partir da chave de tempo que indica o dia em que foram extraídos dos sistemas transacionais.  
b. podem sofrer operações de consulta, mas, devido a sua não volatilidade, não podem ser alterados, não havendo necessidade de bloqueio por concorrência de usuários ao seu acesso.  
c. são reunidos a partir de diversas fontes de dados, o que facilita muito o trabalho do analista, embora este tenha que lidar com a grande redundância das informações.  
d. ficam ordenados pela data da extração do sistema transacional, sendo necessárias técnicas de data mining para fazer a sua recuperação orientada por assunto.  
e. são classificados somente pelo assunto principal de interesse da organização. Por exemplo, em uma organização de arrecadação de impostos, os dados são organizados pelo cadastro de contribuintes que possuem impostos a recolher.  

- a) Os dados no DW não são constantemente atualizados, pois eles não são voláteis.
- b) Os dados no DW podem sofrer operações de consulta, mas, devido a sua não volatilidade, não podem ser alterados, não havendo necessidade de bloqueio por concorrência
de usuários ao seu acesso.
- c) Os dados no DW são reunidos a partir de diversas fontes de dados, o que dificulta muito
o trabalho do analista, pois ele tem que lidar com a grande redundância das informações.
- d) Os dados no DW ficam ordenados pela data da extração do sistema transacional, mas não é necessárias técnicas de data mining para fazer a sua recuperação orientada por assunto.
- e) Em uma organização de arrecadação de impostos, os dados são organizados pelo imposto e o contribuinte é apenas uma dimensão.
- Resposta: B

##### (CESGRANRIO/BANCO DA AMAZÔNIA/TÉCNICO CIENTÍFICO/TECNOLOGIA DA INFORMAÇÃO/2018) Um Data Warehouse é recomendado para armazenar dados
a. sumarizados de um departamento.  
b. sumarizados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.  
c. detalhados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.  
d. detalhados gerados por sistemas de informação transacionais.  
e. históricos detalhados de todas as transações realizadas em um determinado período de tempo.  

- Um Data Warehouse é recomendado para armazenar dados sumarizados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.
- Resposta: B

##### (CESPE/CEBRASPE/PGE-RJ/ANALISTA DE SISTEMAS E MÉTODOS/2022) Com relação a data warehouse e data mining, julgue o item a seguir. Um data warehouse usa técnicas estatísticas e de aprendizagem automática para, em uma coleção de dados orientada ao assunto e não volátil, extrair e identificar informações úteis com objetivos de apoiar a tomada de decisão.

- Um data warehouse pode usar técnicas estatísticas e de aprendizagem automática para, em uma coleção de dados orientada ao assunto e não volátil, extrair e identificar informações úteis com objetivos de apoiar a tomada de decisão.
- Resposta: Errado

##### (CESGRANRIO/ELETROBRAS-ELETRONUCLEAR/ANALISTA DE SISTEMAS/APLICAÇÃO E SEGURANÇA DE TIC/2022) OLAP é um tipo de processamento de dados que:
a. organiza, consolida e permite o acesso a dados de múltiplas fontes para tomada de decisão.  
b. controla todo o ordenamento jurídico e legal necessário à operação de uma empresa.  
c. permite o registro e o controle de todas as transações de uma empresa.  
d. permite manipulação e análise de dados especializados.  
e. apoia as ordens de serviço internas a uma empresa.  

- OLAP é um tipo de processamento de dados que organiza, consolida e permite o acesso a dados de múltiplas fontes para tomada de decisão.
- Resposta: A

##### (INSTITUTO AOCP/MJSP/ANALISTA DE GOVERNANÇA DE DADOS/BIG DATA/2022) Para suportar inteligência empresarial, em geral, os bancos de dados são montados de forma a fornecer relatórios e ferramentas úteis para a análise. Sabendo disso, assinale a alternativa que apresenta corretamente um programa que possibilite que os usuários explorem dados de diferentes perspectivas para conduzir à inteligência empresarial.
a. Computação em nuvem.  
b. Processamento empresarial.  
c. Distribuição de base de dados.  
d. Processamento analítico on-line.  
e. Sistema de processamento de transações.  

- O processamento analítico on-line é um programa que possibilita que os usuários explorem dados de diferentes perspectivas para conduzir à inteligência empresarial.
- Resposta: C

#####  (CESPE/CEBRASPE/PETROBRAS/ANALISTA DE SISTEMAS/ENGENHARIA DE SOFTWARE/2022) Julgue os itens a seguir, quanto a conceitos de dado, informação, inteligência e business intelligence (BI). No processo de preparação de dados para BI, um dado com incompletude é normalmente aquele cujo valor está fora do domínio do atributo.

- Um dado incompleto é um dado faltante, e não um dado fora do domínio do atributo.
- Resposta: Errado

##### (CESGRANRIO/TRANSPETRO/ANALISTA DE SISTEMAS JÚNIOR/SAP/2018) Na construção de data warehouses é possível – e por vezes recomendado – que a equipe projetista considere a utilização de diversas fontes de dados. Com isso, espera-se melhorar a qualidade das análises a serem realizadas, a partir desse data warehouse. Qual tarefa a seguir listada NÃO corresponde a uma ação de preparação de dados nessa etapa?
a. Avaliação estocástica dos metadados.  
b. Discretização de atributos numéricos.  
c. Imputação de valores ausentes.  
d. Seleção de atributos relevantes.  
e. Verificação de cálculos inválidos.  

- Na etapa de transformação, é necessário realizar a avaliação estocástica dos metadados, a discretização de atributos numéricos, a imputação de valores ausentes, a seleção de atributos relevantes e a verificação de cálculos inválidos.
- Resposta: A