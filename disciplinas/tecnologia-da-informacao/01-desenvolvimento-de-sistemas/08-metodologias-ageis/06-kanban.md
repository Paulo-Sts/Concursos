# Engenharia de Software Kanban

## 1. Conceitos de Kanban e Toyotismo
- O termo kanban possui origem japonesa e significa cartão ou sinalização.
- Consiste na utilização de cartões ou sinalizações para indicar o andamento dos fluxos de produção.
- Os cartões indicam o status da tarefa através de categorias como para executar, em andamento ou finalizado.
- O modelo possui características semelhantes ao sistema toyotista de produção, focando na fabricação de acordo com a demanda.

## 2. Just in Time e Fluxo de Trabalho
- O sistema permite um controle detalhado da produção com informações sobre quando, quanto e o que produzir.
- O conceito de just in time significa produzir bens e serviços exatamente no momento em que são necessários.
- O produto ou matéria-prima só chega ao local de utilização no momento em que é solicitado.
- Caracteriza-se como um sistema puxado, onde o item só é fabricado quando necessário na cadeia de produção.
- O objetivo principal deste modelo é a eliminação total de desperdícios.

> [!CAUTION] OBSERVAÇÃO: 
> - O impacto deste modelo foi evidenciado durante a pandemia de covid-19, onde a paralisação da produção resultou em escassez de automóveis.

## 3. Filosofia Lean e Qualidade do Software
- O pensamento lean está ligado à eliminação de desperdício em qualquer etapa do processo.
- No desenvolvimento de software, desperdícios incluem:
  - Funcionalidades que não agregam valor;
  - Perda de tempo em atividades sem resultado;
  - Construção de funcionalidades que não serão utilizadas;
  - Retrabalho gerado por baixa qualidade.
- A qualidade é um fator crítico, impedindo que o software seja finalizado sem passar por testes, análise estática e avaliação do cliente.

> [!TIP] DICAS: 
> - Não confunda retrabalho com refaturação; a refaturação é uma prática positiva feita para manter o código com alta qualidade, enquanto o retrabalho é considerado desperdício.

## 4. Comparação entre Sistemas Pull e Push
- O sistema original da toyota adotou o pull system ⟶ o trabalho é puxado pela demanda real.
- Linhas de produção tradicionais, como a de ford, utilizam o push system ⟶ o trabalho é empurrado com base em estimativas, independente dos pedidos reais.

| TIPO DE SISTEMA | LÓGICA DE TRABALHO | IMPACTOS E DESPERDÍCIOS |
|---|---|---|
| Puxado | Puxado pela demanda | Eliminação de excessos e desperdícios |
| Empurrado | Empurrado por estimativas | Criação de estoque e ociosidade de trabalhadores |

## 5. Métricas de Progresso e Tempo
- WiP (Work in Progress) ⟶ representa o trabalho em andamento ou progresso em determinado ponto do processo.
- É fundamental limitar o WiP para garantir a manutenção do fluxo e reduzir o tempo total de execução.
- Lead time ⟶ intervalo de tempo em que uma tarefa fica em execução, desde o backlog até ser considerada feita (done).
- Cycle time ⟶ representa os elementos que estão efetivamente em progresso dentro do fluxo.

## 6. Kanban no Contexto das Metodologias Ágeis
- O kanban orienta o trabalho a eventos ao invés de limites estritos de tempo.
- Diferencia-se do scrum, que divide o cronograma em iterações de tempo fixo (time-box) chamadas de sprints.
- A implementação pressupõe a definição de um fluxo de trabalho pela equipe, que pode ser revisto e alterado conforme a evolução do projeto.

> [!TIP] DICAS: 
> - Em questões de prova, associe o kanban ao controle de fluxo por cartões e ao sistema puxado, enquanto o scrum é associado a ciclos de tempo fixos (sprints).