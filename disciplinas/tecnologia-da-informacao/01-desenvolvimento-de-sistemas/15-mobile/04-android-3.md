# Android 3

## 1. Ambiente de Desenvolvimento e Manifesto

### 1.1 Android Studio
- Ferramenta padrão: IDE oficial para desenvolvimento Android.
- Alternativas: IntelliJ IDEA, Eclipse, Visual Studio (com Xamarin).
- Funcionalidades integradas:
  - Emulador: Permite testar aplicativos sem um dispositivo físico.
  - Android Profiler: Analisador de código que monitora o uso de CPU, memória e rendimento da aplicação.

### 1.2 AndroidManifest.xml (Configuração Principal do App)
- Função: Arquivo indispensável que descreve informações essenciais sobre o aplicativo para o sistema operacional.
- Elementos configurados:
  - Componentes: Declaração de Atividades, Serviços, Broadcast Receivers e Provedores de Conteúdo.
  - Permissões (uses-permission): Solicita acesso a recursos como câmera, internet, GPS, envio de SMS.
  - Configuração mínima (uses-feature): Define requisitos de hardware (ex: sensor de bússola, tela).
  - Telas compatíveis (compatible-screens): Especifica as configurações de tela suportadas.
  - Identidade visual: Define o ícone (icon) e o rótulo (label) do aplicativo.

> [!CAUTION] OBSERVAÇÃO: 
> - AndroidManifest.xml é obrigatório em todo aplicativo Android.
> - uses-permission solicita acesso a recursos; uses-feature define requisitos de hardware.

#### 1.2.1 Instrumentation (Testes)
- Definição: Objeto que permite o monitoramento da interação do aplicativo com o sistema para fins de teste.
- Atributos:
  - functionalTest: Habilita execução como teste funcional;
  - handleProfiling: Habilita/desabilita a criação de perfil de operação;
  - targetPackage: Define o pacote alvo do teste;
  - targetProcesses: Define o processo alvo do teste.

## 2. Intents (Intenções)

### 2.1 Conceito e Classificação
- Definição: Mecanismo de comunicação para solicitar uma ação a outro componente (do mesmo app ou de outro app).
- Tipos de intent:
  - Explícita: Especifica exatamente qual componente (classe) irá atender a solicitação (ex: iniciar uma atividade interna específica).
  - Implícita: Declara uma ação genérica (ex: "visualizar uma imagem"), permitindo que o sistema encontre o aplicativo capaz de processá-la.

> [!CAUTION] OBSERVAÇÃO: 
> - Intent explícita: componente específico é definido.
> - Intent implícita: sistema encontra o componente adequado.

### 2.2 Filtro de Intent (Intent Filter)
- Função: Anunciar quais tipos de intents um componente consegue aceitar.
- Elementos de filtragem:
  - Ação (action): A operação a ser realizada (ex: ACTION_VIEW para mostrar algo).
  - Dados (data): O URI ou tipo MIME dos dados a serem operados.
  - Categoria (category): Fornece metadados sobre a intenção.
    - CATEGORY_LAUNCHER: Indica que a atividade é a inicial do app (aparece no Launcher).
    - DEFAULT: Indica que o componente é uma opção padrão para a ação.

## 3. Gerenciamento de Dependências e Recursos

### 3.1 Gradle
- Função: Ferramenta de automação de compilação padrão do Android Studio.
- Responsabilidades: Gerencia o processo de build, baixa dependências e aponta componentes desatualizados.

### 3.2 Classe R e Diretório res
- res (Resources): Diretório com estrutura de árvore que contém todos os recursos visuais e textuais do app (layouts, imagens, cores, strings).
- Classe R: Classe especial gerada automaticamente na compilação que contém referências (IDs) para todos os recursos definidos no diretório res. Permite acessar recursos no código Java/Kotlin (ex: R.id.button, R.string.app_name).

> [!CAUTION] OBSERVAÇÃO: 
> - A classe R é gerada automaticamente durante a compilação.
> - R contém IDs para todos os recursos do diretório res.

## 4. Layouts e Componentes Visuais (Views)

### 4.1 View e ViewGroup
- View (Visão): Objeto principal responsável pela parte visual da aplicação. Todos os componentes visuais (botões, textos, campos) são Views.
- ViewGroup (Grupo de Visão): Contêiner invisível que organiza e posiciona outras Views.

### 4.2 Principais Tipos de Layout

| LAYOUT | DESCRIÇÃO E COMPORTAMENTO |
|---|---|
| LinearLayout | Alinha os componentes em uma única direção: horizontal ou vertical. |
| TableLayout | Organiza os componentes no formato de tabela (linhas e colunas). |
| RelativeLayout | Posiciona elementos de forma relativa uns aos outros ou ao elemento pai. |
| FrameLayout | Layout simples usado como um placeholder para um único item; útil para sobreposições (overlay). |
| ConstraintLayout | Similar ao RelativeLayout, mas com melhor desempenho e mais integrado ao Layout Editor. Ideal para layouts complexos. |

> [!CAUTION] OBSERVAÇÃO: 
> - View é o componente visual básico; ViewGroup é o contêiner que organiza Views.
> - ConstraintLayout é recomendado para layouts complexos por seu melhor desempenho.


## 5. Componentes de Interface do Usuário (UI Components)

### 5.1 Principais Widgets
- TextView: Utilizado para exibir texto na tela.
- Button: Botão clicável para acionar ações.
- RecyclerView: Lista otimizada que reutiliza as views dos itens conforme o usuário rola a tela, melhorando a performance e o uso de memória.
- Switch: Componente de interruptor ("liga/desliga").

> [!CAUTION] OBSERVAÇÃO: 
> - RecyclerView reutiliza views para melhor performance e menor consumo de memória.

### 5.2 Manipulação Programática (MainActivity.java)
- Ciclo de vida inicial: No método onCreate(), o layout XML é vinculado à atividade via setContentView(R.layout.activity_main).
- Acesso a componentes: O método findViewById(R.id.id_do_componente) localiza e retorna uma referência ao componente declarado no XML.
- Alteração de propriedades:
  - Exemplo: Para alterar o texto de um TextView cujo ID é resultado:
    - TextView resultado = findViewById(R.id.resultado);
    - resultado.setText("Sucesso!");

## 6. Fragments

### 6.1 Definição e Características
- Conceito: Um Fragment é uma parte modular e reutilizável da interface do usuário (UI) de uma atividade.
- Ciclo de vida: Possui ciclo de vida próprio, embora esteja sempre atrelado ao ciclo de vida da atividade hospedeira.
- Dependência: Um fragment depende de uma Activity (ou de outro Fragment) para existir.

### 6.2 Gerenciamento
- Adição dinâmica: Podem ser adicionados programaticamente a partir do estado onStart() da atividade.
- Biblioteca: Dependem da biblioteca AndroidX Fragment.

> [!CAUTION] OBSERVAÇÃO: 
> - Fragment tem ciclo de vida próprio, mas depende da Activity hospedeira.
> - Fragment é adicionado dinamicamente a partir do onStart() da Activity.