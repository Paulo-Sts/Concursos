# Anotações (Continuação – Estruturas de Dados)

## 6. Listas Sequenciais (Arrays)

### 6.1 Sinônimos

- **Array**
- **Arranjo**
- **Vetor**

### 6.2 Conceituação

- Lista implementada por meio de **alocação sequencial** (contígua) na memória.
- Os elementos são armazenados em posições consecutivas e acessados por **índice**.
- O **tamanho** (número de posições) é definido em tempo de compilação – **não pode ser alterado** durante a execução.
- É uma estrutura **estática** (diferentemente das listas encadeadas, que são dinâmicas).

> ### 6.2.1 Exemplo prático
> - Criar um array de 6 elementos do tipo `int` → fixa-se o tipo e a quantidade. O usuário deve trabalhar apenas com essas posições.

### 6.3 Vantagens e Desvantagens

| VANTAGENS | DESVANTAGENS |
| --- | --- |
| Acesso direto a qualquer elemento pelo índice (acesso aleatório, O(1)). | Locação exagerada: alocar um array com mil posições e utilizar apenas cinco desperdiça memória. |
| Implementação simples e rápida para leitura. | Locação escassa: alocar 50 posições e precisar de 70 impede a inserção de novos elementos. |
| | Tamanho fixo definido em tempo de compilação – inflexível. |
| | Inserção e remoção (especialmente no início/meio) exigem realocação (deslocamento) de elementos. |

> ### 6.3.1 Atenção
> - A principal limitação das listas sequenciais é a **imutabilidade do tamanho**, o que pode levar ao desperdício ou à falta de espaço.

### 6.4 Operações Típicas em Listas Sequenciais

#### 6.4.1 Criação da lista
- Definir o array com um tamanho máximo (ex.: `VET[1..10]`).

#### 6.4.2 Inserção de elementos
- **No início:** todos os elementos existentes devem ser deslocados uma posição para a direita para abrir espaço.
- **No final:** se houver espaço livre, insere-se diretamente na última posição.
- **No meio:** elementos a partir da posição de inserção são deslocados à direita.

> ### 6.4.3 Acesso a um elemento
> - Acesso direto pelo índice (ex.: `VET[5]` para o sexto elemento). É rápido e independente do tamanho da lista.

#### 6.4.4 Remoção de elementos
- **No início:** remove-se o primeiro elemento; todos os demais devem ser deslocados uma posição para a esquerda.
- **No final:** basta decrementar o contador de elementos (se houver controle); a posição fica disponível.
- **No meio:** remove-se o elemento; os elementos posteriores são deslocados à esquerda para preencher a lacuna.

> ### 6.4.5 Custo das operações
> - Inserção/remoção no **início** ou **meio** custam O(n), pois exigem deslocamento de elementos.
> - Inserção/remoção no **final** custam O(1) (se houver espaço).

## 7. Questões de Concurso Comentadas

### 7.1 (IFPE/2016/TÉCNICO EM TECNOLOGIA DA INFORMAÇÃO)

**Item:** "Array - tipo de estrutura de dados estática."

**Gabarito:** **Certo**.

**Comentário:** Array (ou vetor) é uma estrutura estática porque seu tamanho é definido em tempo de compilação e não pode ser alterado durante a execução.

### 7.2 (IBFC/2014/TRE/AM – TÉCNICO JUDICIÁRIO)

**Item:** Estrutura de dados linear e estática que armazena uma sequência de objetos, todos do mesmo tipo, em posições consecutivas da memória:

**Alternativa correta:** **a) vetor**.

**Comentário:** A descrição refere-se ao array (vetor). "Lista" é um termo genérico que pode ser implementada de forma sequencial ou encadeada; portanto, não atende à especificação "estática".

### 7.3 (SUGEP/UFRPE/2016)

**Item:** "Devido a sua característica dinâmica, uma lista não pode ser implementada em um arranjo."

**Gabarito:** **Errado**.

**Comentário:** Listas podem ser implementadas de forma sequencial por meio de arranjos (arrays), gerando listas estáticas (tamanho fixo). Listas encadeadas são dinâmicas. A afirmação é falsa porque uma lista **pode** ser implementada em um arranjo (lista sequencial).

### 7.4 (CS/UFG/2014/UEAP – ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

**Item:** Vantagem na implementação de listas lineares por contiguidade física (arrays):

**Alternativa correta:** **c) o acesso direto a qualquer elemento da lista por meio do índice no arranjo.**

**Comentário:**
- a) Movimentação de dados em inserção/remoção é **desvantagem**, não vantagem.
- b) Necessidade de estimativa prévia de tamanho é **desvantagem**.
- c) Acesso direto por índice é a principal vantagem de arrays (acesso aleatório O(1)).
- d) Tempo de acesso diretamente proporcional ao tamanho do arranjo seria característica de listas encadeadas (acesso sequencial), não de arrays.

## GABARITO DAS QUESTÕES DA AULA

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (IFPE/2016) | C (Certo) |
| 02 (IBFC/2014) | a |
| 03 (SUGEP/UFRPE/2016) | E (Errado) |
| 04 (CS/UFG/2014) | c |

---

*Material complementar à aula "Estruturas de Dados – Listas Sequenciais" (professor Rogério Araújo, Gran Concursos).*