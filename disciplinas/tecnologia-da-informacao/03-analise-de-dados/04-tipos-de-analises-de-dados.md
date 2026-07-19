# Anotações

# Tipos de Análises de Dados

## 1.1 Análise Descritiva (*Descriptive Analytics*)

### 1.1.1 Conceito
- **Entender o que aconteceu no passado.**
- Descrever e resumir dados históricos.
- Normalmente associada ao **começo do processo** da ciência de dados, onde se pretende descrever melhor os dados.
- Muito associada ao **aprendizado não supervisionado** – possui uma base de dados e não se sabe nada sobre ela.

### 1.1.2 Técnicas
- **Estatística descritiva** (média, mediana, moda, desvio padrão).
- **Visualização de dados** (gráficos, dashboards).
- **Agrupamento (*Clustering*):** os semelhantes ficam juntos.
- **Regras de associação:** encontra valores co-ocorrentes na base – muito utilizada para **cesta de compras** (ex.: "quem comprou pão também comprou manteiga").

> [!TIP] DICAS
> - Análise descritiva responde à pergunta: **"O que aconteceu?"**.
> - É a base para as demais análises.

## 1.2 Análise Preditiva (*Predictive Analytics*)

### 1.2.1 Conceito
- **Prever o futuro** com base em dados passados.
- Utiliza dados históricos para prever tendências e resultados futuros.
- Faz uma **relação entre os dados e a classe/rótulo**.
- Está associada ao **aprendizado supervisionado**.
- **Série temporal:** um histórico de variação de dados permite a previsão do futuro (ex.: previsão do tempo).

### 1.2.2 Técnicas
- **Aprendizado supervisionado** (classificação e regressão).
- **Séries temporais** (análise de dados ao longo do tempo).

> [!TIP] DICAS
> - Análise preditiva responde à pergunta: **"O que pode acontecer?"**.
> - Exemplo: previsão de vendas, previsão do tempo, detecção de fraudes.

## 1.3 Análise Diagnóstica (*Diagnostic Analytics*)

### 1.3.1 Conceito
- **Entender POR QUE algo aconteceu.**
- Identifica **causas e explicações** para os eventos observados.
- É uma análise **mais complexa** que a descritiva e a preditiva.
- Busca a **correlação entre causa e consequência**.

### 1.3.2 Técnicas
- **Análise de correlação.**
- **Análise de regressão.**
- ***Drill-down Analysis*** (análise detalhada em níveis mais profundos).

> [!TIP] DICAS
> - Análise diagnóstica responde à pergunta: **"Por que aconteceu?"**.
> - Exemplo: por que as vendas de um produto caíram no último trimestre?

## 1.4 Análise Prescritiva (*Prescriptive Analytics*)

### 1.4.1 Conceito
- **Sugerir ações ou estratégias** para alcançar os melhores resultados possíveis.
- Prescreve uma **solução** para os problemas identificados.
- Considera **múltiplos cenários** e determina a melhor abordagem.

### 1.4.2 Técnicas
- **Otimização** (ex.: encontrar a melhor alocação de recursos).
- **Simulação** (testar diferentes cenários).
- **Algoritmos de decisão** (árvores de decisão, análise de risco).

> [!TIP] DICAS
> - Análise prescritiva responde à pergunta: **"O que deve ser feito?"**.
> - Exemplo: qual a melhor estratégia para aumentar as vendas?

## 1.5 Analogia com o Diagnóstico Médico

| ANÁLISE | ANALOGIA MÉDICA |
|---------|-----------------|
| **Descritiva** | Anamnese e exames – coleta de informações sobre o paciente |
| **Preditiva** | Previsão do problema – "o paciente provavelmente tem X" |
| **Diagnóstica** | Identificação da causa – "o paciente tem X porque Y" |
| **Prescritiva** | Prescrição da solução – "deve-se fazer o tratamento Z" |

## 1.6 Tabela Resumo – Tipos de Análises

