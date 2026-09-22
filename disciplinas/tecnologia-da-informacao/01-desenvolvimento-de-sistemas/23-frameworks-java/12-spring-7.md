# Framework Spring - Spring Cloud - Eureka 7

## 1. Contexto e Arquitetura de Microsserviços
- A arquitetura de microsserviços é composta por diversas aplicações e módulos que se comunicam entre si, garantindo resiliência ao sistema.
- Diferentemente da arquitetura monolítica, onde todas as partes estão interconectadas e uma falha única pode comprometer todo o sistema, nos microsserviços, a falha em um módulo não afeta o funcionamento dos demais.
- Exemplo prático dessa arquitetura é o Ifood, que possui módulos distintos para restaurante e cliente, que se comunicam e operam de forma independente.

## 2. Spring Cloud
- O Spring Cloud é um conjunto de ferramentas que visa solucionar desafios comuns no desenvolvimento de sistemas distribuídos e arquiteturas de microsserviços.
- Ele facilita a implementação de padrões essenciais para esse tipo de arquitetura, como:
  - Configuração distribuída.
  - Descoberta de serviços.
  - Roteamento inteligente.
  - Balanceamento de carga.
  - Tolerância a falhas.

### 2.1 Componentes do Ecossistema Spring Cloud Netflix
- O Spring Cloud Netflix é um subprojeto do Spring Cloud que integra diversas tecnologias desenvolvidas pela Netflix para orquestrar microsserviços.

#### 2.1.1 Eureka
- Atua como um repositório de descoberta e registro de serviços.
- Permite que os microsserviços se registrem e descubram uns aos outros dinamicamente.
- Aloca um nome lógico para cada serviço registrado, abstraindo a complexidade de endereços IP fixos.

#### 2.1.2 Zuul
- Funciona como um Gateway API, fornecendo um ponto de entrada único para a aplicação.
- É responsável por rotear as requisições dos clientes para os serviços adequados, com base em critérios como roteamento, filtragem, autenticação e autorização.

#### 2.1.3 Ribbon
- Realiza o balanceamento de carga entre as instâncias de um mesmo serviço.
- Controla para qual nó de serviço a requisição será destinada, garantindo alta disponibilidade e distribuição eficiente da carga.

#### 2.1.4 Feign
- Facilita a comunicação síncrona entre microsserviços por meio de chamadas HTTP.
- Permite que um serviço consuma outro de forma declarativa, simplificando a implementação do cliente HTTP.

#### 2.1.5 Hystrix
- Implementa o padrão Circuit Breaker, aumentando a tolerância a falhas do sistema.
- Monitora chamadas entre serviços para verificar o tempo de resposta e a disponibilidade, isolando falhas e evitando que se propaguem.

#### 2.1.6 Turbine
- Agrega e consolida as métricas geradas pelo Hystrix, fornecendo uma visão unificada do status dos Circuit Breakers em todo o sistema.

## 3. Spring Eureka em Detalhes
- O Spring Eureka é a implementação do padrão Service Registry dentro do ecossistema Spring Cloud Netflix.
- Ele é fundamental para a criação de arquiteturas de microsserviços escaláveis e dinâmicas, onde a localização dos serviços pode mudar frequentemente.

### 3.1 Características Principais
- Registro de Serviços: Os microsserviços se registram em um servidor central (Eureka Server) no momento em que são iniciados.
- Descoberta de Serviços: Os microsserviços consultam o servidor Eureka para encontrar a localização de outros serviços, utilizando seus nomes lógicos.
- Alta Disponibilidade: O Eureka Server suporta replicação, garantindo que o registro de serviços permaneça disponível mesmo em caso de falhas.
- Integração com Spring Boot: A configuração e integração com aplicações Spring Boot são simplificadas através de anotações e propriedades.

### 3.2 Funcionamento do Registro e Descoberta
- Os serviços se registram no Eureka Server utilizando um nome lógico.
- Um cliente (ex: Ribbon) consulta o Eureka Server para obter a lista de instâncias disponíveis para um determinado nome lógico.
- O balanceamento de carga (Ribbon) decide para qual endereço IP e porta enviar a requisição, distribuindo a carga entre as instâncias registradas.
- O uso de IP fixo é desaconselhado, pois não contribui para o balanceamento de carga. O nome lógico é essencial para que o Ribbon possa direcionar as requisições de forma dinâmica.

