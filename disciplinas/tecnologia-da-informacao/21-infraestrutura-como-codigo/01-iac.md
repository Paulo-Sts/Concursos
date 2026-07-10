Perfeito, compreendo a sua solicitação. Realmente, para fins de revisão e clareza, a separação estrita entre a **exposição didática do conceito** e a **análise de como o conceito é cobrado** é crucial. O formato anterior, tentando consolidar tudo, pode gerar o efeito contrário e poluir o material de estudo.
# Anotações

# INFRAESTRUTURA COMO CÓDIGO (IaC) – INTRODUÇÃO E CONCEITOS

## 1. Definição e Conceitos-Chave

### 1.1 O que é IaC

- **Infraestrutura como Código (IaC)** é o gerenciamento e provisionamento da infraestrutura por meio de **códigos legíveis por máquinas** (arquivos de configuração, scripts), em vez de processos manuais e interativos.
- O objetivo é substituir a intervenção manual na configuração de servidores, redes e sistemas, passando a usar código para automatizar todo o ciclo de vida da infraestrutura.

### 1.2 Conceitos-Chave Associados

- **Automatização:** Eliminação de processos manuais repetitivos.
- **Escalabilidade:** Capacidade de provisionar e gerenciar recursos em larga escala de forma programática.
- **Consistência (Coesão):** Garantia de que a infraestrutura será provisionada de forma idêntica em todos os ambientes (desenvolvimento, teste, produção).
- **Provisionamento:** Processo de **criação e configuração inicial** da infraestrutura.
- **Gerenciamento de Configuração:** Processo de **manutenção** da infraestrutura no estado desejado após o provisionamento inicial, aplicando atualizações e correções.

## 2. Provisionamento e Gerenciamento

### 2.1 Tipos de Provisionamento

- **Servidores:** Configuração de hardware físico ou virtual, instalação de SO e aplicações.
- **Nuvem:** Criação da infraestrutura subjacente no ambiente de nuvem (redes, serviços).
- **Usuários:** Gerenciamento de identidades e concessão de permissões a serviços.
- **Redes:** Configuração de roteadores, switches, firewalls e alocação de IPs.
- **Serviços:** Configuração de serviços de TI para usuários finais.

### 2.2 Gerenciamento de Configuração

- É o processo de definir e manter a configuração desejada da infraestrutura.
- Exemplos de tarefas: corrigir erros, aplicar patches de segurança, atualizar versões de software, modificar conteúdos.
- Ferramentas populares: **Ansible**, **Puppet**, **Chef**.

## 3. Vantagens da IaC

- **Aumento da velocidade** de implantações.
- **Redução de erros** humanos.
- **Consistência** da infraestrutura (garantida pela idempotência).
- **Redução de custos** operacionais.
- **Prevenção de desvios de configuração** (*configuration drift*).

## 4. Infraestrutura Imutável vs. Mutável

### 4.1 Infraestrutura Imutável

- **Conceito:** Uma vez provisionada, a infraestrutura **não pode ser alterada**.
- **Processo de Atualização:** Para aplicar uma mudança, a versão antiga é **eliminada e substituída** por uma nova versão com a configuração desejada.
- **Vantagem:** Alta **confiabilidade e estabilidade**, pois o estado é sempre conhecido e pode ser facilmente recriado.

### 4.2 Infraestrutura Mutável

- **Conceito:** A infraestrutura **pode ser alterada** após provisionada.
- **Processo de Atualização:** As mudanças são aplicadas **diretamente no recurso existente**, modificando-o e atualizando-o.
- **Desvantagem:** A mutabilidade pode prejudicar a **consistência** e dificultar o **versionamento**.

### 4.3 Aplicação em IaC

- Muitas implantações de IaC são projetadas para serem **imutáveis**, pois este modelo garante maior confiabilidade e facilita a reversão de versões.

## 5. Abordagens de IaC: Imperativa vs. Declarativa

### 5.1 Abordagem Imperativa

- **Definição:** Define os **comandos específicos** (o "COMO") que devem ser executados passo a passo para alcançar o estado desejado.
- **Característica:** É como um script de procedimentos. Pode ser mais fácil de entender para administradores tradicionais, mas gera mais trabalho para gerenciar a escalabilidade.

### 5.2 Abordagem Declarativa

- **Definição:** Define **o estado final desejado** do sistema (o "O QUÊ"), e a ferramenta de IaC se encarrega de descobrir como alcançá-lo.
- **Característica:** Foca no resultado, não nos passos. Requer um administrador mais qualificado para gerenciá-la, mas é mais adequada para infraestruturas complexas e em larga escala.

## 6. Versionamento da Infraestrutura

