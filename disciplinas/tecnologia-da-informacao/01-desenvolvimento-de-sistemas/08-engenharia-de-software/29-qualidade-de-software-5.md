# Engenharia de Software - Qualidade de Software 5

## 1. Medição de Software
- A medição de software está preocupada com a quantificação de algum atributo de um sistema de software, como a sua complexidade ou a sua confiabilidade.
- A medição em si é quantificar algo em um padrão, enquanto a métrica é uma extrapolação dessas medições com dados finitos ou junção de medidas.
- Comparando os valores medidos uns com os outros e com os padrões que se aplicam a uma organização, deve ser possível tirar conclusões sobre a qualidade do software ou avaliar a eficácia de processos de software, de ferramentas e de métodos.
- Em um mundo ideal, o gerenciamento da qualidade pode contar com medições de atributos que afetam a qualidade do software.

## 2. Medidas Diretas e Indiretas
- Uma diferença entre as medidas diretas e indiretas é que as diretas são precisas, enquanto as indiretas são subjetivas.
- Exemplos de medidas diretas e indiretas:

| MEDIDAS DIRETAS | MEDIDAS INDIRETAS |
|---|---|
| Custo | Funcionalidade |
| Esforço | Qualidade |
| Linhas de código | Complexidade |
| Velocidade de execução | Eficiência |
| Memória | Confiabilidade |
| Número de erros | Manutenibilidade |
| Complexidade ciclomática |  |

> [!CAUTION] OBSERVAÇÃO:
> - Existem alguns conceitos que foram mudados devido à atuação do TCU e das áreas de desenvolvimento de software do governo. Uma dessas mudanças foi transformar a medida de Esforço (como é amplamente conhecido na literatura) por Resultado, que seria literalmente ter um resultado para ser entregue.

## 3. Métricas
- É uma característica de um sistema de software, da documentação do sistema ou do processo de desenvolvimento, que pode ser medida objetivamente.
- Exemplos de métricas:
  - Tamanho de um produto em linhas de código;
  - Índice Fog, que é uma medida da compreensão de um texto;
  - Número de falhas relatadas em um produto de software entregue;
  - Número de pessoas-dia necessário para desenvolver um componente de sistema.

> [!TIP] DICAS:
> - Medida é a quantificação de dados em um padrão e qualidade aceitáveis (exatidão, completude, consistência, temporalidade). Quando se mede o comprimento de um material ou peça, por exemplo, pode-se utilizar o metro como unidade, isto é, o objeto medido é representado como uma fração (ou múltiplo) do metro.
> - Métrica é uma extrapolação de medidas, isto é, uma conclusão com base em dados finitos. Segundo essa definição, uma métrica pode ser entendida como a relação entre duas medidas de grandezas iguais ou diferentes. Um exemplo seria o número de defeitos identificados em um lote de produtos finalizados (defeitos [número] / total do lote [número]).
> - Na engenharia de software existem milhares de métricas de medidas, mas nenhuma é totalmente precisa. Por isso existem as medidas diretas e as medidas indiretas.

### 3.1 Métricas de Controle ou Processo
- Métricas de controle (às vezes, chamadas de métricas de processo) apoiam o gerenciamento de processos.
- Exemplos de métricas de controle ou de processo:
  - Esforço médio;
  - Tempo necessário para reparar defeitos relatados.
- Podem ser usados três tipos de métricas de processo:
  1. O tempo que um determinado processo leva para ser concluído. Esse tempo pode ser o total dedicado ao processo, o tempo de calendário, o tempo gasto no processo por determinados engenheiros etc.
  2. Os recursos necessários para um determinado processo. Os recursos podem incluir o esforço total, em pessoas-dia; custos de viagens ou recursos de computadores.
  3. O número de ocorrências de um determinado evento. Exemplos de eventos que podem ser monitorados incluem o número de defeitos detectados durante a inspeção de código, o número de alterações de requisitos solicitadas, o número de relatórios de defeitos em um sistema entregue e o número médio de linhas de código modificadas em resposta a uma mudança de requisitos.

> [!CAUTION] OBSERVAÇÃO:
> - Quando se fala de recursos, são no geral, tanto recursos humanos quanto recursos materiais.

### 3.2 Métricas de Previsão ou Produto
- As métricas de previsão (às vezes, chamadas de métricas de produto) estão associadas ao próprio software.
- Exemplos de métricas de previsão:
  - Complexidade ciclomática de um módulo;
  - Comprimento médio de identificadores em um programa;
  - Número de atributos e operações associadas com classes em um projeto (design).
