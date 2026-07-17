# Anotações

# ANSIBLE (CONCEITOS, CARACTERÍSTICAS E ECOSSISTEMA)

## 1. Definição e Propósito

### 1.1 O que é o Ansible

- **Definição:** Mecanismo ***open source*** de automação que ajuda a automatizar o provisionamento, o gerenciamento de configurações, a implantação de aplicações, a orquestração e muitos outros processos de TI.
- **Contexto IaC:** Opera no paradigma de Infraestrutura como Código (IaC), sendo uma ferramenta especializada em **gerenciamento de configuração**.
- **Linguagens Base:** O motor do Ansible é escrito em **Python**, enquanto seus arquivos de automação (*playbooks*) são escritos em **YAML**.

### 1.2 Divisão de Responsabilidades (Terraform vs. Ansible)

- **Terraform:** Focado no **provisionamento**, ou seja, em "fazer nascer" a infraestrutura de base (redes, VMs, sub-redes).
- **Ansible:** Focado no **gerenciamento de configuração**, ou seja, em "manter" a infraestrutura estável, instalando e configurando softwares (sistemas operacionais e serviços) sobre a base já criada.

> ### 1.2.1 Melhores Práticas
- O uso conjunto de Terraform (provisionamento) e Ansible (configuração) é a abordagem mais comum e alinhada às boas práticas.

## 2. Funcionamento e Arquitetura

### 2.1 Modelo Agentless (Sem Agente)

- **Arquitetura:** O Ansible é **agentless**, o que significa que **não requer a instalação de nenhum software agente** nos servidores que serão gerenciados (alvos).
- **Conexão Remota:** A conexão com os alvos é feita utilizando protocolos nativos do sistema operacional:
    - **Linux/Unix:** Conexão via **SSH**.
    - **Windows:** Conexão via **WinRM**.
- **Vantagem:** Reduz o *overhead* de gerenciamento, pois elimina a necessidade de manter e atualizar agentes distribuídos na infraestrutura.

### 2.2 Mecanismo de Execução (Módulos)

- **Funcionamento:** O Ansible conecta-se aos nós alvos (*hosts*) e envia pequenos programas chamados **módulos**.
- **Características dos Módulos:**
    - São desenvolvidos para representar o **estado desejado** de um recurso do sistema.
    - Podem ser criados novos módulos customizados.
    - São **executados e removidos** ao final da tarefa.

### 2.3 Modos de Operação

- **Ad-hoc:** Execução de comandos pontuais e rápidos diretamente pela linha de comando.
- ***Playbooks:*** Arquivos **YAML** que definem um conjunto estruturado de tarefas (*tasks*) a serem executadas, sendo o modo principal para automação.

## 3. Características Técnicas do Ansible

| CARACTERÍSTICA | DESCRIÇÃO |
| :--- | :--- |
| **Idioma Nativo** | Linux (conexão via SSH). Gerencia também Windows (via WinRM). |
| **Linguagem de Configuração** | **YAML** (legível e fácil de interpretar) para escrever os *playbooks*. |
| **Arquitetura** | **Distribuída**. Não necessita de um servidor central para gerenciamento. |
| **Escalabilidade** | **Escalável e flexível**, adequado para ambientes simples e complexos. |
| **Extensibilidade** | Pode ser estendido por **módulos e plugins**. |
| **Abordagem de Comunicação** | ***Push*** (empurrar). O **nó de controle** envia as configurações para os alvos. |
| **Paradigma IaC** | **Declarativo**. Define o estado desejado da infraestrutura, não os comandos passo a passo. |

## 4. Ecossistema Ansible

| FERRAMENTA | DESCRIÇÃO |
| :--- | :--- |
| **Ansible (Community)** | Ferramenta ***open source*** de linha de comando para automação **gratuita**. |
| **AWX** | Interface gráfica (**GUI**) e **API REST** construída sobre o Ansible para tornar o gerenciamento mais amigável. É o projeto *open source* que deu origem à plataforma corporativa. |
| **Ansible Automation Platform** | Ferramenta **comercializada** pela **Red Hat**, que inclui suporte, interface gráfica, e funcionalidades corporativas adicionais. |

## 5. Componentes da Arquitetura Ansible

| COMPONENTE | DEFINIÇÃO |
| :--- | :--- |
| **Nó de Controle (*Control Node*)** | Máquina onde o Ansible é instalado. É o ponto a partir do qual a automação é orquestrada e de onde as configurações são "empurradas". |
| **Nós Gerenciados (*Managed Nodes/Alvos*)** | Servidores ou dispositivos de rede que são o alvo da automação. São listados no **inventário** e gerenciados remotamente (sem agentes). |
| **Inventário (*Inventory*)** | Arquivo (ou fonte dinâmica) que contém a lista de máquinas-alvo, com seus endereços IP, nomes de host e agrupamentos. Fica no nó de controle. |
| **Módulos (*Modules*)** | Pequenos programas executados nos alvos para realizar uma tarefa específica (ex: instalar pacote, copiar arquivo). São enviados, executados e removidos. |
| **Plugins** | Extensões que aumentam a funcionalidade do sistema. Ex: plugins de inventário dinâmico, filtros, *callbacks*. |
| ***Playbooks*** | Arquivos **YAML** que definem o fluxo de trabalho da automação. Contêm *plays* e *tasks*. |
| **Tarefas (*Tasks*)** | Operações individuais definidas dentro de um *playbook*. Executadas em **ordem sequencial** (de cima para baixo) nos *managed nodes*. |
| ***Roles*** | Conjuntos reutilizáveis de *tasks*, variáveis, arquivos e *handlers*. Facilitam a modularização e o reuso do código. |
| **Coleções (*Collections*)** | Pacotes de conteúdo Ansible que incluem *roles*, módulos, plugins e afins, distribuídos para compartilhamento e reuso. |
| **CMDB** | *Configuration Management Database*. O Ansible **não possui um CMDB incorporado**, mas pode se integrar a ferramentas externas para armazenar o estado das máquinas. |

---