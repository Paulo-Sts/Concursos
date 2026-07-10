# Anotações – Estrutura de Dados – Árvores Binárias: Ordens de Percurso

## 1. Conceituação

- Ordens de percurso (*tree traversals*) são procedimentos para **visitar todos os nós** de uma árvore binária de forma sistemática.
- Existem três ordens principais (clássicas), além de suas respectivas **versões inversas**.
- As bancas (especialmente **Cesgranrio**) costumam cobrar tanto as ordens normais quanto as inversas.

## 2. Ordens Clássicas (Normais)

| PERCURSO | ABREVIAÇÃO | SEQUÊNCIA DE VISITA | POSIÇÃO DA RAIZ |
| --- | --- | --- | --- |
| **Pré-ordem** | (raiz → esq → dir) | 1. Raiz<br>2. Subárvore esquerda (SAE)<br>3. Subárvore direita (SAD) | **Primeira** informação impressa |
| **Em-ordem (simétrica)** | (esq → raiz → dir) | 1. Subárvore esquerda (SAE)<br>2. Raiz<br>3. Subárvore direita (SAD) | **No meio** da listagem |
| **Pós-ordem** | (esq → dir → raiz) | 1. Subárvore esquerda (SAE)<br>2. Subárvore direita (SAD)<br>3. Raiz | **Última** informação impressa |

> ### 2.1 Regra mnemônica
> - **Pré-ordem:** raiz **antes** das subárvores (prefixo *pré* = antes).
> - **Em-ordem:** raiz **entre** as subárvores (prefixo *em* = meio/intermediário).
> - **Pós-ordem:** raiz **depois** das subárvores (prefixo *pós* = depois).

## 3. Ordens Inversas (Reflexo)

- Nas ordens inversas, **troca-se a prioridade**: a subárvore direita (SAD) é visitada **antes** da subárvore esquerda (SAE).
- A posição da raiz **permanece a mesma** (primeira, meio ou última).

| PERCURSO INVERSO | SEQUÊNCIA DE VISITA | POSIÇÃO DA RAIZ |
| --- | --- | --- |
| **Pré-ordem inversa** | 1. Raiz<br>2. Subárvore direita (SAD)<br>3. Subárvore esquerda (SAE) | **Primeira** |
| **Em-ordem inversa** (simétrica inversa) | 1. Subárvore direita (SAD)<br>2. Raiz<br>3. Subárvore esquerda (SAE) | **No meio** |
| **Pós-ordem inversa** | 1. Subárvore direita (SAD)<br>2. Subárvore esquerda (SAE)<br>3. Raiz | **Última** |

> ### 3.1 Comparativo (normal vs. inverso)
> | PERCURSO | NORMAL | INVERSO |
> | --- | --- | --- |
> | Pré-ordem | raiz → esq → dir | raiz → dir → esq |
> | Em-ordem | esq → raiz → dir | dir → raiz → esq |
> | Pós-ordem | esq → dir → raiz | dir → esq → raiz |

## 4. Exemplo Prático (Árvore Binária)

Considere a seguinte árvore (números na raiz e subárvores):

```
        60
       /  \
     10    20
       \  / \
       50 30 70
      / \   \
     90 80   40
```

### 4.1 Pré-ordem (normal: raiz → esq → dir)

**Passos:**
1. Visita **60** (raiz)
2. Percorre SAE (raiz 10):
   - Visita **10**
   - Percorre SAE de 10: vazia
   - Percorre SAD de 10 (raiz 50):
     - Visita **50**
     - Percorre SAE de 50 (raiz 90): visita **90**
     - Percorre SAD de 50 (raiz 80): visita **80**
3. Percorre SAD (raiz 20):
   - Visita **20**
   - Percorre SAE de 20: vazia
   - Percorre SAD de 20 (raiz 30):
     - Visita **30**
     - Percorre SAE de 30: vazia
     - Percorre SAD de 30 (raiz 40): visita **40**
   - (não há filho direito além de 30)

**Resultado:** `60, 10, 50, 90, 80, 20, 30, 40`

### 4.2 Pré-ordem inversa (raiz → dir → esq)

