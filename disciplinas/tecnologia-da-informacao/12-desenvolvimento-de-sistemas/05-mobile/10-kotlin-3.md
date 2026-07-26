# Kotlin 3

## 1. Manipulação de Strings

### 1.1 Métodos e Propriedades Essenciais
- Acesso por índice ([]): Acessa o caractere em uma posição específica (começa de 0). Ex: `txt[0]` retorna o primeiro caractere.
- Tamanho (length): Propriedade que retorna o número de caracteres da string (espaços contam).
- Capitalização:
  - `uppercase()`: Converte todos os caracteres para maiúscula.
  - `lowercase()`: Converte todos os caracteres para minúscula.
- Comparação (compareTo()): Compara duas strings.
  - Retorna `0` se forem iguais.
  - Retorna um número negativo/positivo se forem diferentes (ordem lexicográfica).
- Busca por substring (indexOf()): Retorna o índice da primeira ocorrência de uma substring. Se não encontrar, retorna `-1`.

### 1.2 Concatenação e Interpolação
- Concatenação: Uso do operador `+` para juntar duas ou mais strings.
- Interpolação: Inserir o valor de uma variável diretamente no texto.
  - Sintaxe: `"Texto $variavel"`
  - Expressões complexas: `"Texto ${variavel + 1}"`

## 2. Estruturas Condicionais

### 2.1 IF, ELSE IF e ELSE
- Sintaxe padrão para controle de fluxo. Se houver apenas um comando, as chaves `{}` são opcionais.
- Expressão IF para atribuição: O bloco `if...else` pode ser usado para atribuir um valor a uma variável. Nesse caso, o `else` é obrigatório porque a variável precisa receber um valor.
  ```kotlin
  val saudacao = if (hora < 12) "Bom dia" else if (hora < 18) "Boa tarde" else "Boa noite"
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - Quando `if...else` é usado para atribuição, o `else` é obrigatório.

### 2.2 WHEN (Equivalente ao Switch)
- Estrutura condicional: Alternativa mais limpa para múltiplos `if...else if`.
- Uso como comando:
  ```kotlin
  when (permissao) {
      1 -> println("Admin")
      2 -> println("Usuário")
      else -> println("Inválido")
  }
  ```
- Uso como expressão (atribuição):
  ```kotlin
  val resposta = when (classe) {
      1 -> "Premium"
      2 -> "Superior"
      3 -> "Econômica"
      4, 5 -> { // Bloco para múltiplos casos
          if (classe % 2 == 0) "Gold" else "Iron"
      }
      else -> "Dado inválido."
  }
  println(resposta)
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - `when` pode ser usado como comando ou como expressão (atribuição).
> - O `else` é obrigatório quando `when` é usado como expressão.

#### 2.2.1 Análise da Questão TJ/RO (2021)
- Código: Utiliza `when` como expressão. Se `classe` for `4` ou `5`, executa um `if` aninhado: se `classe` for par, retorna `"Gold"`; se ímpar, retorna `"Iron"`.
- Testando valores:
  - `classe = 3`: `when` retorna `"Econômica"`.
  - `classe = 4`: `4 % 2 == 0` (Par) ⟶ retorna `"Gold"`.
  - `classe = 5`: `5 % 2 != 0` (Ímpar) ⟶ retorna `"Iron"`.

## 3. Estruturas de Repetição (Loops)

### 3.1 WHILE e DO...WHILE
- `while` (Enquanto): Verifica a condição antes de executar o bloco. Se a condição for falsa no início, o bloco nunca é executado.
  ```kotlin
  while (condicao) {
      // Executa enquanto condição for true
  }
  ```
- `do...while` (Faça...Enquanto): Executa o bloco pelo menos uma vez, depois verifica a condição.
  ```kotlin
  do {
      // Executa ao menos uma vez
  } while (condicao)
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - `while` verifica antes de executar.
> - `do...while` executa pelo menos uma vez antes de verificar.

### 3.2 BREAK e CONTINUE
- `break`: Encerra imediatamente o laço de repetição mais interno. A execução continua fora do laço.
- `continue`: Interrompe a iteração atual e avança para a próxima iteração do laço, sem sair do loop.