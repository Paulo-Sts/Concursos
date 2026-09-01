# Anotações

# TYPESCRIPT VI – UNION TYPES E FUNÇÕES

## 1. Operador Union Type (`|`)

### 1.1 Definição e Propósito

- **Conceito:** Permite que uma variável, parâmetro ou retorno de função aceite **mais de um tipo de dado**.
- **Operador:** **Pipe (`|`)**.
- **Funcionalidade:** Adiciona **flexibilidade** ao código sem perder a **segurança da tipagem estática**.
- **Diferença de Tuplas:** Enquanto a tupla exige uma **ordem e quantidade fixa** de tipos (`[string, number]`), o *Union Type* permite que o valor seja **ou um tipo, ou outro**, independentemente de ordem ou posição.

> ### 1.1.1 Exemplo Básico
- **Sintaxe:** `let variavel: string | number;`
- **Comportamento:**
    - `variavel = "Texto";` -> **Válido**.
    - `variavel = 100;` -> **Válido**.
    - `variavel = true;` -> **Erro de Compilação**. O tipo `boolean` não é atribuível a `string | number`.

### 1.2 Union em Arrays

- **Definição:** Permite que um array armazene elementos de **tipos distintos e alternados**.
- **Sintaxe:** `let dados: (string | number)[] = ["Ana", 30, "Pedro", 25];`
- **Comportamento:** Métodos como `push` aceitarão apenas os tipos definidos na união.
    - `dados.push("Júlio");` -> **Válido**.
    - `dados.push(40);` -> **Válido**.
    - `dados.push(true);` -> **Erro**. `boolean` não está na união.

### 1.3 Union com Objetos (Tipos Personalizados)

- **Aplicação:** Permite que um objeto seja de **um tipo OU de outro** tipo definido previamente.
- **Exemplo Prático:**
    ```typescript
    type Usuario = { nome: string; idade: number };
    type Produto = { nome: string; estoque: boolean };

    // Union Type com objetos
    let entidade: Usuario | Produto;

    entidade = { nome: "João", idade: 22 };     // Válido (Usuario)
    entidade = { nome: "Tênis", estoque: true }; // Válido (Produto)
    entidade = "Olá, mundo";                     // Erro (String não é Usuario nem Produto)
    ```

## 2. Criação de Funções com TypeScript

### 2.1 Função sem Retorno (`void`)

- **Definição:** Função que executa uma ação mas **não retorna nenhum valor**.
- **Tipo de Retorno:** `void`.
- **Sintaxe:**
    ```typescript
    function saudacao(nome: string): void {
        console.log(`Olá, ${nome}`);
    }
    ```
- **Observação:** Embora o JavaScript aceite omitir o tipo de retorno, o TypeScript recomenda (e se beneficia de) a definição explícita de `void` para garantir a intenção do código.

### 2.2 Parâmetros Opcionais (`?`)

- **Sintaxe:** Adiciona-se o operador `?` após o nome do parâmetro.
- **Função:** Indica que o argumento **pode ser omitido** na chamada da função.
- **Exemplo:**
    ```typescript
    function apresentar(nome: string, idade?: number): void {
        console.log(`Nome: ${nome}`);
        if (idade) {
            console.log(`Idade: ${idade}`);
        }
    }
    apresentar("Ana");      // Válido (idade omitida)
    apresentar("Ana", 30);  // Válido
    ```
- **Regra de Posição:** Parâmetros opcionais **devem vir após** os parâmetros obrigatórios.

### 2.3 Parâmetros com Valor Padrão (*Default*)

- **Sintaxe:** Atribui-se um valor diretamente na declaração do parâmetro (`parametro: tipo = valor`).
- **Função:** Se o argumento **não for fornecido**, o parâmetro assume o **valor padrão** definido.
- **Exemplo:**
    ```typescript
    // Se 'nome' não for passado, usa "Bom dia"
    function saudacaoDefault(nome: string = "Bom dia"): string {
        return `Olá, ${nome}`;
    }
    console.log(saudacaoDefault());       // "Olá, Bom dia"
    console.log(saudacaoDefault("João")); // "Olá, João"
    ```
- **Observação:** Parâmetros com valor *default* são automaticamente considerados **opcionais** na chamada da função.

### 2.4 Parâmetros Nomeados (Objeto como Parâmetro)

- **Conceito:** Em vez de passar uma lista longa de argumentos posicionais, passa-se um **único objeto** cujas propriedades são os parâmetros.
- **Vantagem:** A ordem dos argumentos **não importa**, aumentando a legibilidade e evitando erros de inversão de valores.
- **Sintaxe:**
    ```typescript
    function divide({ dividendo, divisor }: { dividendo: number; divisor: number }): number {
        return dividendo / divisor;
    }

    // Chamadas equivalentes (ordem não importa)
    console.log(divide({ dividendo: 10, divisor: 2 })); // 5
    console.log(divide({ divisor: 2, dividendo: 10 })); // 5
    ```

## 3. Comparativo de Flexibilidade de Parâmetros

| CARACTERÍSTICA | PARÂMETRO OBRIGATÓRIO | PARÂMETRO OPCIONAL (`?`) | VALOR PADRÃO (*Default*) |
| :--- | :--- | :--- | :--- |
| **Sintaxe** | `nome: string` | `nome?: string` | `nome: string = "Padrão"` |
| **Obrigatoriedade** | **Sim**. Deve ser passado. | **Não**. Pode ser omitido. | **Não**. Se omitido, usa o valor *default*. |
| **Valor se Omitido** | `undefined` (e possível erro de lógica). | `undefined`. | O valor definido na declaração. |
| **Ordem na Declaração** | Primeiros. | Após os obrigatórios. | Normalmente após obrigatórios. |