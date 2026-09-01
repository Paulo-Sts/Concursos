# Classe e Métodos de Testes 5

## 1. Classes de Teste
- Classes de teste são estruturas criadas no JUnit para agrupar métodos que validam o comportamento de uma unidade do sistema (classes, métodos ou funcionalidades).
- Cada classe de teste costuma estar associada a uma classe específica do sistema que será testada, seguindo uma convenção de nomenclatura clara para facilitar a identificação.
- A organização das classes de teste é fundamental para a manutenção e compreensão dos testes, especialmente em projetos de grande porte.

### 1.1 Nomes de Classes de Testes
- A convenção de nomenclatura adotada pelo JUnit é anexar o sufixo "Test" ao nome da classe que está sendo testada, conforme exemplificado na tabela abaixo:

| CLASSE TESTADA | CLASSE DE TESTE |
|---|---|
| Calculadora | CalculadoraTest |
| ValidadorSenha | ValidadorSenhaTest |
| PedidoService | PedidoServiceTest |
| ContaBancaria | ContaBancariaTest |

- Essa padronização permite que desenvolvedores e ferramentas de build (como Maven e Gradle) identifiquem automaticamente as classes que contêm testes.
- A nomenclatura clara é uma boa prática de desenvolvimento e facilita a localização de testes relacionados a uma classe específica.

### 1.2 Estrutura de uma Classe de Teste (Exemplo 1)
- Uma classe de teste básica contém a anotação `@Test` em seus métodos para indicar que são métodos de teste.
- Exemplo de código:
  ```java
  import org.junit.jupiter.api.Test;

  class CalculadoraTest {
      @Test
      void deveSomarDoisNumeros() {
          // teste
      }
  }
  ```
- Neste exemplo, a classe `CalculadoraTest` possui um único método de teste chamado `deveSomarDoisNumeros`, que será executado pelo JUnit.
- O método de teste não possui parâmetros e geralmente é declarado com visibilidade `package-private` ou `public`.

### 1.3 Estrutura de uma Classe de Teste (Exemplo 2)
- Uma classe de teste pode também ter um construtor definido, frequentemente com visibilidade `package-private`, para eventuais configurações iniciais.
- Exemplo de código:
  ```java
  import org.junit.jupiter.api.Test;

  class CalculadoraTest {
      CalculadoraTest() {
          // Construtor package-private
      }

      @Test
      void deveSomarDoisNumeros() {
          // teste
      }
  }
  ```
- O construtor não é obrigatório, mas pode ser usado para preparar o ambiente de teste antes da execução dos métodos.
- A anotação `@Test` continua sendo o requisito mínimo para definir um método de teste.

> [!CAUTION] OBSERVAÇÃO:
> - A presença do construtor não interfere na execução dos testes, mas a ausência da anotação `@Test` em um método faz com que ele não seja reconhecido como um teste.
> - Em provas de concurso, é comum perguntar qual o requisito mínimo para um método ser considerado um teste.

## 2. Métodos de Teste
- Os métodos de teste são os blocos de código que efetivamente executam a validação de uma unidade do sistema, contendo a lógica de verificação de resultados.
- Cada método de teste deve ser independente, ou seja, não deve depender da execução de outros testes, garantindo isolamento e confiabilidade.
- A execução de métodos de teste é gerenciada pelo JUnit, que fornece feedback sobre falhas ou sucessos.

### 2.1 Anotação @Test
- A anotação `@Test` é usada para indicar que um método deve ser executado como um método de teste pelo JUnit.
- Está localizada no pacote `org.junit.jupiter.api`, que faz parte do JUnit 5 (Jupiter).
- Ela marca o código como responsável por verificar se uma unidade do sistema (um método, uma classe ou um comportamento esperado) funciona conforme o esperado.
- A anotação é aplicada diretamente sobre o método, que deve ser público ou package-private, void e sem parâmetros.

> [!TIP] DICAS:
> - A anotação `@Test` não aceita atributos como no JUnit 4 (ex: `expected` ou `timeout`). No JUnit 5, essas configurações são feitas com outras anotações ou métodos específicos.
> - Fique atento a questões que confundem anotações do JUnit 4 (`@Test` do `org.junit`) com o JUnit 5 (`@Test` do `org.junit.jupiter.api`).

### 2.2 Classe Assertions
- A classe `Assertions` é uma classe utilitária do JUnit 5 que fornece métodos estáticos usados para verificar os resultados dos testes.
- Está localizada no pacote `org.junit.jupiter.api`, sendo importada estaticamente para facilitar o uso.
- Os métodos da classe `Assertions` permitem comparar valores esperados com valores reais, verificar condições booleanas, testar exceções e muito mais.
- As asserções são essenciais para validar se o sistema se comporta como esperado, sendo o coração dos testes unitários.

### 2.3 Alguns Métodos da Classe Assertions
- Entre os métodos mais comuns da classe `Assertions`, destacam-se:
  - `assertEquals(expected, actual)`: verifica se dois valores são iguais.
  - `assertNotEquals(expected, actual)`: verifica se dois valores são diferentes.
  - `assertTrue(condition)`: verifica se uma condição booleana é verdadeira.
  - `assertFalse(condition)`: verifica se uma condição booleana é falsa.
  - `assertNull(object)`: verifica se um objeto é nulo.
  - `assertNotNull(object)`: verifica se um objeto não é nulo.
  - `assertThrows(exceptionClass, executable)`: verifica se uma exceção é lançada durante a execução.
  - `assertAll(executables)`: agrupa várias asserções que são executadas juntas, mesmo que algumas falhem.
