# Pipeline de Machine Learning 2

## 1. Divisão do Conjunto de Dados
- O processo de divisão dos dados visa criar subconjuntos distintos para diferentes finalidades no pipeline.
- A decisão sobre como dividir os dados é do cientista de dados, conforme os requisitos do projeto.
- Em algumas configurações, utilizam-se apenas dois conjuntos; em outras, adiciona-se um terceiro.

### 1.1 Conjuntos de Dados
- Conjunto de treinamento: utilizado para ensinar a máquina, apresentando exemplos e fornecendo a resposta correta.
  - O processo é iterativo: quando a máquina erra, seus parâmetros são ajustados para melhorar a precisão.
  - A máquina é treinada repetidamente até atingir um desempenho satisfatório.
- Conjunto de validação: ajuda a identificar problemas como overfitting durante o treinamento.
  - Durante o treinamento, observa-se a acurácia no conjunto de validação para garantir que o modelo não está se ajustando demais aos dados de treinamento.
  - Caso a acurácia caia, o treinamento é interrompido para evitar overfitting.
  - Também é utilizado para otimização de hiperparâmetros ao longo do processo.
- Conjunto de testes: utilizado para a avaliação final do modelo, com dados que a máquina nunca viu antes.
  - Simula a aplicação em dados reais e evita que a máquina memorize a resposta em vez de aprender a generalizar.

> [!TIP] DICAS: 
> - Percentuais comuns: 70-80% para treinamento, 10% para validação e 10% para testes.
> - O conjunto de validação não é obrigatório em todas as configurações.

### 1.2 Métodos de Divisão dos Dados
- Divisão aleatória ou Holdout: consiste na divisão do conjunto de dados em dois subconjuntos.
  - Exemplo: 80% para treinamento e 20% para testes.
- Validação cruzada: busca evitar o overfitting ao variar os dados destinados ao treinamento e ao teste.
  - O conjunto de dados é dividido em K partes, gerando K modelos diferentes.
  - A cada iteração, diferentes subconjuntos são utilizados para treinamento e teste, sem sobreposição.
  - Ao final, utiliza-se votação majoritária para definição da classificação final (em problemas de classificação) ou agregação dos resultados (em regressão).
- Estratificação: técnica em que a divisão dos dados leva em consideração a distribuição das classes.
  - Garante que a proporção de cada classe seja mantida em todos os subconjuntos.
  - Exemplo: em um dataset balanceado, 40% dos dados de cada subconjunto pertencem à classe A e 40% à classe B.
- Divisão temporal: utilizada em dados temporais, preservando a sequência cronológica.
  - Treinamento com dados mais antigos e testes com dados mais recentes.

> [!TIP] DICAS: 
> - A validação cruzada reduz o risco de overfitting, pois modelos diferentes são criados e avaliados.
> - A estratificação é especialmente importante em datasets desbalanceados.

## 2. Seleção do Modelo
- O modelo a ser aplicado depende das características do problema e da base de dados.
- A escolha envolve considerar o tipo de problema, o tamanho da base, a presença de ruídos ou desbalanceamento, a explicabilidade necessária, os recursos computacionais disponíveis, a performance esperada e a tolerância a overfitting.
- O processo é empírico e envolve experimentação com diferentes algoritmos e ajustes de hiperparâmetros.

### 2.1 Critérios para Seleção
- Tipo de problema:
  - Classificação: variável categórica a ser aprendida (ex.: KNN, redes neurais, SVM, Naive Bayes).
  - Regressão: previsão de um número contínuo (ex.: redes neurais, SVM).
  - Clustering: aprendizado não supervisionado, sem rótulos (ex.: K-means).
- Tamanho da base de dados:
  - Pequena: modelos simples (ex.: KNN, regressão linear).
  - Grande: modelos complexos (ex.: redes neurais, SVM).
- Dados com ruídos ou desbalanceados:
  - Técnicas recomendadas: árvores de decisão, Boosting, Random Forest.
- Dados limpos: podem ser processados com redes neurais.
- Explicabilidade:
  - Algoritmos simples e interpretáveis: árvores de decisão, regressão logística.
  - Algoritmos complexos e de difícil interpretação: redes neurais artificiais.
- Recursos computacionais:
  - Poucos recursos: regressão linear, KNN, Naive Bayes.
  - Recursos pesados: redes neurais artificiais (RNA), Deep Learning.
- Performance esperada: modelos mais complexos geralmente oferecem melhor desempenho, mas com maior risco de overfitting.
- Tolerância a overfitting: Random Forest é mais resistente ao overfitting.

