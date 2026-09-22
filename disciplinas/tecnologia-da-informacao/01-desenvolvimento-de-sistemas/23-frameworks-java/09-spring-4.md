# Framework Spring MVC 4

## 1. Introdução ao Spring MVC
- O Spring MVC é o núcleo do framework Spring, representando sua parte central.
- O conceito de MVC (Model-View-Controller) estrutura a aplicação em três camadas lógicas: Model, View e Controller.
- A separação em camadas é fundamental para a segurança, pois evita que a interface (View) acesse diretamente o banco de dados (Model), expondo o sistema a riscos.
- O Controller atua como intermediário, garantindo que a View se concentre apenas na exibição dos dados.
- O Spring inovou com beans leves, inversão de controle e injeção de dependências, substituindo a configuração massiva em XML por anotações a partir do Java 5.
- Com o Spring Boot e o Java 8, surgiram auto-configuração e starters, que simplificaram significativamente o Spring MVC, automatizando componentes como Dispatcher Servlet, View Resolver e handler mappings.

> [!TIP] DICAS: 
> - O Spring MVC é o coração do Spring, e sua compreensão é essencial para provas de desenvolvimento web.
> - A evolução do Spring para Spring Boot eliminou grande parte da configuração manual, um ponto frequentemente cobrado em concursos.

## 2. Padrão MVC
- O padrão MVC é um padrão de arquitetura de software que separa a aplicação em três componentes principais:
  - Model (Modelo);
  - View (Visão);
  - Controller (Controlador).
- Essa separação ajuda a gerenciar a complexidade em aplicações web, facilitando a manutenção e a escalabilidade.
- O principal benefício do MVC é o desacoplamento das camadas, que reduz a dependência entre elas, e a coesão, que organiza internamente cada camada.
- O desacoplamento permite modificar uma camada sem impactar as demais. Por exemplo, trocar o banco de dados de MongoDB para Postgres não afeta as outras camadas.

> [!CAUTION] OBSERVAÇÃO: 
> - O maior benefício do MVC é a separação lógica das camadas, permitindo a modificação das tecnologias de cada uma sem afetar as demais. Esse é um conceito central que costuma cair em provas.

### 2.1 Model
- Representa a camada de dados e a lógica de negócios da aplicação.
- No Spring Boot, o Model é tipicamente representado por:
  - Entidades (classes de domínio) anotadas com @Entity.
  - Repositórios (interfaces para acesso aos dados) que estendem JpaRepository ou CrudRepository.
- Exemplo: classe “Aluno” que mapeia a tabela “Aluno” no banco de dados e contém métodos de manipulação.
- A camada Model inclui classes responsáveis por operações de consulta, criação, atualização e exclusão de dados (Repository).
- O Spring Data JPA simplifica o acesso a dados, abstraindo o boilerplate e permitindo métodos de consulta personalizados por convenção de nomes ou anotações @Query.

### 2.2 View
- Responsável pela apresentação dos dados ao usuário.
- No Spring Boot, pode servir conteúdo estático (HTML, CSS, JavaScript) e templates (como Thymeleaf).
- Muitas aplicações modernas usam o Spring Boot como backend para APIs REST, deixando a renderização para o frontend, que consome dados em formato JSON.
- O modelo clássico do MVC caiu em desuso entre 2010 e 2020 devido à popularização das APIs REST, mas há um movimento recente de retorno ao MVC.
- Template Engines: o Spring Boot integra-se com Thymeleaf, FreeMarker, Mustache, entre outros.
- Suporte para APIs REST: utiliza a anotação @RestController para retornar dados em formatos como JSON ou XML.

> [!TIP] DICAS: 
> - O Thymeleaf é o padrão no Spring para templates, permitindo estruturas condicionais e de repetição no HTML.
> - Em APIs REST, a View é substituída pela entrega de dados JSON, e o frontend é uma aplicação separada.

### 2.3 Controller
- Gerencia a interação do usuário, atuando como intermediário entre a View e o Model.
- No Spring Boot, controllers são classes anotadas com @Controller ou @RestController.
- Os controllers tratam requisições e respostas HTTP.
- Existem dois tipos de controllers:
  - Thin controllers (magros): limitam-se a receber a requisição e delegá-la a uma classe de serviço (service), sem processamento significativo.
  - Fat controllers (gordos): possuem mais atuação direta, interagindo com o Model e a View, mas ainda com foco em intermediação.
- A anotação @Controller é similar a @Component, instruindo o container a instanciar a classe.
- A anotação @RestController é uma especialização de @Controller que adiciona @ResponseBody, indicando que o controller responderá a verbos HTTP (GET, POST, PUT, DELETE) e retornará respostas no formato JSON.

> [!CAUTION] OBSERVAÇÃO: 
> - O controller não deve realizar processamento complexo; sua função principal é de intermediação.
> - @RestController é amplamente utilizado em APIs REST e é um tópico frequente em provas.

