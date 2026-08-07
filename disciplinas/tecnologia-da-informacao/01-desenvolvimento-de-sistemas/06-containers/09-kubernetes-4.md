# Kubernetes 4

## 1. Armazenamento e Volumes Persistentes
- Os volumes são definidos como locais destinados ao armazenamento de dados de forma persistente dentro do ambiente do kubernetes.
- O PersistVolume (PV) consiste em um recurso de armazenamento no cluster que possui um tempo de vida próprio, operando de forma independente dos pods que o utilizam.

| TIPO DE VOLUME PERSISTENTE | DESCRIÇÃO |
|---|---|
| Csi | Interface de armazenamento de contêineres |
| Fibre channel (fc) | Armazenamento de fibre channel |
| Hostpath | Volume utilizado apenas para teste em um único nó |
| Iscsi | Armazenamento scsi sobre ip |
| Local | Dispositivos de armazenamento local montados nos nós |
| Nfs | Armazenamento sistema de arquivos de rede |

## 2. Volumes Projetados
- São caracterizados como informações guardadas fora do aplicativo que são projetadas e entregues diretamente para o contêiner.

| TIPO DE VOLUME PROJETADO | DESCRIÇÃO |
|---|---|
| Secret | Armazena dados confidenciais como senhas, tokens e chaves |
| Downwardapi | Injeta dados sobre o próprio pod, como rótulos e nomes |
| Configmap | Projeção de dados de configuração armazenados no kubernetes |
| Serviceaccounttoken | Projeção de token de serviço para autenticação com a api |
| Clustertrustbundle | Conjunto de certificados confiáveis do cluster para os pods |

## 3. Volumes Efêmeros
- Os volumes efêmeros são aqueles que possuem a mesma vida útil de um pod, vivendo apenas enquanto o pod estiver ativo.
- A plataforma oferece diferentes tipos de volumes efêmeros para atender necessidades temporárias:
  - Emptydir: inicia como um volume vazio no começo do pod, utilizando armazenamento local ou ram;
  - Configmap, downwardapi e secret: modalidades que injetam dados específicos do sistema no pod;
  - Csi ephemeral volumes: volumes criados e gerenciados dinamicamente por drivers csi especiais;
  - Generic ephemeral volumes: volumes temporários fornecidos por qualquer driver que suporte volumes persistentes.

> [!TIP] DICAS: 
> - O volume do tipo emptydir é ideal para o armazenamento de dados temporários durante a execução do pod.

> [!CAUTION] OBSERVAÇÃO: 
> - Volumes que possuem a mesma vida útil de um pod denominam-se efêmeros ⟶ este conceito é recorrente em questões de concursos recentes.
> - O PersistentVolume é provisionado pelo administrador e possui tempo de vida independente dos pods associados.
> - O Kubernetes não utiliza armazenamento do tipo NTFS para facilitar a integração com o Windows; tal afirmação é considerada incorreta em provas de concurso.