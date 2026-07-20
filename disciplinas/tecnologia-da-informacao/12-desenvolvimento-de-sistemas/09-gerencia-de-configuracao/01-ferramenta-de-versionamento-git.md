# Anotações

# Ferramenta de Versionamento Git

## 1.1 Conceito Geral

- **Git** é uma ferramenta de **controle de versões** amplamente utilizada no desenvolvimento de software.
- Projetado para **identificar, armazenar e controlar** diferentes versões de arquivos.
- Opera de forma **descentralizada** – cada desenvolvedor possui uma cópia local do repositório.

### 1.1.1 Centralizado x Descentralizado

| SISTEMA | CARACTERÍSTICA | EXEMPLOS |
|---------|----------------|----------|
| **Centralizado** | Único repositório central; todos os desenvolvedores trabalham nele | Subversion (SVN), SourceSafe |
| **Descentralizado/Distribuído** | Cada desenvolvedor tem uma cópia local completa do repositório | **Git**, Mercurial |

> [!TIP] DICAS
> - O Git **não** gera cópias completas de cada versão – armazena as **diferenças** entre versões, economizando espaço.
> - Conceitos importantes: ***baseline*** (versão base) e ***branch*** (ramificação).

## 1.2 Git x GitLab

| FERRAMENTA | DESCRIÇÃO |
|------------|-----------|
| **Git** | Ferramenta de versionamento (controle de versões) |
| **GitLab** | Suíte completa que **inclui o Git** + funcionalidades adicionais (CI/CD, automação de *pipelines*, etc.) |

> [!CAUTION] OBSERVAÇÃO
> **Git e GitLab não são a mesma coisa.** O Git é a ferramenta de versionamento; o GitLab é uma plataforma que incorpora o Git e adiciona outras funcionalidades.

## 1.3 Comandos Básicos do Git

| COMANDO | FUNÇÃO |
|---------|--------|
| **`git clone`** | Cria uma cópia local de um repositório remoto |
| **`git add`** | Adiciona arquivos modificados ao índice de preparação (*staging area*) |
| **`git commit -m`** | Registra as alterações no repositório local (com mensagem explicativa) |
| **`git push`** | Envia as alterações do repositório local para o repositório remoto |
| **`git pull`** | Atualiza o repositório local com as mudanças do repositório remoto |

### 1.3.1 Fluxo de Trabalho Típico
1. **`git clone`** → clona o repositório remoto para o ambiente local.
2. **Modificações** → altera os arquivos localmente.
3. **`git add`** → adiciona as alterações ao *staging*.
4. **`git commit`** → registra as alterações localmente.
5. **`git pull`** → (opcional) atualiza com mudanças remotas antes de enviar.
6. **`git push`** → envia as alterações para o repositório remoto.

> [!CAUTION] OBSERVAÇÃO
> **Antes de `git pull`, verifique se há alterações locais não comitadas!** Caso contrário, podem surgir conflitos. O procedimento correto é **comitar as alterações locais** antes de realizar o `pull`.

## 1.4 Branches e Merges

| CONCEITO | DESCRIÇÃO |
|----------|-----------|
| ***Branch*** (ramificação) | Permite desenvolver partes do projeto de forma **independente** sem afetar a versão principal |
| ***Merge*** (fusão) | Integra as alterações de um *branch* ao *branch* principal |
| ***Rebase*** | Reorganiza *commits* (comando mais avançado; usar com cautela) |

### 1.4.1 Analogia
- ***Branch*** = ramos de uma árvore.
- ***Root*** = raiz (versão principal/base).

## 1.5 Git e Garantia de Qualidade de Software

- O Git é uma ferramenta essencial para o **controle de qualidade do software**.
- O versionamento de código é um dos pilares da manutenção da qualidade no desenvolvimento.
- **GQE** = Garantia de Qualidade de Software (*Software Quality Assurance*).

> [!TIP] DICAS
> - A gestão de configuração de software envolve: **versionamento**, **construção do sistema** e **controle de mudanças**.
> - Ferramentas de versionamento (Git, SVN, ClearCase, SourceSafe) estão diretamente ligadas ao **gerenciamento de configuração e mudança de software**.

## 1.6 Tabela Resumo – Comandos Git

| COMANDO | FUNÇÃO |
|---------|--------|
| `git clone` | Cópia local do repositório remoto |
| `git add` | Adiciona arquivos ao *staging* |
| `git commit -m` | Registra alterações (com mensagem) |
| `git push` | Envia para o remoto |
| `git pull` | Atualiza o local com o remoto |
| `git branch` | Gerencia ramificações |
| `git merge` | Funde *branches* |
| `git rebase` | Reorganiza *commits* |

---

# Questões de Fixação

## Questão 01
(CS/UFG/2017/UFG/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/DESENVOLVIMENTO DE SISTEMAS)

ClearCase, SourceSafe, Git e SVN são exemplos de ferramentas que automatizam atividades diretamente ligadas

a) ao gerenciamento de configuração e mudança de software.
b) à engenharia de requisitos de software.
c) à engenharia econômica de software.
d) ao gerenciamento de riscos de software.

**Gabarito:** a – Ferramentas de controle de versão estão ligadas ao **gerenciamento de configuração e mudança de software**.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | a |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Washington Henrique Almeida.*