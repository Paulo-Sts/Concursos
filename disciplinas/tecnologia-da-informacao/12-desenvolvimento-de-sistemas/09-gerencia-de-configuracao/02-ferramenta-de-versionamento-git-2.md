# Anotações

# Ferramenta de Versionamento Git II

## 1.1 Características do Git

### 1.1.1 Distribuído
- Cada cópia de um repositório Git contém **todo o histórico de alterações**.
- Altamente resiliente a falhas e permite trabalho **offline**.
- Inicia-se um repositório local com `git init`.

### 1.1.2 Rastreamento de Alterações
- Rastreia **todas as mudanças** em arquivos e diretórios.
- Permite ver **quem fez quais alterações** e **quando**.

### 1.1.3 Branching e Merging (Ramificação e Mesclagem)
- Facilita a criação de **branches** (ramificações) para desenvolvimento paralelo.
- Permite a **fusão (merge)** dessas ramificações de volta ao ramo principal (`master` ou `main`).

### 1.1.4 Histórico de Revisões
- Linha do tempo **completa e rastreável** de todas as mudanças.
- Permite a **recuperação de versões anteriores** do código.
- **Tags** permitem reconstruir uma versão específica do software.

### 1.1.5 Velocidade e Desempenho
- Conhecido por sua **velocidade e eficiência** no gerenciamento de grandes repositórios.

### 1.1.6 Gerenciamento de Conflitos
- Ajuda a resolver conflitos entre diferentes versões de um arquivo.
- Conflitos ocorrem quando **múltiplas alterações** são feitas em um mesmo arquivo por diferentes desenvolvedores.
- Permite selecionar a versão mais apropriada para integração.

### 1.1.7 Flexibilidade
- Pode ser usado em **projetos individuais** até **grandes equipes**.
- Ideal para ambientes com muitos desenvolvedores, inclusive **remotos**.

### 1.1.8 Colaboração
- Frequentemente usado com plataformas de hospedagem: **GitHub, GitLab, Bitbucket**.
- Facilitam colaboração, CI/CD e gerenciamento de *issues*.

### 1.1.9 Rastreamento de Submódulos
- Permite incluir **repositórios externos** como submódulos.
- Útil para projetos que dependem de bibliotecas ou componentes de terceiros.

### 1.1.10 Código Aberto
- Software **open-source** com comunidade ativa de desenvolvedores.

### 1.1.11 Segurança
- Recursos de **autenticação e autorização** para proteger acesso aos repositórios.
- Garantia de **integridade dos dados**.

### 1.1.12 Versionamento de Qualquer Tipo de Arquivo
- Projetado para código-fonte, mas pode controlar versões de **qualquer tipo de arquivo** (documentos, imagens, dados).
- **Importante:** para arquivos binários (imagens, executáveis), o Git apenas armazena o binário – não permite visualizar alterações como no código-fonte.

## 1.2 Comandos Git – Referência Completa

| COMANDO | DESCRIÇÃO |
|---------|-----------|
| `git init` | Inicializa um novo repositório Git no diretório atual |
| `git clone <url>` | Clona um repositório remoto para o computador local |
| `git add <arquivo>` | Adiciona um arquivo específico ao índice (*staging area*) |
| `git add .` | Adiciona **todos** os arquivos modificados no diretório atual |
| `git commit -m "<msg>"` | Cria um *commit* com uma mensagem descritiva |
| `git status` | Mostra o status atual do repositório (arquivos modificados, adicionados ou não) |
| `git log` | Exibe o histórico de *commits* do repositório |
| `git diff` | Mostra as diferenças entre arquivos modificados e o último *commit* |
| `git branch` | Lista todas as *branches* locais ou cria uma nova (`git branch <nome>`) |
| `git checkout <branch>` | Muda para uma *branch* específica |
| `git checkout -b <nome>` | Cria e muda para uma nova *branch* |
| `git merge <branch>` | Mescla a *branch* especificada com a *branch* atual |
| `git pull` | Atualiza o repositório local com as mudanças do remoto |
| `git push` | Envia as mudanças do local para o remoto |
| `git remote add <nome> <url>` | Adiciona um repositório remoto com nome personalizado |
| `git fetch` | Baixa atualizações do remoto, **sem mesclar** automaticamente |
| `git reset <arquivo>` | Remove o arquivo da área de *staging*, mantendo as mudanças no diretório |
| `git revert <commit>` | Reverte um *commit* específico, criando um novo *commit* de reversão |
| `git stash` | Armazena mudanças temporariamente, limpando o diretório de trabalho |
| `git stash pop` | Aplica as mudanças guardadas no *stash* e as remove |
| `git tag <nome>` | Cria uma *tag* (marcação) no *commit* atual |

> [!CAUTION] OBSERVAÇÃO
> **Antes do `git commit`, é necessário executar `git add` para registrar as atualizações no índice!**

## 1.3 Erros Comuns e Boas Práticas

- **Erro:** executar comandos apenas no repositório local, esquecendo de enviar ao remoto.
- **Erro:** realizar `git pull` com alterações locais não comitadas – pode gerar conflitos.
- **Boas práticas:**
  - Sempre comitar alterações locais antes do `pull`.
  - Utilizar `git status` frequentemente para verificar o estado do repositório.
  - Usar mensagens descritivas nos *commits* (`-m "mensagem"`).

## 1.4 Git x BitKeeper – Contexto Histórico

- O Git foi criado por **Linus Torvalds em 2005**.
- Motivação: os desenvolvedores do **kernel Linux** optaram por **não utilizar mais o software proprietário BitKeeper**.
- Isso levou ao desenvolvimento do Git como alternativa **open-source**.

> [!TIP] DICAS
> - O Git **pode ser utilizado em qualquer sistema operacional** (não é exclusivo do Linux).
> - O Git **não se limita a grandes projetos** – é útil em projetos de qualquer porte.

## 1.5 Tabela Resumo – Características do Git

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **Distribuído** | Cada cópia tem o histórico completo |
| **Rastreamento** | Quem, quando e o que foi alterado |
| **Branches/Merges** | Desenvolvimento paralelo e integração |
| **Histórico** | Linha do tempo completa e recuperável |
| **Desempenho** | Rápido e eficiente |
| **Conflitos** | Ajuda na resolução controlada |
| **Flexibilidade** | Projetos individuais a grandes equipes |
| **Submódulos** | Suporte a dependências externas |
| **Segurança** | Autenticação, autorização e integridade |

---

# Questões de Fixação

## Questão 01
(INSTITUTO AOCP/2018/PRODEB/ANALISTA DE TIC I/WEB MOBILE DESIGNER)

O controle de versões pode ser considerado como uma forma correta e sistemática para realizar o gerenciamento de modificações no desenvolvimento de qualquer tipo de documento, tudo isso sendo realizado de forma eficiente, extremamente organizada e prática. Analise as seguintes informações sobre o controlador de versões Git e assinale a alternativa que aponta as corretas.

I – O Git é um software para controle de versões criado por Linus Torvalds em 2005.

II – O Git só pode ser utilizado em distribuições Linux.

III – O Git surgiu quando os desenvolvedores do kernel Linux optaram por não utilizar mais o software proprietário BitKeeper.

IV – O controlador de versões Git só deve ser utilizado em grandes projetos de desenvolvimento, pois seu uso em pequenas aplicações só acarreta um desperdício de tempo e recursos.

a) Apenas I, II e III.
b) Apenas I e III.
c) Apenas II e IV.
d) Apenas II, III e IV.
e) Apenas III e IV.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Washington Henrique Almeida.*