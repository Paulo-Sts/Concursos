# Anotações

# SISTEMA DE BANCO DE DADOS AVANÇADO - ALTA DISPONIBILIDADE

## 1. ALTA DISPONIBILIDADE (HIGH AVAILABILITY - HA)

- É o termo utilizado para descrever a característica de um sistema com alta capacidade de permanecer disponível pelo maior tempo possível durante a execução de serviços críticos.

- Tem como característica principal a garantia das funcionalidades e alta **tolerância a falhas** de hardware, software e energia por meio de dispositivos que gerem **redundância** no sistema.

- A redução dos pontos de falha minimiza os períodos de interrupção no serviço.

### 1.1 Parâmetros de Medição

O grau de disponibilidade é medido por meio de dois parâmetros:

| Parâmetro | Significado |
|-----------|-------------|
| **MTBF** (Mean Time Between Failures) | Tempo Médio entre Falhas. Indica o intervalo médio de tempo entre uma falha e outra. |
| **MTTR** (Mean Time to Repair) | Tempo Médio de Recuperação. Refere-se ao tempo necessário para restaurar o serviço após uma falha. |

- Em ambientes de alta estabilidade, como alguns sistemas de banco de dados, é possível observar períodos superiores a 700 dias sem falhas.

- Em muitos casos práticos, a recuperação ocorre em poucas horas, frequentemente inferior a duas horas.

> ### 1.2 Planos de Contingência
> - Os planos de contingência utilizam, entre outros recursos, os parâmetros MTBF e MTTR.
> - Esses parâmetros são fundamentais para a garantia da **continuidade dos negócios**, objetivo central dos planos de contingência.
> - Tais planos podem ser denominados de diferentes formas, como:
>   - Plano de continuidade de negócios.
>   - Plano de recuperação de desastres.
> - O conhecimento e o monitoramento dessas métricas são essenciais para a elaboração eficaz de planos de contingência.

## 2. CLUSTER

- **Cluster** é uma implementação de compartilhamento de recursos computacionais, utilizando **dois ou mais dispositivos de computação**.

- Pode ser definido como um agrupamento de computadores, também chamados de **"nós"**, conectados entre si e trabalhando em conjunto com a finalidade de aumentar seu desempenho na execução das tarefas.

- Normalmente, o cluster funciona como uma camada ou barramento intermediário, responsável por integrar e coordenar os recursos disponíveis.

- O poder computacional do cluster é distribuído entre vários nós, que atuam de forma conjunta para executar as tarefas de processamento.

- Os "nós" podem estar conectados através de uma **rede local**, sendo mais comuns os padrões da **Ethernet** por terem menor custo e permitirem a retirada ou a inclusão de nós sem alterar seu funcionamento.

### 2.1 Vantagens de um Cluster

- **Alto desempenho**
- **Escalabilidade**
- **Tolerância a falhas**
- **Baixo custo**
- **Independência de fornecedores**

> ### 2.2 Cluster em Bancos de Dados
> - O cluster é uma técnica amplamente utilizada e implementada por diversos fornecedores e softwares.
> - Atualmente, é comum sua aplicação em ambientes de bancos de dados, com destaque para soluções como o **Oracle RAC** (Real Application Clusters), entre outras.
> - Com a crescente migração de sistemas para a nuvem, muitos SGBDs passaram a operar em ambientes *cloud*, nos quais os recursos são automaticamente distribuídos e gerenciados em clusters.
> - Apesar dessa evolução tecnológica, editais de concursos públicos que abordam o tema de alta disponibilidade costumam se basear nos modelos **tradicionais** de clusters de banco de dados.

### 2.3 Tipos de Clusters

Existem 3 tipos principais de clusters:

| Tipo | Descrição |
|------|-----------|
| **HPC** (High Performance Computing) | Alta Performance. Utilizado quando há necessidade de elevado poder computacional para execução de tarefas complexas. |
| **LB** (Load Balance) | Balanceamento de Carga. A tarefa é distribuída entre vários nós para otimizar o uso dos recursos. |
| **HA** (High Availability) | Alta Disponibilidade. Tem como objetivo garantir que os sistemas permaneçam operacionais continuamente. |

## 3. CLUSTER DE ALTA PERFORMANCE (HPC)

- São utilizados para se obter **alto desempenho em menor tempo** para grandes processamentos.

- Tratam-se de máquinas com vários processadores, com maior poder computacional, podendo alcançar maior velocidade de processamento.

- São usados na necessidade de se processar **grandes quantidades de dados**, como em:
  - Resultados de concursos.
  - Eleições.
  - Vestibulares.
  - Grandes variedades de dados e cálculos complexos.

- São comuns em ambientes científicos e de pesquisa que demandam processamento intensivo.

- Exemplo: **Appliances de Data Warehouse (DW)** — dispositivos que combinam hardware e software especializados em um único equipamento, projetado para desempenho e eficiência específicos.

> ### 3.1 Exemplo Prático
> - Em um projeto de pós-doutorado realizado em parceria com o Instituto Butantan, foi utilizado um cluster HPC para análises biológicas avançadas.
> - As análises envolvem o monitoramento de proteínas e a sequência do DNA em diferentes condições.
> - Todo esse processamento é executado no cluster de alta performance do Instituto Butantan.

## 4. CLUSTER DE BALANCEAMENTO DE CARGA (LOAD BALANCE - LB)

