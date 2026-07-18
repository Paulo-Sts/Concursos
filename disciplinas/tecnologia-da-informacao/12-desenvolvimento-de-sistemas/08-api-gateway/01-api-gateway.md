# Anotações

# API Gateway

## 1.1 Conceito

- **API Gateway** é um componente de software que atua como **ponto único de entrada** para múltiplas APIs ou serviços em uma arquitetura de software.
- Funciona como um **proxy reverso**, encaminhando solicitações dos clientes para os serviços de *back-end* correspondentes.
- Centraliza funcionalidades como **autenticação**, **autorização**, **roteamento**, **balanceamento de carga** e **monitoramento**.

> [!TIP] DICAS
> - O API Gateway **não é um serviço de back-end** propriamente dito – ele fica entre o cliente e o(s) serviço(s) de back-end.
> - É posicionado entre o solicitante das requisições e o(s) serviço(s) de back-end.

## 1.2 Por que usar um API Gateway?

- **Simplifica a comunicação** entre clientes e serviços, ocultando a complexidade interna.
- **Melhora a segurança** ao implementar políticas de segurança em um único ponto.
- **Facilita a escalabilidade e manutenção** – permite adicionar ou modificar serviços sem impactar os clientes.

## 1.3 Benefícios

### 1.3.1 Centralização de Serviços
- Permite implementar **segurança, autenticação e autorização em um único ponto**, em vez de em cada serviço individual.
- Gerencia tráfego entre clientes e serviços de *back-end*, controlando acesso e **limites de taxa** (*rate limiting*).
- Quando há gerenciamento em um ponto único, é possível:
  - Diminuir a frequência de respostas para evitar ataques.
  - Fazer o **banimento do IP** de requisições maliciosas.

### 1.3.2 Simplificação do Cliente
- Os clientes interagem com **um único *endpoint***, reduzindo a necessidade de conhecer detalhes dos serviços internos.
- Reduz o **acoplamento** entre clientes e serviços, facilitando mudanças na arquitetura.

### 1.3.3 Monitoramento e Estatísticas
- Permite gerar **logs** de tudo o que acontece e fazer a separação pelos serviços.
- Coleta **métricas de uso e desempenho**, fornecendo visibilidade sobre o tráfego e comportamento das APIs.
- Facilita a **detecção de falhas** e a tomada de decisões baseadas em dados.
- O API Gateway é capaz de **prover estatísticas** de uso.

> [!CAUTION] OBSERVAÇÃO
> **O API Gateway NÃO funciona como um portfólio de serviços em que o usuário escolhe e implementa a chamada do serviço necessário.** Isso seria uma falha de segurança.

## 1.4 Funcionalidades

| FUNCIONALIDADE | DESCRIÇÃO |
|----------------|-----------|
| **Roteamento de Solicitações** | Encaminha solicitações para o serviço de *back-end* apropriado com base no caminho da URL, método HTTP ou outros critérios |
| **Transformação de Protocolos e Dados** | Converte protocolos (ex.: REST para SOAP); normaliza respostas dos serviços para os clientes |
| **Segurança** | Implementa autenticação e autorização; suporta JWT, OAuth 2.0, API Keys |
| **Balanceamento de Carga** | Distribui solicitações entre múltiplas instâncias de um serviço, melhorando disponibilidade e performance |
| **Limitação de Taxa (Rate Limiting)** | Controla o número de solicitações por cliente em um período, protegendo serviços contra abuso |

> [!CAUTION] OBSERVAÇÃO
> **O API Gateway NÃO sobe novos nós para um serviço.** Se houver muitas requisições para um serviço específico, o API Gateway apenas encaminha as requisições – é necessária outra tecnologia para escalar horizontalmente (subir mais instâncias do serviço).

## 1.5 Fluxo de Execução

