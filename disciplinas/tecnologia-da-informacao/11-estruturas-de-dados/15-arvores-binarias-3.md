# Anotações – Estrutura de Dados – Árvores Binárias: Ordens de Percurso (Implementação e Códigos)

## 1. Revisão – Posição da Raiz e Comportamento Geral

| PERCURSO | NORMAL | INVERSO |
| --- | --- | --- |
| **Pré-ordem** | raiz → esq → dir | raiz → dir → esq |
| **Em-ordem** | esq → raiz → dir | dir → raiz → esq |
| **Pós-ordem** | esq → dir → raiz | dir → esq → raiz |

> ### 1.1 Observações importantes
> - **Pré-ordem (normal):** a última informação impressa será, provavelmente, o nó **mais à direita possível**.
> - **Pré-ordem inversa:** a última informação impressa será, provavelmente, o nó **mais à esquerda possível**.
> - **Em-ordem (normal):** a primeira informação impressa será o nó **mais à esquerda possível**; a última, o nó **mais à direita possível**.
> - **Em-ordem inversa:** a primeira informação impressa será o nó **mais à direita possível**; a última, o nó **mais à esquerda possível**.
> - **Pós-ordem (normal):** a primeira informação impressa será o nó **mais à esquerda possível**; a raiz é sempre a **última**.
> - **Pós-ordem inversa:** a primeira informação impressa será o nó **mais à direita possível**; a raiz continua sendo a **última**.

## 2. Implementações em Java (Códigos Recursivos)

### 2.1 Estrutura do nó (`NoArvore`)

```java
public class NoArvore {
    int dado;
    NoArvore esquerda;
    NoArvore direita;

    public NoArvore(int dado) {
        this.dado = dado;
        this.esquerda = null;
        this.direita = null;
    }
}
```

### 2.2 Pré-ordem (normal)

```java
public class PreOrdem {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        System.out.print(raiz.dado + " ");  // visita a raiz
        percurso(raiz.esquerda);            // depois subárvore esquerda
        percurso(raiz.direita);             // depois subárvore direita
    }
}
```

### 2.3 Pré-ordem inversa

```java
public class PreOrdemInversa {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        System.out.print(raiz.dado + " ");  // visita a raiz
        percurso(raiz.direita);             // depois subárvore direita
        percurso(raiz.esquerda);            // depois subárvore esquerda
    }
}
```

> **Diferença:** apenas a ordem das duas chamadas recursivas foi invertida.

### 2.4 Em-ordem (normal)

```java
public class EmOrdem {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        percurso(raiz.esquerda);             // primeiro subárvore esquerda
        System.out.print(raiz.dado + " ");  // depois visita a raiz
        percurso(raiz.direita);             // depois subárvore direita
    }
}
```

### 2.5 Em-ordem inversa

```java
public class EmOrdemInversa {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        percurso(raiz.direita);             // primeiro subárvore direita
        System.out.print(raiz.dado + " ");  // depois visita a raiz
        percurso(raiz.esquerda);            // depois subárvore esquerda
    }
}
```

### 2.6 Pós-ordem (normal)

```java
public class PosOrdem {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        percurso(raiz.esquerda);             // primeiro subárvore esquerda
        percurso(raiz.direita);             // depois subárvore direita
        System.out.print(raiz.dado + " ");  // por último a raiz
    }
}
```

### 2.7 Pós-ordem inversa

```java
public class PosOrdemInversa {
    public static void percurso(NoArvore raiz) {
        if (raiz == null)
            return;
        percurso(raiz.direita);             // primeiro subárvore direita
        percurso(raiz.esquerda);            // depois subárvore esquerda
        System.out.print(raiz.dado + " ");  // por último a raiz
    }
}
```

## 3. Exemplo Prático (Árvore com raiz 42)

Considere a seguinte árvore:

```
          42
         /  \
       16    57
      /  \     \
     8   35     48
    / \         /
   5  11       47
```

### 3.1 Pré-ordem (normal: raiz → esq → dir)

**Resultado:** `42, 16, 8, 5, 11, 35, 57, 48, 47`

- Primeiro: raiz (42)
- Último: nó mais à direita possível (47)

