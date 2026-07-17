# Anotações

# Microsoft SDL – Security Development Lifecycle

## 1.1 Conceito Geral do Microsoft SDL

- Processo de garantia de segurança focado no desenvolvimento e operação de software seguro (***Dev Sec Ops***).
- Fornece requisitos de segurança detalhados e mensuráveis para desenvolvedores e engenheiros reduzirem o número e a gravidade das vulnerabilidades nos produtos e serviços da Microsoft.
- Incorpora três elementos fundamentais: requisitos de segurança abrangentes; ferramentas específicas de tecnologias; e processos obrigatórios no desenvolvimento e no funcionamento dos produtos.

> ### 1.1.1 Integração com DevSecOps e Zero Trust
> **Atenção/Exceção:** A Microsoft trouxe para dentro do seu processo de desenvolvimento o ***Dev Sec Ops***, integrando desenvolvimento, operação e segurança. Dessa forma, um setor não pode mais jogar a responsabilidade para outro setor ao surgir alguma vulnerabilidade.
> A abordagem parte do pressuposto da **confiança zero** (*zero trust*), onde todos precisam caminhar conforme os requisitos de segurança, tanto na arquitetura quanto na governança, sem depositar a confiança em outros.

## 1.2 Funcionamento do Processo - Etapas e *Gates*

- Cada etapa do processo avalia os riscos associados ao seu término, para que possa seguir para a etapa seguinte.
- O ***gate*** apresenta uma lista de verificação que precisa ser conferida e aprovada antes de continuar para a etapa seguinte.
- Exemplo prático: para sair da etapa de *design* e codificação, é preciso fazer análise estática do código; para entrar na construção, é preciso realizar análise binária antes.
- Independentemente da forma como o usuário acessará o sistema (nuvem ou instalação local), haverá um processo de execução monitorado.

### 1.2.1 Práticas do SDL
- Estabelecer padrões de segurança, métricas e governança.
- Exigir o uso de recursos, linguagens e *frameworks* de segurança comprovados.
- Realizar revisão de *design* de segurança e **modelagem de ameaças** (*threat modeling*), gerando arquiteturas resistentes a determinadas ameaças.
- Definir e usar padrões de criptografia.
- Proteger a cadeia de suprimentos de software.
- Proteger o ambiente de engenharia (servidor de homologação, produção, teste etc.).
- Realizar testes de segurança (***SAST***, ***DAST***, ***SCA***, entre outros).
  - **SCA:** está relacionado à cadeia de suprimentos, analisando a composição dos sistemas utilizados.
- Garantir a segurança da plataforma operacional.
- Implementar monitoramento e resposta de segurança.
- Fornecer treinamento em segurança, considerando atualizações constantes.

## 1.3 Fases do SDL

### 1.3.1 Training (Treinamento)
- Todos os funcionários da Microsoft são obrigados a concluir a formação geral de segurança e sensibilização para a privacidade, bem como formação específica relacionada à sua função.
- Formação inicial para novos colaboradores após a contratação e formação anual de atualização obrigatória.
- Programadores e engenheiros participam de formação específica de funções para manter-se informados sobre noções básicas de segurança e tendências recentes.
- Todos os funcionários (tempo integral, estagiários, contingentes, subcontratados e terceiros) são encorajados a buscar formação avançada.

### 1.3.2 Requirements (Requisitos)
- Cada produto, serviço e funcionalidade começa com requisitos de segurança e privacidade claramente definidos.
- Equipes definem requisitos com base em fatores como tipo de dados processados, ameaças conhecidas, melhores práticas, regulamentos e lições aprendidas.
- Requisitos são claramente documentados e controlados.
- Requisitos mudam ao longo do ciclo de vida para refletir alterações na funcionalidade e no panorama de ameaças.

### 1.3.3 Design
- Realização da **modelagem de ameaças** (*threat modeling*).
- Processo em três etapas: planejamento inicial; diagramação com o *design* para identificar e mitigar ameaças; validação do modelo.
- O modelo evita que ameaças ultrapassem o *design* do produto ou sistema.

### 1.3.4 Implementation (Implementação)
- Fase de codificação, onde programadores escrevem código conforme plano das fases anteriores.
- Microsoft fornece ferramentas de desenvolvimento seguras (compiladores, ambientes de desenvolvimento seguros e verificações de segurança incorporadas).

### 1.3.5 Verification (Verificação)
- **Análise de código estático (SAST):** verifica vulnerabilidades no código-fonte antes da execução.
- **Análise binária:** análise do código compilado.
- **Scanner de credenciais e segredos:** verifica se no código fonte estão expostos segredos como senhas, URLs etc. Itens importantes que não fiquem expostos para evitar engenharia reversa com credenciais de acesso.
- **Análise de encriptação.**
- **Teste *fuzz*:** expõe o sistema a entradas nos limites de *buffer* para verificar comportamento.
- **Validação da configuração.**
- **Governança de Componentes (CG):** utiliza ***SCA*** para verificar se os componentes são seguros.

