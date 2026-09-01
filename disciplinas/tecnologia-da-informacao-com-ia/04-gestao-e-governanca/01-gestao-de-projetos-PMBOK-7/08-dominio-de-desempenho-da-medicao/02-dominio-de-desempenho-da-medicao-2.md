# Gestão de Projetos Pmbok 7ª Edição Domínio de Desempenho da Medição 2

## 1. Técnica de Gerenciamento do Valor Agregado (Gva)
- O Gerenciamento do Valor Agregado (GVA) ou Análise do Valor Agregado (AVA) é a técnica utilizada para acompanhar o desempenho do projeto em relação à sua linha de base.
- A linha de base da medição de desempenho resulta da integração das linhas de base de custos, cronograma e escopo.
- Esta técnica permite medir de forma objetiva o progresso do projeto, indicando variações de custo e de tempo.
- O uso do GVA serve para determinar a necessidade de mudanças no projeto com base em indicadores confiáveis.

### 1.1 Dimensões Chave do Gva
- O GVA monitora dimensões essenciais para cada pacote de trabalho e conta de controle:
  - Valor Planejado (VP) ⟶ Orçamento do trabalho que foi programado ou agendado para terminar em determinado momento;
  - Valor Agregado (VA) ⟶ Orçamento associado ao trabalho autorizado que foi efetivamente concluído;
  - Custo Real (CR) ⟶ Custo de fato incorrido no trabalho realizado.

> [!TIP] DICAS: 
> - Para acertar questões de cálculo, lembre-se que o Valor Agregado (VA) deve ser sempre considerado primeiro nas fórmulas.
> - O Valor Agregado representa a quantificação do progresso em termos financeiros (valor orçado do trabalho realizado).

> [!CAUTION] OBSERVAÇÃO: 
> - O Valor Agregado não pode ser superior ao Valor Planejado para o mesmo trabalho quando este último é usado como referência na linha de base.
> - A avaliação por meio do GVA só é possível quando há desempenho a ser analisado; no início do projeto, sem trabalho realizado, não há VA para medir.

## 2. Indicadores e Medidas de Desempenho
- As métricas de desempenho permitem identificar se o projeto está adiantado, atrasado ou com custos fora do previsto.

### 2.1 Índices de Eficiência
- Índice de Desempenho de Prazos (IDP) ⟶ Medida de eficiência do cronograma calculada pela razão entre o valor agregado e o valor planejado (IDP = VA / VP);
- Índice de Desempenho de Custos (IDC) ⟶ Medida de eficiência dos fundos calculada pela razão entre o valor agregado e o custo real (IDC = VA / CR).

### 2.2 Análise de Variações
- Variação de Prazos (VPR) ⟶ Diferença entre o valor agregado e o valor planejado;
- Variação de Custos (VC) ⟶ Diferença entre o valor agregado e o custo real.

### Tabela de Interpretação Gva
| INDICADOR | DESEMPENHO NEGATIVO | DESEMPENHO POSITIVO |
|---|---|---|
| Variância (vpr ou vc) | Menor que zero (atraso/sobrecusto) | Maior que zero (adiantado/economia) |
| Índice (idp ou idc) | Menor que um (ineficiente) | Maior que um (eficiente) |

## 3. Apresentação Visuais de Informações
- A comunicação do desempenho deve ser feita de forma clara para as partes interessadas.

### 3.1 Painéis de Controle e Irradiadores
- Painel de Controle (Dashboard) ⟶ Conjunto de tabelas e gráficos que demonstram o progresso e medidas importantes do projeto em relação às métricas;
- Irradiadores de Informações (Grandes Gráficos Visíveis - GGV) ⟶ Ferramentas visuais expostas para facilitar o acesso rápido aos dados de desempenho;
- Quadro de Tarefas (Kanban) ⟶ Controle visual que utiliza diagramas de fluxo cumulativo para gerenciar o trabalho.

### 3.2 Gráficos de Burn
- São utilizados para monitorar a produtividade da equipe e o progresso das entregas:
  - Burnup ⟶ Gráfico que mostra o volume total de trabalho que já foi concluído;
  - Burndown ⟶ Gráfico que mostra o volume de trabalho restante em função do tempo compromissado.

> [!TIP] DICAS: 
> - No Scrum, o gráfico de burndown é a ferramenta clássica para visualizar a expectativa de produtividade ideal versus a produtividade real.

## 4. Armadilhas e Comportamento na Medição
- O ato de medir pode gerar efeitos colaterais que impactam a qualidade do projeto.
- Efeito Hawthorne ⟶ O próprio ato de medir algo influencia o comportamento das pessoas medidas;
- Métrica de vaidade (Vanity metric) ⟶ Dados que são mostrados mas não fornecem informações úteis para a tomada de decisão;
- Desmoralização ⟶ Ocorre quando metas e medidas inalcançáveis são definidas, reduzindo o moral da equipe;
- Viés de confirmação ⟶ Falsa interpretação de dados para que eles concordem com um ponto de vista pessoal prévio;
- Confusão entre correlação e causalidade ⟶ Atribuição errônea de causa a eventos que apenas ocorrem simultaneamente.

> [!CAUTION] OBSERVAÇÃO: 
> - O efeito Hawthorne pode encorajar a equipe a focar apenas no volume de entregas (quantidade) em vez de focar na satisfação do cliente (qualidade), caso a medição seja focada apenas em produtividade bruta.

## 5. Artefatos e Métodos Aplicados
- O domínio da medição utiliza diversos artefatos de dados e informações.

### 5.1 Artefatos de Informações Visuais
- Diagrama de tempo de ciclo;
- Diagrama de fluxo cumulativo;
- Histograma;
- Matriz de priorização;
- Matriz de rastreabilidade de requisitos;
- Diagrama de dispersão;
- Mapa da cadeia de valor.

### 5.2 Outros Métodos e Artefatos
- Pontuação Líquida de Promotores (NPS) ⟶ Utilizado para medir a satisfação e lealdade do cliente;
- Grupos de Processos ⟶ Os processos de monitoramento e controle ocorrem continuamente ao longo de todos os domínios de desempenho;
- Monitoramento do desempenho e da conformidade ⟶ Propósito de prover transparência e dirigir o atingimento dos objetivos organizacionais.