### 3.2 Pré-ordem inversa (raiz → dir → esq)

**Resultado:** `42, 57, 48, 47, 16, 35, 8, 11, 5`

- Primeiro: raiz (42)
- Último: nó mais à esquerda possível (5)

### 3.3 Em-ordem (normal: esq → raiz → dir)

**Resultado:** `5, 8, 11, 16, 35, 42, 47, 48, 57`

- Primeiro: nó mais à esquerda (5)
- Último: nó mais à direita (57)
- Raiz (42) aparece no meio

### 3.4 Em-ordem inversa (dir → raiz → esq)

**Resultado:** `57, 48, 47, 42, 35, 16, 11, 8, 5`

- Primeiro: nó mais à direita (57)
- Último: nó mais à esquerda (5)
- Raiz (42) ainda aparece no meio (agora após toda a subárvore direita)

### 3.5 Pós-ordem (normal: esq → dir → raiz)

**Resultado:** `5, 11, 8, 35, 16, 47, 48, 57, 42`

- Primeiro: nó mais à esquerda (5)
- Último: raiz (42)

### 3.6 Pós-ordem inversa (dir → esq → raiz)

**Resultado:** `57, 48, 47, 35, 16, 11, 8, 5, 42`

- Primeiro: nó mais à direita (57)
- Último: raiz (42)

## 4. Tabela Comparativa (para revisão rápida)

| PERCURSO | PRIMEIRO | ÚLTIMO | RAIZ | CARACTERÍSTICA |
| --- | --- | --- | --- | --- |
| **Pré-ordem (normal)** | raiz | mais à direita | primeira | raiz → esq → dir |
| **Pré-ordem inversa** | raiz | mais à esquerda | primeira | raiz → dir → esq |
| **Em-ordem (normal)** | mais à esquerda | mais à direita | meio | esq → raiz → dir |
| **Em-ordem inversa** | mais à direita | mais à esquerda | meio | dir → raiz → esq |
| **Pós-ordem (normal)** | mais à esquerda | raiz | última | esq → dir → raiz |
| **Pós-ordem inversa** | mais à direita | raiz | última | dir → esq → raiz |

> ### 4.1 Regra para transformar normal → inverso
> - Troque **esq** por **dir** e **dir** por **esq** na sequência.
> - A posição da raiz (primeira, meio ou última) **permanece a mesma**.

## 5. Síntese de Implementação (Código Estrutural)

```java
// Estrutura base para qualquer percurso
public static void percurso(NoArvore raiz) {
    if (raiz == null) return;
    // [1] Visita (ou chama recursão para esq/dir)
    // [2] Chama recursão para esquerda (ou direita)
    // [3] Chama recursão para direita (ou esquerda)
}
```

### 5.1 O que muda em cada percurso

| PERCURSO | ORDEM DAS OPERAÇÕES |
| --- | --- |
| Pré-ordem (normal) | 1. Visita raiz<br>2. Recursão esq<br>3. Recursão dir |
| Pré-ordem inversa | 1. Visita raiz<br>2. Recursão dir<br>3. Recursão esq |
| Em-ordem (normal) | 1. Recursão esq<br>2. Visita raiz<br>3. Recursão dir |
| Em-ordem inversa | 1. Recursão dir<br>2. Visita raiz<br>3. Recursão esq |
| Pós-ordem (normal) | 1. Recursão esq<br>2. Recursão dir<br>3. Visita raiz |
| Pós-ordem inversa | 1. Recursão dir<br>2. Recursão esq<br>3. Visita raiz |

> ### 5.2 Dica de prova (sem código)
> - **Pré-ordem:** raiz sempre no início.
> - **Pós-ordem:** raiz sempre no fim.
> - **Em-ordem:** raiz no meio (não é a primeira nem a última).
> - Se a questão pedir para identificar o tipo de percurso a partir de uma listagem:
>   1. Veja a posição da raiz (início, meio ou fim).
>   2. Veja se a subárvore que aparece primeiro é a esquerda (normal) ou a direita (inversa).

---

*Material complementar à aula "Árvores Binárias – Ordens de Percurso (Implementações e Códigos)" (professor Rogério Gildo Araujo, Gran Concursos).*