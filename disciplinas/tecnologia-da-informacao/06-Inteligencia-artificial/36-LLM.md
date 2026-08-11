# Modelos De Linguagem De Larga Escala (Llms)

## 1. O Que São Llms?
- São modelos de redes neurais profundas, treinados com quantidades gigantescas de textos, que generalizam e promovem o raciocínio em linguagem natural.
- São a base de toda IA de conversa no mercado, como Gemini, ChatGPT e Copilot.
- O algoritmo processa um prompt (entrada de dados) e gera uma saída processada que faça sentido.
- São capazes de gerar textos, resumos, traduções e códigos em linguagem de programação.
- Podem ser ajustados para tarefas específicas por meio de duas técnicas principais:
  - Fine-tuning: processo que utiliza a ajuda de humanos para avaliar e escolher as melhores respostas, guiando o modelo na direção correta;
  - Engenharia de prompt (Prompt Engineering): técnica em que o usuário constrói prompts específicos com respostas esperadas para treinar a máquina.

## 2. Detalhes Técnicos Dos Llms

### 2.1 Baseados Em Transformadores
- Utilizam a arquitetura Transformer, criada em 2017.
- Possuem o mecanismo de atenção, que permite prestar atenção específica nas palavras mais importantes do texto.
- Permitem paralelismo no treinamento e lidam com dependências de longo prazo, um problema comum em IAs generativas que tendem a ter memória seletiva.
- O RAG (Retrieval-Augmented Generation) é uma base de dados que a IA consulta para não se esquecer de informações passadas.

### 2.2 Autorregressivos
- O modelo gera a resposta token por token (palavra por palavra), tornando o processo de criação mais lento.
- Para gerar imagens, o processo é semelhante, gerando pixel por pixel.
- A previsão do próximo token é baseada no contexto, no prompt e na palavra anterior.

### 2.3 Treinamento Com Aprendizado Não Supervisionado
- O treinamento inicial é feito com uma base gigante de textos, sem rótulos.
- As principais técnicas de modelagem são:
  - Next-token prediction: o modelo aprende a prever a próxima palavra em uma sequência (ex.: "sonho de..." provavelmente será "valsa");
  - Masked language modeling: o texto é mascarado aleatoriamente e o modelo deve prever a palavra que melhor se encaixa naquele espaço.

### 2.4 Domínio Amplo De Linguagem Natural
- Os LLMs são aplicados em Processamento de Linguagem Natural (PLN).
- São capazes de atuar em diversos idiomas e domínios temáticos, desde culinária até assuntos obscuros de TI.

### 2.5 Escalabilidade
- O desempenho do modelo tende a melhorar com o aumento da quantidade de dados e de parâmetros.
- Parâmetros de entrada se referem à quantidade de palavras que o modelo consegue processar e gerar simultaneamente.
- Essa escalabilidade gera habilidades emergentes, como a capacidade de "raciocinar" e codificar em linguagens de programação que não foram estudadas diretamente.

### 2.6 Inferência Sequencial
- Os modelos geram saídas seguindo uma ordem sequencial (um token por vez), com exceção do BERT (do Google).

### 2.7 Sensíveis Ao Contexto
- Utilizam janelas de contexto, que são a quantidade de informações que o modelo consegue reter.
- O contexto é composto pelo histórico da conversa e pelo que se sabe sobre o usuário.
- Modelos mais potentes possuem janelas de contexto maiores.

> [!CAUTION] OBSERVAÇÃO: 
> - A alucinação é um problema crítico, especialmente em áreas como direito, medicina e educação, pois a IA gera informações convincentes, mas imprecisas ou errôneas.

### 2.8 Podem Alucinar
- Em assuntos desconhecidos, mesmo entregando informações corretas na maioria das vezes, o modelo pode gerar dados errados (alucinação).

> [!TIP] DICAS: 
> - Para estudos, recomenda-se usar a IA apenas na etapa de revisão, após aprender o conteúdo com videoaulas e PDFs;
> - Peça resumos ao ChatGPT e corrija os equívocos que ele apresentar;
> - Use a IA para criar questões e simulados;
> - A tríade de estudo é: aprender, revisar e resolver questões.

### 2.9 Exigem Muita Infraestrutura
- O treinamento e a execução são caros e exigem GPUs ou TPUs (placas de vídeo).
- Por isso, utiliza-se a infraestrutura de grandes empresas (OpenAI, Microsoft, Google) ou de institutos de pesquisa e governos.

### 2.10 Sensíveis A Dados Pessoais E Éticos
- As máquinas são treinadas com dados públicos da internet e, muitas vezes, com interações dos usuários, o que pode incluir dados pessoais e sensíveis.
- Embora as correções feitas pelo usuário possam ser guardadas no contexto, um novo treinamento formal é necessário para que a máquina aprenda efetivamente com elas.