# Engenharia de Software - Requisitos 6

## 1. Gerenciamento de Requisitos
- É o processo ou atividade de compreensão e controle das mudanças nos requisitos do sistema.
- É necessário manter a par das necessidades individuais e manter as ligações entre as necessidades dependentes para conseguir avaliar o impacto das mudanças.
- Precisa ser estabelecido um processo formal para fazer propostas de mudanças e a ligação destas às exigências do sistema.
- A evolução do sistema é evidente após a elaboração do documento de requisitos e a implementação. Como a maioria dos processos é interativa e incremental, um processo claro para solicitar mudanças deve ser estabelecido e incorporado ao documento de requisitos.
- O processo formal de gerenciamento de requisitos deve começar assim que uma versão preliminar do documento de requisitos estiver disponível.
- O planejamento de como gerenciar as mudanças deve começar durante o processo de elicitação de requisitos, embora o profissional não realize a gestão diretamente nessa fase.
- Um documento de requisitos inflexível pode impossibilitar mudanças, dificultar o controle de versão e as evoluções do sistema.

### 1.1 Planejamento
- É o primeiro estágio do gerenciamento de requisitos.
- Deve ser determinado o nível de detalhamento requerido para o gerenciamento.

#### 1.1.1 Identificação de Requisitos
- Cada requisito deve ser identificado unicamente para poder ser comparado com outros requisitos e usado em avaliações de rastreabilidade.
- A rastreabilidade, frequentemente documentada em uma matriz de rastreabilidade, é a chave para identificar como um requisito impacta outro.
- Modelos de qualidade de software, como MPS-BR (Melhoria de Processo de Software Brasileiro) e CMMI (internacional), incorporam a engenharia de requisitos e abordam a rastreabilidade desde o requisito até o código-fonte.
- A identificação única é fundamental para verificar, por exemplo, se um trecho de código no versionador atende a um requisito específico.

#### 1.1.2 Processo de Gerenciamento de Mudanças
- É o conjunto de atividades que avaliam o impacto e o custo das mudanças.

> [!CAUTION] OBSERVAÇÃO: 
> - A RDM (Requisição de Mudança) é um termo comum na área de infraestrutura para pedidos de alteração. No contexto de requisitos, a RDM é aplicada quando um profissional precisa modificar um requisito existente ou implementar um novo.

#### 1.1.3 Políticas de Rastreabilidade
- Definem os relacionamentos entre cada requisito e entre os requisitos e o projeto de sistema.
- Devem definir como esses registros de relacionamento devem ser mantidos.

#### 1.1.4 Ferramentas de Apoio
- Ferramentas que podem ser usadas variam desde sistemas especializados em gerenciamento de requisitos até planilhas e sistemas de banco de dados simples.

## 2. Gerenciamento de Mudanças de Requisitos
- O processo de gerenciamento de mudanças é composto por três estágios principais.

### 2.1 Análise de Problema e Especificação de Mudanças
- Analisa-se o problema ou a proposta de mudança para verificar sua validade.
- Essa análise é transmitida a quem solicitou a mudança para avaliação da real necessidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Mesmo que uma funcionalidade passe pela validação de requisitos, pode ocorrer de não ter sido implementada da forma correta.

### 2.2 Análise de Mudanças e Custos
- O custo da mudança é estimado em termos de modificações no documento de requisitos e, se apropriado, no projeto e implementação do sistema.
- Após essa análise, decide-se prosseguir ou não com a mudança.

### 2.3 Implementação de Mudanças
- O documento de requisitos e, quando necessário, o projeto e implementação do sistema são modificados.
- O documento de requisitos deve ser organizado para permitir alterações sem a necessidade de ampla reformulação ou reorganização.

> [!TIP] DICAS: 
> - As mudanças organizacionais e mudanças no negócio, mesmo que no escopo do sistema de software em desenvolvimento, devem ser tratadas pelo mesmo processo de gerenciamento de alterações utilizado para requisitos técnicos.
> - Em toda a análise de custos e viabilidade, deve-se também fazer a análise de riscos.