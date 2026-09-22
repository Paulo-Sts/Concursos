# Tratamento de Incidentes de Segurança da Informação

## 1. Processo de Tratamento e Resposta a Incidentes
- O tratamento de incidentes envolve um conjunto estruturado de etapas que devem ser seguidas para identificar, conter, erradicar e recuperar-se de incidentes de segurança.
- Em vez de decorar as etapas, é preferível entender o processo como um todo, pois diferentes autores podem apresentar nomenclaturas ligeiramente distintas.
- O processo divide-se em fases proativas (anteriores ao incidente) e reativas (após a detecção).

### 1.1 Etapas do Processo de Tratamento de Incidentes

#### 1.1.1 Processo 1 (Visão Geral)
- Preparação: organização do processo de tratamento de incidentes, envolvendo recursos, sistemas, ferramentas e pessoal.
- Detecção e relato: espécie de triagem para verificar se o incidente detectado está realmente ocorrendo, de acordo com o relato. Qualquer usuário pode realizar essa etapa.
- Análise e classificação: o profissional de segurança da informação isola o incidente, faz análise inicial e classifica-o (ex.: malware, tentativa de invasão, vazamento de dados, acesso não autorizado).
- Contenção: após a classificação, o incidente deve ser colocado em um ambiente controlado para evitar que ataque outras áreas da organização.
- Recuperação: tentativa de restaurar os ativos de rede e dados afetados.
- Notificação: as ETIRs (Equipe de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos), presentes em todos os órgãos da administração pública, devem identificar, comprovar e controlar o incidente dentro da organização e notificar o CTIR Gov (Centro de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos de Governo). Se a equipe identificar um crime, deve informar as autoridades.
- Documentação: elaboração de um relatório completo sobre o incidente.
- Aprimoramento contínuo: melhoria da organização e dos controles de segurança da informação.

#### 1.1.2 Processo 2 (Visão Detalhada)
- Preparação pré-incidente: antes do incidente ocorrer, de forma proativa, organizando a segurança da informação, mantendo controles atualizados e implementando prevenção.
- Detecção do incidente: etapa de identificação do incidente.
- Resposta inicial: muitas vezes implica na contenção do incidente.
- Formulação da estratégia de resposta.
- Duplicação: estratégia utilizada em alguns incidentes específicos, que consiste em fazer uma cópia do incidente para um local controlado (sandbox).
- Investigação: investigação da causa do incidente.
- Implementação de medidas de segurança.
- Monitoramento de rede.
- Isolamento e contenção: de forma mais estruturada.
- Recuperação de ativos atingidos.
- Elaboração de relatório.
- Acompanhamento.

#### 1.1.3 Processo 3 (Visão Sintética)
- Análise do incidente.
- Resposta ao incidente.
- Notificação do incidente.

### 1.2 Classificação dos Serviços do CSIRT
- Um CSIRT pode prestar serviços reativos e proativos.
- Serviço proativo: prevenção.
- Serviço reativo: tratamento.

| PROCESSO | DESCRIÇÃO |
|----------|-----------|
| Análise do incidente | Estudar a fundo um incidente informado ou atividade observada para determinar escopo, prioridade e ameaça, além de pesquisar possíveis estratégias de ações e erradicação. |
| Resposta ao incidente | Pesquisar e elaborar recomendações e aplicar ações adequadas para recuperação, contenção e prevenção. |
| Notificação do incidente | Servir como ponto central de contato para receber informes de incidentes locais, permitindo que atividades e incidentes reportados sejam coletados em um único local. |

- A notificação do incidente pode ocorrer em dois momentos:
  - Chegada da notificação para entrada no processo de tratamento (ponto focal interno).
  - Notificação para fora do processo, para um CSIRT central (ex.: CTIR Gov).

> [!TIP] DICAS: 
> - A análise envolve estudo, pesquisa e determinação de escopo, prioridade e ameaça.
> - A resposta envolve recomendações e ações concretas de recuperação, contenção e prevenção.
> - A notificação envolve o papel de ponto central de contato para recebimento de relatos.

## 2. Conceitos Fundamentais e Integrações

### 2.1 Proatividade no Tratamento de Incidentes
- A preparação pré-incidente é a fase proativa do processo, envolvendo não apenas a obtenção de ferramentas e desenvolvimento de técnicas, mas também a execução de ações nos sistemas e redes que podem ser examinados em caso de incidentes.
- A equipe de tratamento de incidentes deve atuar constantemente na melhoria dos controles de segurança.
- As demais etapas (tratamento em si) ocorrem em reação a um incidente que ultrapassou as barreiras de prevenção.

> [!CAUTION] OBSERVAÇÃO: 
> - A preparação pré-incidente não é apenas sobre ferramentas e técnicas, mas também sobre ações preventivas nos sistemas e redes.

### 2.2 Relação com a Política de Continuidade de Negócio
- A política de continuidade de negócio trata-se da capacidade estratégica e tática da organização de se planejar e responder a incidentes e interrupções, mantendo operações em nível predefinido.
- O processo de tratamento de incidentes não é independente da política de continuidade de negócio, pois:
  - Ambos tratam da resposta a incidentes.
  - A estratégia de resposta deve alinhar-se ao plano de continuidade de negócio.
  - A finalidade do plano de continuidade de negócio é a manutenção da disponibilidade dos serviços.
  - A estratégia de resposta não serve apenas para determinar responsáveis por ação legal, mas também para resolver o incidente.
- A relação entre tratamento de incidentes e continuidade de negócio é direta e necessária.

### 2.3 Evidências e Integridade do Processo
- Na condução do processo de resposta, é necessário realizar a geração e manutenção sistemática de registros de todo o processo de coleta e manipulação de evidências.
- Deve-se manter informações para verificação da integridade do processo.
- Exemplo: na análise de malware, a primeira ação é gerar um hash para garantir, a qualquer momento, que ajudará na identificação do arquivo original e assegurar a integridade do processo.
- A geração de hash permite verificar se o arquivo foi alterado ao longo da análise.
- A manutenção de registros é essencial para garantir a cadeia de custódia e a validade das evidências.

### 2.4 Estrutura Organizacional para Tratamento de Incidentes
- As organizações devem adotar uma estrutura simples que permita:
  - Rápida reestruturação.
  - Confirmação da natureza e extensão do incidente.
  - Controle da situação e do incidente.
  - Comunicação com as partes interessadas.
- A simplicidade da estrutura facilita a rápida resposta e recuperação de ativos paralisados devido a um incidente.