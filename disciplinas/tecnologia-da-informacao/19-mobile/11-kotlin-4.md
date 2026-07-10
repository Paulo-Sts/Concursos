# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN IV (COLEÇÕES E ESTRUTURAS DE REPETIÇÃO)

## 1. Arrays

### 1.1 Definição e Criação

- **Conceito:** Coleção de elementos do **mesmo tipo** (ou seus subtipos) com **tamanho fixo**.
- **Criação com `arrayOf()`:**
    ```kotlin
    val nomes = arrayOf("Ana", "Pedro", "Maria")
    val numeros = arrayOf(1, 2, 3)
    ```
- **Acesso e Modificação:** Utiliza-se o **índice** (posição) entre colchetes.
    - Acessar: `nomes[0]` (Retorna "Ana").
    - Modificar: `nomes[0] = "João"`. (O tamanho não muda, apenas o elemento interno).
- **Adição de Elementos (`+=`):** Como o array tem tamanho fixo, o operador `+=` **cria uma cópia** do array original com o novo elemento.
- **Array de Tipos Mistos:** Se criado com tipos diferentes, o Kotlin cria um `Array<Any>`, onde `Any` é a superclasse raiz.

### 1.2 Funções Úteis em Arrays

- **Ordenação:** `sortedArray()` retorna um novo array ordenado.
- **Primeiro/Último:** `first()`, `last()`.
- **Filtro:** `filter { it > 0 }` retorna uma lista com os elementos que satisfazem a condição.
- **Busca por Índice:** `indexOf("Ana")`.
- **Busca Binária:** `binarySearch(3)` (requer array ordenado).

## 2. Estruturas de Repetição (`FOR`) e Verificação (`IN`)

### 2.1 Laço `FOR`

- **Iteração sobre Coleções:** Percorre cada elemento de uma estrutura iterável.
    ```kotlin
    for (nome in nomes) {
        println(nome)
    }
    ```
- **Iteração com Intervalo (Range):**
    ```kotlin
    for (i in 1..5) { println(i) }   // Inclui o 5
    for (i in 1 until 5) { println(i) } // Exclui o 5 (vai de 1 a 4)
    ```

### 2.2 Verificação `IN`

- **Função:** Verifica se um elemento **pertence** a uma coleção ou intervalo.
    ```kotlin
    if ("Ana" in nomes) { println("Encontrado") }
    if (5 !in 1..10) { println("Não está no intervalo") }
    ```

## 3. Hierarquia de Coleções (Collections Framework)

### 3.1 Interfaces Principais

| INTERFACE | IMUTABILIDADE | PERMITE DUPLICATAS | DESCRIÇÃO |
| :--- | :--- | :--- | :--- |
| **`List`** | **Imutável** | **Sim** | Coleção ordenada onde elementos são acessados por **índice**. |
| **`Set`** | **Imutável** | **Não** | Conjunto não ordenado de elementos **únicos**. |
| **`Map`** | **Imutável** | Chaves únicas, Valores podem repetir | Pares **Chave-Valor**. As chaves são usadas como índices exclusivos. |

### 3.2 Derivados Mutáveis

- Para cada tipo imutável, existe uma contraparte **mutável**:
    - **`MutableList`**: `mutableListOf("A", "B")`
    - **`MutableSet`**: `mutableSetOf(1, 2, 3)`
    - **`MutableMap`**: `mutableMapOf("Brasil" to "Brasília")`

> ### 3.2.1 Operações Específicas em Mapas
- **Adicionar/Atualizar:** `capitais["França"] = "Paris"` (Se a chave não existe, insere; se existe, atualiza).
- **Remover:** `capitais.remove("França")`.
- **Iteração no `for`:**
    ```kotlin
    for ((chave, valor) in capitais) {
        println("A capital de $chave é $valor")
    }
    ```
- **Busca com Padrão:** `capitais.getOrDefault("Itália", "Não encontrada")` retorna um valor padrão se a chave não existir.