- As métricas de controle (processo) e de previsão (produto) podem influenciar a tomada de decisões de gerenciamento.

> [!TIP] DICAS:
> - Lembrando que previsão é produto e controle é processo.
> - Complexidade ciclomática é uma métrica do campo da engenharia de software, desenvolvida por Thomas J. McCabe em 1976, e serve para mensurar a complexidade de um determinado módulo (uma classe, um método, uma função etc.), a partir da contagem do número de caminhos independentes que ele pode executar até o seu fim. É uma métrica que era do paradigma estruturado, mas que pode ser aplicada na orientação ao objeto, ainda que para ela existam métricas específicas.

### 3.3 Métricas Internas e Externas (ISO 9126)
- Métricas internas referem-se a medições de um produto de software a partir de suas próprias características internas, sem a necessidade de execução dos programas. São medidas estáticas.
  - Exemplo: linhas de código, número de erros encontrados em revisões.
- Métricas externas são aplicáveis à execução de software. Devem ser usadas para avaliar o comportamento do software, quando usado em situações específicas; predizer a qualidade real no uso; e avaliar e indicar se o produto satisfaz às verdadeiras necessidades durante a operação real pelo usuário.

## 4. Métricas de Produto
- São utilizadas para quantificar atributos internos de um sistema de software.
- Infelizmente, as características de software que podem ser facilmente medidas, como tamanho e complexidade ciclomática, não têm uma relação clara e consistente com atributos da qualidade, como compreensibilidade e manutenibilidade.
- Por mais que se veja que um programa tem incontáveis voltas, possui uma complexidade ciclomática alta, não quer dizer que ele é necessariamente um programa difícil de manter. A complexidade pode se dar pelo fato de o software ser bem-feito.
- As métricas de produtos enquadram-se em duas classes:

### 4.1 Métricas Dinâmicas
- São coletadas por medições feitas em um programa em execução.
- Essas métricas podem ser coletadas durante o teste de sistema ou após o sistema ter entrado em uso.
- Exemplo: número de relatórios de defeitos ou o tempo consumido para concluir uma computação.
- Métricas dinâmicas ajudam a avaliar a eficiência e a confiabilidade de um sistema.

### 4.2 Métricas Estáticas
- São coletadas por medições feitas de representações do sistema, como o projeto (design), o programa ou a documentação.
- Métricas estáticas ajudam a avaliar a complexidade, a compreensibilidade e a manutenibilidade de um sistema ou de seus componentes.
- Veja que não é de maneira direta, existe uma certa subjetividade. Mas se perceber que um software tem o nome de um método muito complexo, com diversos parâmetros, entenda que ele será muito mais difícil de manter do que um método mais enxuto.

> [!TIP] DICAS:
> - Se o aluno tiver interesse em conhecer todas as métricas, é de bom tom ler a tabela que consta no material original, que ajudará muito no entendimento do assunto.

## 5. Medições
- As medições de um sistema de software podem ser usadas de duas maneiras:
  1. Para atribuir um valor aos atributos da qualidade do sistema. Medindo as características dos componentes do sistema e, em seguida, agregando essas medições, pode ser possível avaliar atributos da qualidade do sistema, como a manutenibilidade.
  2. Para identificar os componentes do sistema cuja qualidade está aquém do padrão. As medições podem identificar componentes individuais com características que se desviam da norma. Por exemplo, é possível medir componentes para descobrir aqueles com maior complexidade. Esses componentes são mais propensos a conter defeitos, pois a complexidade torna mais provável que o desenvolvedor do componente tenha cometido erros.

## 6. Atributos de Qualidade
- Atributos da qualidade, como a manutenibilidade, a compreensibilidade e a usabilidade, são atributos externos que se relacionam com a forma como os desenvolvedores e os usuários experimentam o software.
- Para fazer um julgamento sobre esses atributos, deve-se medir alguns atributos internos do software (como o seu tamanho e a sua complexidade) e presumir que eles estão relacionados às características da qualidade que estão no foco da preocupação.

> [!CAUTION] OBSERVAÇÃO:
> - Devido a essas medições não serem totalmente objetivas que surgiu o ponto de função. Foi uma forma encontrada de ter uma métrica que ajudasse naquilo que só a linha de código não resolveria.