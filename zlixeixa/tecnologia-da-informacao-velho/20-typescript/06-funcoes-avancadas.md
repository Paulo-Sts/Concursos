# Anotações

# TYPESCRIPT VII – FUNÇÕES AVANÇADAS E QUESTÕES

## 1. Arrow Functions

### 1.1 Definição e Sintaxe

- **Conceito:** Forma **sintética** (menos verbosa) de declarar funções.
- **Objetivo:** Reduzir a verbosidade do código, dispensando a palavra-chave `function`.
- **Sintaxe Básica:**
    ```typescript
    const dobrar = (valor: number): number => {
        return valor * 2;
    };
    // Forma ainda mais concisa (return implícito)
    const dobrar2 = (valor: number): number => valor * 2;
    ```

### 1.2 Arrow Function como Parâmetro (Callbacks Tipados)

- **Contexto:** Passar uma função como argumento para outra função (ex: *callbacks*, `map`, `reduce`).
- **Exemplo de Definição:**
    ```typescript
    // A função 'executar' recebe uma função 'acao' (que recebe number e retorna void)
    // e um 'valor' number.
    function executar(acao: (x: number) => void, valor: number): void {
        acao(valor);
    }

    // Chamada: Passamos uma arrow function que atende à assinatura esperada
    executar((x) => { console.log("O valor é:", x); }, 10);
    executar((x) => { console.log(x * 2); }, 10); // Saída: 20
    ```

## 2. Funções com Objetos como Parâmetro

### 2.1 Tipagem de Objetos em Parâmetros

- **Funcionalidade:** O TypeScript verifica se o objeto passado possui **todas as propriedades esperadas** (e com os tipos corretos).
- **Sintaxe:**
    ```typescript
    interface Produto {
        nome: string;
        valor: number;
    }

    function exibirProduto(produto: Produto): void {
        console.log(`Produto: ${produto.nome}, Valor: R$ ${produto.valor}`);
    }

    exibirProduto({ nome: "Livro", valor: 10 }); // Válido
    // exibirProduto({ nome: "Caneta" }); // ERRO: Falta a propriedade 'valor'
    ```

## 3. Funções com Union Types (Parâmetros e Retorno)

### 3.1 Parâmetros com Union Type

- **Definição:** Permite que um parâmetro aceite múltiplos tipos de dados.
- **Exemplo:**
    ```typescript
    function converter(valor: number | string): string {
        return `Valor convertido: ${valor}`;
    }
    console.log(converter(10));    // "Valor convertido: 10"
    console.log(converter("10"));  // "Valor convertido: 10"
    // console.log(converter(true)); // ERRO: boolean não é string | number
    ```

### 3.2 Retorno com Union Type (Ex: `string | null`)

- **Exemplo Prático (Busca Condicional):**
    ```typescript
    function buscar(id: number): string | null {
        if (id === 1) {
            return "Usuário encontrado";
        }
        return null; // Retorna null se não encontrado
    }

    console.log(buscar(1));  // "Usuário encontrado"
    console.log(buscar(30)); // null
    ```

## 4. Análise de Questões de Concurso

### 4.1 Compilação TypeScript -> JavaScript (INSTITUTO ACESSO/2024)

- **Código TypeScript:**
    ```typescript
    function saudacao(nome: string) {
        return `Olá, ${nome}!`;
    }
    console.log(saudacao("Mundo TypeScript"));
    ```
- **Processo de Compilação:** O compilador `tsc` **remove as tipagens** (`: string`) e converte a *template string* (crases) para concatenação comum (se o target for ES5 ou inferior).
- **Resultado em JavaScript:**
    ```javascript
    function saudacao(nome) {
        return "Olá, " + nome + "!";
    }
    console.log(saudacao("Mundo TypeScript"));
    ```
- **Gabarito:** Alternativa **C**.

### 4.2 Declaração de Union Type (FCC/2022 - TRT 4ª Região)

- **Enunciado:** Identificar uma declaração de variável de **tipo união** válida.
- **Análise das Sintaxes:**
    - **a)** `let v: (number|string) = 924;` -> **Válido**. Sintaxe correta do *Union Type*.
    - **b)** `let v:[number, string] => ...` -> Errado. Isso é sintaxe de **tupla**.
    - **c)** `let v: string <=> null` -> Errado. Operador `<=>` não existe.
    - **d)** `var v:[x=1, y="Tribunal"]` -> Errado. Sintaxe inválida.
    - **e)** `var v:(x:number, y:string) => 145` -> Errado. Isso define um **tipo de função**.
- **Gabarito:** Alternativa **A**.

### 4.3 Tipos Primitivos em Funções (FEPESE/2023)

- **Enunciado:** Assinalar a declaração **correta** de função em TypeScript.
- **Regra de Ouro:** TypeScript **NÃO** possui os tipos `int` ou `float`. O tipo numérico universal é **`number`**.
- **Análise:**
    - `d) function SomaValores(valor1: Number, valor2: Number): Number.` -> **Válido**. (Obs: `Number` (maiúsculo) se refere à interface do objeto wrapper, mas é aceito; o ideal é `number` minúsculo). As demais são inválidas por usarem `Int` ou `Float`.
- **Gabarito:** Alternativa **D**.

### 4.4 Função sem Retorno (`void`) (FCC/2022 - TRT 23ª Região)

- **Enunciado:** Definir que a função `exibir` não recebe parâmetros e não retorna valor.
- **Sintaxe Correta:**
    ```typescript
    function exibir(): void {
        console.log('TRIBUNAL REGIONAL DO TRABALHO DA 23ª REGIÃO');
    }
    ```
- **Gabarito:** Alternativa **E**.

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (INST. ACESSO/2024) | **C** | JS gerado remove tipos (`: string`) e converte *template string*. |
| **02** (FCC/2022 - TRT 4) | **A** | `let v: (number\|string) = 924;` é a sintaxe correta do *Union Type*. |
| **03** (FEPESE/2023) | **D** | TypeScript usa `number`; não existem `int` ou `float`. |
| **04** (FCC/2022 - TRT 23) | **E** | `function exibir(): void { ... }` define função sem retorno. |