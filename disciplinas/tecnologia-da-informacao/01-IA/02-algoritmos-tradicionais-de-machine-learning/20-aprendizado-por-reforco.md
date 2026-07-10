# Anotações – Aprendizado por Reforço

## 1. Conceito de Aprendizado por Reforço

- **Aprendizado por Reforço (Reinforcement Learning)** é um tipo de aprendizado de máquina onde um **agente** aprende a tomar decisões **interagindo com um ambiente**.
- O aprendizado ocorre por **tentativa e erro** – o agente recebe **recompensas** (positivas) ou **penalidades** (negativas) com base em suas ações.
- **Objetivo:** maximizar a **recompensa cumulativa** ao longo do tempo.

> ### 1.1 Analogia simples
> - Se o agente acerta, **ganha**.
> - Se o agente erra, **perde**.
> - Com o tempo, ele aprende quais ações levam a melhores resultados.

## 2. Conceitos-Chave do Aprendizado por Reforço

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Agente** | A entidade que toma decisões (ex.: robô, software). |
| **Ambiente** | O mundo com o qual o agente interage (sobre o qual não tem controle total). |
| **Estado** | Representação da situação atual do agente no ambiente. |
| **Ações** | As possíveis intervenções que o agente pode fazer no ambiente. |
| **Recompensa** | Sinal do ambiente em resposta às ações do agente (positivo ou negativo). |
| **Política (Policy)** | Estratégia que define qual ação o agente deve tomar em cada estado. |
| **Função de Valor** | Previsão da recompensa futura esperada – avalia quão bom é um estado ou ação. |
| **Episódio** | Sequência de ações, estados e recompensas que termina em um estado final. |

## 3. Funcionamento do Aprendizado por Reforço

1. **Observação:** o agente observa o estado atual do ambiente.
2. **Decisão:** com base na política, o agente escolhe uma ação.
3. **Ação e feedback:** o agente executa a ação e recebe a **recompensa** e o **novo estado**.
4. **Atualização:** a política é atualizada com base na recompensa recebida.
5. O processo se repete iterativamente.

```
Agente → Ação → Ambiente → Recompensa + Novo Estado → Agente (atualiza política)
```

## 4. Exploração (Exploration) vs. Exploração (Exploitation)

| CONCEITO | DESCRIÇÃO |
| --- | --- |
| **Exploration (Exploração)** | Tentar **ações novas** (desconhecidas) para descobrir informações valiosas sobre o ambiente. Essencial para encontrar estratégias ótimas. |
| **Exploitation (Exploração/uso)** | Usar o **conhecimento adquirido** – repetir ações que já se sabe que geram boas recompensas. |

> ### 4.1 Dilema (trade-off)
> - Se o agente só **explora**, nunca usa o que aprendeu.
> - Se o agente só **explora**, nunca descobre novas estratégias melhores.
> - O agente deve encontrar um **equilíbrio** entre os dois.

## 5. Aplicações do Aprendizado por Reforço

| APLICAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Jogos** | Melhorar estratégias em jogos complexos (Go, xadrez, videogames). |
| **Robótica** | Ensinar robôs a caminhar, pegar objetos, etc. |
| **Sistemas de recomendação** | Personalizar conteúdo para usuários. |
| **Otimização de processos** | Melhorar logística e cadeia de suprimentos. |
| **Automação de veículos** | Desenvolver sistemas de condução autônoma. |

## 6. Deep Q-Network (DQN)

- **Q-learning:** algoritmo que ensina ao agente qual ação tomar em cada estado para maximizar a soma de recompensas futuras (função de valor Q).
- **DQN (Deep Q-Network):** combina Q-learning com **redes neurais profundas**.
  - Permite lidar com **estados de alta dimensão** (ex.: imagens de pixels).
  - Supera a *maldição da dimensionalidade* dos métodos tradicionais.

## 7. Quadro Comparativo – Tipos de Aprendizado

| CRITÉRIO | SUPERVISIONADO | NÃO SUPERVISIONADO | POR REFORÇO |
| --- | --- | --- | --- |
| **Rótulos** | Sim | Não | Não (apenas recompensas) |
| **Feedback** | Saída desejada (Y) | Padrões ocultos | Recompensa (positiva/negativa) |
| **Interação** | Estática (dados fixos) | Estática | **Dinâmica** (agente-ambiente) |
| **Objetivo** | Prever (classificar/regredir) | Descrever (agrupar/associar) | Maximizar recompensa cumulativa |

