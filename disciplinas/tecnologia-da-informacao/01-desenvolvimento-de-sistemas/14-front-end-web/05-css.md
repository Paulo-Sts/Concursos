# CSS3 – Seletores

## 1. CSS (Cascading Style Sheets)
- É uma linguagem de estilo utilizada para a apresentação de documentos HTML e XML.
- Permite controlar cores, layout, fontes e adaptar a apresentação para diferentes dispositivos (responsividade).

> [!TIP] DICAS: 
> - CSS significa Folhas de Estilo em Cascata.
> - É possível criar páginas responsivas utilizando CSS.

## 2. Formas de Inserir CSS

### 2.1 CSS Definido no HTML
- Utiliza a tag `<style>` dentro do cabeçalho (`<head>`).
- A tag abre com `<style>` e fecha com `</style>`.
- Exemplo:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    h1 {
      color: red;
      font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
      background-color: aquamarine;
    }
  </style>
</head>
<body>
  <h1>Exemplo de página HTML com estilização</h1>
</body>
</html>
```

### 2.2 CSS em Arquivo Separado
- O CSS pode ser definido em um arquivo externo com extensão `.css`.
- No HTML, utiliza-se a tag `<link>` dentro do `<head>` para referenciar o arquivo.
- Atributos do `<link>`:
  - `rel="stylesheet"`: define a relação como folha de estilos.
  - `href="caminho/do/seu/arquivo.css"`: caminho do arquivo CSS.
- Caso o arquivo esteja na mesma pasta, usa-se `./` antes do nome do arquivo.
- Exemplo:
```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meu Site</title>
  <link rel="stylesheet" href="caminho/do/seu/arquivo.css">
</head>
<body>
  <!-- Conteúdo do site aqui -->
</body>
</html>
```

> [!CAUTION] OBSERVAÇÃO: 
> - Evitar colocar estilização diretamente no `<body>`, pois a página pode carregar antes da aplicação dos estilos.

## 3. Seletores CSS
- Seletores são fundamentais para especificar quais elementos serão estilizados.
- Permitem aplicar um mesmo estilo a vários elementos ou estilos específicos a elementos únicos.

### 3.1 Seletor de ID (`#id`)
- Estiliza um único elemento.
- No HTML, utiliza-se o atributo `id`.
- No CSS, representa-se com `#` (hashtag).
- Exemplo:
```html
<!-- HTML -->
<div id="container">
  <p>Este é um parágrafo dentro de uma div com ID "container".</p>
</div>
```
```css
/* CSS */
#container {
  background-color: lightblue;
  padding: 20px;
}
```
- O `padding` define o espaçamento interno para o texto não ficar colado nas bordas.

### 3.2 Seletor de Classe (`.classe`)
- Estiliza um ou mais elementos.
- Utilizado quando vários elementos compartilham o mesmo estilo (ex: páginas de notícias).
- No HTML, utiliza-se o atributo `class`.
- No CSS, representa-se com `.` (ponto).
- Exemplo:
```html
<!-- HTML -->
<p class="destaque">Este parágrafo está em destaque!</p>
```
```css
/* CSS */
.destaque {
  background-color: yellow;
  border: 2px solid orange;
}
```

### 3.3 Seletor de Elemento
- Estiliza todos os elementos de uma determinada tag.
- Exemplo:
```html
<!-- HTML -->
<p>Este é um parágrafo.</p>
<p>Este é outro parágrafo.</p>
```
```css
/* CSS */
p {
  color: blue;
}
```

### 3.4 Seletor Múltiplo (`elemento, elemento`)
- Seleciona mais de um elemento para aplicar os mesmos estilos.
- Exemplo:
```html
<!-- HTML -->
<h1>Título</h1>
<h2>Subtítulo</h2>
```
```css
/* CSS */
h1, h2 {
  color: green;
}
```

### 3.5 Seletor Filho Direto (`elemento > elemento`)
- Seleciona um elemento que é filho direto de outro.
- Exemplo:
```html
<!-- HTML -->
<div class="container">
  <div id="aninhada">
    <p>Parágrafo dentro de uma div aninhada.</p>
  </div>
  <p>Parágrafo fora da div aninhada.</p>
</div>
```
```css
/* CSS */
.container > p {
  color: blue;
}
```
- No exemplo acima, apenas o parágrafo que é filho direto da div com classe "container" será afetado. O parágrafo dentro da div aninhada não será estilizado.

