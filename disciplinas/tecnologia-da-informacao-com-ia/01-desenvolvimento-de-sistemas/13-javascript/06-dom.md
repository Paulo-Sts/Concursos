# Dom

## 1. O Que É O Dom
- O Document Object Model (DOM) é uma interface de programação para documentos HTML ou XML.
- Ele representa a estrutura da página como uma árvore de objetos, em que cada elemento HTML é um nó.
- Todos os elementos, atributos (como id, class e estilização) e tags são considerados nós.
- Essa representação permite manipular dinamicamente o conteúdo, a estrutura e o estilo da página por meio de JavaScript.

## 2. Interação Entre Html E Javascript
- A interação pode ser feita diretamente na página com a tag `<script>` ou vinculando um arquivo externo (ex.: `<script src="script.js"></script>`).
- Geralmente, o script é colocado no final do corpo da página (`</body>`) para garantir que os elementos HTML já tenham sido carregados.

### Exemplo de estrutura básica
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Seleção de Elementos HTML</title>
</head>
<body>
  <div id="conteudo">
    <h1>Seleção de Elementos</h1>
    <p id="paragrafo">Este é um parágrafo de exemplo.</p>
    <button class="botao">Botão 1</button>
    <button class="botao">Botão 2</button>
  </div>
  <script src="script.js"></script>
</body>
</html>
```

> [!TIP] DICAS: 
> - O HTML puro não é interativo; é necessário o JavaScript para manipular o DOM e tornar a página dinâmica.
> - Posicionar o `<script>` no final do corpo evita erros de elementos não encontrados.

## 3. Métodos De Seleção De Elementos
- Para manipular elementos, primeiro é preciso selecioná-los.
- Os principais métodos de seleção no DOM são:
  - `getElementById`
  - `getElementsByClassName`
  - `getElementsByTagName`
  - `querySelector`
  - `querySelectorAll`

### 3.1 getElementById
- Seleciona um único elemento pelo seu atributo `id`.
- O `id` deve ser único na página.
- Retorna o elemento diretamente (não uma lista).

#### Exemplo
```html
<body>
  <div id="uniqueElement">Texto original</div>
  <button onclick="changeTextById()">Mudar Texto</button>
  <script>
    function changeTextById() {
      const element = document.getElementById("uniqueElement");
      element.textContent = "Texto alterado pelo getElementById!";
    }
  </script>
</body>
```

- Explicação:
  - O botão possui `onclick` que chama a função `changeTextById`.
  - A função usa `document.getElementById("uniqueElement")` para obter o elemento com o ID especificado.
  - O conteúdo do elemento é alterado com a propriedade `textContent`.

> [!CAUTION] OBSERVAÇÃO: 
> - IDs são únicos; portanto, esse método só pode ser usado para elementos individuais.

### 3.2 getElementsByClassName
- Seleciona todos os elementos que possuem uma determinada classe.
- Retorna uma coleção (HTMLCollection) que pode ser percorrida com loops.
- Permite alterar múltiplos elementos simultaneamente.

#### Exemplo
- Três divs com a classe `changeStyle` e um botão que as altera.
- Funcionalidade: ao clicar no botão, todos os elementos com a classe `changeStyle` têm a cor do texto alterada para vermelho.

```javascript
function changeStyle() {
  const elements = document.getElementsByClassName("changeStyle");
  for (let element of elements) {
    element.style.color = "red";
  }
}
```

- Explicação:
  - `document.getElementsByClassName("changeStyle")` retorna todos os elementos com essa classe.
  - O loop `for of` percorre a coleção e modifica a propriedade `style.color` de cada um.

> [!TIP] DICAS: 
> - Use classe para alterar vários elementos de uma vez.
> - Se quiser alterar apenas um, prefira `getElementById`.

### 3.3 getElementsByTagName
- Seleciona todos os elementos com uma determinada tag (ex.: `p`, `div`).
- Retorna uma coleção (HTMLCollection).
- Deve ser usado com cuidado, pois pode afetar muitos elementos.

#### Exemplo
- Três parágrafos e um botão que altera o texto de todos eles.

```html
<body>
  <p>Parágrafo 1</p>
  <p>Parágrafo 2</p>
  <p>Parágrafo 3</p>
  <button onclick="changeTextByTag()">Mudar Texto dos Parágrafos</button>
  <script>
    function changeTextByTag() {
      const elements = document.getElementsByTagName("p");
      for (let element of elements) {
        element.textContent = "Texto alterado pelo getElementsByTagName!";
      }
    }
  </script>
