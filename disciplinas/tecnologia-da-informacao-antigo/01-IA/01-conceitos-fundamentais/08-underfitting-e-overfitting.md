# Anotações – Underfitting e Overfitting

## 1. Conceitos Fundamentais

### 1.1 Underfitting (Subajuste)

- O modelo **não consegue capturar adequadamente os padrões** nos dados de treinamento.
- **Características:**
  - Alto erro **tanto no treino quanto no teste**.
  - Modelo muito **simples** para a complexidade dos dados.
  - **Variância baixa** e **viés alto**.

> ### 1.1.1 Causas do Underfitting
> - Algoritmo pouco complexo.
> - Dados insuficientes.
> - Atributos não representativos.
> - Regularização excessiva.
> - Erros de amostragem.
> - Tempo de treinamento insuficiente.

> ### 1.1.2 Soluções para Underfitting
> - Aumentar a complexidade do modelo.
> - Aumentar o tempo de treinamento.
> - Encontrar dados melhores.
> - Aumentar a quantidade de dados.
> - Reduzir a regularização.

### 1.2 Overfitting (Sobreajuste)

- O modelo se ajusta **excessivamente aos dados de treinamento**, capturando também **ruídos** e padrões irrelevantes.
- **Características:**
  - Alta precisão no treino, mas **baixo desempenho em novos dados** (perda de generalização).
  - Modelo muito **complexo**.
  - **Variância alta** e **viés baixo**.

> ### 1.2.1 Causas do Overfitting
> - Algoritmo muito complexo para uma base de dados simples.
> - Poucos dados de treinamento.
> - Dados de treinamento desbalanceados.
> - Ruídos nos dados de treinamento.
> - Atributos pouco relevantes (colunas que não ajudam a prever o rótulo).

> ### 1.2.2 Soluções para Overfitting
> - **Regularização:** reduzir a complexidade do modelo.
>   - **Poda de árvores de decisão:** reduzir decisões, simplificando a árvore.
>   - **Dropout:** desativar neurônios aleatoriamente em redes neurais.
>   - **L1, L2 e Elastic Net:** técnicas de regularização para regressão.
> - **Treinar com mais dados.**
> - **Validação cruzada (k-fold):** treina com todos os dados e testa com todos, gerando múltiplos modelos.
> - **Early Stopping:** interromper o treinamento quando o erro no conjunto de validação/teste começar a aumentar.
> - **Ensemble:** combinar múltiplos modelos (ex.: votação) para reduzir overfitting.
> - **Data Augmentation:** aumentar os dados da classe desbalanceada.

## 2. Gráfico – Erro vs. Complexidade do Modelo

```
Erro
  ↑
  │                    ╭─── test error
  │                  ╱
  │                ╱   ╲
  │              ╱   ╱    ╲
  │            ╱   ╱        ╲
  │          ╱   ╱            ╲
  │        ╱   ╱                ╲
  │      ╱   ╱                    ╲
  │    ╱   ╱                        ╲
  │  ╱   ╱                            ╲
  │╱   ╱                                ╲
  │   ╱                     training error
  │  ╱
  │ ╱
  │╱
  └────────────────────────────────────────→ Complexidade
     Underfitting    Ajuste ideal    Overfitting
```

- **Underfitting:** erro alto no treino e no teste.
- **Overfitting:** erro baixo no treino, erro alto no teste.
- **Ajuste ideal:** ponto onde o erro de teste é mínimo.

## 3. Bias (Viés) vs. Variância

| CONCEITO | DESCRIÇÃO | RELAÇÃO COM UNDER/OVERFITTING |
| --- | --- | --- |
| **Bias (Viés)** | Previsões erradas em razão do aprendizado de um **padrão distorcido**. O modelo faz suposições incorretas sobre os dados. | **Underfitting:** viés alto. |
| **Variância** | O modelo é **muito sensível** a pequenas mudanças nos dados de treinamento. Se os dados mudam ligeiramente, o modelo muda completamente. | **Overfitting:** variância alta. |

### 3.1 Exemplo de viés algorítmico

- Uma IA treinada para prever tempo de cumprimento de pena pode reproduzir **vieses racistas** presentes nos dados históricos (ex.: penas mais altas para indivíduos negros).
- A IA aprendeu um padrão distorcido (bias) a partir dos dados de treinamento.

## 4. Comparativo – Underfitting vs. Overfitting

| CRITÉRIO | UNDERFITTING | OVERFITTING |
| --- | --- | --- |
| **Desempenho no treino** | Ruim (erro alto) | Bom (erro baixo) |
| **Desempenho no teste** | Ruim (erro alto) | Ruim (erro alto) |
| **Complexidade do modelo** | Baixa | Alta |
| **Viés** | Alto | Baixo |
| **Variância** | Baixa | Alta |
| **Causa principal** | Modelo muito simples | Modelo muito complexo |
| **Solução** | Aumentar complexidade, mais dados, menos regularização | Regularização, mais dados, validação cruzada, early stopping, ensemble |

