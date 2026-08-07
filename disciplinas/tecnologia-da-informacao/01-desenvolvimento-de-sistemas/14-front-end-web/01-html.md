# Linguagem de Marcação de Hipertexto (Html)

## 1. Conceitos Fundamentais do Html
- O HTML é a linguagem padrão para criar e estruturar conteúdo na web.
- O termo é um acrônimo para Hyper Text Markup Language, que em português significa Linguagem de Marcação de Hipertexto.
- A linguagem é formada por marcações, chamadas de tags.
- As tags permitem a inclusão de diversos elementos, como texto, imagens, links, formulários e botões.

### 1.1 Tipos de Tags
- As tags em HTML se dividem em dois tipos principais, quanto à sua estrutura.

#### 1.1.1 Tags de Abertura e Fechamento
- A maioria das tags segue o formato de abertura `<tag>` e fechamento `</tag>`.
- O conteúdo afetado pela tag é colocado entre essas duas marcações.
- Exemplo:
```html
<p>Este é um parágrafo de texto.</p>
```
- Neste exemplo, a tag `<p>` é aberta, o conteúdo é inserido e a tag é fechada com `</p>`.

#### 1.1.2 Tags Vazias ou Autofechamento (Self-Closing)
- São utilizadas para indicar que a tag não possui um conteúdo interno, não necessitando de uma tag de fechamento separada.
- São fechadas dentro da própria tag usando uma barra, como `<tag/>`.
- Exemplo:
```html
<img src="imagem.jpg" alt="Descrição da imagem" />
```
- A tag `<img>` é um exemplo clássico, onde as informações e atributos são inseridos diretamente nela, não havendo conteúdo entre uma abertura e um fechamento.

### 1.2 Cabeçalhos
- São elementos utilizados para definir títulos e subtítulos em uma página web.
- São marcados com as tags de 1 a 6: `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>` e `<h6>`.
- Cada tag representa o tamanho e o nível de importância ou hierarquia, sendo `<h1>` o mais importante e `<h6>` o menos importante.
- A tag `<h1>`, por exemplo, pode ser utilizada para a manchete de um site de notícias, pois é o maior título e o mais relevante.

### 1.3 Tags de Comentário
- Servem para adicionar informações que não serão exibidas no navegador.
- Os comentários em HTML são definidos entre `<!--` e `-->`.
- Exemplo:
```html
<!-- Este é um comentário em HTML. --> <h1>Este é um título que será exibido.</h1>
```
- O comentário não aparecerá na página, mas o título `<h1>` será exibido normalmente.

## 2. Estrutura Básica de um Documento Html
- A estrutura básica de um documento HTML é composta por elementos que definem o tipo de documento, as informações sobre a página e o conteúdo a ser exibido.

### 2.1 Elementos da Estrutura
- A estrutura é composta por tags que organizam o documento.

#### 2.1.1 Doctype
- A declaração `<!DOCTYPE html>` serve para indicar qual versão do HTML será utilizada.
- Sempre indicará a versão mais recente.
- A versão mais recente é a HTML5, estabelecida em 2014 e ainda utilizada.

> [!TIP] DICAS: 
> - O HTML5 é a versão mais recente do padrão HTML, sendo um tópico recorrente em provas.

#### 2.1.2 Tag `<html>`
- Possui abertura e fechamento e serve para indicar que tudo que estiver dentro dela é informação HTML.
- O atributo `lang` serve para indicar em qual idioma está a página.
  - Exemplos: `lang="en"` para inglês e `lang="pt-BR"` para português brasileiro.

