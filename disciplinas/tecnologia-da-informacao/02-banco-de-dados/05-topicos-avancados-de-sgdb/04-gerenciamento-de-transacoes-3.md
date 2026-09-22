# Gerenciamento de Transações 3

## 1. Alta Disponibilidade
- Conceito que descreve a característica de um sistema com alta capacidade de permanecer disponível pelo maior tempo possível durante a execução de serviços críticos.
- Garantia das funcionalidades e alta tolerância a falhas de hardware, software e energia por meio de dispositivos que gerem redundância no sistema.
- A redução dos pontos de falha minimiza os períodos de interrupção no serviço.
- Parâmetros de medição:
  - MTBF (Mean Time Between Failures) - Tempo médio entre falhas;
  - MTTR (Mean Time to Repair/Recovery) - Tempo médio de recuperação.
- Os planos de contingência utilizam esses parâmetros para garantir a continuidade dos negócios.
- Os planos podem ser denominados como plano de continuidade de negócios, plano de recuperação de desastres, entre outras nomenclaturas.

### 1.1 MTBF (Mean Time Between Failures)
- Indica o intervalo médio de tempo entre uma falha e outra.
- Exemplo: se a última falha ocorreu há 30 dias, esse pode ser o tempo médio estimado até a próxima ocorrência.
- Em ambientes de alta estabilidade, como alguns sistemas de banco de dados, é possível observar períodos superiores a 700 dias sem falhas.

### 1.2 MTTR (Mean Time to Repair/Recovery)
- Refere-se ao tempo necessário para restaurar o serviço após uma falha.
- Em muitos casos práticos, a recuperação ocorre em poucas horas, frequentemente inferior a duas horas.
- Esses valores são estimativas médias e podem variar conforme o ambiente, a infraestrutura e as práticas de gestão adotadas.
- O conhecimento e o monitoramento dessas métricas são essenciais para a elaboração eficaz de planos de contingência.

## 2. Cluster
- Implementação de compartilhamento de recursos computacionais utilizando dois ou mais dispositivos de computação.
- Agrupamento de computadores chamados de "nós", conectados entre si e trabalhando em conjunto para aumentar o desempenho na execução das tarefas.
- Funciona como uma camada ou barramento intermediário, responsável por integrar e coordenar os recursos disponíveis.
- O poder computacional do cluster é distribuído entre vários nós que atuam de forma conjunta.
- Os "nós" podem estar conectados através de uma rede local, sendo mais comuns os padrões Ethernet por terem menor custo e permitirem a retirada ou inclusão de nós sem alterar seu funcionamento.
- Vantagens de um cluster:
  - Alto desempenho;
  - Escalabilidade;
  - Tolerância a falhas;
  - Baixo custo;
  - Independência de fornecedores.
- O cluster é amplamente implementado por diversos fornecedores e softwares, com destaque para soluções como o Oracle RAC (Real Application Clusters).
- Com a crescente migração para a nuvem, muitos SGBDs passaram a operar em ambientes cloud, onde os recursos são automaticamente distribuídos e gerenciados em clusters.
- Em concursos públicos, o tema de alta disponibilidade costuma se basear nos modelos tradicionais de clusters de banco de dados, com a computação em nuvem abordada separadamente em tópicos específicos.

## 3. Tipos de Cluster
- Existem três tipos principais de clusters.

### Tabela
| TIPO DE CLUSTER | DESCRIÇÃO |
|-----------------|-----------|
| Alta performance (HPC) | Utilizado para elevado poder computacional em tarefas complexas |
| Balanceamento de carga (LB) | Distribuição de tarefas entre nós para otimizar recursos |
| Alta disponibilidade (HA) | Garantia de operação contínua dos sistemas |

### 3.1 Cluster de Alta Performance (HPC - High Performance Computing)
- Utilizado quando há necessidade de elevado poder computacional para execução de tarefas complexas.
- Comum em ambientes científicos e de pesquisa que demandam processamento intensivo.
- Exemplo: projeto de pós-doutorado em parceria com o Instituto Butantan para análises biológicas avançadas sobre a lagarta-do-fogo, envolvendo monitoramento de proteínas e sequência de DNA em diferentes condições (exposição a bactérias, vírus e pesticidas), com processamento automatizado em Python no cluster do Instituto.
- Utilizado para processar grandes quantidades de dados, como resultados de concursos, eleições e vestibulares, ou grandes variedades de dados como cálculos.
- Exemplo: appliances de Data Warehouse (DW), que combinam hardware e software especializados em um único equipamento para desempenho e eficiência específicos.
- Exemplo recente: durante a última eleição, um cluster da Oracle apresentou atrasos no processamento dos dados eleitorais (normalmente duas horas, mas levou entre quatro e seis horas), embora o sistema tenha continuado funcionando adequadamente.

