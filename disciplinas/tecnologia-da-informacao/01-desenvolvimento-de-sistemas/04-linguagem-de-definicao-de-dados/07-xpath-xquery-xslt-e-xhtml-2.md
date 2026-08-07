# Tecnologias XML: XPath, XQuery, XSLT e XHTML 2

## 1. Introdução ao XSLT

### 1.1 O que é XSLT (Extensible Stylesheet Language Transformations)?
- Linguagem de transformação que permite converter documentos XML em outros formatos XML, HTML ou texto puro.
- Utiliza regras específicas definidas em uma "folha de estilo".

### 1.2 Características do XSLT
- Amplamente utilizado para adaptar dados XML a diferentes necessidades de apresentação ou estrutura de dados.
- Construído sobre a linguagem XPath para identificar partes do documento XML que precisam ser transformadas ou substituídas.
- Possui recursos robustos como iteração e condicionais.

### 1.3 Propósito Principal
- O propósito principal do XSLT é realizar transformações.
- Diferenciação:
  - XQuery: semelhanças com XSLT, mas seu propósito principal é realizar buscas de elementos e informações.
  - XSLT: dedicado à transformação de documentos.

> [!TIP] DICAS:
> - XSLT transforma; XQuery busca. Esta é a principal diferença cobrada em provas.
> - O XSLT é construído sobre XPath para navegação e seleção de nós.

## 2. Funcionamento do XSLT: Exemplo Prático

### 2.1 Estrutura do Documento XSLT
- Namespace XML XSL: comumente identificado como XSL, permite o uso de tags específicas do XSLT.
- Elemento raiz: `<xsl:stylesheet>` define o documento como uma folha de estilo XSLT.
- O atributo `match="/"` indica que todo o documento será transformado.

### 2.2 Processo de Transformação XML para HTML
- O documento XML é processado por meio de um documento de transformação XSLT.
- No XSL, cada elemento dentro da tag raiz é selecionado e processado.
- Para cada elemento selecionado, é criada uma linha na tabela HTML resultante.
- A tag `<xsl:value-of>` é usada para obter o valor do elemento específico.

> [!CAUTION] OBSERVAÇÃO:
> - O XSLT não modifica o documento XML original.
> - A transformação gera um novo documento em outro formato (HTML, XML ou texto puro).
> - É possível alterar as informações e gerar um documento completamente diferente.

## 3. Recursos Avançados do XSLT

### 3.1 Estruturas Condicionais
- `<xsl:choose>`, `<xsl:when>`, `<xsl:otherwise>`: estrutura condicional tipo "switch" ou "if-else".
- `<xsl:if>`: testa uma expressão e, se verdadeira, processa o conteúdo dentro dela.
- Exemplo: se o ano for maior ou igual a 2000, adiciona o comentário "obra recente"; caso contrário, marca como "clássico".

### 3.2 Iteração
- `<xsl:for-each>`: itera sobre um conjunto de nós selecionados por uma expressão XPath.
- Dentro deste loop, é possível aplicar templates ou outras operações a cada nó iterado individualmente.

### 3.3 Transformação de Estrutura
- Possibilidade de criar uma nova tag raiz diferente da original.
- Exemplo: a partir da tag "biblioteca", transformar em um novo documento XML com a tag raiz "catálogo".
- Para cada livro, criar um elemento "item" com base na categoria.

> [!TIP] DICAS:
> - O `<xsl:choose>` funciona como um switch-case, sendo cobrado frequentemente em provas.
> - O `<xsl:for-each>` é utilizado para percorrer conjuntos de nós selecionados por XPath.
> - O `<xsl:if>` realiza testes simples e diretos.

## 4. Principais Elementos do XSLT

