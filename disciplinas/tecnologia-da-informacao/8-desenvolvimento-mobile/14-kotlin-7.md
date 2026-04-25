# Anotações

# DESENVOLVIMENTO MOBILE – KOTLIN VII (CLASSES E ORIENTAÇÃO A OBJETOS)

## 1. Conceitos de Orientação a Objetos

### 1.1 Classes e Objetos

- **Classe:** É a **"planta"** ou modelo que define a estrutura e o comportamento de um objeto. Declarada com a palavra reservada **`class`**.
- **Objeto:** É a **instância** (materialização) da classe em memória.
- **Atributos:** Variáveis atreladas à classe (definem o estado do objeto).
- **Métodos:** Funções atreladas à classe (definem o comportamento do objeto).

### 1.2 Construtores

- **Construtor Primário:** Declarado no **cabeçalho da classe**. Pode receber parâmetros que já inicializam os atributos (forma concisa do Kotlin).
    ```kotlin
    // Declaração concisa: Construtor primário inicializa var/val
    class Pessoa(var nome: String, var peso: Float) {
        fun apresenta() = println("Olá, eu sou $nome e peso $peso Kg")
    }
    ```
- **Valor Padrão:** Parâmetros do construtor podem ter valores *default*.
    ```kotlin
    class Pessoa(var nome: String = "Padawan", var peso: Float)
    // Se não passar nome, assume "Padawan"
    ```

### 1.3 Data Class

- **Função:** Classes destinadas principalmente a **armazenar dados**.
- **Vantagem:** O Kotlin gera automaticamente os métodos `equals()`, `hashCode()`, `toString()` e `copy()`.

### 1.4 Modificadores de Acesso (Encapsulamento)

| MODIFICADOR | VISIBILIDADE |
| :--- | :--- |
| **`private`** | Visível **somente dentro** da classe onde foi declarado. |
| **`protected`** | Visível na **própria classe** e em suas **subclasses**. |
| **`internal`** | Visível em qualquer lugar dentro do **mesmo módulo** (conjunto de compilação). |
| **`public`** (Padrão) | Visível em **qualquer lugar**. |

### 1.5 Propriedades com Getters e Setters Customizados

- **`get()`:** Customiza a ação realizada ao **ler (acessar)** o valor da propriedade.
- **`set()`:** Customiza a ação realizada ao **atribuir (escrever)** um valor à propriedade.
    ```kotlin
    class Pessoa {
        var idade: Int = 0
            set(value) {
                // Só atribui se for maior que zero
                field = if (value > 0) value else 1
            }
    }
    ```
- **Palavra-chave `field`:** Dentro do `get()`/`set()`, refere-se ao **campo de apoio** (*backing field*) que armazena o valor real na memória, evitando recursão infinita.

## 2. Análise de Questão de Concurso (CESGRANRIO/2021)

### 2.1 Tradução Java -> Kotlin

- **Código Java Original:** Define atributos `private` (codigo, nome, numero, texto) e um construtor público que recebe código e nome.
- **Equivalência Correta em Kotlin (Padrão de Sintaxe):**
    1.  Atributos `private` dentro do corpo da classe: `private var numero = 0`.
    2.  Construtor primário com **parâmetros que não são propriedades da classe** (apenas parâmetros do construtor) ou utilizando propriedades privadas no cabeçalho.
- **Alternativa Correta (Gabarito E):**
    ```kotlin
    class AlunoKotlin (private val nome: String, private val codigo: String) {
        private var numero = 0
        private var texto = "EscolaX"
    }
    ```
    - Nota-se que `nome` e `codigo` são declarados como `private val` diretamente no construtor primário, o que é totalmente válido e substitui a declaração explícita no corpo.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESGRANRIO/2021) | **E** | Uso correto de `private val` no construtor primário e sintaxe de atributos no corpo da classe. |