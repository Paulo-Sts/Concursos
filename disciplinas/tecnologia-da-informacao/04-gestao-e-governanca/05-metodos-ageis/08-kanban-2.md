# Cumulative Flow Diagram (CFD) e Métricas Kanban

## 1. Cumulative Flow Diagram (CFD)
- É uma métrica para visualizar o fluxo de trabalho através dos status das atividades.
- Demonstra a quantidade de atividade que ainda resta a fazer, as atividades em andamento e as atividades concluídas.
- Permite visualizar possíveis problemas que possam ocorrer com o time/projeto, como gargalos ou impedimentos.
- Possibilita visualizar o comportamento real do fluxo de trabalho.

> [!TIP] DICAS:
> - O CFD é uma ferramenta visual que mostra o "retrato" do fluxo de trabalho ao longo do tempo.
> - A principal utilidade do CFD é identificar gargalos e tendências de desempenho da equipe.

### 1.1 Gargalos no Fluxo
- Podem surgir em uma ou mais etapas do fluxo.
- Uma das práticas do Kanban é o constante gerenciamento do fluxo para identificar e resolver gargalos.

> [!CAUTION] OBSERVAÇÃO:
> - A identificação de gargalos é um dos objetivos centrais do CFD e do Kanban como um todo.

## 2. Work In Progress (WIP) e Limites
- WIP (Work In Progress): número de itens de trabalho que estão em andamento, mas não concluídos.
- WIP Limit (Limite de Trabalho em Progresso): restrição arbitrada pelo time/squad para cada etapa do fluxo.
- Capacity (Capacidade): somatório do Limite de Trabalho em Progresso (WIP Limit) de cada etapa.
- Occupation Level (Nível de Ocupação): medida que relaciona o WIP com a capacidade do sistema.

### 2.1 Estados do Sistema com Base no WIP
- Se WIP maior ou igual a Capacidade + 1 ⟶ Sobrecarga.
- Se WIP igual a Capacidade ⟶ sistema sob stress.
- Se WIP igual a capacidade menos uma folga acordada/prevista ⟶ sistema com folga desejada.
- Outras situações: Excesso de folga e Starvation.

### 2.2 Função Principal dos Limites de WIP
- Melhorar a eficiência do fluxo de trabalho ao limitar a quantidade de trabalho em andamento.
- Otimizar o fluxo das atividades e reduzir acúmulo de trabalho.

> [!TIP] DICAS:
> - O WIP Limit não serve para determinar ordem de tarefas, aumentar quantidade de trabalho ou garantir ocupação total da equipe.
> - O principal objetivo é otimizar o fluxo e reduzir acúmulo de trabalho.

### 2.3 Descrição do WIP
- O WIP descreve o total de trabalho que está em progresso no Kanban.
- Pode incluir todos os itens ou apenas aqueles selecionados para implementação.

## 3. Métricas de Tempo e Desempenho

### 3.1 Lead Time (Tempo de Espera)
- Tempo total que uma demanda leva desde o momento em que surge para o cliente (ou entra no sistema - commitment) até o momento em que é efetivamente entregue.
- Reflete a experiência completa do cliente com o processo.
- Começa a medir a partir do momento em que o pedido entra na fila de produção (ponto de compromisso).
- Inclui períodos de espera, filas, priorização, análise e desenvolvimento.
- É essencial para a previsão e otimização do fluxo de valor.
- Utilizado como indicador chave de desempenho no sistema Kanban.

### 3.2 Cycle Time (Tempo de Ciclo)
- Tempo gasto apenas após a equipe assumir o trabalho.
- Desde o início efetivo da execução até a conclusão da demanda.
- Começa a medir quando o trabalho é iniciado.

### 3.3 Throughput (Taxa de Entrega)
- Mede a quantidade de trabalho concluído em um determinado período (semana, sprint, etc).
- Fórmula: WIP / Cycle Time.

### 3.4 Demanda de Falha ou Carga de Falha
- Indica qual porcentagem das entregas é relacionada à correção de defeitos.
- Evidencia retrabalhos e/ou desperdícios.

### 3.5 Action Time (Tempo de Ação) / Touching Time (Tempo de Toque)
- Tempo em que o item está em uma etapa de ação no fluxo.
- Mostra o tempo que o time efetivamente trabalhou no item.

### 3.6 Relação entre Lead Time e Cycle Time
- O lead time é maior que o cycle time, pois inclui o tempo de espera antes do início do trabalho.
- O lead time mede desde o compromisso (commitment) até a entrega (delivery).
- O cycle time mede apenas do início da execução até a conclusão.

> [!CAUTION] OBSERVAÇÃO:
> - Para medir o lead time de uma Sprint, deve-se selecionar no quadro Kanban uma Sprint da situação "Fazendo" (ou seja, em andamento) e considerar todo o tempo desde o compromisso até a entrega final.

## 4. Práticas e Conceitos do Kanban
- Visualização do fluxo de trabalho.
- Limitação do Trabalho em Progresso (WIP) para identificar gargalos e otimizar a vazão de entregas.
- Constante gerenciamento do fluxo para evitar e resolver gargalos.
- Uso de indicadores quantitativos como lead time, cycle time e throughput.
- A análise de métricas como throughput visa identificar gargalos.
- Ações como redistribuição de recursos são condizentes com o espírito de melhoria contínua do Kanban.

> [!TIP] DICAS:
> - O Kanban não se baseia em papéis fixos como product owner e scrum master.
> - O foco do Kanban é no fluxo coletivo, não na produtividade individual.

## 5. Kanban e Scrum
- O método Kanban pode ser utilizado em substituição à metodologia Scrum.
- Ambos podem ser combinados para o alcance de resultados mais eficazes.

> [!CAUTION] OBSERVAÇÃO:
> - Embora sejam metodologias distintas, Kanban e Scrum são complementares e podem ser usados em conjunto.