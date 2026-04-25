# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN III (STRINGS E CONTROLE DE FLUXO)

## 1. Manipulação de Strings

### 1.1 Métodos e Propriedades Essenciais

- **Acesso por Índice (`[]`):** Acessa o caractere em uma posição específica (começa de `0`). Ex: `txt[0]` retorna o primeiro caractere.
- **Tamanho (`length`):** Propriedade que retorna o número de caracteres da string (espaços contam).
- **Capitalização:**
    - **`uppercase()`:** Converte todos os caracteres para maiúscula.
    - **`lowercase()`:** Converte todos os caracteres para minúscula.
- **Comparação (`compareTo()`):** Compara duas strings.
    - Retorna `0` se forem iguais.
    - Retorna um número negativo/positivo se forem diferentes (ordem lexicográfica).
- **Busca por Substring (`indexOf()`):** Retorna o **índice da primeira ocorrência** de uma substring. Se não encontrar, retorna **`-1`**.

### 1.2 Concatenação e Interpolação

- **Concatenação:** Uso do operador **`+`** para juntar duas ou mais strings.
- **Interpolação:** Inserir o valor de uma variável diretamente no texto.
    - **Sintaxe:** `"Texto $variavel"`
    - **Expressões Complexas:** `"Texto ${variavel + 1}"`

## 2. Estruturas Condicionais

### 2.1 `IF`, `ELSE IF` e `ELSE`

- Sintaxe padrão para controle de fluxo. Se houver apenas um comando, as chaves `{}` são opcionais.
- **Expressão `IF` para Atribuição:** O bloco `if...else` pode ser usado para atribuir um valor a uma variável. Nesse caso, o `else` é **obrigatório** porque a variável precisa receber um valor.
    ```kotlin
    val saudacao = if (hora < 12) "Bom dia" else if (hora < 18) "Boa tarde" else "Boa noite"
    ```

### 2.2 `WHEN` (Equivalente ao `Switch`)

- **Estrutura Condicional:** Alternativa mais limpa para múltiplos `if...else if`.
- **Uso como Comando:**
    ```kotlin
    when (permissao) {
        1 -> println("Admin")
        2 -> println("Usuário")
        else -> println("Inválido")
    }
    ```
- **Uso como Expressão (Atribuição):**
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

> ### 2.2.1 Análise da Questão TJ/RO (2021)
- **Código:** Utiliza `when` como expressão. Se `classe` for `4` ou `5`, executa um `if` aninhado: se `classe` for par, retorna `"Gold"`; se ímpar, retorna `"Iron"`.
- **Testando Valores:**
    - `classe = 3`: `when` retorna `"Econômica"`.
    - `classe = 4`: `4 % 2 == 0` (Par) -> retorna `"Gold"`.
    - `classe = 5`: `5 % 2 != 0` (Ímpar) -> retorna `"Iron"`.
- **Gabarito:** Para o par que indica valor e saída correta: **`5` / `Iron`** (Alternativa C). (Questão 5 / Iron).

## 3. Estruturas de Repetição (Loops)

### 3.1 `WHILE` e `DO...WHILE`

- **`while` (Enquanto):** Verifica a condição **antes** de executar o bloco. Se a condição for falsa no início, o bloco nunca é executado.
    ```kotlin
    while (condicao) {
        // Executa enquanto condição for true
    }
    ```
- **`do...while` (Faça...Enquanto):** Executa o bloco **pelo menos uma vez**, depois verifica a condição.
    ```kotlin
    do {
        // Executa ao menos uma vez
    } while (condicao)
    ```

### 3.2 `BREAK` e `CONTINUE`

- **`break`:** Encerra **imediatamente** o laço de repetição mais interno. A execução continua fora do laço.
- **`continue`:** Interrompe a **iteração atual** e avança para a **próxima iteração** do laço, sem sair do loop.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESGRANRIO/2021) | **A** | Constante = `val`; Inteiro 32 bits = `Int`. `val idadeMinima : Int = 18` |
| **02** (TJ/RO 2021) | **C** | `classe = 5` (ímpar) retorna `"Iron"`. |