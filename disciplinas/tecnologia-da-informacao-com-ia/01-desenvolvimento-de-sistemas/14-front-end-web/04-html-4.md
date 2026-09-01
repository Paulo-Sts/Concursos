# HTML5 – Tags de Estrutura e Formatação de Texto

## 1. Tags de Estrutura Semântica
- As tags de estrutura organizam e definem a hierarquia do conteúdo em uma página web.
- Conferem semântica ao documento, facilitando a compreensão do conteúdo e melhorando a acessibilidade.
- Exemplos principais: `<header>`, `<nav>`, `<main>`, `<footer>`, `<article>`, `<section>` e `<aside>`.

### 1.1 Tag `<header>`
- Representa o cabeçalho de uma seção ou página.
- Pode conter títulos, logotipos e informações introdutórias.
- Exemplo:
```html
<header>
  <h1>Meu Site</h1>
  <p>Bem-vindo ao meu site!</p>
</header>
```

### 1.2 Tag `<nav>`
- Define uma seção de navegação.
- Geralmente contém links para outras páginas ou seções do site.

### 1.3 Tag `<footer>`
- Representa o rodapé de uma seção ou página.
- Pode conter créditos, links de contato ou direitos autorais.
- Exemplo:
```html
<footer>
  <p>&copy; 2023 Meu Site. Todos os direitos reservados.</p>
</footer>
```

### 1.4 Tag `<article>`
- Define conteúdo independente e autossuficiente.
- Exemplo: postagem de blog ou artigo em página de notícias.
- Exemplo:
```html
<article>
  <h2>Título do Artigo</h2>
  <p>Conteúdo do artigo...</p>
</article>
```

### 1.5 Tag `<section>`
- Define uma seção em um documento.
- Utilizada para agrupar conteúdos relacionados.
- Exemplo:
```html
<section>
  <h2>Seção Principal</h2>
  <p>Conteúdo da seção...</p>
</section>
```

### 1.6 Tag `<aside>`
- Representa conteúdo relacionado ao conteúdo vizinho, geralmente em barra lateral.
- É conteúdo relacionado ao principal, mas sem estar diretamente envolvido com ele.

> [!TIP] DICAS:
> - A tag `<aside>` é frequentemente cobrada em provas como elemento que define conteúdo tangencialmente relacionado ao conteúdo principal.

### 1.7 Tag `<main>`
- Define o conteúdo principal de um documento HTML.
- Deve conter o conteúdo central da página, excluindo cabeçalho, rodapé, barras laterais e áreas relacionadas.
- Exemplo:
```html
<main>
  <h1>Conteúdo Principal</h1>
  <p>Texto principal...</p>
</main>
```

### 1.8 Tag `<div>`
- É uma tag de contêiner genérica para agrupar e estruturar outros elementos HTML.
- Não possui significado semântico próprio.
- Serve como bloco divisório para aplicar estilos, scripts ou manipular grupos de elementos.
- Pode substituir outras tags, mas tags específicas melhoram a semântica do site.

> [!CAUTION] OBSERVAÇÃO:
> - Embora a `<div>` possa ser usada para estruturar o site, o uso de tags semânticas (`<header>`, `<nav>`, etc.) é recomendado para melhor acessibilidade e interpretação pelos navegadores.

### 1.9 Tags `<figure>` e `<figcaption>`
- A tag `<figure>` encapsula conteúdo relacionado a uma imagem, gráfico, código etc.
- A tag `<figcaption>` fornece uma legenda para o conteúdo encapsulado por `<figure>`.

### 1.10 Tags `<details>` e `<summary>`
- A tag `<details>` define um widget de divulgação/ocultação.
- A tag `<summary>` fornece um título para o conteúdo oculto dentro de `<details>`.
- Exemplo:
```html
<details>
  <summary>Detalhes</summary>
  <p>Conteúdo oculto...</p>
</details>
```

### 1.11 Tag `<time>`
- Representa datas e horas, melhorando a interpretação para máquinas.
- Aceita o atributo `datetime` para fornecer uma representação legível para os usuários.
- Exemplo:
```html
<p>A reunião está agendada para
  <time datetime="2023-02-15T18:30">
    15 de fevereiro de 2023, 18:30
  </time>
</p>
```
- Útil para o navegador entender que se trata de um tempo, com data e horário.

### 1.12 Tag `<iframe>`
- Incorpora conteúdo de outra fonte (página web, vídeo) dentro de uma página HTML.
- Utilizada para inserir mapas, vídeos do YouTube ou páginas de outros sites.
- Possui abertura e fechamento.

> [!TIP] DICAS:
> - Em provas, fique atento à posição correta das tags de abertura e fechamento, especialmente em combinações com `<a>` e `<img>`.

### Tabela de Tags Estruturais
| TAG | DESCRIÇÃO |
|-----|-----------|
| `<header>` | Define o cabeçalho de uma seção ou página |
| `<nav>` | Representa uma seção de navegação |
| `<footer>` | Define o rodapé de uma seção ou página |
| `<article>` | Usada para definir conteúdo independente e autossuficiente |
| `<section>` | Define uma seção em um documento |
| `<aside>` | Representa conteúdo relacionado ao conteúdo circundante |
| `<main>` | Define o conteúdo principal de um documento HTML |
| `<figure>` | Utilizada para encapsular conteúdo relacionado a uma imagem |
| `<figcaption>` | Fornece uma legenda para o conteúdo encapsulado por `<figure>` |
| `<details>` | Cria um widget de divulgação/ocultação |
| `<summary>` | Fornece um título para o conteúdo oculto dentro de `<details>` |
| `<time>` | Representa datas e horas |
| `<mark>` | Destaca partes do texto para referência ou destaque visual |

> [!CAUTION] OBSERVAÇÃO:
> - Tags estruturais são aquelas que organizam a página: `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, `<nav>`, `<aside>`.
> - Tags como `<p>` (parágrafo) e `<div>` (contêiner genérico) **não são** consideradas tags estruturais semânticas.

## 2. Tags de Estilo Visual
- São tags utilizadas para formatação visual do texto.

## 3. Tags de Estilo Semântico
- Tags que conferem significado ao conteúdo, além da formatação visual.

## 4. Tags Introduzidas no HTML5
- Destacam-se as tags: `<header>`, `<nav>`, `<footer>`, `<article>`, `<section>`, `<aside>`, `<main>`, `<figure>`, `<figcaption>`, `<details>`, `<summary>`, `<time>`, `<mark>`.

> [!TIP] DICAS:
> - O HTML5 introduziu diversas tags semânticas para substituir o uso excessivo de `<div>` e melhorar a acessibilidade e o SEO.