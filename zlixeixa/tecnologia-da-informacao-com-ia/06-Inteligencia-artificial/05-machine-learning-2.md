# Introdução à Aprendizado de Máquina 2

## 1. Conjuntos de Treinamento e de Teste
- Consiste na divisão do conjunto de dados em subconjuntos para permitir que a máquina aprenda e tenha seu desempenho avaliado de forma realista.
- O subconjunto de treino é utilizado para gerar a inteligência artificial, ou seja, o modelo treinado.
- O subconjunto de teste contém dados que a máquina nunca viu durante o treinamento, servindo para calcular a acurácia, que representa o percentual de acerto.
- Essa métrica de acurácia obtida no teste representa mais fielmente o resultado do modelo no mundo real.

## 2. Divisão de Dados e Parâmetros
- A configuração completa de divisão de dados envolve três frentes distintas: treinamento, validação e teste.
- Treinamento ⟶ utilizado para o aprendizado do modelo.
- Validação ⟶ utilizado para o ajuste e a comparação de parâmetros entre as diversas estruturas de modelos.
- Teste ⟶ utilizado para a avaliação final e imparcial da solução.

### 2.1 Parâmetros e Desempenho
- Parâmetros representam as características ajustáveis de cada modelo, como a quantidade de neurônios, a taxa de aprendizagem e os pesos em uma rede neural.
- O conjunto de validação serve para verificar se, ao longo do treinamento, dados independentes apresentam melhora ou piora no desempenho.
- Durante o processo de treinamento, o erro no conjunto de treino tende a diminuir conforme o sistema ganha acesso aos dados.

> [!CAUTION] OBSERVAÇÃO: 
> - Existe o risco da máquina decorar os dados de treinamento, o que faz com que ela perca o poder de generalização e o erro comece a aumentar em dados que ela nunca viu.

## 3. Divisão Clássica ou Hold-out
- É a configuração mais simples de se preparar o dataset, definindo percentuais fixos para a separação dos dados.
- Uma divisão comum utiliza 80% para treino, 10% para validação e 10% para teste.

| CONJUNTO | FUNÇÃO | PERCENTUAL MÉDIO |
|---|---|---|
| Treinamento | Usado para ajustar os parâmetros internos do modelo | 60% a 80% |
| Validação | Usado para ajustar hiperparâmetros e comparar modelos | 10% a 20% |
| Teste | Usado apenas na avaliação final para medir a generalização | 10% a 20% |

> [!CAUTION] OBSERVAÇÃO: 
> - A fase de validação garante que o modelo não se ajuste demais ao conjunto de treinamento, fenômeno que prejudicaria a performance com novos dados.

## 4. Validação Cruzada
- Representa um processo de treinamento onde a máquina não tem acesso a dados já vistos, permitindo treinar e testar com todos os dados do dataset.
- O dataset completo é dividido em pedaços denominados folds, que não possuem sobreposição entre si.
- O processo ocorre em rodadas: em cada ciclo, um pedaço diferente é separado para teste enquanto os demais são utilizados para o treino.
- Ao final, são gerados múltiplos modelos (um para cada rodada) e o resultado final é obtido através da média das performances individuais.

### 4.1 Tipos de Validação Cruzada
- K-Fold Cross-Validation: divisão equilibrada dos dados em um número k de partes, sendo comum o uso de k=5 ou k=10.
- Stratified K-Fold: mantém a proporção original das classes em cada divisão, o que é fundamental em classificações desbalanceadas.
- Leave-One-Out (LOOCV): utiliza apenas uma única amostra para teste e todas as outras para o treino em cada rodada, sendo muito aplicado em bases de dados pequenas.

> [!TIP] DICAS: 
> - Em datasets desbalanceados (ex.: 99% transações normais e 1% fraudulentas), é de bom tom equilibrar a base para cerca de 50% de cada classe para que o modelo consiga aprender os exemplos negativos.

## 5. Validação por Bootstrap
- Técnica que utiliza amostragem com reposição para criar diversos subconjuntos de treinamento a partir do dataset original.
- Em cada rodada, realiza-se o sorteio aleatório de N valores com reposição para compor o treino; os registros que não forem selecionados formam o conjunto de teste.
- Essa abordagem permite criar modelos diferentes com subconjuntos de dados variados.

> [!CAUTION] OBSERVAÇÃO: 
> - O erro de generalização é definido como o erro cometido pela máquina ao processar dados que nunca foram apresentados a ela anteriormente.