# Variáveis e Arrays

## 1. Sobre Javascript
- É uma linguagem de programação de alto nível, amplamente utilizada para criar interatividade em páginas da web.
- Alto nível significa que é uma linguagem mais próxima da fala humana do que da linguagem de máquina.
- Originalmente desenvolvida para ser executada nos navegadores, agora também utilizada em ambientes fora do navegador, como no desenvolvimento de aplicativos móveis e desktop.
- Exemplo: Biblioteca React e React Native para criação de sites e aplicativos.

## 2. Hoisting
- Comportamento em Javascript que permite acessar funções e variáveis antes de serem declaradas.
- Ocorre porque na fase de compilação, as declarações são elevadas ao topo do escopo, mas não são inicializadas.
- Funções e variáveis são declaradas, mas as variáveis não são inicializadas no processo de hoisting.
- Exemplo:
```javascript
console.log(minhaFuncao()); // 'olá!'
function minhaFuncao() {
  return 'olá!';
}
```

> [!CAUTION] OBSERVAÇÃO:
> - O retorno da variável é "undefined". O código percebe que a variável existe em algum local, mas não acessa seu valor pois ela ainda não foi inicializada.

## 3. Variáveis

### 3.1 Var
- Têm escopo de função.
- Valores podem variar.
- São suscetíveis ao hoisting.
- Exemplo de hoisting com var:
```javascript
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```

- Exemplo de escopo de função:
```javascript
function exemplovar() {
  var x = 10;
  if (true) {
    var x = 20;
    console.log(x); // 20
  }
  console.log(x); // 20
}
```

> [!TIP] DICAS:
> - Escopo de função significa que o valor da variável vai mudar durante a função.
> - Bloco de códigos é tudo o que está entre chaves {}.
> - No exemplo acima, "function exemploVar() {" é a função.

### 3.2 Let
- Introduzida no ECMAScript 6 (ES6).
- Valores podem variar.
- Têm escopo de bloco (entre {}).
- Não são suscetíveis ao hoisting.
- Exemplo:
```javascript
console.log(x); // Error: ReferenceError: Cannot access 'x' before initialization
let x = 5;
console.log(x); // 5
```

- Exemplo de escopo de bloco:
```javascript
function exemploLet() {
  let x = 10;
  if (true) {
    let x = 20;
    console.log(x); // 20
  }
  console.log(x); // 10
}
```

> [!CAUTION] OBSERVAÇÃO:
> - Como a variável let não tem escopo de função, o "console.log(x);" fora do bloco continua com a saída 10.

### 3.3 Const
- Introduzida no ECMAScript 6 (ES6).
- Valores são constantes.
- Têm escopo de bloco (entre {}).
- Não são suscetíveis ao hoisting.
- Exemplo:
```javascript
console.log(x); // Erro: ReferenceError: Cannot access 'x' before initialization
const x = 5;
console.log(x); // 5
```

- Exemplo de erro ao tentar reatribuir:
```javascript
function exemploConst() {
  const x = 10;
  x = 20; // Isso resultaria em um erro porque x é uma constante
  console.log(x); // 10
}
```

> [!CAUTION] OBSERVAÇÃO:
> - Resulta em erro porque o valor é constante, ou seja, não pode ser redefinido.

### 3.4 Comparativo entre Var, Let e Const
| CARACTERÍSTICA | VAR | LET | CONST |
|----------------|-----|-----|-------|
| Escopo | Função | Bloco | Bloco |
| Hoisting | Sim (undefined) | Não (erro) | Não (erro) |
| Redeclaração | Permite | Não permite | Não permite |
| Reatribuição | Permite | Permite | Não permite |

## 4. Arrays

### 4.1 Conceito
- Estrutura de dados que pode armazenar vários elementos em uma única variável.
- Dentro de um array é possível colocar strings, números, objetos, etc.
- São dinâmicos - tamanho se altera conforme necessidade.

