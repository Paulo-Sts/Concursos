# Técnicas de Priorização e Estimativas

## 1. Planning Poker
- Técnica de estimativa consensual usada por equipes ágeis para estimar esforço ou complexidade de tarefas.
- Processo:
  - Apresentação da Tarefa: um item de backlog é apresentado e a equipe discute requisitos e detalhes;
  - Estimativa Individual: cada membro seleciona uma carta de um baralho de Planning Poker que representa sua estimativa de esforço, frequentemente usando a sequência de Fibonacci;
  - Revelação e Discussão: todos revelam suas cartas ao mesmo tempo; se as estimativas variarem significativamente, discute-se as razões para as discrepâncias;
  - Repetição: o processo é repetido até que a equipe chegue a um consenso sobre a estimativa.
- Cartas típicas: 1/2; 1; 2; 3; 5; 8; 13; 20; 40; 100; ?; ∞; café.
- A técnica é tipicamente utilizada no Scrum para estimar o esforço necessário para terminar atividades.

> [!TIP] DICAS:
> - A sequência mais cobrada em prova é 0, 1, 2, 3, 5, 8, 13, 20, 40 e 100, embora o material também apresente 1/2 e a carta de café.
> - Planning Poker não é priorização; é estimativa.

## 2. Story Points
- Unidade de medida relativa usada para quantificar esforço, complexidade e incerteza envolvidos na realização de cada história de usuário.
- O Planning Poker é o método pelo qual a equipe chega a um consenso sobre a quantidade de story points que uma história deve receber.
- Story Points é a unidade relativa de tempo criada pelo Time de Desenvolvimento e a mais utilizada por equipes ágeis.
- A análise de ponto de função baseia-se nas funcionalidades que um sistema deve realizar, enquanto Story Points baseia-se em estimativa relativa, comparando complexidade e esforço de uma tarefa com outras já realizadas.

> [!CAUTION] OBSERVAÇÃO:
> - Não confunda Story Points com tempo real; é uma medida relativa.

## 3. T-Shirt Sizing
- Técnica que usa tamanhos de camisetas (XS, S, M, L, XL) para categorizar tarefas por nível de esforço ou complexidade.
- Ajuda a equipe a fazer uma estimativa relativa rápida.
- Processo:
  - Apresentação dos Itens: cada item a ser estimado é apresentado e discutido pela equipe;
  - Discussão e Comparação: a equipe compara os itens considerando complexidade, esforço necessário e incertezas;
  - Votação: cada membro vota no tamanho de camiseta que acredita ser mais representativo para cada item;
  - Consenso: se as estimativas variarem significativamente, há discussão adicional até que a equipe chegue a um consenso.
- Vantagens:
  - Facilita a compreensão e a discussão sobre complexidade relativa entre os membros da equipe;
  - Encoraja a colaboração e o consenso;
  - É rápido e fácil de aplicar, especialmente em estágios iniciais do planejamento.

## 4. Técnica MoSCoW
- Método de priorização que ajuda equipes a classificar requisitos ou tarefas em quatro categorias, com base em sua importância para a entrega do projeto.
- Categorias:
  - Must have (Deve ter): requisitos críticos para o sucesso do projeto; sem eles, o projeto é considerado um fracasso;
  - Should have (Deveria ter): requisitos importantes que não são críticos; sua ausência diminui a entrega, mas o projeto ainda é considerado um sucesso;
  - Could have (Poderia ter): requisitos desejáveis que têm impacto positivo, mas não são essenciais; podem ser incluídos se houver tempo e recursos;
  - Won’t have this time (Não terá desta vez): requisitos acordados para serem excluídos da entrega atual, mas que podem ser considerados no futuro.
- No Scrum, é uma técnica para ajudar a priorizar histórias de usuário.

> [!TIP] DICAS:
> - Memorize a ordem de prioridade: Must > Should > Could > Won’t.
> - Must have é o único que, se ausente, leva ao fracasso do projeto.

