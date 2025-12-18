# Resumo: Linux – Gerenciadores de Boot e Diretórios

## 1. Gerenciadores de Boot (Bootloaders)

### 1.1. Função
- Programas responsáveis pela inicialização (boot) do sistema.
- Permitem escolher entre sistemas operacionais em dual boot.

### 1.2. Principais Gerenciadores
- **LILO** (Linux Loader): um dos mais comuns.
- **GRUB** (GRand Unified Bootloader): muito utilizado em distribuições modernas.
- **BURG**: derivado do GRUB, com interface mais elegante.

## 2. Tipos de Usuários

### 2.1. Superusuário Root
- Conta de administrador com acesso total ao sistema.
- Só existe uma conta root.
- Identificado pelo símbolo `#` no terminal.

### 2.2. Usuário Comum
- Possui restrições de acesso.
- Identificado pelo símbolo `$` no terminal.

### 2.3. Usuário do Sistema
- Criado pelo sistema para executar aplicativos específicos.

## 3. Estrutura de Diretórios do Linux

### 3.1. Diretório Raiz (`/`)
- Primeiro diretório criado no sistema de arquivos.
- Todos os outros diretórios estão dentro dele.

### 3.2. Principais Subdiretórios

#### `/bin`
- Comandos e programas essenciais para todos os usuários.
- Exemplos: `ls`, `mkdir`, `cp`.

#### `/sbin`
- Comandos de administração e gerenciamento do sistema.
- Acesso restrito ao superusuário.

#### `/boot`
- Arquivos de inicialização do sistema (ex: GRUB, LILO).
- Módulos do kernel.

#### `/dev`
- Arquivos que representam dispositivos de hardware (ex: impressoras, discos).

#### `/etc`
- Arquivos de configuração do sistema e scripts de inicialização.

#### `/home`
- Pastas pessoais dos usuários (ex: `/home/usuario`).

#### `/lib`
- Bibliotecas compartilhadas e módulos do kernel.

#### `/root`
- Pasta pessoal do superusuário root (diferente de `/home`).

#### `/tmp`
- Arquivos temporários.

#### `/var`
- Arquivos variáveis: logs, filas de e-mail, impressão, bancos de dados.

#### `/usr`
- Executáveis e bibliotecas de programas instalados.
- Subdiretórios: `/usr/bin`, `/usr/sbin`, `/usr/lib`.

#### `/media`
- Ponto de montagem para dispositivos removíveis (ex: pen drives).

#### `/mnt`
- Ponto de montagem temporário para dispositivos.

## 4. Observações Importantes

- Não é possível salvar dois arquivos ou pastas com o mesmo nome no mesmo diretório (a menos que se use case sensitive: `Arquivo.txt` ≠ `arquivo.txt`).
- O diretório `/usr` não se relaciona com usuários; é uma abreviação de "Unix System Resources".
- `/dev` refere-se a dispositivos (devices), não a desenvolvimento.
- `/var` armazena dados variáveis, como logs e filas.
- `/home` é para usuários comuns; `/root` é exclusivo do superusuário.