> [!CAUTION] OBSERVAÇÃO: 
> - A seleção do modelo é considerada uma arte dentro dos projetos de ciência de dados.
> - Em problemas de classificação, é comum variar não apenas os modelos, mas também seus hiperparâmetros para otimizar o desempenho.

## 3. Treinamento do Modelo
- Envolve a definição da função de custo, inicialização dos hiperparâmetros, escolha do algoritmo de otimização e validação durante o treinamento.
- A regularização desempenha um papel crucial para evitar overfitting.

### 3.1 Componentes do Treinamento
- Função de custo: específica para cada modelo, utilizada para avaliar o erro do modelo.
- Inicialização dos hiperparâmetros:
  - Grid Search: explora diferentes combinações de hiperparâmetros para encontrar a que oferece a melhor acurácia.
  - Random Search: explora o espaço de busca de maneira aleatória, mais eficiente em problemas de alta dimensionalidade.
- Algoritmo do gradiente descendente: utilizado no processo de retropropagação (backpropagation).
- Validação durante o treinamento: realizada por meio de validação cruzada ou monitoramento da acurácia no conjunto de validação.
- Regularização: técnica para evitar overfitting durante o treinamento.

### 3.2 Tecnologias para Treinamento
- Scikit-learn, TensorFlow, PyTorch: para treinamento de modelos em Python.
- XGBoost, LightGBM: para modelos baseados em árvores.
- GridSearchCV, RandomSearch, Optuna: para otimização de hiperparâmetros.

> [!TIP] DICAS: 
> - A seleção do melhor conjunto de hiperparâmetros não é trivial; em muitos casos, não é possível determinar a configuração ideal apenas observando o dataset.
> - Optuna é uma ferramenta destinada especificamente à otimização de hiperparâmetros.

## 4. Avaliação do Modelo
- Utiliza-se o conjunto de testes para calcular as métricas de avaliação e verificar se o modelo está aprovado.
- A matriz de confusão é empregada para avaliar o desempenho e identificar se o modelo apresenta overfitting ou underfitting.

### 4.1 Métricas e Ferramentas
- Métricas de avaliação: acurácia, F1-score, MSE (Mean Squared Error).
- Matriz de confusão: para avaliação detalhada do desempenho.
- Overfitting e Underfitting: identificados durante a avaliação.
- Tecnologias:
  - Scikit-learn: para métricas de desempenho.
  - MLflow: para rastreamento de experimentos e avaliação estruturada.

> [!TIP] DICAS: 
> - O MLflow permite acompanhar todas as etapas do pipeline, incluindo a avaliação, de maneira estruturada.

## 5. Implantação do Modelo
- Após a avaliação, o modelo é colocado em produção.
- É necessário garantir que o pipeline e o modelo estejam preparados para lidar com dados de entrada constantes ou periódicos.
- O modelo deve ser reavaliado e, se necessário, retreinado.

### 5.1 Tipos de Implantação
- Implantação em tempo real (Online Inference): respostas imediatas a requisições.
- Implantação em lote (Batch Inference): processamento de grandes volumes de dados em intervalos.
- Implantação em dispositivos (Edge Computing): execução em dispositivos específicos (ex.: IoT).
- Implantação em contêineres: uso de Docker para empacotamento e portabilidade.

### 5.2 Tecnologias para Implantação
- Flask, FastAPI: para servir o modelo como uma API.
- Docker: para conteinerização de modelos, garantindo portabilidade e segurança.
- AWS SageMaker, Google AI Platform: para implantação de modelos na nuvem.

> [!CAUTION] OBSERVAÇÃO: 
> - O SageMaker, oferecido pela Amazon, é amplamente utilizado para implantação de modelos.
> - A conteinerização promove maior segurança ao evitar interferências entre os ambientes de desenvolvimento, homologação e produção.

## 6. Monitoramento do Modelo
- Essencial para abordar problemas como Data Drift e Concept Drift.
- Inclui monitoramento de infraestrutura, segurança e previsões anômalas.

### 6.1 Tipos de Monitoramento
- Data Drift: mudança nas características dos dados de entrada.
  - Exemplo: em um sistema que identifica transações fraudulentas, se fraudadores alteram suas estratégias, o modelo pode classificar transações fraudulentas como normais.
  - Solução: capturar novos dados e retreinar o modelo com base nas atualizações.
- Concept Drift: mudança na lógica subjacente dos dados, alterando a relação entre variáveis e classes.
  - Exemplo: mesmo que os dados permaneçam os mesmos, a relação entre as variáveis e as classes se altera, exigindo retreinamento.
- Previsões anômalas: respostas incoerentes do modelo.
  - Exemplo: o ChatGPT apresentava mais incoerências na versão 3.5 do que na versão 4.0.
  - Solução: atualizações contínuas para corrigir erros e eliminar inconsistências.
