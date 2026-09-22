# Introdução ao Spring Boot 6

## 1. Contexto Histórico do Spring Framework
- O Spring Framework surgiu no início dos anos 2000, criado por Rod Johnson após a publicação do livro Enterprise Java EE Patterns.
- Os padrões de projeto prescritos tornaram-se conhecidos como Inversão de Controle (IoC) e Injeção de Dependência (DI).
- Embora nunca tenham sido oficializados pela indústria, foram amplamente adotados, tornando-se um padrão de fato.
- A grande inovação do Spring Framework foi a redução do uso de configurações XML, que eram excessivas na época.
- Com o lançamento do Java 5 e a introdução de anotações, essa necessidade de configuração foi ainda mais reduzida.
- Esse movimento culminou no lançamento do Spring Boot, que trouxe diversas inovações para o ecossistema Spring.

> [!TIP] DICAS:
> - IoC e DI são padrões de projeto fundamentais do Spring, frequentemente cobrados em provas.

## 2. Spring Boot
- O Spring Boot é um framework dentro do ecossistema Spring que facilita o desenvolvimento, a configuração e a implantação de aplicações baseadas em Spring.
- É projetado para simplificar o início de novos projetos Spring, aderindo à filosofia de "convenção sobre configuração".
- Essa filosofia foi popularizada pelo framework Ruby on Rails, que estabelece convenções dentro do framework, eliminando a necessidade de configurar todos os aspectos do sistema.
- O Spring Boot reduz drasticamente a quantidade de configuração necessária, especialmente para aplicações web utilizando o Spring MVC.
- Antes do Spring Boot, para iniciar o uso do Spring, era necessário configurar diversos componentes, como o dispatch service, o view resolver, o handler mapping, entre outros, com códigos conhecidos como "boilerplate".
- Ao utilizar outros recursos, como o Spring Security, era necessário configurar múltiplos itens para implementar filtros de segurança, autenticação e autorização.

### 2.1 Características Principais
- Criação de aplicações standalone (autocontidas) que não dependem de servidores de aplicação externos.
- Geração de um arquivo JAR (Java Archive) que já inclui um servidor web embutido, conhecido como "fat JAR".
- Arquivo de configuração centralizado: application.properties.
- Ferramentas robustas para monitoramento e otimização, como o Spring Boot Actuator.
- Suporte à GraalVM para geração de executáveis nativos otimizados.

### 2.2 Aplicações Standalone e Fat JAR
- Diferente das aplicações Java Web tradicionais, que geram arquivos WAR (Web Archive) e precisam ser implantadas em servidores como Tomcat ou Wildfly, o Spring Boot gera um arquivo JAR que já inclui um servidor web embutido.
- Esse tipo de arquivo JAR é conhecido como "fat JAR" pois contém toda a aplicação web e as bibliotecas necessárias.
- Qualquer ambiente com Java pode executar esse JAR, que inicia a aplicação web automaticamente, geralmente na porta 8080.

> [!TIP] DICAS:
> - A geração de fat JAR é uma das principais características do Spring Boot para aplicações standalone.

### 2.3 Arquivo Application.Properties
- Localizado no diretório src/main/resources, este arquivo é crucial para personalizar a configuração padrão do Spring Boot.
- Permite ajustar detalhes da aplicação sem alterar o código fonte, tornando a aplicação fácil de configurar e implantar em diferentes ambientes.
- Centraliza todas as configurações em um único arquivo, facilitando a manutenção e o diagnóstico de problemas.
- Oferece suporte a diversas configurações, como integração com bancos de dados, caches (como o Redis) e outros serviços essenciais.
- Exemplo de configuração no application.properties:
```
# Configuração do servidor
server.port=8080
server.servlet.context-path=/app

# Configurações do DataSource
spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
spring.datasource.username=root
spring.datasource.password=senha

# JPA/Hibernate
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.format_sql=true

# Logging
logging.level.org.springframework.web=INFO
logging.level.org.hibernate=ERROR

# Actuator
management.endpoints.web.exposure.include=*
management.endpoint.health.show-details=always
```

### 2.4 Spring Boot Actuator
- O Spring Boot Actuator é uma ferramenta que fornece recursos para monitorar e gerenciar aplicações.
- Permite acessar informações sobre o estado e o desempenho da aplicação em tempo real.
- Ao incluir a dependência do Actuator no projeto, diversos endpoints são ativados automaticamente.

