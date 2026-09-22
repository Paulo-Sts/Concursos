# Teste de Turing e Tipos de Inteligência Artificial

## 1. Teste de Turing
- Critério formal proposto por Alan Turing em 1950 para discutir a inteligência em máquinas.
- Avalia se uma inteligência artificial consegue enganar um ser humano em uma interação.
- Metodologia: um avaliador humano conversa por terminal com um humano e uma máquina simultaneamente sem saber quem é quem.
- Critério de sucesso ⟶ o sistema demonstra comportamento inteligente se o avaliador não conseguir identificar quem é a máquina.
- Foco da avaliação:
  - Comportamento observável;
  - Produção de respostas semelhantes às de uma pessoa;
  - Não busca provar consciência ou sentimentos.

### 1.1 Capacidades Exigidas no Teste Original
- Processamento de Linguagem Natural (PLN) para permitir comunicação bem-sucedida;
- Representação de Conhecimento para armazenar o que sabe ou ouve;
- Raciocínio Automatizado para usar informações e tirar novas conclusões;
- Aprendizado de Máquina para adaptar-se a novas circunstâncias e extrapolar padrões.

## 2. Teste de Turing Total
- Evolução do teste original que abandona o isolamento do mundo virtual.
- Envolve a interação direta com o ambiente físico e o uso de robótica.
- Adiciona a percepção e a ação física às capacidades originais de comunicação e raciocínio.

### Tabela de Comparação de Capacidades
| CAPACIDADES | TESTE ORIGINAL | TESTE TOTAL |
|---|---|---|
| Processamento de linguagem natural | Exige | Exige |
| Representação de conhecimento | Exige | Exige |
| Raciocínio automatizado | Exige | Exige |
| Aprendizado de máquina | Exige | Exige |
| Visão computacional | Não exige | Exige |
| Robótica | Não exige | Exige |

> [!TIP] DICAS: 
> - O diferencial crítico do teste total em relação ao original é a exigência de robótica e visão computacional.

> [!CAUTION] OBSERVAÇÃO: 
> - O teste original evitou a interação física por considerar a simulação física desnecessária para a definição de inteligência.

## 3. Classificação por Abordagem Técnica
- Define como a máquina funciona internamente e o algoritmo utilizado.

### 3.1 Inteligência Artificial Simbólica
- Considerada a abordagem antiga, baseada em regras explícitas.
- Trabalha com conhecimento perfeitamente compreensível pelo ser humano.
- O conhecimento é representado por símbolos, fatos e ontologias.
- Exemplos:
  - Sistemas especialistas;
  - Motores de inferência;
  - Chatbots baseados em opções fixas (ex.: menu numérico).

### 3.2 Inteligência Artificial Conexionista
- Inspirada abstratamente no funcionamento do cérebro humano.
- Baseada em redes neurais artificiais compostas por neurônios ou nós conectados em camadas.
- O conhecimento não é uma regra explícita, mas fica distribuído em pesos e conexões.
- Padrão dominante no mercado atual para Deep Learning e reconhecimento de padrões.

### 3.3 Inteligência Artificial Evolucionista
- Utiliza algoritmos genéticos como principais representantes.
- Baseada no processo de seleção natural digital para encontrar a melhor solução.
- Processo iterativo:
  - Geração de soluções;
  - Avaliação e seleção das melhores;
  - Recombinação e mutação para novas gerações.

### Tabela de Síntese Técnica
| TIPO | TRATAMENTO DO CONHECIMENTO | ESTRUTURA PRINCIPAL | CASOS DE USO |
|---|---|---|---|
| Simbólica | Conhecimento explícito e regras | Símbolos e ontologias | Sistemas especialistas |
| Conexionista | Padrões distribuídos por exemplos | Redes neurais e pesos | Imagem, voz e textos |
| Evolucionista | Adaptação e sobrevivência | Seleção e mutação | Otimização e busca |

## 4. Classificação por Nível de Capacidade
- Avalia o quão inteligente o sistema é em relação ao ser humano.

### 4.1 Inteligência Artificial Fraca ou Estreita (ANI)
- Representa a realidade tecnológica atual.
- Projetada para executar tarefas específicas e delimitadas em um domínio restrito.
- Não possui consciência, mente ou compreensão geral do mundo.
- Pode superar humanos em tarefas isoladas (ex.: processar grandes planilhas ou filtrar spams).

### 4.2 Inteligência Artificial Forte ou Geral (AGI)
- Hipótese teórica de uma inteligência comparável à humana.
- Seria capaz de aprender, raciocinar e transferir conhecimento entre diferentes contextos de forma fluida.
- Pressupõe autonomia cognitiva plena e consciência.

### 4.3 Superinteligência (ASI)
- Possibilidade estritamente teórica que ultrapassaria o nível humano máximo.
- Superior à inteligência humana em praticamente todos os domínios, incluindo criatividade e ciência.

### Tabela de Escala de Capacidade
| SIGLA | NOME | ESCOPO DE ATUAÇÃO | STATUS ATUAL |
|---|---|---|---|
| ANI | Estreita ou fraca | Uma tarefa específica | Realidade existente |
| AGI | Geral ou forte | Múltiplas tarefas e nível humano | Hipótese teórica |
| ASI | Superinteligente | Supera o humano em tudo | Teórica e ficção |

> [!TIP] DICAS: 
> - O ChatGPT e outros modelos generativos atuais ainda são classificados como inteligência artificial fraca (ANI).

> [!CAUTION] OBSERVAÇÃO: 
> - Não existe transição natural ou autônoma da ANI para a AGI; a inteligência artificial estreita não evolui sozinha para o nível humano.