- Monitoramento da infraestrutura: garantir que o sistema suporte aumento no uso, prevenindo quedas.
- Monitoramento de segurança: proteção contra vazamentos e violações de privacidade.
- Retreinamento automático: configurado para disparar retreinamentos automatizados, mantendo o desempenho e a confiabilidade do modelo.

### 6.2 Tecnologias para Monitoramento
- Prometheus: coleta de métricas em tempo real (latência, acurácia).
- Grafana: visualização das métricas coletadas.
- Evidently AI: monitoramento de Data Drift e Concept Drift.
- MLflow: rastreamento contínuo e versão de modelos.
- ElasticSearch + Kibana: análise de logs e erros para monitorar modelos em produção.

> [!TIP] DICAS: 
> - O Prometheus é usado para coleta de métricas; o Grafana, para visualizações gráficas.
> - A ferramenta Evidently AI é voltada especificamente para monitoramento de Data Drift e Concept Drift.

## 7. Orquestração do Pipeline
- Garante o funcionamento integrado das tarefas do pipeline.
- As tarefas devem ser executadas de maneira coordenada, seja de forma periódica, em implantações em lotes, ou conforme a demanda.

### 7.1 Tecnologias para Orquestração
- Apache Airflow: orquestração de workflows complexos, permite agendamento de tarefas e rastreamento de execuções.
  - Amplamente utilizado não apenas em machine learning, mas também na automação de fluxos de trabalho.
- Kubeflow: orquestração de pipelines de ML com integração ao Kubernetes, focado em fluxos de trabalho escaláveis e distribuídos.
  - Relacionado ao gerenciamento de workflows de contêineres para diferentes etapas de um pipeline.
  - Não se caracteriza como um serviço de nuvem autônomo, mas como uma solução para organizar e executar tarefas em containers.
- MLflow: gerenciamento de experimentos, rastreamento de métricas, versionamento de modelos e suporte à automação de pipelines.
  - É uma solução abrangente, projetada para gerenciar todo o pipeline de machine learning.
  - Funcionalidades: experimentação, rastreamento e otimização de parâmetros, avaliação e reprodução de modelos, empacotamento e implantação.
- Prefect: alternativa moderna ao Airflow, fácil de configurar e flexível.

> [!CAUTION] OBSERVAÇÃO: 
> - O MLflow não é exclusivo para uma única tarefa (como treinamento ou implantação), mas sim uma ferramenta multifuncional que integra diversas etapas do pipeline.
> - O Kubeflow é uma solução para organizar e executar tarefas em containers de forma eficiente, não um serviço de nuvem autônomo.

## 8. Tecnologias e Ferramentas no Pipeline de Machine Learning

### 8.1 Principais Ferramentas por Etapa
| ETAPA DO PIPELINE | FERRAMENTAS |
|-------------------|-------------|
| Pré-processamento | Scikit-learn (one-hot encoding, label encoding, normalização, padronização); Pandas (manipulação de dados) |
| Treinamento | Scikit-learn, TensorFlow, PyTorch, XGBoost, LightGBM |
| Otimização de hiperparâmetros | GridSearchCV, RandomSearch, Optuna |
| Avaliação | Scikit-learn (métricas), MLflow (rastreamento de experimentos) |
| Implantação | Flask, FastAPI (APIs), Docker (conteinerização), AWS SageMaker, Google AI Platform |
| Monitoramento | Prometheus, Grafana, Evidently AI, MLflow, ElasticSearch + Kibana |
| Orquestração | Apache Airflow, Kubeflow, MLflow, Prefect |

### 8.2 Observações sobre Ferramentas Específicas
- Scikit-learn: ferramenta mais comum em Python para transformação de variáveis categóricas em numéricas (one-hot encoding, label encoding). Também utilizada para criação e avaliação de modelos.
- Docker: ferramenta de conteinerização utilizada para criar ambientes isolados e consistentes.
  - Permite que todo o pipeline e as ferramentas de desenvolvimento sejam incluídos em um único contêiner.
  - Aplicável nas fases de desenvolvimento, homologação e produção.
  - Promove maior segurança ao evitar interferências entre os ambientes.
- Apache Airflow: permite agendar e monitorar workflows.
- Prometheus: utilizado para monitoramento, não para treinamento de modelos.
- Grafana: ideal para visualizar métricas do pipeline.

> [!CAUTION] OBSERVAÇÃO: 
> - A gestão eficiente de recursos como CPU e memória é consideração crítica em pipelines de machine learning, independentemente da possibilidade de alocação dinâmica.
> - O pipeline deve ser projetado para atender às capacidades computacionais disponíveis.