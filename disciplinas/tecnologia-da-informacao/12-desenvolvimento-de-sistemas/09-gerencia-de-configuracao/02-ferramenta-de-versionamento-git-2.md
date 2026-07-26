# Ferramenta de Versionamento Git 2

## 1. Características do Git

### 1.1 Estrutura e Funcionamento

#### 1.1.1 Distribuído
- Cada cópia de um repositório Git contém todo o histórico de alterações.
- Altamente resiliente a falhas e permite trabalho offline.
- Inicia-se um repositório local com `git init`.

#### 1.1.2 Velocidade e Desempenho
- Conhecido por sua velocidade e eficiência no gerenciamento de grandes repositórios.

### 1.2 Controle e Histórico

#### 1.2.1 Rastreamento de Alterações
- Rastreia todas as mudanças em arquivos e diretórios.
- Permite ver quem fez quais alterações e quando.

#### 1.2.2 Histórico de Revisões
- Linha do tempo completa e rastreável de todas as mudanças.
- Permite a recuperação de versões anteriores do código.
- Tags permitem reconstruir uma versão específica do software.

#### 1.2.3 Gerenciamento de Conflitos
- Ajuda a resolver conflitos entre diferentes versões de um arquivo.
- Conflitos ocorrem quando múltiplas alterações são feitas em um mesmo arquivo por diferentes desenvolvedores.
- Permite selecionar a versão mais apropriada para integração.

### 1.3 Colaboração e Flexibilidade

#### 1.3.1 Branching e Merging (Ramificação e Mesclagem)
- Facilita a criação de branches (ramificações) para desenvolvimento paralelo.
- Permite a fusão (merge) dessas ramificações de volta ao ramo principal (`master` ou `main`).

#### 1.3.2 Flexibilidade
- Pode ser usado em projetos individuais até grandes equipes.
- Ideal para ambientes com muitos desenvolvedores, inclusive remotos.

#### 1.3.3 Colaboração
- Frequentemente usado com plataformas de hospedagem: GitHub, GitLab, Bitbucket.
- Facilitam colaboração, CI/CD e gerenciamento de issues.

#### 1.3.4 Rastreamento de Submódulos
- Permite incluir repositórios externos como submódulos.
- Útil para projetos que dependem de bibliotecas ou componentes de terceiros.

### 1.4 Segurança e Cobertura

#### 1.4.1 Código Aberto
- Software open-source com comunidade ativa de desenvolvedores.

#### 1.4.2 Segurança
- Recursos de autenticação e autorização para proteger acesso aos repositórios.
- Garantia de integridade dos dados.

#### 1.4.3 Versionamento de Qualquer Tipo de Arquivo
- Projetado para código-fonte, mas pode controlar versões de qualquer tipo de arquivo (documentos, imagens, dados).
- Importante: para arquivos binários (imagens, executáveis), o Git apenas armazena o binário – não permite visualizar alterações como no código-fonte.

> [!TIP] DICAS:
> - O Git pode ser utilizado em qualquer sistema operacional (não é exclusivo do Linux).
> - O Git não se limita a grandes projetos – é útil em projetos de qualquer porte.

## 2. Comandos Git

### 2.1 Comandos Essenciais (Fluxo Básico)

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git init` | Inicializa um novo repositório Git no diretório atual. |
| `git clone <url>` | Clona um repositório remoto para o computador local. |
| `git add <arquivo>` | Adiciona um arquivo específico ao índice (staging area). |
| `git add .` | Adiciona todos os arquivos modificados no diretório atual. |
| `git commit -m "<msg>"` | Cria um commit com uma mensagem descritiva. |
| `git status` | Mostra o status atual do repositório (arquivos modificados, adicionados ou não). |
| `git log` | Exibe o histórico de commits do repositório. |
| `git pull` | Atualiza o repositório local com as mudanças do remoto. |
| `git push` | Envia as mudanças do local para o remoto. |

### 2.2 Comandos Complementares

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git diff` | Mostra as diferenças entre arquivos modificados e o último commit. |
| `git branch` | Lista todas as branches locais ou cria uma nova (`git branch <nome>`). |
| `git checkout <branch>` | Muda para uma branch específica. |
| `git checkout -b <nome>` | Cria e muda para uma nova branch. |
| `git merge <branch>` | Mescla a branch especificada com a branch atual. |
| `git remote add <nome> <url>` | Adiciona um repositório remoto com nome personalizado. |
| `git fetch` | Baixa atualizações do remoto, sem mesclar automaticamente. |
| `git reset <arquivo>` | Remove o arquivo da área de staging, mantendo as mudanças no diretório. |
| `git revert <commit>` | Reverte um commit específico, criando um novo commit de reversão. |
| `git stash` | Armazena mudanças temporariamente, limpando o diretório de trabalho. |
| `git stash pop` | Aplica as mudanças guardadas no stash e as remove. |
| `git tag <nome>` | Cria uma tag (marcação) no commit atual. |

> [!CAUTION] OBSERVAÇÃO:
> - Antes do `git commit`, é necessário executar `git add` para registrar as atualizações no índice!

## 3. Erros Comuns e Boas Práticas

### 3.1 Erros Frequentes
- Executar comandos apenas no repositório local, esquecendo de enviar ao remoto (`git push`).
- Realizar `git pull` com alterações locais não comitadas – pode gerar conflitos.

### 3.2 Boas Práticas
- Sempre comitar alterações locais antes do `pull`;
- Utilizar `git status` frequentemente para verificar o estado do repositório;
- Usar mensagens descritivas nos commits (`-m "mensagem"`).

## 4. Contexto Histórico – Git x BitKeeper
- O Git foi criado por Linus Torvalds em 2005.
- Motivação: os desenvolvedores do kernel Linux optaram por não utilizar mais o software proprietário BitKeeper.
- Isso levou ao desenvolvimento do Git como alternativa open-source.

> [!TIP] DICAS:
> - O Git pode ser utilizado em qualquer sistema operacional (não é exclusivo do Linux).
> - O Git não se limita a grandes projetos – é útil em projetos de qualquer porte.

## 5. Tabela Resumo – Características do Git

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Distribuído | Cada cópia tem o histórico completo. |
| Rastreamento | Quem, quando e o que foi alterado. |
| Branches/Merges | Desenvolvimento paralelo e integração. |
| Histórico | Linha do tempo completa e recuperável. |
| Desempenho | Rápido e eficiente. |
| Conflitos | Ajuda na resolução controlada. |
| Flexibilidade | Projetos individuais a grandes equipes. |
| Submódulos | Suporte a dependências externas. |
| Segurança | Autenticação, autorização e integridade. |