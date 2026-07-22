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
> - A arquitetura cliente-servidor veio para separar as aplicações em duas partes: cliente (solicitações) e servidor (processamento). Não faria sentido que uma camada do servidor pudesse ser tanto do cliente quanto do servidor.

### 1.2 Sistemas Distribuídos na Arquitetura Cliente-Servidor
- Na arquitetura cliente-servidor, faz-se uso de sistemas distribuídos.
- A parte do cliente e a parte do servidor não necessariamente estão na mesma máquina.
- Utilizam-se computadores diferentes, mas o sistema funciona como um único sistema, mesmo que, fisicamente, a aplicação esteja dividida.
- Esses computadores, também chamados de nós, interagem entre si para alcançar um objetivo comum: fazer com que o sistema funcione.
- Sistemas distribuídos aproveitam a arquitetura cliente-servidor para organizar a comunicação e a distribuição de tarefas, mas expandem além disso para incluir maior flexibilidade, resiliência e escalabilidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Caso caia alguma questão afirmando que não é possível ter um sistema com arquitetura cliente-servidor em mais de um computador, isso é falso. Os sistemas distribuídos podem sim ter cliente e servidor em máquinas diferentes.

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
> - Os servidores de aplicação podem ser executados nos lados do cliente ou do servidor de uma aplicação cliente/servidor? Não. O servidor de aplicação fica no lado do servidor. Essa arquitetura veio para fazer a separação dessas duas partes.

> [!TIP] DICAS: 
> - O papel do servidor é fornecer serviços e recursos. O cliente é quem inicia a comunicação e solicita os serviços.

## 4. Quadro Comparativo: Cliente x Servidor

| CARACTERÍSTICA | CLIENTE | SERVIDOR |
|----------------|---------|----------|
| Função principal | Interage com o usuário e faz solicitações | Fornece serviços e processa solicitações |
| Inicia a comunicação | Sim | Não (responde às solicitações) |
| Processa lógica de negócios | Geralmente não | Sim (centraliza a lógica) |
| Gerencia dados | Não | Sim |
| Exemplos | Navegadores, apps móveis, apps *desktop* | Apache, Tomcat, MySQL, RabbitMQ |