## 5. Dot Voting
- Técnica de priorização em que os membros da equipe usam uma quantidade limitada de pontos ou dots para votar nas funcionalidades ou tarefas que consideram mais importantes.
- Processo:
  - Preparação: as opções a serem votadas são apresentadas claramente para a equipe;
  - Votação: cada membro cola seus pontos nas opções que prefere; a distribuição reflete preferência pessoal e importância percebida;
  - Contagem e Discussão: após a votação, os pontos são contados; as opções com mais pontos são consideradas prioritárias;
  - Decisão: a equipe discute o resultado e toma decisões com base nas opções mais votadas.
- Vantagens:
  - É democrático e inclusivo, permitindo que todos expressem sua opinião;
  - É rápido e eficiente para identificar as preferências da equipe;
  - É flexível, podendo ser adaptado para diferentes contextos e quantidades de opções.

## 6. Scorecard
- Ferramenta que utiliza pontuação ponderada para avaliar e priorizar iniciativas, projetos ou tarefas com base em múltiplos critérios.
- Etapas:
  - Definição dos critérios;
  - Atribuição de pesos;
  - Avaliação dos itens;
  - Cálculo da pontuação total;
  - Ordenação.
- O primeiro passo é definir os critérios de priorização.
- O critério Impacto no Negócio representa o valor que uma tarefa traz para a organização.
- Vantagem: tomada de decisão objetiva e baseada em dados.

| TAREFA | IMPACTO (40%) | URGÊNCIA (30%) | CUSTO (20%) | RISCO (10%) | PONTUAÇÃO TOTAL |
|---|---|---|---|---|---|
| A | 9 (3.6) | 7 (2.1) | 5 (1.0) | 4 (0.4) | 7.1 |
| B | 6 (2.4) | 8 (2.4) | 3 (0.6) | 7 (0.7) | 6.1 |
| C | 5 (2.0) | 6 (1.8) | 8 (1.6) | 3 (0.3) | 5.7 |

## 7. BUC
- BUC significa Business Benefit, User Benefit, Cost.
- Metodologia de priorização que considera três perspectivas: Business (Negócio), User (Usuário) e Cost (Custo).
- Cada perspectiva é avaliada para determinar o valor e a urgência das iniciativas.

| ITEM | IMPACTO NO NEGÓCIO (B) | IMPACTO NO USUÁRIO (U) | CUSTO (C) | PONTUAÇÃO TOTAL |
|---|---|---|---|---|
| A | 8 | 7 | 9 | 24 |
| B | 5 | 9 | 6 | 20 |
| C | 7 | 8 | 8 | 23 |

> [!CAUTION] OBSERVAÇÃO:
> - No método BUC, o custo é uma das três perspectivas analisadas; portanto, a priorização não ocorre independentemente do custo da feature ou story.
> - O BUC facilita a tomada de decisões de forma balanceada entre diferentes perspectivas.

## 8. Gráficos de Burn
- Oferecem visibilidade sobre o progresso e facilitam ajustes no planejamento e execução.

### 8.1 Gráfico de Burndown
- Ferramenta visual para rastrear a quantidade de trabalho que resta versus o tempo disponível.
- Mostra uma linha ideal de como o trabalho deveria ser completado para atingir o objetivo no tempo previsto, comparando com a linha real de progresso.
- Ajuda a identificar se a equipe está atrasada ou adiantada em relação ao planejado.
- Se a linha real estiver acima da linha ideal, o time está atrasado na sprint.
- É uma representação visual do trabalho a ser realizado em relação ao tempo necessário para a sua conclusão.
- Mostra quanto trabalho ainda falta ao longo do tempo.
- Foco: trabalho restante.
- Ideal para acompanhar a execução da sprint.

### 8.2 Gráfico de Burnup
- É útil para visualizar o quanto do projeto foi concluído e quanto ainda resta, além de mudanças no escopo.
- Destaca o trabalho total realizado contra o escopo total do projeto.
- Mostra o progresso realizado e também a evolução do escopo.
- Foco: trabalho concluído e escopo.
- Ajuda a visualizar mudanças no escopo.
- Quando a linha de concluído encontra a de escopo, o trabalho foi finalizado.

> [!TIP] DICAS:
> - Burndown: trabalho restante; linha real acima da ideal ⟶ atraso.
> - Burnup: trabalho concluído e escopo total; útil para visualizar mudanças de escopo.
> - Estimativas: Planning Poker e T-Shirt Sizing.
> - Priorização: MoSCoW, Dot Voting, Scorecard e BUC.