- **Definição:** Aplicar sistemas de controle de versão (como Git) aos arquivos de código da infraestrutura.
- **Benefícios:**
    - Permitir a **reversão** para versões anteriores em caso de problemas.
    - Facilitar a **correção de erros** de forma controlada.
    - Manter um **histórico detalhado** de todas as mudanças.

---

# QUESTÕES DE CONCURSOS - IaC (Introdução)

## 1. Definição e Conceitos Gerais

### 1.1 (AOCP/DPE-MS/2024 - Analista)

- **Enunciado:** Gerenciamento e provisionamento de recursos por meio de arquivos de configuração e scripts, em vez de acesso direto a máquinas.
- **Gabarito:** **A) Infraestrutura como código.**
- **Análise:** A descrição corresponde à definição exata de IaC. As demais alternativas (Entrega contínua, Integração contínua, Monitoramento) são práticas de DevOps, mas não definem o processo de provisionamento de infraestrutura por código.

### 1.2 (CESPE/BACEN/2024 - Tecnologia da Informação)

- **Enunciado 1:** "No modelo de IaC, é possível a implantação de uma infraestrutura com definição de sub-redes, balanceadores de carga e máquinas virtuais com a utilização de código, sem a necessidade de configurações manuais."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** A premissa central da IaC é exatamente automatizar todas essas tarefas complexas de provisionamento de infraestrutura.

### 1.3 (CESPE/BACEN/2024 - Tecnologia da Informação)

- **Enunciado 2:** "Em IaC, o modelo controlado por API da nuvem permite que os desenvolvedores interajam com a infraestrutura de modo programático e em escala, em vez de precisarem instalar e configurar manualmente os recursos."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** A interação programática via APIs de provedores de nuvem é uma das formas de implementar IaC, permitindo escala e automação.

### 1.4 (FGV/CGU/2022 - Auditor)

- **Enunciado:** Equipe utiliza uma API em nuvem para interagir com a infraestrutura de modo programático, evitando instalação manual a cada recriação de ambiente. Qual prática DevOps foi utilizada?
- **Gabarito:** **E) Infraestrutura como código.**
- **Análise:** A descrição de interação programática com infraestrutura em escala é característica da IaC. As outras opções (Comunicação, CI, CD, Microsserviços) não se referem à automação de infraestrutura.

### 1.5 (CESPE/BNB/2022 - Especialista)

- **Enunciado:** "IaC é o processo de gerenciamento e provisionamento de data centers de computador, por meio de arquivos de definição legíveis por máquina, ao invés de configuração de hardware físico ou ferramentas de configuração interativas."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** É a definição formal de IaC, contrastando com o modelo manual e interativo.

## 2. Impacto, Benefícios e Práticas

### 2.1 (CESPE/PETROBRAS/2022 - Analista)

- **Enunciado:** "Entre os fatores que influenciam diretamente o uso da IaC estão o aumento dos custos e a diminuição na velocidade de implantação da infraestrutura."
- **Gabarito:** **ERRADO**.
- **Análise:** **Errado.** O texto inverte os benefícios. O uso de IaC é influenciado pela **diminuição dos custos** e pelo **aumento da velocidade** de implantação.

### 2.2 (CESPE/BANRISUL/2022 - Técnico)

- **Enunciado:** "A integração contínua, a entrega contínua e a infraestrutura como código estão entre as melhores práticas de DevOps."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** IaC é reconhecida como uma das práticas técnicas fundamentais do DevOps, juntamente com CI/CD.

## 3. Imutabilidade

### 3.1 (UFRJ/2023 - Analista)

- **Enunciado:** Assinalar a alternativa **INCORRETA** sobre práticas DevOps. A alternativa A descrevia Infraestrutura Imutável como estática, não suscetível a alterações, e que "cada ambiente possui sua versão com fontes de configuração diferentes".
- **Gabarito:** **A**.
- **Análise:** A banca considerou a alternativa incorreta, provavelmente pela afirmação de que "cada ambiente possui sua versão com fontes de configuração diferentes", o que contraria o ideal de padronização e consistência da IaC.
- **Nota:** As demais alternativas (B a E) são definições corretas de conteinerização, telemetria, IaC e entrega contínua, respectivamente.

## 4. Abordagens Declarativa e Imperativa

### 4.1 (CESGRANRIO/BNDES/2024 - Analista)

- **Enunciado:** Abordagem caracterizada por "definir o estado no qual se deseja o sistema, com a inclusão dos recursos necessários, as propriedades que tais recursos precisam ter e uma ferramenta específica para configurar esse estado".
- **Gabarito:** **D) Declarativa.**
- **Análise:** A definição se refere à abordagem declarativa, que foca em definir o estado final desejado.

### 4.2 (CESPE/DATAPREV/2023 - Analista)

- **Enunciado:** "A IaC declarativa especifica as propriedades dos recursos de infraestrutura que deseja provisionar e, em seguida, a ferramenta IaC descobre como alcançar esse resultado final por conta própria."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** É a descrição precisa do funcionamento da abordagem declarativa.

