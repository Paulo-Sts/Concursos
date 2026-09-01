# Funções 2

## 1. Métodos de Strings
- Strings são sequências de caracteres e possuem métodos para manipulação.
- Os métodos são chamados diretamente na string ou em uma variável que a contém.
- Exemplos:
  - `'hello'.substring(0, 3);` 
  - Explicação: extrai caracteres do índice 0 até o índice 3 (excluindo o 3), retornando `"hel"`.
  - `'hello'.toUpperCase();` 
  - Explicação: converte todos os caracteres para maiúsculas, retornando `"HELLO"`.
  - `'HELLO'.toLowerCase();` 
  - Explicação: converte todos os caracteres para minúsculas, retornando `"hello"`.

### Tabela - Métodos de Strings (Parte 1)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| substring() | Extrai parte de uma string e retorna uma nova. | `'hello'.substring(0, 3); // Saída: 'hel'` |
| toUpperCase() | Converte a string em maiúsculas. | `'hello'.toUpperCase(); // Saída: 'HELLO'` |
| toLowerCase() | Converte a string em minúsculas. | `'HELLO'.toLowerCase(); // Saída: 'hello'` |

- `substring(início, fim)`:
  - O início é o índice onde começa a extração (inclusivo).
  - O fim é o índice onde a extração para (exclusivo).
  - No exemplo `"Hello".substring(0, 3)`, o método começa no índice 0 (`H`), vai até o índice 3 (parando antes do caractere no índice 3, que é `l`), resultando em `"Hel"`.
- `toUpperCase()`:
  - Útil para padronizar entradas de usuários, como em formulários, garantindo que os dados sejam armazenados em um formato uniforme.
- `toLowerCase()`:
  - Similar ao `toUpperCase()`, mas converte para minúsculas.

> [!TIP] DICAS: 
> - `substring` é frequentemente usado para extrair partes específicas de textos, como primeiros nomes ou códigos.
> - Os métodos de conversão de caixa são essenciais para comparações case-insensitive entre strings.

### Tabela - Métodos de Strings (Parte 2)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| indexOf() | Retorna o índice da primeira ocorrência de um valor em uma string. | `'hello'.indexOf('e'); // Saída: 1` |
| charAt() | Retorna o caractere no índice especificado da string. | `'hello'.charAt(0); // Saída: 'h'` |
| replace() | Substitui uma substring por outra em uma string. | `'hello'.replace('e', 'a'); // Saída: 'hallo'` |

- `indexOf(valor)`:
  - Retorna o índice (posição) da primeira ocorrência do valor na string.
  - A contagem começa em 0 (primeiro caractere).
  - Exemplo: `"Hello".indexOf('e')` retorna `1`, pois `H` é índice 0 e `e` é índice 1.
  - Exemplo: `"Hello".indexOf('l')` retorna `2`, pois o primeiro `l` aparece no índice 2.
- `charAt(índice)`:
  - Retorna o caractere que está na posição especificada.
  - Exemplo: `"Hello".charAt(0)` retorna `"H"`.
  - Exemplo: `"Hello".charAt(2)` retorna `"l"`.
- `replace(valorAntigo, valorNovo)`:
  - Substitui a primeira ocorrência da substring `valorAntigo` por `valorNovo`.
  - Exemplo: `"Hello".replace('e', 'a')` retorna `"Hallo"`.
  - Exemplo: `"Hello".replace('llo', 'y')` retorna `"Heyo"`.

> [!CAUTION] OBSERVAÇÃO: 
> - O método `replace` só substitui a primeira ocorrência por padrão. Para substituir todas, é necessário usar expressões regulares.

## 2. Objeto Math
- O JavaScript possui um objeto embutido chamado `Math` com métodos para operações matemáticas.
- Não precisa ser importado; está sempre disponível.
- É usado para cálculos mais complexos que vão além dos operadores aritméticos básicos.

### 2.1 Métodos de Comparação e Valor Absoluto
- `Math.max(numeros...)`:
  - Retorna o maior número da lista fornecida.
  - Exemplo: `Math.max(1, 2, 3);` retorna `3`.
- `Math.min(numeros...)`:
  - Retorna o menor número da lista fornecida.
  - Exemplo: `Math.min(1, 2, 3);` retorna `1`.
- `Math.abs(numero)`:
  - Retorna o valor absoluto do número (remove o sinal).
  - Exemplo: `Math.abs(-5);` retorna `5`.
  - Exemplo: `Math.abs(5);` retorna `5`.

