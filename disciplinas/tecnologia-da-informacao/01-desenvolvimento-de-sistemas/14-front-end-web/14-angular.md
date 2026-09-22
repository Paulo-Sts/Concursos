# Angular

## 1. Angular (Angular 2+)
- Framework de desenvolvimento criado pelo Google.
- Projetado principalmente para a construção de Single Page Applications (SPAs).
- Permite criar aplicações web interativas e dinâmicas utilizando arquitetura baseada em componentes.
- Suporta programação reativa e ferramentas avançadas de desenvolvimento.
- Integra práticas essenciais para garantir qualidade e durabilidade do software em ambientes de produção, como testes unitários e end-to-end.

> [!TIP] DICAS:
> - SPA (Single Page Application) é um site com uma única página onde os componentes são alterados conforme a interação do usuário.
> - Programação reativa é a capacidade de obter uma resposta imediata da aplicação diante de alguma ação.
> - Teste unitário: divisão da aplicação em partes e teste de cada uma em ambientes isolados.
> - Teste end-to-end: testagem do início ao fim da aplicação.

## 2. AngularJS x Angular

### 2.1 Lançamento
- AngularJS: 2010.
- Angular: 2016.

### 2.2 Linguagem
- AngularJS: JavaScript puro.
- Angular: TypeScript.

> [!TIP] DICAS:
> - TypeScript é um superset do JavaScript.
> - Diferença principal: tipagem.
>   - JavaScript: tipagem dinâmica (não é necessário determinar o tipo da variável, usa-se let/const/var).
>   - TypeScript: exige determinação do tipo da variável.

### 2.3 Arquitetura
- AngularJS: MVC (Model-View-Controller).
  - Model: lógica de negócio e especificações do site.
  - View: visualização do usuário.
  - Controller: mediação entre Model e View.
- Angular: Serviços e componentes.
  - Serviços: funcionalidades do site.
  - Componentes: responsáveis pela interface do usuário.

> [!CAUTION] OBSERVAÇÃO:
> - Ainda há questões de concurso que cobram assuntos relacionados ao AngularJS.

## 3. Arquitetura do Angular

### 3.1 Componentes
- Blocos de construção que controlam as views.
- Consistem em:
  - Arquivo de template HTML.
  - Classe para a lógica.
  - Opcionalmente, arquivos CSS para estilização.
- Exemplo de template HTML (app.component.html):
```html
<h1>{{ title }}</h1>
```

> [!TIP] DICAS:
> - A sintaxe {{ title }} entre chaves duplas é chamada de interpolação.
> - Interpolação permite exibir valores dinâmicos da classe no template.

- Exemplo de componente (app.component.ts):
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Minha Aplicação Angular';
}
```

- Estrutura do componente:
  - Importação do decorador Component do pacote @angular/core.
  - Decoradores: funções especiais que agregam metadados a uma classe.
  - @Component: declaração do decorador com propriedades:
    - selector: define o nome do componente para uso no HTML (ex: 'app-root').
    - templateUrl: caminho para o arquivo HTML.
    - styleUrls: array com caminhos para arquivos CSS.
  - Exportação da classe AppComponent com definição de propriedades.

### 3.2 Módulos
- Definem um contexto de compilação para um grupo de componentes.
- Cada aplicação tem pelo menos um módulo raiz.
- Exemplo de módulo (app.module.ts):
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

- Estrutura do módulo:
  - NgModule: decorador que define uma classe TypeScript como módulo.
  - BrowserModule: módulo necessário para aplicações rodarem em navegadores.
  - Propriedades do @NgModule:
    - declarations: lista de componentes, diretivas e pipes do módulo.
    - imports: importa outros módulos necessários (ex: BrowserModule).
    - providers: define provedores de serviços (vazio no exemplo).
    - bootstrap: componente raiz a ser instanciado quando o módulo for carregado.

### 3.3 Serviços
- Classes que encapsulam regras de negócio não diretamente ligadas à visualização (views).
- Todas as verificações são feitas dentro dos serviços, sem exposição ao usuário.

### 3.4 Injeção de Dependências (DI)
- Padrão de design que permite que as classes recebam suas dependências de fontes externas.
- Evita que as classes criem suas próprias dependências.
- Facilita a separação de responsabilidades, testes e manutenção do código.
- Exemplo de serviço com injeção de dependência (log.service.ts):
```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class LogService {
  log(message: string) {
    console.log(message);
  }
}
```

- Estrutura do serviço:
  - Injectable: decorador do pacote @angular/core que define a classe como serviço.
  - providedIn: 'root' – configuração disponibilizada em toda a aplicação.
  - Classe LogService exportada com método log que imprime mensagem no console.

> [!CAUTION] OBSERVAÇÃO:
> - O elemento app-root (selector do componente raiz) é o primeiro componente carregado e funciona como contêiner para os demais componentes.