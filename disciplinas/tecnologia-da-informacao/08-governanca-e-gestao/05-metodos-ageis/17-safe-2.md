# Resumo de SAFe: Papéis, Eventos, Artefatos e DevOps

## 1. Responsabilidades e Papéis
- SAFe distribui responsabilidades em níveis: Equipe Ágil, ART, Solution Train e Portfólio.
- Equipe Ágil: Product Owner, Scrum Master / Team Coach.
- Agile Release Train (ART) / Trem de Liberação Ágil: Product Management, Release Train Engineer (RTE), System Architect, Business Owners e Equipes Ágeis.
- Solution Train: Solution Management, Solution Train Engineer e Solution Architect, quando aplicável, incluindo fornecedores.
- Portfólio: Lean Portfolio Management, Epic Owners e Enterprise Architect.

### 1.1 Papéis na Equipe Ágil
- Equipes Ágeis: grupo multifuncional de dez ou menos indivíduos que pode definir, construir, testar e implantar um incremento de valor em uma caixa de tempo curto.
- Cada ART é composto por 5 a 12 equipes Ágeis e inclui os papéis e a infraestrutura necessários para entregar soluções de negócios totalmente funcionais e testadas.
- Product Owner (PO): autoridade de conteúdo do backlog da equipe; é responsável por definir as histórias e priorizar o backlog.
- Scrum Master / Team Coach: líder servidor e coach de equipe Ágil; ajuda a equipe a remover impedimentos, facilita eventos em equipe e promove um ambiente para equipes de alto desempenho.

### 1.2 Papéis na ART
- Release Train Engineer (RTE): principal facilitador e servant leader do ART; ajuda a coordenar o trem, facilitar eventos como PI Planning e Inspect & Adapt, tratar impedimentos sistêmicos e melhorar o fluxo de valor.
- Didaticamente, o RTE é o papel mais próximo de um Scrum Master na escala do ART, embora não seja simplesmente um Scrum Master ampliado.
- Product Management: responsável pela direção do produto no nível do ART; trabalha com visão, roadmap, Features e ART Backlog, priorizando o que deve ser desenvolvido conforme necessidades de clientes e objetivos de negócio.
- Comparação didática: Product Owner ⟶ Team; Product Management ⟶ ART.
- System Architect: responsável pela direção arquitetural e técnica do sistema no nível do ART; ajuda a definir arquitetura, requisitos não funcionais, Architectural Runway e decisões técnicas que afetam várias equipes.
- Business Owners: stakeholders com responsabilidade significativa sobre resultados de negócio, governança e valor entregue pelo ART; participam de eventos importantes, especialmente do PI Planning, e ajudam a avaliar os PI Objectives.
- Product Owner (PO): atua no nível da Agile Team; é responsável pelo conteúdo e priorização do Team Backlog, trabalhando com Stories e alinhando o trabalho da equipe com Features e objetivos mais amplos definidos no ART.
- Scrum Master / Team Coach: atua na escala da equipe; facilita eventos, ajuda a remover impedimentos e promove melhoria contínua e efetividade da Agile Team.
- Agile Teams: equipes multifuncionais que efetivamente definem, constroem, testam e entregam valor dentro do ART; várias Agile Teams formam o Agile Release Train.

> [!TIP] DICAS:
> - Para prova, associe: RTE ⟶ facilitar eventos do ART e remover impedimentos sistêmicos; Product Management ⟶ priorizar ART Backlog e Features; System Architect ⟶ orientação técnica e arquitetural.

> [!CAUTION] OBSERVAÇÃO:
> - Não confunda Product Owner com Product Management. O PO prioriza o Team Backlog; Product Management prioriza o ART Backlog e as Features.

## 2. Eventos por Equipes
- As equipes do SAFe gerenciam seu processo com uma série de eventos regulares.
- Planejamento de Iterações: evento em equipe no qual uma equipe Ágil determina os objetivos da iteração e quanto do backlog da equipe pode se comprometer durante uma próxima iteração.
- A capacidade da equipe determina o número de histórias e facilitadores selecionados.
- Refinamento do backlog: evento realizado uma ou duas vezes durante a iteração para refinar, revisar e estimar histórias futuras e facilitadores do backlog da equipe.
- Sincronização em Equipe: reunião curta, geralmente 15 minutos ou menos, normalmente realizada diariamente, para inspecionar o progresso em direção à meta da iteração, comunicar e ajustar o trabalho planejado futuro.
- Revisão de Iteração: evento baseado em cadência ao final de cada iteração, no qual a equipe revisa os resultados do incremento anterior e ajusta o backlog da equipe com base no feedback.
- Iteration Retrospective: evento realizado ao final da iteração para que a equipe Ágil revise suas práticas e identifique formas de melhorar.
- A retrospectiva aplica informações qualitativas e quantitativas apresentadas durante a revisão de iteração.