## 3. Fluxo de Requisição no Spring MVC
- O fluxo de uma requisição no Spring MVC segue os seguintes passos:
  1. A requisição é recebida pela Dispatcher Servlet, que atua como Front Controller, roteando a solicitação para o controller adequado.
  2. A Dispatcher Servlet consulta o Handler Mapping para determinar qual controller será utilizado.
  3. A Dispatcher Servlet invoca o controller selecionado.
  4. O controller processa a requisição e retorna um objeto ModelAndView, que contém a view e os dados a serem exibidos.
  5. A Dispatcher Servlet chama o View Resolver, que identifica a view a ser gerada (HTML, CSS, JavaScript).
  6. A view é criada e a resposta é enviada ao usuário.

> [!TIP] DICAS: 
> - A Dispatcher Servlet é o ponto central de entrada no Spring MVC, funcionando como um roteador.
> - O Handler Mapping e o View Resolver são componentes automatizados no Spring Boot, mas seu funcionamento é importante para entender o fluxo.

### 3.1 ModelAndView
- O objeto ModelAndView encapsula a view e os dados que serão exibidos.
- O Controller retorna esse objeto, que é processado pela Dispatcher Servlet.
- Na prática, a View Resolver utiliza as informações do ModelAndView para gerar a resposta final.

## 4. Anotações Principais no Controller
- As anotações são fundamentais para mapear requisições e parâmetros no Spring MVC.

### 4.1 @RestController
- Especialização de @Controller que adiciona @ResponseBody.
- Utilizada para serviços RESTful, retornando dados em formatos como JSON ou XML.
- Exemplo:
  ```java
  @RestController
  public class ApiController {
      @GetMapping("/dados")
      public Map<String, String> getData() {
          return Collections.singletonMap("chave", "valor");
      }
  }
  ```

### 4.2 @RequestMapping
- Mapeia requisições HTTP para métodos manipuladores em controladores.
- Pode ser especificado a nível de classe ou método.
- Atalhos específicos: @GetMapping, @PostMapping, @PutMapping, @DeleteMapping.

### 4.3 @RequestParam
- Acessa parâmetros de consulta (query parameters) em requisições GET.
- Pode definir um valor padrão caso o parâmetro não seja enviado.
- Exemplo:
  ```java
  @GetMapping("/saudacao")
  public String saudar(@RequestParam(defaultValue = "mundo") String nome) {
      return "Olá, " + nome;
  }
  ```

### 4.4 @PathVariable
- Captura valores de variáveis definidas em caminhos de URL.
- Utilizado em requisições com dados dinâmicos na URL.
- Exemplo:
  ```java
  @GetMapping("/usuario/{id}")
  public Usuario buscarUsuario(@PathVariable Long id) {
      // lógica para buscar o usuário
  }
  ```

### 4.5 @RequestBody
- Acessa o corpo da requisição (request body).
- Comum em requisições POST e PUT com dados JSON ou XML.
- Exemplo:
  ```java
  @PostMapping("/usuario")
  public ResponseEntity<String> criarUsuario(@RequestBody Usuario usuario) {
      // lógica para criar o usuário
      return ResponseEntity.ok("Usuário criado com sucesso!");
  }
  ```

> [!TIP] DICAS: 
> - @RequestParam é usado para parâmetros na URL (ex: ?nome=valor).
> - @PathVariable é usado para partes dinâmicas da URL (ex: /usuario/1).
> - @RequestBody é usado para dados enviados no corpo da requisição, geralmente em JSON.

> [!CAUTION] OBSERVAÇÃO: 
> - Em provas, é comum perguntar a diferença entre @RequestParam, @PathVariable e @RequestBody, bem como suas aplicações específicas.
> - A anotação @RestController é a mais utilizada em APIs REST e substitui o uso combinado de @Controller e @ResponseBody.

## 5. Resumo dos Componentes do Spring MVC
- O Spring MVC organiza a aplicação em torno do padrão MVC, com forte ênfase no desacoplamento e na coesão.
- A evolução para o Spring Boot trouxe auto-configuração e starters, reduzindo a necessidade de configuração manual.
- As camadas Model, View e Controller são bem definidas, com anotações específicas para cada função.
- O fluxo de requisição é centralizado na Dispatcher Servlet, que coordena o Handler Mapping, o Controller, o ModelAndView e o View Resolver.
- As anotações @RestController, @RequestMapping (e seus atalhos), @RequestParam, @PathVariable e @RequestBody são essenciais para o desenvolvimento de controladores no Spring MVC.

> [!TIP] DICAS: 
> - Revisar o fluxo da Dispatcher Servlet e as anotações é fundamental para provas de desenvolvimento web com Spring.
> - Entender a diferença entre o MVC clássico e o modelo de APIs REST é um ponto recorrente em concursos.