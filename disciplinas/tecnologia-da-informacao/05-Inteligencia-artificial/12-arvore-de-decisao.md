# Árvore de Decisão

## 1. Conceitos Fundamentais
- A árvore de decisão é um algoritmo simples e de fácil explicação, pertencente ao grupo de algoritmos de classificação e regressão.
- O algoritmo constrói uma árvore baseada no conjunto de dados histórico fornecido.
- O objetivo é identificar os atributos que melhor separam os dados, ou seja, que mais auxiliam na identificação da classe.
- O conjunto de entrada x é formado por vários atributos (colunas) e o objetivo é aprender a prever y (classe ou valor numérico).
- No topo da árvore são colocados os atributos que melhor distribuem os dados do conjunto.

### 1.1 Estrutura da Árvore de Decisão
- A árvore é composta por:
  - Node root (nó raiz): primeira decisão a ser tomada;
  - Níveis de nós: decisões intermediárias;
  - Sub-árvores: ramificações da árvore;
  - Folhas: onde estão presentes as classes ou médias de números.

### 1.2 Exemplo Prático (Frutas)
- Dataset com frutas (melancia, maçã, cereja, uva).
- Atributos que descrevem a fruta: cor, tamanho, sabor.
- Primeiro atributo escolhido pelo algoritmo: cor.
  - Cor verde ⟶ segue um caminho;
  - Cor amarela ⟶ segue outro caminho;
  - Cor vermelha ⟶ segue outro caminho.
- Atributo cor separa as classes (relacionado à entropia).
- Próximo atributo escolhido: tamanho.
  - Tamanho médio ⟶ maçã (pode ser maçã verde);
  - Tamanho pequeno ⟶ próximo nível.
- Próxima decisão: sabor.
  - Doce ⟶ cereja;
  - Azedo ⟶ uva (grape).

### 1.3 Divisão do Espaço de Características
- Árvores de decisão dividem o espaço de características em eixos paralelos retangulares.
- Cada retângulo é rotulado com uma classe.
- Exemplo bidimensional (x1 e x2):
  - Primeira divisão: x2 < 3 ou x2 ≥ 3;
  - Se x2 < 3:
    - Verifica x1 < 4 ou x1 ≥ 4;
    - x1 < 4 ⟶ classe azul;
    - x1 ≥ 4 ⟶ classe vermelha.
  - Se x2 ≥ 3:
    - Segue outro caminho.
- A árvore realiza partições sucessivas, dividindo o espaço de dimensões.

> [!CAUTION] OBSERVAÇÃO:
> - A primeira divisão considera o atributo que melhor separa os dados.
> - As partições são feitas em eixos paralelos, não em diagonais.

## 2. Entropia e Ganho de Informação
- Entropia: mede o nível de desordem ou incerteza de um conjunto de dados.
- Mistura entre classes: quanto mais classes misturadas, maior a entropia.
  - Se todos os exemplos são da mesma classe ⟶ entropia = 0 (puro);
  - Se há classes equilibradas (ex.: 50%/50%) ⟶ entropia alta (máxima incerteza).
- Ao selecionar um atributo que divide o dataset, cada subconjunto gerado pode ter entropias distintas.
- Na construção da árvore, são procurados atributos que minimizem a entropia.
- Quando todos os exemplos direcionados a uma divisão forem da mesma classe:
  - Entropia = 0;
  - Subdivisão pode ser encerrada com inserção de uma folha.

### 2.1 Ganho de Informação
- Mede o quanto a entropia diminui ao dividir os dados por um atributo.
- Representa o "ganho" de pureza obtido após a divisão.
- Quanto maior o ganho, melhor o atributo para dividir.
- Escolhe o atributo que mais "organiza" o conjunto.
- É utilizado por algoritmos que constroem árvores de decisão.

### 2.2 Grau de Impureza (Índice de Gini)
- Mede o nível de impureza de um nó (quanto está misturado entre classes diferentes).
- Representa a probabilidade de erro ao classificar um item aleatoriamente.
- Gini = 0 ⟶ nó puro (todos pertencem à mesma classe);
- Gini alto ⟶ nó misto (impuro);
- Melhor atributo = menor índice Gini.

### Tabela de Conceitos
| CONCEITO | DEFINIÇÃO DIDÁTICA | O QUE MEDE | COMO INTERPRETAR |
|----------|-------------------|------------|------------------|
| Entropia | Mede o nível de desordem ou incerteza de um conjunto de dados | A "mistura" entre classes (quanto mais misto, maior a entropia) | Se todos os exemplos são da mesma classe – entropia = 0 (puro). Se há classes equilibradas – entropia alta (máxima incerteza) |
| Ganho de Informação | Mede o quanto a entropia diminui ao dividir os dados por um atributo | O "ganho" de pureza obtido após a divisão | Quanto maior o ganho, melhor o atributo para dividir. Escolhe o que mais "organiza" o conjunto |
| Grau de Impureza (Gini) | Mede o nível de impureza de um nó – ou seja, quanto ele está misturado entre classes diferentes | A probabilidade de erro se classificarmos um item aleatoriamente | Gini = 0 – nó puro. Gini alto – nó misto (impuro). Melhor atributo = menor índice Gini |

