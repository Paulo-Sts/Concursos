# Governança e Ética na IA

## 1. Introdução
- Campo que aborda preocupações e diretrizes sobre como sistemas de IA devem ser projetados, desenvolvidos e usados de maneira responsável e justa.
- Necessidade de uma abordagem ética para garantir que a IA seja utilizada de forma a promover o bem-estar coletivo, sem prejudicar indivíduos ou grupos.

## 2. Ética em Ia

### 2.1 Viés Algorítmico
- O viés, em uma máquina, é o conceito de que a máquina irá aprender em cima de uma base de dados feita por seres humanos.

### 2.2 Privacidade
- Está relacionada à privacidade dos dados pessoais de quem utiliza a IA.

### 2.3 Explicabilidade
- Árvore de decisão é um modelo de IA super explicável, sendo um dos únicos a trazer o modelo de ferramenta de explicação.
- Exemplo: a partir da entrada X foi gerada a saída Y pelo motivo Z.
  - Entrada: Indivíduo A deseja um empréstimo;
  - Saída: empréstimo negado;
  - Motivação fornecida pela IA: "Dado que o salário de A é menor que tanto e A já apresenta as dívidas X e Y com o banco, foi negado o empréstimo para A".
- O Chat GPT não possui árvore de decisão, não possui ferramenta de explicação. Logo, não é possível saber porque foi decidido ser apresentada determinada resposta por aquela IA.

### 2.4 Responsabilidade
- A responsabilidade sempre será do ser humano, pois sempre há supervisão humana (principalmente nas IAs generativas). Não há como processar uma máquina.
- A IA não fica igual ano após ano, porque ocorre o retreinamento.

> [!CAUTION] OBSERVAÇÃO:
> - As IAs estão proporcionando um processo de transformação tão grande quanto foi o surgimento da internet.

### 2.5 Impacto no Emprego
- As IAs já estão impactando em questões relacionadas à empregabilidade, visto que é preciso menos funcionário humano para realizar determinadas tarefas a partir do momento em que o funcionário humano necessita apenas supervisionar a IA.

### 2.6 Ética na Pesquisa
- É possível solicitar à IA que sejam criados dados fake e ela montará um dataset parecido com um já existente, de forma que o ser humano possa não ter certeza se aquele artigo apresentado é verdadeiro ou falso. Isso é um problema ético.
- Por outro lado, a máquina pode identificar, por exemplo, casos de plágio em livros, dissertações e artigos científicos.

## 3. Viés Algorítmico

### 3.1 Conceito
- O ser humano possui tendências e/ou preconceitos que podem ser passados de formas não intencionais aos sistemas de IA.

### 3.2 Causas
- Dados de treinamento prejudicados;
- Design do algoritmo;
- Interpretação e uso de saída de algoritmo.

### 3.3 Exemplos

#### 3.3.1 Reconhecimento Facial
- Pesquisa do MIT Media Lab: erro de 0,8% para brancos e 34% para mulheres negras.
- Explicação: o aumento no erro não significa necessariamente um problema na base, podendo ocorrer por causa da variação das cores dos pixels.
  - Pele branca: expressão facial é mais facilmente identificável na variação de pixels por serem pixels pretos (representantes das linhas) em meio a pixels claros (representantes da pele);
  - Pele negra: o contraste de pixels entre as linhas de expressão facial e a pele é menor, o que faz com que o reconhecimento facial por parte da IA, que está vinculado ao reconhecimento de bordas e de seus elementos, possa apresentar maiores erros.

#### 3.3.2 Mundo Jurídico
- Viés contra negros em score de reincidência, classificando como existência maior para reincidência em crimes as pessoas de pele negra em detrimento das pessoas de pele branca, independente do crime.
- Exemplo: Brisha Bordem, mulher, negra, condenada por um crime pequeno, ganhou classificação 08 no risco de reincidência, enquanto Vernon Prater, homem, pele branca, condenado por assassinatos em série ganhou classificação 03 em risco de reincidência.

> [!CAUTION] OBSERVAÇÃO:
> - O caso do exemplo 3.3.2 realmente ocorre nos Estados Unidos e o sistema deixou de ser utilizado.

## 4. Transparência
- Dados de entrada: mostrar que tipo de dados é usado para treinar o modelo;
- Processos de desenvolvimento: informar como os modelos de IA são construídos, incluindo algoritmos usados, fontes de dados e critérios de seleção;
- Governança: explicar as medidas de controle e supervisão estabelecidas, bem como quem é responsável pelos resultados do sistema de IA;
- Conformidade: disponibilizar informações sobre como os sistemas de IA atendem às regulamentações locais e internacionais relevantes.

## 5. Explicabilidade
- Racionalização de decisões: fornecer justificativas legíveis e compreensíveis para as decisões tomadas por um sistema de IA;
- Modelos interpretáveis: utilizar ou desenvolver modelos que naturalmente permitem explicação, como árvores de decisão, em contraste com modelos "caixa-preta", como redes neurais profundas;
- Ferramentas de explicação: desenvolver interfaces e ferramentas que ajudam a explicar as decisões de IA para os usuários.

## 6. Abordagens para Promoção da Ética em Ia
- Regulamentação: diretrizes e princípios éticos.
- Auditorias: avaliação de impacto e mitigação de riscos;
- Desenvolvimento inclusivo: diversidade na construção das bases de treinamento;
- Educação: desenvolvedores, usuários e legisladores;
- Diversificação dos dados de treinamento;
- Análise de equidade: é visto o resultado da IA e observado se existe algum tipo de preconceito ou não nela.

> [!CAUTION] OBSERVAÇÃO:
> - O Brasil já possui um projeto para a regulamentação das IAs.