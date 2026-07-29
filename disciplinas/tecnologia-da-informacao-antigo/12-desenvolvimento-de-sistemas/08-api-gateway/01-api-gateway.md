# API Gateway

## 1. Conceito e Posicionamento

### 1.1 Definição
- API Gateway é um componente de software que atua como ponto único de entrada para múltiplas APIs ou serviços em uma arquitetura de software.
- Funciona como um proxy reverso, encaminhando solicitações dos clientes para os serviços de back-end correspondentes.
- Centraliza funcionalidades como autenticação, autorização, roteamento, balanceamento de carga e monitoramento.

### 1.2 Posicionamento na Arquitetura
- O API Gateway não é um serviço de back-end propriamente dito – ele fica entre o cliente e o(s) serviço(s) de back-end.
- É posicionado entre o solicitante das requisições e o(s) serviço(s) de back-end.

> [!TIP] DICAS:
> - O API Gateway não é um serviço de back-end – ele atua como intermediário.
> - É posicionado entre o cliente e os serviços de back-end.

## 2. Funcionalidades

### 2.1 Roteamento de Solicitações
- Encaminha solicitações para o serviço de back-end apropriado com base no caminho da URL, método HTTP ou outros critérios.

### 2.2 Transformação de Protocolos e Dados
- Converte protocolos (ex.: REST para SOAP);
- Normaliza respostas dos serviços para os clientes.

### 2.3 Segurança
- Implementa autenticação e autorização;
- Suporta JWT, OAuth 2.0, API Keys.

### 2.4 Balanceamento de Carga
- Distribui solicitações entre múltiplas instâncias de um serviço, melhorando disponibilidade e performance.

> [!CAUTION] OBSERVAÇÃO:
> - O API Gateway NÃO sobe novos nós para um serviço. Se houver muitas requisições para um serviço específico, o API Gateway apenas encaminha as requisições – é necessária outra tecnologia para escalar horizontalmente (subir mais instâncias do serviço).

### 2.5 Limitação de Taxa (Rate Limiting)
- Controla o número de solicitações por cliente em um período, protegendo serviços contra abuso.
- Permite diminuir a frequência de respostas para evitar ataques e fazer o banimento do IP de requisições maliciosas.

## 3. Benefícios

| BENEFÍCIO | DESCRIÇÃO |
|-----------|-----------|
| Centralização de Serviços | Permite implementar segurança, autenticação e autorização em um único ponto, em vez de em cada serviço individual. |
| Simplificação do Cliente | Os clientes interagem com um único endpoint, reduzindo a necessidade de conhecer detalhes dos serviços internos. |
| Redução de Acoplamento | Reduz o acoplamento entre clientes e serviços, facilitando mudanças na arquitetura. |
| Monitoramento e Estatísticas | Permite gerar logs de tudo o que acontece e fazer a separação pelos serviços; coleta métricas de uso e desempenho; facilita a detecção de falhas. |
| Gerenciamento de Tráfego | Gerencia tráfego entre clientes e serviços de back-end, controlando acesso e limites de taxa. |

> [!CAUTION] OBSERVAÇÃO:
> - O API Gateway NÃO funciona como um portfólio de serviços em que o usuário escolhe e implementa a chamada do serviço necessário. Isso seria uma falha de segurança.

## 4. Fluxo de Execução
1. Cliente envia uma solicitação para o API Gateway;
2. O API Gateway aplica políticas de segurança (autenticação, autorização, rate limiting);
3. O API Gateway roteia a solicitação para o serviço de back-end apropriado;
4. O serviço de back-end processa a solicitação e retorna a resposta;
5. O API Gateway (opcionalmente) transforma a resposta e a envia de volta ao cliente.

## 5. Tabela Resumo – API Gateway

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Posição | Entre o cliente e os serviços de back-end. |
| Função | Proxy reverso / ponto único de entrada. |
| Centralização | Autenticação, autorização, roteamento, balanceamento, monitoramento. |
| Benefícios | Segurança unificada, simplificação do cliente, monitoramento centralizado. |
| Limitação | Não escala serviços horizontalmente (não sobe novos nós). |