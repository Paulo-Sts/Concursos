# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – CONCEITOS BÁSICOS

## 1. Sistemas Operacionais Móveis

### 1.1 Principais Plataformas

- **Android:** Desenvolvido pela **Google**. É um sistema ***Open Source***, permitindo acesso ao código-fonte para customizações por diversos fabricantes.
- **iOS:** Desenvolvido pela **Apple**. É um sistema **exclusivo** (não *Open Source*), utilizado apenas em dispositivos fabricados pela própria empresa (iPhone, iPad).

### 1.2 Tipos de Aplicativos (Formas de Desenvolvimento)

| CARACTERÍSTICA | APLICATIVO NATIVO | APLICATIVO MULTIPLATAFORMA (HÍBRIDO/CRUZADO) |
| :--- | :--- | :--- |
| **Linguagens/Base** | **Android:** Java, Kotlin.<br>**iOS:** Objective-C, Swift. | **Um código base** adaptado para diferentes SOs. Ex: HTML, CSS, JS (Ionic) ou Dart (Flutter). |
| **Compilação/Acesso** | Acesso direto a bibliotecas e APIs do sistema. Performance **otimizada**. | Roda em ***WebView*** (navegador embutido) ou é compilado para código nativo. |
| **Vantagens** | **Alto desempenho**, acesso total a recursos do hardware (GPS, Câmera), UI nativa. | **Menor custo e tempo** de desenvolvimento, reutilização de código. |
| **Desvantagens** | Maior custo (equipes diferentes para cada SO). | Desempenho pode ser inferior ao nativo, dependendo da ponte de comunicação com o hardware. |

> ### 1.2.1 Frameworks Multiplataforma (Questão ADM&TEC/2024)
- **Principais Estruturas (Plataforma Cruzada):**
    - **React Native** (Facebook/Meta).
    - **Flutter** (Google).
    - **Xamarin** (Microsoft).
    - **Ionic** (Utiliza WebView: HTML, CSS, JS).
- **Observação da Banca:** O uso de plataforma cruzada **reduz** (e não aumenta) o custo e o tempo final do projeto.

## 2. Comportamentos e Funcionalidades Comuns em Apps

### 2.1 Design e Usabilidade

- **Responsividade:** O design deve se adaptar a diferentes resoluções de tela (celular, tablet, TV), sem distorcer ou cortar o conteúdo.
- **Intuitividade:** A interface deve ser fácil de usar, com recursos interativos que guiam o cliente.
- **Tecnologias de Suporte:** *Frameworks* de *frontend* (ex: **Bootstrap**) ainda são amplamente utilizados para garantir acessibilidade responsiva, não caindo em desuso (CESPE/2019).

### 2.2 Performance e Segurança

- **Desempenho:** As aplicações devem se preocupar com o tempo de carregamento de telas, otimização de serviços e **consumo de bateria**.
- **Segurança:** É crucial devido à vulnerabilidade a ataques. Envolve práticas como a **criptografia** de dados (ex: mensagens do WhatsApp, transações bancárias).

### 2.3 Conectividade e Armazenamento

- **Sincronização *Online/Offline*:** Permite acesso a conteúdos sem consumir dados móveis, mediante **download prévio**.
- **Recuperação de Falhas (*Failover*):** Capacidade do app de se recuperar e continuar funcionando mesmo quando o hardware ou software apresentam falhas.

### 2.4 Testes de Configuração (CESPE/TELEBRAS/2022)

- **Definição:** Testes que verificam o comportamento do aplicativo em **diferentes versões de hardware e software** (diferentes modelos de aparelho, versões de SO).
- **Erro Comum:** **Não** se referem à verificação de tempos de resposta ou recuperação de falhas (isso é teste de performance/resiliência).

## 3. Análise de Questões Específicas

### 3.1 Linguagem Nativa: Kotlin x Java (CESGRANRIO/2023)

- **Afirmativa:** Grau de compatibilidade entre Kotlin e Java no Android.
- **Realidade:** Há **interoperabilidade total**. É possível construir um aplicativo com código parcialmente em Java e parcialmente em Kotlin, permitindo que um chame funções do outro sem restrições. Ambas rodam na JVM.

### 3.2 Aplicações Híbridas e WebView (AOCP/2021)

- **Afirmativa da Banca:** "Aplicativo híbrido **não contém** uma instância isolada do navegador (*WebView*)...".
- **Análise:** **ERRADO**. A definição clássica de aplicativo híbrido (como os construídos com Ionic/Cordova) é justamente executar um aplicativo web (HTML, CSS, JS) **dentro de um *WebView*** (navegador embutido no app nativo).

### 3.3 Funcionamento do GPS (IGEDUC/2023)

- **Afirmativa:** "O GPS funciona com base em torres de celular...".
- **Análise:** **ERRADO**. O sistema de **GPS** (*Global Positioning System*) baseia-se numa rede de **satélites** para determinar a posição. A triangulação de torres de celular é um método auxiliar de localização, usado quando o sinal de satélite está fraco, mas não é a base do GPS.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FURB/2024) | **C** | Android (Google), iOS (Apple), Sistemas Operacionais Móveis. |
| **02** (IGEDUC/2023) | **E** | GPS funciona com base em **satélites**. |
| **03** (CEBRASPE/2019) | **E** | *Frameworks* de responsividade (ex: Bootstrap) não caíram em desuso. |
| **04** (AOCP/2021) | **E** | Aplicativo híbrido **utiliza** *WebView* para executar conteúdo web. |
| **05** (IBFC/2019) | **C** | I e III corretas. Aplicativo Android **não** roda nativamente no iOS. |
| **06** (CEBRASPE/2022) | **E** | Testes de configuração = hardware/software; Recuperação = resiliência/failover. |
| **07** (CESGRANRIO/2023) | **E** | Existe **interoperabilidade total** entre Java e Kotlin (módulos mistos). |
| **08** (ADM&TEC/2024) | **C** | Plataforma cruzada **reduz** tempo e custo (Afirmativa I é Falsa). |