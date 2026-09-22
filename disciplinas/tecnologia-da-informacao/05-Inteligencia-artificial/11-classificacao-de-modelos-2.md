# Classificação de Modelos 2

## 1. Métricas de Classificação
- As métricas de classificação são utilizadas para avaliar o desempenho de modelos preditivos em problemas de classificação, especialmente em cenários com classes desbalanceadas.
- A acurácia pode ser uma métrica enganosa em problemas com classes significativamente desbalanceadas, pois o modelo pode obter alta acurácia classificando tudo como a classe majoritária sem realmente aprender a distinguir as classes.
- Para problemas onde a identificação de eventos negativos (fraudes, doenças, incêndios) é crítica, é necessário utilizar métricas que avaliem especificamente o desempenho do modelo em identificar corretamente a classe positiva.

### 1.1 Sensibilidade (Recall ou Revocação)
- A sensibilidade mede a proporção de instâncias positivas que foram corretamente identificadas pelo modelo.
- É uma métrica importante para encontrar falsos negativos, especialmente em problemas críticos como transações fraudulentas, diagnóstico de doenças ou identificação de incêndios.
- Quanto maior a sensibilidade, menor será a quantidade de falsos negativos do modelo.
- Fórmula: VP / (VP + FN)
- A sensibilidade é a métrica mais adequada para problemas com classes desbalanceadas, pois considera a proporção de previsões corretas em relação ao total de amostras positivas.

> [!TIP] DICAS: 
> - Sensibilidade, recall e revocação são sinônimos e representam a mesma métrica.
> - A sensibilidade é o inverso da especificidade: enquanto a sensibilidade avalia o desempenho na classe positiva, a especificidade avalia o desempenho na classe negativa.

### 1.2 Especificidade
- A especificidade mede a capacidade do modelo de identificar corretamente os casos negativos.
- Pode ser interpretada como o recall da classe negativa.
- Fórmula: VN / (VN + FP)

### 1.3 Precisão (Precision)
- A precisão é igual ao verdadeiro positivo dividido pela soma entre os verdadeiros positivos e os falsos positivos.
- Fórmula: VP / (VP + FP)
- Enquanto a sensibilidade utiliza os falsos negativos no denominador, a precisão utiliza os falsos positivos.

> [!CAUTION] OBSERVAÇÃO: 
> - É fundamental não confundir precisão com acurácia. A precisão avalia a qualidade das previsões positivas, enquanto a acurácia avalia o percentual geral de acertos do modelo.

### 1.4 F1-Score
- O F1-score é uma métrica que combina a precisão e o recall (sensibilidade) em uma única medida de desempenho.
- É uma média harmônica entre as duas métricas, penalizando valores extremos.
- Fórmula: 2 * ((Precisão * Recall) / (Precisão + Recall))
- O F1-score é utilizado quando se deseja avaliar o equilíbrio entre precisão e sensibilidade.
- O resultado do F1-score sempre estará entre os valores da precisão e do recall, aproximando-se do menor valor.

> [!TIP] DICAS: 
> - O F1-score é a métrica ideal quando se busca um equilíbrio entre precisão e recall.
> - Para problemas onde os falsos negativos são mais críticos que os falsos positivos, a sensibilidade (recall) deve ser priorizada.

### 1.5 Matriz de Confusão
- A matriz de confusão é uma tabela que resume o desempenho de um modelo de classificação, organizando as previsões em quatro categorias:

| RESULTADO DO MODELO | POSITIVO | NEGATIVO |
|---------------------|----------|----------|
| Valor Real Positivo | VP | FN |
| Valor Real Negativo | FP | VN |

- VP (Verdadeiro Positivo): modelo previu positivo e o valor real era positivo.
- VN (Verdadeiro Negativo): modelo previu negativo e o valor real era negativo.
- FP (Falso Positivo - Erro Tipo 1): modelo previu positivo, mas o valor real era negativo.
- FN (Falso Negativo - Erro Tipo 2): modelo previu negativo, mas o valor real era positivo.

#### 1.5.1 Matriz de Confusão para Cálculo das Métricas
| PREDIÇÃO | REALIDADE | SIM | NÃO |
|----------|-----------|-----|-----|
| Sim | | 600 (VP) | 400 (FN) |
| Não | | 100 (FP) | 900 (TN) |

- Cálculo da Acurácia: (VP + TN) / (VP + TN + FP + FN) = (600 + 900) / (600 + 900 + 100 + 400) = 1500 / 2000 = 75%
- Cálculo da Sensibilidade: VP / (VP + FN) = 600 / (600 + 400) = 600 / 1000 = 60%
- Cálculo da Especificidade: TN / (TN + FP) = 900 / (900 + 100) = 900 / 1000 = 90%

