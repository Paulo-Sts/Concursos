# Anotações

# Prevenção de Incidentes

## 1.1 Políticas e Procedimentos de Segurança

- A primeira estratégia para prevenir incidentes é o estabelecimento de **procedimentos e políticas de segurança da informação**.
- O processo de definição de normas ocorre em **três níveis** dentro da organização:

| NÍVEL | DESCRIÇÃO | PRODUTO |
|-------|-----------|---------|
| **Estratégico** | Grandes metas e objetivos estratégicos da segurança da informação | Política de Segurança da Informação |
| **Tático** | Políticas complementares (normas), como metas para a segurança | Normas |
| **Operacional** | Procedimentos operacionais detalhados | Procedimentos |

> [!TIP] DICAS
> - Políticas bem-definidas **previnem** acidentes de segurança da informação, pois as instruções definem o processo.
> - A política de segurança está no **nível estratégico** – não tem o mesmo nível de detalhamento dos procedimentos operacionais.

## 1.2 Controle de Acesso

- **Controle de acesso** é uma forma de prevenção de incidentes de segurança da informação.
- Pode ser aplicado em diferentes níveis:
  - **Físico:** identificação biométrica para acesso a áreas restritas.
  - **Software:** *login* e senha.
  - **Dados/Informações:** bases de dados acessíveis apenas por pessoas específicas.

### 1.2.1 Princípio do Privilégio Mínimo
- Política de **privilégio mínimo** (*least privilege*): garante que os usuários tenham **apenas o acesso de que realmente precisam**.
- É a política mais utilizada para controle de acesso.
- As políticas de controle de acesso devem ser **fechadas** – somente os acessos especificamente autorizados são permitidos.

> [!CAUTION] OBSERVAÇÃO
> **Diferença com a Lei de Acesso à Informação:**
> - A **Lei de Acesso à Informação** (Lei nº 12.527/2011) tem lógica **inversa**: todo arquivo é **público**, exceto os que são definidos como **restritos**.
> - Já a política de privilégio mínimo parte do princípio de que tudo é **negado**, exceto o que é especificamente autorizado.

## 1.3 Firewall e Segurança de Rede

- **Firewall** ("parede de fogo"): evita que pacotes indesejados, com conteúdo malicioso, ultrapassem a barreira entre a rede externa (*internet*) e a rede interna.
- **Filtros de pacotes tradicionais:** são considerados *firewall* porque executam política de filtragem com base na combinação de **endereços e números de porta**, examinando cada datagrama e determinando, a partir de regras específicas, se deve passar ou ficar.

## 1.4 Softwares de Segurança

### 1.4.1 Antivírus
- Protege contra ***malwares***.
- Impede que o computador se torne um "zumbi" em uma *botnet*, mas **não impede que "zumbis" de fora ataquem a rede**.

### 1.4.2 IPS - Intrusion Prevention System (Sistema de Prevenção de Intrusões)
- Pode estar localizado entre a *internet* e o *firewall*, ou após o *firewall*.
- É **pró-ativo**: atua diretamente no elemento invasor, **não apenas emite alerta** (diferente do IDS).
- **Diferença IDS x IPS:**
  - **IDS** (*Intrusion Detection System*): apenas **detecta e aponta** o erro – não age contra invasores.
  - **IPS** (*Intrusion Prevention System*): **previne e age** ativamente contra invasores.

> [!TIP] DICAS
> - O IDS pode detectar: varreduras de porta; varreduras de pilha TCP; ataques de DoS; inundação de largura de banda; *worms* e vírus.
> - O IDS apenas detecta – quem age contra invasores é o **IPS**.

### 1.4.3 Análise de Logs
- Normalmente, trata-se de uma **análise automatizada**.
- Utilizada para identificar comportamentos anômalos nos sistemas.

### 1.4.4 Replicação e Backup de Dados
- **Backup:** cópia de segurança dos dados.
- **Replicação de dados:** solução utilizada quando há bancos de dados distribuídos. O arquivo é replicado em **três nós distintos** – se um cair, ainda há outros dois contendo os dados.

### 1.4.5 Controle de Spam
- O *spam* pode trazer arquivos maliciosos.
- Formas de controle:

