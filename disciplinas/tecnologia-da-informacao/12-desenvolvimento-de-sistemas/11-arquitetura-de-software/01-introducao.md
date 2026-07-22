# Introdução à Arquitetura de Software

## 1. Conceitos Fundamentais
- Conforme a norma ISO/IEC/IEEE 42.010:2022, arquitetura de software é a estrutura fundamental de um sistema, composta por suas partes, os relacionamentos entre essas partes e o relacionamento com o ambiente, projetada para atender aos requisitos do sistema.
- Permite que, no desenvolvimento de projetos, seja feito o melhor uso possível do tempo e do código.
- Todos os projetos de software atuais seguem algum tipo de arquitetura que comporta as suas necessidades.

### 1.1 Origem e Contexto Histórico
- Na década de 1960, ocorreu a crise do software, quando os sistemas passaram a ficar mais complexos e mais difíceis de serem feitos.
- Em vez de consertar alguma funcionalidade, era mais fácil começar um projeto do zero.
- Conforme os projetos de software foram ficando maiores, mais difíceis e, consequentemente, mais caros de manter, houve a necessidade de criar formas de organizar o código de fonte de uma maneira mais sustentável.
- O conceito de arquitetura de software começou a ganhar forma entre as décadas de 1960 e 1970, mas foi em 1980 que ele se consolidou como uma disciplina fundamental da engenharia de software.
- À época, tratava-se de uma forma de se projetar um código com uma certa lógica, de modo que fosse mais fácil realizar a sua manutenção.

> [!TIP] DICAS: 
> A crise do software (década de 1960) é o marco histórico que deu origem à necessidade de organizar melhor o código.
>

> [!CAUTION] OBSERVAÇÃO: 
> A consolidação da arquitetura de software como disciplina ocorreu em 1980.
>

## 2. Arquitetura Monolítica
- Surgiu em 1970 e foi consolidada em 1980.
- Trata-se da primeira abordagem estruturada para desenvolvimento de sistemas.
- Objetivo: simplificar o desenvolvimento e implementação de sistemas de software.
- Funcionamento: todas as funcionalidades do sistema (interface de usuário, lógica de negócios, acesso a dados) são desenvolvidas juntas, de forma interdependente e em um único arquivo executável.
- As questões de concurso não trazem questões específicas sobre a arquitetura monolítica, porque ela foi a primeira, então era bem primitiva.
- É usada para ser comparada com outras arquiteturas, especialmente com a de microsserviços.

> [!CAUTION] OBSERVAÇÃO: 
> A arquitetura monolítica é cobrada em provas principalmente em contraposição à arquitetura de microsserviços.
>

## 3. Arquitetura Cliente-Servidor
- Criada em 1980.
- Objetivo: distribuir a carga de trabalho para gerir os recursos de forma mais eficiente.
- Funcionamento:
  - O cliente interage com o usuário e envia solicitações ao servidor.
  - O servidor processa as solicitações, executa lógica de negócios e retorna resultados ao cliente.

## 4. Arquitetura Orientada a Objetos
- Surgiu em 1980.
- Objetivo: organizar o desenvolvimento de software de uma forma que imita o mundo real e facilitar a modularidade, reutilização e manutenção do código.
- Funcionamento: organiza o sistema em objetos, que são instâncias de classes.
- Analogia: as classes são como um formulário, ao passo que os objetos são como o preenchimento do formulário.
- O objeto é o elemento real, a classe em si é apenas o molde que se deve seguir para criar algo de verdade.

## 5. Arquitetura MVC (*Model-View-Controller*)
- Surgiu em 1970 e foi consolidada em 1990.
- Objetivo: dividir as aplicações em três componentes por uma organização mais clara.
- Componentes:
  - *Model*: representa os dados da aplicação e a lógica de negócios.
  - *View*: apresenta os dados ao usuário.
  - *Controller*: intermediário entre *model* e *view*, recebe as entradas do usuário, processa e determina qual *view* será exibida.

## 6. Arquitetura em Camadas
- Surgiu em 1980 e foi consolidada em 1990.
- Objetivo: organizar o software em camadas de forma que cada uma tenha um objetivo específico.
- Possui três camadas principais, podendo ser estendida conforme a necessidade:

| CAMADA | RESPONSABILIDADE |
|--------|------------------|
| Apresentação | Responsável pela interface do usuário e interação com usuário final (páginas *web*) |
| Negócios | Processa entradas e aplica regras de negócios (serviços, validações) |
| Dados | Gerencia a persistência de dados (repositórios, conexão com banco de dados) |

- Exemplo: Cadastro de usuário
  - Camada de apresentação: preenchimento de e-mail e senha.
  - Camada de negócios: verificação de que o usuário existe.
  - Camada de dados: persistência dos dados recebidos.

