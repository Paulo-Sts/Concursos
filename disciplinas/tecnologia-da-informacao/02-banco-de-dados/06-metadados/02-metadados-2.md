# Metadados 2

## 1. Metadados
- Dado que descreve outro dado.
- São usados para organizar dados e recursos informacionais.
- Estão fortemente associados à web semântica, pois a ideia é encontrar a semântica dos dados nas páginas da internet, aplicando metadados para identificar a informação.
- A web semântica perdeu espaço para a inteligência artificial.

### 1.1 Dublin Core
- Conjunto de metadados mínimos que permite a organização de qualquer recurso informacional.
- É descrito por meio de 15 metadados previstos no Dublin Core.
- Criado em 1995 pela Dublin Core Metadata Initiative (DCMI), organização dedicada ao desenvolvimento de padrões de metadados interoperáveis.

#### 1.1.1 Interoperabilidade
- Capacidade de um sistema conversar com outro.
- Sistemas feitos em linguagens diferentes (ex.: Java e COBOL) conseguem trocar informações usando padrões de dados semiestruturados, como XML e JSON.
- XML com tags e JSON com pares de valor-chave são exemplos de metadados.

#### 1.1.2 Características do Dublin Core
- Simplicidade: apenas 15 elementos.
- Interoperabilidade semântica: possibilidade de trocar informações mantendo a semântica.
- Consenso internacional: utilizado globalmente.
- Extensibilidade: capacidade de estender o comportamento da biblioteca Dublin Core (ex.: DC:type).
- Modularidade: informações organizadas.

#### 1.1.3 Os 15 Elementos do Dublin Core
- Title (título)
- Creator (criador)
- Subject (assunto)
- Description (descrição)
- Publisher (publicador)
- Other Contributors (outros contribuidores)
- Date (data)
- Resource Type (tipo de recurso)
- Format (formato)
- Identifier (identificador)
- Source (fonte)
- Language (idioma)
- Relation (relação)
- Coverage (cobertura)
- Rights (direitos)

#### 1.1.4 Exemplo de Aplicação do Dublin Core em XML
```xml
<dc:title>Metadados - indexação e recuperação de recursos informacionais na Web</dc:title>
<dc:creator>Marcondes, Carlos Henrique</dc:creator>
<dc:subject>Documentos digitais</dc:subject>
<dc:subject>Descrição bibliográfica</dc:subject>
<dc:subject>Metadados</dc:subject>
<dc:description>Curso em PowerPoint sobre Metadados e seu uso</dc:description>
<dc:publisher>UFF - Depto. de Ciência da Informação</dc:publisher>
<dc:date>2005-03-01</dc:date>
<dc:type>Tutorial</dc:type>
<dc:format>apresentação PowerPoint</dc:format>
<dc:identifier>http://www.professores.uff.br/Marcondes/meta.html</dc:identifier>
<dc:language>portuguese</dc:language>
```

> [!TIP] DICAS:
> - O Dublin Core é um esquema de metadados que auxilia na descrição de objetos digitais por meio da definição de diversos elementos, entre os quais se incluem título, autor, assunto, formato e fonte.
> - É um conjunto de itens de metadados utilizado para descrever recursos disponíveis em rede.
> - O Dublin Core fornece metadados para a descrição de recursos eletrônicos.

> [!CAUTION] OBSERVAÇÃO:
> - O Dublin Core NÃO foi desenvolvido a partir da ISBD consolidada. Foi criado pela DCMI em um evento com diversos especialistas.
> - Os metadados nascem da disciplina de biblioteconomia.

## 2. Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH)
- Padrão para troca de informações e coleta de metadados de outros locais.
- Define uma estrutura de metadados intercambiável, permitindo troca entre diversos usuários.
- Protocolo desenvolvido para facilitar a coleta e intercâmbio de metadados entre repositórios de informações.

### 2.1 Modelo Cliente-servidor
- Provedores de dados (data providers): expõem metadados.
- Provedores de serviços (service providers): coletam metadados.

### 2.2 Características
- Utiliza XML para a representação dos metadados.
- Compatível com Dublin Core.

> [!TIP] DICAS:
> - O protocolo utilizado para coleta de metadados entre dois sistemas de informação é o OAI-PMH.
> - O processo de busca automática, coleta de dados e construção de índices é conhecido como harvesting.
> - Estratégias de preservação de bibliotecas digitais são compatíveis com o protocolo OAI-PMH. É possível trocar metadados de preservação entre bibliotecas digitais usando o OAI-PMH.

## 3. Classificação dos Metadados

### 3.1 Metadados Descritivos
- Detalham um recurso digital para localização, identificação ou compreensão.
- Exemplos: título, autor e assunto.

### 3.2 Metadados Estruturais
- Explicitam a estrutura interna do arquivo digital e as relações hierárquicas de partes integrantes de recursos entre si.
- Exemplo: ordem e lugar na hierarquia (ex.: posição de um livro em uma estante ou série).

### 3.3 Metadados Administrativos
- Fornecem informações que apoiam a gestão do ciclo de vida (criação, seleção, descrição etc.) dos recursos informacionais.
- Exemplos: tipo e tamanho de arquivo, data/hora de criação, evento de preservação, status dos direitos autorais e termos de licença.

#### 3.3.1 Subdivisões dos Metadados Administrativos
- Metadados técnicos: indicam os aspectos e as dependências técnicas de um arquivo digital para decodificá-lo e renderizá-lo.
- Metadados de preservação: incluem informações (ex.: dependências de hardware e software) exigidas para a gerência de um arquivo digital em longo prazo.
- Metadados de direitos: documentam informações para apoio à gestão dos direitos de propriedade intelectual associados a um conteúdo.

### 3.4 Metadados de Preservação
- Informações necessárias para preservar e manter a integridade e acessibilidade dos dados ao longo do tempo.
- Integridade: o dado não foi alterado sem que isso seja registrado.
- Acessibilidade: controle de acesso aos dados.
- Armazena conteúdo, contexto, estrutura de produção e possíveis alterações ocorridas.
- Exemplos: datas de criação e modificação; proprietários; permissões de acesso; e políticas de retenção de dados.

> [!TIP] DICAS:
> - Metadados administrativos: utilizados para permitir que um profissional gerencie melhor o ciclo de vida de determinadas informações (ex.: data de criação, tipo de arquivo, utilidade).
> - Metadados estruturais: têm como função documentar como os recursos complexos, compostos por vários elementos, devem ser ordenados.
> - Metadados de preservação: associados ao conteúdo, contexto, estrutura de produção e possíveis alterações ocorridas em um recurso de informação.
> - Metadados descritivos: descrevem um recurso com o propósito de descoberta e identificação.