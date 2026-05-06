# Anotações

# DATAMESH

## 1. Conceito, Motivação e Princípios

### 1.1 O que é DataMesh

- **Definição:** O **DataMesh** é uma abordagem moderna de arquitetura de dados que aplica os conceitos de arquitetura de software moderna (como microsserviços e produtos) à gestão de dados.
- **Ideia Central:** Em vez de centralizar todos os dados da organização em um único Data Lake ou Data Warehouse gerenciado por uma equipe central de TI (o que gera **gargalos e sobrecarga**), o DataMesh **descentraliza a responsabilidade pelos dados**.

### 1.2 Os 4 Princípios Fundamentais do DataMesh

1.  **Domínio Orientado (*Domain-Oriented Ownership*):**
    - Cada área de negócio (domínio), como RH, Vendas ou Logística, é a **proprietária** dos seus dados.
    - As equipes de domínio produzem, mantêm e servem seus próprios dados, pois são quem melhor entende o contexto do negócio.

2.  **Dados como Produto (*Data as a Product*):**
    - Os dados devem ser tratados como **produtos reais**, com foco em qualidade, usabilidade, confiabilidade e documentação (catálogo de dados, APIs, métricas de qualidade).
    - Cada produto de dados deve ter um responsável (*Product Owner*) e os usuários (cientistas, analistas) são seus "clientes".

3.  **Infraestrutura como Plataforma de Autoatendimento (*Self-Serve Data Infrastructure as a Platform*):**
    - Uma equipe central fornece uma **plataforma padronizada e de autoatendimento** para que os domínios possam publicar, acessar e gerenciar seus dados com facilidade, sem depender de especialistas de infraestrutura. Isso reduz a barreira técnica.

4.  **Governança Federada Computacional (*Federated Computational Governance*):**
    - A governança não é imposta de cima para baixo, mas **coordenada entre os domínios**.
    - Regras comuns de segurança, qualidade e conformidade são automaticamente aplicadas por meio de **código** (*Governança como Código*), garantindo padronização sem perder a autonomia descentralizada.

## 2. Vantagens, Desafios e Comparação com Data Lake

### 2.1 Vantagens e Desafios

- **Vantagens:**
    - **Escalabilidade Organizacional:** Permite que múltiplas equipes trabalhem com dados de forma simultânea e autônoma, sem um gargalo central.
    - **Agilidade:** As decisões sobre dados são tomadas mais rapidamente, próximas de quem entende do negócio.
    - **Qualidade e Confiança:** A responsabilidade local sobre o dado e o tratamento como produto tendem a aumentar a qualidade e a confiabilidade.

- **Desafios:**
    - **Mudança Cultural:** Exige uma transformação organizacional onde as áreas de negócio assumem a propriedade técnica dos dados.
    - **Padrões e Interoperabilidade:** Garantir que diferentes domínios consigam se comunicar e compartilhar dados requer uma plataforma e padrões bem definidos.
    - **Complexidade Inicial:** Implementar os quatro princípios de forma coordenada é mais complexo do que manter um Data Lake centralizado.

### 2.2 DataMesh vs. Data Lake

| CARACTERÍSTICA | DATA LAKE | DATAMESH |
| :--- | :--- | :--- |
| **Definição** | Repositório **centralizado** de dados brutos. | Arquitetura **descentralizada** de gestão de dados. |
| **Modelo de Governança** | **Centralizado** (equipe única controla tudo). | **Federado** (cada domínio é autônomo e responsável). |
| **Responsabilidade** | Da equipe central de engenharia/BI. | Da **própria equipe de negócio** (domínio). |
| **Foco Principal** | Armazenar e processar grandes volumes. | Tornar os dados acessíveis, reutilizáveis e com responsabilidade distribuída. |

## 3. Análise de Questões de Concurso

### 3.1 Modelo de Governança (CESPE/SUSEP/2025)

- **Enunciado:** "O DataMesh adota um modelo centralizado de governança e integração de dados..."
- **Gabarito:** **ERRADO.**
- **Análise:** O DataMesh adota um modelo de governança **federada e descentralizada**, não centralizada. A consistência não é priorizada em detrimento da escalabilidade; o modelo visa justamente a escalabilidade organizacional através da descentralização.

### 3.2 Princípio "Dados como Produto" (FGV/2024)

- **Enunciado:** "Uma prática de publicar dados com catálogo, APIs e métricas de qualidade exemplifica:"
- **Gabarito:** **C) o princípio de dados como produto na arquitetura Data Mesh.**
- **Análise:** A descrição de um time de negócio tratando seus dados com documentação, qualidade e interfaces de acesso dedicadas é a aplicação direta do princípio **Data as a Product**.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (CESPE/SUSEP) | **E** | Governança no DataMesh é **federada e descentralizada**, não centralizada. |
| **02** (CESPE/SUSEP) | **C** | Dados tratados como produtos e cada domínio é responsável pelos seus dados. |
| **03** | **C** | Domínios gerenciam dados como produtos. |
| **04** | **B** | Data Mesh = responsabilidade descentralizada; Data Lake = responsabilidade centralizada. |
| **05** | **E** | Centralização do pipeline de ETL **não** é um princípio do Data Mesh. |
| **06** | **C** | Publicar dados com catálogo, API e métricas é o princípio de **Dados como Produto**. |