## 7. Arquitetura de Objetos Distribuídos
- Surgiu em 1980 e foi consolidada em 1990.
- Objetivo: permitir que objetos de software interajam como se estivessem no mesmo ambiente, mesmo que estejam em sistemas diferentes.
- Funcionamento: objetos residem em diferentes máquinas conectadas por uma rede e interagem entre si através de protocolos de comunicação e *middleware* específico (*CORBA*, *RMI*, *DCOM*).

> [!TIP] DICAS: 
> *CORBA*, *RMI* e *DCOM* são exemplos de *middleware* para arquitetura de objetos distribuídos.
>

## 8. Padrões de Comunicação - SOAP
- Os padrões de comunicação não são uma arquitetura, mas uma forma de se fazer uma transferência de dados.
- SOAP surgiu em 1990.
- Objetivo: permitir comunicação entre aplicações distribuídas em diferentes plataformas, através de *XML*.

> [!CAUTION] OBSERVAÇÃO: 
> SOAP e REST são padrões de comunicação, não arquiteturas de software.
>

## 9. Arquitetura *Peer-to-Peer* (P2P)
- Surgiu em 1990, consolidando-se em 2000.
- Objetivo: distribuir tarefas e recursos de forma descentralizada entre os participantes da rede (*peers*), sem a necessidade de um servidor central.
- Funcionamento: todos os nós (*peers*) na rede são iguais e podem atuar simultaneamente como clientes e servidores.

## 10. Arquitetura Orientada a Serviços (SOA - *Service-Oriented Architecture*)
- Surgiu em 2000.
- Objetivo: permitir que diferentes serviços de software (distribuídos em diferentes sistemas e plataformas) interajam e funcionem juntos.
- Funcionamento: a aplicação é composta por serviços distintos que se comunicam por meio de interfaces bem definidas, fazendo uso de protocolos de comunicação, como *HTTP*.

## 11. Padrões de Comunicação - REST
- Surgiu no ano 2000.
- Objetivo: criar *APIs web* simples e escaláveis.
- Funcionamento: opera com requisições *HTTP* (*GET*, *POST*, *PUT*, *DELETE*).

> [!TIP] DICAS: 
> REST utiliza os verbos *HTTP*: *GET* (consultar), *POST* (criar), *PUT* (atualizar) e *DELETE* (excluir).
>

## 12. Arquitetura *Event-Driven* (Orientada a Eventos)
- Surgiu no ano 2000.
- Objetivo: criar sistemas que reagem rapidamente a eventos e mudanças de estado.
- Funcionamento: o fluxo de trabalho é determinado por eventos, que podem ser qualquer ocorrência significativa detectada e tratada pelo sistema.

## 13. Arquitetura Hexagonal (*Ports and Adapters*)
- Surgiu em 2000.
- Objetivo: criar um design de software que seja independente de tecnologia e *frameworks*.
- Componentes:
  - Núcleo: corresponde à lógica de negócio e às regras de domínio.
  - *Ports* (portas): interfaces que definem a interação do núcleo com o exterior.
  - *Adapters* (adaptadores): implementações das portas, que adaptam a interface externa para a interface esperada pelo núcleo da aplicação e vice-versa.

## 14. Arquitetura de Microsserviços
- Surgiu em 2010.
- Objetivo: dividir uma aplicação monolítica em serviços menores, independentes e focados em funcionalidades específicas.
- Funcionamento: cada serviço é responsável por uma funcionalidade específica e se comunica com outros serviços através de *APIs*.
- Costuma ser bastante cobrada em contraposição com a arquitetura monolítica.

> [!CAUTION] OBSERVAÇÃO: 
> A comparação entre arquitetura monolítica e microsserviços é um dos tópicos mais cobrados em concursos.
>

## 15. Arquitetura *Serverless*
- Surgiu em 2010.
- Objetivo: permitir que os desenvolvedores focassem exclusivamente na lógica de negócios, enquanto a nuvem gerencia a escalabilidade, disponibilidade e manutenção dos servidores.
- Funcionamento: a execução do código é totalmente gerenciada por um provedor de nuvem.

## 16. Linha do Tempo das Arquiteturas

| ARQUITETURA/PADRÃO | SURGIMENTO | CONSOLIDAÇÃO |
|--------------------|------------|--------------|
| Monolítica         | 1970 | 1980 |
| MVC                | 1970 | 1990 |
| Cliente-Servidor   | 1980 | - |
| Orientada a Objetos | 1980 | - |
| Em Camadas | 1980 | 1990 |
| Objetos Distribuídos | 1980 | 1990 |
| SOAP | 1990 | - |
| *Peer-to-Peer* | 1990 | 2000 |
| SOA | 2000 | - |
| REST | 2000 | - |
| *Event-Driven* | 2000 | - |
| Hexagonal | 2000 | - |
| Microsserviços | 2010 | - |
| *Serverless* | 2010 | - |

> [!TIP] DICAS: 
> Decore os marcos temporais: 1960 (crise do software) ⟶ 1980 (consolidação da arquitetura de software como disciplina) ⟶ arquiteturas mais antigas (1970-1980) ⟶ arquiteturas intermediárias (1990) ⟶ arquiteturas modernas (2000-2010).