### 4.2 Formas de Declaração

#### 4.2.1 Array Literals (mais comum)
```javascript
let numeros = [1, 2, 3, 4, 5];
let nomes = ["Maria", "João", "Ana"];
let misturado = [1, "dois", true, { chave: "valor" }];
```

#### 4.2.2 Construtor Array
```javascript
let numeros = new Array(10);
let frutas = new Array('maçã', 'banana', 'laranja');
```
> [!CAUTION] OBSERVAÇÃO:
> - Construtores são tipos especiais de funções associadas a uma classe quando um objeto dessa classe é criado.

#### 4.2.3 Array.of()
- Argumentos passados são elementos.
- Exemplo:
```javascript
let numeros = Array.of(1, 2, 3); // Cria um array [1, 2, 3]
let misto = Array.of(10, 'maçã', true); // Cria um array [10, 'maçã', true]
```

#### 4.2.4 Array.from()
- Cria array a partir de um objeto iterável.
- Transforma uma string em um array de caracteres.
- Exemplo:
```javascript
let stringToArray = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
let setToArray = Array.from(new Set([1, 2, 3])); // [1, 2, 3]
```

#### 4.2.5 Spread Operator
- Copia os elementos de um array para um novo array.
- Exemplo:
```javascript
let frutasOriginais = ['maçã', 'banana'];
let frutasNovas = [...frutasOriginais, 'laranja']; // ['maçã', 'banana', 'laranja']
```
> [!TIP] DICAS:
> - Os arrays mais utilizados são os literais.
> - Quando aparecerem reticências em uma questão, trata-se do Spread Operator (copiando itens de um array para outro).

### 4.3 Métodos de Arrays

#### 4.3.1 Acesso por Índice
- Cada elemento tem um índice que serve para identificá-lo.
- Os índices sempre começam do zero.
- Exemplo:
```javascript
let numeros = [1, 2, 3, 4, 5];
console.log(numeros[0]); // 1
console.log(numeros[2]); // 3
```

#### 4.3.2 Modificação de Valores
```javascript
let numeros = [1, 2, 3, 4, 5];
numeros[2] = 10;
console.log(numeros); // [1, 2, 10, 4, 5]
```

#### 4.3.3 Length
- Retorna o número de elementos no array (tamanho).
- Exemplo:
```javascript
let numeros = [1, 2, 3];
console.log(numeros.length); // 3
```

#### 4.3.4 Push
- Adiciona elementos ao final do array.
- Exemplo:
```javascript
let frutas = ['maçã', 'banana'];
frutas.push('laranja');
console.log(frutas); // ['maçã', 'banana', 'laranja']
```

#### 4.3.5 Pop
- Remove o último elemento do array e o retorna.
- Exemplo:
```javascript
let numeros = [1, 2, 3];
let ultimo = numeros.pop();
console.log(ultimo); // 3
console.log(numeros); // [1, 2]
```

#### 4.3.6 Shift
- Remove o primeiro elemento do array e o retorna.
- Exemplo:
```javascript
let frutas = ['maçã', 'banana', 'laranja'];
let primeira = frutas.shift();
console.log(primeira); // 'maçã'
console.log(frutas); // ['banana', 'laranja']
```

#### 4.3.7 Unshift
- Adiciona elementos no início do array.
- Exemplo:
```javascript
let frutas = ['banana', 'laranja'];
frutas.unshift('maçã');
console.log(frutas); // ['maçã', 'banana', 'laranja']
```

#### 4.3.8 Concat
- Combina o array original com outros arrays/valores.
- Exemplo:
```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const result = array1.concat(array2);
console.log(result); // ['a', 'b', 'c', 'd', 'e', 'f']

const letras = ['A', 'B'];
const maisLetras = ['C', 'D'];
const numeros = [1, 2, 3];
const result2 = letras.concat(maisLetras, numeros, 'E');
console.log(result2); // ['A', 'B', 'C', 'D', 1, 2, 3, 'E']
```

