# Caderno de Erros

## 1. Conceitos

> ##### (FGV/2022/SEFAZ-AM/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO DA FAZENDA ESTADUAL/TARDE)
> ##### 1. Assinale a opção que apresenta os principais componentes da arquitetura de um sistema de BI.

a. Data lake, big data e dashboard.  
b. Data mart, análise de negócio e dashboard.  
c. Data mart, extração-transformação-carga e interfaces do usuário.  
d. Data warehouse, análise de negócio, business process management e interfaces do usuário.  
e. Data warehouse, extração-transformação-carga, ciência de dados, business process management e dashboard.  

- Os principais componentes da arquitetura de um sistema de BI são data warehouse, análise de negócio, business process management e interfaces do usuário.
- Resposta: D

> ##### (CESPE/CEBRASPE/2021/MPE-AP/ANALISTA MINISTERIAL - TECNOLOGIA DA INFORMAÇÃO) 
> ##### 2. Em um sistema de BI, a coleção de ferramentas utilizada como componente para manipular, minerar e analisar os dados no DW (data warehouse) denomina-se:  

a. OLAP (online analytical processing).  
b. BPM (Business Performance Management).  
c. Análise de Negócio.  
d. Dashboard.
e. Processamento de Transações.  

- Em um sistema de BI, a coleção de ferramentas utilizada como componente para manipular, minerar e analisar os dados no DW denomina-se Análise de Negócio.
- Resposta: C

> ##### (FCC/SEFAZ-BA/AUDITOR FISCAL/ADMINISTRAÇÃO, FINANÇAS E CONTROLE INTERNO/PROVA II/2019) 
> ##### 3. Nos sistemas transacionais, os dados sofrem diversas alterações como inclusão, alteração e exclusão. Antes de serem carregados no ambiente de um Data Warehouse, os dados são filtrados e limpos, de forma a gerarem informação útil. Após esta etapa, esses dados:

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

> ##### (CESGRANRIO/BANCO DA AMAZÔNIA/TÉCNICO CIENTÍFICO/TECNOLOGIA DA INFORMAÇÃO/2018) 
> ##### 4. Um Data Warehouse é recomendado para armazenar dados:

a. sumarizados de um departamento.  
b. sumarizados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.  
c. detalhados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.  
d. detalhados gerados por sistemas de informação transacionais.  
e. históricos detalhados de todas as transações realizadas em um determinado período de tempo.  

- Um Data Warehouse é recomendado para armazenar dados sumarizados de toda a empresa para apoio à decisão e utilização de ferramentas OLAP.
- Resposta: B

> ##### (CESPE/CEBRASPE/PGE-RJ/ANALISTA DE SISTEMAS E MÉTODOS/2022) 
> ##### 5. Com relação a data warehouse e data mining, julgue o item a seguir. Um data warehouse usa técnicas estatísticas e de aprendizagem automática para, em uma coleção de dados orientada ao assunto e não volátil, extrair e identificar informações úteis com objetivos de apoiar a tomada de decisão.

- Um data warehouse pode usar técnicas estatísticas e de aprendizagem automática para, em uma coleção de dados orientada ao assunto e não volátil, extrair e identificar informações úteis com objetivos de apoiar a tomada de decisão.
- Resposta: Errado

> ##### (CESGRANRIO/ELETROBRAS-ELETRONUCLEAR/ANALISTA DE SISTEMAS/APLICAÇÃO E SEGURANÇA DE TIC/2022) 
> ##### 6. OLAP é um tipo de processamento de dados que:

a. organiza, consolida e permite o acesso a dados de múltiplas fontes para tomada de decisão.  
b. controla todo o ordenamento jurídico e legal necessário à operação de uma empresa.  
c. permite o registro e o controle de todas as transações de uma empresa.  
d. permite manipulação e análise de dados especializados.  
e. apoia as ordens de serviço internas a uma empresa.  

- OLAP é um tipo de processamento de dados que organiza, consolida e permite o acesso a dados de múltiplas fontes para tomada de decisão.
- Resposta: A

> ##### (INSTITUTO AOCP/MJSP/ANALISTA DE GOVERNANÇA DE DADOS/BIG DATA/2022) 
> ##### 7. Para suportar inteligência empresarial, em geral, os bancos de dados são montados de forma a fornecer relatórios e ferramentas úteis para a análise. Sabendo disso, assinale a alternativa que apresenta corretamente um programa que possibilite que os usuários explorem dados de diferentes perspectivas para conduzir à inteligência empresarial.

a. Computação em nuvem.  
b. Processamento empresarial.  
c. Distribuição de base de dados.  
d. Processamento analítico on-line.  
e. Sistema de processamento de transações.  

- O processamento analítico on-line é um programa que possibilita que os usuários explorem dados de diferentes perspectivas para conduzir à inteligência empresarial.
- Resposta: D

> ##### (CESPE/CEBRASPE/PETROBRAS/ANALISTA DE SISTEMAS/ENGENHARIA DE SOFTWARE/2022) 
> ##### 8. Julgue os itens a seguir, quanto a conceitos de dado, informação, inteligência e business intelligence (BI). No processo de preparação de dados para BI, um dado com incompletude é normalmente aquele cujo valor está fora do domínio do atributo.

- Um dado incompleto é um dado faltante, e não um dado fora do domínio do atributo.
- Resposta: Errado

> ##### (CESGRANRIO/TRANSPETRO/ANALISTA DE SISTEMAS JÚNIOR/SAP/2018) 
> ##### 9. Na construção de data warehouses é possível – e por vezes recomendado – que a equipe projetista considere a utilização de diversas fontes de dados. Com isso, espera-se melhorar a qualidade das análises a serem realizadas, a partir desse data warehouse. Qual tarefa a seguir listada NÃO corresponde a uma ação de preparação de dados nessa etapa?

