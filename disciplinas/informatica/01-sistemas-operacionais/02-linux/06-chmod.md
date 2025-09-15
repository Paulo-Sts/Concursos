# Resumo: Linux – Comando CHMOD

## 1. Introdução ao CHMOD

- **chmod**: comando usado para alterar as permissões de arquivos e diretórios no Linux.
- Significa "change mode".

## 2. Grupos de Usuários

As permissões são atribuídas a três grupos:

- **u** (user/dono): proprietário do arquivo.
- **g** (group): grupo ao qual o dono pertence.
- **o** (others): outros usuários que não são o dono nem do grupo.

## 3. Tipos de Permissões

- **r** (read): permissão de leitura.
- **w** (write): permissão de escrita/edição.
- **x** (execute): permissão de execução.

## 4. Exibição das Permissões

- Use `ls -l` para listar arquivos com permissões.
- Exemplo de saída:  
  `-rwxr--r-- 1 user group 123 Mar 13 exemplo.txt`
  - Primeiro caractere: `-` para arquivo, `d` para diretório.
  - Próximos 9 caracteres: permissões (3 para dono, 3 para grupo, 3 para outros).

## 5. Modo Numérico (Octal)

Cada permissão é representada por um valor:

- `r` = 4
- `w` = 2
- `x` = 1

Combinações comuns:

- `0` = --- (nenhuma permissão)
- `1` = --x (apenas execução)
- `2` = -w- (apenas escrita)
- `3` = -wx (escrita e execução)
- `4` = r-- (apenas leitura)
- `5` = r-x (leitura e execução)
- `6` = rw- (leitura e escrita)
- `7` = rwx (leitura, escrita e execução)

### Exemplos de uso:

- `chmod 755 arquivo.txt`  
  - Dono: rwx (7)  
  - Grupo: r-x (5)  
  - Outros: r-x (5)

- `chmod 644 arquivo.txt`  
  - Dono: rw- (6)  
  - Grupo: r-- (4)  
  - Outros: r-- (4)

## 6. Modo Literal (com Letras)

- `+` : adiciona permissão
- `-` : remove permissão
- `=` : define permissão exata

Exemplos:

- `chmod u+x arquivo` → adiciona execução para o dono.
- `chmod g-w arquivo` → remove escrita do grupo.
- `chmod o=r arquivo` → define outros como apenas leitura.
- `chmod a+r arquivo` → adiciona leitura para todos (a = all).

## 7. Dicas para Provas

- Permissão de execução está presente em todos os números ímpares (1, 3, 5, 7).
- Permissão de leitura está presente a partir do 4 (4, 5, 6, 7).
- `0` = nenhuma permissão.
- `7` = todas as permissões.

## 8. Comandos Relacionados

- `chown`: altera o dono do arquivo.
- `chgrp`: altera o grupo do arquivo.

## 9. Exemplo de Questão

- `chmod 754 arquivo.txt` significa:
  - Dono: rwx (7)
  - Grupo: r-x (5)
  - Outros: r-- (4)

- Incorreto: "todos os usuários podem executar o arquivo" (outros só podem ler).