# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – ANDROID IV (UI, FRAGMENTS E QUESTÕES)

## 1. Componentes de Interface do Usuário (UI Components)

### 1.1 Principais Widgets

- **`TextView`:** Utilizado para exibir texto na tela.
- **`Button`:** Botão clicável para acionar ações.
- **`RecyclerView`:** Lista otimizada que **reutiliza** as *views* dos itens conforme o usuário rola a tela, melhorando a *performance* e o uso de memória.
- **`Switch`:** Componente de interruptor ("liga/desliga").

### 1.2 Manipulação Programática (MainActivity.java)

- **Ciclo de Vida Inicial:** No método `onCreate()`, o layout XML é vinculado à atividade via `setContentView(R.layout.activity_main)`.
- **Acesso a Componentes:** O método `findViewById(R.id.id_do_componente)` localiza e retorna uma referência ao componente declarado no XML.
- **Alteração de Propriedades:**
    - Exemplo: Para alterar o texto de um `TextView` cujo ID é `resultado`:
    ```java
    TextView resultado = findViewById(R.id.resultado);
    resultado.setText("Sucesso!");
    ```

## 2. Fragments

### 2.1 Definição e Características

- **Conceito:** Um **Fragment** é uma parte modular e reutilizável da interface do usuário (UI) de uma atividade.
- **Ciclo de Vida:** Possui **ciclo de vida próprio**, embora esteja sempre atrelado ao ciclo de vida da atividade hospedeira.
- **Dependência:** Um fragment **depende** de uma `Activity` (ou de outro *Fragment*) para existir.

### 2.2 Gerenciamento

- **Adição Dinâmica:** Podem ser adicionados programaticamente a partir do estado `onStart()` da atividade.
- **Biblioteca:** Dependem da biblioteca **AndroidX Fragment**.

## 3. Análise de Questões de Concurso

### 3.1 Método `onCreate()` (AOCP/2019)

- **Enunciado:** Inserir operações de carregamento de layout e inicialização que devem ser executadas **somente uma vez**.
- **Gabarito:** **`onCreate()`**. É o método chamado uma única vez no início do ciclo de vida para configurações essenciais.
- **Observação:** Recebe como parâmetro um `Bundle` para restaurar estados salvos anteriormente.

### 3.2 Conceito de Intent (FGV/2024)

- **Definição Correta:** É um mecanismo de **entrega de mensagens** entre diferentes partes do sistema Android.
- **Classificação:** Podem ser classificados em **Explícitos** (chamam um componente específico) ou **Implícitos** (declaram uma ação genérica a ser resolvida pelo sistema).
- **Escopo:** Não se restringe a um único aplicativo; serve para comunicação entre apps.

### 3.3 Estados da Activity (IF-SP/2023)

- **I - Correta:** `onCreate()` é usado para configurar a interface de usuário.
- **II - Incorreta:** `onStart()` pode ser invocado **diretamente** após o `onCreate()`, não apenas após `onRestart()`.
- **III - Correta:** `onResume()` é executado sempre que a Activity volta a ter o foco (primeiro plano).
- **Gabarito:** **I e III**.

### 3.4 Arquivo `AndroidManifest.xml` (IF-SP/2023)

- **Testes Unitários:** A *tag* usada para ativar o suporte a testes de unidade no projeto é a **`Instrumentation`**.

### 3.5 IDEs para Android (IBFC/2022)

- **Alternativa Incorreta:** **Emacs**. O Emacs é um editor de texto, não uma IDE específica ou amplamente utilizada como padrão para desenvolvimento Android. As IDEs incluem Eclipse, **Android Studio** (oficial) e Visual Studio (com Xamarin).

### 3.6 Layout para Formulário Longo (AOCP/2019)

- **Cenário:** Criar um longo formulário de entrada de dados.
- **Layout Indicado:** **Table Layout**, por sua característica de organização em linhas e colunas, ideal para campos de formulário.

### 3.7 Conceitos Fundamentais (IADES/2021)

- **Assertiva Correta:** Existem **quatro tipos de componentes** de aplicativo: Atividades, Serviços, *Broadcast Receivers* e Provedores de Conteúdo.
- **Erros nas demais:**
    - *ViewGroups* **podem** conter outros *ViewGroups*.
    - `Button` **é** uma subclasse de `View`.
    - `LinearLayout` **é** uma subclasse de `View`.
    - Todo projeto **precisa** do arquivo `AndroidManifest.xml`.

### 3.8 `ConstraintLayout` (AOCP/2021)

- **Afirmativa da Banca:** Comentário sobre o uso de grupos aninhados.
- **Análise da Banca:** Considerado **Errado**. A vantagem do `ConstraintLayout` é justamente criar layouts complexos com hierarquia **plana** (sem necessidade de grupos aninhados profundos), melhorando o desempenho.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (AOCP/2019) | **A** | `onCreate()` para operações executadas uma única vez. |
| **02** (FGV/2024) | **B** | *Intent* é mecanismo de entrega de mensagens. |
| **03** (IF-SP/2023) | **A** | I e III corretas. `onStart()` pode seguir `onCreate()` diretamente. |
| **04** (IF-SP/2023) | **C** | *Tag* `Instrumentation` para testes unitários. |
| **05** (IBFC/2022) | **A** | Emacs não é uma IDE padrão para desenvolvimento Android. |
| **06** (IDECAN/2020) | **A** | Todas as afirmativas sobre Activity e Intent estão corretas. |
| **07** (AOCP/2019) | **C** | `TableLayout` para formulário de entrada de dados. |
| **08** (IADES/2021) | **C** | Quatro componentes: Activities, Services, Broadcast Receivers, Content Providers. |
| **09** (AOCP/2021) | **E** | `ConstraintLayout` não necessita de grupos aninhados profundos. |
| **10** (AOCP/2021) | **C** | `View` é a base do design da UI. |
| **11** (CESGRANRIO/2023) | **D** | `resultado.setText("Sucesso!");` |