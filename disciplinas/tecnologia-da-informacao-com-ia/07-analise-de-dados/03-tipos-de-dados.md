# Tipos de Dados

## 1. Dados Estruturados
- Apresentam um formato definido e rígido que proporciona facilidade de análise e integração simples entre diferentes fontes de dados.
- Exemplos comuns: bancos de dados relacionais e planilhas eletrônicas como as do excel.
- Sgbd relacionais: ferramentas como mysql, postgresql, oracle e sql server utilizadas para gerenciar esses dados.
- Ferramentas de bi: softwares como tableau, power bi e qlikview que selecionam e processam diversas fontes estruturadas.
- Processo de integração: as fontes são reunidas por meio de etl (extração, transformação e carga) para serem organizadas em modelos dimensionais.
- Destino dos dados: após o processamento, as informações são carregadas em um data warehouse para permitir a tomada de decisões gerenciais via operações olap.
- Atributos técnicos: os campos e atributos são obrigatoriamente definidos por um esquema pré-estabelecido.

| CARACTERÍSTICA | DESCRIÇÃO |
|---|---|
| Formato | Definido e com rigidez |
| Facilidade | Análise e integração simples |
| Exemplos | Bancos relacionais e planilhas |
| Ferramentas etl | Talend e apache nifi |

> [!TIP] DICAS: 
> - ETL ⟶ Conjunto de ferramentas que retira os dados da área de produção para uma zona intermediária onde ocorrem as transformações necessárias antes da carga final.

## 2. Dados Não Estruturados
- Caracterizam-se pelo formato livre e grande diversidade de tipos, o que resulta em uma análise de alta complexidade.
- Natureza técnica: consistem em dados binários que demandam intervenção humana ou processamentos sofisticados de inteligência artificial para a extração de significado.
- Contexto de aplicação: estão intrinsecamente relacionados ao conceito de big data devido ao volume e variedade.
- Exemplos comuns: arquivos de texto, e-mails, imagens, vídeos, áudios, documentos em pdf e postagens em redes sociais.
- Sistemas de armazenamento: hadoop hdfs, amazon s3 e google cloud storage.
- Bancos de dados nosql: cassandra, amazon dynamodb e neo4j.

### 2.1 Ferramentas de Análise e Processamento
- Análise de texto: utiliza ferramentas como apache lucene, elasticsearch e solr.
- NLP (Processamento de Linguagem Natural): emprego de bibliotecas como nltk, spacy, tensorflow e bert.
- Processamento de imagens e vídeos: uso de frameworks como opencv, tensorflow e pytorch.
- Inteligência artificial: requer a criação de modelos de treinamento validados por bibliotecas de python para a geração de redes neurais artificiais treinadas.

| CATEGORIA DE ANÁLISE | FERRAMENTAS E BIBLIOTECAS |
|---|---|
| Armazenamento | Hadoop hdfs e amazon s3 |
| Redes neurais | Tensorflow e pytorch |
| Visão computacional | Opencv |

> [!CAUTION] OBSERVAÇÃO: 
> - O simples fato de armazenar um vídeo ou uma imagem dentro de um campo em um banco de dados relacional não transforma esse conteúdo em um dado estruturado.

## 3. Dados Semiestruturados
- Representam a categoria intermediária localizada entre os modelos estruturados e não estruturados.
- Características: possuem um formato que não é tabular, mas que apresenta um nível mínimo de estrutura interna para organização.
- Exemplo principal: arquivos formatados em linguagem xml.

> [!CAUTION] OBSERVAÇÃO: 
> - O business intelligence (bi) tradicional possui relação direta com dados estruturados; o uso de dados não estruturados ocorre apenas em modelos de bi modernos.