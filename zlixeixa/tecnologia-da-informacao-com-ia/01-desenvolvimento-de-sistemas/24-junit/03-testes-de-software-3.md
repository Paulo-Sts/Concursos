# Testes de Software

## 1. Teste Unitário
- Consiste no processo de testar componentes individuais do programa, como métodos ou classes de objeto, de forma isolada.
- O objetivo principal é isolar cada parte do sistema para garantir que esteja funcionando conforme especificado.
- Os casos de teste devem ser efetivos, ou seja:
  - Mostrar que, quando usado como esperado, o componente faz o que foi proposto;
  - Revelar defeitos existentes nos componentes.

## 2. Padrão AAA (Arrange, Act, Assert)
- É uma estrutura comum para escrever testes unitários, dividindo o teste em três etapas distintas.

### 2.1 Arrange (Preparação)
- Etapa de configuração do teste.
- São inicializadas as variáveis e definidos os valores dos dados que serão passados para o método testado.
- O sistema em teste (SUT) é preparado nesta fase.
- Exemplo:
  ```java
  Calculadora calculadora = new Calculadora();
  int a = 2;
  int b = 3;
  ```

### 2.2 Act (Execução)
- Etapa onde o método sendo testado é invocado com os parâmetros organizados.
- A ação propriamente dita do teste é executada.
- Exemplo:
  ```java
  int resultado = calculadora.somar(a, b);
  ```

### 2.3 Assert (Verificação)
- Etapa onde se verifica se o resultado obtido corresponde ao resultado esperado.
- O sistema encontra-se em teste (SUT) durante toda a execução, não apenas nesta etapa.
- No JUnit, a verificação é feita por meio de métodos de asserção, como:
  - `assertEquals()`;
  - `assertTrue()`;
  - `assertFalse()`;
  - `assertNull()`;
  - `assertNotNull()`;
  - `assertThrows()`.
- Exemplo:
  ```java
  assertEquals(5, resultado);
  ```

### 2.4 Exemplo Geral do Padrão AAA
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class CalculadoraTest {
    @Test
    void deveSomarDoisNumeros() {
        // Arrange
        Calculadora calculadora = new Calculadora();
        int a = 2, b = 3;

        // Act
        int resultado = calculadora.somar(a, b);

        // Assert
        assertEquals(5, resultado);
    }
}
```

> [!TIP] DICAS:
> - O padrão AAA separa o que está sendo testado da configuração de testes e da verificação de resultados esperados.
> - O SUT (System Under Test) é preparado no Arrange, executado no Act e verificado no Assert.

## 3. Partições de Entrada em Testes Unitários
- Em um programa que considera idades válidas entre 21 e 75 anos (incluindo os limites), o conjunto mínimo de valores para cobrir todas as partições de entrada não é apenas 21, 48 e 75.
- Para testes de unidade que cubram todas as partições de entrada, é necessário considerar também valores fora dos limites, como idades abaixo de 21 e acima de 75.
- O item que afirma que o conjunto mínimo é 21, 48 e 75 está incorreto.

> [!CAUTION] OBSERVAÇÃO:
> - Para testar partições de entrada corretamente, é preciso incluir valores que representem todas as classes de equivalência:
>   - Valores válidos dentro do intervalo (ex.: 21, 48, 75);
>   - Valores inválidos abaixo do limite inferior (ex.: 20);
>   - Valores inválidos acima do limite superior (ex.: 76).

## 4. Mock Objects
- São objetos simulados, controlados e falsos, utilizados em testes unitários.

### 4.1 Objetivo
- Substituir dependências reais por objetos simulados.
- Permitir testar apenas a unidade de código desejada, de forma isolada.

### 4.2 Uso Comum
- São muito empregados quando a classe testada depende de outros componentes, como:
  - Banco de dados;
  - Repositórios;
  - APIs externas;
  - Serviços de e-mail;
  - Serviços de pagamento;
  - Filas de mensagens;
  - Sistemas de arquivos;
  - Serviços lentos ou instáveis.

### 4.3 Testes sem Mock Objects
- Ao testar uma classe como `PedidoService`, que depende de `PedidoRepository`, que por sua vez acessa o banco de dados, surgem problemas:
  - Dependência de infraestrutura externa;
  - Lentidão na execução dos testes;
  - Dificuldade em isolar falhas.

### 4.4 Testes com Mock Objects
- Substitui-se o `PedidoRepository` real por um mock.
- O mock simula o comportamento esperado, permitindo:
  - Testar apenas a lógica de `PedidoService`;
  - Evitar acesso ao banco de dados real;
  - Controlar cenários de sucesso e falha de forma previsível.

> [!TIP] DICAS:
> - Mocks são especialmente úteis para testar comportamentos em cenários de erro, como exceções lançadas por dependências externas.
> - Frameworks como Mockito são amplamente utilizados para criar mocks em Java.

> [!CAUTION] OBSERVAÇÃO:
> - Mock objects não devem ser usados para testar a lógica de negócio da dependência em si, apenas para isolar a unidade sob teste.
> - O uso excessivo de mocks pode tornar os testes frágeis e difíceis de manter.