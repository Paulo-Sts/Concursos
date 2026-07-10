# Anotações – Grandes Modelos de Linguagem (LLM) e IA Generativa II

## 1. Ética na IA Generativa (revisão e aprofundamento)

| QUESTÃO ÉTICA | DESCRIÇÃO |
| --- | --- |
| **Deep Fake e manipulação de mídia** | Criação de imagens/vídeos/áudios falsos realistas. |
| **Violação de privacidade** | Uso indevido de dados pessoais para treinar modelos. |
| **Viés e discriminação** | Reflexo de preconceitos presentes nos dados de treinamento. |
| **Direitos autorais** | Quem detém os direitos sobre conteúdo gerado por IA? |
| **Perda de emprego** | Automação de tarefas anteriormente humanas. |
| **Manipulação de eleições** | Uso de IA para gerar desinformação política. |
| **Uso de identidade falsa** | Criação de perfis e identidades fictícias. |
| **Manipulação emocional** | Uso de IA para influenciar emoções e opiniões. |
| **Desigualdade digital** | Acesso desigual a tecnologias de IA. |
| **Ataques cibernéticos** | Uso de IA para gerar ataques mais sofisticados. |

## 2. Tecnologias de IA Generativa

### 2.1 Redes Adversariais Generativas (GANs)

- **GAN (Generative Adversarial Network):** duas redes neurais competem entre si:
  - **Criadora (Generator):** gera conteúdo falso (imagens, áudio, etc.).
  - **Discriminadora (Discriminator):** tenta distinguir conteúdo real do falso.
- A criadora melhora continuamente até que a discriminadora não consiga mais diferenciar o real do falso.
- **Aplicações:** geração de imagens realistas, deepfakes, criação de arte.

### 2.2 Modelos de Linguagem (LLMs)

- **GPT (Generative Pre-trained Transformer):** modelo de linguagem da OpenAI.
- **ChatGPT:** variante do GPT otimizada para **conversação**.
- **Bing Chat:** IA da Microsoft integrada ao Bing.
- **Google Bard (atualmente Gemini):** IA generativa do Google.

> ### 2.2.1 ChatGPT
> - **Capacidades:** compreende e responde a solicitações em linguagem natural; pode fornecer informações, realizar tarefas específicas ou engajar em diálogo casual.
> - **Integração com Microsoft:** pode gerar pptx, docx, excel, programação, pesquisa na internet, etc.
> - **Limitações:**
>   - Conhecimento atualizado apenas até a data de corte do treinamento.
>   - Perda de compreensão contextual em textos longos.
>   - Presença de vieses.
>   - Alucinações (informações imprecisas ou falsas).
>   - Interpretação literal (pode não captar nuances).

## 3. Treinamento do ChatGPT

| TIPO DE TREINAMENTO | DESCRIÇÃO |
| --- | --- |
| **Aprendizado supervisionado** | Alimentado com pares de perguntas e respostas para aprender a predizer respostas adequadas. |
| **Aprendizado por reforço** | Ajusta respostas com base em feedback humano (RLHF – Reinforcement Learning from Human Feedback). |

## 4. Engenharia de Prompt

### 4.1 Conceito

- **Engenharia de Prompt:** técnica de formular perguntas/instruções para obter respostas mais precisas e relevantes de modelos de IA generativa.
- É uma habilidade essencial para extrair o melhor desempenho de LLMs como ChatGPT.

### 4.2 Exemplo de Prompt (classificação de sentimento)

```
P: Tweet: "Que dia lindo!" Este tweet é positivo ou negativo?
R: positivo

P: Tweet: "Eu odeio esta aula" Este tweet é positivo ou negativo?
R: negativo

P: Tweet: "Eu amo bolsos em calças"
R: positivo
```

- O modelo aprende com os exemplos fornecidos (few-shot learning).

### 4.3 Orientações para Elaboração de Prompts Eficazes

| ORIENTAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Especificidade** | Seja claro e específico sobre o que deseja. |
| **Contexto** | Forneça contexto suficiente para a IA entender a solicitação. |
| **Estilo** | Defina o estilo de resposta desejado (formal, informal, técnico, etc.). |
| **Palavras-chave** | Use palavras-chave relevantes para direcionar a resposta. |
| **Estruture a resposta desejada** | Indique o formato esperado (lista, parágrafo, tabela, etc.). |
| **Adequação ao domínio** | Especifique a área de conhecimento (jurídico, médico, TI, etc.). |
| **Mitigação de viés** | Peça que a IA evite vieses e ofereça respostas equilibradas. |
| **Analogias** | Use analogias para explicar conceitos complexos. |
| **Use exemplos** | Forneça exemplos (zero-shot, one-shot, few-shot). |
| **Passo a passo** | Peça que a IA explique o raciocínio passo a passo. |

### 4.4 Tipos de Aprendizado por Exemplo

| TIPO | DESCRIÇÃO |
| --- | --- |
| **Zero-shot** | Nenhum exemplo é fornecido – o modelo usa apenas o conhecimento prévio. |
| **One-shot** | Um exemplo é fornecido para orientar a resposta. |
| **Few-shot** | Vários exemplos são fornecidos para melhorar a precisão. |

## 5. Questão de Concurso Comentada

### 5.1 (IESES/2023/SC GÁS – Analista de Sistemas)

**Item:** "Assinale a alternativa correta que apresenta ferramentas de IA."

**Alternativas:**
- a) Bing Chat, Google Bard, ChatGPT.
- b) Bing Chat, Google Bard, OpenGPT.
- c) ChatGPT, Bing Chat, Alxp.
- d) ChatGPT, Google Bard, MeetAI.

**Gabarito: a) Bing Chat, Google Bard, ChatGPT.**

**Comentário:** Bing Chat (Microsoft), Google Bard (Google) e ChatGPT (OpenAI) são as principais ferramentas de IA generativa baseadas em LLMs.

---

## GABARITO DA QUESTÃO

| QUESTÃO | GABARITO |
| --- | --- |
| 001 (IESES/2023) | a |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **GAN** | Duas redes neurais competem (criadora × discriminadora). |
| **ChatGPT** | Variante do GPT otimizada para conversação. |
| **GPT** | Modelo de linguagem generativo da OpenAI. |
| **Bing Chat** | IA da Microsoft integrada ao Bing. |
| **Google Bard (Gemini)** | IA generativa do Google. |
| **Engenharia de Prompt** | Técnica de formular perguntas para obter melhores respostas. |
| **Zero-shot** | Nenhum exemplo fornecido. |
| **One-shot** | Um exemplo fornecido. |
| **Few-shot** | Vários exemplos fornecidos. |

---

*Material complementar à aula "Grandes Modelos de Linguagem (LLM) e IA Generativa II" (professor Vitor Kessler/Gran Concursos).*