### 3.6 Seletor de Irmão Adjacente (`elemento + elemento`)
- Seleciona um elemento imediatamente precedido por outro elemento específico.
- Exemplo:
```html
<!-- HTML -->
<h1>Título 1</h1>
<p>Parágrafo 1</p>
<p>Parágrafo 2</p>
<h2>Título 2</h2>
<p>Parágrafo 3</p>
```
```css
/* CSS */
h1 + p {
  color: red;
}
```
- Apenas o "Parágrafo 1" será afetado, pois é o único imediatamente após um `<h1>`.

### 3.7 Seletor de Irmãos Gerais (`elemento ~ elemento`)
- Seleciona todos os elementos que são irmãos do primeiro elemento e que vêm após ele.
- Exemplo:
```html
<!-- HTML -->
<span>Primeiro parágrafo.</span>
<p>Algum texto aqui.</p>
<p>Segundo parágrafo.</p>
<p>Terceiro parágrafo.</p>
```
```css
/* CSS */
span ~ p {
  color: red;
}
```
- Todos os parágrafos após o `<span>` serão vermelhos.

> [!CAUTION] OBSERVAÇÃO: 
> - Diferença entre `+` e `~`: `+` seleciona apenas o primeiro irmão imediato; `~` seleciona todos os irmãos subsequentes.

### 3.8 Pseudo-classe `:hover`
- Aplica estilos quando o usuário posiciona o cursor do mouse sobre o elemento.
- Exemplo:
```html
<!-- HTML -->
<button>Clique aqui</button>
```
```css
/* CSS */
button {
  background-color: white;
  color: black;
}
button:hover {
  background-color: black;
  color: white;
}
```

> [!TIP] DICAS: 
> - `:hover` é muito utilizado para feedback visual em botões e links.
> - Pode alterar cor, tamanho, borda, cursor (mão), entre outros.

### 3.9 Pseudo-classe `:nth-child(n)`
- Seleciona elementos com base em sua posição em relação a todos os elementos filhos do mesmo pai.
- Pode usar valores como:
  - `odd`: elementos ímpares.
  - `even`: elementos pares.
  - `n`: variável que aplica a todos os elementos.
- Exemplo:
```html
<!-- HTML -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
```css
/* CSS */
li:nth-child(odd) {
  background-color: lightgray;
}
```
- O `:nth-child` considera todos os elementos filhos, independentemente do tipo.
- Exemplo com tipos diferentes:
```html
<!-- HTML -->
<div>
  <h1>Título</h1>
  <h2>Subtítulo</h2>
  <p>Parágrafo</p>
</div>
```
```css
/* CSS */
:nth-child(odd) {
  background-color: lightgray;
}
```
- Neste caso, `<h1>` e `<p>` serão afetados (posições 1 e 3), enquanto `<h2>` (posição 2) não.

### 3.10 Pseudo-classe `:nth-of-type(n)`
- Seleciona elementos com base em sua posição entre elementos do mesmo tipo dentro do pai.
- O tipo do elemento é essencial para a seleção.
- Exemplo:
```html
<!-- HTML -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
```css
/* CSS */
li:nth-of-type(2) {
  color: blue;
}
```
- Apenas o segundo `<li>` será estilizado (Item 2).

| PSEUDO-CLASSE | SELEÇÃO |
|---------------|---------|
| `:nth-child(n)` | Posição em relação a todos os elementos filhos do pai |
| `:nth-of-type(n)` | Posição em relação aos elementos irmãos do mesmo tipo |

> [!CAUTION] OBSERVAÇÃO: 
> - `:nth-child` considera todos os filhos, independente do tipo.
> - `:nth-of-type` considera apenas filhos do mesmo tipo.
> - Exemplo prático: em uma lista com `<li>`, ambos podem parecer iguais, mas com elementos mistos (`<h1>`, `<p>`, etc.), a diferença é crucial.

## 4. Comentários em CSS
- Comentários são usados para explicar ou documentar o código.
- Em CSS, iniciam com `/*` e terminam com `*/`.
- Exemplo:
```css
/* Este é um comentário em CSS */
h1 {
  color: red;
}
```

> [!CAUTION] OBSERVAÇÃO: 
> - Em HTML, os comentários iniciam com `<!--` e terminam com `-->`.
> - Em CSS, o padrão é `/* ... */`.

## 5. Considerações Finais sobre Seletores
- Seletores são essenciais para aplicar estilos de forma precisa e eficiente.
- A combinação de diferentes seletores permite criar layouts complexos e responsivos.
- O conhecimento aprofundado sobre pseudo-classes como `:hover`, `:nth-child` e `:nth-of-type` é fundamental para estilizações dinâmicas.