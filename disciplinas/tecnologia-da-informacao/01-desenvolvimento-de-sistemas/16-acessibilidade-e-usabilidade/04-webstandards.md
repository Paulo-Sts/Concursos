# Webstandards e o Consórcio W3C

## 1. Introdução ao W3C
- O World Wide Web Consortium (W3C) foi fundado em 1994 por Sir Tim Berners-Lee, o inventor da Web.
- A missão central da organização é levar a Web ao seu potencial máximo através do desenvolvimento de protocolos e diretrizes que garantam o crescimento da plataforma a longo prazo.
- Em janeiro de 2023, o W3C tornou-se uma organização sem fins lucrativos de interesse público independente.
- A comunidade é formada por um fórum aberto onde colaboram mais de 330 organizações membros, uma equipe técnica em tempo integral e o público em geral.
- A liderança atual da organização é exercida pelo Presidente e CEO Seth Dobbs.

> [!CAUTION] OBSERVAÇÃO: 
> - O conteúdo sobre a fundação e natureza jurídica é considerado introdutório e pouco cobrado em provas, mas essencial para entender o propósito da organização.

## 2. Padronização e Propósito
- A função primordial do W3C é promover a padronização das tecnologias da rede.
- O consórcio busca evitar que navegadores e desenvolvedores adotem linguagens e estruturas próprias sem um padrão comum, o que geraria desorganização tecnológica.
- Sem a padronização, desenvolvedores precisariam criar versões específicas de uma mesma aplicação para cada navegador diferente.
- A proposta é definir padrões compartilhados para construir uma World Wide Web mais robusta, organizada e interoperável.

## 3. Tecnologias e Padrões Fundamentais
- XML e JSON: são os principais formatos para tráfego de dados estruturados entre aplicações, sendo independentes da linguagem de programação utilizada.
- XHTML (Extensible Hypertext Markup Language): linguagem de marcação que reformula o HTML 4.01 sob as regras mais rigorosas do XML.
- DOM (Document Object Model): padrão que define a interface para a estrutura de documentos, permitindo que scripts acessem e atualizem dinamicamente o conteúdo e o estilo.
- CSS (Cascading Style Sheets): pilar responsável pelo design visual, layout e toda a aparência estética da aplicação web.
- JavaScript: linguagem de programação voltada ao lado do cliente que confere dinamismo e interação à aplicação.
- SVG (Scalable Vector Graphics): formato padrão para descrever gráficos vetoriais bidimensionais que podem ser redimensionados sem perda de qualidade.

> [!TIP] DICAS: 
> - Decore a separação de responsabilidades: HTML ⟶ Semântica e Estrutura; CSS ⟶ Aparência e Layout; JavaScript ⟶ Dinamismo e Interação.

## 4. Evolução do HTML e WHATWG
- Em 2004, foi criado o WHATWG (Web Hypertext Application Technology Working Group) por membros da Apple, Mozilla e Opera.
- O grupo surgiu devido à percepção de que o W3C estava excessivamente focado no XHTML e pouco interessado na evolução prática do HTML.
- O WHATWG focou em uma evolução pragmática voltada para compatibilidade real, formulários ricos e multimídia nativa.
- O HTML5 foi publicado como Recomendação W3C em 28 de outubro de 2014, tornando-se o padrão formal recomendado pelo consórcio.
- Atualmente, o WHATWG é o principal responsável pela criação de padrões do HTML, enquanto o W3C atua com orientações e apoio institucional.

## 5. Áreas de Impacto e Recomendações
- Acessibilidade (WAI): através da Web Accessibility Initiative, o consórcio desenvolve as diretrizes WCAG para garantir que a Web seja utilizável por pessoas com deficiências.
- Internacionalização: garante que a rede suporte as diversas línguas e sistemas de escrita globais.
- Segurança e Privacidade: desenvolvimento de tecnologias de autenticação forte e proteção de dados dos usuários.
- Fronteiras Emergentes: liderança na padronização da Web of Things (WoT) e exploração do impacto da Inteligência Artificial na arquitetura da rede.

## 6. Grupos de Trabalho do W3C
- Os Grupos de Trabalho (Working Groups) representam a estrutura onde ocorre o trabalho técnico de padronização.
- Suas principais entregas incluem as Recomendações W3C (padrões oficiais), relatórios técnicos e especificações de APIs.
- Ciclo de vida: os grupos podem estar abertos (em missão ativa) ou fechados (quando concluem seus objetivos ou missões).

### 6.1 Grupos de Tecnologias e Acessibilidade
- HTML Working Group: responsável por transformar especificações de HTML e DOM em recomendações oficiais;
- CSS Working Group: foca no desenvolvimento e manutenção das folhas de estilo;
- Accessibility Guidelines (AG WG): dedicado ao desenvolvimento das especificações WCAG;
- Accessible Platform Architectures (APA WG): revisa especificações de outros grupos para garantir o suporte à acessibilidade.

### 6.2 Grupos de Mídia e Imersão
- Media Working Group: atua na melhoria da reprodução e processamento de mídia no cliente;
- Audio Working Group: adiciona capacidades de síntese de som e música à web;
- Immersive Web Working Group: responsável por levar Realidade Virtual (VR) e Realidade Aumentada (AR) para o navegador.

| TECNOLOGIA | DEFINIÇÃO | EXEMPLO |
|---|---|---|
| Realidade virtual | Criação de um ambiente totalmente virtual imersivo | Uso de óculos específicos que inserem o usuário em um mundo digital |
| Realidade aumentada | Projeção de elementos virtuais no ambiente real | Aplicativos que usam a câmera para projetar animais ou objetos no ambiente real |

> [!CAUTION] OBSERVAÇÃO: 
> - Importante para provas: As recomendações da WCAG não são tratadas como opcionais pelo W3C; o consórcio enfatiza a adoção obrigatória dessas práticas para garantir a inclusão de todos os usuários.
> - Detalhe técnico: No DOM, a estrutura HTML é carregada em uma árvore que permite a scripts navegar, movimentar elementos e alterar estilos em memória.