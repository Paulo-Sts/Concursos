# JUnit - Assertions e Testes Unitários em Java 7

## 1. Assertions - Métodos da Classe Assertions
- A classe Assertions do JUnit fornece métodos estáticos para verificar resultados esperados em testes unitários.
- Cada método avalia uma condição específica e falha o teste caso a condição não seja satisfeita.
- Os métodos são utilizados dentro de métodos anotados com @Test.

### 1.1 Métodos de Comparação de Valores
- assertEquals: Verifica se dois valores são iguais.
- assertNotEquals: Verifica se dois valores são diferentes.
- assertArrayEquals: Verifica se dois arrays possuem os mesmos elementos na mesma ordem.

### 1.2 Métodos de Condição Booleana
- assertTrue: Verifica se uma condição é verdadeira.
- assertFalse: Verifica se uma condição é falsa.

### 1.3 Métodos de Referência
- assertNull: Verifica se uma referência é null.
- assertNotNull: Verifica se uma referência não é null.
- assertSame: Verifica se duas referências apontam para o mesmo objeto.
- assertNotSame: Verifica se duas referências apontam para objetos diferentes.

### 1.4 Métodos de Exceção e Tempo
- assertThrows: Verifica se uma exceção esperada foi lançada.
- assertDoesNotThrow: Verifica se determinado código não lança exceção.
- assertTimeout: Verifica se determinado código executa dentro de um tempo máximo.

### 1.5 Método Agrupador
- assertAll: Agrupa várias assertions em uma única verificação composta.

## 2. Exemplos de Código

### 2.1 Método assertEquals
- Código de exemplo para testar uma soma:

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

### 2.2 Método assertNotEquals
- Código de exemplo para verificar que o resultado não é igual a um valor específico:

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertNotEquals;

class CalculadoraTest {
    @Test
    void deveSomarDoisNumeros() {
        Calculadora calculadora = new Calculadora();
        int a = 2, b = 3;
        int resultado = calculadora.somar(a, b);
        assertNotEquals(6, resultado);
    }
}
```

### 2.3 Método assertEquals com Delta para Ponto Flutuante
- Quando se trabalha com números de ponto flutuante (double ou float), é necessário informar um delta (margem de erro) para a comparação.
- O delta representa a tolerância aceita na diferença entre o valor esperado e o valor obtido.

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class CalculadoraTest {
    @Test
    void testRaiz() {
        Calculadora calc = new Calculadora();
        assertEquals(4.0, calc.raiz(16.0), 0.0001);
        // O terceiro parâmetro é a margem de erro aceita na comparação
    }
}
```

### 2.4 Exemplo Completo - Método que Retorna o Maior Valor de um Array
- Código da classe a ser testada:
```java
public class Prova {
    static int vetor(int n, int vet[]) {
        int val;
        val = vet[0];
        for (int j = 1; j < n; j++) {
            if (val < vet[j]) {
                val = vet[j];
            }
        }
        return val;
    }
}
```

- Código do teste:
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class ProvaTest {
    @Test
    void testVetor() {
        int[] vet = {89, 90, 84, 91};
        int r = Prova.vetor(vet.length, vet);
        assertEquals(91, r);
    }
}
```

### 2.5 Exemplo Completo - Método que Calcula Produto Interno entre Vetores
- Código da classe a ser testada:
```java
public final class Vetores {
    private Vetores() {
    }
    
    public static int multiplica(int[] a, int[] b) {
        if ((a == null) || (b == null))
            throw new IllegalArgumentException("Argumento nulo");
        if (a.length != b.length)
            throw new IllegalArgumentException("Vetores com tuplas diferentes");
        int sum = 0;
        for (int i = 0; i < a.length; i++)
            sum += a[i] * b[i];
        return sum;
    }
}
```

- Código do teste:
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class VetoresTest {
    @Test
    void testMultiplica() {
        assertEquals(39, Vetores.multiplica(new int[] {3, 4}, new int[] {5, 6}));
        // 3 * 5 + 4 * 6 = 15 + 24 = 39
    }
}
```

> [!TIP] DICAS:
> - O método `assertEquals` aceita diferentes combinações de parâmetros: (esperado, atual) para tipos primitivos e objetos, e (esperado, atual, delta) para números de ponto flutuante.
> - A ordem dos parâmetros no `assertEquals` é sempre: valor esperado primeiro, valor obtido (atual) em segundo.
> - Para comparar arrays, utilize `assertArrayEquals` em vez de `assertEquals`, pois este último compara referências, não o conteúdo.
> - O método `assertAll` é útil para agrupar múltiplas verificações, garantindo que todas sejam executadas mesmo que algumas falhem.

> [!CAUTION] OBSERVAÇÃO:
> - Ao testar métodos que retornam `double` ou `float`, sempre utilize o parâmetro delta para evitar falsos negativos devido a pequenas variações de precisão.
> - O delta deve ser um valor pequeno (ex: 0.0001) que represente a margem de erro aceitável.
> - Não confunda `assertEquals` com `assertSame`: o primeiro compara valores (usando `equals()`), enquanto o segundo compara referências (usando `==`).