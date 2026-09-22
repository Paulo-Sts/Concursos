# Desenvolvimento Mobile

## 1. Sistemas Operacionais Móveis

### 1.1 Principais Plataformas
- Android: Desenvolvido pela Google. É um sistema Open Source, permitindo acesso ao código-fonte para customizações por diversos fabricantes.
- iOS: Desenvolvido pela Apple. É um sistema exclusivo (não Open Source), utilizado apenas em dispositivos fabricados pela própria empresa (iPhone, iPad).

### 1.2 Tipos de Aplicativos (Formas de Desenvolvimento)

| CARACTERÍSTICA | APLICATIVO NATIVO | APLICATIVO MULTIPLATAFORMA (HÍBRIDO/CRUZADO) |
|---|---|---|
| Linguagens/Base | Android: Java, Kotlin. iOS: Objective-C, Swift. | Um código base adaptado para diferentes SOs. Ex: HTML, CSS, JS (Ionic) ou Dart (Flutter). |
| Compilação/Acesso | Acesso direto a bibliotecas e APIs do sistema. Performance otimizada. | Roda em WebView (navegador embutido) ou é compilado para código nativo. |
| Vantagens | Alto desempenho, acesso total a recursos do hardware (GPS, Câmera), UI nativa. | Menor custo e tempo de desenvolvimento, reutilização de código. |
| Desvantagens | Maior custo (equipes diferentes para cada SO). | Desempenho pode ser inferior ao nativo, dependendo da ponte de comunicação com o hardware. |

#### 1.2.1 Frameworks Multiplataforma
- Principais estruturas de plataforma cruzada:
  - React Native (Facebook/Meta);
  - Flutter (Google);
  - Xamarin (Microsoft);
  - Ionic (utiliza WebView: HTML, CSS, JS).
- Observação da banca: O uso de plataforma cruzada reduz (e não aumenta) o custo e o tempo final do projeto.

> [!CAUTION] OBSERVAÇÃO: 
> - Plataforma cruzada reduz custo e tempo de desenvolvimento, não aumenta.

## 2. Comportamentos e Funcionalidades Comuns em Apps

### 2.1 Design e Usabilidade
- Responsividade: O design deve se adaptar a diferentes resoluções de tela (celular, tablet, TV), sem distorcer ou cortar o conteúdo.
- Intuitividade: A interface deve ser fácil de usar, com recursos interativos que guiam o cliente.
- Tecnologias de suporte: Frameworks de frontend (ex: Bootstrap) ainda são amplamente utilizados para garantir acessibilidade responsiva, não caindo em desuso.

> [!CAUTION] OBSERVAÇÃO: 
> - Frameworks de responsividade como Bootstrap não caíram em desuso, conforme CESPE/2019.

### 2.2 Performance e Segurança
- Desempenho: As aplicações devem se preocupar com o tempo de carregamento de telas, otimização de serviços e consumo de bateria.
- Segurança: É crucial devido à vulnerabilidade a ataques. Envolve práticas como a criptografia de dados (ex: mensagens do WhatsApp, transações bancárias).

### 2.3 Conectividade e Armazenamento
- Sincronização online/offline: Permite acesso a conteúdos sem consumir dados móveis, mediante download prévio.
- Recuperação de falhas (failover): Capacidade do app de se recuperar e continuar funcionando mesmo quando o hardware ou software apresentam falhas.

### 2.4 Testes de Configuração
- Definição: Testes que verificam o comportamento do aplicativo em diferentes versões de hardware e software (diferentes modelos de aparelho, versões de SO).
- Erro comum: Não se referem à verificação de tempos de resposta ou recuperação de falhas (isso é teste de performance/resiliência).

> [!CAUTION] OBSERVAÇÃO: 
> - Testes de configuração = hardware/software diferentes. Testes de recuperação = resiliência/failover.