# Anotações

# Prevenção e Tratamento de Incidentes – Introdução

## 1.1 Conceitos Fundamentais

### 1.1.1 Incidente de Segurança da Informação
- Qualquer **evento adverso**, confirmado ou sob suspeita, relacionado à segurança dos sistemas de computação ou das redes de computadores.
- Pode ocorrer por **ação intencional** ou **acidental**.
- Exige **resposta imediata e eficaz**.

### 1.1.2 Tratamento de Incidentes
- Processo de **identificar, mitigar e prevenir** incidentes de segurança da informação.

### 1.1.3 Exemplos de Incidentes de Segurança
- Tentativas (com ou sem sucesso) de ganhar **acesso não autorizado** a sistemas ou dados.
- **Interrupção indesejada** ou **negação de serviço**.
- **Uso não autorizado** de um sistema para processamento ou armazenamento de dados.
- Modificações não autorizadas nas características de **hardware, *firmware* ou *software*** de um sistema.

## 1.2 Prevenção de Incidentes
- Atividade **proativa** – busca contínua por fragilidades que possam expor a organização a riscos.
- Envolve a **identificação de possíveis vulnerabilidades** antes que se transformem em problemas reais.
- Exige **monitoramento constante** dos sistemas e implementação de controles para mitigar riscos potenciais.

## 1.3 CSIRT – Computer Security Incident Response Team

### 1.3.1 Conceito
- **CSIRT** (*Computer Security Incident Response Team*): Equipe de Resposta a Incidentes de Segurança de Computadores.
- Organização responsável por **receber, analisar e responder** a notificações e atividades relacionadas a incidentes de segurança em computadores.

### 1.3.2 Siglas Relacionadas

| SIGLA | SIGNIFICADO |
|-------|-------------|
| **CSIRT** | *Computer Security Incident Response Team* – Equipe de Resposta a Incidentes de Segurança de Computadores |
| **CIRC** | *Computer Incident Response Capability* – Capacidade de Resposta a Incidentes de Computadores |
| **CIRT** | *Computer Incident Response Team* – Equipe de Resposta a Incidentes de Computadores |
| **IRC** | *Incident Response Center* ou *Incident Response Capability* – Centro/Capacidade de Resposta a Incidentes |
| **IRT** | *Incident Response Team* – Equipe de Resposta a Incidentes |
| **SERT** | *Security Emergency Response Team* – Equipe de Resposta a Emergências de Segurança |
| **SIRT** | *Security Incident Response Team* – Equipe de Resposta a Incidentes de Segurança |

### 1.3.3 Atuação do CSIRT

**Redução do Impacto de um Incidente:**
- Depende da **agilidade de resposta**.
- Depende da **redução no número de vítimas**.

**Sucesso depende da confiabilidade:**
- **Nunca divulgar dados sensíveis.**
- **Não expor vítimas.**

> [!CAUTION] OBSERVAÇÃO
> **O CSIRT NÃO É INVESTIGADOR:**
> - O foco do CSIRT é **entender o que aconteceu** para resolver o incidente.
> - A **perícia** é responsável por **investigar criminalmente**.
> - Se identificados **crimes**, o CSIRT deve: atuar na **preservação de evidências**; e **auxiliar investigações posteriores**.

### 1.3.4 Tipos de CSIRT

| TIPO | DESCRIÇÃO |
|------|-----------|
| **CSIRT internos** | Pertencem exclusivamente a uma organização específica |
| **CSIRT nacionais** | Atuam em mais de um órgão, de forma centralizada |
| **Centros de Coordenação** | Coordenam diversas equipes de CSIRTs internos |
| **Centros de Análise** | Especializam-se em determinado tipo de análise (ex.: artefatos maliciosos) |
| **Grupos de empresas fornecedoras** | Atuam na prevenção e tratamento de incidentes relacionados a hardware/software fornecidos |
| **Empresas prestadoras de serviço CSIRT** | Terceirização do serviço (possível na iniciativa privada, mas **não na administração pública federal**) |

