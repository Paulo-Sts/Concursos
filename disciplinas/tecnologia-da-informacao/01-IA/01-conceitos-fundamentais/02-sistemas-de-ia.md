# Anotações – Sistemas de IA

## 1. O que é um Sistema de IA?

- **Sistema computacional** (software, com ou sem hardware embarcado) capaz de realizar tarefas que normalmente exigiriam **inteligência humana**, como:
  - Tomar decisões.
  - Entender linguagem natural.
  - Reconhecer padrões visuais ou sonoros.
  - Aprender com dados.

> ### 1.1 Exemplo prático
> - Criar uma máquina para prever se uma transação de cartão de crédito é fraudulenta ou não envolve um processo de **aprendizado de máquina**.

## 2. Componentes Principais

| COMPONENTE | DESCRIÇÃO |
| --- | --- |
| **Entrada (Input)** | Dados estruturados ou não estruturados (texto, imagem, sensores). |
| **Processamento** | Modelos baseados em regras, algoritmos estatísticos ou aprendizado de máquina. |
| **Saída (Output)** | Previsão, recomendação, decisão, classificação, etc. |

### 2.1 Processo de Treinamento de um Sistema de IA

1. **Construção do dataset** (base de dados).
2. **Divisão do dataset:**
   - Parte maior para **treinamento**.
   - Parte menor (ex.: ¼) para **teste**.
3. O conjunto de treinamento é entregue a um **indutor**, que gera o modelo de IA treinado.
4. **Teste:** dados que o modelo nunca viu são usados para verificar o percentual de acerto.
5. O sistema passa a receber dados do mundo real.

## 3. Tipos de Sistema de IA

| TIPO | DESCRIÇÃO | EXEMPLO |
| --- | --- | --- |
| **Baseados em regras** | Lógica definida manualmente por humanos. | Sistemas especialistas. |
| **Aprendizado de máquina** | Aprendem padrões a partir de dados históricos. | Redes neurais, regressão, etc. |
| **Híbridos** | Combinam regras fixas com aprendizado automático. | Chatbots modernos. |

> ### 3.1 Chatbots (comparação)
> - **Sistema especialista:** o programador define todas as regras do diálogo.
> - **Sistema de IA:** treina-se a máquina com chats antigos realizados por atendentes humanos.

## 4. Níveis de Autonomia

| NÍVEL | DESCRIÇÃO |
| --- | --- |
| **Com supervisão humana** | O sistema recomenda, mas o humano decide. |
| **Intermediário** | Sistemas que tomam decisões, mas sob revisão eventual. |
| **Autônomo** | Atuam sem intervenção humana constante. |

## 5. Questões de Concurso Comentadas

### 5.1 (FUNDATEC/2025/IF FARROUPILHA – Professor)

**Item:** "Ciência e engenharia de construir e tornar máquinas inteligentes... A inteligência exibida por máquinas... estudo de agentes inteligentes... simula funções associadas à mente humana, como aprendizagem e resolução de problemas."

**Gabarito: d) Inteligência artificial (IA).**

**Comentário:** A definição refere-se diretamente à Inteligência Artificial. Data Science trata da extração de conhecimento a partir de dados.

### 5.2 (QUADRIX/2022/CRT-04 – Assistente de TI)

**Item:** "O conceito de inteligência artificial (IA) refere-se, unicamente, a duas grandes áreas do conhecimento: ciência da computação e matemática."

**Gabarito: Errado (E).**

**Comentário:** A IA é **multidisciplinar** e envolve outras áreas como engenharia, medicina, psicologia, etc.

### 5.3 (QUADRIX/2023/CRO-SC – Técnico em Informática)

**Item:** "A inteligência artificial refere-se a um campo de conhecimento que não está associado à aprendizagem..."

**Gabarito: Errado (E).**

**Comentário:** A IA **está associada à aprendizagem** – o aprendizado de máquina é um de seus pilares.

### 5.4 (FGV/2024/PREFEITURA DE CARAGUATATUBA – Técnico)

**Itens:**
- ( ) A IA é uma tecnologia disruptiva que tem o potencial de mudar o mundo. **(V)**
- ( ) A IA é utilizada em diversas aplicações práticas, como carros autônomos, assistentes virtuais e sistemas de recomendação. **(V)**
- ( ) A IA não apresenta riscos éticos... **(F)** – IA apresenta riscos éticos (vieses, discriminação, etc.).

**Gabarito: e) V – V – F.**

### 5.5 (FGV/2024/CÂMARA DOS DEPUTADOS – Analista)

**Item:** "Em relação ao potencial de discriminação ilícita ou abusiva em sistemas de IA, assinale a afirmação mais precisa."

**Gabarito: c) A IA pode inadvertidamente discriminar com base nos dados em que foi treinada.**

**Comentário:**
- Sistemas de IA aprendem padrões a partir de dados históricos – se os dados contiverem vieses, a IA pode perpetuar discriminações.
- Não é necessário haver intenção explícita do programador.

### 5.6 (QUADRIX/2023/CRT-BA – Assistente de TI)

**Item:** "A IA envolve a criação de algoritmos e modelos que permitem que as máquinas processem informações, aprendam com dados, tenham consciência, emoções ou intuição humana..."

**Gabarito: Errado (E).**

**Comentário:** A IA **não** possui consciência, emoções ou intuição humana – isso seria característica de uma **superinteligência** ou IA autoconsciente, ainda no campo da hipótese.

### 5.7 (CESPE/CEBRASPE/2023/DATAPREV – Analista)

**Item:** "A inteligência artificial é um sistema com capacidade de ponderar, aprender e agir para resolver um problema complexo."

**Gabarito: Errado (E).**

**Comentário:** A IA pode ser usada para resolver problemas complexos, mas a definição de "sistema com capacidade de ponderar, aprender e agir" não é precisa para todos os tipos de IA (ex.: sistemas baseados em regras não aprendem).

### 5.8 (FGV/2021/TJ-RO – Analista de Sistemas)

**Item:** "Tecnologia que possui a capacidade de melhorar o desempenho na realização de alguma tarefa por meio da experiência usando dados de treinamento, podendo ser supervisionado ou não, é o(a):"

**Gabarito: e) Aprendizado de Máquina (Machine Learning).**

**Comentário:**
- **Motor de Inferência:** usado em sistemas especialistas (regras).
- **Raciocínio Automatizado:** prova de teoremas.
- **Compreensão de Linguagem Natural:** PLN.
- **Representação do Conhecimento:** lógica de primeira ordem.
- **Machine Learning:** aprende com dados de treinamento (supervisionado ou não).

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FUNDATEC/2025) | d |
| 02 (QUADRIX/2022) | E |
| 03 (QUADRIX/2023) | E |
| 04 (FGV/2024) | e |
| 05 (FGV/2024/CÂMARA) | c |
| 06 (QUADRIX/2023) | E |
| 07 (CESPE/2023) | E |
| 08 (FGV/2021) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Sistema de IA** | Sistema computacional que realiza tarefas que exigem inteligência humana. |
| **Componentes** | Entrada → Processamento → Saída. |
| **Treinamento** | Dataset → divisão treino/teste → indutor → modelo treinado → validação. |
| **Tipos de sistema** | Baseados em regras, aprendizado de máquina, híbridos. |
| **Níveis de autonomia** | Supervisão humana → intermediário → autônomo. |
| **Discriminação em IA** | Pode ocorrer devido a vieses nos dados de treinamento. |
| **Machine Learning** | Subárea da IA que aprende com dados (supervisionado ou não). |

---

*Material complementar à aula "Sistemas de IA" (professor Washington Henrique Almeida/Gran Concursos).*