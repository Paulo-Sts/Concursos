# Operadores

## 1. Operadores Matemáticos
- Os operadores matemáticos realizam operações aritméticas básicas entre valores (operandos).
- Lista de operadores comuns:
  - Adição: `+`;
  - Subtração: `-`;
  - Multiplicação: `*`;
  - Divisão: `/`.
- Operadores adicionais:
  - Módulo (`%`): Retorna o resto de uma divisão inteira entre dois números.
  - Exponenciação (`**`): Eleva um número à potência de outro.
- Incremento (`++`): Adiciona 1 ao valor de uma variável.
  - Pode ser usado como pré-incremento (`++a`): o valor é incrementado antes de ser utilizado na expressão.
  - Pode ser usado como pós-incremento (`a++`): o valor é utilizado na expressão e depois incrementado.
- Decremento (`--`): Subtrai 1 do valor de uma variável.
  - Funciona de forma análoga ao incremento, com pré-decremento (`--b`) e pós-decremento (`b--`).

### 1.1 Exemplos e Observações
- Exemplo de uso do módulo:
  - `let modulo = 5 % 3;` resulta em `2`, que é o resto da divisão de 5 por 3.
- Exemplo de uso da exponenciação:
  - `let exponenciacao = 2 ** 3;` resulta em `8`, que é 2 elevado a 3.
- Exemplo de uso do incremento:
  ```javascript
  let a = 5;
  console.log('Pré-incremento:', ++a); // 6 (a agora é 6)
  console.log('Pós-incremento:', a++); // 6 (a agora é 7)
  console.log(a); // 7
  ```
  - No pré-incremento, a variável é incrementada e seu novo valor é impresso.
  - No pós-incremento, o valor atual é impresso e depois a variável é incrementada.
- Exemplo de uso do decremento:
  ```javascript
  let b = 5;
  console.log('Pós-decremento:', b--); // 5 (b agora é 4)
  console.log('Pré-decremento:', --b); // 3 (b agora é 3)
  console.log(b); // 3
  ```
  - No pós-decremento, o valor atual é impresso e depois a variável é decrementada.
  - No pré-decremento, a variável é decrementada e seu novo valor é impresso.

> [!CAUTION] OBSERVAÇÃO:
> - O sinal de "=" a mais ou a menos nos operadores de comparação e atribuição é uma fonte comum de erros e pegadinhas em provas. É crucial entender a diferença entre eles.

## 2. Operadores de Comparação
- Utilizados para comparar dois valores, retornando um resultado booleano (`true` ou `false`).
- Os operadores podem comparar apenas o valor ou o valor e o tipo do dado.
- Lista de operadores:
  - Igualdade (`==`): Compara se dois valores são iguais, independentemente do tipo.
  - Igualdade Estrita (`===`): Compara se dois valores são iguais E do mesmo tipo.
  - Diferença (`!=`): Compara se dois valores são diferentes, independentemente do tipo.
  - Diferença Estrita (`!==`): Compara se dois valores são diferentes E/ou de tipos diferentes.
  - Maior (`>`): Retorna `true` se o valor da esquerda for maior que o da direita.
  - Maior ou Igual (`>=`): Retorna `true` se o valor da esquerda for maior ou igual ao da direita.
  - Menor (`<`): Retorna `true` se o valor da esquerda for menor que o da direita.
  - Menor ou Igual (`<=`): Retorna `true` se o valor da esquerda for menor ou igual ao da direita.

### 2.1 Exemplos e Observações
- Exemplo de igualdade (`==`):
  ```javascript
  console.log(5 == 5);   // true
  console.log(5 == '5'); // true
  ```
  - A igualdade comum (`==`) considera `5` (número) e `'5'` (string) como iguais porque converte os tipos antes de comparar.
- Exemplo de igualdade estrita (`===`):
  ```javascript
  console.log(5 === 5);   // true
  console.log(5 === '5'); // false
  ```
  - A igualdade estrita (`===`) retorna `false` para `5` e `'5'`, pois são de tipos diferentes.
- Exemplo de diferença (`!=`):
  ```javascript
  console.log(5 != 10);  // true
  console.log(5 != '5'); // false
  ```
  - A diferença comum (`!=`) considera `5` e `'5'` como iguais, portanto, a comparação `5 != '5'` é `false`.
- Exemplo de diferença estrita (`!==`):
  ```javascript
  console.log(5 !== '5'); // true
  console.log(5 !== 5);   // false
  ```
- Exemplos de maior/menor:
  ```javascript
  console.log(10 > 5);  // true
  console.log(5 >= 5);  // true
  console.log(5 < 10);  // true
  console.log(6 <= 5);  // false
  ```

> [!TIP] DICAS:
> - Use sempre `===` e `!==` para evitar comparações inesperadas que podem surgir da conversão automática de tipos.
> - A diferença entre `==` e `===` (e `!=` e `!==`) é um dos tópicos mais cobrados em provas de JavaScript.

## 3. Operadores Lógicos
- Utilizados para combinar expressões booleanas, retornando um novo valor booleano.
- Operadores:
  - AND (`&&`): Retorna `true` se, e somente se, todas as expressões forem `true`.
  - OR (`||`): Retorna `true` se pelo menos uma das expressões for `true`.
  - NOT (`!`): Inverte o valor booleano de uma expressão. `!true` vira `false`, e `!false` vira `true`.

### 3.1 Tabela Verdade
| EXPRESSÃO 1 | EXPRESSÃO 2 | AND (&&) | OR (||) |
|-------------|-------------|----------|---------|
| true        | true        | true     | true    |
| true        | false       | false    | true    |
| false       | true        | false    | true    |
| false       | false       | false    | false   |

### 3.2 Curto-Circuito (Short-Circuit)
- Em JavaScript, os operadores lógicos `&&` e `||` utilizam a avaliação de curto-circuito.
- Para o operador AND (`&&`): Se a primeira expressão for `false`, a segunda não é avaliada, pois o resultado final já será `false`.
- Para o operador OR (`||`): Se a primeira expressão for `true`, a segunda não é avaliada, pois o resultado final já será `true`.

### 3.3 Exemplos e Observações
- Exemplo de `&&`:
  ```javascript
  let x = 5;
  if (x > 0 && x < 10) {
      console.log("x está entre 0 e 10");
  }
  ```
  - A segunda condição (`x < 10`) só é avaliada se a primeira (`x > 0`) for verdadeira.
- Exemplo de `||`:
  ```javascript
  let x = 5;
  if (x === 0 || x === 5) {
      console.log("x é igual a 0 ou 5");
  }
  ```
- Exemplo de `!`:
  ```javascript
  console.log(!true);  // false
  console.log(!false); // true
  ```