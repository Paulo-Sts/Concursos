# Kanban e Lean Management

## 1. Kanban: Definição e Origem
- Kanban é um método de melhoria de processos utilizado por equipes ágeis.
- As equipes que adotam o Kanban iniciam compreendendo a maneira como atualmente constroem software e realizam melhorias ao longo do tempo.
- O método requer a mentalidade de pensamento lean.
- O foco principal está na eliminação de desperdícios do processo produtivo.

## 2. Lean Management
- Abordagem de gestão que aplica os princípios do Lean Manufacturing a toda a organização, não se restringindo apenas à produção.

### 2.1 Princípios Fundamentais
- Foco no Cliente;
- Eliminação dos Desperdícios;
- Melhoria Contínua;
- Empoderamento da equipe, com autonomia e autogerenciamento;
- Fluxo de Valor.

### 2.2 Práticas e Ferramentas Comuns do Lean Manufacturing
| FERRAMENTA | DESCRIÇÃO |
|---|---|
| 5S (Seiri, Seiton, Seiso, Seiketsu, Shitsuke) | Metodologia para organizar e manter o ambiente de trabalho limpo, organizado e eficiente |
| Kaizen (Melhoria Contínua) | Filosofia que encoraja a contribuição contínua de melhorias por parte de todos os colaboradores |
| Jidoka (Autonomação) | Capacidade de um processo parar automaticamente ao detectar uma condição anormal, garantindo qualidade |
| Just-in-Time (JIT) | Sistema que visa a produção e entrega de produtos no exato momento em que são necessários, reduzindo estoques e desperdícios |
| Kanban | Sistema visual de gestão de fluxo de trabalho que sinaliza a necessidade de reposição de estoque ou de iniciar novas tarefas |

> [!TIP] DICAS:
> - O 5S é uma ferramenta de organização do ambiente de trabalho, frequentemente cobrada em provas como prática essencial do Lean Manufacturing.
> - Kaizen e Jidoka são conceitos centrais para entender a melhoria contínua e o controle de qualidade.

## 3. Just in Time (JIT)
- Filosofia de gerenciamento de produção que visa reduzir o desperdício e aumentar a eficiência.
- Propõe produzir apenas o necessário, no momento certo, eliminando estoques excessivos e desperdícios ao longo do processo produtivo.
- Kanban é uma técnica que ajuda a implementar o JIT por meio de um sistema visual de controle de produção.
- O Kanban funciona como um subsistema do JIT, permitindo que as equipes visualizem o fluxo de trabalho e gerenciem a reposição de estoque de forma eficiente.
- Ambos os métodos são interdependentes: o Kanban facilita a execução do JIT, promovendo uma produção mais ágil e responsiva.

> [!CAUTION] OBSERVAÇÃO:
> - O Kanban é um componente do Just in Time, e não o contrário. O JIT é um conceito mais amplo que abrange toda a cadeia de fornecimento da empresa.
> - Em provas, é comum aparecer a afirmação incorreta de que o JIT é parte do Kanban ou que um substitui o outro. A relação correta é de complementaridade, com o Kanban sendo uma ferramenta visual para viabilizar o JIT.

### 3.1 Esclarecimento sobre a Relação JIT e Kanban
- O Kanban é um sistema com foco na produção, utilizado para transmitir informação sobre apanhar ou receber a ordem de produção.
- O Kanban pode ser um dos componentes do conceito Just in Time, que é mais amplo e abrange toda a cadeia de fornecimento da empresa.

> [!TIP] DICAS:
> - Em questões de concurso, fique atento: o Kanban NÃO é mais moderno ou eficiente que o JIT; ele é uma ferramenta que auxilia na implementação do JIT.
> - O JIT não se resume à agilidade, mas sim à eliminação de desperdícios e à produção no momento certo.

## 4. Kanban: Princípios e Práticas

### 4.1 Princípios de Gestão de Mudança
- Comece com o que você faz agora;
- Busque mudanças incrementais e evolutivas;
- Respeite o processo atual, papéis e responsabilidades.

### 4.2 Princípios de Gestão de Serviço
- Foque nas necessidades e expectativas do cliente;
- Gerencie o trabalho, e não as pessoas;
- Melhore colaborativamente, evolua experimentalmente.

### 4.3 Práticas Centrais do Kanban
- Visualizar o fluxo de trabalho;
- Limitar o WIP (trabalho em andamento);
- Gerenciar Fluxo;
- Tornar as políticas de processo explícitas;
- Implementar Ciclos de Feedback;
- Melhorar de forma colaborativa, evoluir experimentalmente (usando modelos/método científico).

> [!CAUTION] OBSERVAÇÃO:
> - O Kanban não é uma metodologia prescritiva; ele parte do processo existente e promove melhorias incrementais.
> - O limite de WIP é uma das práticas mais importantes para evitar gargalos e sobrecarga da equipe.

## 5. Componentes do Quadro Kanban
| COMPONENTE | DESCRIÇÃO |
|---|---|
| Cartões Kanban | Representação visual das entregas. Contêm informações sobre a entrega e seu status (descrição da tarefa, prazo, responsável, etc.) |
| Colunas Kanban | Representam um estágio do fluxo de trabalho |
| Limites WIP | Restringem a quantidade máxima de cartões em cada estágio do fluxo |
| Kanban Swimlanes (Raias) | Faixas horizontais que podem ser usadas para classificação (tipo de atividades, equipes, classes de serviço, etc.) |
| Ponto de Compromisso | Ponto no processo de trabalho em que um item de trabalho está pronto para ser inserido no fluxo |
| Ponto de Entrega | Ponto no fluxo de trabalho em que os itens de trabalho são considerados concluídos |

> [!TIP] DICAS:
> - Os limites WIP são fundamentais para o controle do fluxo e evitam acúmulo de tarefas em uma etapa.
> - As swimlanes são opcionais e servem para organizar diferentes tipos de trabalho ou prioridades.
> - O ponto de compromisso e o ponto de entrega definem os marcos de início e conclusão no fluxo.

## 6. Exemplo Prático de Quadro Kanban
| BACKLOG | ESPECIFICAÇÃO | IMPLEMENTAÇÃO | REVISÃO DE CÓDIGO |
|---|---|---|---|
| H3 | Em especificação | Em implementação T4, T5, T6, T7 | Em revisão T3, T2 |

### 6.1 Análise do Quadro
- A história H3 está no backlog e poderia ser movida para a fase de especificação, caso haja disponibilidade.
- A implementação já contém quatro tarefas (T4, T5, T6, T7).
- A revisão de código contém duas tarefas (T3, T2), indicando que o limite dessa etapa pode ter sido atingido.

> [!CAUTION] OBSERVAÇÃO:
> - Em um quadro Kanban, mover um item para a próxima fase só é permitido se o limite de WIP da fase destino não for ultrapassado.
> - A presença de tarefas em revisão não impede necessariamente a inclusão de novas tarefas, desde que o limite WIP permita.
> - A priorização pode ser indicada pela posição dos cartões dentro das colunas (ex.: itens acima podem ter maior prioridade).