> [!CAUTION] OBSERVAÇÃO: 
> - A acurácia não deve ser confundida com a precisão. Acurácia é o percentual geral de acertos, enquanto precisão avalia apenas os acertos entre as previsões positivas.
> - A sensibilidade não é conhecida como F-measure, F-score ou F1-score; esses termos referem-se a outra métrica que combina precisão e recall.

## 2. Curva ROC (Receiver Operating Characteristic)
- A curva ROC é uma representação gráfica do desempenho de um modelo de classificação binária em diferentes limiares de decisão.
- É utilizada para avaliar o poder discriminatório de modelos de classificação.
- O gráfico relaciona a Taxa de Verdadeiros Positivos (TVP) com a Taxa de Falsos Positivos (TFP) para diferentes pontos de corte do limiar de decisão.
- TVP = VP / (VP + FN)
- TFP = FP / (FP + VN)

### 2.1 Características da Curva ROC
- O classificador ideal apresenta recall (TVP) igual a 1 (sem falsos negativos) e falsos positivos zerados (TFP = 0).
- Quanto mais próxima a curva estiver do canto superior esquerdo do gráfico, melhor será o poder discriminatório do modelo.
- A área sob a curva ROC (AUC) é uma métrica de qualidade para avaliar o modelo.

> [!TIP] DICAS: 
> - O canto superior esquerdo representa o ponto ideal, onde o modelo classifica corretamente todos os positivos sem gerar falsos positivos.
> - A afirmativa de que o canto superior direito seria o ideal está incorreta: o canto superior direito representa o pior cenário possível.

### 2.2 Área Sob a Curva (AUC)
- A AUC (Area Under the Curve) é uma métrica que quantifica o desempenho do modelo através da área sob a curva ROC.
- Quanto mais a AUC se aproxima de 1, melhor é o desempenho do modelo para classificação.
- A AUC permite comparar modelos independentemente do limiar de decisão escolhido.
- O método não paramétrico para calcular a AUC não assume que os dados seguem uma distribuição específica como a normal.

> [!TIP] DICAS: 
> - AUC = 0,5 indica um modelo sem capacidade discriminatória (equivalente a um palpite aleatório).
> - AUC > 0,5 indica que o modelo tem algum poder discriminatório.
> - AUC = 1 indica um modelo perfeito.

### 2.3 Limiares de Decisão e Matriz de Confusão
- A matriz de confusão representa o desempenho do modelo em um único limiar de decisão específico.
- A curva ROC representa o desempenho do modelo em todos os limiares de decisão possíveis.
- Dada apenas uma matriz de confusão, é possível calcular acurácia, precisão, recall, especificidade e F1-score.
- Entretanto, com apenas uma matriz de confusão, não é possível calcular a AUC (área sob a curva ROC).

> [!CAUTION] OBSERVAÇÃO: 
> - Ao ajustar o modelo para minimizar erros do tipo 2 (falsos negativos), geralmente os erros do tipo 1 (falsos positivos) tendem a aumentar.
> - O treinamento mais longo não é necessariamente a solução para melhorar o modelo, pois pode levar ao overfitting.

## 3. Diretrizes para Escolha de Métricas
- Para problemas com classes desbalanceadas, a acurácia não é a métrica mais adequada.
- Quando a identificação de falsos negativos é crítica (diagnóstico de doenças, detecção de fraudes, identificação de incêndios), a sensibilidade (recall) é a métrica mais importante.
- Quando o equilíbrio entre precisão e recall é necessário, o F1-score é a métrica apropriada.
- A especificidade é recomendada quando a identificação correta de casos negativos é prioritária.

### 3.1 Erros Tipo 1 e Tipo 2
- Erro Tipo 1 (Falso Positivo): modelo prevê positivo quando o real é negativo. Geralmente tolerado em diagnósticos, pois há análise posterior.
- Erro Tipo 2 (Falso Negativo): modelo prevê negativo quando o real é positivo. É mais crítico em problemas de saúde, segurança e detecção de fraudes.
- Em problemas onde o erro tipo 2 é mais crítico, a métrica de sensibilidade (recall) deve ser priorizada.

> [!CAUTION] OBSERVAÇÃO: 
> - Para modelos de diagnóstico por imagem, como detecção de câncer de pele, os falsos negativos são mais críticos que os falsos positivos, pois podem comprometer a saúde do paciente.