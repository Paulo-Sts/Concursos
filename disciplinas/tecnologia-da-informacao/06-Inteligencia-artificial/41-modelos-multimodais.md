# Modelos Multimodais

## 1. Definição e Conceitos Fundamentais
- Modelos multimodais são classes de algoritmos de aprendizado de máquina capazes de processar e integrar diferentes tipos de dados para realizar tarefas complexas.
- O ChatGPT-4o é um exemplo prático, pois recebe imagens e consegue descrevê-las com precisão.
- A palavra "multimodal" refere-se à capacidade de trabalhar com múltiplas modalidades de dados simultaneamente.

### 1.1 Modalidades de Dados
- Texto: informações processadas a partir de documentos, descrições textuais, etc.
- Imagem: dados visuais, como fotografias ou vídeos.
- Áudio: sons, fala ou música.
- Sinais: dados temporais, como séries temporais em dispositivos médicos ou dados de sensores.

> [!TIP] DICAS:
> - A principal característica dos modelos multimodais é a integração de diferentes tipos de dados, diferentemente dos modelos unimodais que processam apenas um tipo.

## 2. Arquiteturas de Fusão
- Um modelo de IA recebe uma entrada de dados. Se essa entrada tiver vários formatos diferentes, é preciso construir um dataset que os represente.
- As arquiteturas definem em qual momento do processo as diferentes modalidades são combinadas.

### 2.1 Fusão Precoce (Early Fusion)
- Todas as modalidades são combinadas logo no início do processo de aprendizado.
- Os dados são unificados antes do treinamento do modelo.

### 2.2 Fusão Tardia (Late Fusion)
- Cada modalidade é processada separadamente até uma certa etapa.
- Os resultados de cada modalidade são combinados posteriormente, apenas na fase de decisão final.

### 2.3 Fusão Híbrida
- Combina aspectos da fusão precoce e tardia.
- Permite que algumas modalidades sejam combinadas em diferentes estágios do processo de aprendizado.

### Quadro Comparativo das Arquiteturas de Fusão
| TIPO DE FUSÃO | CARACTERÍSTICA PRINCIPAL | MOMENTO DA COMBINAÇÃO |
|---------------|--------------------------|----------------------|
| Precoce       | Combinação no início do processo | Antes do aprendizado |
| Tardia        | Processamento separado até o final | Apenas na decisão final |
| Híbrida       | Combinação em múltiplos estágios | Em diferentes fases |

> [!CAUTION] OBSERVAÇÃO:
> - A fusão precoce pode ser mais simples de implementar, mas exige que todos os dados estejam sincronizados desde o início.
> - A fusão tardia permite maior flexibilidade no processamento de cada modalidade, mas pode perder correlações importantes entre elas.

## 3. Técnicas Utilizadas

### 3.1 Aprendizado Profundo (Deep Learning)
- Redes Neurais Convolucionais (CNNs): usadas para processar e aprender características complexas de imagens e vídeos.
- Redes Neurais Recorrentes (RNNs): utilizadas para processamento de dados sequenciais, como texto e áudio.

### 3.2 Transformers
- Modelos baseados em transformers são usados para processar grandes volumes de dados multimodais de forma eficiente.
- BERT: arquitetura transformer especializada em processamento de texto.
- ViT (Vision Transformer): arquitetura transformer especializada em processamento de imagens.

> [!TIP] DICAS:
> - Os transformers são a base dos modelos mais modernos e eficientes para tarefas multimodais.
> - A combinação de diferentes arquiteturas (CNNs + Transformers) é comum em soluções multimodais.

## 4. Principais Aplicações

### 4.1 Visão Computacional e Processamento de Linguagem Natural (NLP)
- Desenvolvimento de sistemas que combinam imagem e texto.
- Uma das áreas mais comuns de aplicação de modelos multimodais.

### 4.2 Geradores de Legenda para Imagens
- Modelos que recebem imagens como entrada e geram descrições textuais correspondentes.
- Exemplo prático: legendas automáticas de vídeos.

### 4.3 Busca Baseada em Imagem
- Modelos que encontram imagens semelhantes com base em descrições textuais.
- Possibilidade de consultar imagens baseadas em critérios textuais.

### 4.4 Sistemas de Recomendação Multimodais
- Integram dados de diversas fontes para proporcionar recomendações mais precisas e personalizadas.
- Plataformas de streaming: combinam preferências do usuário (texto, histórico de interação), características dos itens (conteúdo de vídeo ou áudio) e análises de comportamento (séries temporais) para recomendar filmes ou músicas.
- Instagram: combina informações para apresentar os melhores anúncios em cada feed.

### 4.5 Reconhecimento de Emoções
- Combinam múltiplas modalidades para inferir emoções de um indivíduo.
- Vídeo: análise de expressão facial.
- Áudio: análise do tom de voz.
- Texto: análise das palavras faladas.

> [!CAUTION] OBSERVAÇÃO:
> - Os sistemas de recomendação multimodais são considerados mais precisos que os unimodais por considerarem múltiplas dimensões do comportamento do usuário.
> - No reconhecimento de emoções, a combinação de diferentes modalidades aumenta significativamente a precisão da classificação.

## 5. Desafios dos Modelos Multimodais

### 5.1 Sincronização Temporal
- Refere-se à necessidade de alinhar corretamente os dados de diferentes modalidades no tempo.
- Exemplo: sincronizar áudio e vídeo de uma mesma cena.
- Quando o tempo é uma variável presente no modelo, é preciso garantir que todos os dados estejam sincronizados.

> [!TIP] DICAS:
> - A sincronização temporal é um dos desafios mais comuns e críticos em aplicações multimodais que envolvem dados sequenciais.
> - A falta de sincronização pode comprometer todo o aprendizado do modelo.