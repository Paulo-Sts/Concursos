# Orientação a Objetos

## 1. Orientação a Objetos
- Paradigma de programação que permite modelar o mundo real por meio da criação de objetos que contêm dados (propriedades) e comportamentos (métodos).

## 2. Propriedades e Métodos
- Propriedades: Valores associados a um objeto que representam suas características (ex.: nome, idade, altura).
- Métodos: Funções associadas a um objeto que representam suas ações ou comportamentos (ex.: caminhar(), falar(), comer()).

## 3. Objetos
- Coleção de pares chave-valor, onde:
  - Chaves (propriedades): atributos que descrevem o objeto;
  - Valores: podem ser números, strings, arrays, funções (métodos), outros objetos, etc.
- Exemplo:
```javascript
let pessoa = {
  nome: "João",
  idade: 30,
  saudacao: function() {
    return "Olá, meu nome é " + this.nome + " e tenho " + this.idade + " anos.";
  }
};
console.log(pessoa.nome); // Saída: João
console.log(pessoa.saudacao()); // Saída: Olá, meu nome é João e tenho 30 anos.
```

## 4. Classes
- JavaScript foi projetado como linguagem orientada a objetos baseada em protótipos.
- A especificação ECMAScript 2015 (ES6) introduziu a sintaxe de classes.
- Facilita a implementação de programação orientada a objetos (POO), especialmente para quem conhece linguagens como Java e C++.

> [!TIP] DICAS:
> - A sintaxe de classe do ES6 é um "açúcar sintático" sobre o sistema de protótipos do JavaScript. As classes, na verdade, são objetos e tudo ocorre dinamicamente.

## 5. Estendendo Classes (Extends)
- super: Palavra-chave usada para:
  - Chamar o construtor da classe pai (classe base) dentro de uma subclasse (classe filha);
  - Acessar métodos ou propriedades da classe pai.
- extends: Palavra-chave usada para:
  - Implementar a herança entre classes;
  - Permitir que uma subclasse herde as propriedades e métodos da superclasse;
  - Reutilizar, sobrescrever e adicionar métodos.
- Exemplo:
```javascript
class Animal {
  constructor(tipo) {
    this.tipo = tipo;
  }
  fazerSom() {
    console.log("Fazendo som...");
  }
}

class Cachorro extends Animal {
  constructor(raca) {
    super("cachorro");
    this.raca = raca;
  }
  latir() {
    console.log("Au au!");
  }
}
```

## 6. Prototype
- Base da herança em JavaScript.
- Todo objeto tem uma referência a um prototype (objeto "pai") de onde herda propriedades e métodos.
- Se um método não é encontrado no próprio objeto, é buscado no prototype.
- A partir do ES6, os construtores são mais usados que os prototypes de forma explícita.

> [!CAUTION] OBSERVAÇÃO:
> - Em JavaScript, tudo pode ser considerado um objeto. Não há distinção rígida entre tipos e objetos.

## 7. Herança
- Permite que uma classe (ou objeto) herde propriedades e métodos de outra.
- Promove reutilização de código e facilita a extensão de funcionalidades.
- Possibilita a criação de classes que adquirem atributos e comportamentos de outras, promovendo estruturação hierárquica e facilitando a manutenção e extensibilidade dos sistemas.
- Analogia: Classes são formulários com campos a serem preenchidos; objetos são os formulários já preenchidos.
- Exemplo:
```javascript
class Animal {
  constructor(tipo) {
    this.tipo = tipo;
  }
}

class Cachorro extends Animal {
  falar() {
    console.log('Au Au!');
  }
}

const cachorro = new Cachorro('Cachorro');
cachorro.falar(); // Saída: Au Au!
```

## 8. Construtores
- Funções especiais que criam e inicializam objetos de uma classe.
- No ES6, a herança é facilitada pelo uso de classes e do método constructor.
- Aloca memória para o objeto e inicializa suas propriedades com valores padrão ou com valores passados como argumentos.

## 9. Encapsulamento
- Agrupamento de propriedades e métodos dentro de um objeto e controle do acesso a essas informações.
- Garante a integridade dos dados e a segurança do código.
- JavaScript não possui modificadores de acesso como "private", "protected" ou "public" nativamente, mas é possível simular usando técnicas específicas.
- Permite que os detalhes de implementação de um objeto sejam alterados sem afetar o restante do sistema, tornando o código mais flexível e fácil de manter.
- Exemplo:
```javascript
function Conta() {
  let saldo = 0; // Propriedade privada
  this.depositar = function(valor) {
    saldo += valor;
  };
  this.verSaldo = function() {
    return saldo;
  };
}

const minhaConta = new Conta();
minhaConta.depositar(100);
console.log(minhaConta.verSaldo()); // Saída: 100
console.log(minhaConta);
// Saída:
// Conta {
//   depositar: [Function (anonymous)],
//   verSaldo: [Function (anonymous)]
// }
```

## 10. Polimorfismo
- Capacidade de uma função fazer coisas diferentes dependendo do objeto que está sendo usado.
- Permite que funções com o mesmo nome, dependendo do contexto, retornem resultados diferentes.
- Refere-se à capacidade de um único método ou função trabalhar de maneira diferente com diferentes tipos de objetos.
- Propriedade de se usar o mesmo nome para métodos diferentes, implementados em diferentes níveis de uma hierarquia de classes e chamados em tempo de execução (vinculação dinâmica). Para cada classe, tem-se um comportamento específico para o método.
- Exemplo:
```javascript
class Animal {
  falar() {
    return 'Som genérico';
  }
}

class Cachorro extends Animal {
  falar() {
    return 'Au Au!';
  }
}

const animal = new Animal();
const cachorro = new Cachorro();

console.log(animal.falar()); // Saída: Som genérico
console.log(cachorro.falar()); // Saída: Au Au!
```

## 11. Modularidade em OO
- Prática de dividir o código em módulos, classes ou objetos independentes e coesos.
- Módulo: Parte isolada do código que contém funcionalidades específicas.
- Modularizar permite:
  - Reutilização de código;
  - Manutenção facilitada;
  - Desenvolvimento e teste.
- Exemplo:
```javascript
// Pessoa.js
export class Pessoa {
  constructor(name, idade) {
    this.name = name;
    this.idade = idade;
  }
  saudacao() {
    console.log(`ola, meu nome é ${this.name} e tenho ${this.idade} anos.`);
  }
}

// main.js
import { Pessoa } from './Pessoa.js';
const pessoa = new Pessoa('João', 30);
pessoa.saudacao(); // Saída: Ola, meu nome é João e tenho 30 anos.
```

> [!TIP] DICAS:
> - Para utilizar um módulo em outro arquivo, é necessário usar a palavra-chave "export" no arquivo de origem e "import" no arquivo de destino.