### 4.3 (CESPE/TBG/2023 - Analista)

- **Enunciado:** "Em infraestrutura como código, a abordagem declarativa define os comandos específicos necessários para o alcance da configuração desejada."
- **Gabarito:** **ERRADO**.
- **Análise:** **Errado.** Esta é a definição da abordagem **imperativa**. A declarativa define o estado desejado, não os comandos.

### 4.4 (CESPE/SEFIN/2023 - Analista)

- **Enunciado 1:** "A escolha de uma solução de IaC com abordagem declarativa traz como principal desvantagem a necessidade de se ter um administrador qualificado para configurar e gerenciar a solução."
- **Gabarito:** **CERTO**.
- **Análise:** **Correto.** Esta é uma desvantagem reconhecida da abordagem declarativa.

### 4.5 (CESPE/SEFIN/2023 - Analista)

- **Enunciado 2:** "O principal objetivo de se escolher automatizar a infraestrutura por meio de IaC é implantar uma infraestrutura mutável, dinâmica."
- **Gabarito:** **ERRADO**.
- **Análise:** **Errado.** O objetivo é aumentar a eficiência e reduzir a complexidade. Além disso, a IaC é preferencialmente implementada como **imutável**, sendo a mutabilidade um potencial problema para a consistência.

## 5. Aplicação de Princípios e Práticas

### 5.1 (AOCP/MGI/2024 - Especialista)

- **Enunciado 1:** Qual alternativa apresenta a aplicação correta dos princípios de IaC?
- **Gabarito:** **E) Utilizar scripts versionados para definir e provisionar a infraestrutura, permitindo que o ambiente possa ser replicado de forma consistente.**
- **Análise:**
    - **Correta:** Versionamento e replicação consistente são pilares da IaC.
    - **Incorretas:** Configuração manual (A), mudanças sem testes em produção (B), documentação manual (C) e evitar código (D) são práticas antagônicas à IaC.

### 5.2 (AOCP/MGI/2024 - Especialista)

- **Enunciado 2:** Qual alternativa é **INCORRETA** em relação à prática de IaC?
- **Gabarito:** **D) IaC é uma prática que envolve a revisão manual de todo o código antes de ser mesclado.**
- **Análise:**
    - **Incorreta:** A IaC visa automatizar processos; as revisões de código, embora importantes, não são um processo manual que define a IaC, que busca a automação.
    - **Corretas:** As demais alternativas (A, B, C, E) descrevem princípios e benefícios reais da IaC.

### 5.3 (FGV/DATAPREV/2024 - Analista)

- **Enunciado:** Opção que descreve corretamente o conceito e características de IaC.
- **Gabarito:** **A) É uma metodologia que define a automação de processos manuais de infraestrutura por meio de scripts ou arquivos de configuração, permitindo o versionamento e replicação de ambientes.**
- **Análise:** É a definição mais precisa entre as opções.
    - **Incorretas:** Centralização em datacenter físico (B), exclusividade para servidores físicos (C), ausência de scripts/arquivos (D) e terceirização completa (E) não definem IaC.

## 6. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (AOCP/2024) | **A** | Processo de gerenciamento por configuração = IaC. |
| **02** (CESPE/BACEN) | **C** | IaC implanta infra com código, sem manual. |
| **03** (CESPE/BACEN) | **C** | Interação programática via API é IaC. |
| **04** (FGV/CGU) | **E** | API programática = IaC. |
| **05** (CESPE/BNB) | **C** | Definição correta de IaC. |
| **06** (CESPE/PETROBRAS) | **E** | IaC **diminui** custo e **aumenta** velocidade. |
| **07** (CESPE/BANRISUL) | **C** | IaC é boa prática DevOps. |
| **08** (UFRJ) | **A** | A alternativa "A" é a incorreta (Infra. Imutável). |
| **09** (CESGRANRIO) | **D** | Estado desejado = Abordagem **Declarativa**. |
| **10** (CESPE/DATAPREV) | **C** | Declarativa = ferramenta descobre o "como". |
| **11** (CESPE/TBG) | **E** | Quem define comandos específicos é a **Imperativa**. |
| **12** (CESPE/SEFIN) | **C** | Desvantagem da Declarativa: requer admin qualificado. |
| **13** (CESPE/SEFIN) | **E** | IaC prefere infra **imutável**, não mutável. |
| **14** (AOCP/MGI) | **E** | IaC utiliza scripts **versionados** para replicação consistente. |
| **15** (AOCP/MGI) | **D** | IaC **não** faz revisão manual de código. |
| **16** (FGV/DATAPREV) | **A** | Definição correta: automação via scripts, versionamento, replicação padronizada. |