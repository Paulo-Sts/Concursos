# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN VI (TRANSFORMAÇÕES E FILTROS EM COLEÇÕES)

## 1. Operações de Transformação

### 1.1 `Map` (Mapeamento)

- **Função:** Aplica uma **função lambda** a cada elemento de uma coleção e retorna uma **nova lista** com os resultados. A coleção original **não é modificada**.
- **Sintaxe:** `colecao.map { elemento -> transformação }`
- **Exemplo:**
    ```kotlin
    val valores = setOf(3, 4, 6)
    println(valores.map { it * 2 }) // Saída: [6, 8, 12]
    println(valores)                // Saída: [3, 4, 6] (original intacto)
    ```
- **Aplicação em Questão (FGV/2023):**
    ```kotlin
    val list = listOf(1, 2, 3, 5, 8)
    val result = list.map { it * 2 }.filter { it > 4 }
    // 1º: map -> [2, 4, 6, 10, 16]
    // 2º: filter (maior que 4) -> [6, 10, 16]
    println(result) // Saída: [6, 10, 16]
    ```

### 1.2 `Zip` (Emparelhamento)

- **Função:** Combina duas coleções, formando **pares** dos elementos de mesma posição. O resultado tem o tamanho da **menor coleção**.
- **Exemplo:**
    ```kotlin
    val racas = listOf("Anão", "Elfo", "Homem")
    val personagens = listOf("Gimli", "Legolas", "Aragorn")
    println(racas.zip(personagens))
    // Saída: [(Anão, Gimli), (Elfo, Legolas), (Homem, Aragorn)]
    ```

### 1.3 `Associate` (Associação -> Criação de Mapas)

- **Função:** Transforma uma coleção em um **Mapa (Map)**.
- **`associateWith`:** Os elementos originais viram as **chaves**. A função lambda define os **valores**.
    ```kotlin
    val nomes = listOf("Ana", "Pedro")
    val mapa = nomes.associateWith { "${it}@empresa.com" }
    // Resultado: {Ana=Ana@empresa.com, Pedro=Pedro@empresa.com}
    ```
- **`associateBy`:** Os elementos originais viram os **valores**. A função lambda define as **chaves**. Se chaves duplicadas, só a última permanece.
- **`associate`:** A função lambda define **ambos** (chave e valor) usando `to`.
    ```kotlin
    val nomes = listOf("James Howlett", "Bruce Wayne")
    nomes.associate { it.split(" ")[0] to it.split(" ")[1] }
    // Resultado: {James=Howlett, Bruce=Wayne}
    ```

### 1.4 `Flatten` (Achatamento)

- **Função:** Planifica uma **coleção de coleções** (aninhada) em uma única lista "achatada".
- **Exemplo:**
    ```kotlin
    val trios = listOf(setOf("A", "B"), setOf("C", "D"))
    println(trios.flatten()) // Saída: [A, B, C, D]
    ```

## 2. Filtragem de Coleções (`Filter`)

- **Função:** Retorna uma nova lista contendo apenas os elementos que **satisfazem uma condição** (predicado).
- **Predicado:** Uma função lambda que recebe o elemento e retorna **`true`** ou **`false`**.
    ```kotlin
    val numeros = listOf(1, 2, 3, 4, 5, 6)
    val pares = numeros.filter { it % 2 == 0 }
    println(pares) // Saída: [2, 4, 6]
    ```

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/2023) | **D** | `map { *2 }` gera `[2,4,6,10,16]`; `filter { >4 }` retorna `[6,10,16]`. |