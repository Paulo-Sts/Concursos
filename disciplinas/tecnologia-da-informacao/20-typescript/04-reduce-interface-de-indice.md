# Anotações

# TYPESCRIPT V – REDUCE, INTERFACES DE ÍNDICE E QUESTÕES

## 1. Aprofundamento em Operações de Array: `reduce`

### 1.1 Mecanismo Detalhado

- **Definição:** Método que executa uma função **redutora** (fornecida pelo usuário) em cada elemento do array, resultando em um **único valor de retorno**.
- **Parâmetros da Função Redutora:**
    1.  **Acumulador (*Accumulator*):** Armazena o **resultado do cálculo da iteração anterior**.
    2.  **Valor Atual (*Current Value*):** O elemento do array que está sendo processado na iteração atual.
- **Funcionamento:** A função redutora realiza um cálculo utilizando o **Acumulador** e o **Valor Atual**, atualiza o Acumulador com o resultado, e prossegue para o próximo elemento.

### 1.2 Valor Inicial (Segundo Parâmetro do `reduce`)

- **Cenário 1 (Com Valor Inicial):**
    - O Acumulador **inicia com o valor fornecido**.
    - A iteração começa a partir do **primeiro elemento** (índice 0).
    - **Exemplo:** `[1,2,3].reduce((acc, cur) => acc + cur, 0);` -> Cálculo: `0 + 1 = 1`, `1 + 2 = 3`, `3 + 3 = 6`.
- **Cenário 2 (Sem Valor Inicial):**
    - O Acumulador assume o valor do **primeiro elemento do array** (índice 0).
    - A iteração começa a partir do **segundo elemento** (índice 1).
    - **Exemplo:** `[1,2,3].reduce((acc, cur) => acc + cur);` -> Cálculo: `1 + 2 = 3`, `3 + 3 = 6`.
- **Observação de Segurança:** É **altamente recomendado sempre fornecer um valor inicial** para evitar erros caso o array esteja vazio (se o array for vazio e não houver valor inicial, `reduce` lançará um erro).

> ### 1.2.1 Análise de Questão (CESGRANRIO/2021 - Banco do Brasil)
- **Código Base:** `const y = (...args: number[]) => args.reduce(x, 0);`
- **Objetivo:** Encontrar a definição correta de `x` (a função redutora).
- **Requisito:** A função `x` deve aceitar **dois parâmetros** (acumulador e valor atual) e retornar um valor que será usado como próximo acumulador.
- **Alternativa Correta:** `const x = (a: number, b: number) => a + b;`
- **Análise das Erradas:**
    - `const x = 1;` (Não é uma função).
    - `const x = (a: number) => [a*2];` (Só tem 1 parâmetro; retorna array, não `number` para acumular).

## 2. Interfaces com Assinatura de Índice (Index Signatures)

### 2.1 Definição

- **Conceito:** Permite definir o **tipo da chave (índice)** e o **tipo do valor** para objetos que serão usados como "dicionários" ou arrays.
- **Sintaxe:** `[indice: tipoDaChave]: tipoDoValor`
- **Aplicação em Arrays:**
    ```typescript
    interface CriaArrayString {
        [indice: number]: string;
    }
    ```
- **Funcionamento:** Especifica que qualquer propriedade acessada com uma chave do tipo `number` deve retornar um valor do tipo `string`. Isso modela perfeitamente um array tradicional de strings.

### 2.2 Questão FCC/2018 (MPE-PE)

- **Código:**
    ```typescript
    interface CriaArrayString { [indice: number]: string; }
    var nomes: CriaArrayString;
    nomes = ["Ana", "Pedro", "Mariana"];
    document.body.innerHTML = nomes[1];
    ```
- **Pergunta:** Qual o resultado?
- **Análise:** O código **compila e executa sem erros**. A variável `nomes` se comporta como um array comum. O índice `1` corresponde ao segundo elemento.
- **Resultado Exibido:** **Pedro** (Alternativa **B**).

## 3. Revisão de Tipos Primitivos em TypeScript (FGV/2024 - TJ-MS)

### 3.1 Erro de Tipo Específico

- **Código Analisado:**
    ```typescript
    interface Tribunal { sigla: string; id: integer; } // ERRO AQUI
    const tJms: Tribunal = { id: 4, sigla: "TJMS" };
    ```
- **Identificação do Erro:** **`integer` não é um tipo válido em TypeScript**.
- **Tipos Primitivos Válidos em TypeScript:**
    - `number` (Representa inteiros e decimais).
    - `string`.
    - `boolean`.
- **Correção Necessária:** A interface deveria usar `id: number;`.
- **Gabarito:** "b) a indefinição do nome ‘integer’".

## 4. Interação com o DOM (TypeScript + HTML)

### 4.1 Seletores (QUADRIX/2024)

- **Contexto:** Código TypeScript gerando um `.js` para manipular um formulário HTML.
- **Elemento HTML:** `<input type='text' name='texto' id='idTexto' class='classe-input' />`
- **Objetivo:** Selecionar o campo de texto para exibir seu valor no console.
- **Regras de Seletores (JavaScript/DOM):**
    - **`#` (Hashtag):** Seleciona por **ID**.
    - **`.` (Ponto):** Seleciona por **Classe**.
    - **Nome da Tag:** Seleciona por Tag (ex: `'input'`).
- **Código TypeScript:**
    ```typescript
    const texto = document.querySelector('#idTexto') as HTMLInputElement;
    console.log('Texto inicial: ', texto.value);
    ```
- **Gabarito:** `#idTexto` (Alternativa **B**).

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FEPESE/2023) | **E** | Tipos válidos em TS: `Number`, `String`, `Boolean`. |
| **02** (FGV/2024) | **B** | TypeScript não possui o tipo `integer`; usa-se `number`. |
| **03** (QUADRIX/2024) | **B** | Seletor `#idTexto` para acessar elemento por ID. |
| **04** (FCC/2022) | **B** | Tupla definida como `[number, boolean, string]`. |
| **05** (FCC/2018) | **B** | Exibe "Pedro" (índice 1 do array). |
| **06** (CESGRANRIO/2021) | **E** | Função redutora `(a:number, b:number) => a+b`. |

## 6. Próximo Tópico (Union Types)

- **Conceito:** Permite que uma variável aceite **mais de um tipo** de dado.
- **Operador:** **Pipe (`|`)**.
- **Sintaxe:** `let variavel: string | number;`
- **Funcionalidade:** `variavel` poderá receber tanto uma `string` quanto um `number` sem acusar erro de tipo.