### Tabela - Métodos Math (Parte 1)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| Math.max() | Retorna o número maior da lista. | `Math.max(1, 2, 3); // Saída: 3` |
| Math.min() | Retorna o número menor da lista. | `Math.min(1, 2, 3); // Saída: 1` |
| Math.abs() | Retorna o valor absoluto de um número (sem o seu sinal). | `Math.abs(-5); // Saída: 5` |

- `Math.max` e `Math.min` podem receber qualquer quantidade de argumentos.
- `Math.abs` é útil para garantir que um número seja sempre positivo, independente do sinal original.

### 2.2 Métodos de Arredondamento
- `Math.round(numero)`:
  - Arredonda para o inteiro mais próximo.
  - Valores decimais de 0.5 ou mais arredondam para cima; abaixo de 0.5 arredondam para baixo.
  - Exemplo: `Math.round(3.6)` retorna `4`.
  - Exemplo: `Math.round(3.5)` retorna `4` (arredonda para cima em 0.5).
  - Exemplo: `Math.round(3.4)` retorna `3`.
- `Math.floor(numero)`:
  - Arredonda para baixo, para o inteiro mais próximo.
  - Exemplo: `Math.floor(3.6)` retorna `3`.
  - Exemplo: `Math.floor(3.1)` retorna `3`.
- `Math.ceil(numero)`:
  - Arredonda para cima, para o inteiro mais próximo.
  - Exemplo: `Math.ceil(3.1)` retorna `4`.
  - Exemplo: `Math.ceil(3.6)` retorna `4`.

### Tabela - Métodos Math (Parte 2)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| Math.round() | Arredonda um número para o inteiro mais próximo. | `Math.round(3.6); // Saída: 4` |
| Math.floor() | Arredonda um número para baixo (inteiro mais próximo). | `Math.floor(3.6); // Saída: 3` |
| Math.ceil() | Arredonda um número para cima (inteiro mais próximo). | `Math.ceil(3.1); // Saída: 4` |

> [!CAUTION] OBSERVAÇÃO: 
> - `Math.round(0.7)` retorna `1.0` (inteiro 1), não `1.0` como decimal.
> - `Math.ceil(0.7)` retorna `1`, não `0.5`. A função `Math.ceil` sempre arredonda para o inteiro superior.
> - Divisão por zero em JavaScript não gera erro, retorna `Infinity` ou `-Infinity`, dependendo do sinal. A questão 4 (pag. 3) explica que a afirmativa "a" está incorreta, pois não gera erro em todos os casos. O tratamento deve ser feito com lógica apropriada.
> - Para verificar se um valor é `NaN`, a melhor forma é usar `isNaN(x)`, pois `x == NaN` sempre retorna `false`. A afirmativa "b" está incorreta.

## 3. Objeto Date
- O objeto `Date` é usado para trabalhar com datas e horas.
- Permite criar instâncias para representar o momento atual ou uma data específica.
- É comum em aplicações reais, como registrar o horário de submissão de formulários.

### 3.1 Criando um Objeto Date
- `new Date()`:
  - Cria um novo objeto com a data e hora atuais.
  - Exemplo: `let hoje = new Date();`
  - A data gerada contém ano, mês, dia, hora, minuto, segundo e milissegundo.

### Tabela - Métodos Date (Parte 1)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| new Date() | Cria um novo objeto de data e hora. | `let hoje = new Date(); // 2024-03-06T14:30:11.363Z` |
| getFullYear() | Retorna o ano de uma data específica. | `let ano = hoje.getFullYear(); // Saída: 2024` |
| getMonth() | Retorna o mês de uma data específica. | `let mes = hoje.getMonth(); // Saída: 2 (março)` |
| getDate() | Retorna o dia do mês de uma data específica. | `let dia = hoje.getDate(); // Saída: 6` |

- `getFullYear()`: Retorna o ano com quatro dígitos.
- `getMonth()`: Retorna o mês de 0 a 11 (janeiro = 0, fevereiro = 1, março = 2).
- `getDate()`: Retorna o dia do mês (1 a 31).

### 3.2 Métodos de Data e Hora (Continuação)
- `getDay()`:
  - Retorna o dia da semana (0 a 6), onde 0 = domingo, 1 = segunda, ..., 6 = sábado.
  - Exemplo: Se 6 de março foi uma sexta-feira, `getDay()` retorna `5`.
  - Não confundir com `getDate()` (dia do mês).