## 5. Questões de Concurso Comentadas

### 5.1 (CESPE/CEBRASPE/2025/ANM – Especialista)

**Item:** "O overfitting ocorre quando um modelo de machine learning tem alta precisão nos dados de treinamento, mas apresenta desempenho significativamente pior em novos dados."

**Gabarito: Certo (C).**

### 5.2 (CESPE/CEBRASPE/2024/CTI – Tecnologista)

**Item:** "Overfitting é um comportamento esperado e desejável de aprendizado de máquina."

**Gabarito: Errado (E).**

**Comentário:** Overfitting é **problemático e indesejável**.

### 5.3 (CESPE/CEBRASPE/2025/PF – Agente)

**Item:** "Em aprendizado de máquina, não há overfitting."

**Gabarito: Errado (E).**

**Comentário:** Overfitting **existe** e é um problema comum.

### 5.4 (FGV/2024/TJ-MT – Analista)

**Item:** "Afirmativa correta acerca do processo de overfitting:"

**Gabarito: b) O modelo se ajusta excessivamente aos dados de treino, mas apresenta baixo desempenho em dados de teste.**

### 5.5 (FGV/2024/EPE – Analista)

**Item:** "Modelo com alta precisão no treino e baixa precisão em novos dados indica:"

**Gabarito: b) overfitting, já que o modelo é excessivamente ajustado aos dados de treinamento.**

### 5.6 (FGV/2024/TJ-RR – Analista)

**Item:** "Uma maneira de mitigar o overfitting é usar técnicas de:"

**Gabarito: d) regularização.**

### 5.7 (CESPE/CEBRASPE/2025/ANM – Underfitting)

**Item:** "A única maneira de se evitar o underfitting é reduzir a quantidade de dados de entrada."

**Gabarito: Errado (E).**

**Comentário:** Underfitting pode ser evitado aumentando a complexidade do modelo, aumentando dados, reduzindo regularização, etc.

### 5.8 (FGV/2025/TCE-RR – Auditor)

**Item:** "O underfitting ocorre:"

**Gabarito: c) quando o modelo não consegue capturar adequadamente os padrões nos dados do conjunto de treinamento, resultando em um desempenho insuficiente.**

### 5.9 (CESPE/CEBRASPE/2024/CTI – Subajuste)

**Item:** "Modelo de bom desempenho com dados já treinados, mas que não lide muito bem com novos dados é denominado subajuste."

**Gabarito: Errado (E).**

**Comentário:** Isso é **overfitting (sobreajuste)** – o modelo decora os dados de treino e não generaliza.

### 5.10 (CESPE/CEBRASPE/2024/CTI – Sobreajuste)

**Item:** "Ocorre sobreajuste quando o modelo não pode determinar uma relação significativa entre os dados de entrada e saída."

**Gabarito: Errado (E).**

**Comentário:** Isso é **underfitting (subajuste)**. Overfitting ocorre quando o modelo se ajusta excessivamente aos dados de treino.

### 5.11 (FGV/2025/TCE-PI – Auditor)

**Afirmativas:**

- I – Underfitting indica baixa capacidade preditiva no treino. **(V)**
- II – Overfitting impacta negativamente a capacidade de generalização. **(V)**
- III – Ruído favorece overfitting. **(V)**

**Gabarito: e) I, II e III.**

---

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (CESPE/ANM/2025) | C |
| 02 (CESPE/CTI/2024) | E |
| 03 (CESPE/PF/2025) | E |
| 04 (FGV/TJ-MT/2024) | b |
| 05 (FGV/EPE/2024) | b |
| 06 (FGV/TJ-RR/2024) | d |
| 07 (CESPE/ANM/2025) | E |
| 08 (FGV/TCE-RR/2025) | c |
| 09 (CESPE/CTI/2024) | E |
| 10 (CESPE/CTI/2024) | E |
| 11 (FGV/TCE-PI/2025) | e |

---

## Síntese para Revisão Rápida

| CONCEITO | DEFINIÇÃO |
| --- | --- |
| **Underfitting** | Modelo não aprende os padrões dos dados (erro alto no treino e no teste). |
| **Overfitting** | Modelo decora os dados de treino e não generaliza (erro baixo no treino, alto no teste). |
| **Bias (Viés)** | Erro por suposições incorretas (underfitting → viés alto). |
| **Variância** | Sensibilidade a pequenas mudanças nos dados (overfitting → variância alta). |
| **Regularização** | Técnica para reduzir overfitting (simplifica o modelo). |
| **Early Stopping** | Para o treinamento antes do overfitting. |
| **Validação Cruzada** | Avalia o modelo com múltiplos conjuntos (reduz overfitting). |
| **Ensemble** | Combina múltiplos modelos para melhorar a generalização. |

---

*Material complementar à aula "Underfitting e Overfitting" (professor Vitor Kessler/Gran Concursos).*