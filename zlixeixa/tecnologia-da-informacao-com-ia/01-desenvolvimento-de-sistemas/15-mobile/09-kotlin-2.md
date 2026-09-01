# Kotlin 2

## 1. Regras para Nomenclatura de Variáveis

### 1.1 Regras de Ouro
- Caracteres permitidos: Podem conter letras, dígitos (números) e underline (_).
- Início do nome: Devem iniciar com uma letra ou underline. Nunca podem começar com um dígito.
- Sensibilidade a maiúsculas (Case Sensitive): Há diferenciação. `variavel` e `Variavel` são identificadores distintos.
- Espaços: Não são permitidos.
- Palavras reservadas: Não podem ser usadas como nome de variável. Ex: `fun`, `val`, `var`, `if`, `else`.

> [!CAUTION] OBSERVAÇÃO: 
> - Nomes de variáveis não podem começar com números.
> - Palavras reservadas do Kotlin não podem ser usadas como identificadores.

#### 1.1.1 Exemplos Práticos
- Válidos: `nome`, `_idade`, `salarioBase`, `valor1`.
- Inválidos:
    - `1nome` (Inicia com dígito).
    - `salario base` (Contém espaço).
    - `fun` (Palavra reservada).

## 2. Tipos de Dados Primitivos

### 2.1 Números Inteiros

| TIPO | TAMANHO (BITS) | INTERVALO DE VALORES |
|---|---|---|
| Byte | 8 bits | -128 a 127 |
| Short | 16 bits | -32.768 a 32.767 |
| Int | 32 bits | -2.147.483.648 a 2.147.483.647 |
| Long | 64 bits | Grandeza elevada. O valor pode ser sufixado com L (opcional). |

### 2.2 Números de Ponto Flutuante (Decimais)

| TIPO | PRECISÃO (APÓS A VÍRGULA) | OBSERVAÇÃO OBRIGATÓRIA |
|---|---|---|
| Float | 6-7 dígitos | Obrigatório o sufixo F ou f. Ex: `3.14F` |
| Double | 15-16 dígitos | Tipo padrão para decimais. Notação científica aceita (ex: `93E5`). |

> [!CAUTION] OBSERVAÇÃO: 
> - Float exige sufixo F/f obrigatoriamente.
> - Double é o tipo padrão para números decimais.

### 2.3 Caracteres, Textos e Lógicos

| TIPO | DESCRIÇÃO | EXEMPLO |
|---|---|---|
| Char | Armazena um único caractere alfanumérico. | `val letra: Char = 'A'` (Aspas simples). |
| String | Armazena uma cadeia de caracteres (texto). | `var nome: String = "Júlio"` (Aspas duplas). |
| Boolean | Armazena um valor lógico. | `var ativo: Boolean = true` (ou `false`). |

## 3. Conversão de Tipos (Type Casting)

### 3.1 Regra Fundamental
- Kotlin NÃO faz conversão implícita de tipos numéricos. Diferente de outras linguagens, um `Int` não é automaticamente atribuído a um `Long` ou `Double`.
- Erro de prova: `val x: Int = 5; val y: Long = x` resulta em erro de compilação (Type mismatch).

> [!CAUTION] OBSERVAÇÃO: 
> - Kotlin não faz conversão implícita entre tipos numéricos.
> - É obrigatório usar funções de conversão explícita.

### 3.2 Métodos de Conversão Explícita
- Para atribuir um valor a um tipo diferente, é necessário usar as funções de conversão:
    - `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`, `toChar()`.
- Exemplo correto:
    ```kotlin
    val x: Int = 5
    val y: Long = x.toLong() // Conversão explícita
    val z: Float = x.toFloat()
    ```
- Operações aritméticas: É possível realizar operações entre tipos diferentes. O Kotlin promove o tipo para o mais abrangente na expressão (ex: `Long + Float` resulta em `Float`).

## 4. Operadores

### 4.1 Matemáticos

| OPERADOR | FUNÇÃO |
|---|---|
| `+`, `-`, `*`, `/` | Adição, Subtração, Multiplicação, Divisão. |
| `%` | Módulo (Resto da divisão). Ex: `10 % 4` resulta em `2`. |
| `++` (Incremento) | Pré-fixado (`++x`): Incrementa antes de usar o valor. Pós-fixado (`x++`): Usa o valor antes de incrementar. |
| `--` (Decremento) | Mesma lógica do incremento. |

### 4.2 Comparativos

| OPERADOR | FUNÇÃO |
|---|---|
| `==` | Igualdade. |
| `!=` | Diferença. |
| `>` | Maior que. |
| `<` | Menor que. |
| `>=` | Maior ou igual. |
| `<=` | Menor ou igual. |

### 4.3 Lógicos

| OPERADOR | FUNÇÃO | RESULTADO VERDADEIRO |
|---|---|---|
| `&&` | E (Conjunção) | Ambos precisam ser verdadeiros. |
| `\|\|` | OU (Disjunção) | Pelo menos um precisa ser verdadeiro. |
| `!` | NÃO (Negação) | Inverte o valor lógico (`!true` vira `false`). |