| TIPO | PERGUNTA | OBJETIVO | TÉCNICAS | RELAÇÃO COM ML |
|------|----------|----------|----------|----------------|
| **Descritiva** | O que aconteceu? | Descrever/resumir dados históricos | Estatística descritiva, visualização, agrupamento, regras de associação | Não supervisionado |
| **Preditiva** | O que pode acontecer? | Prever o futuro | Aprendizado supervisionado, séries temporais | Supervisionado |
| **Diagnóstica** | Por que aconteceu? | Identificar causas | Correlação, regressão, *drill-down* | — |
| **Prescritiva** | O que deve ser feito? | Sugerir ações/soluções | Otimização, simulação, algoritmos de decisão | — |

> [!CAUTION] OBSERVAÇÃO
> **A análise prescritiva NÃO serve para relatar acontecimentos (descritiva) nem para fazer previsões (preditiva).** O foco é recomendar ações específicas a serem tomadas para melhorar eficiência, eficácia e produtividade.

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2021/TCE-RJ/ANALISTA DE CONTROLE EXTERNO/ESPECIALIDADE: CONTROLE EXTERNO)

Com relação a noções de mineração de dados e Big Data, julgue o item que se segue.

Na mineração de dados preditiva, ocorre a geração de um conhecimento obtido de experiências anteriores para ser aplicado em situações futuras.

**Gabarito:** C (Correto)

## Questão 02
(CESPE/2018/POLÍCIA FEDERAL/ESCRIVÃO DE POLÍCIA FEDERAL)

Em um big data, alimentado com os dados de um sítio de comércio eletrônico, são armazenadas informações diversificadas, que consideram a navegação dos usuários, os produtos comprados e outras preferências que o usuário demonstre nos seus acessos. Tendo como referência as informações apresentadas, julgue o item seguinte.

Dados coletados de redes sociais podem ser armazenados, correlacionados e expostos com o uso de análises preditivas.

**Gabarito:** C (Correto)

## Questão 03
(CESPE/CEBRASPE/2022/TCE-RJ/ANALISTA DE CONTROLE EXTERNO)

Julgue o item subsequente, referentes a Big Data e visualização e análise exploratória de dados. A análise prescritiva é empregada na análise de Big Data para relatar acontecimentos e para fazer previsões de comportamentos futuros de indivíduos e processos.

**Gabarito:** E (Errado) - **Relatar acontecimentos** é análise **descritiva**; **fazer previsões** é análise **preditiva**. A análise prescritiva sugere ações/soluções.

## Questão 04
(CESPE/CEBRASPE/2024/CTI/TECNOLOGISTA PLENO 2 - I - ESPECIALIDADE: INDÚSTRIA 4.0 E GOVERNO DIGITAL - ÁREA DE ATUAÇÃO: SISTEMAS CIBERFÍSICOS E CIDADES INTELIGENTES)

Com relação a Big Data, julgue o item seguinte.

Entre as quatro análises possíveis no Big Data, a análise diagnóstica tem como foco recomendar ações específicas a serem tomadas, e seus resultados podem ser usados para melhorar a eficiência, a eficácia e a produtividade das empresas.

**Gabarito:** E (Errado) - Quem recomenda ações é a análise **prescritiva**, não a diagnóstica.

## Questão 05
(FCC/2022/TRT/5ª REGIÃO (BA)/TÉCNICO JUDICIÁRIO - TECNOLOGIA DA INFORMAÇÃO)

Sobre os conceitos de modelos preditivos, analise as afirmações abaixo.

I – O modelo preditivo não supervisionado recebe dados de entrada e saída e busca correlações entre eles.

II – O modelo supervisionado recebe apenas dados de entrada para encontrar padrões e prevê repetições de ocorrências anteriores.

III – A análise preditiva é utilizada como ferramenta para identificar padrões que podem sugerir ações fraudulentas.

IV – A utilização de técnicas de aprendizagem de máquina para a análise preditiva permite produzir de forma automática e mais rápida modelos mais precisos.

É correto o que se afirma APENAS em

a) I.
b) II.
c) I e III.
d) III e IV.
e) I, II e IV.

**Gabarito:** d

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | C |
| 03 | E |
| 04 | E |
| 05 | d |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*