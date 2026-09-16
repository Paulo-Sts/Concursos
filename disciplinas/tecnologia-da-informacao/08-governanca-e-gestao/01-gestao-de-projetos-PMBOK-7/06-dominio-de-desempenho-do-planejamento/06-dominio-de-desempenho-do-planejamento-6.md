# PMBOK 7ª Edição: Domínio de Desempenho do Planejamento 6

## 1. Análise de Pontos de Função
- A análise de pontos de função (FPA) é uma técnica de estimativa baseada na contagem de funções de dados e funções de transação.
- Funções de dados:
  - Arquivo lógico interno (ALI);
  - Arquivo de interface externa (AIE).
- Funções de transação:
  - Entrada externa (EE);
  - Saída externa (SE);
  - Consulta externa (CE).
- A estimativa é realizada sob a perspectiva do usuário e possui caráter independente da tecnologia ou linguagem de programação utilizada.
- O tamanho funcional é medido com base nos requisitos lógicos do usuário, podendo ser estimado antes da existência do sistema ou contado após a implementação.

> [!TIP] DICAS: 
> - A técnica mede o que o usuário percebe como funcionalidade, não importando se o código é escrito em Java, Python ou outra linguagem.

## 2. Metodologias PERT e CPM
- Program Evaluation Review Technique (PERT) ⟶ Método probabilístico de estimativa que utiliza a média ponderada de três cenários: otimista, pessimista e mais provável.
- Critical Path Method (CPM) ⟶ Abordagem determinística que identifica as atividades que não podem sofrer atrasos sem comprometer o prazo final do projeto.
- O cálculo do tempo estimado no PERT segue a fórmula: (Otimista + 4 x Mais Provável + Pessimista) / 6.

> [!CAUTION] OBSERVAÇÃO: 
> - A principal diferença entre os métodos reside no caráter probabilístico do PERT em oposição ao caráter determinístico do CPM.
> - O PERT é focado na gestão de riscos e incertezas do cronograma.

## 3. Artefatos de Planejamento
- Representam documentos, modelos ou saídas utilizadas para organizar o trabalho do projeto.
- Estratégia: inclui Business case, termo de abertura do projeto (TAP), declaração de visão e roadmap.
- Planos: englobam os planos de gerenciamento de custos, riscos, comunicações, escopo, cronograma e qualidade.
- Gráficos de hierarquia: estrutura analítica do projeto (EAP), organizacional, de recursos e de produto.
- Linhas de base: orçamento, cronograma do projeto e linha de base do escopo.
- Informações visuais: gráficos de burndown, fluxogramas, gráfico de Gantt e diagrama de rede.

## 4. Termo de Abertura do Projeto
- Documento que autoriza formalmente a existência do projeto e concede autoridade ao gerente para aplicar recursos organizacionais.
- É publicado pelo iniciador ou patrocinador do projeto.
- Estabelece um vínculo direto entre o projeto e os objetivos estratégicos da organização.
- Conteúdos típicos: finalidade, objetivos mensuráveis, requisitos de alto nível, riscos identificados, marcos do cronograma e recursos financeiros pré-aprovados.

> [!CAUTION] OBSERVAÇÃO: 
> - O termo de abertura não apresenta detalhamento dos produtos entregáveis; detalhes como a EAP pertencem à fase de planejamento detalhado.
> - A aprovação deste documento é uma atividade do grupo de processos de iniciação.

## 5. Business Case e Justificativa
- Documento de viabilidade econômica usado para validar os benefícios de um componente do projeto.
- Serve como insumo fundamental para a criação do termo de abertura do projeto.
- Deve conter a descrição do problema a ser resolvido, a necessidade e a estratégia do negócio.

### Tabela de Técnicas de Estimativa
| TÉCNICA | BASE DE CÁLCULO | NÍVEL DE EXATIDÃO |
|---|---|---|
| Análoga | Projetos anteriores semelhantes | Baixa exatidão e pouco detalhamento |
| Paramétrica | Relações estatísticas e dados históricos | Alta exatidão se os parâmetros forem precisos |
| Bottom-up | Agregação de custos de pacotes de trabalho | Elevada exatidão com alto nível de detalhe |
| Delphi | Consenso entre especialistas | Baseada na experiência coletiva da equipe |

## 6. Estimativas Complementares
- Estimativa análoga ⟶ Utiliza um parâmetro de referência de projetos passados para estimar rapidamente custos ou durações, sendo ideal quando há pouca informação disponível.
- Estimativa paramétrica ⟶ Utiliza cálculos estatísticos baseados em variáveis, como custo por metro quadrado.
- A exatidão das estimativas aumenta conforme o projeto avança e o detalhamento do escopo é refinado.

> [!TIP] DICAS: 
> - Em projetos inovadores sem precedentes comparáveis, a técnica de estimativa análoga não pode ser aplicada por falta de referência.
> - O desenvolvimento de um cronograma realista é essencial para o sucesso da administração de premissas e restrições pelo gerente.