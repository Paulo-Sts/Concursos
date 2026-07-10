# Anotações – Riscos e Desafios da IA Generativa

## 1. Principais Riscos da IA Generativa

### 1.1 Desinformação

- **Criação de fake news** com aparência real.
- **Deepfakes** – áudio, vídeo e imagens manipuladas com alta qualidade e semelhança ao original.
- **Risco à democracia e confiança pública** – especialmente em contextos eleitorais.

### 1.2 Violação de Direitos Autorais

- **Uso de obras protegidas** sem autorização nos dados de treinamento.
- **Geração de conteúdo que imita estilos ou trechos originais**.
- **Dificuldade em atribuir autoria** ao conteúdo gerado por IA.
- As IAs generativas aprendem a partir de textos/imagens indexados na internet – muitos protegidos por direitos autorais.

### 1.3 Vieses e Discriminação

- A IA aprende com dados históricos produzidos por humanos – que podem conter **preconceitos (racismo, machismo, elitismo)** .
- **Exemplo (EUA):** IA de previsão de pena de prisão atribuía penas mais altas para pessoas negras do que para pessoas brancas pelo mesmo crime.
- **Exemplo (imagens):** IA gera imagens estereotipadas – "caixa de supermercado" → mulheres negras; "pessoa indo para o trabalho de carro" → homem branco com carro "chique".
- Pode reforçar discriminação em decisões automatizadas (contratação, crédito, justiça).

### 1.4 Impacto no Mercado de Trabalho

| ÁREA AFETADA | IMPACTO |
| --- | --- |
| Jornalismo | Automação de produção de notícias e resumos. |
| Design | Geração de imagens e layouts por IA. |
| Atendimento ao cliente | IA resolve a maioria das demandas; humanos só para casos complexos. |
| Programação | Geração de código por IA. |
| Requalificação profissional | Desafio de adaptar trabalhadores a novas funções. |

### 1.5 Exposição de Dados Sensíveis

- IAs podem **coletar ou inferir informações pessoais** durante interações.
- Riscos de violação da **LGPD (Brasil)** e **GDPR (Europa)** .
- Necessidade de **transparência e controle** na coleta e uso de dados.

## 2. Como Mitigar Esses Riscos?

| ESTRATÉGIA | DESCRIÇÃO |
| --- | --- |
| **Regulação ética e transparente** | Criação de leis e diretrizes para o uso responsável da IA. |
| **Auditorias em modelos de IA** | Verificação regular para identificar e corrigir vieses. |
| **Educação digital da sociedade** | Capacitar as pessoas para usar e compreender a IA. |
| **Desenvolvimento responsável** | Empresas devem adotar práticas éticas no desenvolvimento de IA. |
| **Fairness-aware learning** | Abordagem para corrigir vieses no modelo. |
| **Robustness testing** | Simular ataques adversariais para avaliar a resiliência do modelo. |
| **Data augmentation** | Aumentar a diversidade dos dados de treinamento. |
| **Differential privacy** | Proteger dados sensíveis durante o treinamento. |

## 3. Deepfake

- Tecnologia que **manipula arquivos de áudio e vídeo**, colocando vozes e imagens de pessoas em **contextos falsos**, criando uma mídia realista de uma situação que não aconteceu.
- **Grande preocupação:** uso em campanhas eleitorais, desinformação, difamação.

## 4. Direitos Autorais e IA – Legislação Brasileira

- A legislação brasileira **não institui de forma expressa** proteção autoral para criações desenvolvidas exclusivamente por Inteligência Artificial.
- Há quem defenda que tais obras **pertenceriam ao domínio público**.

## 5. Questões de Concurso Comentadas

### 5.1 (UNESPAR/2025 – Agente Universitário)

**Item:** "Preocupações legais e éticas em torno da IA porque esta é uma tecnologia que:"

**Gabarito: a) usa algoritmos para imitar processos de inteligência humana, como a tomada de decisão e a resolução de problemas.**

### 5.2 (CESPE/INSA/2025 – Tecnologista)

**Item:** "Quando treinada com dados diversos e aplicada com rigor técnico, sua automação neutraliza vieses preexistentes, o que garante equidade para grupos historicamente marginalizados."

**Gabarito: Errado (E).**

**Comentário:** A IA não garante equidade automaticamente – vieses podem persistir ou ser amplificados.

### 5.3 (FCC/TRT-6/2025 – Analista)

**Item:** "Para ajustar o desempenho do modelo e evitar problemas como alucinações e vieses, eles optaram por:"

**Gabarito: c) utilizar Reinforcement Learning from Human Feedback (RLHF) para treinar o modelo a partir de respostas corrigidas por humanos.**

**Comentário:** RLHF é uma técnica usada para alinhar modelos com preferências humanas e reduzir vieses/alucinações.

### 5.4 (CESGRANRIO/BNDES/2024 – Analista)

**Item:** Afirmativas sobre mitigação de riscos em sistemas de recomendação.

**Gabarito: e) I, II, III e IV.**

**Comentário:** Todas as estratégias são válidas: fairness-aware learning, robustness testing, data augmentation, differential privacy.

### 5.5 (QUADRIX/CRQ/2024 – Técnico)

**Item:** "A inteligência artificial evolui a ponto do aparecimento das mensagens chamadas de deep fakes."

**Gabarito: Certo (C).**

### 5.6 (INSTITUTO CONSULPLAN/2024 – Salva Vidas)

**Item:** "Deepfakes são uma tecnologia que:"

**Gabarito: d) manipula arquivos de áudio e vídeo, colocando vozes e imagens de pessoas em contextos falsos, criando uma mídia realista de uma situação que não aconteceu.**

### 5.7 (FGV/CÂMARA DOS DEPUTADOS/2024 – Analista)

**Item:** "Se um sistema de IA criar, de forma autônoma, uma obra artística, assinale a afirmativa correta acerca do detentor dos direitos autorais sobre ela."

**Gabarito: d) A legislação brasileira não institui de forma expressa proteção autoral para criações desenvolvidas exclusivamente por Inteligência Artificial, sendo defendido por alguns que tais obras pertenceriam ao domínio público.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (UNESPAR/2025) | a |
| 02 (CESPE/INSA/2025) | E |
| 03 (FCC/TRT-6/2025) | c |
| 04 (CESGRANRIO/BNDES/2024) | e |
| 05 (QUADRIX/CRQ/2024) | C |
| 06 (CONSULPLAN/2024) | d |
| 07 (FGV/CÂMARA/2024) | d |

---

## Síntese para Revisão Rápida

| RISCO | DESCRIÇÃO |
| --- | --- |
| **Desinformação** | Fake news, deepfakes, manipulação eleitoral. |
| **Direitos autorais** | Uso de obras protegidas, autoria indefinida. |
| **Vieses** | Discriminação racial, de gênero, social. |
| **Impacto no emprego** | Automação de tarefas criativas e analíticas. |
| **Privacidade** | Exposição de dados sensíveis. |
| **Deepfake** | Manipulação realista de áudio e vídeo. |
| **Direitos autorais no Brasil** | Não há proteção expressa para obras geradas por IA. |

---

*Material complementar à aula "Riscos e Desafios da IA Generativa" (professor Vitor Kessler/Gran Concursos).*