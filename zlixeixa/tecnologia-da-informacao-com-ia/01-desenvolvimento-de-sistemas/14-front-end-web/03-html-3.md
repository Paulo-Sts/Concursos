# HTML5 – Formulários

## 1. Formulários em HTML
- São elementos que permitem aos usuários inserir dados e interagir com uma aplicação web.
- Exemplos de uso: login, registro, pesquisas, envio de mensagens e cadastros em sites.

## 2. Tag `<form>`
- Define o início e o fim de um formulário.
- Principais atributos:
  - `action`: Especifica para onde os dados do formulário serão enviados (ex.: caminho para outra página ou pasta da aplicação).
  - `method`: Define o método de envio, podendo ser:
    - `get`: Utilizado para receber informações (ex.: filtros de busca).
    - `post`: Utilizado para enviar informações (ex.: cadastros e login).
- Exemplo:
```html
<form action="/processar_formulario" method="post">
  <!-- Elementos do formulário aqui -->
</form>
```

> [!CAUTION] OBSERVAÇÃO:
> - A diferença prática entre `get` e `post` é que `get` é usado para requisitar dados (os parâmetros aparecem na URL) e `post` é usado para enviar dados (os parâmetros não aparecem na URL).

## 3. Tag `<input>`
- Usada para criar campos de entrada de dados.
- O tipo do campo é definido pelo atributo `type`.

### 3.1 Principais tipos de `<input>`
| TIPO | DESCRIÇÃO |
|------|-----------|
| `text` | Exibe um campo de entrada de texto de linha única |
| `radio` | Exibe um botão de opção (seleciona apenas uma opção entre várias) |
| `checkbox` | Exibe uma caixa de seleção (seleciona zero ou mais opções) |
| `submit` | Exibe um botão de envio (submete o formulário) |
| `button` | Exibe um botão clicável (sem ação padrão) |

> [!CAUTION] OBSERVAÇÃO:
> - `radio` permite apenas uma seleção por grupo de opções com o mesmo `name`.
> - `checkbox` permite selecionar múltiplas opções.

### 3.2 Atributos comuns do `<input>`
- `type="email"`: Aceita apenas valores de e-mail válidos.
- `id`: Identificador único do elemento (usado para associar com `<label>` e para estilização com CSS ou manipulação com JavaScript).
- `name`: Identifica o campo no formulário e é enviado como parte dos dados; também é usado para agrupar elementos (ex.: `radio`).
- `placeholder`: Texto de exemplo exibido antes da entrada do usuário (orienta sobre o formato esperado).
- `required`: Torna o preenchimento do campo obrigatório para submissão do formulário.
- Exemplo:
```html
<input type="email" id="email" name="email" placeholder="usuario@dominio.com" required>
```

> [!TIP] DICAS:
> - O atributo `id` deve ser único em toda a página (não pode haver dois elementos com o mesmo `id`).
> - O atributo `placeholder` não substitui o `label`; ele apenas dá uma dica visual sobre o formato esperado.
> - O `required` bloqueia o envio do formulário se o campo estiver vazio.

## 4. Tag `<textarea>`
- Usada para campos de texto longo (multilinha).
- Diferença para `<input type="text">`: enquanto o `text` é para uma única linha, o `<textarea>` permite múltiplas linhas.

### 4.1 Atributos do `<textarea>`
- `name`: Identifica o campo no formulário.
- `id`: Identificador único.
- `rows`: Define o número inicial de linhas visíveis.
- `cols`: Define o número inicial de colunas (caracteres por linha) visíveis.
- Exemplo:
```html
<textarea name="mensagem" id="mensagem" rows="4" cols="50"></textarea>
```

## 5. Atributo `pattern`
- Define uma expressão regular que o valor do campo deve seguir para ser considerado válido.
- Comumente usado em `<input>` e `<textarea>` para validação de formato (ex.: CPF, telefone, placas).
- Exemplos:
```html
<!-- Só permite letras minúsculas -->
pattern="[a-z]+"

<!-- Só permite números inteiros positivos -->
pattern="[0-9]+"

<!-- Formatação de CPF -->
pattern="\d{3}\.\d{3}\.\d{3}-\d{2}"
```

> [!CAUTION] OBSERVAÇÃO:
> - O `pattern` é uma ferramenta de validação nativa do HTML5, mas não substitui a validação no servidor (back-end), pois pode ser contornado pelo usuário.

## 6. Tag `<datalist>`
- Fornece uma lista de opções sugeridas para campos de entrada.
- Diferença para `<select>`: o usuário pode digitar livremente no campo, e as opções aparecem como sugestões; no `<select>`, o usuário só pode escolher entre as opções disponíveis.

