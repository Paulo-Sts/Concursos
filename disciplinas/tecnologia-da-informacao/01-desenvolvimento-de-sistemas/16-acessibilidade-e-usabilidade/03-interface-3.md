# Testes com Usuários e Design System

## 1. Testes e Avaliação de Interface
- Testes de interface de usuário (GUI) servem para verificar se a interface gráfica funciona conforme o esperado, analisando layout, design, responsividade e interação de elementos como botões e menus.
- Testes exploratórios são conduzidos para a identificação de problemas gerais no sistema.
- Testes de tarefa avaliam se o usuário é capaz de completar objetivos específicos dentro da aplicação.
- Testes de usabilidade remota possibilitam a realização de avaliações de interface à distância.
- Percurso cognitivo é um método de avaliação que simula o raciocínio do usuário ao navegar pelo sistema, focando na análise de decisões e potenciais dificuldades em cada etapa.
- Avaliação heurística consiste em examinar elementos da interface para determinar a conformidade com princípios de usabilidade reconhecidos, sendo um método de inspeção rápido e de baixo custo.
- Inspeção semiótica visa avaliar a qualidade da usabilidade da interface junto aos seus usuários finais.

> [!TIP] DICAS: 
> - O percurso cognitivo avalia a facilidade de aprendizado através da exploração, sendo ideal para sistemas onde o usuário prefere aprender fazendo.

## 2. Heurísticas de Nielsen
- Visibilidade do status do sistema garante que o usuário esteja sempre informado sobre o que está ocorrendo no sistema.
- Controle e liberdade do usuário permite que ações sejam desfeitas ou refeitas com facilidade pela interface.
- Consistência e padrões asseguram que elementos semelhantes possuam comportamentos consistentes em toda a aplicação.
- Prevenção de erros auxilia o usuário a evitar falhas antes mesmo de cometê-las através do design inteligente da interface.

## 3. Métodos e Técnicas de Interação
- Teste A/B compara versões distintas de uma interface para determinar qual apresenta melhor desempenho, utilizando métricas como taxa de cliques e tempo de permanência.
- Eye tracking analisa o movimento ocular para compreender como os usuários visualizam a interface e se elementos importantes recebem a atenção necessária.
- Teste de GUI automatizado pode simular situações atípicas, como toques acidentais em áreas não interativas, para garantir a robustez da interface.

## 4. Componentes de Interface com Usuário
- Botões são elementos clicáveis utilizados para o início de ações específicas no sistema.
- Caixas de texto representam as áreas destinadas à entrada de informações pelo usuário.
- Menus consistem em listas de opções que possibilitam a navegação entre diferentes partes da aplicação.
- Sliders permitem a seleção manual de valores dentro de um intervalo pré-determinado.
- Toggle button funciona como um botão de comando para ligar e desligar funções específicas.
- CheckBox é o componente indicado para situações que permitem múltiplas seleções simultâneas em uma lista.
- Radio button é utilizado quando o sistema exige uma única seleção entre as opções disponíveis.
- Alertas informam o usuário sobre ocorrências importantes, como mensagens de sucesso ou de erro no processamento.
- Modais são janelas flutuantes que interrompem o fluxo para exigir uma ação imediata antes da continuação do uso.

### 4.1 Exemplos de Dados Tabulares
- Tabelas são utilizadas para a exibição e organização de dados tabulares de forma estruturada.

| LOAN AMOUNT | 5,50% | 5,75% | 6,00% | 6,25% | 6,50% |
|---|---|---|---|---|---|
| 400.000 € | 3.268 € | 3.322 € | 3.375 € | 3.430 € | 3.484 € |
| 425.000 € | 3.473 € | 3.529 € | 3.586 € | 3.644 € | 3.702 € |
| 450.000 € | 3.677 € | 3.737 € | 3.797 € | 3.858 € | 3.920 € |

## 5. Design System
- Um Design System é um conjunto organizado de diretrizes e componentes reutilizáveis que mantém a consistência entre diferentes produtos e plataformas.
- Guia de estilo visual estabelece as definições de cores (primárias, secundárias e estados), tipografia, espaçamentos, grids e iconografia.
- Biblioteca de componentes reúne elementos reutilizáveis como botões, cards e formulários, facilitando a flexibilidade na configuração dos módulos.
- O uso de componentes reutilizáveis torna a aplicação mais coerente e conectada, melhorando o processo de design e desenvolvimento.

> [!CAUTION] OBSERVAÇÃO: 
> - Métodos de inspeção permitem ao avaliador examinar uma solução para antever possíveis consequências de design sem necessariamente envolver usuários reais em testes empíricos imediatos.