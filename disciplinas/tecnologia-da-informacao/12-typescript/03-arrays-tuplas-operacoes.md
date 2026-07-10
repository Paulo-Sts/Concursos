# Anotações

# TYPESCRIPT IV – ARRAYS, TUPLAS E OPERAÇÕES

## 1. Arrays no TypeScript

### 1.1 Definição e Tipagem

- **Conceito:** Estrutura de dados usada para armazenar **múltiplos valores** em uma única variável.
- **Regra de Tipagem:** Uma vez definido o tipo do array, **todos os elementos** devem respeitar esse tipo.

#### 1.1.1 Sintaxes de Declaração

| SINTAXE | EXEMPLO | OBSERVAÇÃO |
| :--- | :--- | :--- |
| **Colchetes (`tipo[]`)** | `let nomes: string[] = ["Ana", "Júlio"];` | Forma mais comum e recomendada. |
| **Genérico (`Array<tipo>`)** | `let idades: Array<number> = [30, 25];` | Forma alternativa, comum em linguagens tipadas. |

> ### 1.1.2 Comportamento na Compilação (Erros)
- **Cenário:** Tentar adicionar um elemento de tipo diferente (ex: `string` em `number[]`).
- **Resultado:** O TypeScript **acusará erro em tempo de compilação**, mas **ainda assim gerará o arquivo JavaScript** (a menos que a flag `--noEmitOnError` seja usada).
- **Comando para Bloquear Saída:** `tsc --noEmitOnError arquivo.ts` (Impede a geração do `.js` se houver erros de tipo).

### 1.2 Array Somente Leitura (`readonly`)

- **Função:** Impede a **modificação** do array após sua criação (impede `push`, `pop`, atribuição por índice).
- **Sintaxe:**
    ```typescript
    let dados: readonly number[] = [10, 20, 30];
    // dados.push(40); // ERRO: Propriedade 'push' não existe no tipo 'readonly number[]'.
    ```

### 1.3 Array de Objetos

- **Definição:** Array onde cada elemento é um objeto, seguindo uma estrutura predefinida.
- **Sintaxe:**
    ```typescript
    // Define o tipo da estrutura do objeto primeiro (ex: interface ou type)
    interface Pessoa {
        nome: string;
        idade: number;
    }

    let pessoas: Pessoa[] = [
        { nome: "João", idade: 20 },
        { nome: "Maria", idade: 22 }
    ];
    ```

## 2. Tuplas

### 2.1 Definição e Propósito

- **Definição:** Tipo especial de array com **número fixo de elementos** onde **cada posição tem um tipo específico e imutável**.
- **Diferença para Array:** No array (`string[]`), todos os elementos são do mesmo tipo. Na tupla, a posição `[0]` pode ser `string`, a `[1]` `number`, etc.

### 2.2 Sintaxe e Aplicações

- **Declaração:**
    ```typescript
    // Exemplo: Representar um registro de dados heterogêneo fixo
    let aluno: [string, number, boolean] = ["Ana", 12345, true];
    // Ordem fixa: Nome (string), Matrícula (number), Ativo (boolean)
    ```
- **Tupla com Número Variável de Elementos (*Rest Parameter*):**
    ```typescript
    // Primeiro elemento é string, os demais são números (quantos quiser)
    let notas: [string, ...number[]];
    notas = ["Ana", 8.5, 9.0, 7.5]; // Válido
    ```

> ### 2.2.1 Quando Utilizar Tuplas
- **Dados Imutáveis e Heterogêneos:** Representar pares ordenados onde a posição define o significado.
- **Exemplos Práticos:**
    - Coordenadas (x, y): `[number, number]`.
    - Retorno múltiplo de função: `[string, number]` (Ex: "Erro", 404).
    - Dados CSV: Cada linha pode ser interpretada como uma tupla de campos fixos.

## 3. Operações com Arrays (Métodos Nativos)

### 3.1 Métodos de Modificação (Alteram o Array Original)

| MÉTODO | FUNÇÃO | EXEMPLO (Entrada -> Saída) |
| :--- | :--- | :--- |
| **`push()`** | **Adiciona** um ou mais elementos ao **final** do array. Retorna o novo comprimento. | `[1,2].push(3)` -> `[1,2,3]` |
| **`pop()`** | **Remove** o **último** elemento do array. Retorna o elemento removido. | `[1,2,3].pop()` -> `[1,2]` (Retorna `3`) |
| **`unshift()`** | **Adiciona** um ou mais elementos ao **início** do array. Retorna o novo comprimento. | `[2,3].unshift(1)` -> `[1,2,3]` |
| **`splice()`** | **Remove, substitui ou adiciona** elementos em qualquer posição. | `[1,4,7,8,6].splice(2, 2, 99)` -> Remove 2 itens a partir do índice 2, insere `99`. Resultado: `[1,4,99,6]` |

### 3.2 Métodos de Acesso e Consulta (Não Alteram o Array Original)

| MÉTODO | FUNÇÃO | EXEMPLO (Entrada -> Saída) |
| :--- | :--- | :--- |
| **`includes()`** | Verifica se um determinado **valor existe** no array. Retorna `boolean`. | `[1,2,3].includes(2)` -> `true` |
| **`slice()`** | Retorna uma **cópia superficial** de uma parte do array (fatia). **Não modifica o original**. | `[1,4,7,8,6].slice(1, 4)` -> `[4,7,8]` (Índice 1 até antes do 4). |
| **`concat()`** | **Junta dois ou mais arrays**, retornando um **novo array**. | `[1,2].concat([3,4])` -> `[1,2,3,4]` |

### 3.3 Método de Redução (`reduce`)

- **Função:** Executa uma função **redutora** (fornecida pelo usuário) em cada elemento do array, resultando em um **único valor de retorno**.
- **Mecanismo:** Acumula um valor a cada iteração.
    ```typescript
    let numeros: number[] = [1, 2, 3, 4];
    // Somar todos os elementos
    let soma = numeros.reduce((acumulador, valorAtual) => acumulador + valorAtual, 0);
    console.log(soma); // Saída: 10
    ```
- **Parâmetros:**
    1.  **Função Redutora:** Recebe `acumulador` e `valorAtual`.
    2.  **Valor Inicial (Opcional):** Se não fornecido, o primeiro elemento do array é usado como acumulador inicial e a iteração começa do segundo.