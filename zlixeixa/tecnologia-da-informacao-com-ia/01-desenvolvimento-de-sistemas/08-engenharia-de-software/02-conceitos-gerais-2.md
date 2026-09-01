# Engenharia de Software - Conceitos Gerais 2

## 1. Fluxo de Processo
- O fluxo de processo descreve a organização das atividades metodológicas, ações e tarefas em relação à sequência e ao tempo.
- Existem quatro tipos principais de fluxo: linear, iterativo, evolucionário e paralelo.
- É importante não confundir fluxo de processo com modelos de processo (que combinam fluxo, padrões e organização do trabalho). Cada atividade possui um fluxo específico para desenvolver o software conforme o cenário, enquanto os modelos de processo são genéricos.

### 1.1 Fluxo Linear
- As atividades são executadas em sequência, uma única vez, seguindo a ideia de linha de produção (comunicação, planejamento, modelagem, construção e entrega).
- O teste é parte fundamental e está presente em todas as atividades.
- O software só é entregue ao final, quando completo.

### 1.2 Fluxo Iterativo
- Permite repetir atividades, voltando a etapas anteriores quando necessário (como um loop em programação).
- Surgiu para reduzir riscos de incertezas, especialmente quando falhas de comunicação e planejamento eram percebidas apenas na entrega.
- Não deve ser confundido com "interativo" (interação com usuário); iterativo significa repetição de atividades.

### 1.3 Fluxo Evolucionário
- As atividades são executadas de forma circular, com incrementos sucessivos que geram versões mais completas do software.
- O software evolui ao longo do tempo, com lançamentos de novas versões.

### 1.4 Fluxo Paralelo
- As atividades ocorrem simultaneamente, sendo útil em cenários com software mais específico onde tarefas podem ser paralelizadas.

> [!TIP] DICAS: 
> - O fluxo linear (cascata puro) é raro atualmente; a maioria dos processos modernos utiliza iteração.
> - Iterativo não é interativo: o primeiro refere-se a repetir etapas; o segundo, a interagir com usuários.

## 2. Modelo de Processo de Software
- Um modelo de processo fornece um guia específico para o trabalho de engenharia de software, definindo o fluxo de atividades, ações e tarefas, o grau de iteração, os artefatos e a organização do trabalho.
- Classificação:
  - Prescritivos (tradicionais ou dirigidos a planos);
  - Não prescritivos (ágeis).

### 2.1 Modelos Evolucionários (ou Incrementais)
- Utilizados quando há pressão por implantação rápida ou os requisitos essenciais são conhecidos, mas os detalhes ainda precisam ser definidos.
- São iterativos e geram versões cada vez mais completas.
- Atualmente, o termo "evolucionário" caiu em desuso, sendo substituído por "incremental".
- Exemplos clássicos: prototipação e modelo espiral.

> [!CAUTION] OBSERVAÇÃO: 
> - O processo cascata (waterfall) original era linear, mas hoje em dia ele também pode ser iterativo; apenas a primeira versão era estritamente linear.

## 3. Prototipação
- Protótipo é uma versão inicial do sistema, usada para demonstrar conceitos, experimentar opções de projeto e descobrir mais sobre o problema e suas soluções.
- Envolve desenvolvimento rápido e iterativo.
- Diferença entre rápido e ágil:
  - Ágil: processos iterativos incrementais, com foco em adaptação a mudanças e entrega contínua de incrementos.
  - Rápido: ciclo rápido, como na prototipação.
- Atualmente, a prototipação é usada como atividade dentro de outros processos, não mais como um modelo de processo autônomo.

### Tabela de Vantagens e Desvantagens da Prototipação
| VANTAGENS | DESVANTAGENS |
|---|---|
| Facilita a definição dos requisitos | Pressão para aproveitar o código escrito |
| Os envolvidos enxergam o que parece ser uma versão operacional do software | Retrabalho |
| Reduz os riscos e incertezas do desenvolvimento | Pode aumentar o custo do desenvolvimento |
| A experiência obtida pode reduzir o custo das etapas seguintes | |

> [!CAUTION] OBSERVAÇÃO: 
> - Um dos principais problemas da prototipação (e muito cobrado em provas) é a ilusão de que o software está pronto rapidamente, o que levou ao abandono do uso da prototipação como modelo de processo independente. Hoje, ela é usada apenas dentro de atividades de processos iterativos incrementais.

## 4. Modelo Espiral
- Modelo evolucionário que combina a natureza iterativa da prototipação com aspectos sistemáticos e controlados do modelo cascata.
- É fortemente focado em análise de riscos em cada atividade.
- As versões iniciais podem ser protótipos simples (como modelos de papel) e as versões finais tornam-se sistemas cada vez mais complexos.
- Foi projetado para sistemas de ciclo de vida longo e de grande porte.

### 4.1 Desvantagens do Modelo Espiral
- Se o orçamento for fixo, o modelo pode ser problemático, pois sistemas de ciclo de vida longo exigem manutenção e correção de bugs frequentes, gerando custos adicionais.

> [!TIP] DICAS: 
> - O modelo espiral é o exemplo mais clássico de processo evolucionário com ênfase em riscos.

## 5. Modelo Cascata na Visão de Sommerville
- O modelo cascata de Sommerville apresenta atividades diferentes da versão de Pressman.
- Ao final do processo, pode haver feedback, o que o diferencia do cascata linear original (Pressman).
- A principal diferença para o modelo incremental é que, no cascata, o software é entregue completo, enquanto no incremental são feitas versões parciais.

> [!CAUTION] OBSERVAÇÃO: 
> - No cascata de Pressman, o fluxo é linear e sem retorno; já na versão de Sommerville, há possibilidade de feedback, o que o torna menos rígido.