# Resumo: Linux – Comandos de Arquivos e Diretórios

## 1. Comandos de Inicialização e Finalização

### 1.1. `shutdown`
- Desliga ou reinicia o sistema.
- Exemplos:
  - `shutdown -h now`: desliga imediatamente.
  - `shutdown -h +30`: desliga em 30 minutos.
  - `shutdown -r now`: reinicia imediatamente.

### 1.2. `halt` e `poweroff`
- Alternativas para desligar o sistema.
- Menos flexíveis que `shutdown`.

## 2. Comandos de Arquivos e Diretórios

### 2.1. `touch`
- Cria um arquivo vazio.
- Altera registro de data/hora de acesso/modificação.

### 2.2. `mkdir`
- Cria um novo diretório.
- Exemplo: `mkdir pasta`

### 2.3. `cat`
- Exibe o conteúdo de um arquivo no terminal.
- Também usado para concatenar arquivos.

### 2.4. `less` e `more`
- Exibem conteúdo de arquivo paginado (rolagem).
- `less` é mais avançado que `more`.

### 2.5. `cp`
- Copia arquivos ou diretórios.
- Exemplo: `cp arquivo.txt /caminho/destino/`

### 2.6. `mv`
- Move ou renomeia arquivos/diretórios.
- Exemplo:
  - `mv antigo.txt novo.txt` (renomeia)
  - `mv arquivo.txt /outra/pasta/` (move)

### 2.7. `rm`
- Remove arquivos ou diretórios.
- Exemplos:
  - `rm arquivo.txt`: remove arquivo.
  - `rm -r pasta`: remove pasta recursivamente.
  - `rm -rf /`: ⚠️ Remove TUDO (inclusive raiz) – comando perigoso.

### 2.8. `cd`
- Altera o diretório atual.
- Exemplos:
  - `cd pasta`: entra na pasta.
  - `cd ..`: volta um nível.
  - `cd ~`: vai para o diretório home.

## 3. Comandos de Rede

### 3.1. `ifconfig`
- Exibe configurações de rede (interfaces, IP, etc.).
- Equivalente ao `ipconfig` no Windows.

### 3.2. `ping`
- Testa conectividade com outro host.
- Exemplo: `ping 192.168.1.1`

## 4. Comandos de Controle e Acesso

### 4.1. `logout` / `exit`
- Encerra a sessão do terminal.

### 4.2. `passwd`
- Altera a senha do usuário.

### 4.3. `ssh`
- Conecta-se remotamente a outro computador via SSH.

## 5. Observações Importantes

- `grep` não é comando de acesso; é para filtrar texto.
- `cd ..` volta para o diretório pai.
- `rm -rf /` é extremamente perigoso e destrutivo.
- `mv` pode renomear sem mudar o local do arquivo.
- `cat`, `less`, `more` são para exibir conteúdo, não para editar.
- `touch` não compacta arquivos; isso é feito com `tar` ou `gzip`.