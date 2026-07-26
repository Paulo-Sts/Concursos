# Ferramenta de Versionamento Git 3

## 1. Configuração do Git

### 1.1 Comandos de Configuração

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git --version` | Verifica se o Git está instalado. |
| `git config --global user.name "[nome]"` | Configura o nome ligado às transações de commit. |
| `git config --global user.email "[email]"` | Configura o e-mail ligado às transações de commit. |

- Exemplo:

```bash
git config --global user.name "Washington Almeida"
git config --global user.email "wasjediknight@gmail.com"
```

> [!TIP] DICAS:
> - O comando `git config` lê e altera a configuração do Git em nível de repositório, pessoal ou de sistema.
> - Atenção: para fazer `git commit`, é necessário configurar previamente `user.name` e `user.email`, caso contrário o Git não saberá quem fez a alteração.

## 2. Criando Repositórios

### 2.1 Comandos para Criar/Clonar Repositórios

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git init` | Cria um novo repositório local no diretório atual. |
| `git init [nome-do-projeto]` | Cria um novo repositório local com um nome específico. |
| `git clone [url]` | Baixa um projeto e seu histórico de versão inteiro (cópia do remoto para o local). |

### 2.2 O que `git init` faz?
- Cria um novo subdiretório chamado `.git` (pasta oculta) que contém todos os arquivos de repositório necessários para o controle de versionamento.
- O Git passa a monitorar a pasta em que foi iniciado.

> [!CAUTION] OBSERVAÇÃO:
> - `git init` cria um repositório local do zero.
> - `git clone` cria uma cópia local de um repositório remoto existente.

## 3. Áreas do Git e Estados dos Arquivos

### 3.1 As Três Áreas

| ÁREA | DESCRIÇÃO |
|------|-----------|
| Working Directory (Diretório de Trabalho) | Onde se cria, edita e modifica os arquivos ativamente. |
| Staging Area (Index/Área Intermediária) | Onde se preparam as alterações antes de fazer um commit – o usuário seleciona quais alterações incluir no próximo commit. |
| Repository (Repositório) | Onde o histórico completo das alterações é armazenado; contém todos os commits e versões do projeto. |

### 3.2 Fluxo das Áreas
1. Trabalha-se no Working Directory;
2. Os arquivos são enviados para a Staging Area com `git add`;
3. Após o `git commit`, os arquivos vão para o Repository;
4. É possível fazer `checkout` do projeto a partir do repositório.

```
Working Directory → (git add) → Staging Area → (git commit) → Repository
```

### 3.3 Estados dos Arquivos

Arquivos podem estar em um de dois estados:

| ESTADO | DESCRIÇÃO |
|--------|-----------|
| Rastreados (Tracked) | Arquivos que o Git conhece e que estão no repositório. |
| Não rastreados (Untracked) | Arquivos que estão no diretório de trabalho, mas não foram adicionados ao repositório. |

### 3.4 Ciclo de Vida dos Arquivos Rastreados
- Untracked (não rastreado): arquivo recém-criado, não adicionado ao Git;
- Staged (preparado): arquivo adicionado à staging area com `git add`;
- Modified (modificado): arquivo foi alterado após ter sido committed;
- Unmodified (não modificado): arquivo não sofreu alterações.
- Exemplo:

```
Untracked → Staged → Modified → Unmodified
```

### 3.5 Três Possíveis Estados (para arquivos já rastreados)

| ESTADO | DESCRIÇÃO |
|--------|-----------|
| Committed | Dados foram salvos no repositório local. |
| Modified | Arquivo foi modificado, mas ainda não committed. |
| Staged | Arquivo marcado para ser incluído no próximo commit. |

> [!TIP] DICAS:
> - `git status` → mostra o status atual do repositório (quais arquivos foram modificados, adicionados ou não).
> - Arquivos não rastreados aparecem como "Untracked files".

## 4. Comandos de Salvamento e Preparação

