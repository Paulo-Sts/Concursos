# JUnit Framework para Testes Unitários em Java 6

## 1. Introdução ao JUnit
- O JUnit é um framework open-source amplamente utilizado para a criação de testes unitários automatizados na linguagem Java.
- O framework passou por evoluções significativas ao longo de suas versões (JUnit 3, JUnit 4 e JUnit 5), com mudanças importantes na forma de declarar e estruturar os testes.

> [!CAUTION] OBSERVAÇÃO:
> - As diferenças entre as versões são cobradas com frequência em concursos. É fundamental conhecer as características específicas de cada uma.

## 2. JUnit 3
- Nesta versão, as classes de teste precisam estender a classe `junit.framework.TestCase`.
- Os métodos de teste são identificados pelo prefixo "test" no nome do método.
- Os métodos de teste devem ser públicos, não receber parâmetros e ter retorno void.
- A classe de teste não precisa de anotações específicas.

### 2.1 Exemplo de Classe de Teste no JUnit 3
```java
import junit.framework.TestCase;

public class CalculadoraTest extends TestCase {
    public void testSomarDoisNumeros() {
        Calculadora calculadora = new Calculadora();
        int a = 2, b = 3;
        int resultado = calculadora.somar(a, b);
        assertEquals(5, resultado);
    }
}
```

### 2.2 Características Principais do JUnit 3
- A classe de teste deve ser pública.
- A classe de teste deve herdar de `junit.framework.TestCase`.
- Os métodos de teste devem ser públicos.
- Os métodos de teste devem ter o prefixo "test".
- Os métodos de teste não recebem parâmetros.
- Os métodos de teste retornam void.
- Para verificar resultados, utiliza-se o método `assertEquals` da classe `TestCase`.
- A configuração do ambiente requer a adição do arquivo .JAR do JUnit ao classpath do projeto.

> [!TIP] DICAS:
> - A herança de `TestCase` e o prefixo "test" são os marcadores mais característicos do JUnit 3.
> - O arquivo JAR é a extensão correta para adicionar ao projeto, não .ZAR.

## 3. JUnit 4
- Nesta versão, não é mais necessário estender a classe `TestCase`.
- Os métodos de teste são identificados pela anotação `@Test`.
- A anotação `@Test` substitui a necessidade do prefixo "test".
- Os métodos de teste devem ser públicos, não receber parâmetros e ter retorno void.
- As asserções podem ser usadas com import estático de `org.junit.Assert`.

### 3.1 Exemplo de Classe de Teste no JUnit 4
```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class CalculadoraTest {
    @Test
    public void deveSomarDoisNumeros() {
        Calculadora calculadora = new Calculadora();
        int a = 2, b = 3;
        int resultado = calculadora.somar(a, b);
        assertEquals(5, resultado);
    }
}
```

### 3.2 Características Principais do JUnit 4
- A classe de teste deve ser pública.
- A classe de teste não herda de nenhuma classe específica do framework.
- Os métodos de teste devem ser anotados com `@Test`.
- Os métodos de teste devem ser públicos.
- Os métodos de teste não recebem parâmetros.
- Os métodos de teste retornam void.
- A classe `org.junit.Assert` fornece os métodos para asserções.

> [!TIP] DICAS:
> - A anotação `@Test` é a principal diferença em relação ao JUnit 3.
> - A classe `org.junit.Assert` é uma classe, não um pacote.

## 4. JUnit 5
- O JUnit 5 é a versão mais recente e moderna do framework.
- Utiliza a anotação `@Test` do pacote `org.junit.jupiter.api.Test`.
- Não é necessário estender classes ou ter prefixos específicos.
- Os métodos de teste podem ter visibilidade padrão (package-private), não sendo obrigatório serem públicos.
- As asserções são fornecidas pela classe `org.junit.jupiter.api.Assertions`.

