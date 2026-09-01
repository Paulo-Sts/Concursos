# Angular 2

## 1. Ciclo De Vida De Um Componente
- Refere-se às várias fases pelas quais o componente passa desde sua criação até sua destruição.
- O Angular fornece hooks de ciclo de vida, que são úteis para gerenciar recursos, responder a mudanças efetuadas nos dados e integrar com outras bibliotecas ou APIs.

| HOOK | QUANDO É CHAMADO | USO COMUM |
|------|------------------|-----------|
| ngOnChanges | Sempre que há uma mudança em um ou mais inputs do componente | Reagir a mudanças nos dados de entrada, como recalcular algo ou chamar uma API externa |
| ngOnInit | Uma vez, após a primeira inicialização das propriedades vinculadas do componente, mas antes de o componente ser renderizado | Ideal para inicializar dados no componente, como buscar dados de um serviço ou inicializar valores padrão |
| ngDoCheck | Após ngOnInit, e sempre que a detecção de mudança é executada | Implementar verificações de mudança personalizadas ou lógica adicional de detecção de mudanças |
| ngAfterContentInit | Uma vez que todo o conteúdo projetado foi inicializado | Útil quando o componente encapsula conteúdo que é passado de fora e que precisa ser manipulado ou verificado |
| ngAfterContentChecked | Após o ngAfterContentInit e cada subsequente execução de ngDoCheck, e após a verificação do conteúdo projetado | Para reagir às mudanças que ocorrem no conteúdo injetado dentro do componente |
| ngAfterViewInit | Uma vez que a view do componente e as views filhas foram inicializadas | Perfeito para manipulações DOM que dependem da existência da view, ou para integrações com plugins ou bibliotecas que precisam interagir diretamente com o DOM |
| ngAfterViewChecked | Após o ngAfterViewInit e cada subsequente ngAfterContentChecked | Para executar ações após a view do componente ter sido verificada pelas mudanças |
| ngOnDestroy | Imediatamente antes de o Angular destruir o componente | Essencial para limpeza, como desinscrever observáveis e desanexar event handlers para evitar vazamentos de memória |

> [!TIP] DICAS:
> - Como alguns hooks têm nomes sugestivos, caso alguma questão peça a função deles, é possível analisar o nome para ter uma ideia.

## 2. Data Binding
- Data Binding no Angular é um mecanismo para coordenar partes de um template (HTML) com partes de um componente (TypeScript).
- Ele permite a comunicação bidirecional entre o modelo e a view, facilitando a atualização dinâmica da interface de usuário com base nas mudanças de dados e vice-versa.

### 2.1 Interpolation – {{valor}}
- Mais comumente usado para inserir valores dinâmicos dentro do HTML.
- Exemplo: `<h1>{{ title }}</h1>` ⟶ Exibe o título do componente.

### 2.2 Property Binding – [propriedade]="valor"
- Vincula uma propriedade de um elemento DOM a uma propriedade do componente.
- Exemplo: `<img [src]="userImageUrl">` ⟶ Vincula a propriedade 'src' da tag img ao valor de 'userImageUrl' no componente.

### 2.3 Event Binding – (evento)="handler()"
- Vincula eventos do DOM, como cliques e toques, a métodos do componente.
- Exemplo: `<button (click)="save()">Salvar</button>` ⟶ Chama o método 'save' quando o botão é clicado.

### 2.4 Two-Way Binding – [(ngModel)]
- Permite que alterações no modelo de dados e na interface do usuário sejam sincronizadas.
- Quando os dados no modelo mudam, a interface do usuário reflete essa mudança.
- Quando a interface do usuário é alterada (ex.: através de uma entrada do usuário), o modelo de dados no componente é atualizado.
- Exemplo:
  ```
  <!-- No template HTML -->
  <input [(ngModel)]="username">
  <p>Nome de usuário: {{ username }}</p>
  ```

> [!TIP] DICAS:
> - A comunicação bidirecional é chamada de two-way data binding.
> - O two-way binding tem alteração sincronizada entre o modelo e a view.

