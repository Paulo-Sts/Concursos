# Principais Ferramentas de Mercado (Copilot, ChatGPT, Meta)

## 1. Microsoft Copilot
- Lançado em fevereiro de 2023 como Bing Chat e posteriormente renomeado para Microsoft Copilot.
- A Microsoft investiu fortemente na OpenAI, integrando gradualmente suas tecnologias ao portfólio de serviços da empresa.
- Integra-se a diversos produtos, como Windows, Edge, Android, iOS e Microsoft 365.
- Baseado na arquitetura GPT-4 da OpenAI, com uma camada proprietária da Microsoft chamada Prometheus, que o diferencia do ChatGPT tradicional.
- Capaz de gerar textos, imagens, relatórios, resumos e fornecer assistência conversacional.

### 1.1 Soluções do Copilot
- Microsoft 365 Copilot: integrado aos aplicativos do pacote Microsoft 365.
- Microsoft Security Copilot: utiliza dados de sistemas de proteção (antivírus, firewall, IDS/IPS) para analisar logs, identificar problemas e propor soluções, substituindo parte do trabalho do analista de segurança.
- Copilot no Azure: atua na nuvem da Microsoft sugerindo tipos de infraestrutura conforme a necessidade do usuário.
- GitHub Copilot: auxilia desenvolvedores gerando automaticamente trechos de código, reduzindo a codificação manual.
- Microsoft Copilot Studio: permite a criação de agentes inteligentes para execução de tarefas específicas.
- Copilot no Power Apps: conjunto de aplicativos da Microsoft que utiliza o Copilot para desenvolvimento de soluções sem codificação (abordagem no-code).

> [!TIP] DICAS: 
> - O Copilot no Word não exige ativação manual por documento; uma vez ativado, fica disponível automaticamente nos documentos subsequentes.
> - No Excel, o Copilot adiciona novas colunas com fórmulas baseadas nos dados existentes, evitando cálculos manuais linha por linha.

> [!CAUTION] OBSERVAÇÃO: 
> - O Copilot não exige conhecimentos avançados de programação; o usuário insere comandos em linguagem natural (prompts) e obtém respostas em texto, imagens ou descrições de imagens.
> - A responsabilidade final sobre os conteúdos gerados permanece humana, sendo essencial revisar, editar e verificar as sugestões, pois a ferramenta pode cometer erros (alucinações).

## 2. Meta
- Empresa controladora do Facebook, Instagram, WhatsApp e Threads.
- Mudou o nome de Facebook Inc. para Meta Platforms Inc. em 2021, com o objetivo de focar no desenvolvimento do metaverso e tecnologias emergentes.
- Fundador e CEO: Mark Zuckerberg.
- A Meta incorporou inteligência artificial a seus serviços, embora o projeto do metaverso não tenha se desenvolvido conforme o esperado.

### 2.1 IA na Estratégia da Meta
- A Meta investe fortemente em pesquisa de Inteligência Artificial, com foco em:
  - Modelos de linguagem (LLMs), como o GPT;
  - Visão computacional: capacidade de identificar padrões em imagens e vídeos;
  - Aprendizado autossupervisionado: utilizado no treinamento de modelos como os GPTs e transformers;
  - Robótica e simulação.
- A IA é usada em moderação de conteúdo, personalização de feeds, tradução automática e realidade aumentada/virtual.

### 2.2 Principais Projetos da Meta
- LLaMA (Large Language Model Meta AI):
  - Modelos de linguagem abertos, concorrentes do GPT.
  - LLaMA 2 lançado em 2023; LLaMA 3 previsto para 2024–2025.
  - Foco em transparência e código aberto.
  - O maior desafio não está no código, mas no poder de processamento e na base de dados para treinamento (GPUs, processadores avançados, placas gráficas e grandes volumes de dados).
- PyTorch:
  - Biblioteca de aprendizado profundo criada pela Meta AI.
  - Muito usada em pesquisas de IA no mundo todo.
  - Concorrente direta do TensorFlow (Google).
- FAIR (Facebook AI Research):
  - Divisão de pesquisa em IA da Meta.
  - Produz artigos científicos, ferramentas e benchmarks abertos.

### 2.3 Uso de IA nos Produtos da Meta
- Facebook/Instagram:
  - IA para detecção de discurso de ódio, fake news e spam.
  - Algoritmos de recomendação de conteúdo baseados em comportamento.
  - Reconhecimento facial (em pausa desde 2021 por questões éticas).
- WhatsApp:
  - Criptografia ponta a ponta com moderação inteligente de abuso.
  - Bots e IA generativa em testes para atendimento e interações com empresas.
- Metaverso:
  - IA usada para criar avatares realistas, tradução de fala em tempo real e interação com ambientes 3D.

## 3. ChatGPT
- Chatbot baseado em IA, desenvolvido pela OpenAI.
- GPT = Generative Pre-trained Transformer.
- Utiliza modelos de linguagem de larga escala (LLMs) treinados para prever a próxima palavra em uma sequência de texto.
- Capaz de realizar conversações, redação de textos, tradução, resumo, programação, entre outras tarefas.

### 3.1 Base Tecnológica
- Arquitetura baseada em Transformers (principal padrão em Processamento de Linguagem Natural - PLN).
- Versões do GPT:
  - GPT-3 (2020): 175 bilhões de parâmetros;
  - GPT-3.5 (2022);
  - GPT-4 (2023): mais preciso e multimodal;
  - GPT-4o (2024): otimizado, mais rápido e com entrada/saída por voz, texto e imagem.

### 3.2 Treinamento
- O treinamento de modelos como o ChatGPT envolve bilhões de atualizações nos parâmetros da rede neural para melhorar suas previsões.
- Pré-treinamento (Pretraining): o modelo aprende padrões da linguagem em grandes volumes de texto, utilizando aprendizado não supervisionado (previsão da próxima palavra).
- Ajuste fino (Fine-tuning): direcionamento do modelo para tarefas específicas com supervisão humana. Um engenheiro de prompts faz perguntas, analisa respostas e oferece retorno à máquina.
- Aprendizado com Reforço via Feedback Humano (RLHF): otimização da interação com base em preferências humanas. O usuário, ao escolher entre duas opções de resposta, contribui para o treinamento do modelo.
- O Fine Tuning é fundamental para garantir que o modelo se mantenha politicamente correto, evite impropriedades e não reproduza vieses aprendidos nos dados de treinamento (como racismo, misoginia ou homofobia).

> [!TIP] DICAS: 
> - O ChatGPT é uma ferramenta poderosa, mas pode gerar respostas imprecisas ou contextualmente inadequadas (fenômeno conhecido como alucinação).
> - O ChatGPT passou por fine tuning, ou seja, foi ajustado especificamente para tarefas de conversação.

> [!CAUTION] OBSERVAÇÃO: 
> - O ChatGPT não apresenta uma bibliografia confiável das fontes utilizadas; funciona como uma "caixa-preta" (black box), em que não é possível entender claramente como se chegou a determinada resposta.
> - Apesar de aprender a prever a próxima palavra, o ChatGPT possui um tipo de compreensão de estrutura e conteúdo da linguagem, ainda que não seja igual à humana.
> - O ChatGPT não foi desenvolvido pela Microsoft, apesar da parceria entre as empresas.