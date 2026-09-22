# Framework Spring - Injeção de Dependências 2

## 1. Inversão de Controle e Anotações do Spring
- O container assume a responsabilidade de instanciar objetos no código.
- O programador indica, por meio de anotações, quais classes serão instanciadas.
- Ao iniciar, o Spring Boot ou o Spring MVC escaneia o projeto e cria automaticamente instâncias dessas classes, gerenciando-as como beans.

### 1.1 Anotações de Componente
- `@Component`: anotação mais genérica, define uma classe como um componente/bean do Spring.
- `@Repository`: utilizada em classes relacionadas ao banco de dados (camada de persistência).
- `@Service`: utilizada em classes de serviços (camada de negócio).
- `@Controller`: utilizada em classes que recebem requisições HTTP (camada de controle).

> [!TIP] DICAS: 
> - Todas as anotações mencionadas realizam a mesma função no contexto da inversão de controle.
> - A diferença entre elas é apenas semântica e organizacional.
> - Em prova, a anotação correta para camada de persistência é `@repository` (com 'r' minúsculo).

## 2. Injeção de Dependências no Spring
- A injeção de dependências é uma técnica de design usada para obter a inversão de controle.
- O Spring Framework oferece recurso de injeção que permite aos objetos definir suas próprias dependências.
- O container Spring posteriormente injeta essas dependências nos objetos.

### 2.1 Exemplo Prático de Implementação
```java
interface MensagemServico {
    String getMessage();
}

@Component
class MensagemServicoImpl1 implements MensagemServico {
    public String getMessage() { return "Serviço 1"; }
}

@Component
class MensagemServicoImpl2 implements MensagemServico {
    public String getMessage() { return "Serviço 2";}
}

@Component
@Primary // Quando não especificado, indica que é a primeira a ser injetada.
class MensagemServicoImpl3 implements MensagemServico {
    public String getMessage() { return "Serviço Primário";}
}

@Component
class ConsumidorServico {
    @Autowired // Injeção de dependência automática pelo tipo.
    private MensagemServico mensagemServico;

    @Autowired
    @Qualifier("mensagemServicoImpl1") // Diz qual bean injetar quando >1 implementações
    private MensagemServico mensagemServicoQualificado;

    @Resource(name = "mensagemServicoImpl2") // Permite especificar o nome do bean
    private MensagemServico mensagemServicoResource;

    @Inject // Similar ao @Autowired, porém parte do JSR-330.
    private MensagemServico mensagemServicoInject;
}
```

> [!TIP] DICAS: 
> - Uma classe que implementa uma interface precisa fornecer a implementação de seus métodos.
> - Múltiplas implementações de uma mesma interface podem coexistir, cada uma com sua anotação.

### 2.2 Anotações para Injeção de Dependências
- `@Autowired`: realiza injeção automática de dependências pelo tipo. Quando há múltiplos candidatos, o Spring utiliza a classe marcada com `@Primary`.
- `@Primary`: define qual implementação é a preferida quando há múltiplos candidatos para injeção.
- `@Qualifier`: especifica explicitamente qual bean deve ser injetado quando existem múltiplas implementações.
- `@Resource`: permite indicar diretamente o nome do bean a ser injetado.
- `@Inject`: similar ao `@Autowired`, mas proveniente da especificação JSR-330.

### 2.3 Tipos de Injeção de Dependência
| TIPO DE INJEÇÃO | CARACTERÍSTICA |
|---|---|
| Constructor Injection | A dependência é resolvida por meio de um construtor do objeto a receber o objeto dependente |
| Setter Injection | A dependência é injetada através de métodos setters |

> [!CAUTION] OBSERVAÇÃO: 
> - Na injeção via setter, a ausência de uma dependência necessária resulta em erro em tempo de execução.
> - Não se pode afirmar que a classe será criada de forma consistente se uma dependência não estiver disponível.
> - A injeção de dependência permite desacoplar uma classe de suas classes dependentes.

## 3. Conceitos Fundamentais

### 3.1 Inversão de Controle vs Injeção de Dependências
- Inversão de Controle: é um princípio que abrange a delegação de responsabilidades para um contêiner.
- Injeção de Dependências: é uma técnica que implementa o conceito de inversão de controle.
- Os termos não são sinônimos, referem-se a conceitos distintos.

> [!CAUTION] OBSERVAÇÃO: 
> - Ambos os conceitos são contemporâneos e não se limitam a uma única linguagem de programação.
> - Podem ser aplicados em diversas linguagens de programação.

### 3.2 Pool de Objetos
- Pode ser usado no contexto de injeção de dependências para gerenciar a criação e reutilização de instâncias.
- É um dos padrões de gestão de objetos que um container pode adotar.
- O Spring permite configurar beans como "singleton", "prototype", ou utilizar um pool de objetos em casos específicos.

## 4. Análise de Questões Teóricas

### 4.1 Anotações do Spring
- `@IoC`: não corresponde a uma anotação válida no Spring.
- `@DependsOn`: define que um bean depende de outro para ser inicializado.
- `@Autowired`: amplamente utilizada para injetar dependências automaticamente.
- `@Qualifier`: empregada para especificar qual bean deve ser injetado.

> [!TIP] DICAS: 
> - A injeção de dependência é uma prática recomendada para resolver o problema de acoplamento forte entre classes.
> - Em vez de instanciar diretamente (usando new), a injeção de dependência delega essa responsabilidade ao container.