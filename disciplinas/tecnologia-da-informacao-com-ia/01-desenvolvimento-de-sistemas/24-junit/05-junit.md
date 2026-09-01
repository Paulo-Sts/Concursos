# Testes de Software com JUnit

## 1. Introdução e Conceituação

### 1.1 O que é o JUnit?
- É uma ferramenta para projetos Java que permite a criação e automatização de testes.
- É um framework de testes automatizados para Java.
- Usado principalmente para verificar se métodos e classes se comportam conforme o esperado.

### 1.2 Funcionalidades
- Permite indicar falhas e erros encontrados durante a execução dos testes.
- Pode ser estendido ou integrado a outras ferramentas e frameworks por meio de mecanismos de extensão.

## 2. Características do JUnit

### 2.1 Agilidade no Desenvolvimento
- Permite a criação rápida de código de teste.
- Faz com que o programador perca menos tempo na criação dos testes.
- Possibilita um aumento na qualidade do sistema sendo desenvolvido e testado.

### 2.2 Depuração
- Auxilia na depuração do código durante o processo de desenvolvimento.

> [!TIP] DICAS: 
> - A principal proposta do JUnit é acelerar o desenvolvimento de testes sem comprometer a qualidade do sistema.

## 3. Vantagens do JUnit

- Automatização dos testes, reduzindo o esforço manual.
- Identificação precoce de falhas no código.
- Integração com ferramentas de build e IDEs (como Eclipse e IntelliJ).
- Facilidade na manutenção e refatoração do código.
- Suporte a testes de regressão e unitários.

## 4. Exemplo Básico de Teste com JUnit 5

### 4.1 Código de Exemplo
- O exemplo a seguir demonstra um teste unitário simples para uma calculadora:

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

### 4.2 Estrutura do Teste (Padrão AAA)
- Arrange: preparação dos dados e objetos necessários.
- Act: execução da ação a ser testada.
- Assert: verificação do resultado esperado.

## 5. Tipos de Testes

### 5.1 Testes Unitários
- Verificam pequenas unidades do código, como:
  - Métodos;
  - Funções;
  - Classes;
  - Regras de negócio isoladas.

#### 5.1.1 Exemplo
```java
@Test
void deveSomarDoisNumeros() {
    Calculadora calc = new Calculadora();
    int resultado = calc.somar(2, 3);
    assertEquals(5, resultado);
}
```

> [!CAUTION] OBSERVAÇÃO: 
> - Testes unitários devem ser rápidos, isolados e independentes entre si.

### 5.2 Testes de Integração
- Verificam se diferentes partes do sistema funcionam corretamente em conjunto.

#### 5.2.1 Exemplo
```java
@Test
void deveSalvarClienteNoRepositorio() {
    Cliente cliente = new Cliente("Ana");
    Cliente salvo = clienteRepository.salvar(cliente);
    assertNotNull(salvo.getId());
}
```

> [!CAUTION] OBSERVAÇÃO: 
> - Diferente dos testes unitários, os testes de integração podem depender de recursos externos como bancos de dados, APIs ou arquivos.

### 5.3 Testes de Regressão
- Verificam se algo que funcionava antes continua funcionando após uma alteração no sistema.

#### 5.3.1 Funcionamento
- Os testes JUnit existentes são reexecutados após alterações no código.
- Verifica-se se as regras antigas continuam funcionando.
- Detecta se alguma funcionalidade foi quebrada.

> [!TIP] DICAS: 
> - Para garantir eficácia, mantenha uma suíte de testes atualizada e execute-a sempre que houver mudanças no sistema.

### 5.4 Testes Funcionais Automatizados
- Validam funcionalidades ou regras de negócio, ainda em nível de código.

#### 5.4.1 Exemplo
```java
@Test
void deveAprovarAlunoComMediaMaiorOuIgualASete() {
    AlunoService service = new AlunoService();
    boolean aprovado = service.estaAprovado(7.0);
    assertTrue(aprovado);
}
```

### 5.5 Testes de Exceção
- Verificam se uma exceção é lançada corretamente em situações de erro.

#### 5.5.1 Exemplo
```java
@Test
void deveLancarExcecaoAoDividirPorZero() {
    Calculadora calc = new Calculadora();
    assertThrows(ArithmeticException.class, () -> calc.dividir(10, 0));
}
```

### 5.6 Testes Parametrizados
- Executam o mesmo teste com múltiplas entradas diferentes.

#### 5.6.1 Exemplo
```java
@ParameterizedTest
@ValueSource(ints = {18, 19, 20})
void deveRetornarMaiorDeIdade(int idade) {
    ValidadorIdade validador = new ValidadorIdade();
    assertTrue(validador.isMaiorDeIdade(idade));
}
```

- O teste executa uma vez para cada valor informado.

> [!TIP] DICAS: 
> - Testes parametrizados não são um tipo funcional de teste, mas uma técnica/recurso do JUnit para testar múltiplas entradas.

> [!CAUTION] OBSERVAÇÃO: 
> - Fique atento: o uso de testes parametrizados reduz a repetição de código e facilita a manutenção dos testes.