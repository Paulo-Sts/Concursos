# Arquitetura Cliente-Servidor

## 1. Conceitos Fundamentais

### 1.1 Definição e Contexto Histórico
- Surgiu na década de 1980.
- Foi criada para melhorar a distribuição de processamento e armazenamento de dados, em contraste com os sistemas centralizados de *mainframes*.
- Veio para separar as aplicações e os sistemas em duas partes distintas:
  - Cliente: parte que faz as solicitações.
  - Servidor: parte que faz o processamento das solicitações.
- Objetivo: melhorar a eficiência, escalabilidade e manutenção de sistemas, distribuindo tarefas entre clientes e servidores.
- Com objetivos mais claros sobre o que cada parte vai fazer, fica mais fácil realizar alterações no sistema, como adicionar ou retirar funcionalidades.

> [!CAUTION] OBSERVAÇÃO: 
> A arquitetura cliente-servidor veio para separar as aplicações em duas partes: cliente (solicitações) e servidor (processamento). Não faria sentido que uma camada do servidor pudesse ser tanto do cliente quanto do servidor.

### 1.2 Sistemas Distribuídos na Arquitetura Cliente-Servidor
- Na arquitetura cliente-servidor, faz-se uso de sistemas distribuídos.
- A parte do cliente e a parte do servidor não necessariamente estão na mesma máquina.
- Utilizam-se computadores diferentes, mas o sistema funciona como um único sistema, mesmo que, fisicamente, a aplicação esteja dividida.
- Esses computadores, também chamados de nós, interagem entre si para alcançar um objetivo comum: fazer com que o sistema funcione.
- Sistemas distribuídos aproveitam a arquitetura cliente-servidor para organizar a comunicação e a distribuição de tarefas, mas expandem além disso para incluir maior flexibilidade, resiliência e escalabilidade.

> [!CAUTION] OBSERVAÇÃO: 
> Caso caia alguma questão afirmando que não é possível ter um sistema com arquitetura cliente-servidor em mais de um computador, isso é falso. Os sistemas distribuídos podem sim ter cliente e servidor em máquinas diferentes.

### 1.3 Vantagens da Arquitetura Cliente-Servidor
- Centralização de recursos: concentração de dados em um servidor ou outros servidores centralizados.
- Escalabilidade: em um sistema mais distribuído, na hora de escalar (evoluir o sistema), é mais fácil identificar exatamente o que deve ser modificado.
- Manutenção e atualização: por estar mais separado, é mais fácil localizar elementos específicos.
- Segurança: as partes trabalham de forma independente, facilitando o tratamento de segurança.

### 1.4 Desvantagens da Arquitetura Cliente-Servidor
- Dependência do Servidor: se o servidor cair, o cliente não consegue acessar as informações. Na parte do servidor fica a lógica de negócio.
- Complexidade de Rede.
- Latência: atraso na solicitação por conta da separação entre cliente e servidor.

### 1.5 Exemplos de Uso
- Aplicações *Web*.
- Sistemas de Bancos de Dados.
- Serviços de *e-mail*.

## 2. Cliente

### 2.1 Definição
- É a parte do sistema que interage diretamente com o usuário final.
- Exemplo: em uma rede social, a tela de *login* que o usuário vê é a parte do cliente.
- O cliente envia solicitações ao servidor, que processa essas solicitações e retorna os resultados ao cliente.

### 2.2 Responsabilidades do Cliente
- Interação com o Usuário.
- Envio de Solicitações ao Servidor.
- Recebimento e Processamento de Respostas.
- Apresentação dos Resultados ao Usuário.
- Gerenciamento de Estado.
- Validação de Dados.

### 2.3 Exemplos de Cliente
- Navegadores *Web* (Chrome, Firefox, Edge).
- Aplicativos Móveis (WhatsApp, Instagram, Uber).
- Aplicativos *Desktop* (Outlook, Slack, Spotify).
- Clientes de Linha de Comando (Git, *AWS CLI*).

## 3. Servidor

### 3.1 Definição
- É a parte do sistema que fornece serviços ou recursos aos clientes.
- Processa solicitações recebidas dos clientes, executa a lógica de negócios necessária e retorna as respostas adequadas.
- O usuário insere informações no cliente, e o servidor garante que isso não infrinja a lógica de negócio.
- O servidor centraliza a lógica de processamento, a gestão de dados e a execução das operações necessárias para o funcionamento da aplicação.

### 3.2 Responsabilidades do Servidor
- Processamento de Solicitações.
- Execução da Lógica de Negócios.
- Gestão de Dados.
- Comunicação com Outros Sistemas.
- Resposta ao Cliente.
- Segurança.
- Escalabilidade e Desempenho.
- Manutenção e Atualização.

