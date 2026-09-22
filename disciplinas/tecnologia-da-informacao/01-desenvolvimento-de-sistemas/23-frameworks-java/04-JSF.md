# JSF

## 1. Introdução ao JavaServer Faces (JSF)
- O JSF é uma evolução natural do JSP, surgiu no início dos anos 2000 como resposta ao ASP.NET da Microsoft, trazendo melhorias à gestão de interface.
- O JSP surgiu como resposta ao CDI e ao PHP, enquanto o JSF foi desenvolvido para resolver problemas de interface no Java.
- Versões iniciais utilizavam JSP para renderizar interfaces, mas com as evoluções passaram a utilizar Facelets (XHTML) como tecnologia de visualização padrão.

### 1.1 Histórico e Contexto
- JSF é um framework baseado em Java para simplificar a construção de interfaces de usuário (UI) para aplicações web.
- É um padrão oficial que faz parte da plataforma Java Enterprise Edition (Java EE), atualmente Jakarta EE, em sua versão 4.0 sob a nova nomenclatura Jakarta Faces.
- Haviam muitos bugs nas versões iniciais, que foram resolvidos em versões mais recentes.
- Nas provas, as versões 2.2 para baixo são muito cobradas pelas bancas.

> [!CAUTION] OBSERVAÇÃO:
> - O JSF unir as camadas de apresentação e regras de negócio é uma pegadinha comum. O framework busca justamente separá-las, aumentando a coesão e diminuindo o acoplamento.

### 1.2 Propósito e Diferenciais
- Criado para fornecer uma abordagem simplificada ao design de interfaces de usuário em comparação com tecnologias mais antigas como Servlets e JSP.
- O Facelets foi introduzido como tecnologia de visualização padrão no JSF 2.0, oferecendo separação mais clara entre comportamento e apresentação e melhor suporte para reutilização de código.
- O padrão MVC foi melhor delimitado, com XHTML representando a interação com o usuário, Facelets como controle e Managed Beans como modelo.

> [!TIP] DICAS:
> - JSF é um framework para abstrair a web e é orientado a eventos; eventos que acontecem no front-end são refletidos no back-end.
> - A banca costuma cobrar: JSF simplifica o design de UI comparado a Servlets e JSP; JSP foi usado como template nas primeiras versões; Facelets foi introduzido no JSF 2.0.

## 2. Exemplo Prático de Código JSF
- A view HTML importa a biblioteca padrão do JSF com o prefixo "h" seguido de tags, como h:head, h:body e h:form.
- h:form contém componentes prontos, como h:inputText, que utiliza EL (Expression Language) do JSF para vinculação (ex.: userBean.name), que tecnicamente utiliza setName e getName.
- O atributo required="true" torna o campo obrigatório.
- h:commandButton possui o atributo action="#{userBean.submit}" que atribui um método da classe Java submit.
- Exemplo de código XHTML:
```xhtml
<h:form>
    <h:inputText value="#{userBean.name}" required="true" />
    <h:commandButton value="Enviar" action="#{userBean.submit}" />
</h:form>
```

### 2.1 Managed Beans e Escopos
- @RequestScoped define que a cada requisição será instanciado um novo objeto da classe para responder àquela requisição.
- @ManagedBean registra o Bean que responderá ao XHTML, dispensando configurações diretas no arquivo faces-config.xml.
- O método submit invoca a constante getCurrentInstance, adicionando uma mensagem global do JSF ao FacesContext.
- Exemplo de código Java:
```java
@ManagedBean
@RequestScoped
public class UserBean {
    private String name;
    
    public String submit() {
        FacesContext.getCurrentInstance().addMessage(null, 
            new FacesMessage("Dados submetidos com sucesso!"));
        return null; // permanece na mesma página
    }
    // getters e setters
}
```

### 2.2 Componentes de Interface
- h:messages com atributo globalOnly exibe apenas mensagens globais.
- h:outputText exibe o valor do atributo name do UserBean, renderizado apenas se userBean.name não for vazio.

> [!TIP] DICAS:
> - A EL (Expression Language) no JSF utiliza o padrão JavaBeans para acessar propriedades (getters/setters).
> - "Return null" significa que pode retornar o nome da página de navegação ou ficar na mesma página.

