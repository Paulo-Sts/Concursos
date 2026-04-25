# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – ANDROID

## 1. Fundamentos do Sistema Operacional Android

### 1.1 Origem e Arquitetura Básica

- **Desenvolvedor:** **Google** (empresa original Android Inc. foi adquirida).
- **Base:** O Android é um sistema operacional baseado no núcleo **Linux**.
- **Modelo Multiusuário:** Trabalha como um sistema **multiusuário**, onde **cada aplicativo é um "usuário" diferente** do sistema.
    - Cada app possui um **ID único** (UID) no sistema operacional, o qual **não é conhecido** pelo próprio aplicativo.
    - As **permissões** de acesso aos arquivos são concedidas com base nesse ID.
- **Princípio do Privilégio Mínimo:** O app, por padrão, tem acesso apenas aos recursos mínimos para funcionar. O **usuário** define quais permissões extras são concedidas.

### 1.2 Linguagens de Programação e Pacotes

- **Linguagens Suportadas:** **Kotlin**, **Java** e **C++** (via NDK).
    - No **Android Studio** (ambiente oficial), as opções padrão são Java e Kotlin.
    - **Interoperabilidade (Java x Kotlin):** É possível construir apps com código misto, onde um chama funções do outro sem restrições.
- **Formatos de Saída:**
    - **APK (`.apk`):** Arquivo de instalação do aplicativo.
    - ***Bundle* (`.aab`):** Formato de publicação na Google Play. O servidor da Google gera APKs otimizados para cada dispositivo a partir do *bundle*.

### 1.3 Ambiente de Execução (Máquina Virtual)

- **Isolamento:** Cada aplicativo roda em uma **Máquina Virtual (VM) isolada**, garantindo segurança e estabilidade.
- **Compartilhamento de ID:** Dois aplicativos podem ser configurados para **compartilhar o mesmo ID de usuário**, permitindo que rodem na mesma VM e compartilhem recursos.

## 2. Componentes Principais de um Aplicativo (App Components)

| COMPONENTE | FUNÇÃO | INTERFACE VISUAL |
| :--- | :--- | :---: |
| **Atividades (*Activities*)** | **Ponto de entrada** para interação com o usuário. Cada tela do app é uma atividade. | **Sim** |
| **Serviços (*Services*)** | Executa tarefas em **segundo plano** (*background*), sem interação direta do usuário. | **Não** |
| ***Broadcast Receivers*** | **Receptores de eventos** do sistema ou de outros apps (Ex: bateria fraca, inicialização). | **Não** |
| **Provedores de Conteúdo (*Content Providers*)** | **Gerenciam dados compartilhados** (arquivos, SQLite, web) entre diferentes aplicativos. | **Não** |

### 2.1 Atividades (Activities)

- **Definição:** Componente focado na **interação com o usuário**.
- **Mapeamento:** **Cada tela** do aplicativo corresponde a uma **Atividade**.
- **Ciclo de Vida:** Possui métodos de ***callback*** (ex: `onCreate()`, `onStart()`, `onResume()`) que equivalem a estados do seu ciclo de vida.
- **Invocação Externa:** Um aplicativo externo pode chamar uma Atividade de outro app, desde que tenha **permissão** para tal.

### 2.2 Serviços (Services)

- **Definição:** Componente para executar operações **sem interface de usuário**.
- **Tipos de Serviço:**
    1.  ***Foreground Service* (Primeiro Plano):** Executa tarefas perceptíveis ao usuário. **Obrigatoriamente** exibe uma **notificação** enquanto está ativo (Ex: Player de música, rastreamento de exercício). É contínuo.
    2.  ***Background Service* (Segundo Plano):** Executa tarefas não notadas pelo usuário (Ex: compactação de arquivos). O sistema Android pode **interrompê-lo ou limitá-lo** para economizar recursos.
    3.  ***Bound Service* (Vinculado):** Oferece uma interface cliente-servidor. Vários componentes podem **se vincular** a ele. O serviço é destruído quando não há mais vinculações.

### 2.3 Broadcast Receivers

- **Definição:** Componente que **escuta e reage** a anúncios de eventos do sistema ou de outras aplicações.
- **Funcionamento:** Funcionam como uma **entrada de eventos**, mesmo que o aplicativo não esteja em execução.
- **Exemplos de Eventos:** Bateria fraca, inicialização do dispositivo, recebimento de SMS.
- **Transmissão:** O sistema envia eventos ao app; aplicativos também podem transmitir informações para outros apps.

### 2.4 Provedores de Conteúdo (Content Providers)

- **Definição:** Gerencia o acesso a um conjunto de **dados estruturados**.
- **Função:** Encapsulam dados e fornecem mecanismos de segurança para compartilhamento entre diferentes aplicativos.
- **Acesso:** Outros apps podem consultar ou alterar dados do provedor se tiverem a **permissão** adequada.
- **Mecanismo:** A manipulação é feita através de **URIs** (*Uniform Resource Identifiers*).

## 3. Dados e Arquivos (Persistência)

### 3.1 Tipos de Armazenamento

- **Armazenamento Específico do App:** Diretórios privados para cada aplicativo.
- **Armazenamento Compartilhado:** Dados acessíveis por múltiplos apps.
- **Banco de Dados:** Utilização do **SQLite**, integrado ao sistema.

### 3.2 Room e ORM

- **Room:** Biblioteca de persistência que funciona como uma camada de abstração sobre o **SQLite**.
- **ORM (*Object-Relational Mapping*):** Tecnologia que permite mapear objetos Java/Kotlin para tabelas do banco de dados, facilitando a codificação.
- **Componentes do Room:**
    - **`@Entity`:** Anotação que define a classe como uma tabela do banco.
    - **`@PrimaryKey`:** Define a chave primária.
    - **`@ColumnInfo`:** Personaliza o nome da coluna.
    - **`@Dao`:** Interface/Classe que realiza as operações de manipulação (CRUD) no banco (`insert`, `select`, `delete`).