## 3. Diretivas
- Diretivas no Angular são instruções que podem ser adicionadas ao HTML e determinam como controlar ou modificar elementos na página.
- Elas são como comandos especiais que se colocam em partes do código HTML para adicionar comportamentos ou estilos específicos a esses elementos.
- A tag possui um nome específico, que é definido no selector.

### 3.1 Diretivas Estruturais
- São utilizadas para modificar a estrutura do DOM adicionando, removendo ou manipulando elementos.
- Elas são responsáveis por alterar o layout ao renderizar condicionalmente blocos de HTML.

#### 3.1.1 *ngIf
- Diretiva que, condicionalmente, inclui um bloco de HTML no DOM, baseado na verdade do valor da expressão.
- Exemplo: `<div *ngIf="user.isLoggedIn">Bem-vindo, {{ user.name }}!</div>` ⟶ Se `user.isLoggedIn` for `true`, o bloco `<div>` será renderizado; se não, será removido do DOM.

#### 3.1.2 *ngFor
- Diretiva que repete um elemento HTML para cada item em uma lista.
- Exemplo: `<li *ngFor="let item of items">{{ item }}</li>` ⟶ `<li>` é repetido para cada item na lista `items`.

### 3.2 Diretivas de Atributos
- São utilizadas para alterar a aparência ou o comportamento de elementos DOM.
- Elas não modificam a estrutura, mas sim propriedades de elementos existentes.

#### 3.2.1 [ngStyle]
- Diretiva que permite definir estilos CSS dinamicamente.
- Exemplo: `<div [ngStyle]="{'font-style': isItalic ? 'italic' : 'normal'}">Texto estilizado</div>` ⟶ Aplica um estilo de fonte itálica se `isItalic` for `true`.

#### 3.2.2 [ngClass]
- Diretiva que permite adicionar ou remover classes CSS de um elemento de forma condicional.
- Exemplo: `<div [ngClass]="{active: isActive}">Ativo</div>` ⟶ A classe `active` é adicionada ao `<div>` se `isActive` for `true`.

## 4. Pipes
- Pipe é uma maneira de escrever valores de exibição, e permite ao desenvolvedor encapsular a lógica de formatação de dados dentro de uma estrutura reutilizável e fácil de gerenciar.
- É comum em sites, em coisas que aparecem em vários momentos, como a seta que leva o usuário à página anterior.
- Pipes podem ser utilizados para transformações comuns como datas, números e textos, facilitando a internacionalização e a personalização de apresentação sem alterar os dados originais.
- O símbolo `|` (pipe) em uma expressão Angular direciona o valor do objeto à esquerda e o direciona como entrada para o da direita.

### 4.1 Pipes Nativos
- DatePipe: formata uma data de acordo com o locale.
- UpperCasePipe: transforma o texto em maiúsculas.
- LowerCasePipe: transforma o texto em minúsculas.
- CurrencyPipe: formata um número como moeda.
- DecimalPipe: formata um número como um decimal.
- PercentPipe: formata um número como uma porcentagem.

### 4.2 Pipe Customizado
- Permite criar lógicas de transformação personalizadas.
- Exemplo de pipe que inverte a ordem das letras:
  ```
  import { Pipe, PipeTransform } from '@angular/core';
  
  @Pipe({
    name: 'reverse'
  })
  export class ReversePipe implements PipeTransform {
    transform(value: string): string {
      return value.split('').reverse().join('');
    }
  }
  ```
- Explicação:
  - `@Pipe` – decorador.
  - Propriedade `name: 'reverse'` – define o nome do pipe para uso no template.
  - Exportação da classe – implementa o `PipeTransform`.
  - `split` – separa as letras.
  - `reverse` – inverte a ordem.
  - `join` – junta as letras novamente.
- Uso no template:
  ```
  <p>{{ 'hello' | reverse }}</p> <!-- Exibe "olleh" -->
  ```

> [!TIP] DICAS:
> - O JavaScript possui diversos métodos já prontos que podem ser utilizados dentro de pipes customizados.