> [!CAUTION] OBSERVAÇÃO:
> - Os cálculos utilizam logaritmos e probabilidades, com fórmulas específicas que não são cobradas em prova.

> [!TIP] DICAS:
> - Entropia alta = dados misturados = maior incerteza.
> - Entropia baixa = dados puros = menor incerteza.
> - O objetivo é minimizar a entropia e maximizar o ganho de informação.
> - O índice de Gini é uma alternativa à entropia, com interpretação similar (menor índice = melhor divisão).

## 3. Algoritmos de Árvores de Decisão
- Existem três algoritmos principais:

### 3.1 ID3
- Primeiro algoritmo de decisão que obteve grande sucesso.
- Trabalha apenas com variáveis categóricas.
- Se houver variável numérica, não se trata de ID3.
- Critério de divisão: ganho de informação (baseado na entropia).
- Não trata valores ausentes.
- Não realiza poda da árvore.

### 3.2 C4.5
- Evolução do ID3.
- Trabalha com dados numéricos.
- Critério de divisão: ganho de informação normalizado.
- Permite dados categóricos (assim como o ID3).
- Trata valores ausentes.
- Realiza poda da árvore.
- Trabalha apenas com classificação (não faz regressão).

### 3.3 CART
- Único dos três que trabalha com regressão.
- Critério de divisão:
  - Para classificação: índice de Gini;
  - Para regressão: redução de variância.
- Realiza apenas divisões binárias (sempre forma dois subconjuntos).
- Trata valores ausentes.
- Realiza poda da árvore.
- Na regressão, coloca a média dos valores numéricos na folha.

### Tabela Comparativa dos Algoritmos
| CARACTERÍSTICA | ID3 | C4.5 | CART |
|----------------|-----|------|------|
| Tipo de dado | Categórico | Numérico e categórico | Numérico e categórico |
| Critério de divisão | Ganho de informação | Ganho de informação normalizado | Gini (classificação) / Redução de variância (regressão) |
| Trabalha com regressão | Não | Não | Sim |
| Trata valores ausentes | Não | Sim | Sim |
| Realiza poda | Não | Sim | Sim |
| Tipo de divisão | Múltipla | Múltipla | Binária |

> [!CAUTION] OBSERVAÇÃO:
> - C4.5 evoluiu para C5.6 e C5.0, mantendo as mesmas características básicas.
> - O ID3 é o único que não trabalha com dados numéricos.
> - O CART é o único que permite regressão, colocando a média na folha.
> - O CART sempre faz divisões binárias (árvore com divisão ternária não foi construída com CART).

## 4. Poda (Pruning)
- Overfitting ocorre quando a árvore possui muitos níveis, especializando-se excessivamente no conjunto de treinamento.
- A árvore tende a separar perfeitamente o conjunto de treinamento, inclusive dados incorretos.
- A solução para árvores de decisão é a poda.
- Poda consiste na remoção de parte da árvore, substituindo-a por uma folha.
- Aumenta o erro no conjunto de treinamento, mas melhora o desempenho em dados nunca vistos.

### 4.1 Tipos de Poda
- Poda pré: ocorre durante a construção da árvore, realizando cortes enquanto ela é formada.
- Poda pós: ocorre após a conclusão da árvore, removendo sub-árvores e substituindo-as por folhas.

### 4.2 Poda nos Algoritmos
- ID3: não realiza poda.
- C4.5: realiza poda.
- CART: realiza poda.

## 5. Interpretabilidade
- A árvore de decisão é o único algoritmo explicável por natureza.
- É possível explicar de onde a saída foi obtida, seguindo a sequência de decisões.
- Exemplo: decisão sobre cartão de crédito VIP:
  - Verifica salário (> R$ 20 mil?);
  - Verifica valor investido (> R$ 200 mil?);
  - Verifica dívida no banco (> R$ 1 mil?);
  - Verifica número de filhos (> 3?);
  - Conclusão: não é VIP.
- É possível informar ao solicitante o motivo da decisão.
- Diferente de redes neurais, que não são explicáveis (dados são multiplicados por pesos, passam por funções de ativação e neurônios ocultos, sem rastreabilidade clara).

> [!TIP] DICAS:
> - Interpretabilidade é uma característica marcante da árvore de decisão.
> - Em provas, quando o enunciado mencionar "modelo interpretável" ou "explicável", a tendência é a árvore de decisão.
> - Redes neurais são consideradas "caixa-preta" (não explicáveis).

## 6. Aspectos Adicionais
- A árvore de decisão é versátil e pode ser usada para classificação e regressão.
- O CART é o único algoritmo de árvore de decisão que trabalha com regressão.
- Na regressão, o valor predito na folha é a média dos valores numéricos.
- A árvore de decisão pode ser usada para classificação binária (ex.: suspeito/não suspeito, VIP/não VIP).

> [!CAUTION] OBSERVAÇÃO:
> - A árvore de decisão cria uma série de regras (ex.: se x1 > 2, segue caminho; se x2 > 3, classifica como classe A).
> - Essas regras auxiliam na compreensão e interpretabilidade do modelo.
> - Quando o problema é tabular, com vários atributos e regras complexas, a árvore de decisão é indicada.