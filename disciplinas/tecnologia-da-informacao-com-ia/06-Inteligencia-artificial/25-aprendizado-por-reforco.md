# Aprendizado por Reforço

## 1. Definição e Conceito Geral
- O aprendizado por reforço é um método de aprendizado de máquina onde um agente aprende a tomar decisões por meio de tentativa e erro, interagindo com um ambiente.
- O agente recebe recompensas por ações corretas, visando maximizar a recompensa total ao longo do tempo.
- Funcionamento básico: se a máquina acerta, ela ganha; se erra, ela perde.
- O agente de inteligência está no ambiente e precisa explorar a decisão correta.

> [!NOTE] DICA:
> - O aprendizado por reforço é diferente do supervisionado (que possui rótulos prévios) e do não supervisionado (que agrupa dados para extrair padrões ocultos).

## 2. Conceitos-Chave
- Agente: entidade que toma decisões (robô, software, etc.).
- Ambiente: mundo com o qual o agente interage e sobre o qual ele não tem controle total.
- Estado: representação da situação atual do agente dentro do ambiente.
- Ações: possíveis intervenções que o agente pode fazer no ambiente.
- Recompensa: sinal do ambiente em resposta às ações do agente, indicando o sucesso dessas ações (pode ser positiva ou negativa).
- Política (policy): estratégia que define a escolha de ação do agente em determinados estados; quanto melhor a política, melhores serão as escolhas.
- Função de valor: previsão da recompensa futura esperada, utilizada para avaliar quão bom é um estado ou uma ação.
- Episódio: sequência de ações, estados e recompensas que termina em um estado final.

> [!TIP] DICA:
> - A política não é fixa; ela se adapta conforme o agente aprende com as experiências.

## 3. Funcionamento do Aprendizado por Reforço
- Observação do estado do ambiente.
- Tomada de decisão baseada na política.
- Execução da ação e observação da recompensa e do novo estado.
- Atualização da política com base na recompensa recebida.
- O ambiente retorna um prêmio baseado na função e no estado em que o agente ficou; o estado pega a recompensa e atualiza a política com base nos dados recebidos.

> [!CAUTION] OBSERVAÇÃO:
> - A recompensa é recebida apenas após a ação, ou seja, é um feedback atrasado, que avalia a ação anterior.

## 4. Aplicações do Aprendizado por Reforço
- Jogos: melhoria de estratégias em jogos complexos (Go, xadrez).
- Robótica: ensinar robôs a realizar tarefas como caminhar e pegar objetos.
- Sistemas de recomendação: personalização de conteúdo em plataformas de streaming.
- Otimização de processos: melhoria da logística e cadeia de suprimentos.
- Automação de veículos: desenvolvimento de sistemas de condução autônoma.
- Exemplo prático: entre o ponto A e o ponto B existem vários caminhos; a depender do caminho percorrido, o agente recebe uma recompensa (ex.: economia de tempo).

## 5. Exploração (Exploration) vs. Explotação (Exploitation)
- Exploração: processo de tentar novas ações com pouca ou nenhuma experiência anterior para descobrir informações valiosas sobre o ambiente.
  - Essencial em estágios iniciais do aprendizado para coletar dados sobre quais ações resultam em melhores recompensas.
  - Sem exploração suficiente, o agente pode nunca descobrir estratégias ótimas.
  - A exploração tem um custo: ações desconhecidas podem levar a resultados negativos a curto prazo.
- Explotação: uso do conhecimento adquirido para tomar decisões que o agente já sabe que resultarão em boas recompensas.
  - Desafio: se o agente focar exclusivamente na explotação, baseando-se apenas no conhecimento atual, ele pode perder a oportunidade de descobrir ações ainda mais recompensadoras.
- Em um estado desconhecido, a tomada de decisão será explorada e tomada na aleatoriedade.

> [!TIP] DICA:
> - O equilíbrio entre exploração e explotação é crucial para maximizar a recompensa cumulativa.

## 6. Cenário de Utilização (Exemplo Prático)
- Agente: pequeno robô controlado por um programa de IA.
- Ambiente: tabuleiro quadrado com várias células, algumas com obstáculos e uma com o tesouro.
- Recompensa: positiva ao encontrar o tesouro; negativa ao colidir com obstáculos ou sair do tabuleiro.
- Objetivo: aprender a política que maximiza a recompensa cumulativa, ou seja, encontrar o tesouro com o mínimo de colisões.
- Inicialização: o agente começa sem conhecimento sobre o ambiente e explora com ações aleatórias.
- Recompensas: recebidas após cada ação; o agente aprende que colisões resultam em recompensas negativas e o tesouro em positiva.
- Aprendizado da política: usa um algoritmo de aprendizado por reforço para ajustar sua política baseado nas recompensas, aprendendo a evitar obstáculos e procurar o tesouro.
- Dilema: enfrenta a escolha entre explorar novas ações (célula desconhecida) versus explorar ações conhecidas (célula segura).
- Aprimoramento gradual: com o tempo, o agente aprimora sua política, tomando decisões mais inteligentes com base em experiências passadas.

## 7. Deep Q-Network (DQN)
- Q-learning: visa aprender a política ótima, ensinando ao agente qual ação tomar sob determinadas condições para maximizar a soma de recompensas futuras.
  - Isso é feito através de uma função de valor Q, que estima a recompensa total esperada de tomar uma ação em um dado estado.
- Redes neurais profundas: no DQN, redes neurais profundas são usadas para aproximar a função de valor Q.
  - Permite que o agente lide com estados de entrada de alta dimensão (como imagens de pixels de jogos), algo que métodos tradicionais de Q-learning não conseguem fazer de forma eficiente devido à maldição da dimensionalidade.

> [!TIP] DICA:
> - O DQN é um exemplo clássico de aprendizado por reforço profundo (Deep Reinforcement Learning).