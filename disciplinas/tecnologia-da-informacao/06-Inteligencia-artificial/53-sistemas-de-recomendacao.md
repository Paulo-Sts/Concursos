# Sistemas de Recomendação

## 1. Conceitos Fundamentais
- Os sistemas de recomendação são amplamente utilizados em plataformas digitais para personalizar experiências e melhorar o engajamento do usuário.
- Funcionam com base no histórico de interações do usuário, ajustando sugestões para manter o usuário envolvido.
- Exemplo: Netflix sugere filmes com base no que o usuário já assistiu; Amazon recomenda produtos semelhantes; Instagram e WhatsApp exibem anúncios relacionados ao comportamento do usuário.

### 1.1 Exploração vs. Explotação
- O problema do "cold start" ocorre quando um novo usuário entra no sistema sem dados sobre seus interesses.
- A solução para o cold start é a exploração (exploration).
  - O sistema experimenta novos conteúdos aleatórios para avaliar a reação do usuário.
  - Com base no feedback, ajusta recomendações futuras.
- Explotação (exploitation).
  - Ocorre quando o sistema já possui informações sobre os gostos do usuário.
  - Oferece conteúdos semelhantes ao que ele já consome, maximizando a satisfação imediata.

> [!TIP] DICAS:
> - A exploração resolve o "cold start", mas o excesso gera insatisfação com sugestões irrelevantes.
> - A explotação intensiva pode levar à estagnação, sem introduzir novidades.
> - O equilíbrio entre exploração e explotação é essencial para sistemas eficientes.

## 2. Feedback dos Usuários

### 2.1 Feedback Explícito
- Ocorre quando o usuário avalia diretamente um item.
- Exemplos: avaliações por estrelas, curtidas, comentários.
- Ação positiva é interpretada como preferência, e o sistema recomenda conteúdos semelhantes.
- Exemplo: AliExpress e Shein incentivam avaliações com pontos ou frete grátis.
- As avaliações passam por análises de sentimentos para determinar a experiência do usuário.

### 2.2 Feedback Implícito
- Ocorre de maneira passiva, sem avaliação direta do usuário.
- O sistema observa o comportamento do usuário.
  - Itens clicados;
  - Tempo gasto em páginas;
  - Histórico de navegação.
- Exemplo: se o usuário visualiza itens semelhantes por um período prolongado, o sistema infere interesse no tipo de produto.

> [!CAUTION] OBSERVAÇÃO:
> - O feedback explícito é mais preciso, mas menos frequente.
> - O feedback implícito é mais abundante, porém menos exato.

## 3. Algoritmos Utilizados

### 3.1 Principais Algoritmos
- Os sistemas de recomendação utilizam algoritmos de classificação para identificar padrões de comportamento.
- Exemplo: se um usuário acessa os itens 2, 4, 6 e depois 7, o sistema aprende que o próximo recomendado deve ser o 7.

- Algoritmos mais comuns.
  - k-Nearest Neighbors (k-NN);
  - Deep Learning (Redes Neurais Profundas);
  - Random Forest;
  - Gradient Boosting Machines (GBM);
  - Algoritmos de Clusterização;
  - Aprendizado por Reforço.

### 3.2 Clusterização
- Conceito distinto dos demais algoritmos.
- Agrupa itens ou históricos semelhantes.
- Exemplo: filmes podem ser agrupados por gênero, ano de lançamento e atores.
- Se o usuário assiste a um filme de determinado cluster, o sistema recomenda outros filmes desse mesmo grupo.

### 3.3 Aprendizado por Reforço
- O sistema aprende com as ações e resultados do usuário.
- Se o usuário não interage com a recomendação, o sistema reconhece que não foi eficiente.
- Se o usuário clica na recomendação, o sistema recebe uma recompensa positiva e reforça a recomendação em futuras interações.

## 4. Filtragem Colaborativa
- Baseia-se na análise das preferências de outros usuários para recomendar itens a um usuário específico.
- Se dois usuários possuem gostos semelhantes, a recomendação feita a um provavelmente será adequada para o outro.

### 4.1 Filtragem Colaborativa Baseada em Usuários
- Recomenda itens com base nas preferências de outros usuários com gostos semelhantes.
- Utiliza uma matriz de usuários e itens para identificar grupos de usuários com comportamentos semelhantes.
- Exemplo: se o usuário 1 assistiu aos itens 1, 2, 3 e o usuário 2 fez o mesmo, o sistema recomenda o item 3 ao usuário 3 que assistiu aos itens 1 e 2.

### 4.2 Filtragem Colaborativa Baseada em Itens
- Recomendação feita com base em itens semelhantes.
- Exemplo: se o usuário A assistiu a um filme de ficção científica e o sistema sabe que o usuário B também prefere esse gênero, recomenda o mesmo filme ao usuário B.
- Exemplo prático: se um usuário pesquisa informações sobre uma faca e analisa detalhes como tamanho e preço, o sistema sugere outras facas similares.
- Essa abordagem utiliza a criação de clusters (agrupamentos) de itens semelhantes.

> [!TIP] DICAS:
> - Matriz usuário-item: a base da filtragem colaborativa.
> - Baseada em usuários: vizinhos com comportamentos semelhantes.
> - Baseada em itens: clusters de produtos semelhantes.

## 5. Filtragem Baseada em Conteúdo
- Analisa as propriedades de cada item (gênero, autor, palavras-chave).
- Faz recomendações com base nos interesses anteriores do usuário.
- O sistema constrói um perfil para cada usuário com base nas características dos itens consumidos.
- Com esse perfil, recomenda novos itens que compartilham características semelhantes.
- Exemplo: se o usuário assistiu "Star Wars", o sistema pode recomendar "Star Trek" por compartilhar características semelhantes.

