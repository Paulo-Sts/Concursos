# Anotações

# TYPESCRIPT III – TIPOS DE DADOS E CRIAÇÃO DE OBJETOS

## 1. Tipos de Dados Primitivos

### 1.1 Tipos Básicos

- **`boolean`:** Representa valores lógicos `true` ou `false`.
- **`number`:** Representa tanto números **inteiros** (ex: `30`) quanto números de **ponto flutuante** (ex: `1.92`). Não há distinção entre `int` e `float` como em outras linguagens.
- **`string`:** Representa dados textuais. Devem ser declarados entre aspas simples (`'`), duplas (`"`) ou crases (`` ` ``) para *template strings*.

> ### 1.1.1 Sintaxe de Declaração
- **Forma Explícita:**
    ```typescript
    let nome: string = "Júlio Leitão";
    let idade: number = 30;
    let altura: number = 1.92;
    let professor: boolean = true;
    ```

## 2. Criação e Tipagem de Objetos

### 2.1 Formas de Definir a Estrutura de um Objeto

| MÉTODO | DESCRIÇÃO | EXEMPLO |
| :--- | :--- | :--- |
| **Forma Simples (Literal)** | Define o objeto diretamente, tipando suas propriedades na declaração. | `let professor: { nome: string, idade: number } = { nome: "Júlio", idade: 30 };` |
| **Interface (`interface`)** | Define um "contrato" de estrutura que pode ser reutilizado e estendido. | `interface Animal { especie: string; nome: string; }` |
| **Tipo (`type`)** | Define um *type alias* (apelido de tipo) para uma estrutura de objeto. | `type Carro = { marca: string; ano: number; };` |

### 2.2 Propriedades Opcionais

- **Sintaxe:** Utiliza-se o operador `?` após o nome da propriedade.
- **Função:** Indica que a propriedade **pode ou não** estar presente no objeto, sem gerar erro de compilação.
    ```typescript
    interface Usuario {
        nome: string;
        email: string;
        telefone?: string; // Propriedade OPCIONAL
    }
    ```

### 2.3 Herança e Composição (Type vs Interface)

- **Interface (`extends`):** Utiliza a palavra-chave `extends` para herdar propriedades de uma ou mais interfaces base.
    ```typescript
    interface Animal { especie: string; nome: string; }
    interface Cachorro extends Animal { latir(): void; }
    ```
- **Type (`&` - Interseção):** Utiliza o operador de interseção `&` para combinar múltiplos tipos em um único.
    ```typescript
    type Animal = { especie: string; nome: string; };
    type Cachorro = Animal & { latir(): void; };
    ```

> ### 2.3.1 Diferença Crucial: Reabertura (Declaration Merging)
- **Interface:** Permite **"Reabertura"** (*Declaration Merging*). É possível declarar a mesma `interface` várias vezes, e o TypeScript **acumulará** as propriedades definidas em cada bloco.
    ```typescript
    interface Livro { titulo: string; }
    interface Livro { autor: string; } // Acumula! Resultado: titulo E autor.
    ```
- **Type:** **NÃO permite** reabertura. Declarar um `type` com o mesmo nome resultará em **erro de duplicidade**.

## 3. Trabalhando com Arrays

### 3.1 Sintaxe de Tipagem de Array

- **Forma 1 (Recomendada):** `tipo[]`
- **Forma 2 (Genérica):** `Array<tipo>`

| TIPO DE ARRAY | EXEMPLO DE DECLARAÇÃO |
| :--- | :--- |
| **Array de Números** | `let idades: number[] = [30, 25, 18];` |
| **Array de Strings** | `let nomes: string[] = ["Ana", "Júlio"];` |
| **Array de Objetos** | `let alunos: { nome: string; nota: number }[] = [];` |

### 3.2 Array Somente Leitura (`readonly`)

- **Palavra-chave:** `readonly`
- **Função:** Impede que o array seja **modificado** após sua criação (impede operações como `push()`, `pop()`, ou atribuição por índice).
    ```typescript
    let numeros: readonly number[] = [1, 2, 3];
    // numeros.push(4); // ERRO: Propriedade 'push' não existe no tipo 'readonly number[]'.
    ```

## 4. Exemplo Prático Consolidado (Interface com Método)

- **Cenário:** Modelagem de um Cachorro que late.
    ```typescript
    // 1. Definição da Interface Base
    interface Animal {
        especie: string;
        nome: string;
    }

    // 2. Herança (extends)
    interface Cachorro extends Animal {
        latir(): void; // Método que não retorna valor
    }

    // 3. Implementação
    const thor: Cachorro = {
        especie: "Canis lupus familiaris",
        nome: "Thor",
        latir: function() {
            // Uso de Template String (crases)
            console.log(`${this.nome} está latindo!`); 
        }
    };

    thor.latir(); // Saída: "Thor está latindo!"
    ```

## 5. Resumo Comparativo: Interface vs. Type

| CARACTERÍSTICA | `interface` | `type` |
| :--- | :--- | :--- |
| **Herança/Composição** | `extends` | `&` (Interseção) |
| **Reabertura (*Declaration Merging*)** | **Permitido** (Acumula propriedades). | **Não Permitido** (Erro de duplicidade). |
| **Uso Ideal** | Definição de contratos de objetos/classes. | Definição de uniões complexas, tipos primitivos apelidados, tuplas. |