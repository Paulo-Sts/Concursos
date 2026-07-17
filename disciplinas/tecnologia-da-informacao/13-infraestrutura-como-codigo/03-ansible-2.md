# QUESTÕES DE CONCURSOS - ANSIBLE

## 1. Linguagem e Funcionalidades

### 1.1 (FGV/DNIT/2024 - Analista Administrativo)

- **Enunciado:** "Os ansible playbooks são usados para orquestrar processos de TI e são descritos em linguagem..."
- **Gabarito:** **C) YAML.**
- **Análise:** Apesar de o Ansible ser escrito em Python, a linguagem de descrição das tarefas de automação é YAML. As demais (AWK, PERL, BASH) são linguagens de script, mas não são a linguagem dos playbooks.

### 1.2 (INSTITUTO VERBENA/TJ AC/2024 - Analista)

- **Enunciado:** As principais funcionalidades da plataforma Ansible AWX.
- **Gabarito:** **A) automação de processos de implantação e configuração de servidores e aplicativos.**
- **Análise:** O Ansible e, por consequência, o AWX, são focados em automação de infraestrutura (gerenciamento de configuração e implantação). Não são ferramentas primárias de segurança de rede, análise de dados ou segurança em nuvem.

### 1.3 (AVANÇA SP/UNITAU/2025 - Analista de Sistema Sênior)

- **Enunciado:** "Qual das seguintes ferramentas é especializada em automação de infraestrutura como código (IaC)?" com opções contendo **b) Ansible** e **e) Terraform**.
- **Gabarito:** **E) Terraform.** (Considerado o gabarito único pela banca, embora Ansible também seja).
- **Análise:** Esta é uma questão clássica. Ambas são ferramentas de IaC, mas Terraform se especializa em provisionamento e Ansible em gerenciamento de configuração. Neste caso, o gabarito foi Terraform, mas é importante saber que as duas atuam em IaC, frequentemente em conjunto.

## 2. Arquitetura Agentless (Sem Agente)

### 2.1 (QUADRIX/CFO/2025 - Analista de Infraestrutura)

- **Enunciado:** "Ansible utiliza uma arquitetura sem agentes, facilitando a automação de datacenters com menos overhead de gerenciamento."
- **Gabarito:** **CERTO.**
- **Análise:** Esta é uma das principais vantagens e características distintivas do Ansible. A ausência de agentes elimina a sobrecarga de manutenção de softwares adicionais nas máquinas alvo.

### 2.2 (CESPE-CEBRASPE/CAU/2024 - Analista de Infraestrutura)

- **Enunciado:** "O Ansible é uma ferramenta de gerenciamento de configuração que requer um agente instalado nos nós gerenciados, enquanto o Puppet e o Chef não requerem um agente em cada nó."
- **Gabarito:** **ERRADO.**
- **Análise:** A afirmação está totalmente invertida. O Ansible é **agentless** (não requer agente). Puppet e Chef utilizam tradicionalmente uma arquitetura baseada em **agentes**. O texto apresentado troca as características.

### 2.3 (CESPE-CEBRASPE/DATAPREV/2023 - Analista)

- **Enunciado:** "O Ansible é uma solução de software que permite controlar um dispositivo, através de agentes nele instalados [...] sendo que a comunicação [...] ocorre por meio dos referidos agentes."
- **Gabarito:** **ERRADO.**
- **Análise:** Reforça o erro anterior. O Ansible não utiliza agentes. A comunicação é feita por SSH (Linux) ou WinRM (Windows).

## 3. Linguagem de Desenvolvimento e Configuração

### 3.1 (CESPE-CEBRASPE/CNJ/2024 - Analista Judiciário)

- **Enunciado:** "Ansible é uma ferramenta escrita em Java e que usa JSON para descrever o estado desejado dos dispositivos e da configuração."
- **Gabarito:** **ERRADO.**
- **Análise:** O item contém dois erros fundamentais:
    1.  **Linguagem:** O motor do Ansible é escrito em **Python**, não em Java.
    2.  **Formato de descrição:** O estado desejado é descrito em arquivos de configuração chamados ***playbooks***, que são escritos em **YAML**, e não em JSON. Essa é uma pegadinha clássica de prova.

## 4. Idempotência, Conexão e Melhores Práticas

### 4.1 (CESPE/CEBRASPE/TSE/UNIF/2024 - Analista Judiciário)

- **Enunciado:** "Para a sua automatização no Windows, o Ansible se conecta a nós de controle, e o usuário executa comandos [...] projetados para serem idempotentes quanto possível."
- **Gabarito:** **ERRADO.**
- **Análise:** O principal erro é afirmar que o Ansible "se conecta a nós de controle". O correto é:
    - O **nó de controle** é a máquina onde o Ansible está instalado e de onde os comandos partem.
    - O Ansible se conecta **aos nós gerenciados (alvos)**, ou seja, aos servidores que serão configurados. A inversão do fluxo de conexão torna o item errado.

### 4.2 (FGV/CVM/2024 - Analista de Infraestrutura e Segurança)

- **Enunciado:** Melhor prática no Ansible para garantir idempotência e reutilização em diferentes ambientes de nuvem.
- **Gabarito:** **E) empregar roles e variáveis para modularizar os playbooks, facilitando a reutilização e a customização em diferentes ambientes.**
- **Análise:**
    - **Correta:** *Roles* e variáveis são a forma padrão e recomendada para criar código modular, reutilizável e idempotente.
    - **Incorretas:** O uso de `shell`/`scripts` quebra a idempotência (A). *Hardcoding* de senhas (B) é péssima prática de segurança. Evitar variáveis e usar valores fixos (C) impede o reaproveitamento. Usar módulos específicos de um provedor (D) prende a automação ao vendor, quando o objetivo é ser multi-cloud.

