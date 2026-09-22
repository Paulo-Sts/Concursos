# Tipos de Aprendizado de Máquina 2

## 1. Aprofundamento do Aprendizado Supervisionado
- Utiliza uma base de dados previamente classificada ou rotulada para o treinamento do algoritmo.
- O algoritmo é treinado a partir de pares entrada-saída previamente definidos, onde cada entrada X possui uma saída desejada Y.
- Durante o treinamento, o sistema gera uma função de mapeamento, representada matematicamente por Y = f(X).
- O objetivo central deste processo é criar um modelo preditivo capaz de realizar a generalização correta para novos dados que ainda não foram apresentados ao sistema.

> [!CAUTION] OBSERVAÇÃO: 
> - O aprendizado supervisionado exige obrigatoriamente a presença de rótulos, pois o indutor necessita da resposta correta para ajustar seus parâmetros internos.

## 2. Aprofundamento do Aprendizado Não Supervisionado
- Caracteriza-se pela ausência total de rótulos ou classes prévias no conjunto de dados utilizado no treinamento.
- O algoritmo deve identificar padrões, estruturas ou agrupamentos significativos de forma autônoma e sem intervenção humana.
- Funciona através da detecção de similaridades entre os dados, organizando elementos parecidos em grupos e separando os diferentes.
- É a técnica ideal para realizar análises onde o objetivo é descobrir conhecimentos ocultos em dados que não contêm respostas corretas pré-definidas.

> [!CAUTION] OBSERVAÇÃO: 
> - Atribuir rótulos prévios a este tipo de técnica contraria o seu conceito fundamental de descoberta autônoma de padrões.

## 3. Aprendizado Auto-supervisionado
- Representa uma abordagem onde o próprio algoritmo descobre e gera os rótulos durante a fase de pré-treino.
- É a técnica fundamental utilizada em modelos do tipo Transformer, que servem de base para inteligências artificiais generativas como o ChatGPT.
- O modelo é submetido a uma grande base textual não rotulada e aprende as relações entre as palavras por conta própria.

> [!CAUTION] OBSERVAÇÃO: 
> - Alguns autores podem classificar esse processo como aprendizado não supervisionado devido à ausência inicial de rótulos atribuídos por humanos.

## 4. Aprendizado por Reforço
- Consiste na interação contínua de um agente inteligente com um ambiente dinâmico.
- O aprendizado ocorre por meio de um sistema de retroalimentação que fornece recompensas ou penalidades conforme as ações tomadas pelo agente.
- O objetivo do agente é aprender a tomar decisões que maximizem a recompensa cumulativa ao longo do tempo.
- Exemplo prático: um robô explorando a superfície da Lua que recebe penalidades ao colidir com obstáculos e recompensas ao seguir por caminhos seguros.

### 4.1 Equilíbrio entre Exploration e Exploitation
- Exploration: o agente toma decisões inéditas e busca caminhos novos para avaliar resultados nunca obtidos anteriormente;
- Exploitation: o agente repete decisões que já sabe que resultam em recompensas, permanecendo em sua zona de segurança;
- O uso equilibrado das duas táticas é essencial para que o agente encontre as melhores recompensas sem ficar preso em ciclos de ações limitadas.

> [!CAUTION] OBSERVAÇÃO: 
> - O aprendizado por reforço não deve ser confundido com a regressão; a regressão busca prever atributos-alvo a partir de variáveis, enquanto o reforço foca na dinâmica de interação e recompensa.

> [!TIP] DICAS: 
> - O estudo dos diferentes tipos de aprendizado é apontado como o assunto de maior recorrência em provas de concursos públicos sobre inteligência artificial.