### 4.1 Elementos Essenciais
- `<xsl:stylesheet>`: define o documento como uma folha de estilo XSLT e é o elemento raiz de qualquer documento XSLT.
- `<xsl:template>`: define regras para como os dados de entrada devem ser processados. O atributo `match` especifica o padrão de nó ou caminho que o template deve processar.
- `<xsl:value-of>`: extrai o valor de um nó XML e o insere no fluxo de saída. Frequentemente usado para converter texto de um nó XML em texto no documento de saída.
- `<xsl:for-each>`: itera sobre um conjunto de nós selecionados por uma expressão XPath.
- `<xsl:if>`: testa uma expressão e, se verdadeira, processa o conteúdo interno.
- `<xsl:choose>`, `<xsl:when>`, `<xsl:otherwise>`: estrutura condicional tipo "switch" ou "if-else". Contém um ou mais `<xsl:when>` e opcionalmente um `<xsl:otherwise>`.

## 5. XHTML (Extensible Hypertext Markup Language)

### 5.1 Conceito e Diferenças
- O prefixo "X" antes do HTML indica que um documento HTML se torna validável como um documento XML.
- XHTML: deve ser bem-formado e seguir as regras de XML estrito.
- HTML: mais flexível em termos de formatação, permite elementos não fechados e tags em maiúsculas.

### 5.2 Características do XHTML
- Elementos e atributos devem ser em minúsculas.
- Todos os elementos devem ser fechados.
- Elementos vazios devem ser fechados explicitamente (exemplo: `<br />`).
- Deve ser bem-formado e seguir as regras de XML estrito.
- Pode ser parseado por parsers XML, facilitando a integração com outras aplicações XML.
- Utiliza namespaces.

### 5.3 Regras para um Documento XHTML Bem-Formado
- Bem-Formado: todo documento XHTML deve ser bem-formado XML. Inclui fechamento de todas as tags, uso de minúsculas para elementos e atributos, e citação de todos os valores dos atributos.
- DOCTYPE: um documento XHTML deve declarar o tipo de documento no início, utilizando a declaração DOCTYPE para especificar qual versão do XHTML está sendo usada.
- Elementos Aninhados Corretamente: os elementos devem ser corretamente aninhados. Exemplo: `<h1><p>Exemplo</p></h1>` é válido, já `<h1><p>Exemplo</h1></p>` não é.
- Atributos Devem Ser Cercados por Aspas: os valores dos atributos sempre devem estar entre aspas (duplas ou simples, mas não misturadas).

> [!CAUTION] OBSERVAÇÃO:
> - Não existe XHTML5. Existe apenas XHTML e HTML5.
> - A declaração DOCTYPE é obrigatória em documentos XHTML.
> - A presença de um elemento raiz é obrigatória em XHTML.
> - Os nomes dos elementos devem ser escritos em letras minúsculas (case sensitive).
> - Os valores dos atributos devem ser delimitados por aspas (duplas ou simples, sem misturar).
> - A tag `xml:lang` pode ser utilizada junto com o atributo `lang` do HTML, como em `xml:lang="en" lang="en"`.

## 6. Comparativo entre XSLT, XQuery, XPath e XHTML
| TECNOLOGIA | PROPÓSITO PRINCIPAL | CARACTERÍSTICA PRINCIPAL |
|------------|---------------------|--------------------------|
| Xpath | Linguagem de consulta | Buscar elementos em um arquivo XML |
| Xquery | Busca e transformação | Semelhante ao SQL para XML |
| Xslt | Transformação | Converter documentos XML em outros formatos |
| Xhtml | Marcação | HTML validável como XML |

> [!TIP] DICAS:
> - XPath serve para navegar e selecionar nós em documentos XML.
> - XQuery é utilizado para consultas complexas em XML, similar ao SQL.
> - XSLT é utilizado para transformar documentos XML em outros formatos.
> - XHTML é uma versão do HTML que segue as regras do XML.
> - Em provas, é comum cobrarem a distinção entre XSLT (transformação) e XQuery (busca).
> - A banca CESPE já considerou incorreta a afirmação sobre a existência de XHTML5.