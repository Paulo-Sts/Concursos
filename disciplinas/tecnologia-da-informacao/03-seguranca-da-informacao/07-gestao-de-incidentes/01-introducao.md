# Introdução a Prevenção e Tratamento de Acidentes

## 1. Conceitos Fundamentais

### 1.1 Incidente de Segurança da Informação
- Qualquer evento adverso, confirmado ou sob suspeita, relacionado à segurança dos sistemas de computação ou das redes de computadores.
- Representa um comprometimento da segurança dos sistemas e dados de uma organização.
- Pode ocorrer tanto por ação intencional quanto acidental e exige resposta imediata e eficaz.

### 1.2 Tratamento de Incidentes
- Processo de identificar, mitigar e prevenir incidentes de segurança da informação.
- Envolve a notificação de entidades externas à organização quando necessário.

### 1.3 Exemplos de Incidentes
- Tentativas (com ou sem sucesso) de ganhar acesso não autorizado a sistemas ou a seus dados.
- Interrupção indesejada ou negação de serviço.
- Uso não autorizado de um sistema para processamento ou armazenamento de dados.
- Modificações nas características de hardware, firmware ou software de um sistema sem o conhecimento, instruções ou consentimento prévio do dono do sistema.

### 1.4 Prevenção de Incidentes
- Atividade proativa que busca continuamente por fragilidades que possam expor a organização a riscos.
- Envolve a identificação de possíveis vulnerabilidades antes que se transformem em problemas reais.
- Exige monitoramento constante dos sistemas e implementação de controles que possam mitigar riscos potenciais.

> [!TIP] DICAS: 
> - Incidente não é apenas o ataque bem-sucedido; tentativas também são consideradas incidentes.
> - A prevenção é proativa, enquanto o tratamento é reativo (embora o tratamento também envolva prevenção futura).

## 2. CSIRT (Computer Security Incident Response Team)

### 2.1 Definição
- Acrônimo internacional para designar um Grupo de Resposta a Incidentes de Segurança.
- Organização responsável por receber, analisar e responder a notificações e atividades relacionadas a incidentes de segurança em computadores.

### 2.2 Nomenclaturas Equivalentes
- CIRC (Computer Incident Response Capability): Capacidade de Resposta a Incidentes de Computadores.
- CIRT (Computer Incident Response Team): Equipe de Resposta a Incidentes de Computadores.
- IRC (Incident Response Center or Incident Response Capability): Centro de Resposta a Incidentes ou Capacidade de Resposta a Incidentes.
- IRT (Incident Response Team): Equipe de Resposta a Incidentes.
- SERT (Security Emergency Response Team): Equipe de Resposta a Emergências de Segurança.
- SIRT (Security Incident Response Team): Equipe de Resposta a Incidentes de Segurança.

### 2.3 Atuação do CSIRT
- Todo órgão deve possuir uma equipe responsável por lidar com incidentes de segurança da informação.
- Em alguns casos, a equipe pode ter outras responsabilidades além da segurança, mas ao ocorrer um incidente, é destacada exclusivamente para tratar do problema.

### 2.4 Redução do Impacto e Sucesso
- A redução do impacto de um incidente é consequência:
  - Da agilidade de resposta.
  - Da redução no número de vítimas.
- O sucesso depende da confiabilidade:
  - Nunca divulgar dados sensíveis.
  - Não expor vítimas.

### 2.5 Limitação Importante
- O CSIRT não é investigador.
- O foco do CSIRT é entender o que aconteceu (análise técnica do incidente).
- A perícia é responsável por investigar criminalmente.
- Se identificados crimes:
  - O CSIRT atua na preservação de evidências.
  - O CSIRT auxilia investigações posteriores.
- Se o incidente resultar em crime (como em órgãos federais), a Polícia Federal deve ser acionada, essa responsabilidade cabe à equipe de tratamento de incidentes.

> [!CAUTION] OBSERVAÇÃO: 
> - O CSIRT NÃO investiga criminalmente e NÃO decide sobre o acionamento da justiça. Essa é uma pegadinha clássica em provas! Quem investiga é a perícia criminal e as autoridades competentes.
> - A confidencialidade e a proteção das vítimas são fundamentais para a confiabilidade do CSIRT.

## 3. Tipos de CSIRT

