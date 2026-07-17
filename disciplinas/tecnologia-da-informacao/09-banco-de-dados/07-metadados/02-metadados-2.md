# Anotações – Banco de Dados – Metadados II (Dublin Core, OAI-PMH e Classificação)

## 1. Metadados e Web Semântica

- Metadados são **dados que descrevem outros dados**, organizando recursos informacionais.
- São amplamente associados à **web semântica** – a ideia de encontrar o significado dos dados nas páginas da internet.
- Para isso, "jogam-se" metadados em tudo, permitindo identificar a informação.
- **A web semântica** perdeu espaço para a **inteligência artificial** (que faz interpretação semântica de forma mais abrangente).

## 2. Dublin Core

### 2.1 O que é?

- **Dublin Core** é um conjunto de **metadados mínimos** que permite a organização de qualquer recurso informacional.
- Criado em **1995** pela **Dublin Core Metadata Initiative (DCMI)** – organização dedicada ao desenvolvimento de padrões de metadados interoperáveis.
- **Interoperabilidade:** capacidade de um sistema conversar com outro, independentemente da tecnologia (ex.: Java e COBOL trocando informações via XML/JSON).

### 2.2 Características

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Simplicidade** | Apenas 15 elementos. |
| **Interoperabilidade semântica** | Troca de informações mantendo o significado. |
| **Consenso internacional** | Padrão utilizado globalmente. |
| **Extensibilidade** | Possibilidade de estender o comportamento (ex.: `DC:type`). |
| **Modularidade** | Informações organizadas de forma modular. |

### 2.3 Os 15 Elementos do Dublin Core

| ELEMENTO | DESCRIÇÃO |
| --- | --- |
| **Title** | Título do recurso. |
| **Creator** | Criador/autor do recurso. |
| **Subject** | Assunto/palavras-chave. |
| **Description** | Descrição do recurso. |
| **Publisher** | Publicador/editor. |
| **Other Contributors** | Outros contribuidores. |
| **Date** | Data de criação/publicação. |
| **Resource Type** | Tipo do recurso (ex.: tutorial, artigo). |
| **Format** | Formato do arquivo (ex.: PPT, PDF). |
| **Identifier** | Identificador (ex.: URL, ISBN). |
| **Source** | Origem do arquivo. |
| **Language** | Idioma. |
| **Relation** | Relação com outros recursos. |
| **Coverage** | Cobertura (domínio/contexto). |
| **Rights** | Direitos de uso (ex.: licenças, copyright). |

> ### 2.3.1 Exemplo em XML
> ```xml
> <dc:title>Metadados - indexação e recuperação de recursos informacionais na Web</dc:title>
> <dc:creator>Marcondes, Carlos Henriquez</dc:creator>
> <dc:subject>Documentos digitais</dc:subject>
> <dc:subject>Metadados</dc:subject>
> <dc:description>Curso em PowerPoint sobre Metadados e seu uso</dc:description>
> <dc:publisher>UFF - Depto. de Ciência da Informação</dc:publisher>
> <dc:date>2005-03-01</dc:date>
> <dc:type>Tutorial</dc:type>
> <dc:format>apresentação PowerPoint</dc:format>
> <dc:identifier>http://www.professores.uff.br/Marcondes/meta.html</dc:identifier>
> <dc:language>portuguese</dc:language>
> ```

## 3. OAI-PMH (Open Archives Initiative Protocol for Metadata Harvesting)

### 3.1 O que é?

- Protocolo para **coleta e intercâmbio de metadados** entre repositórios de informação.
- Modelo **cliente-servidor**:
  - **Provedores de dados (data providers):** expõem metadados.
  - **Provedores de serviços (service providers):** coletam metadados.
- Utiliza **XML** para a representação dos metadados.
- É compatível com o **Dublin Core**.

### 3.2 Harvesting (Coleta)

- **Harvesting** é o processo de **busca automática, coleta de dados e construção de índices**.
- O protocolo OAI-PMH é o mais famoso para essa finalidade.

## 4. Classificação dos Metadados (por função)

### 4.1 Visão geral

| CATEGORIA | FUNÇÃO | EXEMPLOS |
| --- | --- | --- |
| **Descritivos** | Descrevem o recurso para localização, identificação e compreensão. | Título, autor, assunto, palavras-chave. |
| **Estruturais** | Explicitam a estrutura interna e as relações hierárquicas entre partes. | Ordem de capítulos, posição na estante, sequência de livros em uma série. |
| **Administrativos** | Apoiam a gestão do ciclo de vida do recurso (criação, seleção, descrição, preservação). | Data de criação, tipo de arquivo, permissões de acesso. |

### 4.2 Subdivisões dos Metadados Administrativos

| SUBDIVISÃO | FUNÇÃO | EXEMPLOS |
| --- | --- | --- |
| **Técnicos** | Aspectos e dependências técnicas para decodificar e renderizar o arquivo. | Tamanho do arquivo, formato, codificação, resolução. |
| **Preservação** | Informações para gerência do arquivo digital em longo prazo. | Dependências de hardware/software, histórico de alterações, eventos de preservação. |
| **Direitos** | Gestão dos direitos de propriedade intelectual. | Copyright, termos de licença, permissões de uso. |