- Diferenças entre as abordagens.
  - Filtragem colaborativa: considera interações entre diversos usuários ou agrupamentos de itens.
    - Exemplo: se Maria e João têm históricos semelhantes, itens lidos por Maria podem ser sugeridos a João.
  - Filtragem baseada em conteúdo: foco exclusivo no histórico individual e nas características dos itens consumidos.
    - Exemplo: se João lê o item A e o item B compartilha características com A, o sistema sugere B sem considerar outros usuários.

> [!CAUTION] OBSERVAÇÃO:
> - A filtragem baseada em conteúdo não sofre com o problema de cold start para novos itens, pois utiliza características intrínsecas.
> - Porém, tende a recomendar itens muito semelhantes, limitando a diversidade.

## 6. Sistemas Híbridos
- Combinam várias abordagens de recomendação para melhorar a precisão e a personalização.
- Funcionamento.
  - A filtragem colaborativa identifica um conjunto amplo de opções com base em comportamentos de usuários semelhantes.
  - A filtragem baseada em conteúdo refina essas opções de acordo com as preferências individuais do usuário.

## 7. Recomendação Baseada em Sessão
- Foca apenas no comportamento do usuário durante a sessão atual, sem considerar o histórico completo.
- Comum em plataformas de e-commerce.
- Exemplo: se o usuário busca uma câmera específica, o sistema evita sugerir câmeras já compradas, ajustando as recomendações em tempo real.

## 8. Recomendação em Tempo Real
- Sistemas projetados para reagir instantaneamente ao comportamento do usuário.
- Ao invés de recomendar com base em dados antigos ou estáticos, ajustam as sugestões conforme o usuário navega, clica ou consome conteúdo.

## 9. Filtragem Baseada em Confiabilidade (Trust-Based Filtering)
- Considera a relação de confiança entre usuários.
- Quando um usuário confia em outro, as preferências do usuário confiável são consideradas nas recomendações.
- Exemplo: se João segue Maria, e Maria interage com uma página específica, essa página pode ser sugerida a João, pois ele confia nas escolhas de Maria.

## 10. Filtragem Baseada em Grafo
- Utiliza grafos para representar as relações entre usuários e itens.
- Cada usuário e item é representado por um nó.
- As conexões (arestas) indicam interações, como a visualização de um item.
- Exemplo: se o Usuário 1 assistiu aos itens 1 e 2, e o Usuário 2 assistiu ao item 1, o sistema recomenda o item 2 ao usuário 2.
- Algoritmos como Neo4j são utilizados para otimizar a recomendação.

## 11. Problemas Comuns em Sistemas de Recomendação

### 11.1 Cold Start (Problema de Novo Usuário ou Novo Item)
- Dificuldade de recomendação inicial para novos usuários ou itens.
- Soluções.
  - Sistema híbrido: combina estratégias para agregar informações.
  - Solicitação de preferências iniciais: Netflix solicita gêneros favoritos logo após o cadastro.
  - Exploração: testar novas opções para identificar preferências.

### 11.2 Escalabilidade
- O volume de dados cresce exponencialmente, tornando o processamento mais difícil.
- Exemplo: com 100 mil itens e 100 mil usuários, podem haver milhões de interações simultâneas.
- Soluções.
  - Infraestruturas robustas (armazenamento em nuvem);
  - Algoritmos como k-NN, que identificam itens semelhantes em espaços n-dimensionais;
  - Infraestrutura distribuída para garantir eficiência.

### 11.3 Data Sparsity (Esparsidade dos Dados)
- Ocorre devido à baixa interação dos usuários com a vasta quantidade de itens disponíveis.
- Exemplo: na Netflix, a maioria dos usuários consome uma pequena fração do catálogo total, resultando em uma matriz com muitos valores ausentes.
- Consequências.
  - Itens menos populares têm poucas interações e menos informações para análise;
  - Blockbusters concentram a maioria das interações, centralizando as recomendações.
- Soluções.
  - Fatoração de matrizes;
  - Decomposição em valores singulares (SVD);
  - Modelos de fatores latentes (semelhantes à modelagem de tópicos).

### 11.4 Explicabilidade das Recomendações
- Capacidade de justificar ao usuário as razões por trás de uma recomendação.
- Algoritmos complexos como redes neurais frequentemente não oferecem transparência.
- Soluções.
  - Filtragem baseada em conteúdo: justifica com base nas preferências registradas do usuário.
    - Exemplo: informar que um filme foi recomendado porque pertence ao mesmo gênero de outros assistidos.
  - Regras de associação: estabelecem relações claras entre itens.
    - Exemplo: se o usuário assistiu ao item 1, o sistema recomenda o item 3 com base no histórico de associações.
  - Explicação a posteriori: justifica as recomendações após sua apresentação.
    - Utiliza modelos de interpretabilidade como SHAPE e LIME para identificar itens relevantes.
  - Filtragem baseada em confiabilidade: utiliza a confiança social para justificar recomendações.
    - Exemplo: informar que o item foi sugerido porque um amigo interagiu com ele.

> [!TIP] DICAS:
> - Cold start: novos usuários/itens sem histórico.
> - Escalabilidade: grande volume de dados exige infraestrutura robusta.
> - Data sparsity: poucos itens têm muitas interações.
> - Explicabilidade: necessidade de transparência nas recomendações.