### 6.1 Atributos relacionados
- `autocomplete` (atributo do `<input>`): Controla as sugestões automáticas do navegador (`on` ou `off`).
- `list` (atributo do `<input>`): Associa o campo de entrada à lista de opções definida pela tag `<datalist>`.
- Exemplo:
```html
<label for="browser">Escolha um navegador:</label>
<input list="navegadores" id="browser" name="browser" autocomplete="off">
<datalist id="navegadores">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
  <option value="Opera">
</datalist>
```

> [!TIP] DICAS:
> - O `datalist` é útil para campos de busca ou seleção com muitas opções, onde o usuário pode digitar para filtrar as sugestões.
> - O atributo `id` do `<datalist>` deve ser igual ao valor do atributo `list` do `<input>` correspondente.

## 7. Tag `<label>`
- Associa um rótulo descritivo a um elemento de entrada.
- O atributo `for` no `<label>` deve corresponder ao `id` do elemento de entrada associado.
- Melhora a acessibilidade e a usabilidade (clicar no rótulo foca no campo).
- Exemplo:
```html
<label for="nome">Nome:</label>
<input type="text" name="nome" id="nome">
<br/>
<label for="sobrenome">Sobrenome:</label>
<input type="text" name="sobrenome" id="sobrenome">
```

> [!CAUTION] OBSERVAÇÃO:
> - O `id` deve ser único; o exemplo do material apresenta um erro ao repetir `id="nome"` para dois campos diferentes. O correto é que cada campo tenha seu próprio `id`.

## 8. Tag `<fieldset>` e `<legend>`
- `<fieldset>`: Agrupa elementos relacionados de um formulário.
- `<legend>`: Fornece um título ou legenda para o grupo agrupado pelo `<fieldset>`.
- Úteis para organizar visualmente partes diferentes de um formulário.
- Exemplo:
```html
<fieldset>
  <legend>Dados Pessoais</legend>
  <label for="nome">Nome:</label>
  <input type="text" name="nome" id="nome">
  <br/>
  <label for="idade">Idade:</label>
  <input type="number" name="idade" id="idade">
</fieldset>
```

## 9. Tag `<button>`
- Cria um botão clicável em uma página web.

### 9.1 Atributo `type`
- `submit`: Submete o formulário (comportamento padrão se dentro de um `<form>`).
- `reset`: Reseta os campos do formulário para seus valores padrão.
- `button`: Cria um botão sem ação específica (geralmente usado com JavaScript).
- Exemplo:
```html
<button type="submit">Enviar</button>
<button type="reset">Limpar</button>
<button type="button">Clique aqui</button>
```

> [!TIP] DICAS:
> - Dentro de um `<form>`, um `<button>` sem `type` explícito se comporta como `submit`.
> - Para botões que disparam ações JavaScript, use `type="button"` para evitar o envio acidental do formulário.

## 10. Validação em HTML5
- O HTML5 oferece diversos recursos nativos de validação sem necessidade de JavaScript, como:
  - `required`: Campo obrigatório.
  - `type`: Valida o formato (ex.: `email`, `number`, `url`).
  - `pattern`: Valida com expressão regular.
  - `min`, `max`: Valida limites numéricos.
  - `minlength`, `maxlength`: Valida tamanho de texto.

> [!CAUTION] OBSERVAÇÃO:
> - A validação HTML5 funciona no lado do cliente (navegador) e pode ser facilmente contornada. Nunca confie apenas nela; sempre valide os dados no servidor.
> - A validação HTML5 melhora a experiência do usuário, fornecendo feedback imediato, mas não substitui a segurança no back-end.

## 11. Tipos de entrada do HTML5
- Além dos tipos básicos (`text`, `radio`, `checkbox`), o HTML5 introduziu novos tipos:
  - `email`: Valida formato de e-mail.
  - `number`: Aceita apenas números.
  - `date`: Seleciona uma data.
  - `time`: Seleciona um horário.
  - `url`: Valida formato de URL.
  - `search`: Campo de busca (com comportamento específico em alguns navegadores).
  - `range`: Controle deslizante para selecionar um valor numérico.
  - `color`: Seletor de cores.

> [!TIP] DICAS:
> - Os novos tipos de entrada (`date`, `time`, `email`, etc.) são recursos nativos do HTML5 que melhoram a experiência do usuário e facilitam a validação.
> - Nem todos os navegadores antigos suportam esses tipos; para compatibilidade, pode ser necessário usar fallbacks.