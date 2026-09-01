# Ansible (Conceitos, Características e Ecossistema)

## 1. Definição e Propósito

### 1.1 O que é o Ansible
- Definição: mecanismo open source de automação que ajuda a automatizar o provisionamento, o gerenciamento de configurações, a implantação de aplicações, a orquestração e muitos outros processos de TI.
- Contexto IaC: opera no paradigma de Infraestrutura como Código (IaC), sendo uma ferramenta especializada em gerenciamento de configuração.
- Linguagens Base: o motor do Ansible é escrito em Python, enquanto seus arquivos de automação (playbooks) são escritos em YAML.

### 1.2 Divisão de Responsabilidades (Terraform vs. Ansible)

#### 1.2.1 Comparativo

| ASPECTO | TERRAFORM | ANSIBLE |
|---------|-----------|---------|
| Foco | Provisionamento ("fazer nascer" a infraestrutura). | Gerenciamento de configuração ("manter" a infraestrutura estável). |
| Função | Cria a infraestrutura de base (redes, VMs, sub-redes). | Instala e configura softwares (sistemas operacionais e serviços) sobre a base já criada. |
| Paradigma | Declarativo. | Declarativo. |

#### 1.2.2 Melhores Práticas
- O uso conjunto de Terraform (provisionamento) e Ansible (configuração) é a abordagem mais comum e alinhada às boas práticas.

## 2. Funcionamento e Arquitetura

### 2.1 Modelo Agentless (Sem Agente)
- Arquitetura: o Ansible é agentless, o que significa que não requer a instalação de nenhum software agente nos servidores que serão gerenciados (alvos).
- Conexão Remota: a conexão com os alvos é feita utilizando protocolos nativos do sistema operacional:
  - Linux/Unix: conexão via SSH;
  - Windows: conexão via WinRM.
- Vantagem: reduz o overhead de gerenciamento, pois elimina a necessidade de manter e atualizar agentes distribuídos na infraestrutura.

> [!TIP] DICAS:
> - O modelo agentless é uma das principais diferenças do Ansible em relação a ferramentas como Puppet e Chef, que utilizam agentes instalados nos nós gerenciados.

### 2.2 Mecanismo de Execução (Módulos)
- Funcionamento: o Ansible conecta-se aos nós alvos (hosts) e envia pequenos programas chamados módulos.
- Características dos Módulos:
  - São desenvolvidos para representar o estado desejado de um recurso do sistema;
  - Podem ser criados novos módulos customizados;
  - São executados e removidos ao final da tarefa.

### 2.3 Modos de Operação
- Ad-hoc: execução de comandos pontuais e rápidos diretamente pela linha de comando;
- Playbooks: arquivos YAML que definem um conjunto estruturado de tarefas (tasks) a serem executadas, sendo o modo principal para automação.

## 3. Características Técnicas do Ansible

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Idioma Nativo | Linux (conexão via SSH). Gerencia também Windows (via WinRM). |
| Linguagem de Configuração | YAML (legível e fácil de interpretar) para escrever os playbooks. |
| Arquitetura | Distribuída. Não necessita de um servidor central para gerenciamento. |
| Escalabilidade | Escalável e flexível, adequado para ambientes simples e complexos. |
| Extensibilidade | Pode ser estendido por módulos e plugins. |
| Abordagem de Comunicação | Push (empurrar). O nó de controle envia as configurações para os alvos. |
| Paradigma IaC | Declarativo. Define o estado desejado da infraestrutura, não os comandos passo a passo. |

## 4. Ecossistema Ansible

| FERRAMENTA | DESCRIÇÃO |
|------------|-----------|
| Ansible (Community) | Ferramenta open source de linha de comando para automação gratuita. |
| AWX | Interface gráfica (GUI) e API REST construída sobre o Ansible para tornar o gerenciamento mais amigável. É o projeto open source que deu origem à plataforma corporativa. |
| Ansible Automation Platform | Ferramenta comercializada pela Red Hat, que inclui suporte, interface gráfica, e funcionalidades corporativas adicionais. |

> [!TIP] DICAS:
> - AWX é o projeto open source; Ansible Automation Platform é a versão comercial da Red Hat.
> - O Ansible Community é gratuito; a Ansible Automation Platform é paga.

## 5. Componentes da Arquitetura Ansible

### 5.1 Nó de Controle (Control Node)
- Máquina onde o Ansible é instalado.
- É o ponto a partir do qual a automação é orquestrada e de onde as configurações são "empurradas".

### 5.2 Nós Gerenciados (Managed Nodes / Alvos)
- Servidores ou dispositivos de rede que são o alvo da automação.
- São listados no inventário e gerenciados remotamente (sem agentes).

### 5.3 Inventário (Inventory)
- Arquivo (ou fonte dinâmica) que contém a lista de máquinas-alvo, com seus endereços IP, nomes de host e agrupamentos.
- Fica no nó de controle.

### 5.4 Módulos (Modules)
- Pequenos programas executados nos alvos para realizar uma tarefa específica (ex: instalar pacote, copiar arquivo).
- São enviados, executados e removidos.

### 5.5 Plugins
- Extensões que aumentam a funcionalidade do sistema.
- Exemplos: plugins de inventário dinâmico, filtros, callbacks.

### 5.6 Playbooks
- Arquivos YAML que definem o fluxo de trabalho da automação.
- Contêm plays e tasks.

### 5.7 Tarefas (Tasks)
- Operações individuais definidas dentro de um playbook.
- Executadas em ordem sequencial (de cima para baixo) nos managed nodes.

### 5.8 Roles
- Conjuntos reutilizáveis de tasks, variáveis, arquivos e handlers.
- Facilitam a modularização e o reuso do código.

### 5.9 Coleções (Collections)
- Pacotes de conteúdo Ansible que incluem roles, módulos, plugins e afins, distribuídos para compartilhamento e reuso.

### 5.10 CMDB
- Configuration Management Database.
- O Ansible não possui um CMDB incorporado, mas pode se integrar a ferramentas externas para armazenar o estado das máquinas.