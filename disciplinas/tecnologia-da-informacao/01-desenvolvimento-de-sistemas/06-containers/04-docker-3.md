# Comandos do Docker Client 3

## 1. Introdução e Relevância em Provas
- O estudo detalhado dos comandos do cliente Docker apresenta uma probabilidade de cobrança estimada entre 1% e 2% em provas de concursos públicos.
- Os comandos guardam forte semelhança com as instruções do sistema operacional Linux, o que facilita a intuição para usuários familiarizados.
- A documentação oficial da ferramenta é considerada extensa, contendo centenas de comandos, mas o foco didático recai sobre os mais recorrentes.

## 2. Comandos de Ciclo de Vida e Manipulação
- O gerenciamento de instâncias e contêineres utiliza um conjunto padronizado de instruções operacionais:
  - Docker run: utilizado para criar e iniciar um novo contêiner a partir de uma imagem existente;
  - Docker stop: comando responsável por interromper a execução de um contêiner ativo;
  - Docker start: inicia um contêiner que se encontra em estado parado;
  - Docker rm: comando utilizado para remover um ou mais contêineres do ambiente.

## 3. Gerenciamento de Imagens e Repositórios
- As imagens funcionam como modelos imutáveis para a criação de ambientes isolados e sua manipulação envolve comandos de transferência:
  - Docker build: utiliza as instruções de um arquivo Dockerfile para construir uma imagem local;
  - Docker pull: realiza o download de imagens específicas a partir do Docker Hub ou de outros repositórios;
  - Docker push: envia uma imagem armazenada localmente para um repositório remoto;
  - Docker rmi: comando destinado à remoção de imagens do host local.

## 4. Inspeção e Monitoramento do Ambiente
- Para visualizar o estado atual do host e dos objetos gerenciados, utilizam-se comandos de consulta e diagnóstico:
  - Docker ps: lista os contêineres que estão em execução no momento;
  - Docker images: lista todas as imagens disponíveis e armazenadas no host local;
  - Docker inspect: retorna informações técnicas detalhadas sobre contêineres ou imagens;
  - Docker logs: permite a visualização dos registros de saída e mensagens de erro de um contêiner.

## 5. Tabela de Comandos Auxiliares e Orquestração
| COMANDO | FINALIDADE |
|---|---|
| Docker version | Exibe as versões de api e componentes do host |
| Docker exec | Executa um novo processo dentro de um contêiner ativo |
| Docker top | Lista os processos que estão rodando internamente no contêiner |
| Docker network | Gerencia as configurações e conexões de rede |
| Docker volume | Gerencia o armazenamento persistente de dados |
| Docker-compose | Gerencia e define aplicações com múltiplos contêineres |
| Docker commit | Cria uma imagem nova a partir de um contêiner modificado |

> [!TIP] DICAS: 
> - Para fins de prova, memorize a sequência lógica de criação de um ambiente: Dockerfile ⟶ Docker build ⟶ Imagem ⟶ Docker run ⟶ Contêiner.

> [!CAUTION] OBSERVAÇÃO: 
> - O comando docker container ls serve para listagem e não deve ser apontado como ferramenta para visualizar o consumo de recursos de hardware.
> - Existe diferença entre o comando exec, que dispara uma tarefa, e o comando attach, que permite o acesso e interação direta com o terminal interno do contêiner.
> - A instrução docker stop \$(docker ps -q) é utilizada para automatizar a parada de todos os contêineres em execução no sistema.