### 4.1 Comandos Básicos

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git add [arquivo]` | Adiciona um arquivo específico à staging area. |
| `git add .` | Adiciona todos os arquivos modificados no diretório atual à staging area. |
| `git add --all` | Adiciona todos os arquivos (incluindo os não rastreados). |
| `git commit` | Grava o snapshot permanentemente no histórico de versão. |
| `git commit -m "[mensagem]"` | Grava o snapshot com uma mensagem descritiva. |
| `git commit -a` | Automaticamente prepara todos os arquivos alterados e já rastreados, ignorando a staging area. |

> [!CAUTION] OBSERVAÇÃO:
> - O comando `git commit` sem argumentos grava permanentemente o snapshot do arquivo no histórico de versão.
> - Não é obrigatório informar um argumento ou opção para `git commit` – mas é recomendado usar `-m` para incluir uma mensagem.

## 5. Comandos de Desfazer e Reverter

### 5.1 Reset x Revert – Comparativo

| COMANDO | EFEITO |
|---------|--------|
| `git reset` | Apaga o histórico localmente (volta para um estado anterior). |
| `git revert` | Adiciona um novo commit que desfaz as alterações (preserva o histórico). |

### 5.2 Comandos Detalhados

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git reset [commit]` | Desfaz todos os commits depois de `[commit]`, preservando mudanças locais (não altera o diretório de trabalho). |
| `git reset --hard [commit]` | Descarta todo histórico e mudanças para o commit especificado (cuidado! perda permanente). |
| `git reset -- arquivos` | Remove os arquivos da staging area – "desfaz" o `git add`. |
| `git checkout -- arquivos` | Copia arquivos da staging area para o diretório de trabalho – descarta alterações locais. |
| `git revert [commit]` | Reverte um commit específico, criando um novo commit de reversão (mais seguro que `reset`). |

> [!CAUTION] OBSERVAÇÃO:
> - Após `git push`, `reset` não funciona mais para desfazer remotamente – é necessário usar `git revert` para criar um novo commit que desfaça as alterações.
> - `git reset` altera a referência HEAD (modifica o ponteiro para um commit anterior).
> - `git revert` não altera a referência HEAD – apenas adiciona um novo commit.

## 6. Comandos de Visualização e Inspeção

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git status` | Lista todos os arquivos novos ou modificados a serem commitados. |
| `git log` | Mostra os logs de commit – lista o histórico de versões para o branch atual. |
| `git log --follow [arquivo]` | Lista o histórico de versões para um arquivo, incluindo mudanças de nome. |
| `git diff` | Mostra diferenças no arquivo que não foram realizadas (não staged). |
| `git diff --staged` | Mostra a diferença entre arquivos selecionados e suas últimas versões. |
| `git diff [branch1]...[branch2]` | Mostra a diferença de conteúdo entre dois branches. |
| `git show` | Mostra um ou mais objetos (blobs, árvores, tags e commits). |
| `git show [commit]` | Retorna mudanças de metadata e conteúdo para o commit especificado. |

## 7. Tabela Resumo – Comandos Git

| COMANDO | FUNÇÃO |
|---------|--------|
| `git config` | Configura nome, e-mail e outras opções do Git. |
| `git init` | Cria repositório local. |
| `git clone` | Clona repositório remoto. |
| `git add` | Adiciona arquivos à staging area. |
| `git commit` | Registra alterações no repositório local. |
| `git reset` | Desfaz commits localmente (pode ser destrutivo). |
| `git revert` | Reverte commit com novo commit de reversão. |
| `git status` | Mostra arquivos modificados/não rastreados. |
| `git log` | Histórico de commits. |
| `git diff` | Diferenças entre arquivos/versões. |
| `git show` | Detalhes de um objeto/commit. |
| `git checkout` | Muda de branch ou restaura arquivos. |
| `git merge` | Mescla branches. |
| `git pull` | Atualiza local com remoto. |
| `git push` | Envia local para remoto. |