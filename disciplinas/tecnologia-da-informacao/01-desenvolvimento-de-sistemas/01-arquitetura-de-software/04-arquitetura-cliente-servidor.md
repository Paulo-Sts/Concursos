# Desenvolvimento Web: Arquitetura Cliente Servidor

## 1. Arquitetura Cliente Servidor
- Abordagem surgida na década de 1980 para melhorar a distribuição de processamento e armazenamento de dados em relação aos mainframes.
- Divisão de responsabilidades entre uma parte que faz solicitações (cliente) e outra que realiza o processamento (servidor).
- O cliente representa o usuário que se comunica com a aplicação para solicitar informações.
- O servidor realiza o tratamento das informações, armazenamento em banco de dados e retorno da resposta ao solicitante.
- Foco na eficiência, escalabilidade e facilidade de manutenção e alteração das funcionalidades do sistema.

## 2. Sistemas Distribuídos
- Caracterizam-se pelo fato de o cliente e o servidor não estarem necessariamente operando na mesma máquina física.
- Utilização de computadores diferentes, chamados de nós, que interagem para o funcionamento unificado do sistema.
- A arquitetura permite que uma aplicação esteja estruturada e distribuída em mais de um computador simultaneamente.
- Proporcionam maior flexibilidade, resiliência e escalabilidade ao expandir a comunicação para além de um único servidor.

> [!CAUTION] OBSERVAÇÃO: 
> - É falso afirmar que uma arquitetura cliente-servidor não pode ser implementada em mais de um computador.
> - Sistemas distribuídos operam em ambientes heterogêneos compostos por diversos tipos de hardware, sistemas operacionais e conexões de rede.

## 3. Vantagens e Desvantagens da Arquitetura
| CATEGORIA | ASPECTOS POSITIVOS | DESAFIOS E LIMITAÇÕES |
|---|---|---|
| Gestão de recursos | Centralização de dados e recursos em servidores específicos | Dependência do servidor para acesso às informações |
| Infraestrutura | Facilidade de evolução e escalabilidade do sistema ⟶ melhor localização de pontos de melhoria | Complexidade de rede e latência nas solicitações por conta da separação física |
| Operação | Manutenção e atualização facilitadas pela separação de partes específicas | Atrasos causados pelo tempo de resposta da rede entre as pontas |
| Proteção | Segurança aprimorada pelo trabalho independente e isolado das partes | Lógica de negócio concentrada inteiramente no servidor |

## 4. O Papel do Cliente
- Parte do sistema que realiza a interação direta com o usuário final.
- Responsável por enviar solicitações ao servidor e apresentar os resultados processados ao usuário.
- Atua em navegadores web, aplicativos móveis, aplicativos desktop e clientes de linha de comando.
- Exemplos: Chrome, Firefox, WhatsApp, Instagram, Slack, Spotify e Git.

### 4.1 Responsabilidades do Cliente
- Interação direta com o usuário;
- Envio de solicitações ao servidor;
- Recebimento e processamento de respostas;
- Apresentação dos resultados ao usuário;
- Gerenciamento de estado;
- Validação de dados.

## 5. O Papel do Servidor
- Fornece serviços ou recursos aos clientes a partir do processamento das solicitações recebidas.
- Centraliza a lógica de processamento, a gestão de dados e a execução das operações necessárias.
- Garante que a entrada de informações e as operações não infrinjam as regras de negócio definidas.
- Exemplos: Apache HTTP Server, Nginx, WildFly, Apache Tomcat, MySQL e PostgreSQL.

### 5.1 Responsabilidades do Servidor
- Processamento de solicitações;
- Execução da lógica de negócios;
- Gestão de dados;
- Comunicação com outros sistemas;
- Resposta ao cliente;
- Segurança;
- Escalabilidade e desempenho;
- Manutenção e atualização.

> [!TIP] DICAS: 
> - O papel primordial do servidor é fornecer serviços e recursos, enquanto o cliente inicia a comunicação e solicita esses recursos.
> - Lembre-se que em sistemas distribuídos de grande porte, hardwares e sistemas operacionais variados compõem um ambiente de execução heterogêneo.

> [!CAUTION] OBSERVAÇÃO: 
> - Servidores de aplicação não podem ser executados no lado do cliente; eles pertencem estritamente à camada de servidor para manter a separação da arquitetura.
> - Sistemas distribuídos não eliminam considerações sobre localização de dados ou sincronização; esses itens são fundamentais para o sucesso da aplicação.
> - A autonomia e independência funcional total entre componentes (como bases de dados) é uma característica típica de microsserviços, não da cliente-servidor tradicional.