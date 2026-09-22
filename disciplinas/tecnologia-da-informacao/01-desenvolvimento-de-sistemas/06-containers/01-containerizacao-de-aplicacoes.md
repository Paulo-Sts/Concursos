# Conteinerização de Aplicações

## 1. Introdução
- Contêiner é definido como um pedaço de software e suas dependências.
- No passado, as organizações utilizavam servidores dedicados para diferentes funções, o que gerava processos complexos.
- Servidores físicos costumavam rodar com apenas 10% ou 15% de sua capacidade total.
- A virtualização surgiu para permitir a divisão da capacidade ociosa de um servidor em múltiplas máquinas virtuais.

## 2. Virtualização Tradicional
- Consiste na criação de máquinas virtuais que operam por meio de um hipervisor.
- Cada máquina virtual possui seu próprio sistema operacional independente.
- O sistema operacional da máquina física é denominado hospedeiro, enquanto o da máquina virtual é chamado de parasita.
- Máquinas virtuais não compartilham recursos entre si, permitindo o uso de diferentes sistemas operacionais em um mesmo hardware.
- Uma limitação desse modelo é o peso das máquinas virtuais, que podem levar minutos para iniciar.

## 3. Método de Virtualização ao Nível do Sistema Operacional
- Permite a execução de múltiplas instâncias isoladas em um único sistema operacional anfitrião.
- As aplicações são executadas em espaços isolados chamados contêineres.
- Diferente das máquinas virtuais, os contêineres compartilham o mesmo sistema operacional do host.
- Proporciona o empacotamento e a execução de aplicações de forma previsível e repetível.
- Garante portabilidade entre diferentes sistemas e plataformas de nuvem.
- Permite uma utilização otimizada de recursos como CPU e memória.
- Oferece inicialização rápida, com capacidade de iniciar e parar em segundos.

> [!CAUTION] OBSERVAÇÃO: 
> - Conteinerização é a virtualização de sistema operacional.
> - Os contêineres apresentam uma desvantagem de segurança em relação à virtualização tradicional, pois compartilham o sistema operacional da infra.

## 4. Mecanismos de Isolamento
- O isolamento assegura que cada contêiner opere em seu próprio ambiente sem interferir nos outros ou no host.
- Control Groups (cgroups) ⟶ funcionalidade do kernel do Linux para limitação, priorização e monitoramento de recursos de hardware como CPU, memória, disco e rede.
- Namespace ⟶ funcionalidade do kernel do Linux que provê isolamento dos recursos do sistema para processos, como rede e sistema de arquivos.

> [!TIP] DICAS: 
> - Control Groups (criados por volta de 2008) separam o hardware de forma virtual;
> - Namespace realiza a separação do software e dos recursos de sistema para os processos.

## 5. Tecnologias Principais e Aplicações

### 5.1 Tecnologias de Mercado
- Docker ⟶ plataforma popular utilizada para a criação, empacotamento e gerenciamento de contêineres.
- Kubernetes ⟶ sistema de orquestração voltado para automatizar a implantação, escala e operação de aplicações conteinerizadas.

### 5.2 Aplicações Práticas
- Desenvolvimento de aplicações ⟶ criação de ambientes consistentes que podem ser replicados em diferentes máquinas.
- Microsserviços ⟶ execução de diferentes serviços em contêineres separados para facilitar a manutenção.
- Integração e Entrega Contínuas (CI/CD) ⟶ facilitação de pipelines onde a aplicação é construída, testada e implantada de forma automatizada.
- Nuvem e Multiplataforma ⟶ movimentação simplificada de aplicações entre ambientes locais e nuvem.

> [!TIP] DICAS: 
> - A troca de sistema operacional não é responsabilidade do contêiner ou do desenvolvedor, mas sim da engine, como o Docker.

## 6. Comparação entre Contêineres e Máquinas Virtuais
- A escolha entre contêineres e máquinas virtuais depende de critérios como arquitetura, isolamento e desempenho.

