# Tecnologias XML: DTD e XSD

## 1. Introdução e Contexto do DTD
- O propósito principal da tecnologia DTD é validar o arquivo XML, garantindo que o documento esteja em conformidade com as regras estruturais definidas.
- A capacidade de validação adicional é uma das grandes vantagens do XML em comparação a outras linguagens de configuração como JSON, YAML e TOML.
- A necessidade de compreender um ecossistema vasto de tecnologias para lidar com a validação do XML cria uma barreira de entrada maior para novos usuários.

## 2. Definição e Finalidade
- DTD é a sigla para Document Type Definition, ou Definição de Tipo de Documento.
- Funciona como um mecanismo para definir a estrutura legal e as regras de organização de um arquivo XML.
- Especifica a disposição dos elementos, atributos e entidades que podem aparecer no documento.
- Sua finalidade é assegurar que o XML esteja estruturado corretamente, verificando se ele está bem formado e válido perante o design definido.

## 3. Componentes do DTD
- Elementos: definem quais etiquetas podem aparecer no documento e em qual sequência devem ser organizadas.
- Atributos: especificam quais propriedades são permitidas para cada elemento e como os dados devem ser formatados.
- Entidades: consistem em declarações utilizadas para representar textos ou símbolos mais complexos dentro da estrutura.

## 4. Sintaxe e Definição de Elementos
- <!DOCTYPE>: instrução que especifica o nome do DTD e introduz o conjunto de regras de validação.
- <!ELEMENT>: comando utilizado para definir um elemento específico e sua hierarquia de filhos dentro do documento.
- (#PCDATA): sigla para Parsed Character Data, que indica que o elemento contém texto interpretável pelo processador XML.
- Quantificadores de ocorrência:
  - + ⟶ indica que deve existir um ou mais itens do elemento especificado;
  - * ⟶ indica a presença de zero ou mais ocorrências do item;
  - ? ⟶ indica que o elemento é opcional, podendo aparecer zero ou uma única vez.
- Operador de escolha (|): utilizado para definir que o elemento pai deve conter apenas um dos elementos listados entre parênteses.

> [!TIP] DICAS: 
> - O sinal de interrogação (?) é a chave para identificar elementos que não são obrigatórios no documento.
> - Em definições de escolha (A|B), o uso simultâneo dos dois elementos invalida o documento perante o DTD.

#### Exemplo
```xml
<!-- DTD para definir a estrutura de uma agenda -->
<!DOCTYPE agenda [
  <!-- A agenda contém um ou mais contatos -->
  <!ELEMENT agenda (contato+)>
  <!-- Cada contato possui um nome e um telefone -->
  <!ELEMENT contato (nome, telefone)>
  <!ELEMENT nome (#PCDATA)>
  <!ELEMENT telefone (#PCDATA)>
]>

<?xml version="1.0"?>
<!--Vinculo com "agenda.dtd"-->
<!DOCTYPE agenda SYSTEM "agenda.dtd">
<agenda>
  <contato>
    <nome>Agenor de Miranda Araújo Neto</nome>
    <telefone>123456789</telefone>
  </contato>
  <contato>
    <nome>Emival Eterno Costa</nome>
    <telefone>987654321</telefone>
  </contato>
</agenda>
```

## 5. Lista de Atributos e Propriedades
- <!ATTLIST>: comando utilizado para definir uma lista de atributos vinculada a um determinado elemento.
- ID: especifica que o valor do atributo deve ser um identificador único em todo o documento XML.
- CDATA: indica que o atributo transporta dados de caracteres simples, como texto puro.
- Modificadores de obrigatoriedade:
  - #REQUIRED ⟶ indica que o preenchimento do atributo é obrigatório para a validade do documento;
  - #IMPLIED ⟶ indica que o atributo é opcional e não precisa ser declarado no XML.
- Valores pré-definidos: permite restringir os valores aceitáveis para um atributo, definindo inclusive uma opção padrão caso nada seja informado.

> [!CAUTION] OBSERVAÇÃO: 
> - Tags que já foram declaradas anteriormente não devem ser definidas novamente no mesmo DTD para evitar erros de processamento.
> - A ordem dos elementos dentro da instrução de definição deve ser rigorosamente respeitada no arquivo XML para que este seja considerado válido.

#### Exemplo
```xml
<!-- DTD para a estrutura de um catálogo de livros -->
<!-- Definição do elemento livro com seus subelementos -->
<!DOCTYPE livro [
  <!ELEMENT livro (titulo, autor, ano)>
  <!ELEMENT titulo (#PCDATA)>
  <!ELEMENT autor (#PCDATA)>
  <!ELEMENT ano (#PCDATA)>
  <!-- Atributos do elemento livro -->
  <!ATTLIST livro
    id ID #REQUIRED
    categoria CDATA #IMPLIED>
]>

<?xml version="1.0"?>
<!-- Vinculo com "livro.dtd" -->
<!DOCTYPE livro SYSTEM "livro.dtd">
<livro id="001" categoria="Romance">
  <titulo>Os Supridores</titulo>
  <autor>José Falero</autor>
  <ano>2020</ano>
</livro>
```

#### Exemplo 2
```xml
<!DOCTYPE conferencia [
  <!ELEMENT conferencia (sessao+)>
  <!ELEMENT sessao (titulo, palestrante+, participante*)>
  <!ELEMENT titulo (#PCDATA)>
  <!ELEMENT palestrante (nome, biografia, temas)>
  <!ELEMENT nome (#PCDATA)>
  <!ELEMENT biografia (#PCDATA)>
  <!ELEMENT temas (tema+)>
  <!ELEMENT tema (#PCDATA)>
  <!ELEMENT participante (nome, email?)>
  <!ELEMENT email (#PCDATA)>
  <!ATTLIST sessao
    id ID #REQUIRED
    data CDATA #REQUIRED
    sala CDATA #IMPLIED>
  <!ATTLIST palestrante
    palestrante_id ID #REQUIRED
    afiliacao CDATA #REQUIRED>
  <!ATTLIST participante
    participante_id ID #REQUIRED
    registrado (sim|nao) "nao">
]>

<?xml version="1.0"?>
<!DOCTYPE conferencia SYSTEM "conferencia.dtd">
<conferencia>
  <sessao id="S001" data="2023-10-15" sala="101">
    <titulo>Inteligência Artificial na Saúde</titulo>
    <palestrante palestrante_id="P001" afiliacao="Universidade X">
      <nome>Dr. Alice Martins</nome>
      <biografia>PhD em IA</biografia>
      <temas>
        <tema>Aplicações de IA em diagnóstico</tema>
      </temas>
    </palestrante>
    <participante participante_id="PT001" registrado="sim">
      <nome>Maria Silva</nome>
      <email>maria.silva@email.com</email>
    </participante>
  </sessao>
</conferencia>
```

## 6. Identificadores de Localização e Uso
- SYSTEM: palavra-chave que aponta para a localização de um arquivo DTD no sistema local ou em uma URL específica.
- PUBLIC: permite identificar o DTD por meio de um identificador público, facilitando o uso de padrões conhecidos.

> [!TIP] DICAS: 
> - Quando o identificador SYSTEM é utilizado, o caminho do arquivo DTD deve ser informado logo em seguida entre aspas.
> - A correta vinculação entre o XML e o DTD ocorre logo após o prólogo do documento.