## 5. Integração com CI/CD e IaC

### 5.1 (QUADRIX/CFO/2025 - Analista de Infraestrutura)

- **Enunciado 1:** "A integração com ferramentas de CI/CD [...] permite que Ansible e Puppet sejam utilizados para automatizar o deployment contínuo de aplicações em datacenters."
- **Gabarito:** **CERTO.**
- **Análise:** A integração de ferramentas de IaC (Ansible, Puppet) com pipelines de CI/CD é uma das práticas fundamentais de DevOps para o *deployment* automatizado e contínuo.

### 5.2 (QUADRIX/CFO/2025 - Analista de Infraestrutura)

- **Enunciado 2:** "Ferramentas como Ansible e Puppet permitem a gestão de infraestrutura como código (IaC), proporcionando um maior controle sobre a configuração e a consistência de ambientes."
- **Gabarito:** **CERTO.**
- **Análise:** É a definição precisa da função das ferramentas de gerenciamento de configuração no contexto de IaC: garantir consistência e controle da infraestrutura.

## 6. Funcionalidades e Componentes Específicos

### 6.1 (OBJETIVA/PREF. LAPA/2025 - Operador de Computador)

- **Enunciado:** Termo utilizado para descrever os documentos Ansible que definem as tarefas.
- **Gabarito:** **B) Playbooks.**
- **Análise:** Os *Playbooks* são os documentos mestres que orquestram as tarefas. *Inbooks, Outbooks, Newbooks* e *Taskbooks* não são termos existentes no contexto do Ansible.

### 6.2 (FGV/STN/2024 - Auditor Federal)

- **Enunciado:** Sobre a distribuição comunitária do Ansible, é correto afirmar que:
- **Gabarito:** **C) os modules podem ser escritos em qualquer linguagem que retorne JSON, como Ruby, Python ou bash.**
- **Análise:**
    - **Correta:** Esta é uma característica flexível dos módulos do Ansible.
    - **Incorretas:**
        - A) Uma *task* é uma ação dentro de um *playbook*, não um arquivo YAML com *plays*.
        - B) As *tasks* em uma *play* são executadas em **ordem sequencial** (de cima para baixo).
        - D) O ***inventory*** é a lista de máquinas-alvo, não uma coleção de módulos.
        - E) O Ansible é ***agentless***, não requer instalação de agentes.

### 6.3 (CESPE-CEBRASPE/TRT 10/2025 - Analista Judiciário)

- **Enunciado:** Um playbook que usa o módulo `ansible.builtin.group_by` irá classificar hosts por sistema operacional, e um host com Ubuntu será adicionado ao grupo `os_Ubuntu`.
- **Gabarito:** **CERTO.**
- **Análise:** O módulo `group_by` cria grupos dinâmicos no inventário. A chave `os_{{ ansible_facts['distribution'] }}` irá avaliar a variável `ansible_facts['distribution']` (que coleta o nome da distribuição) e criar grupos como `os_Ubuntu`, `os_CentOS`, etc., dinamicamente.

## 7. Propósito Geral das Ferramentas de Ger. de Configuração

### 7.1 (FGV/DATAPREV/2024 - Analista)

- **Enunciado:** Opção que descreve corretamente o uso de uma ferramenta de gerenciamento de configuração.
- **Gabarito:** **C) Ferramentas como Ansible, Puppet e Chef permitem automatizar a configuração de servidores, aplicando regras consistentes em várias máquinas.**
- **Análise:** É a definição central do propósito dessas ferramentas.
    - **Incorretas:** Elas não são focadas primariamente em backup (A). Não ignoram arquivos de configuração (B). Funcionam em qualquer ambiente, não só nuvem (D). Permitem scripts personalizados, sim (E).

## 8. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/DNIT/2024) | **C** | *Playbooks* são descritos em **YAML**. |
| **02** (INST. VERBENA/2024) | **A** | AWX/Ansible = automação de implantação e configuração. |
| **03** (AVANÇA SP/2025) | **E** | Terraform é IaC; Ansible também, mas o gabarito oficial foi Terraform. |
| **04** (QUADRIX/2025) | **C** | Ansible é **agentless** (sem agente). |
| **05** (CESPE/CAU/2024) | **E** | Ansible é **agentless**. Puppet e Chef usam agentes (padrão). |
| **06** (CESPE/DATAPREV/2023) | **E** | Ansible **não** utiliza agentes. Comunicação é via SSH/WinRM. |
| **07** (CESPE/CNJ/2024) | **E** | Ansible é escrito em **Python** e usa **YAML** (playbooks). |
| **08** (CESPE/TSE/2024) | **E** | Ansible conecta-se **aos alvos**, não a nós de controle. |
| **09** (FGV/CVM/2024) | **E** | Melhor prática: Empregar **roles e variáveis** para modularizar. |
| **10** (QUADRIX/2025) | **C** | Ansible e Puppet podem ser usados com CI/CD para *deployment*. |
| **11** (QUADRIX/2025) | **C** | Ansible e Puppet = gestão de IaC, controle e consistência. |
| **12** (OBJETIVA/2025) | **B** | Documentos de definição de tarefas = ***Playbooks***. |
| **13** (FGV/STN/2024) | **C** | Módulos podem ser escritos em qualquer linguagem que retorne **JSON**. |
| **14** (CESPE/TRT 10/2025) | **C** | `group_by` cria grupos dinâmicos, como `os_Ubuntu`. |
| **15** (FGV/DATAPREV/2024) | **C** | Ferramentas de ger. de configuração automatizam com consistência. |