### 1.3.6 Release (Lançamento)
- **Lançamento em anéis (*rings*):**
  - **Cadência 0:** equipe de desenvolvimento responsável pelo serviço ou funcionalidade.
  - **Anel 1:** todos os funcionários da Microsoft.
  - **Anel 2:** usuários fora da Microsoft que configuraram sua organização ou usuários específicos no canal de lançamento direcionado (similar a teste *beta*).
  - **Anel 3:** lançamento padrão mundial em subfases.

### 1.3.7 Response (Resposta)
- Todos os serviços Microsoft são amplamente registrados e monitorados após o lançamento.
- Identificação de potenciais incidentes de segurança através de um sistema centralizado de monitorização quase em tempo real.

## 1.4 Principais Testes de Segurança

### 1.4.1 SAST - Static Application Security Testing (Análise Estática)
- Teste realizado antes da execução do código, com o código-fonte já desenvolvido.
- Objetivo: identificar vulnerabilidades no código-fonte antes da produção.
- Funciona como uma revisão direta do código-fonte, usando análise estática sem executar o código.
- **Momento de aplicação:** na fase de implementação/verificação.

### 1.4.2 DAST - Dynamic Application Security Testing (Análise Dinâmica)
- **Análise em tempo de execução** do software totalmente compilado.
- Permite verificação de funcionalidades que só podem ser testadas com todos os componentes integrados e em execução.
- Testa interfaces expostas em busca de vulnerabilidades, de fora para dentro.
- Funciona como um teste de caixa preta; a interface já é suficiente para o especialista realizar o teste.
- **Momento de aplicação:** na fase de verificação/release.
- Vulnerabilidades descobertas via DAST costumam custar mais caro para corrigir do que aquelas descobertas no início do ciclo de desenvolvimento.

### 1.4.3 SCA - Software Composition Analysis
- Análise da composição de sistemas utilizados.
- Relacionado à cadeia de suprimentos de software.

### 1.4.4 Teste *Fuzz*
- Exposição do sistema a entradas nos limites de *buffer* para verificar o comportamento.

### 1.4.5 DREAD
- *Framework* de gestão de risco (não é teste).

### 1.4.6 STRIDE
- Metodologia para descoberta de ameaças e vulnerabilidades (não é teste).

## 1.5 Tabela Resumo das Fases e Atividades

| FASE | ATIVIDADES PRINCIPAIS | TESTES RELACIONADOS |
|------|----------------------|---------------------|
| Training | Formação geral e específica em segurança | - |
| Requirements | Definição de requisitos de segurança e privacidade | - |
| Design | Modelagem de ameaças (*threat modeling*) | - |
| Implementation | Codificação com ferramentas seguras | Revisões de código; padrões de codificação e teste |
| Verification | Análises diversas de segurança | SAST; análise binária; scanner de credenciais; análise de encriptação; teste *fuzz*; validação de configuração; SCA |
| Release | Lançamento em anéis (0, 1, 2, 3) | DAST |
| Response | Monitoramento e resposta a incidentes | - |

> ### 1.5.1 Quadro de Testes - Comparativo
> 
> | TESTE | MOMENTO | CARACTERÍSTICA |
> |-------|---------|----------------|
> | SAST | Antes da execução | Análise estática do código-fonte; revisão direta |
> | DAST | Em tempo de execução | Análise dinâmica; aplicação compilada e rodando; teste de caixa preta; mais caro para corrigir |
> | SCA | Durante verificação | Análise de composição de sistemas; cadeia de suprimentos |

> [!TIP] DICAS
> - **SAST** é antes da execução; **DAST** é durante a execução com o software compilado.
> - **SAST** é revisão direta do código-fonte; **DAST** é teste de caixa preta das interfaces expostas.
> - **DREAD** é gestão de risco; **STRIDE** é metodologia de descoberta de ameaças - nenhum deles é teste.
> - **VAST** não existe.

> [!CAUTION] OBSERVAÇÃO
> O **SDL** possui roteiro único, não dois roteiros distintos (um para novos sistemas e outro para manutenção de sistemas existentes). A modelagem de ameaças ocorre na fase de **Design**, não na fase de **Requisitos**.

---

# Questões de Fixação

## Questão 01
(CESGRANRIO/TRANSPETRO/PROFISSIONAL TRANSPETRO DE NÍVEL SUPERIOR/JUNIOR: ÊNFASE 6: PROCESSOS DE NEGÓCIOS/2023)

