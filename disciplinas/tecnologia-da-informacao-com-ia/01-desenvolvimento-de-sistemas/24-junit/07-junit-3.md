# Arquitetura JUnit e Testes Automatizados 3

## 1. Arquitetura JUnit 5

### 1.1 Conceituação
- Representa a forma como o framework é organizado internamente para permitir a criação, descoberta, execução e extensão de testes automatizados em Java.
- O JUnit 5 é composto por três subprojetos principais: JUnit Platform, JUnit Jupiter e JUnit Vintage.

### 1.2 JUnit Platform
- É a base da arquitetura do JUnit moderno.
- Contém elementos estruturais para execução de testes.
- Define a API TestEngine, que permite a descoberta e execução de testes.
- Possibilita que outros frameworks (que utilizam um modelo de programação próprio) sejam executados pela plataforma.
- Fornece a infraestrutura para:
  - Execução de testes;
  - Descoberta de testes;
  - Relatórios de execução.

### 1.3 JUnit Jupiter
- É a combinação do modelo de programação e do modelo de extensão do JUnit 5.
- Fornece um TestEngine para escrever e executar testes e extensões na plataforma, baseados no paradigma Jupiter.
- Inclui as anotações modernas (ex.: @Test, @BeforeEach, @AfterEach) e a nova API de asserções (Assertions).
- Pode ser utilizado em programas escritos em Kotlin, além de Java.

### 1.4 JUnit Vintage
- Projeto que provê uma TestEngine para execução de testes legados.
- Permite executar na plataforma JUnit 5 testes baseados em JUnit 3 e JUnit 4.
- Garante compatibilidade retroativa com códigos de teste antigos.

> [!TIP] DICAS:
> - A questão que pergunta qual subprojeto executa testes JUnit 3 e 4: a resposta é "Vintage".
> - Os três subprojetos são: Platform, Jupiter e Vintage. Essa tríade é cobrada com frequência.

### Exemplo de código com JUnit Jupiter
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

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

### Exemplo de código com JUnit Vintage (JUnit 4)
```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class CalculadoraTest {
    @Test
    public void deveSomarDoisNumeros() {
        Calculadora calc = new Calculadora();
        int resultado = calc.somar(2, 3);
        assertEquals(5, resultado);
    }
}
```

## 2. Testes Automatizados

### 2.1 Conceituação
- São testes executados por meio de código, scripts ou ferramentas.
- Objetivo: verificar automaticamente se um software apresenta o comportamento esperado.
- Em vez de um teste manual para cada funcionalidade, os códigos dos testes automatizados testam outros códigos, executando ações, comparando resultados e informando se o comportamento está correto ou não.
- Exemplos de ferramentas amplamente utilizadas: Selenium, JUnit, PyTest, Appium.

### 2.2 Para que servem
- Agilizam o processo de validação, pois uma vez codificados, podem ser repetidos quantas vezes forem necessárias.
- Permitem testes de regressão: reexecução de testes anteriores para verificar se alterações não introduziram novos bugs.
- Aumentam a confiabilidade do software, pois detectam falhas precocemente.
- Reduzem o retrabalho manual e podem ser integrados a processos de integração contínua.

> [!CAUTION] OBSERVAÇÃO:
> - Testes automatizados não eliminam completamente a necessidade de testes manuais (ex.: testes de usabilidade ou cenários complexos). Eles complementam, mas não substituem totalmente.
> - A automação pode aumentar custos iniciais (contratação de engenheiro de automação, infraestrutura), mas traz ganhos de eficiência a médio/longo prazo.

### 2.3 Exemplo comparativo: teste manual vs JUnit

#### Classe a ser testada
```java
public class Calculadora {
    public int somar(int a, int b) {
        return a + b;
    }
}
```

#### Teste manual (sem framework)
```java
public class Main {
    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        System.out.println(calc.somar(2, 3));
    }
}
```
- Nesse caso, o programador precisa verificar visualmente a saída no console.
- Não há automação da verificação; o resultado é avaliado manualmente.

#### Teste automatizado com JUnit
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
- O framework compara automaticamente o resultado obtido com o esperado.
- Em caso de falha, o JUnit reporta o erro sem necessidade de inspeção manual da saída.

> [!TIP] DICAS:
> - A principal vantagem do teste automatizado é a repetibilidade e a verificação automática, o que reduz erros humanos e agiliza o ciclo de desenvolvimento.
> - Em provas, geralmente associam testes automatizados a testes de regressão e a ferramentas como JUnit, Selenium etc.