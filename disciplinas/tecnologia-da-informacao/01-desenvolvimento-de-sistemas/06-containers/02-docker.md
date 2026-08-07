# Conteinerização e Docker

## 1. Docker e Conteinerização
- O Docker é um aplicativo de conteinerização responsável pelo gerenciamento de contêineres.
- Trata-se de uma plataforma de código aberto voltada para o desenvolvimento, o envio e a execução de aplicações.
- A ferramenta funciona em diversos ambientes, como Linux, Windows e MacOS, sendo independente do sistema operacional.
- O nível de cobrança em concursos costuma ser mais superficial do que o uso profissional da ferramenta.

### 1.1 Fluxo de Trabalho e Execução
- O processo inicia-se com o DockerFile, que consiste em uma série de comandos indicando os arquivos existentes no projeto.
- A partir do DockerFile, constrói-se uma imagem.
- A partir da imagem, é possível gerar diversos contêineres.
- O Docker provê a capacidade de container runtime, sendo o responsável por executar os contêineres e gerenciar suas imagens.
- O fluxo de criação segue a sequência:
  - DockerFile;
  - Imagem;
  - Contêineres.

> [!TIP] DICAS: 
> - O Docker é independente do sistema operacional porque torna o ambiente transparente para a aplicação.

### 1.2 Características dos Contêineres
- Um contêiner inclui o aplicativo e todas as suas dependências.
- O contêiner compartilha o kernel do sistema operacional com outros contêineres no mesmo host.
- São considerados leves e ágeis quando comparados às máquinas virtuais tradicionais.
- O isolamento e a segurança permitem a execução simultânea de vários contêineres em um único host.
- O usuário possui a capacidade de compartilhar contêineres entre diferentes ambientes.
- A orquestração é definida como o gerenciamento do momento em que o Docker vai lançar os contêineres.

### 1.3 Arquitetura e Camadas
- A estrutura de funcionamento posiciona a plataforma Docker entre o sistema operacional e as aplicações.
- O contêiner isola uma aplicação da outra, impedindo que elas se enxerguem, embora sejam lançadas pelo mesmo gerenciador.
- A hierarquia de execução segue o modelo abaixo:

| CAMADA | DESCRIÇÃO |
|---|---|
| Aplicação | Programas que rodam de forma isolada |
| Docker | Plataforma que lança e gerencia os contêineres |
| Sistema operacional | Kernel compartilhado entre os contêineres |
| Infraestrutura | Base física ou hardware do host |

### 1.4 Benefícios e Comparação com Máquinas Virtuais
- O Docker utiliza menos recursos de hardware que uma máquina virtual tradicional.
- O uso do mesmo contêiner nos ambientes de desenvolvimento, homologação e produção garante maior consistência no processo.
- A tecnologia melhora a portabilidade e a organização das aplicações.
- Diferente das máquinas virtuais, os contêineres não precisam de um sistema operacional completo para cada instância.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora o contêiner seja seguro, as máquinas virtuais são consideradas mais seguras por possuírem seu próprio sistema operacional isolado.
> - O Docker pode rodar em Linux, Windows ou Mac, tanto em 32 quanto em 64 bits; restrições impostas por questões de prova sobre sistemas operacionais específicos geralmente estão incorretas.