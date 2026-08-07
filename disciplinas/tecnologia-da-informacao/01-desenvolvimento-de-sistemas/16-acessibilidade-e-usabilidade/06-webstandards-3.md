# Webstandards e Acessibilidade Digital 3

## 1. Conceitos de Acessibilidade Digital
- A acessibilidade digital, segundo a Web Accessibility Initiative (WAI) do W3C, garante que os usuários consigam perceber, compreender, navegar, interagir e contribuir para a web.
- Trata-se de uma característica intrínseca de uma rede bem construída e não de um recurso opcional.
- Os requisitos dividem-se entre aspectos técnicos de código e características de design visual e de interação.
- A estruturação de um ecossistema digital para todos os usuários requer a integração de três conceitos fundamentais: acessibilidade, usabilidade e inclusão.
- A acessibilidade foca na promoção de experiência de uso equivalente para pessoas com deficiência, abordando requisitos de código e interação.
- A usabilidade refere-se à eficácia, eficiência e satisfação com que usuários atingem objetivos em contextos específicos de uso.
- A inclusão expande o escopo para a diversidade humana total, englobando idade, cultura, idioma, localização e situação socioeconômica.

> [!CAUTION] OBSERVAÇÃO: 
> - A usabilidade é visada tanto quanto a acessibilidade para que o usuário finalize o objetivo da página e não apenas entenda o seu conteúdo.

## 2. Tríade de Padrões de Acessibilidade do W3C
- A arquitetura de acessibilidade fundamenta-se na inter-relação de três componentes técnicos essenciais, cada um governado por uma diretriz específica.

| PADRÃO DE ACESSIBILIDADE | ESCOPO DE ATUAÇÃO E COMPONENTES GOVERNADOS | PRINCIPAIS DESTINATÁRIOS DAS DIRETRIZES |
|---|---|---|
| Web content accessibility guidelines (wcag) | Define requisitos para qualquer parte de um website, incluindo texto, imagens, formulários e scripts | Desenvolvedores web, web designers, autores de conteúdo e avaliadores |
| Authoring tool accessibility guidelines (atag) | Regula softwares e serviços utilizados para produzir conteúdo web | Desenvolvedores de sistemas de gerenciamento de conteúdo (cms) e plataformas sociais |
| User agent accessibility guidelines (uaag) | Explica como tornar os agentes de usuário acessíveis a pessoas com deficiência | Desenvolvedores de navegadores, reprodutores de mídia e leitores eletrônicos |

> [!TIP] DICAS: 
> - O Pulo do Gato: Conceitualmente, o WCAG é o tópico mais cobrado em provas dentro da tríade de padrões de acessibilidade.

## 3. Princípios e Diretrizes do WCAG 2.2
- O WCAG estrutura-se em quatro princípios basilares que podem ser memorizados pelo mnemônico PORC.

### 3.1 Princípio Percebível
- A informação e os componentes da interface devem ser apresentáveis aos usuários de formas que eles possam perceber.
- Alternativas em texto: prover textos para qualquer conteúdo não textual para conversão em caracteres ampliados, braile ou fala.
- Mídias baseadas em tempo: fornecer legendas sincronizadas, audiodescrição ou transcrições para áudio e vídeo.
- Adaptável: criar conteúdo apresentável de diferentes formas sem perda de informação ou estrutura.
- Distinguível: facilitar a visualização e audição do conteúdo, separando claramente o primeiro plano do plano de fundo.

### 3.2 Princípio Operável
- Os componentes da interface e a navegação devem ser operáveis por diferentes meios.
- Acessibilidade por teclado: tornar todas as funcionalidades operáveis por meio de um teclado ou emuladores.
- Tempo suficiente: oferecer aos usuários tempo adequado para ler e interagir com o conteúdo.
- Convulsões e reações físicas: evitar designs que possam desencadear crises convulsivas ou reações adversas.
- Navegável: fornecer caminhos e orientações claras para ajudar usuários a localizar informações.

### 3.3 Princípio Compreensível
- A informação e a operação da interface devem ser inteligíveis.
- Legível: assegurar que os textos sejam de fácil compreensão idiomática e cognitiva.
- Previsível: desenhar páginas para que apareçam e operem de maneira uniforme.
- Assistência na entrada: ajudar usuários a evitar e corrigir erros em formulários.