- Esses métodos são amplamente utilizados em testes unitários e são frequentemente cobrados em provas de concurso.

## 3. Exemplos de Testes com Asserções

### 3.1 Exemplo com a Classe Calculadora
- A classe a ser testada (`Calculadora`) contém um método `somar` que retorna a soma de dois números inteiros.
- Código da classe `Calculadora`:
  ```java
  public class Calculadora {
      public int somar(int a, int b) {
          return a + b;
      }
  }
  ```
- O método `somar` é público e retorna um inteiro, sendo uma unidade simples que pode ser testada com uma asserção.

### 3.2 Código da Classe de Teste (Exemplo 1)
- A classe de teste `CalculadoraTest` importa a anotação `@Test` e o método `assertEquals` da classe `Assertions`.
- O método de teste `deveSomarDoisNumeros` instancia a calculadora, executa a soma e verifica o resultado esperado.
- Código da classe de teste:
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
- A asserção `assertEquals(5, resultado)` verifica se o resultado da soma é igual a 5. Se for diferente, o teste falha.

### 3.3 Exemplo com a Classe Professor e ProfessorService
- A classe `Professor` é um modelo com atributos como nome, disciplina e salário, além de métodos getters e setters.
- Código da classe `Professor`:
  ```java
  public class Professor {
      private String nome;
      private String disciplina;
      private double salario;

      public String getName() {
          return nome;
      }

      public String getDisciplina() {
          return disciplina;
      }

      public double getSalario() {
          return salario;
      }

      public void setNome(String nome) {
          this.nome = nome;
      }

      public void setDisciplina(String disciplina) {
          this.disciplina = disciplina;
      }

      public void setSalario(double salario) {
          this.salario = salario;
      }
  }
  ```
- A classe `ProfessorService` contém regras de negócio, como o cálculo do salário anual e da bonificação com base no salário.
- Código da classe `ProfessorService`:
  ```java
  public class ProfessorService {
      public double calcularSalarioAnual(Professor professor) {
          return professor.getSalario() * 12;
      }

      public double calcularBonificacao(Professor professor) {
          if (professor.getSalario() < 10000)
              return 500;
          return 1000;
      }
  }
  ```
- O método `calcularSalarioAnual` retorna o salário multiplicado por 12, enquanto `calcularBonificacao` retorna 500 se o salário for menor que 10000, ou 1000 caso contrário.

### 3.4 Código da Classe de Teste ProfessorServiceTest
- A classe de teste `ProfessorServiceTest` contém métodos que testam as regras de negócio da classe `ProfessorService`.
- O método `deveCalcularSalarioAnual` segue o padrão Arrange-Act-Assert (AAA): prepara o cenário, executa a ação e verifica o resultado.
- Código do método `deveCalcularSalarioAnual`:
  ```java
  import org.junit.jupiter.api.Test;
  import static org.junit.jupiter.api.Assertions.assertEquals;

  public class ProfessorServiceTest {
      @Test
      void deveCalcularSalarioAnual() {
          // Arrange
          ProfessorService regraNegocio = new ProfessorService();
          Professor rogerao = new Professor();
          rogerao.setNome("Rogerão Araújo");
          rogerao.setDisciplina("Desenvolvimento de Sistemas");
          rogerao.setSalario(8000);

          // Act
          double salarioAnual = regraNegocio.calcularSalarioAnual(rogerao);

          // Assert
          assertEquals(96000, salarioAnual, 0.0);
      }
  }
  ```
- O método `deveCalcularBonificacaoQuandoSalarioForMenorQueDezMil` testa a bonificação para um salário inferior a 10000.
- Código do método de teste para bonificação:
  ```java
  @Test
  void deveCalcularBonificacaoQuandoSalarioForMenorQueDezMil() {
      // Arrange
      ProfessorService regraNegocio = new ProfessorService();
      Professor rogerao = new Professor();
      rogerao.setNome("Rogerão Araújo");
      rogerao.setDisciplina("Desenvolvimento de Sistemas");
      rogerao.setSalario(8000);

      // Act
      double bonificacao = regraNegocio.calcularBonificacao(rogerao);

      // Assert
      assertEquals(500, bonificacao, 0.0);
  }
  ```
- O terceiro parâmetro em `assertEquals` (0.0) define uma margem de erro para comparações com números de ponto flutuante, garantindo precisão.

> [!TIP] DICAS:
> - O padrão Arrange-Act-Assert (AAA) é uma boa prática para organizar testes, tornando-os mais legíveis e compreensíveis.
> - Sempre que possível, use nomes descritivos para os métodos de teste, como `deveCalcularSalarioAnual`, para indicar claramente o que está sendo testado.

> [!CAUTION] OBSERVAÇÃO:
> - Em provas, é comum perguntar sobre a estrutura mínima de um teste, como a necessidade da anotação `@Test` e a importação correta.
> - Não confunda `assertEquals` com `assertSame`. Enquanto `assertEquals` verifica igualdade de valores, `assertSame` verifica se duas referências apontam para o mesmo objeto.
> - A anotação `@Test` do JUnit 5 não requer herança ou implementação de interfaces, ao contrário do JUnit 3, que exigia herança de `TestCase`.