# Arquitetura e Componentes do Docker 2

## 1. Arquitetura Docker
- O Docker é um gerenciador de contêineres que opera sobre o sistema operacional, dividindo-se em módulos que interagem para o lançamento de aplicações.
- O Docker Host representa a instância do Docker instalada sobre o sistema operacional.
- O Docker daemon atua como o processo principal dentro do host, sendo responsável por gerenciar objetos como imagens, redes e volumes.
- O Docker Client é o aplicativo de interface de linha de comando utilizado para enviar instruções ao daemon.
- A interação com o daemon também pode ser realizada por meio de interfaces de programação de aplicativos do tipo api rest.

### 1.1 Comandos e Fluxo de Operação
- O funcionamento básico do sistema baseia-se em comandos específicos enviados pelo cliente:
  - Docker run: utilizado para executar um contêiner a partir de uma imagem;
  - Docker build: utilizado para construir uma imagem a partir de um arquivo Dockerfile;
  - Docker pull: utilizado para baixar uma imagem armazenada em um Registry;
  - Docker push: utilizado para enviar imagens para repositórios remotos.

| COMPONENTE | DESCRIÇÃO |
|---|---|
| DOCKER DAEMON | Software que roda na máquina hospedeira e recebe comandos do cliente |
| DOCKER CLIENT | Interface de linha de comando para interação do usuário com o engine |
| REGISTRY | Coleção de imagens hospedadas que permite a criação do sistema de arquivos |
| DOCKER HUB | Repositório público ou privado usado para hospedar e baixar diversas imagens |

> [!TIP] DICAS: 
> - Lembre-se da ordem de fornecimento: o Client envia o comando ⟶ o Daemon processa a solicitação ⟶ o Registry fornece a imagem se ela não estiver local.

## 2. Imagens Docker
- Uma imagem Docker é um modelo imutável que reúne o código, bibliotecas, dependências e configurações necessárias para a execução de um serviço.
- O conceito de imagem assemelha-se a uma classe na programação, enquanto o contêiner representa a instância dessa classe em execução.
- As imagens podem ser armazenadas em repositórios para compartilhamento entre diferentes sistemas e usuários.
- A criação de uma imagem ocorre geralmente por meio de um Dockerfile ou a partir de um contêiner já existente.
- A imagem funciona como um template que permite a geração de múltiplas instâncias de si mesma no ambiente.

> [!CAUTION] OBSERVAÇÃO: 
> - As imagens são estáticas e imutáveis; qualquer alteração no ambiente em execução não modifica a imagem base original, a menos que uma nova imagem seja gerada.

## 3. Dockerfiles
- O Dockerfile consiste em um script de texto que contém todas as instruções e argumentos necessários para construir uma imagem.
- Funciona como um guia passo a passo que o Docker Engine processa para montar o ambiente do contêiner.
- É o mecanismo utilizado para reunir as instruções que definem a composição da imagem de contêiner.

### 3.1 Principais Instruções do Script
- O desenvolvimento de um Dockerfile utiliza comandos específicos para configurar a aplicação:
  - FROM: instrução que define a imagem base utilizada para iniciar a construção;
  - EXPOSE: comando que indica em quais portas a aplicação estará escutando;
  - ENTRYPOINT: define o local ou comando principal para onde o contêiner será direcionado ao iniciar;
  - ENV e ARG: instruções utilizadas para a definição de variáveis no processo.

## 4. Segurança e Gerenciamento de Credenciais
- O Docker Content Trust é um recurso que permite verificar a integridade e a procedência das imagens por meio de assinaturas digitais.
- O Credential Helper atua na proteção e armazenamento seguro das credenciais de autenticação para repositórios como o Docker Hub.

### 4.1 Docker Secrets
- O Docker Secrets é utilizado para gerenciar informações sensíveis como senhas, tokens e chaves ssh.
- A ferramenta evita a exposição de dados sigilosos no código-fonte ou diretamente nas imagens.
- Durante a operação, os segredos são montados em um sistema de arquivos temporário acessível apenas pelos processos internos do contêiner autorizado.

> [!CAUTION] OBSERVAÇÃO: 
> - A funcionalidade de segredos foi projetada prioritariamente para operar em conjunto com o Docker Swarm.

## 5. Ferramentas de Orquestração e Desktop
- O Docker Swarm é uma ferramenta voltada para clustering e scheduling, permitindo o gerenciamento de vários nós como um único sistema virtual.
- O Docker Desktop é um aplicativo disponível para Windows e Mac que facilita a criação e compartilhamento de microsserviços.
- O pacote Desktop inclui ferramentas integradas como o Docker Compose, Kubernetes e o próprio cliente Docker.