### 4.1 Exemplo de Classe de Teste no JUnit 5
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class CalculadoraTest {
    @Test
    void deveSomarDoisNumeros() {
        Calculadora calculadora = new Calculadora();
        int a = 2, b = 3;
        int resultado = calculadora.somar(a, b);
        assertEquals(5, resultado);
    }
}
```

### 4.2 Características Principais do JUnit 5
- A classe de teste não precisa ser pública.
- A classe de teste não herda de nenhuma classe específica.
- Os métodos de teste são anotados com `@Test` (do pacote `org.junit.jupiter.api`).
- Os métodos de teste podem ter visibilidade padrão (package-private).
- Os métodos de teste não recebem parâmetros.
- Os métodos de teste retornam void.
- As asserções estão na classe `org.junit.jupiter.api.Assertions`.
- A classe `Assertions` fornece métodos estáticos para verificação de resultados.
- É possível usar import estático para os métodos de asserção, como `assertEquals`.

> [!TIP] DICAS:
> - No JUnit 5, a visibilidade padrão (sem modificador) é suficiente para os métodos de teste.
> - O pacote das anotações e asserções mudou: `org.junit.jupiter.api` em vez de `org.junit`.

## 5. A Classe Assertions
- A classe `Assertions` é fundamental no JUnit 5 para validar os resultados dos testes.
- Ela está localizada no pacote `org.junit.jupiter.api`.
- Fornece métodos estáticos para comparar o resultado esperado com o resultado obtido.
- A verificação ocorre durante a execução de um teste.

### 5.1 Exemplo de Importação da Classe Assertions
- Existem duas formas principais de importar e usar a classe:
  - Usando o nome da classe:
```java
import org.junit.jupiter.api.Assertions;

class CalculadoraTest {
    @Test
    void deveSomarDoisNumeros() {
        // ...
        Assertions.assertEquals(5, resultado);
    }
}
```

  - Usando import estático:
```java
import static org.junit.jupiter.api.Assertions.assertEquals;

class CalculadoraTest {
    @Test
    void deveSomarDoisNumeros() {
        // ...
        assertEquals(5, resultado);
    }
}
```

### 5.2 Características dos Métodos de Asserção
- Os métodos são estáticos, permitindo uso direto sem instanciar a classe.
- O método `assertEquals` é um dos mais utilizados para comparar valores esperados e obtidos.
- Outros métodos comuns incluem `assertTrue`, `assertFalse`, `assertNull`, `assertNotNull` e `assertThrows`.

> [!CAUTION] OBSERVAÇÃO:
> - No JUnit 4, a classe de asserções é `org.junit.Assert`.
> - No JUnit 5, a classe de asserções é `org.junit.jupiter.api.Assertions`.
> - É importante não confundir os pacotes nas diferentes versões.

## 6. Comparativo entre as Versões do JUnit
| CARACTERÍSTICA | JUNIT 3 | JUNIT 4 | JUNIT 5 |
|---|---|---|---|
| Classe base necessária | `junit.framework.TestCase` | Nenhuma | Nenhuma |
| Identificação do método de teste | Prefixo "test" | Anotação `@Test` | Anotação `@Test` |
| Pacote da anotação `@Test` | Não se aplica | `org.junit.Test` | `org.junit.jupiter.api.Test` |
| Visibilidade do método de teste | Público | Público | Padrão (package-private) ou público |
| Retorno do método de teste | void | void | void |
| Parâmetros do método de teste | Nenhum | Nenhum | Nenhum |
| Classe de asserções | `junit.framework.TestCase` (herdado) | `org.junit.Assert` | `org.junit.jupiter.api.Assertions` |
| Necessidade de extensão de classe | Sim (`TestCase`) | Não | Não |

## 7. Pontos Importantes para Concursos
- A configuração do JUnit no projeto exige a adição do arquivo .JAR (e não .ZAR).
- No JUnit 3, a classe de teste deve herdar de `junit.framework.TestCase`.
- No JUnit 3, os métodos de teste são públicos, não recebem parâmetros e retornam void.
- No JUnit 4, os métodos de teste são identificados pela anotação `@Test` e devem ser públicos.
- No JUnit 5, os métodos de teste são identificados pela anotação `@Test` e podem ter visibilidade padrão.
- A classe `org.junit.Assert` (JUnit 4) é uma classe, não um pacote.
- A classe `org.junit.jupiter.api.Assertions` (JUnit 5) é uma classe, não um pacote.
- O método `assertEquals` gera uma exceção do tipo `AssertionFailedError` quando os valores comparados são diferentes.

> [!TIP] DICAS:
> - A versão do JUnit utilizada no código pode ser identificada pela forma como os testes são declarados.
> - Herança de `TestCase` ou prefixo "test" indicam JUnit 3.
> - Anotação `@Test` do pacote `org.junit` indica JUnit 4.
> - Anotação `@Test` do pacote `org.junit.jupiter.api` indica JUnit 5.
> - A importação de asserções também ajuda a identificar a versão.

> [!CAUTION] OBSERVAÇÃO:
> - Uma classe de teste não pode ser declarada como `abstract` ou `private`.
> - A anotação `@TestCase` não existe no JUnit 5.
> - A anotação `@Enabled` não é necessária para que um teste seja executado.
> - Métodos de teste não podem receber parâmetros em nenhuma das versões.