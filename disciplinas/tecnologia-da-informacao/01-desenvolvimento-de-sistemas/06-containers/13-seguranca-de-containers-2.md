# Segurança de Contêineres: Docker, Kubernetes e Runtime Security 2

## 1. Segurança no Docker
- O Docker utiliza namespaces do Linux para isolar processos, rede e sistemas de arquivos.
- Os cgroups são empregados para limitar o uso de recursos como cpu, memória e disco.
- Cada contêiner opera como um processo isolado, compartilhando o mesmo kernel do host.
- O objetivo principal do isolamento por design é impedir que um contêiner interfira ou espione outro.

### 1.1 Controle de Privilégios e Perfis
- Recomenda-se que contêineres não sejam executados como usuário root.
- O uso da instrução USER no Dockerfile é a prática sugerida para definir usuários sem privilégios.
- As capabilities permitem a remoção seletiva de privilégios de processo, como o CAP_SYS_ADMIN.
- Perfis de segurança reforçados podem ser aplicados para restringir o acesso ao sistema:
  - AppArmor e SELinux: definem o que o contêiner pode acessar no sistema;
  - Seccomp: bloqueia chamadas de sistema (syscalls) perigosas ao kernel.

> [!TIP] DICAS: 
> - O Seccomp evita chamadas como ptrace, mount, mknod e reboot para impedir que um processo comprometido realize ações danosas ⟶ foco total no bloqueio de syscalls.

### 1.2 Gerenciamento de Imagens e Daemon
- As imagens devem possuir versões fixas e confiáveis, evitando-se a utilização da tag latest.
- Ferramentas como Trivy, Snyk e Clair são fundamentais para detectar vulnerabilidades conhecidas nas imagens.
- O Docker daemon roda como root no host, representando um risco sistêmico se for comprometido.
- O modo rootless permite que um usuário sem privilégios de root controle os contêineres.
- A exposição da api do Docker via tcp deve ser evitada sem o uso de autenticação e criptografia tls.

## 2. Docker Secrets e Content Trust
- O Docker Secrets é um recurso voltado para o gerenciamento seguro de informações sensíveis como senhas, tokens e certificados.
- As informações são mantidas criptografadas em memória e ficam acessíveis apenas aos processos autorizados.
- O Docker Content Trust permite verificar se uma imagem foi assinada por uma fonte confiável.
- A funcionalidade visa impedir o uso de imagens não verificadas ou corrompidas e proteger contra ataques na cadeia de suprimentos.

| RECURSO | OBJETIVO PRINCIPAL |
|---|---|
| Docker secrets | Proteger dados sensíveis sem exposição em arquivos env |
| Docker content trust | Garantir a integridade e autenticidade das imagens |

## 3. Segurança no Kubernetes
- A segurança do plano de controle (control plane) fundamenta-se no api server, que centraliza os comandos do cluster.
- A proteção do cluster depende de pilares essenciais:
  - Autenticação via tokens, certificados ou oidc;
  - Autorização baseada em funções (rbac);
  - Comunicação criptografada através de tls;
  - Habilitação de logs e auditoria.

### 3.1 Proteção de Dados e Pods
- O etcd atua como o banco de dados do cluster e deve ser acessível apenas pelo api server.
- É fundamental habilitar a criptografia em repouso (encryption at rest) para segredos armazenados no etcd.
- O uso do securityContext nos pods permite definir restrições como a proibição do modo privilegiado.
- Recomenda-se evitar a montagem do volume /var/run/docker.sock dentro de pods.
- As políticas de admissão, como PodSecurity Standards ou ferramentas como OPA/Gatekeeper, impedem a criação de pods vulneráveis.

> [!CAUTION] OBSERVAÇÃO: 
> - Por padrão, os segredos no Kubernetes são armazenados em base64, o que não constitui criptografia real ⟶ deve-se habilitar a criptografia no etcd ou usar gerenciadores externos.

### 3.2 Isolamento de Rede e RBAC
- O Kubernetes não aplica regras de rede restritivas por padrão.
- O uso de Network Policies em conjunto com plugins CNI como Calico ou Cilium define quem pode realizar comunicações no cluster.
- O rbac deve ser configurado seguindo o princípio do menor privilégio, concedendo permissões mínimas e temporárias.
- Deve-se evitar o uso indiscriminado da função cluster-admin como padrão para usuários e serviços.

## 4. Auditoria e Segurança em Tempo de Execução
- A segurança em tempo de execução (runtime security) utiliza ferramentas como Falco para detectar execuções suspeitas.
- A cadeia de software (supply chain) deve ser protegida através do escaneamento de imagens e uso de SBOM.
- O SBOM (Software Bill of Materials) consiste em uma lista detalhada dos códigos e dependências existentes dentro dos contêineres.

| COMPONENTE | FUNÇÃO NA SEGURANÇA |
|---|---|
| Sbom | Rastreamento de dependências e inventário de software |
| Network policies | Prevenção de movimentação lateral entre pods |
| Rbac | Controle granular de acesso aos recursos do cluster |
| Falco | Detecção de comportamentos anômalos como bash inesperado |