## 3. Eventos da Agile Release Train (ART)
- Planning Interval (PI) / Intervalo de Planejamento:
  - Timebox de desenvolvimento do ART, tipicamente de 8 a 12 semanas;
  - Tem início com o PI Planning, com duração de 2 dias a cada PI;
  - Um PI típico possui 4 ou 5 Iterações.
- A Iteração está para Agile Team assim como PI está para ART.
- Nas versões anteriores, o PI era chamado de Program Increment.

### 3.1 PI Planning
- Evento presencial baseado em cadência que atua como o coração do Agile Release Train (ART) ao alinhar todos os times do ART em torno de uma visão e missão compartilhadas.
- Duração: 2 dias a cada 8-12 semanas.
- Product Management assume as prioridades da Feature.
- Benefícios:
  - Estabelecer comunicação pessoal entre todos os membros do time e stakeholders;
  - Alinhar as metas de desenvolvimento e negócios com o contexto do negócio, visão e objetivos do PI do time/ART;
  - Identificar dependências e promover a colaboração entre times e ARTs;
  - Oferecer a oportunidade para a proporção certa de arquitetura e orientação sobre Lean UX;
  - Equiparar demanda e capacidade, eliminando o excesso de trabalho em processo (WIP);
  - Tomada rápida de decisão.

> [!TIP] DICAS:
> - Guarde: PI Planning = coração do ART; 2 dias; a cada 8-12 semanas; alinhamento, dependências e capacidade x demanda.

### 3.2 ART Sync
- Combina o Coach Sync e o PO Sync em um único evento para um ART.
- Coach Sync: ajuda a coordenar as dependências dos ARTs e fornece visibilidade sobre o progresso e impedimentos.
- PO Sync: fornece visibilidade sobre o quanto o ART está progredindo para atingir os objetivos do PI do ART, discute problemas ou oportunidades com desenvolvimento de recursos e avalia quaisquer ajustes de escopo.
- Analogia com Scrum: ART Sync está para o ART assim como a Daily Scrum está para o Scrum Team.
- Diferença importante: o ART Sync é mais amplo.

### 3.3 System Demo
- Oferece uma visão integrada dos novos recursos da iteração mais recente entregue por todas as equipes do ART.
- Cada demonstração inclui stakeholders do ART com uma medida objetiva do progresso durante um PI.
- Demonstra a solução integrada produzida pelo ART.

### 3.4 Inspect & Adapt
- Evento significativo no qual o estado atual da solução é demonstrado e avaliado.
- Acontece ao final do PI e tem como objetivo inspecionar resultados, analisar problemas e promover melhoria.
- As equipes refletem e identificam itens de melhoria atrasados por meio de um workshop estruturado de resolução de problemas.

## 4. Artefatos no ART
- O PI Planning gera e utiliza artefatos para guiar a execução do trabalho.

### 4.1 Team PI Objectives
- Resumo dos objetivos técnicos e de negócio que uma Agile Team pretende alcançar no PI.
- São elaborados durante o PI Planning e podem ser committed ou uncommitted.

### 4.2 ART Planning Board
- Quadro visual que mostra datas previstas de entrega das Features, dependências entre equipes e milestones relevantes durante o PI.
- É uma das duas principais saídas do PI Planning.
- Contém: Features + Iterations + dependências + milestones.

### 4.3 ART PI Risks / ROAM
- Riscos identificados que podem afetar a capacidade do ART de atingir seus PI Objectives.
- Durante o PI Planning, são normalmente tratados por meio da classificação ROAM:
  - Resolved (resolvido);
  - Owned (assumido);
  - Accepted (aceito);
  - Mitigated (mitigado).

### 4.4 ART PI Objectives
- Consolidação, no nível do ART, dos objetivos técnicos e de negócio que o Agile Release Train pretende alcançar no PI.
- Permitem comunicar propósito, acompanhar resultados e posteriormente avaliar previsibilidade.

> [!TIP] DICAS:
> - Program Board / ART Planning Board é o artefato visual para dependências, datas e milestones. Em prova, ele aparece ligado a interdependências entre times no PI Planning.

## 5. SAFe e DevOps
- SAFe e DevOps são abordagens complementares que visam melhorar a entrega de software.
- O SAFe aborda principalmente a coordenação e a escala das práticas ágeis.
- O DevOps se concentra na automação, colaboração e integração entre as equipes de desenvolvimento e operações.
- No SAFe, o DevOps é uma prática-chave que promove a integração contínua, a entrega contínua e a automação de processos para acelerar a entrega de valor ao cliente.
- O SAFe enfatiza a importância de implementar práticas de DevOps em todos os níveis de escala, permitindo uma colaboração mais estreita entre as equipes de desenvolvimento, operações e qualidade.