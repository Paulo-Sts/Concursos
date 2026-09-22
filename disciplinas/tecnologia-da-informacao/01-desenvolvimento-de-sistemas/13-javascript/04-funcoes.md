# Funções

## 1. Conceitos Fundamentais
- Funções são blocos de código projetados para realizar tarefas específicas e podem ser reutilizadas.
- São executadas quando algo as chama, sendo necessários gatilhos como ações do usuário (inserir valor ou clicar em botão).
- Podem aceitar parâmetros para receber informações variáveis (números, nomes, frases) durante a execução.
- Isolam lógicas específicas, permitindo flexibilidade e reaproveitamento.

## 2. Declaração de Funções

### 2.1 Declaração Direta com Function
- Forma mais comum: uso da palavra-chave `function`, seguida do nome, parênteses e chaves.
- Exemplo:
```javascript
function soma(a, b) { 
  return a + b; 
}
console.log(soma(3, 2)); // 5
```
- Suscetível ao hoisting: a função é elevada ao topo do código, permitindo chamada antes da declaração.
- Funções podem ser chamadas antes de sua definição no código, dentro do mesmo escopo.

### 2.2 Funções Associadas a Variáveis (Expressões de Função)
- Funções podem ser anônimas ou nomeadas e associadas a variáveis.
- Exemplo de função anônima:
```javascript
const quadrado = function(x) {
  return x * x;
};
```
- Exemplo de função nomeada:
```javascript
const fatorial = function fat(n) {
  return n <= 1 ? 1 : n * fat(n - 1);
};
```
- Não são suscetíveis ao hoisting quando declaradas com `let` ou `const`.
- Com `var`, a variável é elevada, mas não inicializada, impedindo acesso prévio.
- Não é possível acessar ou executar a função antes de sua definição.

> [!TIP] DICAS:
> - Funções recursivas precisam ser nomeadas para que possam referenciar a si mesmas.
> - A nomeação de funções em expressões ajuda na depuração de pilhas de chamadas.

## 3. Arrow Functions
- Introduzidas no ES6, também chamadas de funções de flecha, usam a sintaxe `=>`.
- São funções anônimas, sempre associadas a variáveis.
- Exemplos:
  - Sem parâmetros:
```javascript
const semParametros = () => 'Sem parâmetros';
console.log(semParametros()); // Sem parâmetros
```
  - Com um parâmetro (parênteses opcionais):
```javascript
const quadrado = x => x * x;
console.log(quadrado(3)); // 9
```
  - Com múltiplos parâmetros (parênteses obrigatórios):
```javascript
const soma = (a, b) => a + b;
console.log(soma(2, 3)); // 5
```
- Para múltiplas instruções, usar chaves e `return` explícito:
```javascript
const multiplica = (a, b) => {
  let resultado = a * b;
  return resultado;
};
console.log(multiplica(2, 3)); // 6
```
- Para retornar um objeto, envolvê-lo entre parênteses:
```javascript
const criaPessoa = (nome, idade) => ({ nome, idade });
console.log(criaPessoa("Alice", 25)); // { nome: "Alice", idade: 25 }
```

> [!CAUTION] OBSERVAÇÃO:
> - Em Arrow Functions com múltiplas instruções, as chaves são obrigatórias e o `return` deve ser explícito.
> - Para retornar objetos literais em Arrow Functions, é necessário usar parênteses para evitar conflito com as chaves do bloco.

## 4. Funções Construtoras
- Utilizadas para criar objetos, definidas com a palavra-chave `function` e chamadas com `new`.
- Exemplo:
```javascript
function Pessoa(nome, idade) {
  this.nome = nome;
  this.idade = idade;
  this.descrever = function() {
    return `${this.nome} tem ${this.idade} anos.`;
  };
}
const pessoa1 = new Pessoa("Alice", 24);
const pessoa2 = new Pessoa("Bob", 30);
console.log(pessoa1.descrever()); // "Alice tem 24 anos."
console.log(pessoa2.descrever()); // "Bob tem 30 anos."
```
- Métodos podem ser definidos diretamente no objeto utilizando `this`.
- Permitem criar múltiplas instâncias com propriedades e comportamentos compartilhados.

## 5. Funções Assíncronas
- Utilizadas para operações que dependem de respostas externas, como requisições a APIs.
- Declaradas com a palavra-chave `async`.
- Utilizam `await` para aguardar a resolução de promessas.
- Exemplo:
```javascript
async function buscarDados() {
  let dados = await fetch('url');
  let resposta = await dados.json();
  console.log(resposta);
}
```
- O `fetch` obtém a resposta da URL especificada; `await` pausa a execução até a resposta chegar.
- Após a resposta, os dados são convertidos para JSON com `await dados.json()`.
- Permitem que outras operações continuem enquanto a resposta não chega.

> [!TIP] DICAS:
> - Funções assíncronas são ideais para operações de rede, leitura de arquivos e temporizadores.
> - Sempre tratar possíveis erros com `try...catch` ao usar `await`.