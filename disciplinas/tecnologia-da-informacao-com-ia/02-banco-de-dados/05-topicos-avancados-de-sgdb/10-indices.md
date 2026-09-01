# Índices

## 1. Conceito Fundamental de Índices
- No contexto de estrutura de dados, um índice é uma referência associada a uma chave que é utilizada para fins de otimização, permitindo localização mais rápida de um registro quando uma consulta é realizada.
- O índice em banco de dados é semelhante ao índice de um livro: ao observar o índice, é possível chegar ao ponto buscado mais rapidamente.
- Em termos teóricos, é uma estrutura que possibilita acesso a um item indexado desde que a busca tenha complexidade inferior à linear, podendo ser logarítmica ou constante.
- O índice apenas será utilizado se acelerar o processo; caso a busca linear seja mais rápida, o índice não deve ser utilizado.
- Exemplo: para chegar à página 1 de um livro, não é necessário utilizar o índice.

### 1.1 Índice e Chave Primária
- Em um banco de dados normalizado, todas as tabelas possuem uma chave primária que é um índice, servindo para uma pesquisa pelo menos linear.
- Para chegar a um determinado registro, é possível percorrer de forma linear/sequencial até chegar ao ponto buscado.

### 1.2 Considerações sobre SGBDs e Concursos
- Em aulas mais avançadas, há zonas de interseção entre os SGBDs.
- Os SGBDs de mercado têm estruturas de índice distintas: alguns possuem vasta quantidade de recursos (Oracle) e outros possuem estrutura mais simplória (SQL Server).
- Caso o concurso cobre índices genericamente, serão questões apenas sobre a teoria de índices.
- Quando são cobrados SGBD e índice, as perguntas são feitas quanto ao índice de determinado SGBD, o que demanda estudo específico.
- O SQL Server não possui questões de índice, pois seu esquema de indexação é simplório e não costuma ser cobrado pela banca.

### 1.3 Definição Prática de Índice
- No contexto de banco de dados, um índice é uma estrutura (ou arquivo) auxiliar associado a uma tabela (ou coleção de dados).
- Tem a função de acelerar o tempo de acesso às linhas de uma tabela, criando ponteiros para os dados armazenados em colunas específicas.

## 2. Funcionamento e Otimização de Índices
- O banco de dados utiliza o índice de forma semelhante ao índice remissivo de um livro: verifica um assunto determinado no índice e localiza sua posição em determinada página.
- O índice é uma das atividades clássicas de otimização.
- O SGBD possui funcionalidades que indicam onde seria bom criar ou eliminar um índice.
- Índices podem ter suas características modificadas com o tempo, tornando-os inadequados ao campo indexado.

### 2.1 Cuidados na Criação de Índices
- Em tabelas atualizadas constantemente, o índice também precisa ser atualizado; caso contrário, não encontrará determinado registro.
- Devem ser escolhidos campos cuja atualização faça sentido para a indexação.
- A criação de índices em uma tabela inteira demanda a criação de várias estruturas paralelas que precisarão ser atualizadas constantemente.
- O excesso de índices torna a estrutura auxiliar da tabela (sua consulta) mais lenta.

> [!CAUTION] OBSERVAÇÃO: 
> - Índice é uma ferramenta de otimização, mas deve ser usado com critério. Em tabelas com muitas atualizações, o custo de manutenção do índice pode superar o benefício na consulta.
> - O SGBD possui funcionalidades que indicam onde seria bom criar ou eliminar um índice, pois com o tempo suas características podem se modificar.

## 3. Classificação dos Índices

### 3.1 Índices Compostos x Índices Simples
- Índices compostos: fazem referência a mais de uma coluna.
- Índices simples: fazem referência a uma única coluna.

### 3.2 Índices Esparsos x Índices Densos
- Índice esparso: o total de entradas no índice será igual ao número de blocos do arquivo de dados.
- Índice denso: possui uma entrada para cada registro no arquivo de dados.

### 3.3 Índices Internos x Índices Externos
- Índices internos: a chave está contida dentro da tabela. Normalmente, quando se declara uma chave primária em uma tabela, ela se torna um índice.
- Índices externos: existe uma tabela de chaves separada que associa ponteiros a registros de uma tabela.
- O índice interno ou externo dependerá da implementação do SGBD.
- Não se sabe se o MySQL possui uma estrutura separada ou não, mas, quando se cria, já é associado um índice àquela estrutura.

> [!CAUTION] OBSERVAÇÃO: 
> - A distinção entre índice interno e externo depende da implementação do SGBD; não é uma regra universal.

## 4. Índice Primário x Chave Primária

### 4.1 Índice Primário
- É um arquivo ordenado cujos registros são de tamanho fixo com dois campos:
  - O primeiro campo é do mesmo tipo de dado do campo de chave de ordenação (chave primária) do arquivo de dados.
  - O segundo campo é um ponteiro para um bloco de disco (um endereço de bloco).