As práticas de SDL (*Security Development Lifecycle*) recomendam ações importantes que devem ser adotadas por projetistas, arquitetos e programadores durante o processo de desenvolvimento de um software. Um teste muito utilizado é a análise em tempo de execução do software totalmente compilado, permitindo a verificação das funcionalidades que podem apenas ser testadas quando todos os componentes estão integrados e em execução. Esse tipo de teste é conhecido como:

a) SAST.
b) DAST.
c) VAST.
d) DREAD.
e) STRIDE.

**Gabarito:** b

## Questão 02
(SELECON/PREFEITURA DE PONTES E LACERDA – MT/ADMINISTRADOR DE SISTEMAS DE INFORMAÇÃO/2023)

O "*Security Development Lifecycle (SDL)*" consiste em um conjunto de práticas que suportam garantia de segurança e requisitos de conformidade. O SDL ajuda os desenvolvedores a criar softwares mais seguros, reduzindo o número e a gravidade das vulnerabilidades no software. Nesse contexto, existem duas abordagens descritas a seguir:

I – Tem como objetivo identificar as vulnerabilidades no seu código-fonte antes de ele ser colocado em produção. É como uma revisão direta do código-fonte. Para isso são usadas técnicas de análise de código estático para procurar problemas sem precisar executar o código.

II – Tem por objetivo testar as interfaces expostas em busca de vulnerabilidades. Dessa forma, o teste é feito de fora para dentro, sendo que, nesse caso, a interface já é o suficiente para que o especialista realize o teste.

As abordagens descritas em I e II são conhecidas pelas siglas:

a) SAST e DAST.
b) DAST e PAST.
c) PAST e EAST.
d) EAST e SAST.

**Gabarito:** a

## Questão 03
(ESAF/GESTÃO E DESENVOLVIMENTO DE SISTEMAS O SDL/2015)

(*Security Development Lifecycle*), processo de desenvolvimento de software com segurança proposto pela Microsoft, segue, em geral, um fluxo composto pelas fases de treinamento, requisitos, *design*, implementação, verificação, lançamento e resposta. Na fase de implementação são recomendados os seguintes elementos do SDL, exceto:

a) realizar revisões de código.
b) aplicar padrões de codificação e teste.
c) aplicar ferramentas de verificação de código de análise estática.
d) aplicar ferramentas de verificação de código de análise dinâmica.
e) aplicar ferramentas de testes de segurança, incluindo ferramentas de difusão.

**Gabarito:** d

## Questão 04
(CESPE/TCE-PA/AUDITOR DE CONTROLE EXTERNO/ÁREA INFORMÁTICA/ANALISTA DE SEGURANÇA/2016)

Acerca de segurança de banco de dados e de desenvolvimento de software, julgue o item subsecutivo.

Na metodologia de desenvolvimento seguro de software SDL (*Security Development Lifecycle*), a modelagem de ameaças é realizada na fase de requisitos.

**Gabarito:** C (Errado) - A modelagem de ameaças é realizada na fase de **Design**.

## Questão 05
(CESPE/POLÍCIA FEDERAL/PERITO CRIMINAL FEDERAL/CARGO 3/2013)

No que se refere a processos de desenvolvimento seguro de aplicações, julgue os itens subsecutivos. O processo SDL (*Secure Development Lifecycle*) tem sido adotado pela Microsoft no desenvolvimento de alguns de seus produtos, como Windows Server, SQL Server e Exchange Server, reduzindo o número de vulnerabilidades encontradas nesses produtos em versões desenvolvidas sem o uso do SDL. Uma das características desse processo é que ele provê dois roteiros, sendo um com foco no suporte a desenvolvimento de novos sistemas com base em um processo iterativo, e outro que enfoca a manutenção de sistemas já existentes.

**Gabarito:** E (Errado) - O SDL possui roteiro único, não dois roteiros distintos.

## Questão 06
(FGV/PC-AM/PERITO CRIMINAL – 4ª CLASSE/PROCESSAMENTO DE DADOS/2022)

Sobre o ciclo de desenvolvimento seguro de aplicações, assinale V para a afirmativa verdadeira e F para a falsa.

( ) Uma das práticas definidas pelo modelo SDL da Microsoft é a modelagem de ameaças.
( ) Uma análise estática de segurança (SAST) exige que a aplicação já esteja em funcionamento.
( ) O conserto de vulnerabilidades descobertas por meio de análise dinâmica de segurança (DAST) costuma custar mais caro do que aquelas descobertas no início do ciclo de desenvolvimento.

As afirmativas são, respectivamente:

a) F, F, V.
b) F, V, V.
c) V, F, V.
d) V, V, F.
e) F, V, F.

**Gabarito:** c

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | b |
| 02 | a |
| 03 | d |
| 04 | C |
| 05 | E |
| 06 | c |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*