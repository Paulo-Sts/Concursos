# Regressão Logística

## 1. Definição e Conceitos Fundamentais
- A regressão logística é uma técnica aplicada a problemas de classificação, apesar do nome "regressão".
- Não se trata de um método de regressão, mas sim de um modelo paramétrico de classificação.
- Utiliza a função logística ou sigmoide, que recebe uma entrada e produz uma saída entre 0 e 1.
- A saída pode ser zero, um ou um valor entre zero e um, aproximando-se de zero quando representa zero, e aproximando-se de um quando representa um.
- Por esse motivo, é utilizada principalmente para classificação binária.
- Quando o resultado é zero, identifica-se uma classe; quando o resultado é um, identifica-se outra classe.

### 1.1 Função Sigmoide
- A fórmula da regressão logística é: p = 1 / (1 + e^(-z)).
- O termo "e" refere-se aos logaritmos naturais (base de Euler).
- Insere-se o valor de z na fórmula, e obtém-se p, que será um valor entre 0 e 1.
- A representação gráfica dessa função corresponde ao formato em "S" (curva sigmoide).
- Quanto menor que 10 for o valor associado a z, observa-se um comportamento específico da curva.
- Caso o sinal negativo seja retirado da fórmula, a curva é invertida.
- Quanto maior o coeficiente, mais íngreme se torna a curva.

## 2. Classificação Binária e Multiclasse
- A regressão logística é uma ferramenta de classificação binária por natureza.
- É possível utilizá-la para classificação multiclasse, com diversas classes.
- Para classificação multiclasse, executa-se uma regressão para cada classe.
- Exemplo: considerando as classes A, B e C:
  - Executa-se uma regressão para identificar se pertence à classe A ou não;
  - Outra regressão logística para indicar se pertence à classe B ou não;
  - Outra para indicar se pertence à classe C ou não.
- Se o resultado for 0,82 para a classe A, 0,97 para a classe B e 0,2 para a classe C, a classe B prevalece por apresentar o maior valor.

## 3. Aplicação Prática da Regressão Logística
- Exemplo clássico: empresa de seguros de automóveis que deseja prever se concederá ou não o contrato de seguro a um indivíduo.
- A decisão é binária: ou se concede o seguro ou não se concede.
- O modelo recebe todas as informações constantes na ficha de inscrição e prevê se o indivíduo apresentará ou não sinistro ao longo de um ano.
- Para fins didáticos, utiliza-se apenas uma variável (exemplo: idade) para demonstrar o funcionamento.
- A seguradora empregará uma regressão logística que, a partir da idade, preverá se o indivíduo irá ou não ocasionar um sinistro no período de um ano.
- Não é possível utilizar uma reta (regressão linear) para esse caso.
- Pode-se utilizar transformação logarítmica com o objetivo de reduzir outliers.

## 4. Características do Modelo
- A regressão logística é um modelo paramétrico.
- Utiliza a função logística ou sigmoide, que é a mesma função empregada nos neurônios das redes neurais artificiais.
- Trata-se de uma função de ativação bastante comum, pois sua saída é zero ou um, indicando se o neurônio é ativado ou não.
- Variáveis independentes (como local de residência, tempo de habilitação e idade) determinam a variável dependente (sinistro ou ausência de sinistro).

### 4.1 Diferença entre Regressão Logística e Regressão Linear
| CARACTERÍSTICA | REGRESSÃO LINEAR | REGRESSÃO LOGÍSTICA |
|----------------|------------------|---------------------|
| Tipo de problema | Regressão (previsão de valor numérico) | Classificação (binária ou multiclasse) |
| Variável dependente | Número (valor contínuo) | Categórica (0 ou 1; ou múltiplas classes) |
| Função utilizada | Função linear (reta) | Função logística ou sigmoide (curva em "S") |
| Saída do modelo | Valor numérico qualquer | Valor entre 0 e 1 (probabilidade) |

## 5. Overfitting e Regularização
- O algoritmo de minimização da função custo do processo de aprendizado supervisionado aplicado à regressão logística com a hipótese do modelo definida a partir da função sigmoide não é imune ao overfitting.
- O overfitting pode ocorrer na regressão logística.
- É possível mitigar o overfitting por meio de técnicas de regularização.
- A regularização torna o modelo mais adequado ao conjunto de dados.

> [!CAUTION] OBSERVAÇÃO: 
> - A regressão logística utiliza variáveis independentes numéricas (ou vetores numéricos) para prever uma variável dependente categórica binária. Não se utiliza variáveis independentes categóricas para prever uma variável lógica ou booleana.
> - A regressão logística não pode ser usada para prever variáveis dependentes contínuas. A variável prevista é categórica binária.
> - Os algoritmos de regressão logística não se baseiam em uma relação linear. A regressão logística é não linear e prevê um valor binário. A relação linear é característica da regressão linear.

> [!TIP] DICAS: 
> - A regressão logística é frequentemente confundida com regressão linear em provas. Fique atento: a regressão logística é usada para CLASSIFICAÇÃO, enquanto a regressão linear é usada para REGRESSÃO (previsão de valores numéricos).
> - Para classificação binária, a saída da regressão logística é sempre um valor entre 0 e 1, representando a probabilidade de pertencer a uma determinada classe.
> - Em problemas de classificação multiclasse, utiliza-se uma regressão logística para cada classe (abordagem "one-vs-rest").
> - A função sigmoide é a mesma utilizada como função de ativação em redes neurais artificiais.