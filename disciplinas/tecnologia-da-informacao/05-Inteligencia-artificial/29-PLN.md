# PLN 

## 1. Conceito de Processamento de Linguagem Natural
- O PLN é um campo da inteligência artificial que busca permitir que computadores compreendam, interpretem e gerem linguagem humana escrita ou falada.
- É o algoritmo que reconhece a voz (áudio) e a transforma em texto.
- A entrada também pode ser o próprio texto. Por exemplo, um áudio para o ChatGPT é transformado em texto e, depois, a IA generativa considera o texto gerado para desenvolver a resposta.
- O PLN conecta:
  - Linguística;
  - Estatística;
  - Machine Learning;
  - Redes Neurais;
  - Computação.
- O objetivo é fazer máquinas entenderem textos como nós entendemos, ainda que isso seja extremamente complexo.

### 1.1 Desafios do PLN
- A linguagem humana apresenta características que dificultam o processamento por máquinas:
  - Ambiguidade: palavras com múltiplos significados (ex.: "sinistro" pode ser colisão de veículos ou algo muito bom; "manga" pode ser parte da blusa ou fruta);
  - Ironia;
  - Contexto cultural: varia regionalmente (ex.: "pai d'égua" em Belém significa algo bom, diferindo do contexto do Sudeste);
  - Polissemia: palavras com múltiplos sentidos;
  - Dependências longas dentro do texto;
  - Erros de digitação, gírias, variações, ruídos, pronomes neutros etc.

> [!TIP] DICAS:
> - O grande desafio do PLN está na ambiguidade da linguagem humana, que dificulta a interpretação precisa pelas máquinas.

> [!CAUTION] OBSERVAÇÃO:
> - Apesar dos desafios, atualmente é possível gerar e compreender texto de qualidade com PLN.

## 2. Etapas do PLN
- Coleta: é preciso coletar os dados.
- Pré-processamento: tem como objetivo diminuir a quantidade de palavras que serão processadas.
- Vetorização (representação): representar texto para uma rede que trabalha somente com números; geralmente, esse texto é transformado em um vetor numérico.
- Modelagem.

## 3. Aplicações Clássicas de PLN
- Chatbots e assistentes virtuais (ex.: Alexa);
- Análise de sentimento: permite classificar o texto como positivo, negativo ou neutro. Pode ser usado no e-commerce nos comentários dos consumidores que adquiriram o produto.
  - As redes sociais analisam sentimento em tudo o que é postado. Por exemplo, ao tecer comentários positivos no Instagram acerca de um determinado político, a rede social interpreta o texto e passa a alimentar a bolha desse usuário com pessoas que têm o mesmo pensamento. Contudo, é possível que o Instagram comece a inserir postagens de políticos adversários, para que o usuário confirme a opção política. Essa é uma forma de manipular o usuário, engajar comentários e postagens, e, com isso, arrecadar mais recursos com propagandas.
- Tradução automática;
- Corretores ortográficos;
- Busca inteligente;
- Sistemas de recomendação;
- Extração de informação em documentos: pode obter informações sobre o documento apresentado;
- Geração de relatórios automáticos.

| APLICAÇÃO | DESCRIÇÃO |
|-----------|-----------|
| Chatbots e assistentes virtuais | Exemplo: Alexa |
| Análise de sentimento | Classifica texto como positivo, negativo ou neutro |
| Tradução automática | Traduz textos entre idiomas |
| Corretores ortográficos | Corrige erros de escrita |
| Busca inteligente | Melhora a relevância dos resultados de busca |
| Sistemas de recomendação | Sugere conteúdos com base em análise textual |
| Extração de informação em documentos | Obtém informações estruturadas de documentos |
| Geração de relatórios automáticos | Cria relatórios a partir de dados textuais |

> [!CAUTION] OBSERVAÇÃO:
> - A análise de sentimento em redes sociais pode ser usada para manipular usuários, engajar comentários e postagens, e arrecadar mais recursos com propagandas.

## 4. Paradigmas do PLN

### 4.1 Paradigma Simbólico (Baseado em Regras)
- Ideia central:
  - Regras eram escritas por especialistas e explicitamente programadas.
  - O conhecimento da língua é explicitamente programado por especialistas.
- Como funciona:
  - Regras gramaticais explícitas;
  - Dicionários, léxicos e ontologias;
  - Árvores sintáticas;
  - Gramáticas formais.
- Tudo isso vai extrair o conteúdo do texto que for digitado.

### 4.2 Paradigma Estatístico (Aprendizado Probabilístico)
- Ideia central:
  - A linguagem é tratada como um fenômeno estatístico.
  - O computador aprende padrões a partir de grandes quantidades de texto.
- Como funciona – usa técnicas como:
  - Naive Bayes;
  - TF-IDF.

### 4.3 Paradigma Neural (Aprendizado Profundo)
- Ideia central:
  - A linguagem é representada como vetores densos (vetores com poucas colunas) que capturam significado.
  - O computador aprende representações distribuídas, não regras.
  - Durante o treinamento, a rede neural vai aprender representações desses textos, e não regras.
- Tecnologias principais:
  - Word embeddings (Word2Vec, GloVe);
  - RNN, LSTM, GRU;
  - CNN para texto;
  - Transformers (BERT, GPT, T5, LLaMA...).

> [!CAUTION] OBSERVAÇÃO:
> - O PLN combina os três paradigmas: simbólico (baseado em regras), estatístico e neural.
> - Modelos recentes como Gemini e GPT também são PLN, baseados no paradigma neural.