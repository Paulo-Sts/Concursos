# Tipos de Análise de Dados

## 1. Análise Descritiva
- Representa o estágio inicial do processo de ciência de dados voltado para descrever e resumir dados históricos.
- Objetivo principal ⟶ entender o que ocorreu no passado para fornecer uma visão clara dos fatos.
- Relaciona-se ao aprendizado não supervisionado de inteligência artificial por lidar com bases de dados desconhecidas.
- Técnicas principais:
  - Estatística descritiva;
  - Visualização de dados;
  - Agrupamento (clusterização) para reunir elementos semelhantes;
  - Regras de associação para identificar valores co-ocorrentes como em cestas de compras.

| TÉCNICA | FUNÇÃO |
|---|---|
| Agrupamento | Unir dados semelhantes sem conhecimento prévio |
| Regras de associação | Encontrar co-ocorrência em bases de dados |
| Visualização | Facilitar o entendimento dos dados apresentados |

> [!TIP] DICAS: 
> - A análise descritiva foca em relatar acontecimentos passados.

## 2. Análise Preditiva
- Utiliza o histórico de dados para prever tendências, comportamentos e resultados futuros.
- Estabelece uma relação direta entre os dados conhecidos e uma classe ou rótulo específico.
- Associa-se ao aprendizado supervisionado pois a máquina utiliza experiências anteriores para situações futuras.
- Técnicas principais:
  - Séries temporais para análise de histórico de variações;
  - Modelos de aprendizado de máquina automatizados para maior precisão.
- Exemplo: previsão do tempo alimentada por séries históricas de temperatura e meteorologia.

> [!CAUTION] OBSERVAÇÃO: 
> - O aprendizado supervisionado exige obrigatoriamente dados de entrada e de classe para o treinamento.

## 3. Análise Diagnóstica
- Possui um nível de complexidade superior às análises descritiva e preditiva.
- Foca em identificar por que algo aconteceu através da correlação entre causa e consequência.
- É fundamental no contexto empresarial para explicar variações como a queda na venda de produtos.
- Técnicas principais:
  - Análise de correlação;
  - Análise de regressão;
  - Drill-down analysis.

| ANÁLISE | FOCO DA PERGUNTA |
|---|---|
| Descritiva | O que aconteceu? |
| Diagnóstica | Por que aconteceu? |

> [!CAUTION] OBSERVAÇÃO: 
> - Diferente da prescritiva, a análise diagnóstica foca na identificação de causas e não na recomendação de ações.

## 4. Análise Prescritiva
- Define-se pela prescrição de soluções para problemas e sugestão de estratégias para melhores resultados.
- Considera múltiplos cenários e utiliza simulações para determinar a melhor abordagem a ser adotada.
- Funciona como a recomendação de ações específicas para melhorar a produtividade e eficiência.
- Técnicas principais:
  - Otimização;
  - Simulação;
  - Algoritmos de decisão.

### 4.1 Analogia do Processo de Análise
- Análise descritiva ⟶ médico realiza entrevista e solicita exames do paciente.
- Análise preditiva ⟶ médico prevê qual é o problema com base nos dados.
- Análise diagnóstica ⟶ médico encontra a causa específica para o problema.
- Análise prescritiva ⟶ médico fornece a solução ou tratamento ao paciente.

> [!TIP] DICAS: 
> - Análise prescritiva ⟶ Recomenda a solução ideal para o usuário.