- O índice primário associa a chave primária.
- Ao realizar uma consulta, o SGBD vai para o menor arquivo do índice e percorre o registro.
- Exemplo clássico (Navathe): um arquivo de índice com o valor da chave primária e o campo chave primária ocupado pelo nome. Normalmente, na prática, a chave primária é o CPF, não o nome.

### 4.2 Chave Primária
- Identificador único de uma tabela, utilizado para distinguir um registro de outro.

### 4.3 Índices Secundários
- Podem ser definidos sobre atributos da tabela.
- Normalmente são chaves (sem valores repetidos) ou não chave (com valores repetidos).

> [!TIP] DICAS: 
> - Índice primário: usa a chave primária como parte do índice; a chave primária é copiada para uma estrutura separada e criado um ponteiro que direciona para o registro.
> - O índice primário tem dois campos: a chave e o ponteiro para o registro no disco.

### Exemplo de Estrutura do Índice Primário
| ÍNDICE | CHAVE | REGISTRO |
|--------|-------|----------|
|        | 11    | Maria    |
|        | 22    | Ana      |
|        | 33    | Paulo    |
|        | 44    | Rodrigo  |
|        | 55    | Carlos   |

## 5. Índice de Agrupamento
- Se os registros de arquivo forem fisicamente ordenados em um campo não chave (que não tem um valor distinto para cada registro), esse campo é chamado de campo de agrupamento.
- O arquivo de dados é chamado de arquivo agrupado.
- Serve para agilizar a recuperação de todos os registros que têm o mesmo valor para o campo de agrupamento.
- Exemplo: número do departamento em que o indivíduo trabalha - diversas pessoas podem trabalhar no mesmo departamento (campo que se repete, não é único).
- No arquivo de índice, há entradas: a chave (k) e o ponteiro.
- O campo de agrupamento 1 aponta para onde há 1, e assim sucessivamente.
- Ao buscar o valor 2, serão apontados todos os registros em que consta 2.

> [!TIP] DICAS: 
> - Índice de agrupamento é usado quando se deseja recuperar todos os registros com o mesmo valor em um campo não chave.
> - É diferente do índice primário, que trabalha com chave única.

## 6. Índice Multinível
- O esquema multinível pode ser usado em qualquer tipo de índice (primário, de agrupamento ou secundário).
- É utilizado quando já há o índice primário na tabela e é criado um índice para outro campo.
- O índice de primeiro nível deve ter valores distintos para K(i) e entradas de tamanho fixo.
- O objetivo é reduzir a parte do índice que a pesquisa seguirá.

### 6.1 Funcionamento do Índice Multinível
- Há dois níveis: o nível primário (base) e o nível secundário (topo).
- O nível secundário aponta para o nível primário.
- Exemplo: para chegar ao registro 2, o nível secundário aponta para 2, que é encontrado no nível primário.
- O índice é uma estrutura na qual, em algum momento, também serão feitas pesquisas lineares.
- Se o índice não for multinível e contar com todos os registros na sequência, ficará extenso e o percurso será demorado.
- Vantagem: apenas três leituras são necessárias para encontrar o registro - uma no nível secundário, uma no nível primário e a terceira chega ao campo de chave primária.

### 6.2 Comparação com Busca Linear
- Havendo 85 registros, em uma busca linear seriam necessárias 85 leituras (iniciando em 1 até chegar em 85).
- Com o índice multinível, para chegar a 85: uma leitura no nível secundário (topo), outra no nível primário (base) e, com mais uma leitura, chega-se ao final.
- Com poucos saltos chega-se ao registro.

> [!TIP] DICAS: 
> - O índice multinível é semelhante ao índice de um livro, que possui um nível macro e um nível mais detalhado.
> - É semelhante à estruturação do índice B-Tree, baseado na árvore binária estudada em algoritmos.

## 7. Índice B-Tree
- A árvore é balanceada: possui o ponteiro de nó de árvore e o ponteiro de árvore nulo (que não possui nenhum valor).
- Diferença para o índice multinível: organiza os registros e faz balanceamentos.
- Há o nó central, que normalmente está no meio dos registros.
- Exemplo: se há 12 registros, o central é o 5.
- Para chegar ao 12, são feitas buscas no sentido em que ele está; com três leituras é possível chegar ao registro.
- Isso é totalmente diferente da pesquisa sequencial, que levaria 12 leituras (do 1 até o 12).
- Existem SGBDs em que o padrão de índice é ser uma árvore, conforme explicado na abordagem dos índices de cada SGBD.

> [!TIP] DICAS: 
> - B-Tree é uma estrutura balanceada que organiza os dados em forma de árvore, com um nó central e outros nós.
> - Permite chegar ao registro com poucos saltos, otimizando a busca.

## 8. Índice e Otimização de Desempenho
- O índice pode ser cobrado como:
  - Tuning de segurança.
  - Otimização de desempenho.
  - Índice (ocasião em que se aplica a regra de view e gatilho).

> [!CAUTION] OBSERVAÇÃO: 
> - Índice é uma estrutura de otimização, mas seu uso deve ser planejado considerando o volume de atualizações e a natureza dos dados.