# Anotações

# Ferramenta de Versionamento Git III

## 1.1 Configuração do Git

### 1.1.1 Comandos de Configuração

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git --version` | Verifica se o Git está instalado |
| `git config --global user.name "[nome]"` | Configura o nome ligado às transações de *commit* |
| `git config --global user.email "[email]"` | Configura o e-mail ligado às transações de *commit* |

**Exemplo:**
```bash
git config --global user.name "Washington Almeida"
git config --global user.email "wasjediknight@gmail.com"
```

> [!TIP] DICAS
> - O comando `git config` lê e altera a configuração do Git em **nível de repositório**, **pessoal** ou **de sistema**.
> - **Atenção:** para fazer `git commit`, é necessário configurar previamente `user.name` e `user.email`, caso contrário o Git não saberá quem fez a alteração.

## 1.2 Criando Repositórios

### 1.2.1 Comandos para Criar/Clonar Repositórios

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git init` | Cria um novo repositório local no diretório atual |
| `git init [nome-do-projeto]` | Cria um novo repositório local com um nome específico |
| `git clone [url]` | Baixa um projeto e seu histórico de versão inteiro (cópia do remoto para o local) |

### 1.2.2 O que `git init` faz?
- Cria um novo subdiretório chamado **`.git`** (pasta oculta) que contém todos os arquivos de repositório necessários para o controle de versionamento.
- O Git passa a **monitorar a pasta** em que foi iniciado.

> [!CAUTION] OBSERVAÇÃO
> - `git init` cria um repositório **local do zero**.
> - `git clone` cria uma **cópia local de um repositório remoto existente**.

## 1.3 Áreas do Git (Working Directory, Staging Area, Repository)

### 1.3.1 As Três Áreas

| ÁREA | DESCRIÇÃO |
|------|-----------|
| **Working Directory (Diretório de Trabalho)** | Onde se cria, edita e modifica os arquivos ativamente |
| **Staging Area (Index/Área Intermediária)** | Onde se preparam as alterações antes de fazer um *commit* – o usuário seleciona quais alterações incluir no próximo *commit* |
| **Repository (Repositório)** | Onde o histórico completo das alterações é armazenado; contém todos os *commits* e versões do projeto |

### 1.3.2 Fluxo das Áreas

```
Working Directory → (git add) → Staging Area → (git commit) → Repository
```

1. Trabalha-se no **Working Directory**.
2. Os arquivos são enviados para a **Staging Area** com `git add`.
3. Após o `git commit`, os arquivos vão para o **Repository**.
- É possível fazer `checkout` do projeto a partir do repositório.

### 1.3.3 Estados dos Arquivos

**Arquivos podem estar em um de dois estados:**

| ESTADO | DESCRIÇÃO |
|--------|-----------|
| **Rastreados (*Tracked*)** | Arquivos que o Git conhece e que estão no repositório |
| **Não rastreados (*Untracked*)** | Arquivos que estão no diretório de trabalho, mas não foram adicionados ao repositório |

**Ciclo de vida dos arquivos rastreados:**

```
Untracked → Staged → Modified → Unmodified
```

- **Untracked (não rastreado):** arquivo recém-criado, não adicionado ao Git.
- **Staged (preparado):** arquivo adicionado à *staging area* com `git add`.
- **Modified (modificado):** arquivo foi alterado após ter sido *committed*.
- **Unmodified (não modificado):** arquivo não sofreu alterações.

### 1.3.4 Três Possíveis Estados (para arquivos já rastreados)

| ESTADO | DESCRIÇÃO |
|--------|-----------|
| **Committed** | Dados foram salvos no repositório local |
| **Modified** | Arquivo foi modificado, mas ainda não *committed* |
| **Staged** | Arquivo marcado para ser incluído no próximo *commit* |

> [!TIP] DICAS
> - `git status` → mostra o status atual do repositório (quais arquivos foram modificados, adicionados ou não).
> - Arquivos não rastreados aparecem como **"Untracked files"**.

## 1.4 Comandos de Salvamento e Preparação

