# Kubernetes 5

## 1. Kubectl e Interação com o Cluster
- O kubectl é a ferramenta nativa de linha de comando utilizada para a interação, gerenciamento de objetos e controle de clusters do kubernetes.
- A ferramenta realiza a comunicação com o servidor da api do kubernetes, localizado no nó mestre do cluster, através do protocolo http.

## 2. Comandos de Gerenciamento de Recursos
- O gerenciamento de arquivos e recursos no cluster utiliza comandos de criação, atualização e remoção:
  - Kubectl apply -f: aplica configurações contidas em arquivos yaml ou json para criar ou atualizar recursos;
  - Kubectl create -f: comando utilizado para criar novos recursos no cluster a partir de um arquivo de configuração;
  - Kubectl delete: remove permanentemente recursos especificados do ambiente do cluster;
  - Kubectl edit: permite a modificação direta de um recurso através da abertura de um editor de texto;
  - Kubectl get: recupera e exibe uma lista de informações sobre os recursos solicitados, como pods e serviços.

## 3. Comandos de Operação e Monitoramento
- Para a manutenção e observação do estado das aplicações, utilizam-se instruções de execução e métricas:
  - Kubectl logs: permite visualizar os registros de saída de um contêiner para auxiliar na resolução de problemas;
  - Kubectl exec -it: possibilita a execução de comandos e a interação direta com o ambiente interno de um contêiner ativo;
  - Kubectl scale: ajusta dinamicamente a quantidade de réplicas de um recurso para suportar mudanças na carga de trabalho;
  - Kubectl top: fornece métricas em tempo real sobre o consumo de cpu e memória por parte de nós e pods.

## 4. Tabela de Comandos de Diagnóstico e Configuração
| COMANDO | FINALIDADE |
|---|---|
| Kubectl get events | Exibe eventos recentes e mudanças de estado no cluster |
| Kubectl port-forward | Cria um túnel para acessar serviços internos localmente |
| Kubectl proxy | Inicia um proxy para permitir acesso à api do kubernetes |
| Kubectl cluster-info | Mostra informações sobre o cluster e seus componentes |
| Kubectl config view | Exibe a configuração atual do contexto e do kubectl |
| Kubectl config get-clusters | Lista os clusters configurados no arquivo kubeconfig |
| Kubectl taint | Aplica manchas em nós para restringir o agendamento de pods |

> [!TIP] DICAS: 
> - Lembre-se que o kubectl funciona como a ponte principal entre o administrador e a api do kubernetes ⟶ essencial para automação via scripts.

> [!CAUTION] OBSERVAÇÃO: 
> - O comando kubectl taint não serve para listar serviços, mas para impor restrições (manchas) que o scheduler deve considerar ao alocar pods.
> - O uso das flags --grace-period=0 e --force no comando delete força a remoção imediata do pod sem aguardar o encerramento adequado do contêiner.
> - O estudo detalhado desses comandos costuma ter baixa incidência em provas, embora exista uma tendência de aumento gradual nas cobranças recentes.