#### 4.3.9 LastIndexOf
- Retorna o índice da última ocorrência de um valor especificado dentro de uma string ou array.
- Exemplo:
```javascript
let texto = "Olá, mundo! Olá, todos!";
console.log(texto.lastIndexOf("Olá")); // 12
console.log(texto.lastIndexOf("Olá", 10)); // 0
console.log(texto.lastIndexOf("olá")); // -1 (case-sensitive)
```
> [!CAUTION] OBSERVAÇÃO:
> - Na contagem dos índices, pontuações e espaços também são considerados.
> - Javascript faz distinção entre maiúsculas e minúsculas (case-sensitive).
> - "olá" com todas as letras minúsculas não será considerado na busca.

- Exemplo com array:
```javascript
let numeros = [2, 5, 9, 2];
console.log(numeros.lastIndexOf(2)); // 3
console.log(numeros.lastIndexOf(7)); // -1
```

#### 4.3.10 Join
- Junta todos os elementos de um array em uma string.
- Possibilidade de definir o caractere de concatenação.
- Exemplo:
```javascript
let frutas = ['Maçã', 'Banana', 'Laranja'];
console.log(frutas.join()); // "Maçã,Banana,Laranja"
console.log(frutas.join(' - ')); // "Maçã - Banana - Laranja"
```
> [!CAUTION] OBSERVAÇÃO:
> - Por padrão, a lista será transformada em texto separado por vírgula e sem espaço.
> - É possível separar os itens da lista com algum elemento definido como parâmetro.

#### 4.3.11 IndexOf
- Retorna o primeiro índice em que um elemento pode ser encontrado no array.
- Exemplo:
```javascript
let frutas = ['Maçã', 'Banana', 'Laranja'];
console.log(frutas.indexOf('Banana')); // 1
console.log(frutas.indexOf('Uva')); // -1
```

#### 4.3.12 Slice
- Extrai uma parte de um array e retorna um novo array.
- Exemplo:
```javascript
let frutas = ['Maçã', 'Laranja', 'Limão', 'Pera'];
console.log(frutas.slice(1)); // ['Laranja', 'Limão', 'Pera']
console.log(frutas.slice(1, 3)); // ['Laranja', 'Limão']
```
> [!CAUTION] OBSERVAÇÃO:
> - Se não for colocado nenhum parâmetro, o slice "cortará" o array da posição definida até o final.
> - Quando se define um parâmetro final, a última posição não é considerada.
> - O slice não modifica o array original.

#### 4.3.13 Splice
- Modifica o conteúdo de um array adicionando, removendo e substituindo elementos.
- Sintaxe: array.splice(começo, qtdDeletada, item1, item2...);
- Removendo itens:
```javascript
const tarefas = ['Estudar', 'Comprar pão', 'Ir ao médico', 'Pagar contas'];
const removidos = tarefas.splice(1, 2);
console.log(tarefas); // ['Estudar', 'Pagar contas']
console.log(removidos); // ['Comprar pão', 'Ir ao médico']
```
> [!TIP] DICAS:
> - No splice, é colocada a quantidade de elementos que se quer deletar, e não a posição final do array.

- Adicionando itens:
```javascript
let frutas = ['Maçã', 'Banana', 'Pera'];
frutas.splice(2, 0, 'Laranja', 'Manga'); // não remove itens
console.log(frutas); // ['Maçã', 'Banana', 'Laranja', 'Manga', 'Pera']
```

- Substituindo itens:
```javascript
const convidados = ['Ana', 'Carlos', 'Márcia', 'Paulo'];
const substituídos = convidados.splice(1, 2, 'Julia', 'Ricardo');
console.log(convidados); // ['Ana', 'Julia', 'Ricardo', 'Paulo']
console.log(substituídos); // ['Carlos', 'Márcia']
```