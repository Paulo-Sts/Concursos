# Anotações

# Estruturas de Dados – Listas

## 1. Conceituação de Estruturas de Dados e Listas

### 1.1 Estruturas de dados

- São estruturas que carregam informações de dados e as operações relacionadas a essas estruturas.

### 1.2 Listas (Listas Lineares)

- Conjuntos de elementos, objetos, variáveis, tarefas ou qualquer coisa que se possa enumerar ou formar um conjunto.
- Estruturas de dados nas quais os elementos do **mesmo tipo** estão organizados de maneira **sequencial** (existe uma ordem lógica entre eles, ainda que fisicamente possam não estar em sequência).

### 1.3 Exemplos cotidianos de listas

- Pessoas na fila de um banco.
- Letras em uma palavra.
- Relação de notas dos alunos de uma turma.
- Itens em estoque.
- Dias da semana.
- Vagões de um trem.
- Pilha de pratos.
- Cartas de baralho.

## 2. Operações sobre Listas

| OPERAÇÃO | DESCRIÇÃO |
| --- | --- |
| Criar | uma lista |
| Remover | uma lista |
| Inserir | um elemento na lista |
| Remover | um elemento da lista |
| Acessar | um elemento da lista |
| Alterar | um elemento da lista |
| Combinar | duas ou mais listas |
| Ordenar | uma lista |
| Copiar | uma lista |
| Localizar | elemento através de informação |

## 3. Tipos de Alocação em Listas

### 3.1 Alocação Sequencial

- **Características:**
  - Elementos armazenados em posições **contíguas** na memória.
  - Implementada em **arrays** (arranjos, vetores).
  - O acesso a um elemento é direto pelo índice.
- **Vantagem:** acesso rápido e simples.
- **Desvantagem:** tamanho fixo definido em tempo de compilação – não é possível aumentar ou diminuir dinamicamente.

> ### 3.1.1 Observação
> - Em Java, por exemplo, um array de inteiros com 5 posições não pode ter seu tamanho alterado após criado.

### 3.2 Alocação Encadeada (Listas Encadeadas)

- **Características:**
  - Os elementos **não estão necessariamente armazenados sequencialmente** na memória.
  - Cada nó armazena um **ponteiro** (referência) que indica a posição do próximo elemento.
  - A ordem lógica entre os elementos é mantida pelos ponteiros.
- **Vantagem:** permite criar ou remover elementos em tempo de execução, sem tamanho fixo pré-definido.
- **Desvantagem:** acesso sequencial (não indexado diretamente).

> ### 3.2.1 Definição (questão FUNDATEC 2022)
> - A estrutura caracterizada por um conjunto de dados dispostos por uma sequência de nós, onde cada nó também armazena um ponteiro que indica a posição do próximo elemento, é a **lista encadeada**.

## 4. Sinônimos de Array

- **Array**
- **Arranjo**
- **Vetor** (na lógica de programação)

## 5. Questões de Concurso Comentadas

### 5.1 (FUNDATEC/2022/PREFEITURA DE FLORES DA CUNHA/RS – TÉCNICO EM INFORMÁTICA)

**Item:** Assinale a estrutura de dados caracterizada por um conjunto de dados dispostos por uma sequência de nós, onde cada nó também armazena um ponteiro que indica a posição do próximo elemento.

**Alternativa correta:** **c) Lista encadeada**.

**Comentário:** Lista encadeada possui nós com ponteiros para o próximo elemento, não exigindo contiguidade física na memória.

### 5.2 (CESPE/2013/MPU – TÉCNICO – TECNOLOGIA DA INFORMAÇÃO E COMUNICAÇÃO)

**Item:** Existem duas formas de representar o armazenamento de dados estruturados: a sequencial, que é utilizada para estruturas de tamanho fixo, como arrays, e a encadeada, que é utilizada para estruturas de tamanho variado, como listas, pilhas e vetores.

**Gabarito:** **Errado**.

**Comentário:** O erro está em incluir **vetores** como exemplo de estruturas de tamanho variado. Vetor é sinônimo de array, que é de tamanho fixo e usa alocação sequencial. O correto seria "listas, pilhas e **filas**" (estruturas dinâmicas).

### 5.3 (COPESE/UFPI/2017/UFPI – ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

**Item:** Em uma lista encadeada, cada elemento ocupa posição sucessiva ao elemento anterior.

**Gabarito:** **Falso**.

**Comentário:** Em uma lista encadeada, os elementos não necessariamente ocupam posições sucessivas (contíguas) na memória. Apenas a ordem lógica é mantida por ponteiros.

## GABARITO GERAL

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FUNDATEC) | c |
| 02 (CESPE) | E |
| 03 (COPESE/UFPI) | Falso (na questão original a sequência foi considerada correta? O material indica resposta "e" – mas o item isolado é falso) |

> ### Observação sobre a questão 3
> - O material indica "3. e" como resposta, provavelmente referindo-se à alternativa correta no contexto da prova. O item analisado isoladamente é **falso**.

---

*Material elaborado com base na aula do professor Rogério Araújo (Gran Concursos).*