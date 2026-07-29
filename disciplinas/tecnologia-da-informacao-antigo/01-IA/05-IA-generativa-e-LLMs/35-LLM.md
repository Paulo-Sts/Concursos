# Anotações – Modelos de Linguagem de Larga Escala (LLMs)

## 1. O que são LLMs?

- **LLM (Large Language Model)** – Modelo de Linguagem de Larga Escala.
- São **redes neurais profundas** com milhares de camadas de neurônios, treinadas com quantidades **gigantescas** de textos.
- **Capacidades:** generalizam e promovem o raciocínio em linguagem natural.
- **Aplicações:** geram textos, resumos, traduções e códigos em linguagem de programação.
- **Ajuste para tarefas específicas:** pode ser feito via:
  - **Fine-tuning:** ajuste fino do modelo com exemplos específicos (com supervisão humana).
  - **Engenharia de prompt:** construção de prompts específicos para guiar a resposta.

> ### 1.1 O que roda por trás das IAs conversacionais?
> - **ChatGPT, Gemini, Copilot** – todos rodam um **LLM** por baixo.

## 2. Características Técnicas dos LLMs

| CARACTERÍSTICA | DESCRIÇÃO |
| --- | --- |
| **Baseados em Transformers** | Arquitetura Transformer (2017). Utiliza **mecanismo de atenção** para focar nas palavras mais importantes. Permite paralelismo no treinamento e lida com dependências de longo prazo. |
| **Autorregressivos** | Geram **token por token** (palavra por palavra). Preveem o próximo token dado o contexto e as palavras anteriores. Processo sequencial e lento. |
| **Treinamento não supervisionado** | Aprendem com grandes volumes de texto sem rótulos. Usam **next-token prediction** e **masked language modeling**. |
| **Domínio amplo** | Capazes de conversar sobre diversos temas – da culinária à TI, em múltiplos idiomas. |
| **Escalabilidade** | Quanto mais dados e parâmetros, melhor o desempenho. Habilidades emergentes surgem com o aumento de escala. |
| **Inferência sequencial** | Processam token por token (exceto BERT). Isso torna a geração mais lenta. |
| **Sensíveis ao contexto** | Possuem **janelas de contexto** que armazenam informações sobre o usuário e o histórico da conversa. |
| **Podem alucinar** | Geram informações convincentes, mas incorretas ou imprecisas. Crítico em áreas como direito, medicina e educação. |
| **Exigem muita infraestrutura** | Treinamento caro – exige GPUs, TPUs. Grandes empresas (OpenAI, Google) ou órgãos públicos (ex.: CGU com a LIA) desenvolvem seus próprios LLMs. |
| **Sensíveis a dados pessoais e éticos** | Podem ser treinados com dados públicos ou com interações dos usuários. Riscos de privacidade e uso indevido. |

## 3. Detalhamento das Características

### 3.1 Arquitetura Transformer

- **Mecanismo de atenção:** permite que o modelo foque nas palavras mais relevantes de um texto.
- **Paralelismo:** diferente de RNNs/LSTMs, o Transformer processa sequências em paralelo, tornando o treinamento mais eficiente.
- **Dependências de longo prazo:** o Transformer lida melhor com contextos longos.

> ### 3.1.1 RAG (Retrieval-Augmented Generation)
> - Técnica que combina LLMs com bases de dados externas para evitar que o modelo "esqueça" informações.
> - A IA consulta uma base de dados para responder perguntas específicas.

### 3.2 Treinamento não supervisionado

- **Next-token prediction:** o modelo aprende a prever a próxima palavra com base nas anteriores.
- **Masked language modeling:** palavras são mascaradas e o modelo tenta adivinhar qual palavra se encaixa (ex.: BERT).

### 3.3 Alucinações

- O modelo gera respostas que **parecem verdadeiras** mas são **incorretas**.
- **Risco:** pode confundir o usuário e levar a erros em estudos ou decisões.

> ### 3.3.1 Recomendação para concursos
> 1. **Aprender:** assista videoaulas e leia o PDF.
> 2. **Revisar:** use IA para criar resumos e mapas mentais (corrigindo possíveis erros).
> 3. **Resolver questões:** pratique com questões de concursos.
> - A IA é excelente para criar **questões e simulados**.

## 4. Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **LLM** | Modelo de linguagem de larga escala (redes neurais profundas). |
| **Transformer** | Arquitetura com mecanismo de atenção. |
| **Autorregressivo** | Gera token por token (palavra por palavra). |
| **Next-token prediction** | Previsão da próxima palavra no treinamento. |
| **Alucinação** | Geração de respostas incorretas, mas convincentes. |
| **Fine-tuning** | Ajuste do modelo com exemplos específicos. |
| **Engenharia de Prompt** | Criação de prompts para guiar a resposta. |
| **RAG** | Consulta a base de dados externa para evitar esquecimento. |
| **Janela de contexto** | Quantidade de informações que o modelo pode processar de uma vez. |

---

*Material complementar à aula "LLM – Modelos de Linguagem de Larga Escala" (professor Vitor Kessler/Gran Concursos).*