# Anotações

# TYPESCRIPT IX – GENÉRICOS (GENERICS)

## 1. Introdução aos Genéricos

### 1.1 Definição e Propósito

- **Conceito:** Mecanismo para escrever **funções, classes, interfaces e tipos** que funcionam com **múltiplos tipos de dados**, sem perder a **segurança de tipos** (*type safety*).
- **Objetivo:** Criar código **reutilizável** e **flexível**, mantendo a verificação de tipo em tempo de compilação.
- **Comparação com Outros Recursos:**
    - **`any`**: Oferece flexibilidade total, mas **remove a segurança de tipos**. O TypeScript "desiste" de verificar.
    - **`Union Type` (`|`)**: Permite um conjunto **fechado e conhecido** de tipos (`string | number`). Não escala bem para uma quantidade infinita de possibilidades.
    - **Genéricos (`<T>`)**: Permite **qualquer tipo**, mas **preserva a informação do tipo original** ao longo do fluxo do código.

> ### 1.1.1 Funcionamento Básico
- **Sintaxe:** Utiliza-se um **parâmetro de tipo** (ex: `<T>`) que atua como uma "variável de tipo".
- **Comportamento:** O tipo `T` é **definido no momento do uso** da função ou classe, e o TypeScript rastreia esse tipo para garantir a consistência.

## 2. Funções Genéricas

### 2.1 Exemplo Fundamental: Função `retornaValor`

- **Cenário:** Uma função que recebe um argumento e retorna o mesmo valor. Sem genéricos, seria necessário usar `any` (perdendo o tipo) ou criar múltiplas *overloads* (uma para cada tipo).
- **Implementação com Genérico:**
    ```typescript
    function retornaValor<T>(valor: T): T {
        return valor;
    }

    // Uso:
    let saidaString = retornaValor<string>("Olá"); // Tipo inferido: string
    let saidaNumber = retornaValor<number>(100);   // Tipo inferido: number
    let saidaArray = retornaValor([1, 2, 3]);      // Tipo inferido: number[]
    ```
- **Vantagem:** O tipo de retorno `T` corresponde exatamente ao tipo do argumento passado. O TypeScript sabe que `saidaString` é uma `string` e oferece os métodos correspondentes.

### 2.2 Restringindo Genéricos com `extends` (Constraints)

- **Problema:** Às vezes, o genérico `T` precisa ter **certas propriedades garantidas**. Não se pode acessar `valor.length` se `T` puder ser um `number`.
- **Solução:** Utilizar `extends` para definir uma **restrição (constraint)**.
    ```typescript
    interface TemComprimento {
        length: number;
    }

    // T deve ser um tipo que possua a propriedade 'length'
    function logarComprimento<T extends TemComprimento>(arg: T): T {
        console.log(arg.length); // Agora é seguro acessar 'length'
        return arg;
    }

    logarComprimento("Teste"); // Válido (string tem length)
    logarComprimento([1, 2]);  // Válido (array tem length)
    // logarComprimento(10);   // ERRO: number não tem 'length'
    ```

## 3. Análise de Questões de Concurso

### 3.1 Questão FCC/2023 (TRT 18ª Região) - Enum

- **Código Analisado:**
    ```typescript
    I cliente {
        nome = 'Paulo Silva',
        cidade = 'Goiânia',
        uf = 'GO',
    };
    console.log(cliente.nome);
    ```
- **Pergunta:** Qual a instrução usada na lacuna `I`?
- **Análise da Estrutura:** O código define um conjunto de constantes nomeadas (`nome`, `cidade`, `uf`) com valores associados, agrupadas sob o identificador `cliente`. Isso é a definição clássica de um **Enum** (Enumeration).
- **Gabarito:** Alternativa **D (`enum`)**.

### 3.2 Questão CESGRANRIO/2021 (Banco do Brasil) - Genéricos com Restrição

- **Código Analisado:**
    ```typescript
    const a = <T extends (b: string)> (obj: T) => { /* <código removido> */ };
    ```
- **Interpretação da Sintaxe:**
    1.  `const a = ...`: Declara uma constante `a`.
    2.  `<T extends (b: string)>`: Define um **tipo genérico `T`**.
    3.  `extends (b: string)`: Impõe uma **restrição**. `T` deve ser um tipo que seja compatível com um objeto que tenha uma propriedade `b` do tipo `string`.
    4.  `(obj: T) => { ... }`: É uma **arrow function** que recebe um parâmetro `obj` do tipo `T`.
- **Conclusão Lógica:** O objeto que for passado como argumento para a função `a()` **deve ter, obrigatoriamente, um campo `b` do tipo `string`**.
- **Gabarito:** Alternativa **D**.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FCC/2023) | **D** | A sintaxe corresponde à definição de um `enum`. |
| **02** (CESGRANRIO/2021) | **D** | A restrição `T extends (b: string)` exige a presença do campo `b: string` no objeto passado. |