# Anotações – Tipos de Aprendizado III (Mapa Mental e Algoritmos)

## 1. Aprendizado Semissupervisionado

- Dataset **parcialmente rotulado** (poucos dados rotulados, muitos não rotulados).
- **Processo:**
  1. Treina-se uma IA com os dados rotulados (supervisionado).
  2. Essa IA prevê os rótulos dos dados não rotulados.
  3. Treina-se uma nova IA com **todos os dados agora rotulados**.
  4. A nova IA é usada para previsões no problema real.
- **Utilidade:** reduz o custo de rotulação manual.

## 2. Aprendizado por Transferência

- Um modelo treinado em uma tarefa é usado para **ajudar em outra tarefa relacionada**.
- **Processo:**
  1. Treina-se um modelo genérico com dados amplos (ex.: ChatGPT com toda a internet).
  2. Adicionam-se dados específicos (ex.: dados internos de uma instituição).
  3. O modelo se especializa na tarefa específica.
- **Vantagem:** não é preciso treinar do zero.

## 3. Aprendizado Online

- O modelo é treinado **em tempo real** à medida que novos dados chegam.
- **Exemplo:** modelo de detecção de fraudes no Bolsa Família – quando o modelo erra, o dado é imediatamente usado para retreinamento.
- **Utilidade:** quando há **evolução e drift** (os padrões mudam ao longo do tempo).

## 4. Aprendizado Profundo (Deep Learning)

- Uso de **redes neurais com muitas camadas** (*deep neural networks*).
- **Exemplos:**
  - **GPT (Generative Pre-trained Transformer):** rede neural com milhões de neurônios.
  - **Redes Neurais Convolucionais (CNN):** para reconhecimento de padrões em imagens.
- **Diferenciação:**
  - **Machine Learning tradicional:** árvores de decisão, KNN, SVM, etc.
  - **Deep Learning:** redes neurais profundas.

## 5. Aprendizado Auto-supervisionado

- O modelo **gera seus próprios rótulos** automaticamente a partir dos dados de entrada.
- **Exemplo:** IA generativa de texto (GPT) – o modelo aprende a prever a **próxima palavra** em uma sequência, gerando os rótulos a partir do próprio texto.
- **Funcionamento:** usa estatística e probabilidade para determinar a próxima palavra com base no contexto.

## 6. Aprendizado de Adversidade (Adversarial Learning)

- Modelo treinado para **enfrentar adversários** que tentam enganá-lo.
- **Exemplo:** **GANs (Generative Adversarial Networks):**
  - Duas redes neurais competem:
    1. **Criadora (Generator):** gera imagens falsas.
    2. **Discriminadora (Discriminator):** treinada com imagens reais, classifica as imagens como reais ou falsas.
  - A criadora melhora continuamente até que a discriminadora não consiga mais distinguir as imagens falsas das reais.

## 7. Mapa Mental – Classificação e Algoritmos

### 7.1 Aprendizado Supervisionado

| TIPO DE PROBLEMA | ALGORITMOS |
| --- | --- |
| **Classificação** | Naive Bayes, Regressão Logística |
| **Regressão** | Regressão Linear |
| **Ambos (Classificação e Regressão)** | Redes Neurais, Árvore de Decisão, Random Forest, KNN (K-Vizinhos Mais Próximos), SVM (Support Vector Machine) |

> ### 7.1.1 Regressão Logística
> - Usa a **função sigmoide** (logística) para classificação binária.
> - Valores > 0.5 → classe 1; valores < 0.5 → classe 0.
> - Também retorna probabilidades (valores intermediários).

### 7.2 Aprendizado Não Supervisionado

| TIPO DE PROBLEMA | ALGORITMOS |
| --- | --- |
| **Agrupamento (Clustering)** | K-Means (K-médias), Algoritmos Hierárquicos, DBSCAN (Density-Based) |
| **Regras de Associação** | A Priori |
| **Redução de Dimensionalidade** | PCA (Análise de Componentes Principais) |