## 4. Configuração e Anotações do Eureka

### 4.1 Configurando o Eureka Server
- Para ativar um servidor Eureka, é necessário adicionar a dependência `spring-cloud-starter-netflix-eureka-server` ao projeto.
- A classe principal da aplicação deve ser anotada com `@EnableEurekaServer`.
- A configuração da porta e outras propriedades é feita no arquivo `application.properties`.

### 4.2 Configurando o Eureka Client
- Para que um microsserviço atue como cliente e se registre no Eureka Server, a dependência `spring-cloud-starter-netflix-eureka-client` deve ser adicionada.
- A classe principal pode ser anotada com `@EnableDiscoveryClient` (mais genérica) ou `@EnableEurekaClient` (específica para Eureka).
- O endereço do Eureka Server deve ser configurado no `application.properties` do cliente.

### 4.3 Anotações Importantes
- `@EnableEurekaServer`: Habilita a aplicação como um servidor Eureka. Usada na classe principal da aplicação que será o repositório de serviços.
- `@EnableEurekaClient`: Habilita a aplicação como um cliente Eureka, específico para o servidor Eureka. Usada na classe principal do microsserviço.
- `@EnableDiscoveryClient`: Habilita a descoberta de serviços de forma genérica, funcionando com Eureka, Consul ou Zookeeper. Usada na classe principal do microsserviço.

#### 4.3.1 Diferença entre @EnableEurekaClient e @EnableDiscoveryClient
- `@EnableEurekaClient`: É a anotação específica para usar o Eureka como servidor de registro.
- `@EnableDiscoveryClient`: É uma abstração genérica que permite a integração com múltiplos servidores de registro (Service Registry). É a mais recomendada para flexibilidade, embora a questão da FCC considere `@EnableEurekaClient` como a anotação específica para o cliente Eureka.

### 4.4 Configuração no application.properties
- Localizado em `src/main/resources`, é o arquivo central de configuração do Spring Boot.
- Exemplo de configuração para o Eureka Server:
  - `server.port=8761`: Define a porta padrão do Eureka Server.
  - `eureka.client.register-with-eureka=false`: Impede que o servidor se registre nele mesmo.
  - `eureka.client.fetch-registry=false`: Impede que o servidor tente buscar o registro de outros serviços (já que ele é o registro).

> [!TIP] DICAS:
> - A porta padrão do Eureka Server é a 8761.
> - A configuração do Spring Boot é centralizada no arquivo application.properties.
> - Em provas, a FCC cobra a distinção entre `@EnableEurekaClient` (específico) e `@EnableDiscoveryClient` (genérico).

### 4.5 Exemplo de Código: Eureka Server
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApp {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApp.class, args);
    }
}
```

### 4.6 Exemplo de Código: Eureka Client
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;

@SpringBootApplication
@EnableDiscoveryClient
public class MicroserviceApp {
    public static void main(String[] args) {
        SpringApplication.run(MicroserviceApp.class, args);
    }
}
```

> [!CAUTION] OBSERVAÇÃO:
> - Em questões de concurso, a anotação `@EnableEurekaClient` é frequentemente citada como a específica para o cliente Eureka.
> - Embora a anotação `@EnableDiscoveryClient` seja válida e mais genérica, o comando da questão pode pedir a específica para a tecnologia Eureka.

## 5. Tecnologias Complementares (Conceitos)
- Feign: Realiza a comunicação declarativa entre serviços.
- Zuul: Atua como um Gateway API e ponto único de entrada.
- Hystrix: Monitora serviços e atua como um Circuit Breaker, mantendo métricas de execução para avaliar a saúde dos serviços.
- Ribbon: Realiza o balanceamento de carga entre os nós de um serviço.
- Data Envers: Módulo do Hibernate que adiciona funcionalidades de auditoria às entidades JPA, permitindo rastrear alterações nos dados.