## 8. Questões de Concurso Comentadas

### 8.1 (CESPE/CEBRASPE/2023/SEFIN FORTALEZA – Analista)

**Item:** "Nos algoritmos de aprendizado por reforço, o agente recebe uma recompensa atrasada na próxima etapa de tempo para avaliar sua ação anterior; seu objetivo, então, é maximizar a recompensa."

**Gabarito: Certo (C).**

**Comentário:** A recompensa é recebida após a ação, e o objetivo é maximizar a recompensa cumulativa.

### 8.2 (CESPE/CEBRASPE/2023/DATAPREV – Analista)

**Item:** "O aprendizado por reforço é um tipo de aprendizagem de máquina que tem por objetivo prever o resultado de um atributo alvo exclusivamente por meio de reforço no treinamento do modelo."

**Gabarito: Errado (E).**

**Comentário:** Previsão de atributo-alvo é característica do **aprendizado supervisionado**. O reforço envolve agente, ambiente e recompensas.

### 8.3 (Questão conceitual)

**Item:** "Qual das opções melhor descreve o princípio básico do aprendizado por reforço?"

**Gabarito: c) O agente aprende a tomar decisões através da experimentação no ambiente, buscando maximizar a soma de recompensas ao longo do tempo.**

### 8.4 (Questão conceitual – Política)

**Item:** "O que é uma política (policy) no aprendizado por reforço?"

**Gabarito: c) Um mapeamento de estados do ambiente para ações que o agente deve tomar, baseado em experiências passadas.**

### 8.5 (Questão conceitual – Função de valor)

**Item:** "O que é a função de valor?"

**Gabarito: b) Uma estimativa das recompensas futuras que um agente pode esperar receber, estando em um determinado estado ou tomando uma certa ação.**

### 8.6 (Questão conceitual – DQN)

**Item:** "Qual dos seguintes algoritmos é um exemplo de aprendizado por reforço profundo?"

**Gabarito: c) Deep Q-Network (DQN).**

### 8.7 (Questão conceitual – Robô caminhando)

**Item:** "Robô ajusta seus movimentos baseando-se em recompensas por manter o equilíbrio e penalidades por cair."

**Gabarito: c) Recebendo recompensas por manter o equilíbrio e penalidades por cair, ajustando seus passos de acordo.**

### 8.8 (Questão conceitual – Xadrez)

**Item:** "Sistema de IA treinado para jogar xadrez, melhorando ao maximizar recompensas (vencer partidas)."

**Gabarito: c) O agente melhora suas decisões ao maximizar suas recompensas, que, neste caso, são ganhar as partidas.**

### 8.9 (Questão conceitual – Otimização de rotas)

**Item:** "Agente aprendendo a otimizar rotas de entrega com feedback após cada rota."

**Gabarito: b) Q-learning para ajustar a política de decisão com base no feedback recebido.**

### 8.10 (Questão conceitual – Moderador de comentários)

**Item:** "Software aprende a moderar comentários usando feedback dos usuários (recompensas e penalidades)."

**Gabarito: e) A habilidade do agente de aprender e otimizar seu comportamento através da interação com o ambiente.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/SEFIN/2023) | C |
| 02 (CESPE/DATAPREV/2023) | E |
| 03 (Conceitual) | c |
| 04 (Conceitual – Política) | c |
| 05 (Conceitual – Função de valor) | b |
| 06 (Conceitual – DQN) | c |
| 07 (Conceitual – Robô) | c |
| 08 (Conceitual – Xadrez) | c |
| 09 (Conceitual – Rotas) | b |
| 10 (Conceitual – Moderador) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Aprendizado por Reforço** | Agente aprende por tentativa e erro com recompensas. |
| **Agente** | Quem toma as decisões. |
| **Ambiente** | Mundo com o qual o agente interage. |
| **Estado** | Situação atual do agente. |
| **Ação** | Intervenção do agente no ambiente. |
| **Recompensa** | Feedback positivo ou negativo. |
| **Política (Policy)** | Estratégia que mapeia estados → ações. |
| **Exploration** | Tentar novas ações. |
| **Exploitation** | Usar ações conhecidas. |
| **DQN** | Q-learning + redes neurais profundas. |

---

*Material complementar à aula "Aprendizado por Reforço" (professor Vitor Kessler/Gran Concursos).*