#### 2.1.3 Tag `<head>`
- É o cabeçalho da página, utilizado para inserir metadados, ou seja, informações sobre a página.
- Os metadados não são exibidos diretamente na página, mas fornecem informações importantes para o navegador e mecanismos de busca.
- Exemplo de metadados:
  - `<meta charset="UTF-8">`: Indica quais caracteres serão utilizados. O padrão UTF-8 é usado no Ocidente para português, inglês, etc.
  - `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Indica que o conteúdo da página deve ser ajustado para se adaptar a diferentes dispositivos (celular, computador).

#### 2.1.4 Tag `<title>`
- Serve para indicar o nome que estará na guia do navegador.
- É o texto que aparece na parte superior da aba do site acessado.

#### 2.1.5 Tag `<body>`
- Serve para inserir todo o conteúdo da página que será exibido visualmente.
- Todo o conteúdo relacionado à página (texto, imagens, links) estará dentro dessa tag.

> [!TIP] DICAS: 
> - A tag `<head>` contém informações sobre a página, enquanto a tag `<body>` contém o conteúdo que o usuário vê.

## 3. Tipos de Listas
- As listas são usadas para organizar e estruturar informações.
- Existem três tipos principais de listas em HTML.

### 3.1 Listas Ordenadas (`<ol>`)
- São usadas para representar itens que têm uma ordem específica.
- Os itens são marcados pela tag `<li>` (List Item).
- Por padrão, a ordem é numérica, mas pode ser alterada.
- Exemplo:
```html
<ol>
  <li>Primeiro item</li>
  <li>Segundo item</li>
  <li>Terceiro item</li>
</ol>
```
- A saída será uma lista numerada de 1 a 3.

#### 3.1.1 Atributos de Listas Ordenadas
- Os atributos permitem personalizar a numeração.

##### 3.1.1.1 Type
- Especifica o tipo de marcador a ser usado.
- Os valores possíveis são:

| TIPO | DESCRIÇÃO | EXEMPLO |
|------|-----------|---------|
| "1" | Números arábicos | 1, 2, 3 |
| "A" | Letras maiúsculas | A, B, C |
| "a" | Letras minúsculas | a, b, c |
| "I" | Números romanos maiúsculos | I, II, III |
| "i" | Números romanos minúsculos | i, ii, iii |

- Exemplo com type "A":
```html
<ol type="A">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>
```
- A saída será: A. Item 1 / B. Item 2 / C. Item 3.

##### 3.1.1.2 Start
- Permite especificar o valor inicial para a contagem dos itens.
- Exemplo:
```html
<ol start="10">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>
```
- A saída será: 10. Item 1 / 11. Item 2 / 12. Item 3.

##### 3.1.1.3 Reversed
- Inverte a ordem dos itens na lista.
- Exemplo:
```html
<ol reversed>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>
```
- A saída será: 3. Item 1 / 2. Item 2 / 1. Item 3.

### 3.2 Listas Não Ordenadas (`<ul>`)
- Representa uma lista que tem itens sem ordem rígida.
- Cada item é precedido por um símbolo, que por padrão é um círculo preto.
- Os itens também são marcados pela tag `<li>`.
- Exemplo:
```html
<ul>
  <li>Primeiro item</li>
  <li>Segundo item</li>
  <li>Terceiro item</li>
</ul>
```
- A saída será:
  - Primeiro item.
  - Segundo item.
  - Terceiro item.

### 3.3 Listas de Definição (`<dl>`)
- Utilizadas para agrupar termos e suas respectivas definições.
- Composta por duas tags:
  - `<dt>` (Definition Term): Para o título do item.
  - `<dd>` (Definition Description): Para a explicação ou descrição do termo.
- Exemplo:
```html
<dl>
  <dt>HTML</dt>
  <dd>Linguagem de Marcação de Hipertexto, usada na construção de páginas web.</dd>
  <dt>CSS</dt>
  <dd>Folhas de Estilo em Cascata, utilizadas para estilizar elementos HTML.</dd>
  <dt>JavaScript</dt>
  <dd>Linguagem de programação para tornar páginas web interativas.</dd>
</dl>
```
- A saída terá cada termo (`<dt>`) seguido por sua definição (`<dd>`).

> [!CAUTION] OBSERVAÇÃO: 
> - A numeração em listas ordenadas pode ser modificada. O atributo `start` define o ponto de partida, independente do `type`. Em provas, atente-se para a combinação destes dois atributos.
> - A tag `<meta>` está no `<head>` e não no `<body>`, pois fornece informações sobre a página, e não conteúdo visual.
> - A estrutura básica (`<html>`, `<head>`, `<body>`) é sempre cobrada. Decore a hierarquia e a função de cada tag.