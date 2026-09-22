# Json E Api Rest

## 1. Json (Javascript Object Notation)

### 1.1 Definição e Propósito
- JSON significa "Notação de Objeto Javascript" e é um formato leve de armazenar e transportar dados.
- É derivado da notação de objetos do JavaScript, mas é independente dele, sendo usado em muitas linguagens de programação por meio de bibliotecas disponíveis.
- É comumente usado para enviar dados entre um servidor e uma aplicação web ou entre sistemas computacionais.
- É usado principalmente em APIs (Interfaces de Programação de Aplicações) e configurações web, devido à sua simplicidade e capacidade de ser rapidamente interpretado e gerado por diversas tecnologias.

### 1.2 Formato Leve
- Simplicidade de estrutura, com pares de chave e valor;
- Facilidade de implementação, já que se baseia em texto;
- Economia de banda, pois não é tão denso quanto o XML;
- Rapidez no processamento, sendo ainda mais rápido que o XML;
- Flexibilidade, porque pode transportar desde dados mais simples até os mais complexos.

### 1.3 Estrutura
- JSON é construído com duas estruturas fundamentais:
  - Uma coleção de pares nome/valor (em várias linguagens, isso é realizado como um objeto, registro, struct, dicionário, tabela hash, lista com chaves ou um array associativo);
  - Uma lista ordenada de valores (na maioria das linguagens, isso é realizado como um array, vetor, lista ou sequência).

### 1.4 Componentes Básicos
- Objetos: delimitados por chaves `{}` e contêm pares chave/valor separados por vírgulas. Exemplo: `{ "nome": "João", "idade": 30 }`.
- Arrays: delimitados por colchetes `[]` e contêm valores ordenados separados por vírgulas. Exemplo: `[ "maçã", "banana", "cereja" ]`.
- Valores: podem ser string (entre aspas duplas), número (sem aspas), objeto JSON, array, true, false ou null (ausência de valor).

### 1.5 Exemplos

#### 1.5.1 Objeto Simples
- Estrutura entre chaves, com pares chave/valor separados por vírgulas. As chaves são strings entre aspas; os valores podem ser strings (entre aspas), números, booleanos ou null.
```json
{
  "nome": "Carlos",
  "idade": 28,
  "ativo": true
}
```

#### 1.5.2 Array de Objetos
- É comum armazenar múltiplos objetos de mesma estrutura dentro de um array.
```json
[
  { "nome": "Carlos", "idade": 28 },
  { "nome": "Fernanda", "idade": 32 }
]
```

#### 1.5.3 Arrays Mistos e Objetos Aninhados
- É possível combinar objetos, arrays e valores primitivos dentro de uma mesma estrutura.
```json
{
  "identificador": 78912,
  "historico": ["login", "logout", "update"],
  "configuracoes": {
    "background": "claro",
    "notificacoes": true
  },
  "notas": [10, 9.5, 8, 7]
}
```
- Nesse exemplo, o objeto contém:
  - Chave `identificador` com valor numérico;
  - Chave `historico` com um array de strings;
  - Chave `configuracoes` com um objeto aninhado (background e notificações);
  - Chave `notas` com um array de números.

> [!TIP] DICAS: 
> - Strings sempre entre aspas duplas; números, booleanos e null não usam aspas.
> - Objetos são delimitados por `{}`; arrays por `[]`.
> - A vírgula separa elementos de um mesmo nível, mas não deve haver vírgula após o último elemento.

> [!CAUTION] OBSERVAÇÃO: 
> - JSON não suporta comentários, funções ou datas nativas; esses precisam ser representados como strings ou números.

## 2. Api Rest (Representational State Transfer)

### 2.1 Definição e Propósito
- REST é um estilo de arquitetura que define um conjunto de regras para criar serviços web que são fáceis de manter e escalar.
- Tem o mesmo propósito de uma arquitetura orientada a SOAP, mas é diferente em sua abordagem.
- Geralmente utiliza métodos HTTP como protocolo de transporte.

### 2.2 Princípios de Uma Api Rest

#### 2.2.1 Uso de Métodos Http Padronizados
- GET: usado para recuperar informações sobre um recurso;
- POST: usado para criar um novo recurso;
- PUT: usado para atualizar um recurso existente;
- DELETE: usado para deletar um recurso.
- Esses métodos correspondem às operações CRUD (Create, Read, Update, Delete):
  - Create ⟶ POST;
  - Read ⟶ GET;
  - Update ⟶ PUT;
  - Delete ⟶ DELETE.

#### 2.2.2 Comunicação Sem Estado (Stateless)
- Cada requisição deve conter todas as informações necessárias para ser compreendida pelo servidor.
- Não há dependência de estado armazenado no servidor entre requisições (não é feito em etapas).

#### 2.2.3 Recursos Identificáveis Por Urls
- Cada recurso (ex.: usuário, produto) deve ter uma URL única que o identifique.
- Exemplo: `https://api.exemplo.com/usuarios/123`.

#### 2.2.4 Representações
- Os recursos podem ser representados em vários formatos, como JSON, XML, HTML, entre outros.
- Os tipos de dados mais utilizados em requisições e respostas são JSON e XML.

### 2.3 Openapi (Swagger)
- É um conjunto de ferramentas de software de código aberto para projetar, construir, documentar e usar serviços web RESTful.
- Ajuda a definir uma linguagem padrão e interativa para APIs REST, permitindo que humanos e computadores entendam as capacidades de um serviço sem acesso direto ao código-fonte.
- Contribui para o desenvolvimento de APIs RESTful permitindo a documentação padronizada e interativa das APIs.

> [!TIP] DICAS: 
> - A diferença entre PUT e POST: PUT é idempotente (mesma requisição várias vezes produz o mesmo efeito), POST não é.
> - REST não é um protocolo, mas um estilo arquitetural; o protocolo mais comum associado é o HTTP.

> [!CAUTION] OBSERVAÇÃO: 
> - A comunicação sem estado é um princípio obrigatório no REST; qualquer violação descaracteriza a arquitetura.
> - O uso de JSON é preferencial, mas não obrigatório; o formato pode ser negociado entre cliente e servidor (ex.: via cabeçalho Accept).