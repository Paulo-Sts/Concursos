# Desenvolvimento Web: Arquitetura Cliente Servidor 2

## 1. Comunicação Cliente-Servidor
- Interação baseada fundamentalmente no modelo de solicitação e resposta entre duas partes distintas.
- O cliente é a entidade que inicia a comunicação enviando uma solicitação, enquanto o servidor recebe, processa a lógica de negócios e devolve a resposta ao usuário.

### 1.1 Comunicação Síncrona
- O cliente envia uma solicitação ao servidor e interrompe suas atividades, aguardando a resposta antes de prosseguir com outras operações;
- As ações do usuário permanecem bloqueadas até que a etapa seguinte seja liberada pelo processamento do servidor;
- Exemplo: carregamento de uma página web via requisição http get, onde a interface só fica disponível após a carga completa.

### 1.2 Comunicação Assíncrona
- O usuário envia uma solicitação para o servidor, mas permanece livre para realizar outras tarefas no sistema sem necessidade de resposta imediata;
- Ideal para operações que demandam tempo de processamento elevado ou atualizações parciais de interface;
- Exemplo: tecnologia ajax, que permite atualizar partes de uma página na internet sem a necessidade de recarregar o conteúdo por inteiro.

## 2. Arquitetura Multicamadas (N-Tier)
- Representa uma evolução da arquitetura cliente-servidor onde a aplicação é fragmentada em diversos níveis independentes.
- Permite que cada camada detenha uma responsabilidade específica, facilitando a gestão e separação de projetos.

### 2.1 Modelos de Camadas
- 2-Tier ⟶ arquitetura composta por duas camadas, dividindo o sistema entre cliente (interface) e servidor (processamento e lógica);
- 3-Tier ⟶ forma mais comum de separação, organizada em camadas de apresentação, negócios e dados;
- N-Tier ⟶ arquitetura com duas ou mais camadas que pode incluir níveis auxiliares como serviços restful, integração e cache.

### 2.2 Responsabilidades na Arquitetura de Quatro Camadas
| CATEGORIA | DESCRIÇÃO DA FUNÇÃO | SERVIDOR CORRESPONDENTE |
|---|---|---|
| Acesso | Navegação realizada por meio de browsers | Clientes |
| Dados | Gestão de todas as informações necessárias | Servidor de banco de dados |
| Apresentação | Local onde ocorrem as alterações de interface | Servidor web |
| Lógica | Execução e alteração das regras de negócio | Servidor de aplicações |

## 3. Redes Peer-to-Peer (P2P)
- Redes de computadores onde cada nó atua simultaneamente como cliente e como servidor, promovendo comunicação direta entre os pontos.
- Propõe a descentralização do processamento funcional, distribuindo as responsabilidades igualmente entre as estações da rede.

### 3.1 Características do Modelo P2P
- Descentralização ⟶ elimina a necessidade de um servidor central, pois cada nó assume papéis de fornecimento e requisição;
- Igualdade entre os nós ⟶ todas as partes possuem as mesmas capacidades operacionais;
- Redundância ⟶ os dados são replicados em múltiplos nós para garantir disponibilidade mesmo em situações de falha técnica;
- Escalabilidade ⟶ facilidade para o crescimento e evolução do sistema conforme novos participantes ingressam na rede;
- Autonomia e Independência ⟶ cada estação opera de forma independente e se adapta dinamicamente às mudanças de estado da rede.

### 3.2 Tipos de Organização P2P
- Estruturadas ⟶ utilizam uma estrutura de dados bem definida para localização eficiente de recursos, geralmente baseada em chaves únicas como dht;
- Não estruturadas ⟶ sem organização predefinida, utilizando algoritmos de busca que enviam solicitações para todos os nós vizinhos;
- Híbridas ⟶ sistemas que mesclam características de redes estruturadas e não estruturadas para otimizar a organização e flexibilidade.

## 4. Dinâmica de Papéis Simultâneos
- Em arquiteturas multicamadas, uma mesma aplicação tem a capacidade de atuar como servidor e cliente de forma concomitante para diferentes destinos.
- A camada de lógica de negócios funciona como servidor para o usuário final, mas assume o papel de cliente ao realizar requisições para a camada de banco de dados.

> [!TIP] DICAS: 
> - O ajax (asynchronous javascript and xml) é o exemplo clássico de comunicação assíncrona cobrado em provas para justificar a fluidez de navegação.
> - Em arquiteturas n-tier, quanto maior a separação das camadas, maior é a especialização e a facilidade de manutenção de cada componente.

> [!CAUTION] OBSERVAÇÃO: 
> - A sobrecarga de servidores permanece como um desafio real de infraestrutura, independentemente da melhoria na capacidade de processamento nos últimos anos.
> - Nas redes p2p, a queda de um único nó não inviabiliza a aplicação, ao contrário do modelo centralizado onde a falha do servidor interrompe o serviço.
> - Na arquitetura 2-tier, a lógica de negócios não possui local fixo, podendo residir tanto na interface do usuário quanto na parte de dados.