> ### 7.2.1 A Priori
> - Algoritmo mais famoso para **regras de associação**.
> - Exemplo: descobrir que "quem compra banana também compra maçã" (vendas casadas).

## 8. Síntese – Mapa Mental (resumo visual)

```
INTELIGÊNCIA ARTIFICIAL (IA)
    └── MACHINE LEARNING (Aprendizado de Máquina)
          ├── SUPERVISIONADO (com rótulos)
          │     ├── Classificação
          │     │     ├── Naive Bayes
          │     │     └── Regressão Logística
          │     ├── Regressão
          │     │     └── Regressão Linear
          │     └── Ambos (Classificação + Regressão)
          │           ├── Redes Neurais
          │           ├── Árvore de Decisão
          │           ├── Random Forest
          │           ├── KNN (K-Vizinhos)
          │           └── SVM (Máquina de Vetor de Suporte)
          │
          ├── NÃO SUPERVISIONADO (sem rótulos)
          │     ├── Agrupamento (Clustering)
          │     │     ├── K-Means
          │     │     ├── Hierárquicos
          │     │     └── DBSCAN
          │     ├── Regras de Associação
          │     │     └── A Priori
          │     └── Redução de Dimensionalidade
          │           └── PCA
          │
          └── POR REFORÇO (agente + ambiente + recompensas/punições)
```

## 9. Questões de Concurso Comentadas

### 9.1 (FGV/2025/TCE-PE – Auditor)

**Item:** "Com relação ao aprendizado não supervisionado em Machine Learning, assinale a afirmativa correta."

**Gabarito: c) O aprendizado não supervisionado é utilizado para gerar automaticamente rótulos com base em padrões nos dados, sem necessidade de saídas conhecidas previamente.**

**Comentário:** O não supervisionado gera grupos (clusters) sem rótulos prévios – a "geração de rótulos" aqui se refere à separação em grupos.

### 9.2 (FGV/2025/TCE-RR – Auditor)

**Afirmativas:**

- ( ) Classificação e regressão são supervisionados. **(V)**
- ( ) Não supervisionado usa dados não rotulados. **(V)**
- ( ) SVM, árvores de decisão e regressão logística são supervisionados. **(V)**

**Gabarito: a) V – V – V.**

### 9.3 (CESPE/CEBRASPE/2024/ANTT – Especialista)

**Item:** "No aprendizado supervisionado, os algoritmos de Naive Bayes e de máquinas de vetores de suporte são utilizados tanto na classificação quanto na regressão."

**Gabarito: Errado (E).**

**Comentário:** Naive Bayes é usado **apenas em classificação**. SVM pode ser usado em ambos, mas a afirmação generaliza incorretamente.

### 9.4 (FGV/2025/TCE-PE – Contas Públicas)

**Item:** "Selecione a opção que contém somente métodos de aprendizado não supervisionado."

**Gabarito: a) DBSCAN e K-Means.**

**Comentário:** DBSCAN e K-Means são algoritmos de **agrupamento (clustering)** – não supervisionados.

### 9.5 (FGV/2024/DATAPREV – ATI/Inteligência)

**Item:** "Cenário: identificar grupos de clientes com comportamentos semelhantes."

**Gabarito: d) supervisionado considerará a abstração de um modelo de conhecimento da forma (entrada, saída desejada).**

**Comentário:** O problema é de **agrupamento** (não supervisionado), mas a alternativa correta descreve corretamente o aprendizado supervisionado (entrada → saída desejada).

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (FGV/TCE-PE/2025) | c |
| 02 (FGV/TCE-RR/2025) | a |
| 03 (CESPE/ANTT/2024) | E |
| 04 (FGV/TCE-PE/2025) | a |
| 05 (FGV/DATAPREV/2024) | d |

---

*Material complementar à aula "Tipos de Aprendizado III" (professor Vitor Kessler/Gran Concursos).*