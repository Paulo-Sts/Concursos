# Big Data

## 1. Introdução
- As bases de big data surgiram com a internet, pois antes dela os sistemas de gerenciamento de bancos de dados (SGBD) tinham volumes menores.
- O big data trouxe dados em formatos variados, como vídeos, imagens e textos longos, resultando na necessidade de novas tecnologias.
- É impossível armazenar tantos dados em uma única máquina, como fazem os servidores de dados tradicionais.
- Criou-se o conceito de computação distribuída: em vez de um único computador, há um cluster, isto é, um grupo de computadores interligados em rede, e o SGBD é instalado em todos esses computadores, distribuindo os dados entre eles.
- Surgiu o conceito de escalabilidade:
  - Escalabilidade horizontal: quando todos os computadores estão lotados, instala-se mais uma máquina no cluster.
  - Escalabilidade vertical: adiciona-se um HD maior em uma única máquina.

> [!CAUTION] OBSERVAÇÃO:
> - A infraestrutura do big data engloba um conjunto de computadores ligados entre si por meio de computação distribuída; se faltar espaço, adicionam-se novos computadores (escalabilidade horizontal).

## 2. Conceito de Big Data
- Definição: conjunto de métodos, tecnologias e processos voltados para lidar com grandes volumes de dados, em alta velocidade e com alta variedade, de forma que ferramentas tradicionais não conseguem processar de maneira eficiente.
- O big data não é apenas a base de dados, mas toda a arquitetura que envolve armazenamento, processamento, extração de informações e apresentação de informações por meio de ferramentas de visualização (como um dashboard ou um painel). O big data, portanto, é um processo.
- Para ser considerada big data, uma base de dados deve ter "os 3 Vs":
  - Volume;
  - Velocidade;
  - Variedade.
- Objetivo principal: extrair valor e gerar conhecimento a partir de dados massivos, estruturados ou não, para embasar decisões e criar vantagens competitivas.
- O valor é outra característica fundamental do big data, pois os dados devem entregar informações que trazem vantagens competitivas.

> [!TIP] DICAS:
> - As ferramentas tradicionais não conseguiriam transformar esses dados em informações de maneira eficiente.
> - A partir do processamento das informações, é possível chegar ao conhecimento, cuja consolidação se transforma em sabedoria.
> - As bases de dados de big data geram valor para quem as possui.

## 3. Origem
- Explosão de dados com a popularização da internet, redes sociais, dispositivos móveis e sensores.
- Avanço de tecnologias de armazenamento e processamento distribuído (como Hadoop e Spark).
- Necessidade crescente de análises em tempo real para apoiar processos críticos.
- Hoje, um conceito muito conhecido, ligado ao big data, é a internet das coisas, que significa ter outros aparelhos além do computador conectados à internet, gerando dados. Um exemplo disso são as câmeras de vigilância que mandam informações em tempo real para a nuvem.
- As fontes de big data, como as redes sociais, inserem dados nos repositórios de computadores, nos quais são feitos o processamento e a transformação dos dados para gerar modelagens por meio da IA.

> [!TIP] DICAS:
> - Os algoritmos, como o do Instagram, sabem tudo sobre a vida dos usuários, pois a IA consome os dados de big data e identifica padrões de comportamento.
> - Isso é muito útil para empresas que querem vender produtos, pois assim podem exibir anúncios personalizados.

## 4. Principais Tecnologias
- Armazenamento e processamento distribuído: Hadoop, Apache Spark.
- Bancos NoSQL: MongoDB, Cassandra, HBase.
- Ferramentas de ingestão: Apache Kafka, Flume, Sqoop.
- Análise e visualização: Tableau, Power BI, Kibana.
- Os bancos NoSQL (não relacionais) são flexíveis e distribuídos e são tecnologias utilizadas "por baixo" do armazenamento.
- A ingestão ocorre quando as fontes, como as redes sociais, inserem dados nos repositórios de computadores (data lake).

## 5. Modelos de Processamento
- Batch Processing (Lote): processamento de grandes volumes de dados em intervalos definidos.
- Stream Processing (Streaming): processamento contínuo e incremental de dados assim que chegam.
- Processamento significa transformar os dados em informação que faça sentido para quem irá consumi-la.
- O processamento pode ocorrer de tempos em tempos (em lote) ou em tempo real (que tem sido mais utilizado).

## 6. Características
- Processamento distribuído: dados armazenados e processados em múltiplos nós/servidores para ganho de desempenho e escalabilidade.
- Escalabilidade horizontal: possibilidade de adicionar novos servidores para aumentar a capacidade de armazenamento e o processamento.
- Alta disponibilidade: arquiteturas tolerantes a falhas, com replicação e recuperação automática.
- Baixa latência em streaming: suporte à ingestão e análise de dados contínuos com baixa demora entre chegada e processamento.
- Capacidade de integração: conexão com múltiplas fontes: APIs, sensores IoT, bancos de dados, logs, redes sociais.
- Flexibilidade de modelagem: uso de modelos não relacionais (NoSQL) e esquemas flexíveis (schema-on-read).
- Segurança e governança: controle de acesso, criptografia, trilhas de auditoria e conformidade legal (LGPD, GDPR).

> [!CAUTION] OBSERVAÇÃO:
> - A replicação faz cópias dos dados em outros computadores. Isso é útil no caso de o computador original ser destruído, por exemplo, para que os dados não sejam perdidos.
> - O streaming deve ser rápido, isto é, deve entregar os vídeos ao vivo e sem demora do outro lado.
> - Nos bancos relacionais, a estrutura é rígida; já os dados do big data devem ter flexibilidade de modelagem.

## 7. Fontes de Big Data

### 7.1 Dispositivos e Sensores (IoT)
- Sensores industriais e de manufatura.
- Dispositivos médicos (wearables, monitores de saúde).
- Sensores agrícolas (umidade, temperatura, solo).
- Equipamentos de transporte e logística (GPS, telemetria).

### 7.2 Sistemas Corporativos
- ERPs (Enterprise Resource Planning).
- CRMs (Customer Relationship Management).
- Sistemas de gestão de estoque e logística.
- Registros de transações financeiras.

### 7.3 Web e Mídias Digitais
- Redes sociais (Facebook, X/Twitter, Instagram, TikTok).
- Sites de comércio eletrônico.
- Blogs, fóruns e portais de notícias.
- Vídeos, imagens e transmissões ao vivo.

### 7.4 Registros de Operações e Logs
- Logs de servidores e aplicações.
- Dados de navegação e cliques (clickstream data).
- Registros de segurança e autenticação.

### 7.5 Dispositivos Móveis
- Aplicativos mobile (dados de uso e geolocalização).
- Serviços de mapas e rotas.
- Transações via dispositivos móveis.

### 7.6 Dados Públicos e Governamentais
- Portais de dados abertos (Open Data).
- Estatísticas oficiais (IBGE, INEP).
- Registros de licitações, contratos e gastos públicos.

### 7.7 Fontes Científicas
- Bases de dados de pesquisa (genômica, astronômica, climática).
- Registros de experimentos e simulações.

### 7.8 Multimídia
- Áudio (podcasts, chamadas gravadas, reconhecimento de voz).
- Imagens e vídeos (câmeras de vigilância, streaming).
- Reconhecimento de padrões visuais (visão computacional).

> [!TIP] DICAS:
> - Uma das principais características do big data é o grande volume de dados.
> - Fontes como transações de aplicativos bancários e financeiros são exemplos clássicos de dados que contribuem para o big data.