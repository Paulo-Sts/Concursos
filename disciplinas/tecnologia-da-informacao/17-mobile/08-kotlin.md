# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN

## 1. Fundamentos da Linguagem

### 1.1 Características Principais

- **Interoperabilidade Total:** Totalmente compatível com **Java**. É possível chamar código Kotlin em Java e vice-versa.
- **Multiuso:** Usado para desenvolvimento **Android**, desenvolvimento *Web* (*server-side*), *Data Science*, entre outros.
- **Ponto de Entrada:** A execução do programa começa pela **função `main`**.
- **Extensão de Arquivo:** `.kt`

> ### 1.1.1 Função `main`
- **Declaração:** Utiliza-se a palavra reservada `fun`. Pode receber ou não argumentos (`args`).
    ```kotlin
    // Com argumento (opcional)
    fun main(args: Array<String>) {
        println("Olá, Kotlin!")
    }
    // Sem argumento
    fun main() {
        println("Olá, Kotlin!")
    }
    ```
- **Função de Corpo Único:** Se a função tem apenas uma instrução, pode-se usar o sinal de igual (`=`).
    ```kotlin
    fun main() = println("Olá, Padawan.")
    ```

### 1.2 Sintaxe Básica

- **Saída no Console:**
    - **`print()`:** Imprime sem pular linha.
    - **`println()`:** Imprime e **pula para a linha seguinte**.
- **Comentários:**
    - **Linha:** `// Comentário de linha`
    - **Bloco:** `/* Comentário de bloco (pode pular linhas) */`
- **Ponto e Vírgula (`;`):** **Opcional**. O fim da instrução é definido pela quebra de linha.
- **Concatenação:** Operador **`+`** concatena *strings* e valores numéricos (convertendo-os implicitamente para texto na impressão).

## 2. Variáveis e Constantes

### 2.1 Declaração (`var` vs `val`)

| PALAVRA-CHAVE | DEFINIÇÃO | MUTABILIDADE |
| :--- | :--- | :--- |
| **`var`** | Declara uma **Variável**. | **Mutável**. O valor pode ser alterado após a atribuição inicial. |
| **`val`** | Declara uma **Constante** (*Value*). | **Imutável**. Uma vez atribuído um valor, ele não pode ser modificado. |

- **Analogia:** `val` é como um "apelido" para um espaço de memória que não mudará (ex: `val pi = 3.14`). `var` é um apelido para um espaço que pode ser atualizado (ex: `var altura = 1.92`).

### 2.2 Tipagem (Inferência vs. Explícita)

- **Inferência de Tipo (Implícita):** O compilador Kotlin deduz o tipo automaticamente com base no valor atribuído.
    ```kotlin
    var idade = 35 // Inteiro (Int)
    val nome = "Júlio" // Texto (String)
    ```
- **Declaração Explícita:** O tipo é declarado com `:` após o nome da variável.
    ```kotlin
    var salario: Double = 1500.50
    val ativo: Boolean = true
    ```

> ### 2.2.1 Regra Importante para Provas
- Se uma variável **não é inicializada** no momento da declaração, a declaração do **tipo é obrigatória**. Caso contrário, o compilador não saberá qual tipo alocar e retornará um erro.
    ```kotlin
    var nome: String // Correto: Tipo definido. Pode ser inicializado depois.
    nome = "Ana"

    var nome // ERRO: 'This variable must either have a type annotation or be initialized'
    ```