### 3.4 Princípio Robusto
- O conteúdo deve ser interpretado de forma confiável por uma ampla variedade de agentes de usuário e tecnologias assistivas.
- Compatibilidade: maximizar a compatibilidade com agentes de usuário atuais e futuros.

> [!CAUTION] OBSERVAÇÃO: 
> - Em relação à diretriz de mídias baseadas em tempo, o objetivo é transmitir a imersão completa do conteúdo, incluindo a adaptação de todos os aspectos.

## 4. Novos Critérios de Sucesso do WCAG 2.2
- A publicação oficial de outubro de 2023 inseriu nove novos critérios voltados a usuários com baixa visão, deficiências cognitivas e limitações de mobilidade.
- Focus Not Obscured (Minimum): o componente focado pelo teclado não pode ficar inteiramente oculto por conteúdos como cabeçalhos fixos ou pop-ups.
- Focus Not Obscured (Enhanced): proibição categórica de que qualquer parte do componente focado seja obscurecida por conteúdo do desenvolvedor.
- Focus Appearance: estabelece regras de tamanho e contraste para o indicador de foco, exigindo contraste de pelo menos 3:1 entre o estado focado e de repouso.
- Dragging Movements: operações de arrastar devem possuir alternativa de clique ou toque único para usuários com tremores ou rastreadores oculares.
- Target Size (Minimum): exige tamanho mínimo para alvos interativos para prevenir erros de toque acidentais.
- Redundant Entry: impede que dados já fornecidos sejam reinseridos no mesmo fluxo, demandando soluções de autopreenchimento.
- Accessible Authentication: restringe o uso de testes cognitivos complexos em logins, como cálculos ou memorização de credenciais.

## 5. Implementação Técnica e Boas Práticas
- A implementação exige o uso de linguagens de marcação de forma semântica e estruturada.
- O HTML5 deve ser utilizado com tags estruturais como <header>, <main>, <nav> e <aside> para definir a anatomia da página.
- Emprego de papéis ARIA como role=“search” e estados dinâmicos como aria-expanded para comunicar a mutabilidade da interface a leitores de tela.
- Formulários devem possuir vinculação programática entre elementos de entrada e rótulos visuais através dos atributos for e id.
- O idioma primário deve ser explicitado no elemento raiz via propriedade <html lang=“pt-BR”>.
- O código deve ser tolerante a falhas cognitivas e processar entradas de forma permissiva, como aceitar números de telefone com espaços ou hífens.
- Documentos extensos devem ser organizados com cabeçalhos hierárquicos e links semanticamente descritivos.

## 6. Matriz de Técnicas para Conteúdos não Textuais
- O W3C estabelece técnicas específicas para diferentes naturezas de conteúdo para garantir a acessibilidade.

| NATUREZA DO CONTEÚDO NÃO TEXTUAL | SITUAÇÃO TÉCNICA GOVERNAMENTAL | TÉCNICA SUFICIENTE RECOMENDADA PELO W3C |
|---|---|---|
| Imagem informativa | Descrição curta é suficiente para a finalidade | Uso de texto alternativo curto que resuma o propósito exato |
| Imagem de verificação (captcha) | Elemento é um teste de turing visual para segurança | Texto descritivo do propósito com método alternativo por outra modalidade sensorial |
| Imagem decorativa | Elemento não agrega informação | Ocultação visual programática via css ou uso de atributo alt nulo |
| Vídeo sem áudio gravado | Conteúdo exclusivamente visual baseado em tempo | Fornecimento de faixa de descrição de áudio ou transcrição completa |
| Filme gravado | Fornecimento de faixa de descrição de áudio | Incorporação de narração descritiva na trilha sonora nativa |

## 7. Design Visual e Interface
- A acessibilidade deve ser integrada como um requisito de projeto de experiência.
- Contraste de luminância: o texto em primeiro plano deve possuir contraste suficiente com o plano de fundo imediato.
- Proibição do uso exclusivo de cor: canais de cor não devem ser a única forma de codificar dados ou diferenciar elementos.
- Rotulação textual clara: elementos coloridos devem vir acompanhados de rótulos, padrões texturais ou simbólicos.
- Navegação estrutural: o layout deve oferecer múltiplas formas de navegação, como mecanismos de busca e mapas lógicos do site.
- Uniformidade espacial: manter o posicionamento uniforme de cabeçalhos e menus favorece a memorização espacial.