> [!CAUTION] OBSERVAÇÃO
> **Administração Pública Federal:** a terceirização do CSIRT **não é permitida**, pois a segurança da informação é responsabilidade de um servidor público. Pode-se contratar apoio, mas a **responsabilidade final não pode ser delegada**.

### 1.3.5 Papel do CSIRT – Três Categorias de Serviços

O CSIRT realiza três categorias de serviços:

**1. Serviços Reativos (*Reactive Services*):**
- **Alertas e Avisos** (*Alerts and Warnings*).
- **Tratamento de Incidentes** (*Incident Handling*): análise, resposta no local, suporte e coordenação.
- **Tratamento de Vulnerabilidades** (*Vulnerability Handling*): análise, resposta e coordenação.
- **Tratamento de Artefatos** (*Artifact Handling*): análise, resposta e coordenação de artefatos maliciosos.

**2. Serviços Proativos (*Proactive Services*):**
- **Monitoramento Tecnológico** (*Technology Watch*).
- **Auditoria e Avaliação de Segurança** (*Security Audit or Assessments*).
- **Configuração e Manutenção** de ferramentas, aplicações e infraestruturas de segurança.
- **Desenvolvimento de Ferramentas de Segurança**.
- **Serviços de Detecção de Intrusão** (*Intrusion Detection Services*).
- **Disseminação de Informações Relacionadas à Segurança**.

**3. Serviços de Gerenciamento da Qualidade da Segurança (*Security Quality Management Services*):**
- **Análise de Risco** (*Risk Analysis*).
- **Planejamento de Continuidade de Negócios e Recuperação de Desastres**.
- **Consultoria em Segurança**.
- **Construção de Conscientização** (*Awareness Building*).
- **Educação e Treinamento** (*Education/Training*).
- **Avaliação e Certificação de Produtos** (*Product Evaluation or Certification*).

### 1.3.6 Tabela Resumo dos Serviços do CSIRT

| CATEGORIA | SERVIÇOS |
|-----------|----------|
| **Serviços Reativos** | Alertas e avisos; tratamento de incidentes; tratamento de vulnerabilidades; tratamento de artefatos |
| **Serviços Proativos** | Monitoramento tecnológico; auditoria; configuração/manutenção; desenvolvimento de ferramentas; detecção de intrusão; disseminação de informações |
| **Gerenciamento da Qualidade da Segurança** | Análise de risco; continuidade de negócios; consultoria; conscientização; treinamento; avaliação/certificação de produtos |

## 1.4 Exemplo Prático – Cenário de Incidente

> **Atenção/Exceção:** Ordem correta dos eventos em um ataque com *malware*:
> 1. **Malware** infecta o dispositivo.
> 2. **Conexão ao servidor C2** (*Command and Control*).
> 3. **Emissão de comandos** para a máquina infectada atacar outras redes (DDoS).

### 1.4.1 Ações de Resposta (Esquema do Professor)

| ATOR | AÇÕES |
|------|-------|
| **Usuário** | Limpeza da máquina; atualização de sistemas; capacitação |
| **Rede** | Correção de problemas; remoção de arquivo malicioso; *anti-spoofing* |
| **Desenvolvedor** | Desenvolvimento de sistemas mais seguros |
| **Vítima do DDoS** | Aumento de recursos; ferramentas de mitigação |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE-2021-TCE-RJ-ANALISTA DE CONTROLE EXTERNO-ESPECIALIDADE: TECNOLOGIA DA INFORMAÇÃO)

A respeito de segurança em redes de computadores e criptografia, julgue o item seguinte.

No que se refere à prevenção e ao tratamento de incidentes, um dos papéis do CSIRT (*Computer Security Incident Response Team*) é investigar criminalmente os incidentes ocorridos e decidir sobre o acionamento da justiça em cada caso.

**Gabarito:** E (Errado) - O CSIRT resolve o incidente de segurança da informação; a investigação criminal é realizada por perito criminal e autoridades responsáveis. O CSIRT atua na preservação de evidências e auxílio a investigações, mas não investiga criminalmente.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*