# Kotlin 7

## 1. Conceitos de Orientação a Objetos

### 1.1 Classes e Objetos
- Classe: É a "planta" ou modelo que define a estrutura e o comportamento de um objeto. Declarada com a palavra reservada `class`.
- Objeto: É a instância (materialização) da classe em memória.
- Atributos: Variáveis atreladas à classe (definem o estado do objeto).
- Métodos: Funções atreladas à classe (definem o comportamento do objeto).

### 1.2 Construtores
- Construtor primário: Declarado no cabeçalho da classe. Pode receber parâmetros que já inicializam os atributos (forma concisa do Kotlin).
  ```kotlin
  // Declaração concisa: Construtor primário inicializa var/val
  class Pessoa(var nome: String, var peso: Float) {
      fun apresenta() = println("Olá, eu sou $nome e peso $peso Kg")
  }
  ```
- Valor padrão: Parâmetros do construtor podem ter valores default.
  ```kotlin
  class Pessoa(var nome: String = "Padawan", var peso: Float)
  // Se não passar nome, assume "Padawan"
  ```

> [!CAUTION] OBSERVAÇÃO: 
> - Construtor primário é declarado no cabeçalho da classe.
> - Parâmetros do construtor podem ter valores padrão.

### 1.3 Data Class
- Função: Classes destinadas principalmente a armazenar dados.
- Vantagem: O Kotlin gera automaticamente os métodos `equals()`, `hashCode()`, `toString()` e `copy()`.

> [!CAUTION] OBSERVAÇÃO: 
> - Data Class gera automaticamente equals, hashCode, toString e copy.

### 1.4 Modificadores de Acesso (Encapsulamento)

| MODIFICADOR | VISIBILIDADE |
|---|---|
| private | Visível somente dentro da classe onde foi declarado. |
| protected | Visível na própria classe e em suas subclasses. |
| internal | Visível em qualquer lugar dentro do mesmo módulo (conjunto de compilação). |
| public (Padrão) | Visível em qualquer lugar. |

> [!CAUTION] OBSERVAÇÃO: 
> - `private`: apenas dentro da classe.
> - `protected`: classe e subclasses.
> - `internal`: dentro do mesmo módulo.
> - `public`: qualquer lugar (padrão).

### 1.5 Propriedades com Getters e Setters Customizados
- `get()`: Customiza a ação realizada ao ler (acessar) o valor da propriedade.
- `set()`: Customiza a ação realizada ao atribuir (escrever) um valor à propriedade.
  ```kotlin
  class Pessoa {
      var idade: Int = 0
          set(value) {
              // Só atribui se for maior que zero
              field = if (value > 0) value else 1
          }
  }
  ```
- Palavra-chave `field`: Dentro do `get()`/`set()`, refere-se ao campo de apoio (backing field) que armazena o valor real na memória, evitando recursão infinita.

> [!CAUTION] OBSERVAÇÃO: 
> - `field` é o campo de apoio que armazena o valor real.
> - Usar `field` no getter/setter evita recursão infinita.

## 2. Análise de Questão de Concurso (CESGRANRIO/2021)

### 2.1 Tradução Java -> Kotlin
- Código Java original: Define atributos `private` (codigo, nome, numero, texto) e um construtor público que recebe código e nome.
- Equivalência correta em Kotlin (padrão de sintaxe):
  1. Atributos `private` dentro do corpo da classe: `private var numero = 0`.
  2. Construtor primário com parâmetros que não são propriedades da classe (apenas parâmetros do construtor) ou utilizando propriedades privadas no cabeçalho.
- Alternativa correta (Gabarito E):
  ```kotlin
  class AlunoKotlin (private val nome: String, private val codigo: String) {
      private var numero = 0
      private var texto = "EscolaX"
  }
  ```
  - Nota-se que `nome` e `codigo` são declarados como `private val` diretamente no construtor primário, o que é totalmente válido e substitui a declaração explícita no corpo.

> [!CAUTION] OBSERVAÇÃO: 
> - Parâmetros do construtor primário podem ser declarados como propriedades da classe com `var`/`val`.
> - Modificadores de acesso como `private` podem ser aplicados diretamente no construtor primário.