Principais endpoints do Actuator:
- /actuator/health: retorna dados sobre o status de funcionamento da aplicação, indicando se está "up" (em operação), com detalhes sobre componentes como banco de dados e espaço em disco.
- /actuator/info: retorna informações sobre a aplicação, como nome, versão e descrição.
- /actuator/metrics: exibe métricas detalhadas, como o uso de memória pela JVM.
- /actuator/env: apresenta informações sobre variáveis de ambiente, como a versão do Java em uso.

### 2.5 GraalVM
- A GraalVM é uma tecnologia que permite que o arquivo final gerado (o "fat JAR") seja extremamente otimizado.
- Possibilita a geração de executáveis nativos para a arquitetura da máquina, reduzindo significativamente o tamanho do arquivo e o uso de recursos.
- Comparada a uma imagem JVM padrão, a aplicação gerada com GraalVM:
  - Consome menos memória;
  - Ocupa um espaço reduzido (ex: de centenas de megabytes para apenas 5 a 12 megabytes);
  - Possui tempo de inicialização mais rápido.
- É especialmente útil em ambientes de computação em nuvem (cloud-native) e ambientes containerizados como Docker.

> [!CAUTION] OBSERVAÇÃO:
> - GraalVM reduz o consumo de memória e o tempo de inicialização, ao contrário do que muitas questões de concurso tentam afirmar.

## 3. Spring Boot Initializr
- O Spring Initializr é uma ferramenta online disponível em https://start.spring.io/ que permite a criação rápida de uma aplicação Spring Boot pré-configurada.
- Permite definir parâmetros como:
  - Linguagem de programação (Java, Kotlin ou Groovy);
  - Sistema de build (Maven ou Gradle);
  - Versão do Spring Boot;
  - Nome do projeto e descrição;
  - Tipo de empacotamento (WAR ou JAR);
  - Versão do Java.
- Na seção de dependências, podem ser adicionados os starters (starter web, starter JPA, DevTools, Actuator, etc.).
- Após a seleção das dependências, a aplicação é gerada com todas as configurações necessárias já integradas.

### 3.1 Spring CLI
- O Spring CLI é uma interface de linha de comando com funcionalidades similares ao Spring Initializr.
- Permite a criação de projetos Spring Boot diretamente pelo terminal, utilizando o comando spring init.
- O Spring Initializer utiliza o Spring Init nos bastidores para gerar o projeto.

## 4. Principais Starters
- Os starters são dependências que agrupam bibliotecas e configurações para funcionalidades específicas.

| STARTER | FUNCIONALIDADE |
|---|---|
| spring-boot-starter-web | Desenvolvimento de aplicações web com Spring MVC |
| spring-boot-starter-data-jpa | Integração com bancos de dados usando JPA |
| spring-boot-starter-actuator | Monitoramento e gerenciamento da aplicação em produção |
| spring-boot-starter-test | Suporte para testes com JUnit, Mockito, Hamcrest |
| spring-boot-starter-security | Implementação de segurança na aplicação |
| spring-boot-starter-undertow | Servidor embutido Undertow |
| spring-boot-starter-jetty | Servidor embutido Jetty |
| spring-boot-starter-tomcat | Servidor embutido Tomcat |
| spring-boot-starter-logging | Sistema de log com suporte ao Logback |

> [!TIP] DICAS:
> - Os servidores de aplicação (Tomcat, Jetty, Undertow) são incorporados de forma "embarcada" no fat JAR.
> - A escolha do servidor influencia diretamente na execução da aplicação e é configurada no pom.xml do Maven.

> [!CAUTION] OBSERVAÇÃO:
> - As configurações centralizadas no application.properties simplificam o processo e evitam a dispersão de dados em múltiplos arquivos XML, como era comum em versões anteriores do Spring.

## 5. Características Não Funcionais do Spring Boot
- Spring Boot Starter Actuator: serve para funcionalidades avançadas como monitoramento e rastreamento para aplicações em produção.
- Spring Boot Starter Undertow, Jetty e Tomcat: servem para escolher a opção específica de Embedded Servlet Container.
- Spring Boot Starter Logging: serve para logging usando o Logback, com suporte para diferentes tecnologias de log.

> [!CAUTION] OBSERVAÇÃO:
> - A grande inovação do Spring Boot está nos starters e na auto-configuração, que eliminam a necessidade de configurar diversos arquivos XML para aspectos como segurança e web.