| LISTA | DESCRIÇÃO |
|-------|-----------|
| **Blacklist** (lista negra) | Remetentes **não confiáveis** – entrada bloqueada |
| **Whitelist** (lista branca) | Remetentes **confiáveis** – entrada liberada (processo mais custoso) |

### 1.4.6 Honeypot ("Pote de Mel")
- Atua atraindo pacotes maliciosos que tenham conseguido passar pelo *firewall*.
- Vulnerabilidade **conhecida** incluída no sistema para **atrair invasores**.
- **Funções:**
  - Atrair atacantes e afastá-los de sistemas críticos.
  - Coletar informações sobre a atividade do atacante.
  - Incentivar o atacante a ficar no sistema por tempo suficiente para que haja resposta dos administradores.

> [!CAUTION] OBSERVAÇÃO
> **O honeypot NÃO serve APENAS para atrair atacantes – também permite a análise de suas atividades!**

## 1.5 Patches de Correção
- Utilizados para corrigir *bugs* identificados ao longo do uso do sistema.
- **Risco:** ao aplicar o *patch*, pode-se gerar um problema não mapeado (erro em outra função do sistema).
- Todo sistema de segurança deve ser **atualizado com frequência**.

## 1.6 Detecção de Incidentes

- A detecção de incidentes **NÃO se restringe** a alertas e alarmes de ferramentas automáticas.
- Pode ser feita por:
  - Ferramentas automáticas;
  - Denúncias;
  - Avaliação feita por analista de segurança.
- O incidente **NÃO precisa ser confirmado** para iniciar o protocolo de tratamento – o simples fato de observar o risco ou detectar um pretenso incidente já é motivo para agir.

> [!TIP] DICAS
> - **Triagem de incidentes:** processo de avaliação rápida dos incidentes, inclusive para confirmá-los.
> - A **mudança de políticas de segurança INFLUENCIA** a identificação da ocorrência de incidentes.

## 1.7 Tabela Resumo – Ferramentas de Prevenção

| FERRAMENTA | FUNÇÃO | CARACTERÍSTICA PRINCIPAL |
|------------|--------|--------------------------|
| **Firewall** | Barreira entre redes | Filtra pacotes com base em regras |
| **IDS** | Detecção de intrusões | Apenas detecta e alerta |
| **IPS** | Prevenção de intrusões | Atua ativamente contra invasores |
| **Antivírus** | Proteção contra *malwares* | Impede infecção local |
| **Honeypot** | Atração de invasores | Coleta informações e afasta de sistemas críticos |
| **Blacklist** | Bloqueio de remetentes | Lista de remetentes não confiáveis |
| **Whitelist** | Liberação de remetentes | Lista de remetentes confiáveis |

---

# Questões de Fixação

## Questão 01
(FGV/2021/TCE-AM/AUDITOR TÉCNICO DE CONTROLE EXTERNO/TECNOLOGIA DA INFORMAÇÃO/2ª DIA)

Em termos de prevenção e tratamento de incidentes de segurança, analise as afirmativas a seguir.

I – A política de segurança da organização deve conter os procedimentos necessários para recuperação de um incidente que paralise um processo crítico.

II – Controle de spam pode ser realizado através de listas brancas ou listas negras.

III – Honeypots servem para atrair atacantes e afastá-los de sistemas críticos, mas não permitem que as atividades desses atacantes sejam analisadas.

Está correto somente o que se afirma em:

a) I.
b) II.
c) III.
d) I e II.
e) II e III.

**Gabarito:** b

## Questão 02
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Um IDS (Intrusion Detection System) pode ser usado para detectar varreduras de porta e de pilha TCP, além de ataques de DoS, de inundação de largura de banda, de worms e de vírus.

**Gabarito:** C (Correto)

## Questão 03
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

No caso de um ataque de DoS (Denial of Service) a uma rede de computadores, seria mais indicado como resposta reconfigurar o roteador para minimizar efeitos de flooding que duplicar a configuração dos ativos envolvidos para investigação forense.

**Gabarito:** C (Correto)

## Questão 04
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Um dos princípios que norteiam o gerenciamento de privilégios administrativos é o privilégio mínimo, de acordo com o qual as políticas de controle de acesso devem ser as fechadas, ou seja, somente os acessos especificamente autorizados são permitidos.

