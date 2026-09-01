# Segurança de Contêineres: Docker, Kubernetes e Runtime Security

## 1. Principais Riscos de Segurança
- A segurança em contêineres é um tema relevante para o cotidiano profissional e possui importância crescente em processos de conteinerização.
- Os contêineres compartilham o kernel do sistema operacional do host, o que compromete o isolamento e a segurança em comparação com máquinas virtuais.
- O compartilhamento do kernel permite que a inserção de um processo malicioso resulte em acesso indevido ao ambiente do host.
- Ataques podem ser iniciados por meio do comando docker exec, que permite a execução de instruções dentro do contêiner.
- Exemplo: a vulnerabilidade CVE-2019-5736 permitia que um processo malicioso sobrescrevesse o executável do runc e comprometesse o host.

### 1.1 Imagens Inseguras
- O Docker utiliza o Docker Hub como repositório para a criação de contêineres, mas imagens públicas podem apresentar riscos.
- Pesquisadores identificaram malwares em diversas imagens que executavam mineração de criptomoeda (cryptojacking) silenciosamente.
- Imagens genéricas com nomes comuns, como ubuntu ou nginx-secure, podem conter payloads maliciosos embutidos.
- É fundamental verificar a origem e a confiabilidade das imagens para evitar o uso de versões não oficiais.

### 1.2 Escalonamento de Privilégios e Volumes
- Por padrão, o usuário root (UID 0) dentro do contêiner também é o usuário root no host se não houver namespaces de usuário habilitados.
- A ausência de isolamento adequado permite que o root do contêiner acesse recursos do host em caso de falha.
- A montagem de volumes em diretórios sensíveis do host, como /etc ou /var/run/docker.sock, representa um ponto crítico.
- Processos maliciosos em volumes sensíveis podem:
  - Substituir binários do host;
  - Criar novos usuários;
  - Injetar chaves ssh.

### 1.3 Opções de Execução Perigosas
- O uso da opção --privileged concede acesso completo a todos os dispositivos e capacidades do host.
- Esta configuração permite modificar o kernel, carregar módulos e acessar interfaces de rede diretamente.
- O comando docker run com o parâmetro -v /:/mnt permite que o contêiner enxergue e altere todo o sistema do host.

| COMANDO OU OPÇÃO | EXPLICAÇÃO |
|---|---|
| Docker run | Inicia um novo contêiner docker |
| --rm | Remove o contêiner automaticamente ao final da execução |
| -it | Abre um terminal interativo para comando |
| --privileged | Concede permissões totais e acesso irrestrito ao kernel |
| -v /:/mnt | Monta o sistema de arquivos raiz do host no contêiner |

> [!CAUTION] OBSERVAÇÃO: 
> - Cada contêiner gerenciado pelo Docker compartilha o kernel do sistema operacional do host ⟶ esta é uma pegadinha comum de prova que afirma o contrário.

## 2. Boas Práticas e Ferramentas de Defesa
- A construção de imagens deve focar na redução da superfície de ataque e na utilização de fontes confiáveis.
- Recomenda-se o uso de imagens oficiais e mínimas, como a Alpine, para manter a estrutura simplificada.
- É essencial fixar versões específicas no Dockerfile (ex: FROM ubuntu:20.04) e evitar a tag latest.
- Ferramentas desnecessárias, como curl, wget ou bash, devem ser removidas ao final do processo de construção.

### 2.1 Escaneamento de Vulnerabilidades
- O escaneamento regular auxilia na detecção de falhas em bibliotecas, pacotes e configurações incorretas.

| FERRAMENTA | DESENVOLVEDOR | FUNÇÃO PRINCIPAL |
|---|---|---|
| Trivy | Aqua security | Analisa imagens, repositórios, segredos e configurações de iac |
| Clair | Comunidade | Focado em repositórios de imagens como o harbor |

- O Trivy destaca-se pela facilidade de integração em pipelines CI/CD e por ser gratuito.
- O Clair é indicado para ambientes on-premise, analisando camadas da imagem e consultando bancos de dados de cves.

### 2.2 Isolamento e Controle de Execução
- Deve-se evitar o uso de usuários com privilégios de root durante a criação do contêiner.
- Opções de segurança para execução:
  - read-only: define o sistema de arquivos como somente leitura;
  - cap-drop=ALL: remove capacidades adicionais de permissão;
  - no-new-privileges: impede que o contêiner receba novos privilégios após a criação.
- O uso de namespaces isola processos, enquanto os cgroups limitam o consumo de recursos como cpu e memória.
- A implementação de RBAC no Kubernetes assegura que cada agente atue conforme o princípio do menor privilégio.

### 2.3 Segurança de Rede e Produção
- A segmentação de contêineres por propósito reduz o risco de movimentação lateral (lateral movement).
- Estruturar redes específicas para frontend e backend impede comunicações diretas desnecessárias.
- As Network Policies no Kubernetes são ferramentas fundamentais para limitar o tráfego entre pods no cluster.
- Medidas de atenção especial em produção incluem:
  - Hardening do host com aplicação de patches;
  - Monitoramento contínuo de logs e métricas;
  - Atualização regular de imagens e dependências.

> [!TIP] DICAS: 
> - Para reduzir a superfície de ataque, prefira sempre imagens mínimas (distroless ou alpine) e remova shells interativos.