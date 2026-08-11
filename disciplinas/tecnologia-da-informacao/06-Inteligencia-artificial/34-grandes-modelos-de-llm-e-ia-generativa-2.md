# Grandes Modelos de Linguagem (LLM) e IA Generativa 2

## 1. Ética na Ia Generativa
- Deep fake e manipulação de mídia;
- Violação de privacidade;
- Viés e discriminação;
- Direitos autorais e propriedade intelectual;
- Perda de emprego;
- Manipulação de eleições;
- Uso de identidade falsa;
- Manipulação emocional;
- Desigualdade digital;
- Ataques cibernéticos;
- Redes Adversariais Generativas.

## 2. Tecnologias

### 2.1 Redes Adversariais Generativas (Gans)
- As GANs são compostas por duas redes neurais que competem entre si: um gerador e um discriminador.
- O gerador cria novos dados a partir de um conjunto de treinamento.
- O discriminador, treinado com dados reais, avalia se os dados gerados são autênticos ou falsos.
- Esse processo competitivo aprimora a qualidade da geração de dados.

### 2.2 Generative Pre-Training Transformer (Gpt)
- O ChatGPT é um exemplo de grande modelo de linguagem baseado na arquitetura GPT.
- Ele funciona como um grande codificador (encoder) e decodificador (decoder), processando e gerando texto.

## 3. Chatgpt

### 3.1 Características Gerais
- Variante do modelo de linguagem GPT (Generative Pretrained Transformer) desenvolvido pela OpenAI.
- Otimizado especificamente para gerar respostas em formato de conversação.
- Com a integração com a Microsoft, o ChatGPT pode gerar arquivos nos formatos pptx, docx, excel, além de executar programação e realizar pesquisas na internet.
- Capaz de compreender e responder a uma ampla variedade de solicitações em linguagem natural.
- Fornece informações, realiza tarefas específicas ou engaja-se em diálogos casuais.

### 3.2 Treinamento
- O treinamento utiliza duas técnicas principais:
  - Aprendizado supervisionado: o modelo é alimentado com pares de perguntas e respostas para aprender a prever respostas adequadas.
  - Aprendizado por reforço a partir de demonstrações humanas: usado para ajustar as respostas com base em feedback humano.

### 3.3 Limitações
- Conhecimento atualizado: a última atualização do modelo ocorreu em março de 2023.
- Perda de compreensão contextual em textos longos.
- Vieses presentes nos dados de treinamento podem ser reproduzidos nas respostas.
- Precisão da informação: o modelo pode gerar informações incorretas ou fictícias, fenômeno conhecido como alucinação.
- Interpretação literal: pode não captar nuances ou contextos implícitos.

> [!TIP] DICAS: 
> - Para questões de concurso, memorize as três principais ferramentas de IA generativa citadas: Bing Chat, Google Bard e ChatGPT.
> - A questão do material (IESES/2023) exemplifica bem como o assunto é cobrado: identificar exemplos concretos de IAs generativas.

### 3.4 Exemplo Prático
- Ferramentas de IA generativa: Bing Chat, Google Bard e ChatGPT são exemplos amplamente reconhecidos.
- O ChatGPT, especificamente, é uma variante do GPT da OpenAI, otimizada para diálogo.

## 4. Engenharia De Prompt

### 4.1 Conceito e Exemplo
- Engenharia de prompt é a prática de projetar entradas (prompts) para guiar o modelo de IA a gerar a saída desejada.
- Exemplo de classificação de sentimentos:
  - Prompt: "Que dia lindo!" ⟶ Resposta: positivo.
  - Prompt: "Eu odeio esta aula" ⟶ Resposta: negativo.
  - Prompt: "Eu amo bolsos em calças" ⟶ Resposta: positivo.

### 4.2 Orientações Para Elaboração De Prompts
- Especificidade;
- Contexto;
- Estilo;
- Palavras-chave;
- Estruture a resposta desejada;
- Adequação ao domínio;
- Mitigação de viés;
- Analogias;
- Use exemplos (zero-shot, one-shot, few-shot);
- Passo a passo.

> [!CAUTION] OBSERVAÇÃO: 
> - Zero-shot, one-shot e few-shot referem-se à quantidade de exemplos fornecidos no prompt: zero-shot não fornece exemplos, one-shot fornece um, few-shot fornece alguns. Essa técnica melhora a precisão da resposta.