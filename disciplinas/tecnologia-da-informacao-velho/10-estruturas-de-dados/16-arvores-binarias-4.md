# Anotações – Estrutura de Dados – Árvores Binárias: Ordens de Percurso (Questões Comentadas)

## 1. Estratégia Geral para Resolver Questões de Percurso

| SITUAÇÃO | CONDUTA |
| --- | --- |
| A questão **especifica** o tipo de percurso (pré-ordem, em-ordem, pós-ordem) | Aplicar a definição correspondente (normal ou inversa, conforme indicado). |
| A questão **não especifica** se é normal ou inversa | Testar primeiro a **ordem normal** (esquerda → raiz → direita para em-ordem; raiz → esquerda → direita para pré-ordem; esquerda → direita → raiz para pós-ordem). Se nenhuma alternativa corresponder, testar a **ordem inversa**. |
| A questão é da **Cesgranrio** | Esta banca tem preferência pela **em-ordem inversa** (simétrica inversa). Para pré-ordem e pós-ordem, costuma utilizar a **normal**. |

> ### 1.1 Dica importante do professor
> - Em questões de múltipla escolha, se a ordem normal não produzir nenhuma das alternativas, **a ordem inversa** pode ser a resposta esperada.
> - Para **em-ordem**, a Cesgranrio frequentemente adota a **versão inversa** (direita → raiz → esquerda).

## 2. Questões Comentadas

### 2.1 (CESGRANRIO/2024/CAIXA – Técnico Bancário/TI)

**Figura:** árvore binária (mesma do material de percursos – raiz 60, subárvores 10 e 20 etc.).

**Pergunta:** Aplicando-se o percurso **em-ordem** e somando o 2º, 3º e 4º valores obtidos, qual o resultado?

**Resolução:**

- **Em-ordem normal (esq → raiz → dir):** `90, 50, 80, 10, 60, 20, 30, 40`
  - 2º valor: 50
  - 3º valor: 80
  - 4º valor: 10
  - Soma: `50 + 80 + 10 = 140` → *nenhuma alternativa com 140.*

- **Em-ordem inversa (dir → raiz → esq):** `40, 30, 20, 60, 10, 80, 50, 90`
  - 2º valor: 30
  - 3º valor: 20
  - 4º valor: 60
  - Soma: `30 + 20 + 60 = 110` (alternativa **b** – o material indica 120? Revisão: a sequência correta da inversa é `40,30,20,70,100,60,10,80,50,90`. Soma 2º+3º+4º = 30+20+70=120 → alternativa **b, 120**.)

**Gabarito:** **b) 120**.

### 2.2 (CESGRANRIO/2024/IPEA – Técnico de Planejamento/Desenvolvimento de Sistemas)

**Pergunta:** "Qual será o sexto valor a ser exibido por essa função?" (sem especificar o tipo de percurso)

**Resolução:**

- **Em-ordem normal:** `90, 50, 80, 10, 60, 100, 70, 20, 30, 40`
  - 6º valor: 100 → *não consta nas alternativas.*

- **Em-ordem inversa:** `40, 30, 20, 70, 100, 60, 10, 80, 50, 90`
  - 6º valor: 60 → alternativa **c**.

**Gabarito:** **c) 60**.

> ### 2.2.1 Observação
> - A banca não especificou o tipo de percurso. O professor testou ambas as versões e identificou que a **inversa** produziu o valor presente nas alternativas.

### 2.3 (IDECAN/2023/SEFAZ-RR – Desenvolvedor de Software)

**Item:** "Selecione a alternativa que mostra as estratégias de ordenação de nós de uma árvore binária."

**Alternativas:**
- a) malloc()
- b) Raiz; Nós; Folhas
- c) FIFO; LIFO; FEFO
- d) Pré-ordem; Pós-ordem (incompleta)
- e) Pré-ordem; Intra-ordem; Pós-ordem

**Gabarito:** **e) Pré-ordem; Intra-ordem; Pós-ordem**.

**Comentário:** A terminologia correta é **pré-ordem, em-ordem (ou intra-ordem, simétrica) e pós-ordem**. A alternativa "d" está incompleta (faltou em-ordem).

### 2.4 (CESGRANRIO/2023/BANCO DO BRASIL – Agente de Tecnologia)

**Entrada (pré-ordem):** `80, 84, 55, 76, 72`

**Pergunta:** Qual árvore foi recebida como parâmetro?

**Resolução:**
- **Pré-ordem normal:** raiz → esquerda → direita.
- **Pré-ordem inversa:** raiz → direita → esquerda.

**Primeira informação = raiz = 80** → eliminar alternativas cuja raiz não seja 80.

**Testando as alternativas:**

- Alternativa **a**: a estrutura corresponde a uma árvore onde, em pré-ordem normal, gera-se `80, 84, 55, 76, 72`. ✅

**Gabarito:** **a**.

### 2.5 (FEPESE/2022/UDESC – Analista de Sistemas)

**Árvore fornecida** (números: 25 raiz, subárvore esquerda com 15,10,4,12,22,18,24; subárvore direita com 50,35,31,44,70,66,90).

**Pergunta:** Sequência do percurso **pré-ordem** (pre-order).

**Resolução:**

- Pré-ordem normal: raiz → esquerda → direita.
- A raiz é **25** → a sequência deve começar com 25.
- Alternativa **e** começa com 25.

**Verificação completa da alternativa e:** `25, 15, 10, 4, 12, 22, 18, 24, 50, 35, 31, 44, 70, 66, 90` (corresponde à pré-ordem normal da árvore).

**Gabarito:** **e**.

## 3. Síntese para Resolução de Questões de Percurso

| PASSO | AÇÃO |
| --- | --- |
| 1 | Identifique a **raiz** (primeiro elemento na pré-ordem; último na pós-ordem; no meio na em-ordem). |
| 2 | Verifique se a questão especifica **normal** ou **inversa**. |
| 3 | Se não especificar, teste primeiro a **normal**. |
| 4 | Se a normal não produzir alternativa compatível, teste a **inversa**. |
| 5 | Para a Cesgranrio: **em-ordem** → privilegie a **inversa**. |

> ### 3.1 Reconhecimento do tipo de percurso pela posição da raiz
> | POSIÇÃO DA RAIZ NA LISTAGEM | TIPO DE PERCURSO |
> | --- | --- |
> | Primeira | Pré-ordem (normal ou inversa) |
> | No meio (não primeira nem última) | Em-ordem (normal ou inversa) |
> | Última | Pós-ordem (normal ou inversa) |

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESGRANRIO/2024/CAIXA) | b |
| 02 (CESGRANRIO/2024/IPEA) | c |
| 03 (IDECAN/2023/SEFAZ-RR) | e |
| 04 (CESGRANRIO/2023/BB) | a |
| 05 (FEPESE/2022/UDESC) | e |

---

*Material complementar à aula "Árvores Binárias – Ordens de Percurso III" (professor Rogério Gildo Araujo, Gran Concursos).*