- As tarefas são divididas igualmente entre os nós individuais ou divididas por *performance*.

- Cada nó recebe uma parte de acordo com sua capacidade operacional.

- As requisições são direcionadas para o nó que estiver com o **menor número de tarefas**.

- São utilizados normalmente em **aplicações Web**, cujas requisições podem aumentar em função da demanda e comprometer o desempenho computacional.

> ### 4.1 Exemplo Prático
> - No sistema da Justiça Federal, conhecido como **PJ-e** (Processo Judicial Eletrônico), a camada de aplicação é composta por múltiplos nós.
> - Entretanto, existe uma limitação no aumento do número de nós, pois cada nó realiza consultas ao banco de dados, o que pode gerar gargalos e limitar a escalabilidade do sistema.
> - É necessário implementar estratégias de balanceamento de carga entre os nós para otimizar o desempenho e evitar sobrecargas.

## 5. CLUSTER DE ALTA DISPONIBILIDADE (HIGH AVAILABILITY - HA)

- Os clusters de HA buscam a **alta disponibilidade dos sistemas de processamento sem paradas**, por meio de:
  - Monitoramento de possíveis falhas de HW (nós) ou de SW.
  - Soluções de **replicação de dados** entre computadores.

- **Máquinas podem ser substituídas sem indisponibilidade do sistema.**

- Há **redundância de HW** com replicação de dados.

- Clusters de HA são utilizados amplamente em:
  - Instituições financeiras.
  - *E-commerce*.
  - Aeroportos.
  - Hospitais.
  - Outros sistemas críticos.

- Sistemas críticos, como os de controle de tráfego aéreo, são projetados para operar com alta disponibilidade, garantindo que não sofram interrupções.

- Em ambientes de *big data*, bancos de dados NoSQL frequentemente utilizam replicação horizontal dos nós para distribuir a carga e assegurar a continuidade do serviço.

> ### 5.1 HA em Bancos de Dados
> - A concepção tradicional de cluster envolve também o aspecto de **hardware**, sendo uma abordagem que vem evoluindo ao longo do tempo.
> - Essa distinção é relevante, pois as questões sobre clusters podem ser abordadas de diversas formas em estudos clássicos de bancos de dados.

## 6. ESCALABILIDADE

Existem 2 tipos de escalabilidade:

| Tipo | Descrição |
|------|-----------|
| **Vertical (*Scale Up*)** | Adicionar recursos em um **único nó** do sistema (mais memória, processador ou um disco rígido mais rápido). |
| **Horizontal (*Scale Out*)** | Adicionar **mais nós** ao sistema, tais como um novo computador com uma aplicação para clusterizar o software. |

### 6.1 Comparação entre os Tipos

- Para aumentar a capacidade de processamento, especialmente em sistemas que utilizam bancos de dados relacionais, é comum investir em **escalabilidade vertical**.

- A escalabilidade vertical pode ser comparada ao crescimento de um único elemento que se torna mais robusto, embora tenha **limites físicos e técnicos**.

- A **escalabilidade horizontal** é característica dos bancos de dados não relacionais (NoSQL), que são amplamente utilizados em soluções de *big data*.

- A escalabilidade horizontal assemelha-se à multiplicação de unidades que compartilham a carga, facilitando a expansão do sistema de forma mais flexível.

> ### 6.2 Relação com Clusters
> - Clusters, em geral, são projetados para aproveitar a **escalabilidade horizontal**, pois fazem sentido quando há dois ou mais nós que aumentam os recursos coletivamente.
> - A escalabilidade horizontal é a estratégia mais eficiente para clusters.
> - A escalabilidade vertical é limitada à ampliação dos recursos de um único nó.

## 7. QUESTÕES COMENTADAS

### Questão 01 (FCC/2020/AL/AP)

**Alta disponibilidade tem a ver com Cluster.**

- Em avaliações, quando se menciona alta disponibilidade no contexto de SGBDs, geralmente trata-se da implementação de **clusters**.
- As bancas examinadoras costumam basear-se em abordagens clássicas presentes em obras de referência da área, nas quais o conceito de cluster é enfatizado como a principal solução para garantir a continuidade dos serviços.

**Gabarito: c**

### Questão 02 (COMPERVE/2020/TJ/RN)

**Requisitos de um SGBD:**

| Alternativa | Análise |
|-------------|---------|
| a) backup e restauração, orientação a objetos e relacionamento complexo | Mistura conceitos que não são obrigatórios para um SGBD (orientação a objetos e relacionamento complexo). |
| b) compartilhamento de dados, fornecimento de múltiplas interfaces e restrições de integridade | ✓ Requisitos clássicos e essenciais de um SGBD. |
| c) acesso multi-usuário, alta disponibilidade e restrições de integridade | Alta disponibilidade **não** é funcionalidade intrínseca ao SGBD — trata-se de estratégia implementada externamente. |
| d) relacionamento complexo entre dados, compartilhamento de dados e orientação a objetos | Conceitos genéricos e misturados; não são requisitos fundamentais. |

**Gabarito: b**

> ### Análise da Questão 02
> - Os requisitos clássicos de um SGBD são: **compartilhamento de dados**, **múltiplas interfaces** e **restrições de integridade**.
> - A **alta disponibilidade** não é uma funcionalidade intrínseca ao SGBD, mas sim uma estratégia implementada externamente por meio de infraestrutura adicional, como clusters ou soluções de replicação.