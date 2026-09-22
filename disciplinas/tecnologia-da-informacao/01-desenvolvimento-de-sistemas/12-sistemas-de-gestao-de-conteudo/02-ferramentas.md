# Ferramentas de Gestão de Conteúdo

## 1. WordPress
- Sistema de gerenciamento de conteúdo (CMS) gratuito e de código aberto voltado para criação e manutenção de sites e blogs.
- Permite a construção de plataformas de baixa codificação, sendo acessível para usuários sem conhecimento técnico avançado.
- Atributos principais:
- Interface intuitiva;
- Suporte a múltiplos tipos de conteúdo como textos, imagens e vídeos;
- Personalização através de milhares de temas e plugins;
- Otimização nativa para mecanismos de busca (SEO);
- Compatibilidade multiplataforma com diversos dispositivos e navegadores;
- Suporte contínuo via comunidade ativa.

### 1.1 Extensões do WordPress
- Funcionalidades que não pertencem originalmente à plataforma e são adicionadas para estender seu funcionamento.
- Plugins ⟶ adicionam funções específicas como formulários, segurança e e-commerce;
- Temas ⟶ definem o layout e design visual, podendo ser personalizados via CSS e construtores visuais;
- Widgets ⟶ pequenos blocos de conteúdo para áreas específicas como barras laterais ou rodapés, como calendários e caixas de busca.

### 1.2 Principais Plugins do WordPress
- Yoast SEO ⟶ focado na otimização para buscadores, analisa legibilidade, palavras-chave e gera sitemap XML.
- Elementor ⟶ criador visual de páginas com editor do tipo arrastar e soltar (drag-and-drop) que permite personalização sem uso de código.
- Wordfence Security ⟶ proteção contra ataques através de firewall de aplicação web (WAF), scanner de malware e bloqueio de IPs.

> [!CAUTION] OBSERVAÇÃO: 
> - No desenvolvimento de temas personalizados, recomenda-se usar um tema-pai e criar um tema-filho para as customizações.
> - Os temas-filhos são ideais porque mantêm as referências de segurança e design do tema original enquanto permitem modificações específicas.

## 2. Drupal
- CMS gratuito e de código aberto reconhecido por sua flexibilidade, segurança avançada e escalabilidade.
- Amplamente utilizado por governos e grandes instituições devido ao rigor na proteção de dados.
- Características técnicas:
- Estrutura modular para criação de soluções complexas sob medida;
- Controle refinado de permissões e perfis de acesso;
- Suporte nativo robusto para sites em vários idiomas.

## 3. Joomla
- CMS de código aberto que equilibra facilidade de uso com recursos avançados, muito utilizado em portais do governo federal.
- Estrutura de extensões:
- Componentes ⟶ extensões complexas que funcionam como miniaplicações, como o gerenciador de artigos;
- Módulos ⟶ extensões leves para exibição de conteúdo em áreas específicas da página;
- Plugins ⟶ executam ações em segundo plano ou modificam comportamentos do sistema;
- Templates ⟶ controlam o layout visual do site;
- Linguagens ⟶ permitem a tradução do núcleo do sistema e das extensões.

### 3.1 Layouts Alternativos no Joomla
- Conjunto de ferramentas que oferece maior controle sobre a saída HTML do template.
- Categorias de layouts alternativos oficiais:
  - Módulo;
  - Componente;
  - Categoria;
  - Item de menu;
  - Jlayouts.

> [!TIP] DICAS: 
> - Joomla e Drupal são as ferramentas recomendadas quando a necessidade é exclusivamente voltada para a gestão de conteúdo empresarial.
> - O artigo não é considerado um tipo de layout alternativo no sistema Joomla.

### Comparativo de Ferramentas CMS
| FERRAMENTA | FOCO PRINCIPAL | CARACTERÍSTICA DESTAQUE |
|---|---|---|
| Wordpress | Blogs e sites rápidos | Interface intuitiva e plugins |
| Drupal | Complexidade e segurança | Estrutura modular e escalável |
| Joomla | Portais governamentais | Equilíbrio entre uso e recursos |