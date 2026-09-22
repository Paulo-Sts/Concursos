# Tecnologias XML: XPATH, XQUERY, XSLT E XHTML

## 1. Visão Geral das Tecnologias XML
- XPath é uma linguagem utilizada para navegar em documentos XML.
- XQuery é usada para realizar consultas a documentos XML.
- XSLT serve para transformar documentos XML em outros formatos.
- XHTML é uma reformulação do HTML utilizando a sintaxe do XML, garantindo maior rigor e consistência na estruturação das páginas web.
- A compreensão básica dessas tecnologias é essencial para responder questões técnicas com precisão, evitando confusões comuns devido à semelhança entre os termos e suas aplicações.

> [!TIP] DICAS: 
> - Em provas, ao ser questionado sobre qual tecnologia descreve web services em XML, a resposta correta é WSDL; atenção para não confundir com XPath, XQuery, DTD ou XSL.

## 2. XPath (XML Path Language)

### 2.1 Conceito e Finalidade
- XPath é uma linguagem que permite localizar e processar itens em documentos XML usando expressões de caminho.
- É uma tecnologia fundamental usada em conjunto com XSLT, XQuery e outras aplicações XML.
- Fornece uma sintaxe eficiente e flexível para descrever e selecionar partes específicas de um documento XML.
- Permite a navegação na estrutura do XML, selecionando nós por critérios específicos e computando valores a partir do conteúdo XML (strings, números e valores lógicos).

> [!TIP] DICAS: 
> - XPath funciona de forma semelhante a um comando "CTRL-F", permitindo procurar por conjuntos específicos de tags dentro do documento XML.

### 2.2 Características do XPath
- Seleção de nós: permite selecionar elementos, atributos, textos e outros nós dentro de um documento XML.
- Funções internas: inclui funções para manipulação de strings, números, sequências de nós, além de capacidades para testes lógicos e matemáticos.

### 2.3 Sintaxe e Exemplos de Expressões XPath
| EXPRESSÃO | DESCRIÇÃO |
|-----------|-----------|
| //* | Seleciona todos os elementos no documento |
| /biblioteca/livro | Seleciona todos os elementos livro diretamente sob o elemento biblioteca |
| //titulo | Seleciona todos os elementos titulo em qualquer lugar do documento |
| /biblioteca/livro[@id='1']/titulo | Seleciona o titulo do livro com id="1" |
| //livro[categoria='Poesia']/titulo | Seleciona o titulo do livro classificado como "Poesia" |
| child::livro[1] | Seleciona o primeiro nó livro que é filho direto do nó corrente |

- Exemplo de documento XML base:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Biblioteca>
  <livro id="1">
    <titulo>Capão Pecado</titulo>
    <categoria>Literatura Nacional</categoria>
  </livro>
  <livro id="2">
    <titulo>Quarto de Despejo</titulo>
    <categoria>Biografia</categoria>
  </livro>
  <livro id="3">
    <titulo>Bagagem</titulo>
    <categoria>Poesia</categoria>
  </livro>
</Biblioteca>
```

> [!CAUTION] OBSERVAÇÃO: 
> - Quando "categoria" é uma tag filho de "livro" (e não um atributo), não se utiliza o "@" para referenciá-la.
> - O "@" é utilizado exclusivamente para referenciar atributos (ex: @id).
> - O termo "PATHEXPRESSIONS" significa "expressões de caminho", que são as expressões inseridas para realizar buscas, como no comando CTRL-F.

## 3. XQuery

### 3.1 Conceito e Finalidade
- XQuery é uma linguagem de consulta poderosa e flexível projetada para consultar dados armazenados em formato XML.
- É recomendada pelo W3C.
- É similar à SQL para bancos de dados, mas aplicada a documentos XML.
- XQuery é para o XML o que a linguagem SQL é para as bases de dados.

> [!TIP] DICAS: 
> - XQuery é uma linguagem de programação completa e pode ser usada para transformar dados XML para XHTML.

### 3.2 Características do XQuery
- Baseada em expressões XPath para navegação nos elementos XML.
- Suporta construções como loops (for), condições (if) e funções.
- É case sensitive.
- Permite a criação de novos documentos XML a partir de consultas específicas.
- Pode ser utilizada mesmo em documentos XML que não atendam plenamente aos critérios de validação.

### 3.3 Estrutura FLWOR
- FLWOR é um acrônimo que representa a essência da linguagem XQuery.

| LETRA | SIGNIFICADO | FUNÇÃO |
|-------|-------------|--------|
| F | For | Itera sobre os elementos |
| L | Let | Define variáveis |
| W | Where | Aplica condições de filtragem |
| O | Order by | Realiza ordenação dos resultados |
| R | Return | Projeta e retorna os dados conforme padrões específicos |

- Exemplo prático de consulta XQuery:
```xquery
let $biblioteca := doc("biblioteca.xml")
for $livro in $biblioteca/biblioteca/livro
where $livro/categoria = "literatura nacional"
return
  <detalhe>
    <titulo>{ $livro/titulo }</titulo>
    <autor>{ $livro/autor }</autor>
  </detalhe>
```

> [!TIP] DICAS: 
> - O FLWOR permite iteração, definição de variáveis, aplicação de condições (where), ordenação (order by) e projeção de dados em consultas XQuery.

### 3.4 Funções Comuns do XQuery
| FUNÇÃO | DESCRIÇÃO |
|--------|-----------|
| doc() | Carrega documentos XML |
| contains() | Verifica se uma string contém uma substring (retorna booleano) |
| current-date() | Retorna a data atual (não inclui hora) |
| avg() | Calcula a média de uma sequência de números |

> [!CAUTION] OBSERVAÇÃO: 
> - A função `contains()` retorna um valor booleano (verdadeiro ou falso), não uma substring.
> - A função `current-date()` retorna apenas a data atual, não a data e hora correntes.
> - A função `avg()` retorna a média de uma sequência de valores passados como parâmetro.

- Exemplo avançado com funções:
```xquery
let $palavra-chave := "sapo"
for $livro in doc("biblioteca.xml")/biblioteca/livro
where contains($livro/titulo, $palavra-chave)
return
  <resultado>
    <titulo>{ $livro/titulo }</titulo>
    <ano-media>{ avg($livro/ano-publicacao) }</ano-media>
  </resultado>
```
> [!TIP] DICAS: 
> - A função `doc()` é utilizada para abrir um arquivo XML (e não `open()`).
> - A função `contains()` retorna valor booleano, não substring.
> - A função `current-date()` retorna apenas data, não data e hora.
> - A função `avg()` retorna a média de uma sequência de valores.
> - Não existe função `sort()` no XQuery; a ordenação é feita com `order by` na estrutura FLWOR.