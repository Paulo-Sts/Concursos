# Framework Spring MVC 5

## 1. Padrão MVC no Spring Framework
- O Spring MVC é um framework que implementa o padrão de arquitetura MVC (Model-View-Controller) para desenvolvimento de aplicações web em Java.
- O padrão MVC separa a aplicação em três camadas distintas, promovendo alta coesão e baixo acoplamento.
- O MVC pode ser utilizado em diferentes plataformas, como aplicações web, mobile e desktop.

### 1.1 DispatcherServlet
- O DispatcherServlet é uma classe concreta que segue o padrão de projeto Front Controller.
- A classe estende HttpServlet, garantindo sua funcionalidade como servlet no contexto de aplicações web Spring.
- O Front Controller direciona todas as requisições recebidas para as classes responsáveis por tratá-las.

### 1.2 Anotação @Controller
- Classes marcadas com @Controller verificam a URL solicitada por meio da anotação @RequestMapping.
- @RequestMapping pode ser utilizada tanto no nível da classe quanto no nível dos métodos.
- A anotação estabelece uma relação clara entre a URL requisitada e a lógica que deve ser executada.

### 1.3 Anotação @RestController
- Utilizada para marcar uma classe como controlador em serviços web RESTful.
- Diferencia-se do @Controller tradicional, pois cada método retorna um objeto de domínio em vez de uma exibição.
- Por padrão, o @RestController fornece uma resposta em formato JSON.

### 1.4 Anotações para Mapeamento de Requisições
- @GetMapping: mapeia requisições HTTP GET para o método especificado.
- Exemplo: @GetMapping("/dados") garante que requisições GET para /dados sejam tratadas pelo método dados().
- @PathVariable: extrai valores do caminho da URL e os passa como argumentos para o método do controlador.
- @RequestParam: obtém parâmetros da query string (parâmetros após o símbolo ? na URL).
- @RequestHeader: captura valores dos cabeçalhos da requisição HTTP.

> [!TIP] DICAS:
> - O @RestController é a anotação correta para RESTful, não existem anotações como @RestfulController, @RestfulMapping, @RestApplicationController ou @RequestController.
> - Para obter valores da URL, utilize @PathVariable; para parâmetros de query string, utilize @RequestParam.

### 1.5 Parâmetros com @RequestParam
- O argumento defaultValue define um valor padrão para o parâmetro quando ele não é fornecido na requisição.
- O argumento required define se o parâmetro é obrigatório ou não.
- O argumento value define o nome do parâmetro da solicitação HTTP.

> [!CAUTION] OBSERVAÇÃO:
> - O argumento defaultValue elimina a necessidade de o parâmetro ser obrigatório.
> - Required não aceita estruturas condicionais ou expressões, apenas valores booleanos.

## 2. Gerenciamento de Transações
- O Spring Framework possui suporte nativo para gerenciamento de transações.
- Não há necessidade de recorrer a bibliotecas externas para essa finalidade.

## 3. Segurança no Spring
- O Spring Security é parte do próprio Spring Framework e oferece solução completa para segurança da informação.
- Utiliza filtros no contexto de desenvolvimento web, invocados em todas as requisições antes de serem encaminhadas aos controladores.
- Permite implementação de mecanismos de autenticação e autorização.

## 4. Reutilização de Código
- A reutilização de código é uma prática essencial no desenvolvimento de software.
- Favorece a manutenção e a escalabilidade da aplicação.
- A escalabilidade não é influenciada negativamente pela reutilização de código.