# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – iOS (SWIFT)

## 1. Fundamentos do Desenvolvimento iOS

### 1.1 Plataforma e Ambiente

- **Linguagens Nativas:** **Objective-C** e **Swift**.
- **Exclusividade:** O iOS é **exclusivo** para hardware Apple (iPhone, iPad). Código Swift não roda nativamente em Android.
- **Ambiente de Desenvolvimento (IDE):** **Xcode** (exclusivo para macOS).
    - **Source Editor:** Editor de código.
    - **Interface Builder:** Construtor visual de interfaces.
    - **Simulador:** Emulador de dispositivos iOS.
    - **Debugger:** Ferramenta de depuração.

### 1.2 Primeiros Passos com Swift

- **Saída no Console:** `print("Texto")`
- **Variáveis e Constantes:**
    - **`var`:** Declara uma **variável** (mutável).
    - **`let`:** Declara uma **constante** (imutável). Após definida, seu valor não pode ser alterado.
- **Tipagem:**
    - **Implícita (Inferência de Tipo):** O tipo é definido automaticamente na primeira atribuição. O Swift é fortemente tipado, portanto, uma vez definido o tipo, a variável não aceitará outros tipos.
        ```swift
        var numero = 42 // Int
        let nome = "Ana" // String
        ```
    - **Explícita:** O tipo pode ser declarado com dois pontos (`:`) após o nome.
        ```swift
        var idade: Int = 25
        let altura: Double = 1.75
        var ativo: Bool
        ativo = true
        ```

## 2. Manipulação de Dados e Estruturas de Controle

### 2.1 Strings

- **Interpolação:** `"Texto \(variavel)"`
- **Concatenação:** Uso direto do operador `+`.
- **Múltiplas Linhas:** Uso de **aspas triplas** (`"""`).

### 2.2 Coleções e Estruturas de Repetição

- **`For...in...`:** Percorre cada elemento de uma sequência (ex: Array).
    ```swift
    let nomes = ["Ana", "Júlio"]
    for nome in nomes {
        print(nome)
    }
    ```
- **`While`:** Repete um bloco **enquanto** a condição for verdadeira. A verificação ocorre **antes** da execução do bloco.
- **`Repeat...While`:** Repete um bloco **até** que a condição seja falsa. A verificação ocorre **depois** da execução do bloco (garante ao menos uma execução).

### 2.3 Estruturas de Controle de Fluxo

- **`IF`:** Estrutura condicional tradicional.
- **`SWITCH`:** Seleciona um valor e executa o bloco correspondente ao `case`. Suporta intervalos com `...` (ex: `case 2...4:`). Não há *fallthrough* implícito (não precisa de `break` obrigatório).

## 3. Funções, Estruturas e Classes

### 3.1 Funções (`func`)

- **Declaração:**
    ```swift
    func saudacao(nome: String, idade: Int) {
        print("\(nome) tem \(idade) anos.")
    }
    // Chamada: saudacao(nome: "Ana", idade: 25)
    ```
- **Parâmetros e Retorno:** Na chamada, o **rótulo do parâmetro** é obrigatório (a menos que se use `_`).
    ```swift
    func somar(a: Int, b: Int) -> Int {
        return a + b
    }
    // Chamada: somar(a: 5, b: 3)
    ```

### 3.2 Struct vs. Class (Valor vs. Referência)

- **`struct` (Estrutura):** **Value Type**. Ao atribuir a outra variável, é feita uma **cópia** do valor. São instâncias independentes.
- **`class` (Classe):** **Reference Type**. Ao atribuir a outra variável, ambas **apontam para a mesma instância** na memória.
    - **Herança:** Utiliza-se `:` para herdar de uma superclasse.
    - **Sobrescrita:** Utiliza-se `override func nomeFuncao()` para modificar o comportamento herdado.

> ### 3.2.1 Observação sobre Construtores
- Em `class`, é necessário definir explicitamente um **construtor** (`init`) para inicializar as propriedades da instância, a menos que elas tenham valores padrão.

### 3.3 Protocolos

- **Definição:** Um **Protocolo** é um modelo que define um conjunto de métodos e propriedades que uma classe ou `struct` deve implementar. Equivale a uma **Interface** em outras linguagens (como Java).
- **Conformidade:** Uma `struct` ou `class` **adota** o protocolo (diz-se que está "em conformidade").
- **Exemplo (`Equatable`):** Protocolo que permite comparar duas instâncias para verificar se são iguais (`==`). Para conformar, deve-se implementar o operador `==`.