### 1.4.1 Comandos Básicos

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git add [arquivo]` | Adiciona um arquivo específico à *staging area* |
| `git add .` | Adiciona **todos** os arquivos modificados no diretório atual à *staging area* |
| `git add --all` | Adiciona **todos** os arquivos (incluindo os não rastreados) |
| `git commit` | Grava o snapshot permanentemente no histórico de versão |
| `git commit -m "[mensagem]"` | Grava o snapshot com uma mensagem descritiva |
| `git commit -a` | **Automaticamente** prepara todos os arquivos alterados e já rastreados, ignorando a *staging area* |

> [!CAUTION] OBSERVAÇÃO
> - O comando `git commit` **sem argumentos** grava permanentemente o snapshot do arquivo no histórico de versão.
> - **Não é obrigatório** informar um argumento ou opção para `git commit` – mas é **recomendado** usar `-m` para incluir uma mensagem.

## 1.5 Comandos de Desfazer e Reverter

### 1.5.1 Comparativo

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git reset [commit]` | Desfaz todos os *commits* depois de `[commit]`, preservando mudanças locais (não altera o diretório de trabalho) |
| `git reset --hard [commit]` | Descarta todo histórico e mudanças para o *commit* especificado (**cuidado!** perda permanente) |
| `git reset -- arquivos` | Remove os arquivos da *staging area* – "desfaz" o `git add` |
| `git checkout -- arquivos` | Copia arquivos da *staging area* para o diretório de trabalho – descarta alterações locais |
| `git revert [commit]` | Reverte um *commit* específico, criando um **novo commit de reversão** (mais seguro que `reset`) |

### 1.5.2 Reset x Revert

| COMANDO | EFEITO |
|---------|--------|
| **`git reset`** | **Apaga** o histórico localmente (volta para um estado anterior) |
| **`git revert`** | **Adiciona** um novo *commit* que desfaz as alterações (preserva o histórico) |

> [!CAUTION] OBSERVAÇÃO
> - **Após `git push`, `reset` não funciona mais** para desfazer remotamente – é necessário usar `git revert` para criar um novo *commit* que desfaça as alterações.
> - `git reset` **altera a referência HEAD** (modifica o ponteiro para um *commit* anterior).
> - `git revert` **não altera a referência HEAD** – apenas adiciona um novo *commit*.