- `getHours()`: Retorna a hora (0 a 23).
- `getMinutes()`: Retorna os minutos (0 a 59).

### Tabela - Métodos Date (Parte 2)
| MÉTODO | DESCRIÇÃO | EXEMPLO EM CÓDIGO |
|--------|-----------|-------------------|
| getDay() | Retorna o dia da semana de uma data específica. | `let diaSemana = hoje.getDay(); // Saída: 5 (sexta-feira)` |
| getHours() | Retorna a hora de uma data específica. | `let hora = hoje.getHours(); // Saída: 14` |
| getMinutes() | Retorna os minutos de uma data específica. | `let minutos = hoje.getMinutes(); // Saída: 30` |

> [!TIP] DICAS: 
> - A contagem dos meses começa em 0 (janeiro), então `getMonth()` retorna 2 para março.
> - Os dias da semana também começam em 0 (domingo).

> [!CAUTION] OBSERVAÇÃO: 
> - Confundir `getDate()` (dia do mês) com `getDay()` (dia da semana) é um erro comum em provas. A questão 5 (pag. 5) cobra exatamente essa distinção. Para obter o dia do mês, usa-se `getDate()`.

## 4. Tratamento de Erros (try...catch...finally)
- JavaScript oferece mecanismos para lidar com erros em tempo de execução.
- Permite que o programa continue executando mesmo quando um erro ocorre, em vez de travar completamente.
- Usa os blocos `try`, `catch` e `finally`.

### 4.1 Estrutura Básica
- `try`:
  - Bloco onde o código que pode gerar um erro é colocado.
  - Se uma exceção for lançada dentro do `try`, a execução é interrompida e o controle passa para o `catch`.
  - Se nenhum erro ocorrer, o `catch` é ignorado.
- `catch(erro)`:
  - Bloco que captura e trata o erro.
  - Recebe um parâmetro (geralmente chamado de `error` ou `err`) que contém informações sobre o erro.
  - Permite exibir mensagens de erro, fazer logs ou tentar uma recuperação.
- `finally`:
  - Bloco opcional que sempre é executado, independentemente de um erro ter ocorrido ou não.
  - Útil para limpeza de recursos (ex: fechar conexões, liberar memória).

### 4.2 Sintaxe
```javascript
try {
  // Código que pode falhar
  console.log("Tentando executar o bloco try...");
  let resultado = dividir(10, 0); // Simula um erro
  console.log("Resultado da divisão:", resultado);
} catch (error) {
  // Captura e trata o erro
  console.log("Erro capturado:", error.message);
} finally {
  // Sempre executado
  console.log("Finalmente: Execução concluída, com ou sem erro.");
}
```

- `dividir(10, 0)` lançará um erro (ex: divisão por zero ou erro na função, dependendo da implementação).
- O `catch` captura o erro e exibe a mensagem.
- O `finally` exibe a mensagem de conclusão independentemente do resultado.

> [!TIP] DICAS: 
> - A ordem sempre deve ser `try`, `catch` e, opcionalmente, `finally`.
> - O `catch` só pode ser usado após um `try`.
> - O `finally` é útil para garantir que ações como fechamento de arquivos ou conexões sejam executadas.

### 4.3 Exemplo de Função com Verificação de Tipo
- Função `soma(x, y)` que verifica se os parâmetros são números.
- Exemplo:
```javascript
function soma(x, y) {
  if (typeof x !== 'number' || typeof y !== 'number') {
    throw new Error('x e y precisam ser números.');
  }
  return x + y;
}
```

- `typeof` verifica o tipo de uma variável.
- Se `x` ou `y` não forem do tipo `number`, a função lança um erro com uma mensagem personalizada.
- A comparação `!==` verifica valor e tipo (`strict inequality`).

### 4.4 Exemplo de Uso com try...catch...finally
```javascript
try {
  let resultado = soma('1', '2');
  console.log('Resultado:', resultado);
} catch (error) {
  console.log('Erro:', error.message);
} finally {
  console.log('Sucesso!');
}
```

- `soma('1', '2')` lança um erro porque `'1'` e `'2'` são strings.
- O `catch` captura e exibe a mensagem `"x e y precisam ser números."`.
- O `finally` exibe `"Sucesso!"`.
- Saída final:
  - `"Erro: x e y precisam ser números."`
  - `"Sucesso!"`