a. Avaliação estocástica dos metadados.  
b. Discretização de atributos numéricos.  
c. Imputação de valores ausentes.  
d. Seleção de atributos relevantes.  
e. Verificação de cálculos inválidos.  

- Na etapa de transformação, é necessário realizar a avaliação estocástica dos metadados, a discretização de atributos numéricos, a imputação de valores ausentes, a seleção de atributos relevantes e a verificação de cálculos inválidos.
- Resposta: A

> ##### (FUNDATEC/2023/BRDE/ANALISTA DE SISTEMAS - CIÊNCIA DE DADOS) 
> ##### 10. Analise as assertivas abaixo, assinalando DW, para as características de Data Warehouse, ou DL, para as características de Data Lakes.

(  ) O esquema é gravado no momento da análise, denominado esquema de leitura.  
(  ) Quanto à qualidade dos dados, os dados são altamente selecionados e representam a versão central da verdade.  
(  ) Utilizam dados não relacionais e relacionais oriundos de dispositivos como aplicações móveis, mídia social, IoT (Internet das Coisas), aplicações corporativas, entre outras.  
(  ) Os resultados das consultas são mais rápidos e as análises são relatórios em lote e visualizações.  
A ordem correta de preenchimento dos parênteses, de cima para baixo, é:  

a. DW – DL – DL – DW.  
b. DW – DW – DL – DL.  
c. DW – DL – DW – DL.  
d. DL – DW – DL – DW.  
e. DL – DL – DW – DW.  

- No DW, quanto à qualidade dos dados, os dados são altamente selecionados e representam a versão central da verdade e os resultados das consultas são mais rápidos e as análises são relatórios em lote e visualizações. 
- No DL, o esquema é gravado no momento da análise, denominado esquema de leitura, e o DL utiliza dados não relacionais e relacionais oriundos de dispositivos como aplicações móveis, mídia social, IoT (Internet das Coisas), aplicações corporativas, entre outras.
- Resposta: D

> ##### (PROVA: CESPE/CEBRASPE/2025/BDMG/ANALISTA DE DESENVOLVIMENTO/INFRAESTRUTURA E SEGURANÇA CIBERNÉTICA) 
> ##### 11. Acerca da modelagem de dados, julgue o próximo item. O esquema estrela constitui-se de uma tabela de fatos, várias tabelas de dimensão e chaves estrangeiras da tabela de fatos para as tabelas de dimensão.

- O esquema estrela (Star Scheme) apresenta uma tabela de fatos, diversas tabelas de dimensão e chaves estrangeiras partindo da tabela de fatos em direção às tabelas de
dimensão, configurando a estrutura básica do modelo dimensional. Na tabela fato, existe chave primária para identificar chave surrogate e, em regra, constam medidas numéricas, como valor da venda e lucro da venda, além de chaves estrangeiras. 
- Como exemplo, existe chave estrangeira referente ao local em que cada venda ocorreu, a qual referencia a tabela de dimensão local. Na dimensão local, existe código como chave primária e atributos descritivos, como cidade e endereço, e demais informações relacionadas ao local da compra.
- Resposta: Certo

> ##### (PROVA: FUNCERN/2025/IF-PE/TÉCNÓLOGO/FORMAÇÃO GESTÃO DE TECNOLOGIA DA INFORMAÇÃO) 
> ##### 12. A planilha a seguir foi resultado da exportação dos dados de um Sistema de Informação: Deseja-se transformar essa planilha de acordo com as boas práticas da Modelagem Dimensional, técnica voltada para construção de sistemas de Business Intelligence, com o objetivo de criar uma tabela de fatos sobre a venda de produtos, além de uma ou mais tabelas de dimensões, conforme seja necessário. O resultado dessa transformação deve criar:

| CLIENTE | PRODUTO | QUANTIDADE_ITENS | TOTAL_VENDA |
|---|---|---|---|
| Cliente 1      | Produto A       | 2               | 30,00  |
| Cliente 2      | Produto B       | 3               | 24,00  |
| Cliente 3      | Produto A       | 1               | 10,00  |
| Cliente 1      | Produto C       | 3               | 63,00  |

a) uma tabela de dimensão para clientes e uma outra tabela de dimensão para produtos, mantendo, na tabela de fatos, as chaves estrangeiras para essas tabelas de dimensão e as medidas quantidade_itens e total_venda.  
b) uma tabela de dimensão para clientes, mantendo, na tabela de fatos, a chave estrangeira para essa tabela de dimensão e as medidas produto, quantidade_itens e total_venda.  
c) tabelas de dimensão para quantidade_itens e total_venda, mantendo, na tabela de fatos, as medidas cliente e produto, além das chaves estrangeiras para as tabelas de dimensão.  
d) uma tabela de dimensão para clientes e uma outra tabela de dimensão para quantidade_itens, mantendo, na tabela de fatos, as chaves estrangeiras para essas tabelas e as medidas produto e total_venda.  
e) uma tabela igual à que se vê na planilha, sendo desnecessária a criação de tabelas de dimensão ou chaves estrangeiras, cujas medidas já estão contidas na tabela.  

- a) Indica que a estrutura apresentada corresponde ao fato, com adição de dimensão cliente com detalhes do cliente e dimensão produto com detalhes do produto, considerando o campo como chave.
- b) Produto não configura medida; produto configura descrição.
- c) Cliente e produto não configuram medidas; configuram chaves.
- d) Quantidade_itens configura medida numérica.
- e) Sem criação de dimensões, não há modelagem dimensional.
- Resposta: A