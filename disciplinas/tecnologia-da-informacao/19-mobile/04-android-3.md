# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – ANDROID III (FERRAMENTAS E ARQUIVOS)

## 1. Ambiente de Desenvolvimento e Manifesto

### 1.1 Android Studio

- **Ferramenta Padrão:** IDE oficial para desenvolvimento Android.
- **Alternativas:** IntelliJ IDEA, Eclipse, Visual Studio (com Xamarin).
- **Funcionalidades Integradas:**
    - **Emulador:** Permite testar aplicativos sem um dispositivo físico.
    - **Android Profiler:** Analisador de código que monitora o uso de **CPU, memória e rendimento** da aplicação.

### 1.2 AndroidManifest.xml (Configuração Principal do App)

- **Função:** Arquivo **indispensável** que descreve informações essenciais sobre o aplicativo para o sistema operacional.
- **Elementos Configurados:**
    - **Componentes:** Declaração de Atividades, Serviços, *Broadcast Receivers* e Provedores de Conteúdo.
    - **Permissões (`uses-permission`):** Solicita acesso a recursos como **câmera, internet, GPS**, envio de SMS.
    - **Configuração Mínima (`uses-feature`):** Define requisitos de hardware (ex: sensor de bússola, tela).
    - **Telas Compatíveis (`compatible-screens`):** Especifica as configurações de tela suportadas.
    - **Identidade Visual:** Define o **ícone** (`icon`) e o **rótulo** (`label`) do aplicativo.

> ### 1.2.1 Instrumentation (Testes)
- **Definição:** Objeto que permite o **monitoramento da interação** do aplicativo com o sistema para fins de teste.
- **Atributos:**
    - **`functionalTest`:** Habilita execução como teste funcional.
    - **`handleProfiling`:** Habilita/desabilita a criação de perfil de operação.
    - **`targetPackage`:** Define o pacote alvo do teste.
    - **`targetProcesses`:** Define o processo alvo do teste.

## 2. Intents (Intenções)

### 2.1 Conceito e Classificação

- **Definição:** Mecanismo de comunicação para solicitar uma ação a outro componente (do mesmo app ou de outro app).
- **Tipos de Intent:**
    - **Explícita:** **Especifica** exatamente qual componente (classe) irá atender a solicitação (ex: iniciar uma atividade interna específica).
    - **Implícita:** Declara uma **ação genérica** (ex: "visualizar uma imagem"), permitindo que o sistema encontre o aplicativo capaz de processá-la.

### 2.2 Filtro de Intent (Intent Filter)

- **Função:** Anunciar quais tipos de *intents* um componente consegue aceitar.
- **Elementos de Filtragem:**
    - **Ação (`action`):** A operação a ser realizada (ex: `ACTION_VIEW` para mostrar algo).
    - **Dados (`data`):** O URI ou tipo MIME dos dados a serem operados.
    - **Categoria (`category`):** Fornece metadados sobre a intenção.
        - **`CATEGORY_LAUNCHER`:** Indica que a atividade é a inicial do app (aparece no Launcher).
        - **`DEFAULT`:** Indica que o componente é uma opção padrão para a ação.

## 3. Gerenciamento de Dependências e Recursos

### 3.1 Gradle

- **Função:** Ferramenta de **automação de compilação** padrão do Android Studio.
- **Responsabilidades:** Gerencia o processo de *build*, baixa **dependências** e aponta componentes desatualizados.

### 3.2 Classe R e Diretório `res`

- **`res` (Resources):** Diretório com estrutura de árvore que contém todos os **recursos visuais e textuais** do app (layouts, imagens, cores, strings).
- **Classe `R`:** Classe especial gerada automaticamente na compilação que contém **referências (IDs)** para todos os recursos definidos no diretório `res`. Permite acessar recursos no código Java/Kotlin (ex: `R.id.button`, `R.string.app_name`).

## 4. Layouts e Componentes Visuais (Views)

### 4.1 View e ViewGroup

- **`View` (Visão):** Objeto principal responsável pela parte visual da aplicação. Todos os componentes visuais (botões, textos, campos) são *Views*.
- **`ViewGroup` (Grupo de Visão):** Contêiner invisível que organiza e posiciona outras *Views*.

### 4.2 Principais Tipos de Layout

| LAYOUT | DESCRIÇÃO E COMPORTAMENTO |
| :--- | :--- |
| **LinearLayout** | Alinha os componentes em uma **única direção**: horizontal ou vertical. |
| **TableLayout** | Organiza os componentes no formato de **tabela** (linhas e colunas). |
| **RelativeLayout** | Posiciona elementos de forma **relativa** uns aos outros ou ao elemento pai. |
| **FrameLayout** | Layout simples usado como um *placeholder* para um único item; útil para sobreposições (*overlay*). |
| **ConstraintLayout** | Similar ao *RelativeLayout*, mas com melhor desempenho e mais integrado ao *Layout Editor*. Ideal para layouts complexos. |