## 1.6 Comandos de Visualização e Inspeção

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git status` | Lista todos os arquivos novos ou modificados a serem *commitados* |
| `git log` | Mostra os *logs* de *commit* – lista o histórico de versões para o *branch* atual |
| `git log --follow [arquivo]` | Lista o histórico de versões para um arquivo, incluindo mudanças de nome |
| `git diff` | Mostra diferenças no arquivo que **não foram realizadas** (não *staged*) |
| `git diff --staged` | Mostra a diferença entre arquivos selecionados e suas últimas versões |
| `git diff [branch1]...[branch2]` | Mostra a diferença de conteúdo entre dois *branches* |
| `git show` | Mostra um ou mais objetos (*blobs*, árvores, tags e *commits*) |
| `git show [commit]` | Retorna mudanças de *metadata* e conteúdo para o *commit* especificado |

## 1.7 Tabela Resumo – Comandos Git

| COMANDO | FUNÇÃO |
|---------|--------|
| `git config` | Configura nome, e-mail e outras opções do Git |
| `git init` | Cria repositório local |
| `git clone` | Clona repositório remoto |
| `git add` | Adiciona arquivos à *staging area* |
| `git commit` | Registra alterações no repositório local |
| `git reset` | Desfaz *commits* localmente (pode ser destrutivo) |
| `git revert` | Reverte *commit* com novo *commit* de reversão |
| `git status` | Mostra arquivos modificados/não rastreados |
| `git log` | Histórico de *commits* |
| `git diff` | Diferenças entre arquivos/versões |
| `git show` | Detalhes de um objeto/*commit* |
| `git checkout` | Muda de *branch* ou restaura arquivos |
| `git merge` | Mescla *branches* |
| `git pull` | Atualiza local com remoto |
| `git push` | Envia local para remoto |

---

# Questões de Fixação

## Questão 01
(QUADRIX/CRC-PR/ANALISTA DE INFORMÁTICA/2022)

Julgue o item, relativo ao protocolo SOAP, ao Laravel e ao Git.

No Git, o comando git config lê e altera a configuração de Git em nível de repositório, pessoal ou de sistema.

**Gabarito:** C (Correto)

## Questão 02
(FUNCERN/CÂMARA DE NATAL/RN/ASSISTENTE LEGISLATIVO/ALNS/ENGENHEIRO DA COMPUTAÇÃO/2023)

Ainda sobre o sistema de controle de versão Git, ao executar o comando git init dentro de um diretório vazio,

a) as alterações do repositório local são enviadas para o repositório remoto.
b) os novos arquivos do projeto são automaticamente adicionados ao controle de versão.
c) é criado um novo subdiretório chamado .git, que contém todos os arquivos de repositório necessários para o controle de versionamento.
d) uma cópia do repositório remoto é criada no diretório local.

**Gabarito:** c

## Questão 03
(AVANÇA SP/CÂMARA MUNICIPAL DE TABOÃO DA SERRA/SP/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/2023)

O comando utilizado para clonar um repositório no git é o comando:

a) git Pull.
b) git clone.
c) git add.
d) git status.
e) git.

**Gabarito:** b

## Questão 04
(FGV/TRT 13ª REGIÃO/TÉCNICO JUDICIÁRIO/TECNOLOGIA DA INFORMAÇÃO/2022)

O Git é um sistema de controle de versões distribuído comumente utilizado no desenvolvimento de software. O comando do Git que pode ser utilizado para baixar o código-fonte existente de um repositório remoto é

a) add.
b) checkout.
c) clone.
d) remote.
e) status.

**Gabarito:** c

## Questão 05
(UFSC/UFSC/TÉCNICO DE TECNOLOGIA DA INFORMAÇÃO/2023)

Analise as afirmativas abaixo sobre a ferramenta de versionamento Git e assinale a alternativa correta.

I) O Git trabalha com uma estrutura de árvores em três níveis: work directory, stage (ou index) e head.

**Gabarito:** C (Correto)

## Questão 06
(FGV/BANCO DO BRASIL/ANALISTA TECNOLÓGICO/2023)

GIT é uma ferramenta utilizada para fazer controles de versões de projetos e seus arquivos. Assinale a opção que apresenta os três possíveis estados em que os arquivos recém-criados ainda não foram submetidos a um snapshot.

a) commited, saved e shared.
b) commited, modified e staged.
c) consolidated, shared e logged.
d) consolidated, persisted e shared.
e) consolidated, confirmed e logged.

**Gabarito:** b

## Questão 07
(UFSC/UFSC/TÉCNICO DE TECNOLOGIA DA INFORMAÇÃO/2023)

Analise as afirmativas abaixo sobre a ferramenta de versionamento Git e assinale a alternativa correta.

IV) O comando git reset serve para desfazer alterações, sem alterar a referência head.

**Gabarito:** E (Errado) - `git reset` **altera a referência HEAD**, apontando para um *commit* anterior.

## Questão 08
(FGV/SEFAZ/MG/AUDITOR FISCAL DA RECEITA ESTADUAL/TECNOLOGIA DA INFORMAÇÃO/TARDE/2023)

O comando git que deve ser usado para descartar commits que foram feitos apenas localmente e traz o repositório local para o estado do último push do repositório remoto é o

a) git reset.
b) git revert.
c) git clean.
d) git stash.
e) git discard.

**Gabarito:** a - `git reset` retorna ao estado do último *push* (local).

## Questão 09
(QUADRIX/CRC-PR/ANALISTA DE INFORMÁTICA/2022)

Julgue o item, relativo ao protocolo SOAP, ao Laravel e ao Git.

Para que o comando git commit seja executado no Git, é imprescindível que se informe, no mínimo, um argumento ou uma opção.

**Gabarito:** E (Errado) - `git commit` **sem argumentos** grava permanentemente o snapshot do arquivo no histórico de versão.

## Questão 10
(FGV/TRT/16ª REGIÃO/ANALISTA JUDICIÁRIO/TECNOLOGIA DA INFORMAÇÃO/2022)

O comando que pode ser executado na ferramenta de versionamento Git para exibir a lista dos arquivos alterados no diretório de trabalho local é

a) git fetch.
b) git gc.
c) git status.
d) git prune.
e) git remote.

**Gabarito:** c

## Questão 11
(COVEST/COPSET/UFFE/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/ÁREA SISTEMAS/2017)

No contexto do Git, sistema de controle de versão distribuído, é correto afirmar que o comando:

a) salva alterações e impossibilita o uso do git rollback a partir daquele ponto.
b) salva alterações em um repositório local.
c) salva alterações em um repositório central.
d) salva alterações e atualiza automaticamente os repositórios de todos os usuários.
e) salva alterações em memória apenas, sem persisti-las.

**Gabarito:** b - `git commit` salva alterações no **repositório local**. `git push` que envia ao central.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | c |
| 03 | b |
| 04 | c |
| 05 | C |
| 06 | b |
| 07 | E |
| 08 | a |
| 09 | E |
| 10 | c |
| 11 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Washington Henrique Almeida.*