</body>
```

- Explicação:
  - `document.getElementsByTagName("p")` retorna todos os elementos `<p>`.
  - O loop altera o `textContent` de cada parágrafo.

> [!CAUTION] OBSERVAÇÃO: 
> - Esse método é generalista. Em projetos grandes, pode afetar elementos indesejados se houver muitos parágrafos.

### 3.4 querySelector
- Retorna o primeiro elemento que corresponde ao seletor CSS passado como argumento.
- Suporta seletores de classe (`.classe`), ID (`#id`), tag (`tag`), entre outros.
- Útil quando se quer alterar apenas a primeira ocorrência.

#### Exemplo
```html
<body>
  <div class="changeMe">Primeiro Elemento</div>
  <div class="changeMe">Segundo Elemento</div>
  <div class="changeMe">Terceiro Elemento</div>
  <button onclick="changeByQuerySelector()">Mudar Primeiro Elemento</button>
  <script>
    function changeByQuerySelector() {
      const firstElement = document.querySelector(".changeMe");
      firstElement.textContent = "Texto alterado pelo querySelector!";
      firstElement.style.color = "blue";
    }
  </script>
</body>
```

- Explicação:
  - `document.querySelector(".changeMe")` seleciona a primeira div com a classe `changeMe`.
  - Apenas o primeiro elemento é alterado (texto e cor).

> [!TIP] DICAS: 
> - Use `querySelector` para selecionar o primeiro elemento de um grupo.
> - O seletor pode ser qualquer seletor CSS válido (ex.: `"#id"`, `"div.classe"`).

### 3.5 querySelectorAll
- Retorna todos os elementos que correspondem ao seletor CSS.
- Retorna uma NodeList (estática), que pode ser percorrida com `forEach` ou loops.

#### Exemplo
```html
<body>
  <div class="multipleItems">Item 1</div>
  <div class="multipleItems">Item 2</div>
  <div class="multipleItems">Item 3</div>
  <button onclick="changeTextByQuerySelectorAll()">Mudar Texto de Todos os Itens</button>
  <script>
    function changeTextByQuerySelectorAll() {
      const elements = document.querySelectorAll(".multipleItems");
      elements.forEach((element) => {
        element.textContent = "Texto alterado pelo querySelectorAll!";
      });
    }
  </script>
</body>
```

- Explicação:
  - `document.querySelectorAll(".multipleItems")` retorna todos os elementos com essa classe.
  - O método `forEach` é usado para iterar e alterar o `textContent` de cada um.

> [!CAUTION] OBSERVAÇÃO: 
> - `querySelectorAll` retorna uma NodeList, que possui o método `forEach` (diferente de HTMLCollection).
> - Para HTMLCollections (como as retornadas por `getElementsByClassName`), é necessário usar `for of` ou converter para array.

### Comparação entre os métodos
| MÉTODO | RETORNO | SELECIONA | USO RECOMENDADO |
|--------|---------|-----------|-----------------|
| getElementById | Elemento único | Por ID | Elemento único com ID único |
| getElementsByClassName | HTMLCollection (viva) | Por classe | Múltiplos elementos com mesma classe |
| getElementsByTagName | HTMLCollection (viva) | Por tag | Múltiplos elementos de mesma tag |
| querySelector | Primeiro elemento encontrado | Seletor CSS (qualquer) | Primeira ocorrência de um seletor |
| querySelectorAll | NodeList (estática) | Seletor CSS (qualquer) | Todos os elementos que correspondem ao seletor |

> [!TIP] DICAS: 
> - Prefira `querySelector` e `querySelectorAll` para maior flexibilidade com seletores CSS.
> - `getElementById` é mais performático para seleção por ID.
> - Ao usar classes, se precisar de todos os elementos, use `getElementsByClassName` ou `querySelectorAll`.
> - Lembre-se: `querySelector` só altera o primeiro; `querySelectorAll` altera todos.