1. **Cliente** envia uma solicitação para o **API Gateway**.
2. O **API Gateway** aplica políticas de segurança (autenticação, autorização, *rate limiting*).
3. O **API Gateway** roteia a solicitação para o serviço de *back-end* apropriado.
4. O serviço de *back-end* processa a solicitação e retorna a resposta.
5. O **API Gateway** (opcionalmente) transforma a resposta e a envia de volta ao cliente.

## 1.6 Tabela Resumo – API Gateway

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| **Posição** | Entre o cliente e os serviços de *back-end* |
| **Função** | Proxy reverso / ponto único de entrada |
| **Centralização** | Autenticação, autorização, roteamento, balanceamento, monitoramento |
| **Benefícios** | Segurança unificada, simplificação do cliente, monitoramento centralizado |
| **Limitação** | Não escala serviços horizontalmente (não sobe novos nós) |

---

# Questões de Fixação

## Questão 01
(CEBRASPE/CESPE/CAU-BR/2024)

Com relação a barramento de serviços corporativos (EBS), e dos aspectos de segurança e versatilidade do API Gateway, julgue o item subsequente. Uma das vantagens de se usar um API Gateway é que ele permite implementar a segurança da API em um único ponto, em vez de em cada serviço individual.

**Gabarito:** E (Errado) - Embora o API Gateway permita centralizar a segurança, a afirmativa é ambígua. A banca considerou errado porque não é uma vantagem em relação à segurança, pois o ideal não é centralizar tudo em um único ponto – há riscos de ponto único de falha.

## Questão 02
(CEBRASPE/CESPE/SEPLAG-CE/2024)

Acerca de gerenciamento de API, de RESTful e de ITIL 4, julgue o item subsequente. Um API gateway atua como um ponto central de entrada para várias APIs e desempenha um papel importante na simplificação da gestão de tráfego, autenticação, autorização e monitoramento das chamadas de API.

**Gabarito:** C (Correto)

## Questão 03
(CEBRASPE/CESPE/PREF. FORTALEZA/2023)

Acerca de API Gateway, julgue o próximo item. Considere-se que seja necessário criar uma API Gateway para um serviço back-end que responde a solicitações HTTP na rota /api/fiscalização. Nessa situação hipotética, na etapa de configuração da rota para o serviço de back-end, é necessário especificar, na API Gateway, o método HTTP (GET, POST etc.) que a aplicação back-end suporta, para que a integração funcione corretamente.

**Gabarito:** C (Correto)

## Questão 04
(CEBRASPE/CESPE/SERPRO/2021)

A respeito de orquestração de serviços e API gateway, julgue o item a seguir.

APIs podem ser protegidas com recursos de autenticação.

**Gabarito:** C (Correto)

## Questão 05
(CEBRASPE/CESPE/SERPRO/2021)

A respeito de orquestração de serviços e API gateway, julgue o item a seguir.

Um gateway de API é utilizado entre o cliente e os serviços back-end, sendo capaz de prover estatísticas.

**Gabarito:** C (Correto)

## Questão 06
(CEBRASPE/CESPE/MPO/2024)

A respeito de arquitetura de aplicações, julgue o próximo item.

Um gateway de API funciona como um portfólio de serviços, em que o usuário escolhe e implementa a chamada do serviço necessário.

**Gabarito:** E (Errado) - O API Gateway como um portfólio de serviços seria uma falha de segurança.

## Questão 07
(VUNESP/CIJUN/2023)

De modo geral, um API gateway:

a) consiste em um serviço de back-end propriamente dito, respondendo diretamente requisições provenientes de usuários da API.
b) é posicionado entre o solicitante das requisições e o(s) serviço(s) de back-end.
c) é inadequado para prover serviços de autenticação.
d) é uma tecnologia específica da linguagem Java.
e) é uma tecnologia específica de servidores Windows Server, não estando disponíveis em Linux.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | C |
| 03 | C |
| 04 | C |
| 05 | C |
| 06 | E |
| 07 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Gunter Ribeiro Amorim.*