**Gabarito:** C (Correto)

## Questão 05
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Filtros de pacotes tradicionais são considerados firewall porque podem executar uma política de filtragem com base na combinação de endereços e números de porta, examinando cada datagrama e determinando, a partir de regras específicas, se ele deve passar ou ficar.

**Gabarito:** C (Correto)

## Questão 06
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Com a implementação do whitelisting, recurso que é o contrário do blacklisting, impossibilita-se a entrada de qualquer executável que não esteja cadastrado, dada a existência de uma lista de e-mails, domínios ou endereços IP previamente aprovados e, normalmente, não submetidos aos filtros.

**Gabarito:** E (Errado) - A descrição apresentada se refere ao **blacklisting**, não ao *whitelisting*. O *whitelisting* é uma lista de remetentes confiáveis que **permite** o acesso; o *blacklisting* é que impossibilita a entrada do que não está cadastrado.

## Questão 07
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Os honeypots (potes de mel), enquanto tecnologia de detecção de intrusão, podem ser utilizados para atingir os objetivos de atrair um atacante potencial e afastá-lo de sistemas críticos e de incentivar o atacante a ficar no sistema por período de tempo suficiente para que haja resposta dos administradores, mas não para coletar informações sobre a atividade do atacante, uma vez que não foram projetados para esse fim.

**Gabarito:** E (Errado) - Os honeypots **também coletam informações** sobre a atividade do atacante.

## Questão 08
(CESPE/2018/ABIN/OFICIAL DE INTELIGÊNCIA/ÁREA 4)

Acerca de prevenção e tratamento de incidentes, julgue o item seguinte.

Situação hipotética: Um sistema apresentava falhas ao executar uma função específica X. Após a aplicação de patch do fabricante do software, o erro que causava essas falhas foi corrigido, mas outro erro na aplicação foi encontrado na função Y.

Assertiva: Nessa situação, o erro na função Y pode ter sido causado pelo patch, já que essa ferramenta é capaz de alterar diversos aspectos do software ao qual é aplicada.

**Gabarito:** C (Correto)

## Questão 09
(CESPE/2013/CPRM/ANALISTA EM GEOCIÊNCIAS/SISTEMAS)

Com referência à prevenção e ao tratamento de incidentes, julgue os itens subsecutivos.

A detecção de um incidente de segurança computacional se distingue da gerência de falhas, restringindo suas fontes aos alertas e aos alarmes de ferramentas automáticas.

**Gabarito:** E (Errado) - A detecção de incidentes não é feita somente por meio de ferramentas automáticas; pode ser feita por denúncia, avaliação de analista de segurança, etc.

## Questão 10
(CESPE/2012/TJ-RO/ANALISTA JUDICIÁRIO/ANÁLISE DE SISTEMAS/DESENVOLVIMENTO)

Assinale a opção correta acerca de prevenção e tratamento de incidentes decorrentes de ataques a redes de computadores.

a) O uso de honeypots facilita a análise de tendências de ataques a redes de computadores.
b) O uso de antivírus é uma prática efetiva de prevenção de ataques por botnets.
c) Apenas os eventos adversos à segurança que tenham sido confirmados podem ser enquadrados como incidentes de segurança de rede.
d) A mudança de políticas de segurança não influencia a identificação da ocorrência de incidentes em redes de computadores.
e) O monitoramento de eventos em uma rede de computadores depende do estabelecimento prévio de um processo de triagem de incidentes.

**Gabarito:** a

## Questão 11
(CESPE/2012/TJ-AC/ANALISTA JUDICIÁRIO/ANÁLISE DE SUPORTE)

Julgue os itens a seguir, relativos a ataques a redes de computadores, prevenção e tratamento de incidentes. Uma das formas de barrar ataques às vulnerabilidades de sistemas é aplicar rotineiramente os patches disponibilizados pelos fabricantes de software.

**Gabarito:** C (Correto)

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | b |
| 02 | C |
| 03 | C |
| 04 | C |
| 05 | C |
| 06 | E |
| 07 | E |
| 08 | C |
| 09 | E |
| 10 | a |
| 11 | C |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*