### 3.1 Classificação
- CSIRTs internos: pertencem exclusivamente a uma organização específica e atuam apenas dentro dela.
- CSIRTs nacionais: trabalham em mais de um órgão, atuando de forma mais centralizada (espécie de CSIRT central).
- Centros de coordenação: responsáveis por coordenar diversas equipes de CSIRTs internos.
- Centros de análise: especializam-se em determinado tipo de análise (ex.: análise de artefatos maliciosos).
- Grupos de empresas fornecedoras de hardware e software: atuam na prevenção e tratamento de incidentes relacionados ao hardware e software fornecidos.
- Empresas que prestam o serviço de CSIRT (terceirização).

### 3.2 Terceirização do CSIRT
- Na administração pública federal, a terceirização não é permitida, pois a segurança da informação é responsabilidade de um servidor público.
- Na iniciativa privada, é possível contratar uma empresa externa para realizar essas funções.
- Na administração pública, pode-se contratar pessoas para apoiar, mas a responsabilidade final pela segurança da informação não pode ser delegada.

> [!CAUTION] OBSERVAÇÃO: 
> - A proibição de terceirização do CSIRT na administração pública federal é um ponto específico que pode ser cobrado em provas para órgãos públicos.

## 4. Papel do CSIRT (Serviços Prestados)
- O CSIRT realiza três categorias principais de serviços: reativos, proativos e de gerenciamento da qualidade da segurança.

### 4.1 Serviços Reativos
- Alertas e avisos: resposta imediata quando ocorre um incidente.
- Tratamento de incidentes: inclui análise do incidente, resposta no local, suporte e coordenação da resposta.
- Tratamento de vulnerabilidades: identificação e correção de vulnerabilidades que permitiram o incidente.
- Tratamento de artefatos: análise e resposta a artefatos maliciosos (vírus, códigos maliciosos), incluindo coordenação das respostas.

### 4.2 Serviços Proativos
- Configuração e manutenção de ferramentas de segurança.
- Desenvolvimento de ferramentas de segurança.
- Detecção de intrusões.
- Disseminação de informações relacionadas à segurança.
- Capacitação de servidores públicos e funcionários em práticas de segurança da informação.

### 4.3 Serviços de Gerenciamento da Qualidade da Segurança
- Análises de risco.
- Gerenciamento da continuidade de negócios.
- Planos de recuperação de desastres.
- Consultoria em segurança.
- Educação e treinamento em segurança.
- Certificação e avaliação de produtos para garantir que atendam aos padrões de segurança.

| SERVIÇOS REATIVOS | SERVIÇOS PROATIVOS | GERENCIAMENTO DA QUALIDADE |
|-------------------|-------------------|---------------------------|
| Alertas e avisos | Configuração e manutenção de ferramentas | Análise de risco |
| Análise de incidentes | Desenvolvimento de ferramentas | Continuidade de negócios e recuperação de desastres |
| Resposta no local | Detecção de intrusões | Consultoria em segurança |
| Suporte e coordenação | Disseminação de informações | Educação e treinamento |
| Tratamento de vulnerabilidades | Capacitação | Certificação e avaliação |
| Tratamento de artefatos | - | - |

> [!TIP] DICAS: 
> - Os serviços reativos são acionados APÓS a ocorrência do incidente; os proativos ocorrem ANTES.
> - O tratamento de vulnerabilidades e artefatos faz parte tanto da resposta reativa quanto da prevenção futura.

## 5. Cenário Prático de Atuação do CSIRT

### 5.1 Descrição do Incidente
- Um usuário recebe um e-mail com um link malicioso e clica. Ao clicar, um malware é baixado e executado na rede. O malware se conecta a um servidor de comando e controle (C2) e a máquina infectada passa a funcionar como um "bot", participando de um ataque DDoS contra outra rede.

### 5.2 Ordem dos Eventos
1. O malware infecta o dispositivo.
2. O malware se conecta ao servidor C2.
3. O servidor C2 emite comandos para a máquina infectada atacar outras redes.

### 5.3 Ações do CSIRT e Envolvidos
- Usuário:
  - Limpeza da máquina.
  - Atualização de sistemas.
  - Capacitação (para evitar novas infecções).
- Rede:
  - Correção de problemas.
  - Remoção de arquivo malicioso.
  - Anti-spoofing.
- Desenvolvedor:
  - Desenvolvimento de sistemas mais seguros.
- Vítima do DDoS:
  - Aumento de recursos.
  - Ferramentas de mitigação.

> [!TIP] DICAS: 
> - O CSIRT atua em várias frentes: no usuário (conscientização), na rede (correção), no desenvolvimento (prevenção) e até auxiliando a vítima do ataque.
> - A ordem correta dos eventos (infecta ⟶ conecta C2 ⟶ recebe comandos ⟶ ataca) é importante para entender a dinâmica do ataque.