# DataMesh

## 1. Conceito de DataMesh
- O DataMesh, ou malha de dados, é um modelo arquitetônico para Big Data onde os dados são armazenados e processados para gerar informações.
- Diferentemente do modelo tradicional, os dados não ficam centralizados em um único repositório (como Data Lake ou Data Warehouse) para serem extraídos posteriormente por cientistas de dados.
- Neste modelo, cada área de negócio assume a responsabilidade pelos seus próprios dados, conduzindo processos de gestão, processamento, modelagem e geração de produtos de dados.
- A noção de "produto" é central, pois os dados são concebidos como produtos que devem ter qualidade para serem consumidos, assim como um software.
- Apesar da descentralização, um órgão central permanece para prestar suporte às demais áreas, desenvolvendo padrões e aplicando governança orientada por código.

### 1.1 Características Principais
- Abordagem moderna de arquitetura de dados.
- Descentraliza a responsabilidade pelos dados.
- Os domínios de negócio são responsáveis por seus próprios produtos de dados.

> [!CAUTION] OBSERVAÇÃO:
> - O DataMesh rompe com o modelo tradicional de centralização, onde a responsabilidade pelos dados estava concentrada em uma API, Data Lake ou Data Warehouse.

## 2. Problema Tradicional com Big Data
- Nos modelos tradicionais, os dados são centralizados em um Data Lake ou Data Warehouse.
- Uma equipe central (geralmente de engenharia de dados ou BI) coleta, limpa, transforma e disponibiliza os dados.
- Essa estrutura gera gargalos, sobrecarga da equipe central e distanciamento dos dados em relação ao negócio.
- Exemplo prático: Na Secretaria Federal de Controle (SFC), auditores dependem da Diretoria de TI para cruzar bases de dados, inserindo suas demandas em filas de priorização.

> [!TIP] DICAS:
> - A centralização retarda respostas e afasta os dados das necessidades reais do negócio.
> - O DataMesh surge como alternativa, transferindo a gestão dos dados para as áreas responsáveis pelo negócio.

## 3. Princípios do DataMesh
- O DataMesh é fundamentado em quatro princípios essenciais, concebidos por Zhamak Dehghani.

### 3.1 Domínio Orientado (Domain-Oriented Ownership)
- Cada domínio de negócio (ex: RH, Vendas, Logística) é responsável por seus próprios dados, como se fossem produtos.
- As equipes de domínio passam a produzir, manter e servir dados de forma independente.
- Incentiva o conhecimento do dado por quem realmente entende do negócio.
- Reduz a dependência de times centralizados de dados.

### 3.2 Dados como Produto (Data as a Product)
- Os dados devem ser tratados como produtos reais, com foco em qualidade, usabilidade e confiabilidade.
- Cada conjunto de dados deve ter um responsável (product owner).
- Os "data products" devem ser descobertos, compreendidos e reutilizados facilmente.
- Os usuários (cientistas de dados, analistas) são tratados como clientes desses dados.

> [!CAUTION] OBSERVAÇÃO:
> - Dados de baixa qualidade equivalem a produtos ruins, que deixarão de ser consumidos.
> - A responsabilidade pela qualidade recai sobre a área de negócio, detentora do conhecimento necessário para garantir utilidade e confiabilidade.

### 3.3 Infraestrutura de Dados como Plataforma (Self-Serve Data Infrastructure as a Platform)
- Fornecer uma plataforma de autoatendimento padronizada para que os domínios possam publicar, acessar e manter dados com facilidade.
- A equipe de plataforma fornece ferramentas para ingestão, validação, versionamento e acesso a dados.
- Reduz a barreira técnica para equipes de domínio que não são especialistas em engenharia de dados.

> [!TIP] DICAS:
> - Características-chave: descentralização operacional, centralização tecnológica e democratização.
> - Vantagens: elimina a necessidade de cada domínio desenvolver sua própria infraestrutura, mantém padrões de qualidade e governança, preserva a autonomia das áreas e otimiza investimentos.

### 3.4 Governança Federada Computacional (Federated Computational Governance)
- Estabelecer padrões de governança de dados descentralizada, com regras compartilhadas e automatizadas.
- Cada domínio segue políticas comuns de segurança, qualidade e compliance.
- Essas políticas são implementadas por código (governança como código).
- A governança não é centralizada, mas coordenada entre os domínios.

> [!CAUTION] OBSERVAÇÃO:
> - A estrutura federada permite que os domínios colaborem entre si na definição dos padrões, sem uma autoridade unilateral, similar a um Estado federativo (ex: Brasil).

## 4. Vantagens e Desafios

### 4.1 Vantagens
- Escalabilidade organizacional.
- Agilidade.
- Qualidade e confiança.

### 4.2 Desafios
- Mudança cultural.
- Padrões e interoperabilidade.
- Complexidade inicial.

> [!TIP] DICAS:
> - A escalabilidade organizacional ocorre pela capacidade de executar processos de gestão, processamento e modelagem de dados em paralelo.
> - A qualidade e confiabilidade são reforçadas porque a responsabilidade pelos dados fica a cargo dos profissionais da área de negócio, não apenas da TI.

## 5. Diferença Entre DataMesh e DataLake
- O Data Lake é um repositório centralizado que armazena dados em seu estado bruto, estruturados ou não.
- O DataMesh não é um repositório, mas uma arquitetura que determina como as responsabilidades relativas aos dados devem ser distribuídas.

> [!CAUTION] OBSERVAÇÃO:
> - O Data Lake e o DataMesh não são tecnologias concorrentes e podem coexistir.
> - O DataLake é um repositório; o DataMesh é uma arquitetura de distribuição de responsabilidades.