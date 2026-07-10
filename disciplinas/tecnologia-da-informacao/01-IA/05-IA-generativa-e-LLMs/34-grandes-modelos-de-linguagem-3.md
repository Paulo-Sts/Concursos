# Anotações – Grandes Modelos de Linguagem (LLM) e IA Generativa III

## 1. Engenharia de Prompt (Revisão e Aprofundamento)

### 1.1 Exemplo de Prompt (classificação de sentimento)

```
P: Tweet: "Que dia lindo!" Este tweet é positivo ou negativo?
R: positivo

P: Tweet: "Eu odeio esta aula" Este tweet é positivo ou negativo?
R: negativo

P: Tweet: "Eu amo bolsos em calças"
R: positivo
```

- O modelo aprende com os exemplos fornecidos (few-shot learning) e classifica corretamente o último tweet como **positivo**.

### 1.2 Orientações para Elaboração de Prompts Eficazes

| ORIENTAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Especificidade** | Seja claro e específico sobre o que deseja. |
| **Contexto** | Quanto mais contexto, mais específica será a resposta. |
| **Estilo** | Defina o estilo de resposta desejado. |
| **Palavras-chave** | Use termos relevantes para direcionar a resposta. |
| **Estruture a resposta desejada** | Indique o formato esperado (lista, parágrafo, tabela). |
| **Adequação ao domínio** | Especifique a área de conhecimento. |
| **Mitigação de viés** | Peça que a IA evite vieses e ofereça respostas equilibradas. |
| **Analogias** | Use analogias para explicar conceitos complexos. |
| **Use exemplos** | Zero-shot, one-shot, few-shot. |
| **Passo a passo** | Peça que a IA explique o raciocínio passo a passo. |

### 1.3 Tipos de Aprendizado por Exemplo

| TIPO | DESCRIÇÃO |
| --- | --- |
| **Zero-shot** | Nenhum exemplo é fornecido. |
| **One-shot** | Um exemplo é fornecido. |
| **Few-shot** | Vários exemplos são fornecidos. |

## 2. ChatGPT – Características e Limitações

### 2.1 Desenvolvedor

- **ChatGPT** é desenvolvido pela **OpenAI**.
- Utiliza IA para interagir com os usuários por meio de **textos**, imagens, códigos, etc.

### 2.2 Limitações e Desvantagens

| LIMITAÇÃO | DESCRIÇÃO |
| --- | --- |
| **Alucinações** | O modelo pode gerar respostas incorretas ou inventadas. |
| **Viés** | Respostas podem refletir preconceitos presentes nos dados de treinamento. |
| **Conhecimento desatualizado** | A data de corte limita o conhecimento. |
| **Perda de contexto em textos longos** | Dificuldade em manter coerência em diálogos extensos. |
| **Interpretação literal** | Pode não captar ironia, sarcasmo ou nuances culturais. |

> ### 2.2.1 Alucinação
> - O ChatGPT cria respostas ao **prever a palavra mais lógica que vem a seguir** em uma frase.
> - Isso pode resultar em respostas incorretas, que parecem plausíveis – o fenômeno é chamado de **alucinação**.

## 3. Principais Ferramentas de IA Generativa

| FERRAMENTA | DESENVOLVEDOR | DESCRIÇÃO |
| --- | --- | --- |
| **ChatGPT** | OpenAI | Modelo de linguagem para conversação. |
| **Bing Chat** | Microsoft | IA integrada ao mecanismo de busca Bing. |
| **Bard (agora Gemini)** | Google | Chatbot de IA do Google. |
| **GPT-3 / GPT-4** | OpenAI | Modelos de linguagem generativos. |

## 4. Questões de Concurso Comentadas

### 4.1 (FGV/2023/SEDUC-SP – Professor)

**Item:** "O termo 'biased AI' (IA enviesada) na IA generacional significa:"

**Gabarito: b) Refere-se à tendência de modelos de IA geracional em gerar respostas tendenciosas ou discriminatórias com base em dados de treinamento enviesados.**

### 4.2 (OBJETIVA/2024/PREFEITURA DE NOVA ROMA DO SUL – Assistente Social)

**Item:** "ChatGPT é desenvolvido pela OpenAI, que usa IA para interagir com os usuários. Apresenta uma variedade maior de respostas, e estas são realizadas por textos."

**Gabarito: a.**

### 4.3 (FGV/2023/PREFEITURA DE SÃO JOSÉ DOS CAMPOS – Agente)

**Item:** "Uma desvantagem atribuída ao ChatGPT:"

**Gabarito: b) Cria respostas ao prever a palavra mais lógica que vem a seguir numa frase, podendo ser a palavra incorreta.**

**Comentário:** Isso é a **alucinação** – um dos maiores problemas do ChatGPT.

### 4.4 (COSEAC/2023/UFF – Técnico)

**Item:** "Sistema que utilize uma interface natural tal como o ChatGPT."

**Gabarito: c) Sistema Inteligente de Apoio a Decisão (IA).**

### 4.5 (OBJETIVA/2023/PREFEITURA DE ILÓPOLIS – Analista de TI)

**Item:** "Chatbot de IA do Google para concorrer com o ChatGPT."

**Gabarito: c) Bard.** (atualmente chamado de Gemini).

### 4.6 (QUADRIX/2023/CREFONO 2 – Assistente)

**Item:** "O ChatGPT pode gerar grande preocupação, pois o que antes era uma pessoa expressando sua opinião, agora pode ser apenas um robô que esboça artificialmente um argumento."

**Gabarito: Certo (C).**

### 4.7 (AMEOSC/2023/PREFEITURA DE TUNÁPOLIS – Médico)

**Item:** "O GPT-3 é capaz de:"

**Gabarito: c) Escrever textos semelhantes aos escritos pelos humanos.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/SEDUC-SP/2023) | b |
| 02 (OBJETIVA/2024) | a |
| 03 (FGV/SÃO JOSÉ/2023) | b |
| 04 (COSEAC/UFF/2023) | c |
| 05 (OBJETIVA/2023) | c |
| 06 (QUADRIX/2023) | C |
| 07 (AMEOSC/2023) | c |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **ChatGPT** | IA da OpenAI para conversação. |
| **Bing Chat** | IA da Microsoft. |
| **Bard / Gemini** | IA do Google. |
| **Alucinação** | Geração de respostas incorretas pela IA. |
| **Viés** | Reflexo de preconceitos dos dados de treino. |
| **Engenharia de Prompt** | Técnica de formular perguntas para melhores respostas. |
| **Few-shot** | Vários exemplos no prompt. |
| **Zero-shot** | Nenhum exemplo no prompt. |

---

*Material complementar à aula "Grandes Modelos de Linguagem (LLM) e IA Generativa III" (professor Vitor Kessler/Gran Concursos).*