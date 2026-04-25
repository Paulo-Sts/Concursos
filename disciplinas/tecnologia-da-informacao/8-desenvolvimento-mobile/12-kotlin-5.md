# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN V (NULL SAFETY, FUNÇÕES E LAMBDA)

## 1. Segurança Contra Nulos (Null Safety)

### 1.1 O Problema do `NullPointerException`

- **Causa:** Ocorre quando se tenta acessar um objeto que está **nulo** (aponta para vazio na memória).
- **Filosofia Kotlin:** Por padrão, os tipos em Kotlin são **não anuláveis** (*Non-Nullable*). O compilador impede a atribuição de `null` a uma variável comum.

### 1.2 Tipos Anuláveis (`?`)

- **Sintaxe:** Para permitir que uma variável receba `null`, adiciona-se **`?`** após o tipo.
    ```kotlin
    var nome: String = "Júlio"
    // nome = null // ERRO: Null can not be a value of a non-null type String

    var nomeNullable: String? = "Júlio"
    nomeNullable = null // Ok
    ```
- **Restrição:** Ao usar um tipo anulável, o acesso a métodos e atributos é bloqueado para evitar o *NullPointer*.

### 1.3 Mecanismos de Acesso Seguro

- **Chamada Segura (`?.`):** Executa o método/acesso apenas se o objeto **não for nulo**. Caso contrário, retorna `null`.
    ```kotlin
    println(nomeNullable?.length) // Se null, imprime null ao invés de quebrar
    ```
- **Operador Elvis (`?:`):** Se o valor à esquerda for `null`, retorna o valor padrão à direita.
    ```kotlin
    val tamanho = nomeNullable?.length ?: 0 // Se nome for nulo, tamanho = 0
    ```
- **Operador de Afirmação Não-Nulo (`!!`):** Converte um tipo anulável em não anulável. **Se o objeto for nulo, lança um `NullPointerException`**. Usar apenas com certeza absoluta de que o valor não é nulo.
    ```kotlin
    val tamanho = nomeNullable!!.length // Assume o risco!
    ```

## 2. Funções

### 2.1 Declaração e Parâmetros

- **Blocos de Código Reutilizáveis:** Definidos com a palavra-chave `fun`.
- **Parâmetros Obrigatórios:** Definem os dados de entrada.
    ```kotlin
    fun saudacao(nome: String, idade: Int) {
        println("Olá, $nome, você tem $idade anos.")
    }
    ```
- **Argumentos Nomeados:** Na chamada, pode-se alterar a ordem passando o nome do parâmetro explicitamente.
    ```kotlin
    saudacao(idade = 30, nome = "Ana")
    ```

### 2.2 Parâmetros Opcionais (Valor Padrão)

- Permite definir um valor *default* para o parâmetro. Se nenhum argumento for passado, o valor padrão é usado.
    ```kotlin
    fun saudacao(nome: String = "Padawan", idade: Int = -1) {
        // ...
    }
    saudacao() // Usa valores padrão
    saudacao("Júlio") // Usa "Júlio" e idade padrão
    ```

### 2.3 Funções com Retorno

- Especifica-se o tipo de retorno após os parênteses. A função retorna um valor utilizando `return`.
    ```kotlin
    fun somar(a: Int, b: Int): Int {
        return a + b
    }
    ```

## 3. Funções Lambda (Anônimas)

### 3.1 Definição

- **Conceito:** "Função Anônima". Um corpo de função que pode ser passado como expressão, sem a necessidade de declarar `fun nome()`.
- **Sintaxe:** Definida por **chaves `{}`**. Parâmetros e corpo são separados por **`->`**.

### 3.2 Exemplos

- **Lambda sem Parâmetros:**
    ```kotlin
    val mensagem = { println("Olá, Kotlin!") }
    mensagem() // Executa o bloco
    ```
- **Lambda com Parâmetros:**
    ```kotlin
    val somar = { a: Int, b: Int -> a + b }
    val resultado = somar(5, 3) // Retorna 8
    ```
- **Passagem como Argumento (High-Order Functions):** Muito usado em funções de coleções (`filter`, `map`).
    ```kotlin
    val numeros = listOf(1, 2, 3, 4)
    val pares = numeros.filter { it % 2 == 0 } // 'it' é o parâmetro implícito
    ```