### 3.3 Exemplos de Servidores
- Servidores *Web* (Apache *HTTP Server*, Nginx).
- Servidores de Aplicação (WildFly, Apache Tomcat).
- Servidores de Banco de Dados (MySQL, PostgreSQL).
- Servidores de Mensageria (RabbitMQ, ActiveMQ).

> [!CAUTION] OBSERVAÇÃO: 
> Os servidores de aplicação podem ser executados nos lados do cliente ou do servidor de uma aplicação cliente/servidor? Não. O servidor de aplicação fica no lado do servidor. Essa arquitetura veio para fazer a separação dessas duas partes.

> [!TIP] DICAS: 
> O papel do servidor é fornecer serviços e recursos. O cliente é quem inicia a comunicação e solicita os serviços.

## 4. Quadro Comparativo: Cliente x Servidor

| CARACTERÍSTICA | CLIENTE | SERVIDOR |
|----------------|---------|----------|
| Função principal | Interage com o usuário e faz solicitações | Fornece serviços e processa solicitações |
| Inicia a comunicação | Sim | Não (responde às solicitações) |
| Processa lógica de negócios | Geralmente não | Sim (centraliza a lógica) |
| Gerencia dados | Não | Sim |
| Exemplos | Navegadores, apps móveis, apps *desktop* | Apache, Tomcat, MySQL, RabbitMQ |

## 5. Questões de Fixação

### Questão 01
(CESPE-CEBRASPE/2024/CAPES/ANALISTA EM CIÊNCIA E TECNOLOGIA/ESPECIALIDADE: INFORMÁTICA) Acerca de servidores de aplicação, julgue o próximo item.

Os servidores de aplicação podem ser executados nos lados do cliente ou do servidor de uma aplicação do tipo cliente/servidor.

Gabarito: Errado (E). O servidor de aplicação fica no lado do servidor. Essa arquitetura veio para fazer a separação dessas duas partes. Não faria sentido que uma camada do servidor pudesse ser tanto do cliente quanto do servidor.

### Questão 02
(FUNCERN/2024/PREFEITURA DE CARNAÚBA DOS DANTAS/RN/ANALISTA LEGISLATIVO/ESPECIALIDADE TECNOLOGIA DA INFORMAÇÃO) Em redes de computadores, na arquitetura cliente-servidor, o papel que, geralmente, o servidor desempenha é

a) iniciar a comunicação.
b) fornecer serviços e recursos.
c) solicitar serviços e recursos.
d) facilitar a comunicação entre clientes.

Gabarito: B. O servidor é responsável por pegar as solicitações do cliente, fazer o processamento da lógica de negócios e gerenciamento de dados.

- a) Esse é o papel do cliente.
- c) Essa parte é do cliente.
- d) O servidor pode facilitar a comunicação entre os clientes, mas esse não é o papel que geralmente desempenha.

### Questão 03
(CESPE-CEBRASPE/2021/APEX BRASIL/ANALISTA/TECNOLOGIA DA INFORMAÇÃO E COMUNICAÇÃO) Assinale a opção que corresponde a uma característica típica de uma aplicação *web* de grande porte construída como sistema distribuído em uma arquitetura cliente/servidor moderna.

a) eliminação de considerações relacionadas à localização dos dados físicos e às estratégias de sincronização dos dados distribuídos geograficamente
b) ambiente de execução heterogêneo composto de vários tipos de *hardware*, conexões de rede, sistemas operacionais, servidores e navegadores
c) autonomia e independência funcional em relação aos componentes que integram a aplicação, como bases de dados, componentes legados e componentes de prateleira
d) uso estrito da lógica de aplicação do lado do cliente para enriquecer a camada de apresentação com interfaces dinâmicas

Gabarito: B.

- a) Essas partes são muito importantes em um sistema. Podem até ser abstraídas, mas eliminadas não.
- b) Os sistemas distribuídos fazem uso da arquitetura cliente-servidor, que vai estar sendo aplicada em vários computadores distintos. Isso implica que eles vão ter *hardwares* diferentes, conexões de rede diferentes, sistemas operacionais, servidores e navegadores diferentes.
- c) Essa descrição se encaixa muito melhor para a arquitetura de microsserviços.
- d) É o contrário disso.

### GABARITO OFICIAL

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | B |
| 03 | B |

> [!TIP] DICAS: 
> - Cliente: interage com o usuário, faz solicitações, recebe respostas.
> - Servidor: fornece serviços, processa solicitações, executa lógica de negócios, gerencia dados.
> - Sistemas distribuídos permitem que cliente e servidor estejam em máquinas diferentes.
> - Vantagens: centralização, escalabilidade, manutenção facilitada, segurança.
> - Desvantagens: dependência do servidor, complexidade de rede, latência.