### 3.2 Cluster de Balanceamento de Carga (Load Balance - LB)
- As tarefas são divididas igualmente entre os nós individuais ou divididas por performance.
- Cada nó recebe uma parte de acordo com sua capacidade operacional.
- As requisições são direcionadas para o nó que estiver com o menor número de tarefas.
- Utilizados normalmente em aplicações Web, cujas requisições podem aumentar em função da demanda e comprometer o desempenho computacional.
- Exemplo: sistema da Justiça Federal (PJ-e - Processo Judicial Eletrônico), onde a camada de aplicação é composta por múltiplos nós que podem ser adicionados conforme a demanda.
- Existe limitação no aumento do número de nós, pois cada nó realiza consultas ao banco de dados, o que pode gerar gargalos.

### 3.3 Cluster de Alta Disponibilidade (HA - High Availability)
- Buscam a alta disponibilidade dos sistemas de processamento sem paradas.
- Monitoramento de possíveis falhas de hardware (nós) ou de software e soluções de replicação de dados entre computadores.
- Máquinas podem ser substituídas sem indisponibilidade do sistema.
- Há redundância de hardware com replicação de dados.
- Utilizados amplamente em instituições financeiras, e-commerce, aeroportos, hospitais e outros sistemas críticos.
- Exemplo: sistemas de controle de tráfego aéreo são projetados para operar com alta disponibilidade, garantindo que não sofram interrupções.
- Em big data, bancos de dados NoSQL frequentemente utilizam replicação horizontal dos nós para distribuir a carga e assegurar a continuidade do serviço, adotando estratégias de HA geralmente implementadas a nível de software.
- A concepção tradicional de cluster envolve também o aspecto de hardware, sendo uma abordagem que vem evoluindo ao longo do tempo.

## 4. Escalabilidade
- Duas formas principais de aumentar a capacidade de processamento.

### 4.1 Escalabilidade Vertical (Scale Up)
- Adicionar recursos em um único nó do sistema (mais memória ou um disco rígido mais rápido).
- Comum em bancos de dados relacionais.
- Exemplo: camada de aplicação do sistema PJ-e, onde um servidor central responde pelas operações.
- Pode ser comparada ao crescimento de um único elemento que se torna mais robusto, embora tenha limites físicos e técnicos.
- É a estratégia limitada à ampliação dos recursos de um único nó.

### 4.2 Escalabilidade Horizontal (Scale Out)
- Adicionar mais nós ao sistema, como um novo computador com uma aplicação para clusterizar o software.
- Característica dos bancos de dados não relacionais (NoSQL), amplamente utilizados em soluções de big data.
- Consiste na adição de múltiplos nós, distribuindo a carga de trabalho entre eles.
- Assemelha-se à multiplicação de unidades que compartilham a carga, facilitando a expansão do sistema de forma mais flexível.
- Clusters são projetados para aproveitar a escalabilidade horizontal, pois fazem sentido quando há dois ou mais nós que aumentam os recursos coletivamente.
- É a estratégia mais eficiente para clusters.

> [!TIP] DICAS: 
> - MTBF ⟶ tempo entre falhas (quanto maior, melhor).
> - MTTR ⟶ tempo para recuperar (quanto menor, melhor).
> - Escalabilidade vertical ⟶ "crescer para cima" (melhorar o que já existe).
> - Escalabilidade horizontal ⟶ "crescer para os lados" (adicionar mais unidades).
> - HPC ⟶ processamento científico e pesquisa.
> - Load Balance ⟶ distribuição de tarefas em aplicações web.
> - HA ⟶ sistemas críticos que não podem parar.

> [!CAUTION] OBSERVAÇÃO: 
> - Alta disponibilidade não é uma funcionalidade intrínseca ao SGBD, mas sim uma estratégia implementada externamente por meio de infraestrutura adicional, como clusters ou soluções de replicação.
> - Os recursos de um cluster aumentam por meio da adição de nós (escalabilidade horizontal), não pela ampliação de um único nó (escalabilidade vertical).