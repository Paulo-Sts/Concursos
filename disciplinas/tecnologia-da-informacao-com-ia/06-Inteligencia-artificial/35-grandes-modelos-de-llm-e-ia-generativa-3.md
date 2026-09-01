# Grandes Modelos de Linguagem (LLM) e IA Generativa 3

## 1. Engenharia de Prompt
- A engenharia de prompt consiste na arte e técnica de formular instruções claras e específicas para modelos de linguagem, visando obter respostas precisas e relevantes.
- A qualidade do prompt determina diretamente a qualidade da resposta gerada pela IA.

### 1.1 Exemplo de Classificação de Sentimentos
- O material apresenta um exemplo prático de classificação de tweets como positivos ou negativos.
- Exemplo: Tweet "Que dia lindo!" ⟶ classificado como positivo.
- Exemplo: Tweet "Eu odeio esta aula" ⟶ classificado como negativo.
- Exemplo: Tweet "Eu amo bolsos em calças" ⟶ classificado como positivo.

### 1.2 Orientações para Elaboração de Prompts
- Especificidade: quanto mais detalhada a instrução, mais precisa será a resposta.
- Contexto: fornecer contexto amplia a capacidade da IA de gerar respostas adequadas.
- Estilo: definir o estilo desejado (formal, informal, técnico, etc.) direciona a saída.
- Palavras-chave: incluir termos relevantes ajuda a IA a focar no assunto.
- Estrutura da resposta desejada: indicar o formato esperado (lista, resumo, passo a passo) melhora a organização da resposta.
- Adequação ao domínio: adaptar a linguagem ao campo de conhecimento específico.
- Mitigação de viés: estar atento para evitar respostas tendenciosas ou discriminatórias.
- Analogias e exemplos: fornecer exemplos concretos (zero-shot, one-shot, few-shot) melhora o entendimento da IA.
- Passo a passo: solicitar respostas detalhadas em etapas facilita a compreensão.

> [!TIP] DICAS:
> - Quanto mais contexto fornecido, mais específica será a resposta.
> - Use exemplos (zero-shot, one-shot, few-shot) para orientar melhor a IA.
> - Estruture a resposta desejada para obter exatamente o formato que você precisa.

## 2. Conceitos Fundamentais sobre IA e LLMs

### 2.1 IA Enviesada (Biased AI)
- Refere-se à tendência de modelos de IA generativa em gerar respostas tendenciosas ou discriminatórias.
- Essa tendência é baseada em dados de treinamento que contêm vieses históricos ou sociais.
- Os modelos de IA aprendem com textos humanos, portanto, herdam os vieses presentes nesses textos.

> [!CAUTION] OBSERVAÇÃO:
> - O viés em IA não se refere à incapacidade de aprender ou à falta de ética, mas sim à reprodução de preconceitos existentes nos dados de treinamento.

### 2.2 ChatGPT
- É desenvolvido pela OpenAI, laboratório de pesquisas em inteligência artificial.
- Utiliza IA para interagir com os usuários por meio de textos.
- Apresenta uma variedade ampla de respostas, incluindo textos, imagens, apresentações (PPT), códigos, entre outros formatos.

> [!TIP] DICAS:
> - O ChatGPT foi lançado em novembro de 2022 e recebeu apoio da Microsoft.
> - O principal concorrente do ChatGPT é o Google Bard (atualmente chamado de Gemini).

### 2.3 Alucinação em IA
- A alucinação ocorre quando a IA cria respostas ao prever a palavra mais lógica que vem a seguir em uma frase.
- Esse processo pode resultar na geração de palavras ou informações incorretas.
- A alucinação é considerada um dos maiores problemas do ChatGPT atualmente.

> [!CAUTION] OBSERVAÇÃO:
> - A alucinação não é um erro deliberado, mas uma limitação do modelo preditivo.
> - Pode gerar informações falsas que parecem plausíveis, exigindo verificação humana.

### 2.4 GPT-3
- O GPT-3 (Generative Pre-trained Transformer 3) é um algoritmo capaz de gerar diversos tipos de informação.
- Uma de suas principais capacidades é escrever textos semelhantes aos escritos por humanos.
- O GPT-3 não é especializado em resolver problemas matemáticos complexos, prestar assessoramento jurídico preciso ou fazer atendimentos médicos sem supervisão.

## 3. Aplicações e Implicações dos LLMs

### 3.1 Sistemas de Informação com Interface Natural
- Sistemas que utilizam interface natural, como o ChatGPT, são classificados como Sistemas Inteligentes de Apoio à Decisão (IA).
- Esses sistemas permitem interação em linguagem natural, facilitando o acesso e a análise de informações.

### 3.2 Ferramentas Concorrentes
- Google Bard (atualmente Gemini) é o chatbot de IA desenvolvido pelo Google para concorrer com o ChatGPT.
- O Bard foi disponibilizado ao público com o objetivo de competir no mercado de assistentes virtuais baseados em IA.

> [!TIP] DICAS:
> - O Bing, da Microsoft, também é um concorrente, mas integra IA em seu mecanismo de busca.
> - Colorize e Replika são outras ferramentas de IA, mas não são concorrentes diretos do ChatGPT no mesmo segmento.

### 3.3 Impactos e Preocupações
- A criação do ChatGPT revolucionou a inteligência artificial, mas trouxe preocupações significativas.
- Antes, uma opinião social, econômica ou política era expressa por uma pessoa; hoje, pode ser um robô que esboça artificialmente um argumento.
- A automação de tarefas e a geração de conteúdo podem favorecer a produtividade, mas também geram desafios éticos e de veracidade.

> [!CAUTION] OBSERVAÇÃO:
> - É fundamental verificar a autenticidade e a fonte das informações geradas por IA.
> - O uso indiscriminado de IA pode levar à desinformação e à manipulação de opiniões.