# Spring Framework e Spring Boot - Injeção de Dependências

## 1. História e Evolução do Spring Framework
- O Spring Framework surgiu como alternativa aos EJBs (Enterprise Java Beans), que eram complexos e exigiam código repetitivo.
- Rod Johnson propôs uma solução mais ágil utilizando POJOs (Plain Old Java Objects) e os princípios de Inversão de Controle (IoC) e Injeção de Dependência.
- Com o Java 5 e as Annotations, o Spring reduziu drasticamente o uso de XML para configurações.
- O Spring Boot foi um marco que introduziu o conceito de autoconfiguração, eliminando a necessidade de configurações manuais para funcionalidades como Spring MVC, dispatcher servlet, data sources e segurança.

## 2. Características do Spring Framework
- Mecanismos de validação, vinculação de dados (data binding) e conversão de dados.
- Linguagem de expressão própria para simplificar a criação de templates.
- Suporte à programação orientada a aspectos (AOP) para funcionalidades transversais como logs.
- Ferramentas integradas para testes, incluindo criação de objetos, contextos de teste e mocks.
- Integração com JDBC, ORM, Hibernate, Spring MVC, WebFlux, JMS, JMX, envio de emails e tarefas agendadas.
- Compatibilidade com Java, Kotlin e Groovy.

## 3. Inversão de Controle (IoC)
- É um princípio de design onde o controle do fluxo da aplicação é invertido, passando do código da aplicação para o container ou framework.
- O container do Spring gerencia o ciclo de vida dos objetos e cria instâncias das classes conforme necessário.
- A indicação de que uma classe deve ser gerenciada pelo container é feita por meio de anotações.

### 3.1 Anotações de IoC
- @Component: Anotação genérica para indicar que a classe pode ser instanciada pelo container como um bean genérico.
- @Repository: Variação de @Component para classes de acesso a banco de dados.
- @Service: Variação de @Component para classes de serviço com lógica de negócios.
- @Controller: Variação de @Component para classes que lidam com requisições HTTP.
- Todas as quatro anotações desempenham a mesma função, diferenciando-se pelo papel semântico da classe.

## 4. Injeção de Dependência (DI)
- É um padrão que permite que uma classe declare suas dependências em vez de criá-las diretamente.

### 4.1 Tipos de Injeção
- Injeção por Construtor: Dependências passadas através do construtor da classe.
- Injeção por Setter: Dependências passadas através de métodos setters.

### 4.2 Anotações de DI
- @Autowired: Anotação que indica ao container que ele deve injetar uma instância de uma classe específica.
- @Qualifier: Utilizada quando há múltiplas implementações de uma mesma interface, especificando qual deve ser injetada.
- @Inject: Equivalente ao @Autowired, faz parte da especificação oficial Java (enquanto @Autowired foi popularizado pelo Spring).

## 5. Analogia para Entender IoC e DI
- Imagine um ator em Hollywood que precisa ligar constantemente para diretores para saber se conseguiu um papel (cenário sem IoC).
- Na realidade, os diretores ligam para os atores quando são selecionados, e esse processo pode ser terceirizado (cenário com IoC e DI).
- No desenvolvimento, o container de IoC atua como a empresa terceirizada, fornecendo as dependências (como UsuarioDAO) para as classes que precisam delas, sem que elas precisem criar as instâncias diretamente.

## 6. Exemplo Prático Sem IoC e DI
- Código com acoplamento forte, onde cada classe instancia diretamente suas dependências.

```java
class UsuarioRepository {
    public void salvar(String usuario) {
        // Salva o usuario no banco de dados
    }
}

class UsuarioServiceA {
    private UsuarioRepository repository = new UsuarioRepository();

    public void adicionarUsuario(String usuario) {
        repository.salvar(usuario);
    }
}

class UsuarioServiceB {
    private UsuarioRepository repository = new UsuarioRepository();

    public void adicionarUsuario(String usuario) {
        repository.salvar(usuario);
    }
}
```

### 6.1 Problemas do Exemplo Sem IoC e DI
- Cada classe é responsável por instanciar suas próprias dependências.
- Mudanças nos parâmetros do construtor de UsuarioRepository exigem alterações em todas as classes que o utilizam.
- Criação de forte acoplamento, tornando o código rígido e difícil de manter.

## 7. Exemplo Prático Com IoC e DI
- Código com IoC e DI, onde o container gerencia as dependências.

```java
@Repository
class UsuarioRepository {
    public void salvar(String usuario) {
        // Salva o usuario no banco de dados
    }
}

@Service
class UsuarioServiceA {
    @Autowired
    private UsuarioRepository repository;

    public void adicionarUsuario(String usuario) {
        repository.salvar(usuario);
    }
}

@Service
class UsuarioServiceB {
    @Autowired
    private UsuarioRepository repository;

    public void adicionarUsuario(String usuario) {
        repository.salvar(usuario);
    }
}
```

### 7.1 Vantagens do Exemplo Com IoC e DI
- O repositório é anotado com @Repository, instruindo o container do Spring a gerenciar sua instância.
- As dependências são injetadas automaticamente com @Autowired, eliminando instâncias diretas.
- Promove a reutilização de instâncias (a mesma instância do repositório é utilizada em ambas as classes).
- Código mais eficiente, aderente aos princípios SOLID e otimiza o uso de recursos.

> [!TIP] DICAS:
> - Lembre-se da analogia de Hollywood para entender IoC e DI: o container é a "empresa terceirizada" que fornece as dependências.
> - As anotações @Component, @Repository, @Service e @Controller têm a mesma função, mas indicam papéis semânticos diferentes.
> - @Autowired é a anotação mais comum para injeção de dependências no Spring, enquanto @Inject é o padrão oficial do Java.

> [!CAUTION] OBSERVAÇÃO:
> - O Spring não é exclusivo para aplicações Android e suporta a criação de APIs RESTful (não é focado apenas em SOAP).
> - O Spring Boot simplificou o desenvolvimento com autoconfiguração, eliminando a necessidade de configurações manuais.
> - A injeção de dependência pode ser feita por construtor ou por setter, sendo a primeira a mais recomendada.