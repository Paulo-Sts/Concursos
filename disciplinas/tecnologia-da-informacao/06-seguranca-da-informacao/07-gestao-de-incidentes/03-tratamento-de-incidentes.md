# Anotações

# Tratamento de Incidentes

## 1.1 Conceito Geral

- O tratamento de incidentes é o processo de **identificar, mitigar e prevenir** incidentes de segurança da informação.
- Envolve ações **reativas** (em resposta a incidentes que ocorreram) e **proativas** (preparação e prevenção).

> [!TIP] DICAS
> - **Serviços proativos** = prevenção.
> - **Serviços reativos** = tratamento.
> - A **preparação pré-incidente** é a única fase **proativa** do processo de tratamento e resposta.

## 1.2 Processos de Tratamento de Incidentes

O material apresenta três visões diferentes do processo de tratamento de incidentes. As etapas essenciais são:

### 1.2.1 Visão 1 – Etapas do Tratamento de Incidentes

| ETAPA | DESCRIÇÃO |
|-------|-----------|
| **Preparação** | Organização do processo: recursos, sistemas, ferramentas e pessoal |
| **Detecção e Relato** | Triagem – verificar se o incidente detectado está ocorrendo de fato (qualquer usuário pode fazer) |
| **Análise e Classificação** | Isolar o incidente, análise inicial e classificação (*malware*, invasão, vazamento, acesso não autorizado) |
| **Contenção** | Colocar o incidente em ambiente controlado para não atacar outras áreas |
| **Recuperação** | Tentativa de recuperar ativos de rede e dados afetados |
| **Notificação** | Comunicação ao CTIR Gov (Centro de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos de Governo) e autoridades |
| **Documentação** | Relatório completo do incidente |
| **Aprimoramento Contínuo** | Melhorar os controles de segurança da informação |

### 1.2.2 Visão 2 – Processo Estruturado

| ETAPA | DESCRIÇÃO |
|-------|-----------|
| Preparação pré-incidente | Pró-ativa: organização da segurança, controles atualizados, prevenção |
| Detecção do incidente | Identificação do incidente |
| Resposta inicial | Muitas vezes implica contenção |
| Formulação da estratégia de resposta | Planejamento da ação |
| Duplicação | Cópia do incidente para ambiente controlado (*sandbox*) |
| Investigação | Investigação da causa |
| Implementação de medidas de segurança | Correções necessárias |
| Monitoramento de rede | Acompanhamento contínuo |
| Isolamento e contenção | De forma estruturada |
| Recuperação de ativos | Restauração dos ativos atingidos |
| Elaboração de relatório | Documentação completa |
| Acompanhamento | Monitoramento pós-incidente |

### 1.2.3 Visão 3 – Síntese

| ETAPA | DESCRIÇÃO |
|-------|-----------|
| **Análise do incidente** | Estudar o incidente para determinar escopo, prioridade, ameaça e possíveis estratégias |
| **Resposta ao incidente** | Pesquisar, elaborar recomendações e aplicar ações para recuperação, contenção e prevenção |
| **Notificação do incidente** | Servir como ponto central de contato para receber informes |

## 1.3 CTIR Gov – Centro de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos de Governo

- As **ETIRs** (Equipe de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos), presentes em todos os órgãos da administração pública, devem:
  - Identificar, comprovar e, às vezes, controlar o incidente de segurança detectado dentro da organização.
  - **Notificar o CTIR Gov** – Centro de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos de Governo.
- Se a equipe de tratamento de incidentes identifica um **crime**, deve informar às **autoridades** (ex.: Polícia Federal).

## 1.4 Evidências e Integridade do Processo

- Na condução do processo de resposta, é necessário realizar a **geração e manutenção sistemática de registros** de todo o processo de coleta e manipulação de evidências.
- A primeira coisa a se fazer na análise de um *malware* é **gerar um hash** para:
  - Garantir a identificação do arquivo original a qualquer momento.
  - Garantir a **integridade do processo**.

> [!CAUTION] OBSERVAÇÃO
> **A estratégia de resposta deve se alinhar ao plano de continuidade de negócio!** O tratamento de incidentes e a continuidade de negócio estão diretamente relacionados.

## 1.5 Política de Continuidade de Negócio

- Trata-se da capacidade estratégica e tática da organização de se planejar e responder a incidentes e interrupções dos negócios.
- Mantém as operações em um nível previamente definido pelos gestores.
- Tem **relação direta** com o processo de tratamento e resposta a incidentes de segurança da informação.
- A estratégia de resposta **deve se alinhar** ao plano de continuidade de negócio.

> [!TIP] DICAS
> - A organização deve adotar uma estrutura **simples** que permita:
>   - Rápida reestruturação.
>   - Confirmação da natureza e extensão do incidente.
>   - Controle da situação.
>   - Comunicação com as partes interessadas.

