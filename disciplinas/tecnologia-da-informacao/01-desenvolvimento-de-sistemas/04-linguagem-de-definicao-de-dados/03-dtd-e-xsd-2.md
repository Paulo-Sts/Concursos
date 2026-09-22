# Tecnologias XML: DTD e XSD 2

## 1. Introdução ao XSD

### 1.1 Definição de XSD
- XSD (XML Schema Definition), também conhecido como XML Schema, é uma linguagem de schema usada para definir a estrutura e as regras de validação de documentos XML de maneira mais detalhada e rigorosa do que DTD.

### 1.2 Finalidade do XSD
- Permite especificar não apenas a estrutura de documentos XML, mas também regras de restrição para os dados, como tipos de dados, padrões e limitações específicas.
- Serve para garantir que os dados estejam corretos e válidos conforme as regras de negócio.

### 1.3 Relação com DTD
- Ao contrário do DTD, XSD oferece suporte a tipos de dados predefinidos e à criação de tipos personalizados.
- XSD é escrito em XML, proporcionando uma integração mais consistente e flexível.
- XSD é mais poderoso e expressivo, oferecendo maior controle sobre a validação e sendo mais adaptável a diferentes necessidades e tecnologias.

> [!TIP] DICAS:
> - XSD é mais completo que DTD porque suporta tipos de dados e namespaces.
> - DTD não suporta tipos de dados; essa é a principal diferença cobrada em provas.

## 2. Estrutura e Sintaxe do XSD

### 2.1 Elementos Básicos
- xs:element: Define um elemento no documento XML.
- type: Especifica o tipo de dados do elemento.

#### 2.1.1 Exemplo Simples
```xml
<xs:element name="nota" type="xs:float"/>
```
- Neste exemplo, o elemento "nota" é definido com o tipo xs:float, indicando que seu conteúdo deve ser um número flutuante.

### 2.2 Tipos Complexos
- xs:complexType: Define um tipo complexo que pode incluir uma mistura de outros elementos e atributos.
- xs:sequence: Define que os elementos dentro dela devem aparecer em uma sequência específica no documento XML.

#### 2.2.1 Exemplo Intermediário
```xml
<xs:element name="aluno">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="nome" type="xs:string"/>
      <xs:element name="idade" type="xs:integer"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```
- No exemplo, "aluno" é um tipo complexo que contém os elementos "nome" e "idade" em sequência obrigatória.

### 2.3 Atributos
- xs:attribute: Usado para definir um atributo para um elemento XML.
- use: Especifica se um atributo é obrigatório (required) ou opcional (optional). Por padrão, os atributos são opcionais em XSD.

> [!CAUTION] OBSERVAÇÃO:
> - Para especificar que um atributo é obrigatório, utiliza-se use="required".
> - Esta é uma pegadinha comum em provas: as opções "mandatory", "required" como valor de outra propriedade, ou "fixed" estão incorretas. O correto é sempre use="required".

#### 2.3.1 Exemplo com Atributo
```xml
<xs:element name="aluno">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="nome" type="xs:string"/>
      <xs:element name="idade" type="xs:integer"/>
    </xs:sequence>
    <xs:attribute name="id" type="xs:string" use="required"/>
  </xs:complexType>
</xs:element>
```

### 2.4 Ocorrência de Elementos
- minOccurs: Determina o número mínimo de vezes que um elemento pode ocorrer.
- maxOccurs: Determina o número máximo de vezes que um elemento pode ocorrer.
- maxOccurs="unbounded": Permite que um elemento ocorra um número ilimitado de vezes.

#### 2.4.1 Exemplo com Ocorrências
```xml
<xs:element name="alunos">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="aluno" type="tipoAluno" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

## 3. Tipos Primitivos no XSD

### 3.1 Lista de Tipos Primitivos
| TIPO | DESCRIÇÃO |
|------|-----------|
| xs:string | Representa uma sequência de caracteres, sem restrições de formato. |
| xs:integer | Representa números inteiros de qualquer tamanho. |
| xs:decimal | Representa números decimais de precisão fixa ou arbitrária. |
| xs:float | Representa números de ponto flutuante de precisão simples. |
| xs:double | Representa números de ponto flutuante de precisão dupla. |
| xs:boolean | Representa valores booleanos (true ou false). |
| xs:date | Representa datas no formato YYYY-MM-DD (ano, mês, dia). |

> [!TIP] DICAS:
> - O tipo xs:date segue o formato YYYY-MM-DD. Em XML, um elemento com data deve ser declarado como `<xs:element name="datanasc" type="xs:date"/>`.
> - Em provas, fique atento para não confundir com sintaxe de DTD, que usa `<!ELEMENT>` e `#PCDATA`.

## 4. Restrições em XSD

### 4.1 Restrições com Padrões (Pattern)
- xs:restriction: Restringe a base (ex.: xs:string) a uma forma mais específica.
- xs:pattern: Define um padrão que o valor do elemento deve seguir, usando expressões regulares.

#### 4.1.1 Exemplo com Expressão Regular
```xml
<xs:element name="cargo">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:pattern value="[a-z]+"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```
- A expressão regular [a-z]+ indica que o elemento "cargo" pode conter uma ou mais letras minúsculas de 'a' a 'z'.

> [!CAUTION] OBSERVAÇÃO:
> - Para restringir um elemento a letras minúsculas, usa-se `<xs:pattern value="[a-z]+"/>`.
> - Não confundir com `[a-z]` (apenas uma letra) ou com `$[a-z]` (início de linha e letra).
> - No XML válido, o valor deve estar em letra minúscula (ex.: "analista").

### 4.2 Estrutura da Restrição
```xml
<xs:element name="elemento">
  <xs:simpleType>
    <xs:restriction base="xs:tipo">
      <xs:pattern value="expressao"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

## 5. Representação de Elementos em XML

### 5.1 Sintaxe XML versus XSD
- No XML, a representação correta de um elemento com atributo é:
```xml
<organization category="justice">MPEPB123</organization>
```

> [!CAUTION] OBSERVAÇÃO:
> - A forma correta no XML é sempre com o atributo no formato `atributo="valor"`.
> - Sintaxes incorretas comuns: `<element:organization attribute:category value:justice>`, `<organization category("justice")>`, ou separando o atributo do conteúdo.

## 6. Principais Características do XSD

### 6.1 Pontos Essenciais para Provas
- XSD suporta tipos de dados e namespaces, diferentemente do DTD.
- XSD é escrito em XML (sintaxe com `xs:`).
- DTD usa sintaxe própria (`<!ELEMENT>`, `#PCDATA`, `<!ATTLIST>`).

### 6.2 Comparativo DTD × XSD
| DTD | XSD |
|-----|-----|
| Não suporta tipos de dados. | Suporta tipos de dados primitivos. |
| Sintaxe própria. | Sintaxe baseada em XML. |
| Menos expressivo. | Mais expressivo e flexível. |
| Não suporta namespaces. | Suporta namespaces. |

> [!TIP] DICAS:
> - Se a questão mencionar "suporte a tipos de dados" e "namespaces", a resposta é XML Schema (XSD).
> - Se mencionar apenas "estrutura de documentos", pode ser DTD, mas o XSD é mais completo.
> - Em provas, "XML Schema" e "XSD" são sinônimos.