# Framework Spring - Beans e Ciclo de Vida 3

## 1. Visão Geral dos Beans no Spring
- Beans são os componentes centrais de qualquer aplicação Spring, representando os objetos que o contêiner Spring gerencia.
- O contêiner Spring controla o ciclo de vida e as dependências dos Beans de forma automática.
- A configuração dos Beans pode ser feita via XML, anotações ou classes Java.
- O escopo define o tempo de vida do Bean e como ele será compartilhado dentro da aplicação.
- Um bean é qualquer classe cujo ciclo de vida é gerido pelo contêiner de injeção de dependência, garantindo o gerenciamento automático e ordenado das dependências.

### 1.1 Função do Contêiner IoC
- Inversão de Controle (IoC): o contêiner é responsável pela criação, gerenciamento e destruição dos Beans, injetando as dependências conforme necessário.
- Analogia com o "Hollywood Principle": em vez de o ator (ou classe) buscar um papel, é o diretor (ou contêiner) que o seleciona, ilustrando o conceito de inversão de controle.
- Cabe ao desenvolvedor indicar se uma instância deve ser criada por solicitação ou quando a aplicação é inicializada, definindo o ciclo de vida dos objetos.
- A configuração de beans evoluiu de arquivos XML para anotações no código, agilizando o desenvolvimento.

### 1.2 ApplicationContext
- O ApplicationContext representa o contêiner de injeção de dependência e inclui as classes de gerenciamento do framework.
- Por meio do ApplicationContext, é possível obter uma instância de bean usando o método getBean, passando a classe.
- Exemplo de uso do bean:
  ```java
  ApplicationContext context = SpringApplication.run(MyApp.class, args);
  MyBean bean = context.getBean(MyBean.class); // MyBean é instanciado aqui.
  ```
- O uso do contêiner reduz o acoplamento entre classes, pois ele lida com as dependências, assegurando que sejam instanciadas na ordem correta.

## 2. Ciclo de Vida dos Beans
- Criação: o contêiner Spring cria os Beans conforme definido no arquivo de configuração ou via anotações.
- Inicialização: após a criação, o Spring chama métodos de inicialização configurados pelo desenvolvedor.
- Destruição: quando o ciclo de vida do Bean termina, o contêiner chama métodos de destruição, se configurados.

### 2.1 Anotações para o Ciclo de Vida
- @PostConstruct: executado após o Bean ser criado e injetado com suas dependências.
- @PreDestroy: executado antes de o Bean ser destruído pelo contêiner.
- Essas anotações facilitam reações específicas ao processo de instanciação e ao término do ciclo de vida dos objetos.

### 2.2 Exemplo de Código
```java
@Component
public class MyBean {

    @PostConstruct
    public void init() {
        System.out.println("Bean iniciado");
    }

    @PreDestroy
    public void destroy() {
        System.out.println("Bean destruído");
    }
}
```
- Assim que o contêiner instancia o objeto, o método init é invocado, exibindo "Bean iniciado" no console.
- Quando o garbage collector remove o objeto da memória, o método @PreDestroy é chamado, registrando "Bean destruído" no console.

### 2.3 Métodos Customizados
- @PostConstruct: executado após o Bean ser criado e injetado com suas dependências.
- @PreDestroy: executado antes de o Bean ser destruído pelo contêiner.

## 3. Tipos de Escopo dos Beans

### 3.1 Singleton
- Garante que haja uma única instância do Bean dentro do container Spring durante o ciclo de vida da aplicação.
- É o escopo padrão do Spring, aplicado automaticamente quando o escopo não é especificado.
- Utilizado para serviços globais ou componentes que devem ser compartilhados em toda a aplicação.
- Deve-se evitar o uso de variáveis de estado em classes singleton, já que uma única instância será compartilhada por todas as referências.
- Ao solicitar uma instância de um bean com escopo singleton, o contêiner verifica se a instância já existe; se sim, retorna a existente, caso contrário, cria uma nova.

### 3.2 Prototype
- Cria uma nova instância do Bean toda vez que ele é solicitado ao container Spring.
- Utilizado quando múltiplas instâncias do mesmo Bean são necessárias, ou seja, quando um Bean não deve ser compartilhado entre os componentes da aplicação.
- Ideal para objetos de curta duração ou componentes que não compartilham estado.
- Cada chamada para o contêiner Spring retorna uma nova instância do bean, ao contrário do singleton, que reaproveita a mesma instância.
- A anotação @Scope("prototype") deve ser explicitamente definida para o contêiner saber que uma nova instância deve ser gerada para cada requisição.

### 3.3 Request
- Cria uma nova instância do Bean para cada requisição HTTP.
- Utilizado principalmente em aplicações web, em que o estado do Bean não deve ser compartilhado entre diferentes requisições.
- Ideal para componentes que armazenam informações específicas de uma requisição, como formulários ou parâmetros de consulta.
- Exemplo de código:
  ```java
  @Component
  @Scope("request")
  public class RequestBean {
      public RequestBean() {
          System.out.println("Instância RequestBean criada.");
      }
  }

  @RestController
  public class RequestController {

      @Autowired
      private RequestBean requestBean;

      @GetMapping("/request")
      public String handleRequest() {
          System.out.println("RequestBean sendo usado.");
          return "Bean de Request criado!";
      }
  }
  ```

### 3.4 Session
- Cria um Bean que é compartilhado durante toda a sessão HTTP.
- Utilizado para armazenar informações específicas de um usuário durante a sua sessão, como dados de login, preferências ou carrinho de compras em uma aplicação web.
- Ideal para componentes que precisam manter um estado por toda a duração da sessão de um usuário, sem serem recriados a cada requisição.
- Exemplo de código:
  ```java
  @Component
  @Scope("session")
  public class SessionBean {
      public SessionBean() {
          System.out.println("Instância SessionBean criada.");
      }
  }

  @RestController
  public class SessionController {

      @Autowired
      private SessionBean sessionBean;

      @GetMapping("/session")
      public String handleSession() {
          System.out.println("SessionBean sendo usado.");
          return "Bean de Sessão criado!";
      }
  }
  ```
- O SessionBean é criado uma vez por sessão de usuário e reutilizado para todas as requisições que esse usuário fizer enquanto a sessão estiver ativa.

### 3.5 Resumo Comparativo dos Escopos
| ESCOPO | COMPORTAMENTO | QUANDO UTILIZAR |
|---|---|---|
| Singleton | Única instância por aplicação | Serviços globais e componentes compartilhados |
| Prototype | Nova instância a cada solicitação | Objetos de curta duração e sem compartilhamento de estado |
| Request | Nova instância por requisição HTTP | Dados específicos de uma requisição, como formulários |
| Session | Única instância por sessão de usuário | Dados específicos do usuário durante a sessão |

> [!TIP] DICAS:
> - O escopo singleton é o padrão do Spring, portanto a anotação @Scope("singleton") é opcional.
> - Para o escopo prototype, a anotação @Scope("prototype") é obrigatória.
> - Os escopos request e session são utilizados exclusivamente em aplicações web.
> - O escopo singleton não deve ser confundido com o padrão de projeto singleton; no Spring, refere-se a uma instância gerida pelo contêiner, criada quando a classe é utilizada pela primeira vez.

> [!CAUTION] OBSERVAÇÃO:
> - No escopo singleton, deve-se evitar o uso de variáveis de estado, pois uma única instância será compartilhada por todas as referências, o que pode causar inconsistências.
> - No escopo prototype, cada solicitação resulta em uma nova instância, implicando maior consumo de memória.