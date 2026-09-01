# Introdução à Aprendizado de Máquina 

## 1. Conceitos Fundamentais
- O Machine Learning (ML) ou aprendizado de máquina consiste na criação de máquinas que aprendem por meio da identificação de padrões e da realização de previsões automáticas.
- Representa uma subárea da Inteligência Artificial (IA), campo responsável pelo desenvolvimento de sistemas capazes de realizar tarefas que exigem raciocínio, percepção e tomada de decisão.
- O aprendizado ocorre pela exposição contínua à experiência, que no contexto da tecnologia da informação corresponde às bases de dados históricas.
- Diferente dos sistemas tradicionais que seguem instruções fixas e manuais, os sistemas de IA extraem regras automaticamente a partir das informações contidas nos dados.
- Quanto mais dados e exemplos o sistema recebe, mais precisos se tornam os seus resultados.

> [!CAUTION] OBSERVAÇÃO:
> - O Machine Learning não tem como objetivo principal a automação de processos, embora possa ser integrado a sistemas automatizados através do conceito de MLOps.

## 2. Áreas de Aplicação da Inteligência Artificial
- Análise descritiva: identifica padrões ocultos em grandes bases de dados, permitindo, por exemplo, o agrupamento automático de dados semelhantes como notas de estudantes em níveis de desempenho;
- Análise preditiva: utiliza dados históricos para antecipar eventos futuros e prever comportamentos, como a detecção de fraudes em transações de cartão de crédito;
- Inteligência Artificial generativa: produz novos conteúdos originais, como textos, imagens, vídeos e músicas, a partir de padrões aprendidos em grandes volumes de dados.

## 3. Etapas do Processo de Aprendizado de Máquina
- Coleta e preparação dos dados: reunião de informações relevantes provenientes de múltiplas fontes;
- Pré-processamento: limpeza, transformação, normalização e padronização dos dados para garantir qualidade e consistência;
- Treinamento do modelo: etapa em que o algoritmo efetivamente aprende a partir dos dados por meio de múltiplas iterações para ajuste de parâmetros internos;
- Validação e teste: avaliação da capacidade de generalização do modelo para dados que ele nunca viu anteriormente;
- Implantação: uso prático do modelo em ambiente de produção para realizar previsões ou apoiar decisões.

> [!TIP] DICAS:
> - O primeiro e mais trabalhoso passo em um projeto de ciência de dados consiste na organização, preparação e pré-processamento da base de dados.

## 4. Estrutura e Partes do Dataset
- O dataset é o conjunto de dados estruturado e tabular que serve de entrada para o modelo de aprendizado de máquina.
- Exemplos: representam as linhas do dataset, também chamados de instâncias, registros ou pontos de dados.
- Atributos: representam as colunas ou características que descrevem cada exemplo, como valor, local e horário em uma transação financeira.
- Representação matemática: o processo é descrito pela função Y = f(X), onde X são os atributos de entrada e Y é a saída esperada.

| COMPONENTE | SINÔNIMOS | FUNÇÃO |
|---|---|---|
| Exemplo | Instância, caso, registro, linha, dado | Unidade de informação para treinamento |
| Atributo | Campo, feature, variável independente, coluna | Características descritivas do exemplo |
| Classe | Rótulo, alvo, target, variável dependente | Variável que o modelo deve aprender a prever |

> [!CAUTION] OBSERVAÇÃO:
> - Nem todo dataset possui uma coluna de classe; isso ocorre em análises descritivas ou aprendizado não supervisionado onde o foco é apenas identificar padrões ocultos.

## 5. Divisão do Dataset e Métricas de Desempenho
- Conjunto de treinamento: representa geralmente 80% dos dados e é utilizado para ensinar o modelo;
- Conjunto de teste: corresponde a cerca de 20% dos dados e é reservado para avaliar o desempenho com informações inéditas;
- Generalização: capacidade do modelo de prever resultados corretos para novos dados que não fizeram parte do treinamento;
- Métricas: o sucesso do modelo é medido através de indicadores como acurácia, precisão, revocação e F1-score.

> [!CAUTION] OBSERVAÇÃO:
> - Treinar e testar o modelo utilizando o mesmo conjunto de dados gera resultados enganosos, pois o sistema teria acesso prévio às respostas corretas.