- **60** (raiz)
- Percorre SAD primeiro:
  - **20**, depois **30**, **40** (parte direita)
- Depois SAE:
  - **10**, depois **50**, **80**, **90** (invertendo a ordem da direita para esquerda dentro da subárvore)

**Resultado:** `60, 20, 30, 40, 10, 50, 80, 90`

### 4.3 Em-ordem (normal: esq → raiz → dir)

- Percorre SAE primeiro (até a folha mais à esquerda):
  - Nó mais à esquerda: **90** (através de 10 → 50 → 90)
  - Depois **50**, depois **80**, depois **10**
- Depois raiz: **60**
- Depois SAD (parte direita):
  - **20** (raiz da direita), depois **30**, depois **40**

**Resultado:** `90, 50, 80, 10, 60, 20, 30, 40`

### 4.4 Em-ordem inversa (dir → raiz → esq)

- Percorre SAD primeiro (parte direita, mais à direita):
  - **40**, depois **30**, depois **20**
- Depois raiz: **60**
- Depois SAE (parte esquerda, ordem inversa):
  - **80**, depois **50**, depois **90**, depois **10**

**Resultado:** `40, 30, 20, 60, 80, 50, 90, 10`

### 4.5 Pós-ordem (normal: esq → dir → raiz)

- Percorre SAE:
  - **90**, **80**, **50**, **10** (com raiz 50 por último no bloco)
- Percorre SAD:
  - **40**, **30**, **20**
- Por fim, raiz: **60**

**Resultado:** `90, 80, 50, 10, 40, 30, 20, 60`

### 4.6 Pós-ordem inversa (dir → esq → raiz)

- Percorre SAD primeiro:
  - **40**, **30**, **20**
- Depois SAE:
  - **80**, **90**, **50**, **10**
- Por fim, raiz: **60**

**Resultado:** `40, 30, 20, 80, 90, 50, 10, 60`

## 5. Dicas para Identificação em Provas

### 5.1 Posição da raiz

| PERCURSO | POSIÇÃO DA RAIZ NA LISTAGEM |
| --- | --- |
| Pré-ordem (normal ou inversa) | **Primeira** |
| Em-ordem (normal ou inversa) | **No meio** (não necessariamente exatamente central, mas após todos os nós da subárvore visitada antes) |
| Pós-ordem (normal ou inversa) | **Última** |

> ### 5.2 Interpretação sem especificação
> - Se a banca **não especificar** se é ordem normal ou inversa, assume-se a **ordem normal**.
> - Se a questão apresentar alternativas e nenhuma corresponder à ordem normal, teste a **ordem inversa** (especialmente Cesgranrio).

### 5.3 Estratégia de resolução

Para determinar a ordem de percurso a partir do resultado de uma listagem:

1. **Veja a posição da raiz:**
   - Primeira → pré-ordem.
   - Meio → em-ordem.
   - Última → pós-ordem.

2. **Verifique a sequência das subárvores:**
   - Se a subárvore esquerda aparece antes da direita → ordem **normal**.
   - Se a subárvore direita aparece antes da esquerda → ordem **inversa**.

## 6. Exemplo de Implementação (Java) – Nó de Árvore

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

## 7. Síntese para Revisão Rápida

| PERCURSO | NORMAL (esq → dir) | INVERSO (dir → esq) |
| --- | --- | --- |
| **Pré-ordem** | raiz → esq → dir | raiz → dir → esq |
| **Em-ordem** | esq → raiz → dir | dir → raiz → esq |
| **Pós-ordem** | esq → dir → raiz | dir → esq → raiz |

> ### 7.1 Pegadinha comum
> - Não confunda **em-ordem inversa** com pós-ordem. Em ambos a raiz não está no início, mas em-ordem inversa tem a raiz **no meio**; pós-ordem tem a raiz **no fim**.
> - A Cesgranrio costuma cobrar **em-ordem inversa** (simétrica inversa) com frequência.

---

*Material complementar à aula "Árvores Binárias – Ordens de Percurso" (professor Rogério Gildo Araujo, Gran Concursos).*