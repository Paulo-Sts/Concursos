# HTML5 – Imagens, Links e Tabelas

## 1. Imagens e Links

### 1.1 A Tag `<img>`
- A tag `<img>` é utilizada para inserir imagens em uma página HTML.
- Trata-se de uma tag vazia, ou seja, não possui uma tag de fechamento (ex: `</img>`), pois todo o seu conteúdo é definido por atributos dentro da própria tag.

#### 1.1.1 Atributos da Tag `<img>`
- `src` (source): Atributo obrigatório que especifica o caminho (path) para o arquivo da imagem.
- `alt` (alternative text): Atributo opcional que fornece um texto alternativo descrevendo a imagem. Este texto será exibido caso a imagem não seja carregada corretamente, sendo também essencial para acessibilidade.
- Exemplo de uso:
```html
<img src="/caminho/para/imagem.jpg" alt="Descrição da Imagem">
```

> [!CAUTION] OBSERVAÇÃO:
> - O atributo `src` é o único obrigatório para a tag `<img>`. Sem ele, a imagem não será exibida.

### 1.2 A Tag `<a>`
- A tag `<a>` (âncora) é usada para criar hiperlinks, conectando o recurso atual a uma variedade de outros recursos.
- Podem ser links para:
  - Páginas web internas ou externas;
  - Arquivos locais (ex: PDFs);
  - Outros documentos web (ex: CSS);
  - Números de telefone e endereços de e-mail.

#### 1.2.1 Atributos da Tag `<a>`
- `href` (Hypertext Reference): Atributo obrigatório que especifica o URL de destino para o qual o link aponta.
- `target`: Atributo opcional que define onde o link será aberto.
  - `_blank`: O link é aberto em uma nova janela ou aba.
  - Outros valores comuns: `_self` (padrão, abre na mesma janela/aba), `_parent`, `_top`.
- `title`: Atributo opcional que fornece um texto de dica (tooltip) que aparece quando o usuário passa o mouse sobre o link, orientando sobre o destino do link.
- Exemplo de uso:
```html
<a href="URL_do_destino" target="_blank" title="Texto do Tooltip">
  Texto do Link
</a>
```

> [!TIP] DICAS:
> - O atributo `target="_blank"` é uma boa prática para links externos, evitando que o usuário saia do seu site.
> - O atributo `title` é útil para dar mais contexto ao usuário, melhorando a experiência de navegação.

## 2. Tabelas
- As tabelas em HTML são estruturas criadas para exibir dados em um formato de linhas e colunas.
- A tag principal que agrupa todos os elementos da tabela é a `<table>`.

### 2.1 Elementos Visuais da Tabela
- `<tr>` (Table Row): Define uma linha na tabela. Todo o conteúdo de uma linha deve estar dentro desta tag.
- `<th>` (Table Header): Define uma célula de cabeçalho. Geralmente usada para os títulos das colunas ou linhas. O texto dentro de `<th>` é renderizado em negrito e centralizado por padrão.
- `<td>` (Table Data): Define uma célula de dados padrão. Contém as informações normais da tabela.

### 2.2 Elementos de Organização Estrutural
- `<thead>` (Table Head): Agrupa o conjunto de linhas que compõem o cabeçalho da tabela. Geralmente contém as tags `<th>`.
- `<tbody>` (Table Body): Agrupa o conjunto de linhas que compõem o corpo principal da tabela. Contém os dados em `<td>`.
- `<tfoot>` (Table Foot): Agrupa o conjunto de linhas que compõem o rodapé da tabela. Usado para resumos ou totais.

> [!CAUTION] OBSERVAÇÃO:
> - A separação em `<thead>`, `<tbody>` e `<tfoot>` não afeta a aparência visual da tabela por si só, mas é crucial para a semântica do documento e permite uma estilização mais refinada com CSS, além de ajudar em acessibilidade.

### 2.3 Estrutura Prática de uma Tabela
- Para construir uma tabela, primeiro define-se a tag `<table>`.
- Dentro dela, os elementos são aninhados na seguinte ordem lógica: `<thead>`, `<tbody>` (e opcionalmente `<tfoot>`).
- Dentro de cada grupo (`<thead>`, `<tbody>`), as linhas são definidas com `<tr>`.
- Dentro de cada `<tr>`, são inseridas as células (`<th>` para cabeçalho ou `<td>` para dados).
- Exemplo de código:
```html
<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Idade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>João</td>
      <td>25</td>
    </tr>
    <tr>
      <td>Maria</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
```