## 1.6 Tabela Resumo – Principais Etapas

| ETAPA | PALAVRA-CHAVE | DESCRIÇÃO SINTÉTICA |
|-------|---------------|---------------------|
| Preparação | Pró-ativa | Organizar recursos e controles antes do incidente |
| Detecção | Triagem | Identificar e confirmar o incidente |
| Análise | Classificação | Determinar escopo, prioridade e tipo de ameaça |
| Contenção | Isolamento | Impedir propagação do incidente |
| Recuperação | Restauração | Recuperar ativos e dados afetados |
| Notificação | Comunicação | Reportar ao CTIR Gov e autoridades |
| Documentação | Registro | Gerar relatório completo |
| Aprimoramento | Melhoria | Atualizar controles e processos |

---

# Questões de Fixação

## Questão 01
(CESPE/2013/CPRM/ANALISTA EM GEOCIÊNCIAS/SISTEMAS)

Com referência à prevenção e ao tratamento de incidentes, julgue os itens subsecutivos.

A preparação pré-incidente é a única fase proativa do processo de tratamento e resposta, envolvendo não somente a obtenção de ferramentas e o desenvolvimento de técnicas para a resposta, mas também a execução de ações nos sistemas e redes que possam vir a ser examinados em caso de ocorrência de incidentes.

**Gabarito:** C (Correto)

## Questão 02
(CESPE/2013/TCE-RO/AUDITOR DE CONTROLE EXTERNO/TECNOLOGIA DA INFORMAÇÃO)

Acerca de prevenção e tratamento a ataques a redes de computadores, julgue o item subsecutivo.

O processo de tratamento e de resposta a incidentes de segurança da informação é independente da política de continuidade de negócio.

**Gabarito:** E (Errado) - A política de continuidade de negócio tem relação direta com o processo de tratamento e resposta a incidentes.

## Questão 03
(CESPE/2013/CPRM/ANALISTA EM GEOCIÊNCIAS/SISTEMAS)

Com referência à prevenção e ao tratamento de incidentes, julgue os itens subsecutivos.

A estratégia de resposta não precisa alinhar-se ao plano de continuidade de negócio, uma vez que a estratégia de resposta objetiva determinar os responsáveis pelo incidente, visando ação legal, enquanto a finalidade do plano de continuidade de negócio é a manutenção da disponibilidade dos serviços.

**Gabarito:** E (Errado) - A estratégia de resposta não serve apenas para determinar responsáveis; também visa resolver o incidente. Deve-se alinhar ao plano de continuidade de negócio.

## Questão 04
(CESPE/2013/CPRM/ANALISTA EM GEOCIÊNCIAS/SISTEMAS)

Com referência à prevenção e ao tratamento de incidentes, julgue os itens subsecutivos.

Na condução do processo de resposta, é necessário realizar a geração e manutenção sistemática de registros de todo o processo de coleta e manipulação de evidências, juntamente com as informações para verificação da integridade do processo.

**Gabarito:** C (Correto)

## Questão 05
(CESPE/2012/BANCO DA AMAZÔNIA/TÉCNICO CIENTÍFICO/SEGURANÇA DA INFORMAÇÃO)

A respeito de prevenção e tratamento de incidentes, julgue os itens que se seguem.

Convém que as organizações adotem uma estrutura simples, que permita uma rápida reestruturação e a confirmação da natureza e da extensão do incidente, além de possibilitar o controle da situação e do incidente e a comunicação com as partes interessadas.

**Gabarito:** C (Correto)

## Questão 06
(FCC/2015/MPE-PB/ANALISTA DE SISTEMAS/ADMINISTRADOR DE REDES)

O tratamento de incidentes possui componentes relativos aos serviços reativos que um CSIRT (Computer Security Incident Response Team) pode prestar, quais sejam:

I – Estudar a fundo um incidente informado ou uma atividade observada para determinar o escopo, prioridade e ameaça representada pelo incidente, bem como pesquisar acerca de possíveis estratégias de ações e erradicação.

II – Pesquisar e elaborar recomendações e aplicar as ações adequadas para a recuperação, contenção e prevenção de incidentes.

III – Servir como um ponto central de contato para receber informes de incidentes locais. Isto permite que todas as atividades e os incidentes reportados sejam coletados em um único local.

Os componentes do tratamento de incidentes descritos em I, II e III correspondem, correta e respectivamente, a

a) análise do incidente, resposta ao incidente e notificação do incidente.
b) recepção do incidente, recomendações para o incidente e resposta ao incidente.
c) notificação do incidente, análise do incidente e resposta ao incidente.
d) verificação do incidente, mitigação do incidente e análise do incidente.
e) resposta ao incidente, notificação do incidente e análise do incidente.

**Gabarito:** a

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | E |
| 03 | E |
| 04 | C |
| 05 | C |
| 06 | a |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*