# Condicionais e Loops

## 1. Estruturas Condicionais
- Estruturas condicionais permitem que o código execute diferentes blocos com base em condições lógicas.

### 1.1 If...Else
- O `if` executa um bloco de código se a expressão for verdadeira.
- O `else if` especifica uma nova condição se a primeira for falsa.
- O `else` será executado se nenhuma condição anterior for verdadeira.
- Sintaxe:
  ```javascript
  let idade = 18;
  if (idade >= 18) {
    console.log("Você é maior de idade.");
  }
  ```
- Exemplo com múltiplas condições:
  ```javascript
  let hora = 14;
  if (hora < 12) {
    console.log("Bom dia!");
  } else if (hora < 18) {
    console.log("Boa tarde!");
  } else {
    console.log("Boa noite!");
  }
  ```
- Exemplo com operador lógico OR:
  ```javascript
  let diaSemana = "domingo";
  if (diaSemana == "sábado" || diaSemana == "domingo") {
    console.log("É fim de semana!");
  } else {
    console.log("Não é fim de semana.");
  }
  ```

### 1.2 Operador Ternário
- Forma abreviada de escrever uma declaração `if-else`.
- Estrutura: `(condição) ? valor_se_verdadeiro : valor_se_falso`.
- Exemplo:
  ```javascript
  let idade = 20;
  let mensagem = (idade >= 18) ? "Você é maior de idade." : "Você é menor de idade.";
  console.log(mensagem);
  ```

### 1.3 Switch
- Alternativa ao `if...else` para definir várias condições possíveis para uma expressão.
- Utiliza `case` para cada condição e `break` para interromper a execução.
- O `default` é executado se nenhum `case` for atendido.
- Exemplo:
  ```javascript
  let diaSemana = 3;
  let mensagem;
  switch (diaSemana) {
    case 1:
      mensagem = "Segunda-feira";
      break;
    case 2:
      mensagem = "Terça-feira";
      break;
    case 3:
      mensagem = "Quarta-feira";
      break;
    case 4:
      mensagem = "Quinta-feira";
      break;
    case 5:
      mensagem = "Sexta-feira";
      break;
    case 6:
    case 7:
      mensagem = "Fim de semana";
      break;
    default:
      mensagem = "Dia inválido";
  }
  console.log(mensagem); // Saída: "Quarta-feira"
  ```

> [!TIP] DICAS:
> - A instrução `default` será executada caso nenhuma das instruções `case` seja atendida.
> - No `switch`, os `case` sem `break` executam os blocos seguintes (fall-through).

> [!CAUTION] OBSERVAÇÃO:
> - Em JavaScript, variáveis declaradas com `const` não podem ser reatribuídas. Tentar modificar seu valor resultará em erro, portanto, o código não será executado e a variável não será impressa.
> - O `switch` compara valores com `===` (igualdade estrita).

## 2. Estruturas de Repetição (Loops)
- Loops executam uma operação repetidamente até que uma condição seja satisfeita.

### 2.1 For
- Utilizado quando se sabe exatamente quantas vezes o código deve ser repetido.
- Funciona com um índice que é incrementado a cada iteração.
- O índice deve ser declarado com `let` ou `var`, pois seu valor é modificado.
- Estrutura: `for (inicialização; condição; incremento) { bloco }`.
- Exemplo:
  ```javascript
  for (let i = 0; i < 5; i++) {
    console.log(i); // Saída: 0, 1, 2, 3, 4
  }
  ```

### 2.2 While
- Executa um bloco de código enquanto uma condição especificada for verdadeira.
- A condição é verificada antes de cada iteração.
- Exemplo:
  ```javascript
  let i = 0;
  while (i < 5) {
    console.log(i); // Saída: 0, 1, 2, 3, 4
    i++;
  }
  ```

### 2.3 Do...While
- Semelhante ao `while`, mas a condição é verificada após a execução do bloco.
- Garante que o bloco de código seja executado pelo menos uma vez.

### 2.4 For...Of
- Usado para iterar sobre elementos de iteráveis (arrays, strings, etc.).
- Mais simples e direto para percorrer valores.
- Exemplo:
  ```javascript
  let numeros = [1, 2, 3, 4, 5];
  for (let numero of numeros) {
    console.log(numero); // Saída: 1, 2, 3, 4, 5
  }
  ```

> [!CAUTION] OBSERVAÇÃO:
> - O loop `for...of` itera sobre elementos iteráveis, exceto objetos. Objetos não são iteráveis diretamente por `for...of`.

### 2.5 For...In
- Usado para iterar sobre as propriedades de um objeto.
- Percorre as chaves (propriedades) do objeto.
- Exemplo:
  ```javascript
  let carro = { marca: 'Ford', modelo: 'Focus', ano: 2020 };
  for (let chave in carro) {
    console.log(chave + ':' + carro[chave]); // Saída: marca: Ford, modelo: Focus, ano: 2020
  }
  ```

### Comparação entre Loops
| TIPO | ITERA SOBRE | USO PRINCIPAL |
|------|-------------|---------------|
| For | Índice numérico | Repetições com contador |
| While | Condição lógica | Repetições com condição variável |
| Do...While | Condição lógica (pós-teste) | Execução garantida ao menos uma vez |
| For...Of | Valores de iteráveis | Arrays, strings, Map, Set |
| For...In | Chaves de objetos | Propriedades de objetos |

### Tabela
| TIPO DE LOOP | ITERA SOBRE | EXEMPLO DE USO |
|--------------|-------------|----------------|
| For | Índice numérico | Repetir um bloco N vezes |
| While | Condição lógica | Repetir até que uma condição mude |
| Do...While | Condição lógica (pós-teste) | Validar entrada do usuário |
| For...Of | Valores de iteráveis | Percorrer elementos de um array |
| For...In | Chaves de objetos | Percorrer propriedades de um objeto |