## 3. Arquitetura MVC no JSF
- O JSF utiliza o padrão MVC para separar lógica de negócios (Model), interface do usuário (View) e controle de fluxo (Controller).
- O MVC garante que os componentes não interfiram entre si, aumentando a coesão e diminuindo o acoplamento.
- Se a View precisar mudar de XHTML para JSP, essa alteração não afeta o Controller nem o Model.

### 3.1 Componentes do MVC
- Model: Os Managed Beans representam o modelo, gerenciando os dados e ações do usuário.
- View: As páginas Facelets (XHTML) são a camada de visualização, onde os componentes JSF criam a interface gráfica.
- Controller: O FacesServlet atua como controlador, processando solicitações, manipulando eventos, navegando entre páginas e conectando visão e modelo.

> [!CAUTION] OBSERVAÇÃO:
> - O MVC é um padrão conceitual, não um arquivo específico. Arquivos como Controle.java, View.java e Model.java não são arquivos de configuração do JSF.

## 4. FacesServlet
- É o ponto de entrada para todas as requisições JSF.
- Mapeado na configuração web.xml, intercepta solicitações para arquivos XHTML e inicia o processamento do ciclo de vida do JSF.
- Responsável por criar e restaurar visualizações e renderizar respostas ao usuário.
- Reconhece os Managed Beans por meio do arquivo faces-config.xml.
- Exemplo de configuração no web.xml:
```xml
<web-app>
    <servlet>
        <servlet-name>Faces Servlet</servlet-name>
        <servlet-class>javax.faces.webapp.FacesServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>Faces Servlet</servlet-name>
        <url-pattern>*.xhtml</url-pattern>
    </servlet-mapping>
</web-app>
```

### 4.1 faces-config.xml
- Define o nome do Managed Bean, pacote, classe e escopo.
- Na prática, o arquivo faces-config geralmente fica sem configurações de Managed Beans porque as anotações nas classes são recuperadas em tempo de execução.
- Exemplo de faces-config.xml vazio:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<faces-config xmlns="http://xmlns.jcp.org/xml/ns/javaee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee 
    http://xmlns.jcp.org/xml/ns/javaee/web-facesconfig_2_2.xsd"
    version="2.2">
</faces-config>
```

> [!TIP] DICAS:
> - FacesServlet é o front controller da aplicação; o objeto dele é o FacesContext, disponível em toda a aplicação.
> - Requisições JSF processadas são direcionadas para o FacesServlet, que cria o objeto FacesContext.

> [!CAUTION] OBSERVAÇÃO:
> - As bancas CESPE/CEBRASPE costumam cobrar que o JSF utiliza JSP como template padrão em versões iniciais, mas Facelets (XHTML) passou a ser usado a partir do JSF 2.0.
> - Facelets é uma linguagem de marcação, não de declaração.

## 5. Componentes JSF
- Componentes são objetos de UI reutilizáveis que geram marcação HTML no lado do cliente.
- São organizados em uma árvore de componentes, refletindo a estrutura e o layout da página.
- Suportam funcionalidades como validação, conversão de dados e gerenciamento de eventos.

## 6. Integração com Managed Beans
- Os componentes interagem com os Managed Beans por meio de EL (Expression Language), vinculando dados e ações.
- Os Managed Beans podem ter escopos de requisição, sessão ou aplicação, controlando como cada classe será instanciada ao longo do ciclo de vida da aplicação.
- Fornecem uma abordagem orientada a objetos para o desenvolvimento da camada de negócios e interação com a camada de apresentação.

## 7. Construtores de UI e Tag Libraries
- JSF fornece bibliotecas de tags ricas para declarar componentes de interface do usuário nas páginas.
- As tag libraries incluem HTML Taglib e Core Taglib, com tags que correspondem aos componentes JSF e gerenciam o comportamento do lado do servidor.
- Principais prefixos:
  - h: referência à taglib HTML do JSF;
  - c: referência à Taglib Core (também presente no JSP).

## 8. Arquivos de Configuração Essenciais para JSF
- faces-config.xml: arquivo de configuração do JSF.
- web.xml: arquivo de configuração da aplicação web.

> [!TIP] DICAS:
> - persistence.xml é arquivo de configuração da fonte de dados (JPA).
> - bean.xml é arquivo de configuração do CDI (Contexts and Dependency Injection).

> [!CAUTION] OBSERVAÇÃO:
> - O JSF é uma implementação voltada para interface de aplicações web com modelo de programação dirigida a eventos (event-driven).