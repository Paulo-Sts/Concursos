# Anotações

# TYPESCRIPT VIII – ENUM, CLASSES E ORIENTAÇÃO A OBJETOS

## 1. Enum (Enumeration)

### 1.1 Definição e Propósito

- **Conceito:** Recurso que permite definir um conjunto de **constantes nomeadas** associadas a valores (numéricos ou *string*).
- **Objetivo:** Melhorar a **clareza**, **legibilidade** e **segurança** do código, substituindo "números mágicos" por nomes semânticos.
- **Funcionamento Padrão:** Por padrão, o primeiro elemento recebe o valor `0`, o segundo `1`, e assim sucessivamente.

> ### 1.1.1 Exemplo Prático (Status de Pedido)
- **Problema:** Usar `if (status == 2)` exige consultar documentação para saber o que significa "2".
- **Solução com Enum:**
    ```typescript
    enum StatusPedido {
        Processando, // 0
        Enviado,     // 1
        Entregue     // 2
    }

    let situacao: StatusPedido = StatusPedido.Enviado;
    if (situacao == StatusPedido.Enviado) {
        console.log("Pedido já foi despachado.");
    }
    ```

### 1.2 Enum com Valores Personalizados (String)

- **Funcionalidade:** É possível atribuir valores **textuais** diretamente aos membros do *enum*, tornando a saída do código autoexplicativa.
    ```typescript
    enum Perfil {
        Admin = "Administrador",
        Usuario = "Usuário Comum",
        Consulta = "Apenas Leitura"
    }

    let perfilUsuario: Perfil = Perfil.Admin;
    console.log(`Perfil: ${perfilUsuario}`); // Saída: "Perfil: Administrador"
    ```

## 2. Classes e Modificadores de Acesso (Orientação a Objetos)

### 2.1 Definição de Classe

- **Estrutura:** Agrupa **atributos** (dados) e **métodos** (funções) que operam sobre esses dados.
- **Sintaxe com Tipagem:**
    ```typescript
    class Pessoa {
        nome: string;
        altura: number;

        constructor(nome: string, altura: number) {
            this.nome = nome;
            this.altura = altura;
        }

        apresentar(): void {
            console.log(`Olá, sou ${this.nome} e tenho ${this.altura}m.`);
        }
    }
    ```

### 2.2 Modificadores de Acesso

| MODIFICADOR | ACESSIBILIDADE |
| :--- | :--- |
| **`public`** (Padrão) | Acessível de **qualquer lugar** (dentro e fora da classe). |
| **`private`** | Acessível **apenas dentro da própria classe** onde foi declarado. |
| **`protected`** | Acessível na **própria classe** e em **subclasses** (herança). |

### 2.3 Herança (`extends`) e Métodos Abstratos (`abstract`)

- **Herança:** Permite que uma classe (**filha**) derive atributos e métodos de outra classe (**pai**).
    ```typescript
    class Animal {
        constructor(protected nome: string) {} // 'protected' permite acesso na subclasse
        mover(distancia: number): void {
            console.log(`${this.nome} moveu ${distancia}m.`);
        }
    }

    class Cachorro extends Animal {
        latir(): void {
            console.log("Uau Uau!");
        }
    }
    ```
- **Classe Abstrata (`abstract`):** Não pode ser instanciada diretamente. Serve como modelo para subclasses. Pode conter **métodos abstratos** (sem implementação) que **devem** ser implementados pelas classes filhas.
    ```typescript
    abstract class Pessoa {
        constructor(public nome: string, public idade: number) {}
        abstract profissao(): void; // Método abstrato
    }

    class Professor extends Pessoa {
        constructor(nome: string, idade: number, public disciplina: string) {
            super(nome, idade); // Chama o construtor da classe pai
        }
        // Implementação OBRIGATÓRIA do método abstrato
        profissao(): void {
            console.log(`${this.nome} é professor de ${this.disciplina}.`);
        }
    }
    ```

## 3. Implementação de Interfaces em Classes (`implements`)

- **Definição:** Uma **interface** define um **contrato** de métodos e propriedades que uma classe deve implementar.
- **Palavra-chave:** `implements`.
- **Exemplo:**
    ```typescript
    interface Autenticador {
        login(usuario: string, senha: string): boolean;
    }

    class Sistema implements Autenticador {
        // A classe é OBRIGADA a implementar o método 'login'
        login(usuario: string, senha: string): boolean {
            return usuario === 'admin' && senha === 'admin';
        }
    }

    const sys = new Sistema();
    console.log(sys.login('admin', 'admin')); // true
    ```

## 4. Introdução a Genéricos (Generics)

### 4.1 Conceito Inicial

- **Problema do `Union Type`:** Permite definir um conjunto **fechado** de tipos (`string | number`).
- **Problema do `any`:** Permite **qualquer tipo**, mas **desabilita a verificação de tipo** (perde-se a segurança do TypeScript).
- **Solução Genéricos:** Permite que um componente (função, classe, interface) trabalhe com **diversos tipos** sem perder a **verificação de tipo**. O tipo é "definido" no momento do uso.

> ### 4.1.1 Próxima Aula
- **Tópico:** Aprofundamento e implementação prática de **Genéricos (*Generics*)**.