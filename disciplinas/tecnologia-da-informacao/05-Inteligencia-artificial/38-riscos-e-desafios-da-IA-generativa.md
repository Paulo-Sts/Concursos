# Riscos Associados à IA Generativa

## 1. Principais Riscos

### 1.1 Desinformação
- A IA generativa pode criar fake news com aparência realista, dificultando a distinção entre conteúdo verdadeiro e fabricado.
- Geração de deepfakes, que incluem áudio, vídeo e imagens manipuladas com alta qualidade e semelhança ao original.
- Risco à democracia e à confiança pública, especialmente quando utilizado em contexto eleitoral para disseminar informações falsas.
- Exemplo: deepfakes podem colocar vozes e imagens de pessoas em contextos falsos, criando uma mídia realista de situações que não ocorreram.

### 1.2 Violação de Direitos Autorais
- Uso de obras protegidas por direitos autorais sem autorização durante o treinamento dos modelos de IA.
- Geração de textos, imagens ou músicas que imitam estilos ou trechos originais protegidos.
- Dificuldade em atribuir autoria ao conteúdo gerado pela IA.
- Explicação: IAs generativas de texto, como o ChatGPT, recebem bases de treinamento com praticamente todos os textos indexados no Google, incluindo obras protegidas. A máquina não é um motor de busca; ela entende probabilidades. Já nas IAs generativas de imagem, só é possível gerar imagens representativas se houver imagens reais protegidas por direitos autorais na base de dados de treinamento. Nos Estados Unidos, há disputas judiciais intensas sobre esse tema.

### 1.3 Vieses e Discriminação
- A máquina aprende a partir de bases de dados históricas criadas por humanos, que contêm preconceitos como racismo e misoginia.
- A IA pode reforçar racismo, machismo, elitismo e outras formas de discriminação.
- Exemplo 1: Nos Estados Unidos, uma IA utilizada para prever penas atribuiu sentenças mais altas para pessoas negras do que para pessoas brancas pelo mesmo crime.
- Exemplo 2: Ao gerar imagens de um caixa de supermercado, a IA apresenta majoritariamente mulheres negras; ao gerar imagens de uma pessoa indo para o trabalho de carro, apresenta majoritariamente homens brancos com carros "chiques".
- Impacto negativo em decisões automatizadas nas áreas de contratação, concessão de crédito e justiça criminal.

### 1.4 Impacto no Mercado de Trabalho
- Automação de tarefas criativas e analíticas que antes exigiam intervenção humana.
- Risco de substituição de empregos em áreas como:
  - Jornalismo;
  - Design (criação de imagens);
  - Atendimento ao cliente (apenas demandas não resolvidas pela IA são encaminhadas a humanos);
  - Programação.
- Desafio para a requalificação profissional dos trabalhadores afetados.

### 1.5 Exposição de Dados Sensíveis
- IAs podem coletar ou inferir informações pessoais durante interações com usuários.
- Durante o treinamento, há uma quantidade absurda de dados pessoais disponíveis na internet, que são incorporados aos modelos.
- Riscos de violação de leis de proteção de dados, como a LGPD no Brasil e a GDPR na Europa.
- Necessidade de transparência e controle na coleta, armazenamento e uso de dados pessoais.

> [!CAUTION] OBSERVAÇÃO:
> - O principal desafio relacionado à exposição de dados sensíveis é que as IAs podem armazenar e inferir informações sem o consentimento explícito do usuário, violando princípios fundamentais da LGPD e da GDPR.

## 2. Como Mitigar esses Riscos?
- Regulação ética e transparente para orientar o desenvolvimento e uso da IA.
- Auditorias regulares em modelos de IA para identificar e corrigir vieses, vulnerabilidades e falhas de segurança.
- Educação digital da sociedade, garantindo que mais pessoas conheçam e utilizem a IA generativa para não ficarem excluídas digitalmente.
- Desenvolvimento responsável por parte das empresas que criam e implementam sistemas de IA.

> [!TIP] DICAS:
> - Quem não usa IA está excluído digitalmente, assim como muitas pessoas que não têm acesso a computadores.
> - A regulação e a auditoria são ferramentas essenciais para garantir que a IA seja utilizada de forma ética e segura.

## 3. Etapas do Treinamento de IA Generativa

- Primeira etapa (aprendizado não supervisionado): os dados são fornecidos à máquina, que aprende estatísticas e identifica palavras importantes em cada texto.
- Segunda etapa (ajuste fino ou fine-tuning): a máquina pré-treinada recebe textos e respostas apropriadas para ensinar domínios específicos.
- Terceira etapa (aprendizado por reforço com feedback humano - RLHF): o modelo é treinado a partir de respostas corrigidas por humanos, melhorando a precisão e reduzindo alucinações e vieses.

> [!TIP] DICAS:
> - O fine-tuning é útil para adaptar a IA a áreas específicas, como direito ou medicina, usando conjuntos de dados menores e mais direcionados.
> - O RLHF é amplamente utilizado para refinar a qualidade das respostas de modelos como o ChatGPT.

## 4. Técnicas para Mitigação de Riscos em Modelos de IA
- Fairness-aware learning: abordagem para corrigir potenciais vieses no modelo, garantindo recomendações justas para todos os grupos de usuários.
- Robustness testing: simulação de ataques adversariais para avaliar a resiliência do modelo e auditorias regulares para identificar e corrigir vieses algorítmicos.
- Data augmentation: criação de dados de treinamento com maior diversidade para reduzir o risco de viés algorítmico.
- Differential privacy: técnica para proteger dados sensíveis durante o treinamento, garantindo que as previsões do modelo não revelem informações específicas dos clientes.
- Monitoramento contínuo: estratégia para detectar e mitigar ataques adversariais e vieses emergentes.

> [!TIP] DICAS:
> - Sistemas de recomendação, como o da Amazon, baseiam-se em históricos de consumo e devem adotar essas técnicas para evitar discriminação e exposição de dados.
> - A combinação de fairness-aware learning, robustness testing, data augmentation, differential privacy e monitoramento contínuo é essencial para garantir modelos éticos e seguros.