| ASPECTO | CONTÊINERES | MÁQUINAS VIRTUAIS (VMS) |
|---|---|---|
| Arquitetura | Compartilham o kernel do host | Incluem um kernel completo e sistema operacional |
| Isolamento | Isolamento a nível de aplicação (namespace e cgroups) | Isolamento completo (hipervisor) |
| Tempo de inicialização | Rápido (segundos) | Mais lento (minutos) |
| Desempenho | Geralmente mais eficiente devido à sobrecarga menor | Pode ter sobrecarga maior devido ao hipervisor |
| Uso de recursos | Mais eficiente, compartilhando recursos do host | Menos eficiente, requerendo recursos dedicados |
| Isolamento de falhas | Menos isolado, compartilha kernel | Mais isolado, falhas não afetam outras vms |
| Compatibilidade | Melhor para aplicações cloud-native e microservices | Melhor para executar diferentes sos e aplicações legadas |
| Segurança | Depende do isolamento do kernel | Geralmente mais seguro devido ao isolamento completo |

## 7. Definições Técnicas de Imagem e Contêiner
- Imagem consiste em um conjunto de arquivos necessários para montar um contêiner, funcionando de forma análoga a uma imagem de disco;
- Dockerfile ⟶ arquivo de configuração utilizado para a construção de uma imagem a partir de definições do desenvolvedor;
- Contêiner é a instância de execução de uma imagem no sistema operacional hospedeiro;
- Processo de execução envolve o download da imagem de um registro, como o Docker Hub, através da Engine do Docker.

## 8. Virtualização de Sistema vs Virtualização de Hardware
- Conteinerização virtualiza o sistema e sua interface com o sistema operacional, não o hardware físico da máquina;
- Virtualização do hardware físico (bare metal) é característica exclusiva da virtualização tradicional ou máquinas virtuais;
- Docker atua como um middleware que intercepta chamadas e gerencia a hospedagem no lado do servidor;
- Isolamento entre contêineres impede que uma instância acesse arquivos ou diretórios pertencentes a outra.

> [!CAUTION] OBSERVAÇÃO: 
> - O kernel do sistema hospedeiro é compartilhado entre todos os contêineres, o que diferencia este modelo da virtualização de hardware;
> - A independência do sistema operacional é uma percepção do usuário, mas tecnicamente limitada pelo compartilhamento do kernel.

## 9. Microsserviços e Gerenciamento de Escalabilidade
- Microsserviços são classificados como softwares de alto nível pois não interagem diretamente com a infraestrutura ou kernel;
- Escalabilidade horizontal é alcançada pelo lançamento de novos contêineres com a mesma aplicação para suprir demandas de acesso;
- Controle granular permite ajustar a capacidade de processamento de componentes específicos da aplicação conforme a necessidade;
- Unidade de escalabilidade do sistema é representada por cada contêiner individualmente.

## 10. Ciclo de Vida e Segurança no Desenvolvimento
- Padronização garante que o mesmo pacote seja utilizado sem variações em ambientes de desenvolvimento, homologação e produção;
- Agilidade na modificação e iteração ocorre pela facilidade de destruir contêineres antigos e iniciar novos a partir de imagens atualizadas;
- Portabilidade assegura que o mesmo código execute em dispositivos com diferentes infraestruturas e sistemas operacionais.

> [!CAUTION] OBSERVAÇÃO: 
> - Segurança não é uma vantagem intrínseca dos contêineres quando comparados às máquinas virtuais;
> - Máquinas virtuais oferecem isolamento mais robusto por possuírem sistemas operacionais independentes gerenciados por um hipervisor.

> [!TIP] DICAS: 
> - Namespace ⟶ provê o isolamento lógico dos processos para que simulem operar sozinhos no sistema operacional;
> - Control Groups (cgroups) ⟶ realizam a gestão, monitoramento e limitação dos recursos físicos como CPU, memória e rede.