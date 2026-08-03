# API Gateway

## 1. Definição e Arquitetura
- O API Gateway atua como um ponto único de entrada para múltiplas APIs ou serviços em uma arquitetura de software, sendo comum em ambientes de microsserviços.
- Funciona tecnicamente como um proxy reverso ⟶ encaminha as solicitações dos clientes para os serviços de back-end correspondentes.
- Centraliza diversas funcionalidades em um só componente:
  - Autenticação e autorização;
  - Roteamento de tráfego;
  - Balanceamento de carga;
  - Monitoramento e coleta de métricas.
- Os clientes interagem com um único endpoint, o que oculta a complexidade interna e reduz a necessidade de conhecer detalhes dos serviços de back-end.

> [!TIP] DICAS: 
> - O API Gateway é um serviço de borda e não o back-end propriamente dito.
> - Ele é agnóstico à tecnologia, podendo ser implementado em diversas linguagens e sistemas operacionais como Linux ou Windows.

## 1.1 Benefícios da Implementação
- Simplificação do cliente ao reduzir o acoplamento entre as requisições e a infraestrutura interna.
- Melhoria na segurança ao permitir a aplicação de políticas em um único ponto centralizado.
- Facilitação da escalabilidade e manutenção, permitindo alterar serviços internos sem impactar a interface do cliente.
- Geração de logs centralizados e estatísticas de uso para visibilidade de desempenho e detecção de falhas.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora centralize a segurança, em provas de concurso, a afirmação de que isso é uma vantagem absoluta pode ser considerada incorreta dependendo do contexto comparativo (ex: em relação ao ideal de segurança distribuída ou EBS).
> - O API Gateway não deve funcionar como um portfólio ou cardápio de serviços para o usuário, pois isso é considerado uma falha de segurança.

## 2. Funcionalidades e Operação
- Roteamento de solicitações: o redirecionamento é feito com base no caminho da URL, no método HTTP ou outros critérios específicos.
- Transformação de protocolos e dados: possui a capacidade de converter protocolos (ex: REST para SOAP) e normalizar o formato das respostas para os clientes.
- Segurança: oferece suporte a diversos mecanismos, como tokens JWT, OAuth 2.0 e API Keys.
- Balanceamento de carga: distribui as solicitações entre as instâncias existentes de um serviço para melhorar a performance.
- Limitação de taxa (Rate Limiting): controla o volume de solicitações por cliente em determinado período para evitar abusos ou ataques.

### 2.1 Fluxo de Execução
- Recebimento de solicitação do cliente ⟶ autenticação da identidade.
- Verificação de autorização (controle de acesso).
- Roteamento para o serviço de back-end apropriado.
- Processamento da requisição pelos serviços internos.
- Transformação da resposta (se necessário, como de SOA para JSON).
- Entrega da resposta final ao cliente e envio de métricas para monitoramento.

> [!CAUTION] OBSERVAÇÃO: 
> - O API Gateway gerencia o tráfego e faz o balanceamento, mas não é responsável por subir novos nós (instâncias) de um serviço; essa função depende de outras tecnologias de orquestração.
> - Para configurar uma integração corretamente, é obrigatório especificar na rota qual o método HTTP (GET, POST, etc.) que o back-end suporta.