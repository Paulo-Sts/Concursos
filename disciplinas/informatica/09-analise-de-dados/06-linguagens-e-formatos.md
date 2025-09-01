# Linguagens e Formatos

## 1. Níveis de organização de dados
- Não estruturados: Sem estrutura definida.
- Semiestruturados: Estrutura implícita, flexível (XML, JSON, CSV).
- Estruturados: Estrutura rígida e definida (bancos de dados relacionais).

## 2. XML (Extensible Markup Language)
- Linguagem de marcação para armazenar e transportar dados.
- Separa dados da apresentação.
- Semiestruturada e autodescritiva.
- Permite comunicação entre sistemas diferentes.
- Pertence à família SGML (como HTML).

#### Características
- Usa tags definidas pelo usuário (não predefinidas).
- Hierárquica (estrutura de árvore).
- Elementos podem ter atributos, valores e filhos.
- Arquivo com extensão `.xml`.

#### Sintaxe básica
- Deve ter um elemento raiz.
- Tags com fechamento: `<tag></tag>` ou `<tag/>`.
- Case sensitive.
- Elementos devem estar aninhados corretamente.
- Atributos entre aspas.
- Comentários: `<!-- comentário -->`.
- Caracteres especiais: `&lt;` para `<`, `&amp;` para `&`.

#### Validação
- **DTD (Document Type Definition):**
  - Define estrutura, elementos e atributos.
  - Pode ser interno ou externo.
  - Não valida tipos de dados.
  - Sintaxe própria (não XML).
- **XSD (XML Schema Definition):**
  - Define estrutura e valida conteúdos.
  - Suporta tipos de dados.
  - Escrito em XML.
  - Mais robusto que DTD.

## 3. JSON (JavaScript Object Notation)
- Formato de texto para armazenamento e transporte de dados.
- Derivado da notação de objetos JavaScript.
- Semiestruturado e autodescritivo.
- Codificação UTF-8.

#### Sintaxe
- Pares nome/valor: `"nome": "valor"`.
- Objetos entre chaves `{}`.
- Arrays entre colchetes `[]`.
- Dados separados por vírgulas.
- Tipos de dados: string, number, boolean, null, object, array.

#### Exemplo
```json
{
  "employees": [
    { "firstName": "John", "lastName": "Doe" },
    { "firstName": "Anna", "lastName": "Smith" }
  ]
}
```

#### Comparação com XML
- Mais simples e leve.
- Não suporta namespaces, comentários ou atributos.
- Hierarquia por aninhamento de objetos/arrays.

## 4. CSV (Comma-Separated Values)
- Formato de texto para dados tabulares.
- Semiestruturado com autodescrição rudimentar (baseada em posição).
- Usado para importação/exportação de dados.
- Codificações: UTF-8, ASCII, etc.

#### Características
- Linear (não hierárquico).
- Não suporta tipos de dados, namespaces, comentários ou tags.
- Leve e simples.

#### Sintaxe
- Valores separados por vírgula (ou outro delimitador).
- Cada linha representa um registro.
- Primeira linha pode ser cabeçalho (opcional).

#### Exemplo
```
nome,sobrenome,idade
João,Silva,30
Maria,Souza,25
```