> ### 4.2.1 Metadados de Preservação (detalhe)
> - Informações necessárias para preservar e manter a **integridade** e **acessibilidade** dos dados ao longo do tempo.
> - **Integridade:** o dado não foi alterado sem registro.
> - **Acessibilidade:** controle de acesso aos dados.
> - **Exemplos:** datas de criação e modificação, proprietários, permissões de acesso, políticas de retenção.

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/2021/TCE-RJ – Analista)

**Item:** "Dublin Core é um esquema de metadados que auxilia na descrição de objetos digitais por meio da definição de diversos elementos de metadados, entre os quais se incluem título, autor, assunto, formato e fonte."

**Gabarito: Certo (C).**

### 5.2 (CESPE/CEBRASPE/2024/CAPES – Analista/Biblioteconomia)

**Item:** "Dublin Core é um conjunto de itens de metadados utilizados para descrever recursos disponíveis em rede."

**Gabarito: Certo (C).**

### 5.3 (INSTITUTO AOCP/2021/ITEP-RN – Assistente/Biblioteconomia)

**Item incorreto sobre metadados:**

**Gabarito: b) O Dublin Core é um padrão de metadados desenvolvido a partir da ISBD consolidada.**

**Comentário:** Dublin Core foi criado pela DCMI em um workshop, não a partir da ISBD.

### 5.4 (CESPE/CEBRASPE/2020/MPE-CE – Analista/Biblioteconomia)

**Item:** "Entre os quinze elementos básicos do DC estão: creator, coverage, description, relation e type."

**Gabarito: Certo (C).**

### 5.5 (IDECAN/2023/SEFAZ-RR – Administrador de BD)

**Item:** "Protocolo utilizado para coleta de metadados entre dois sistemas de informação."

**Gabarito: b) OAI/PMH.**

### 5.6 (CESPE/CEBRASPE/2022/TRT-8 – Analista/Biblioteconomia)

**Item:** "Processo de busca automática, coleta de dados e construção de índices."

**Gabarito: a) harvesting.**

### 5.7 (CESPE/CEBRASPE/2021/PG-DF – Analista/Biblioteconomia)

**Item:** "Estratégias de preservação de bibliotecas digitais são incompatíveis com o protocolo OAI-PMH."

**Gabarito: Errado (E).**

**Comentário:** O OAI-PMH pode ser usado para trocar metadados de preservação entre bibliotecas digitais.

### 5.8 (IDECAN/2023/SEFAZ-RR – Administrador de BD)

**Item:** "Tipo de metadado utilizado para permitir que um profissional gerencie melhor o ciclo de vida das informações (data de criação, tipo de arquivo, utilidade)."

**Gabarito: c) Administrativo.**

### 5.9 (FGV/2024/TJ-MS – Bibliotecário)

**Item:** "Metadados que documentam como recursos complexos devem ser ordenados."

**Gabarito: d) Estruturais.**

### 5.10 (FGV/2023/TJ-RN – Analista/Biblioteconomia)

**Item:** "Metadados associados ao conteúdo, contexto, estrutura de produção e possíveis alterações."

**Gabarito: b) De preservação.**

### 5.11 (CESPE/CEBRASPE/2022/TRT-8 – Analista/Biblioteconomia)

**Item:** "Tipo de metadado presente na classificação conceitual dos metadados."

**Gabarito: c) Descritivo.**

### 5.12 (FGV/2021/TJ-RO – Bibliotecário)

**Item:** "Metadados que descrevem um recurso com o propósito de descoberta e identificação."

**Gabarito: c) Descritivos.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/TCE-RJ/2021) | C |
| 02 (CESPE/CAPES/2024) | C |
| 03 (AOCP/2021) | b |
| 04 (CESPE/MPE-CE/2020) | C |
| 05 (IDECAN/2023) | b |
| 06 (CESPE/TRT-8/2022) | a |
| 07 (CESPE/PG-DF/2021) | E |
| 08 (IDECAN/2023) | c |
| 09 (FGV/TJ-MS/2024) | d |
| 10 (FGV/TJ-RN/2023) | b |
| 11 (CESPE/TRT-8/2022) | c |
| 12 (FGV/TJ-RO/2021) | c |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Dublin Core** | Conjunto de 15 metadados mínimos para descrever recursos informacionais. |
| **OAI-PMH** | Protocolo para coleta e intercâmbio de metadados (harvesting). |
| **Metadados Descritivos** | Identificam e descrevem o recurso (título, autor, assunto). |
| **Metadados Estruturais** | Organizam a estrutura interna (ordem, hierarquia). |
| **Metadados Administrativos** | Gerenciam o ciclo de vida (criação, permissões, preservação). |
| **Metadados de Preservação** | Mantêm integridade e acessibilidade ao longo do tempo. |
| **Metadados Técnicos** | Detalhes técnicos para decodificação e renderização. |
| **Metadados de Direitos** | Direitos de propriedade intelectual. |

---

*Material complementar à aula "Banco de Dados – Metadados II" (professor Vitor Kessler/Gran Concursos).*