# Resumo: Linux – Operadores e Comandos de Ajuda e Administração

## 1. Operadores no Terminal

### 1.1. `&` (E comercial)
- Executa o comando em segundo plano.
- Libera o terminal para novos comandos.

### 1.2. `>` (Maior que)
- Redireciona a saída de um comando para um arquivo.
- Cria ou sobrescreve o arquivo.
- Exemplo: `ls > arquivo.txt`

### 1.3. `>>` (Dois maiores que)
- Redireciona a saída para um arquivo, adicionando ao final.
- Não sobrescreve; acrescenta conteúdo.
- Exemplo: `echo "texto" >> arquivo.txt`

### 1.4. `|` (Pipe)
- Conecta a saída de um comando à entrada de outro.
- Exemplo: `comando1 | comando2`

### 1.5. `.` (Ponto antes do nome)
- Torna o arquivo oculto.
- Exemplo: renomear para `.arquivo.txt`

## 2. Comandos de Ajuda

### 2.1. `man comando`
- Exibe o manual completo do comando.

### 2.2. `comando --help`
- Exibe ajuda rápida do comando.

### 2.3. `info comando`
- Exibe informações detalhadas sobre o comando.

### 2.4. `whatis comando`
- Exibe uma breve definição do comando.

### 2.5. `whereis comando`
- Localiza onde o comando está instalado.

## 3. Comandos de Informações Rápidas

### 3.1. `whoami`
- Exibe o nome do usuário atual.

### 3.2. `pwd`
- Exibe o diretório atual (Print Working Directory).

### 3.3. `ls`
- Lista o conteúdo do diretório atual.

### 3.4. `free`
- Exibe informações sobre o uso da memória RAM.

## 4. Comandos de Administração

### 4.1. `su [usuário]`
- Troca para outro usuário.
- Sem parâmetro: troca para superusuário root.

### 4.2. `sudo comando`
- Executa um comando com privilégios de superusuário temporariamente.

### 4.3. `adduser`
- Adiciona um novo usuário.
- Pode também adicionar usuário a um grupo.

## 5. Observações Importantes

- O operador `>` sobrescreve o arquivo; `>>` acrescenta.
- Arquivos ocultos começam com `.` (ponto).
- `man` é mais completo que `--help`.
- `whoami` mostra apenas o usuário atual, não todos os logados.
- `pwd` é essencial para saber o diretório de trabalho atual.
- `sudo` não cria usuários; concede permissão temporária de root.