# Engenharia de Software - Conceitos Gerais

## 1. Definição de Software
- Software é composto por instruções (programas), estrutura de dados e documentação.
- A documentação amplia o escopo do software para além do código-fonte, sendo essencial para o entendimento e manutenção do sistema.
- Exemplo: manuais do usuário, especificações de requisitos e guias de instalação são partes da documentação que compõem o software.

## 2. Origem e Evolução da Engenharia de Software
- A engenharia de software surgiu na década de 1970 em resposta à crise do software.
- A crise foi causada pelo descompasso entre a rápida evolução do hardware e o desenvolvimento de software amador, que carecia de processos estruturados e disciplinados.
- A necessidade de uma abordagem mais profissional levou à adoção de práticas organizadas, afastando-se do desenvolvimento solitário e sem métodos.
- Inicialmente, adotou-se uma abordagem linear, semelhante a uma linha de produção, mas esta se mostrou limitada e foi substituída por abordagens mais adaptáveis aos variados cenários de desenvolvimento.

### 2.1 Problemas Recorrentes da Crise do Software
- Estouros de orçamento;
- Descumprimento de prazos;
- Software que não atende aos requisitos do cliente;
- Código de difícil manutenção.
- A falta de aplicação dos princípios da engenharia de software é vista atualmente como a principal causa desses problemas em projetos de TI.

> [!TIP] DICAS:
> - A crise do software não foi um evento único, mas um período de reconhecimento da necessidade de profissionalização da área.
> - A abordagem linear foi abandonada por ser rígida e não conseguir lidar com as mudanças, um ponto chave para entender a evolução para métodos ágeis.

## 3. Abordagem Disciplinada e Integrada
- A engenharia de software adota uma abordagem disciplinada e integrada para evitar a dependência de um único programador e garantir a qualidade do produto.
- A ênfase na qualidade requer a implementação de três elementos chave:
  - Processos;
  - Métodos;
  - Ferramentas.

### 3.1 Camadas da Engenharia de Software (Pressman)
- A organização das camadas, segundo Pressman, segue uma hierarquia onde as ferramentas ocupam a camada superior, apoiando-se em métodos e processos.
- A prioridade é aprimorar a forma de trabalho (processo) antes de automatizar com ferramentas.

#### 3.1.1 Foco nas Ferramentas
- Ferramentas não devem ser a primeira camada, pois, se o processo for inadequado, elas apenas automatizarão as deficiências existentes.
- É um equívoco comum em TI priorizar ferramentas sem ter processos estruturados, resultando na automação de ambientes caóticos.
- A adoção correta ocorre após a implementação de processos e métodos, incluindo os ágeis.
- O avanço tecnológico simplificou tarefas complexas, como a análise estática de código, mas a não aplicação dos princípios da engenharia de software reflete uma abordagem obsoleta.

> [!CAUTION] OBSERVAÇÃO:
> - A ordem de implementação é crucial: primeiro o processo, depois os métodos e, por fim, as ferramentas. Inverter essa ordem é uma falha comum e um ponto frequentemente explorado em provas.

## 4. Processo de Software
- O processo de software é a metodologia que define as atividades, ações e tarefas necessárias para desenvolver um software de alta qualidade.
- Pressman define o processo de software como a metodologia para as atividades de desenvolvimento.
- Sommerville descreve o processo de software como um conjunto de atividades relacionadas que resultam na produção de um produto de software.

### 4.1 Características do Processo
- Os processos devem ser adaptáveis e não excessivamente rígidos para se adequar às dinâmicas do desenvolvimento de software.
- A flexibilidade e a agilidade são necessárias devido à alta probabilidade de mudanças nos requisitos, diferentemente de áreas como a engenharia civil.
- Não há um processo universalmente ideal; a adaptação ao contexto (produto, equipe, recursos) é não apenas possível, mas necessária.
- A flexibilidade pode variar entre uma abordagem mais formal ("dirigido a planos") e outra mais flexível.

> [!TIP] DICAS:
> - A diferença entre a abordagem "dirigida a planos" (mais prescritiva) e a adaptável é um tema central para entender os modelos de processo.
> - Lembre-se: o processo é adaptável, mas as atividades fundamentais de desenvolvimento são constantes.

## 5. Atividades do Processo (Pressman)
- Pressman categoriza as atividades do processo de software em um conjunto de ações principais e de apoio.

### 5.1 Atividades Principais (Pressman)
| ATIVIDADE | DEFINIÇÃO |
|---|---|
| Comunicação | Entender os objetivos dos envolvidos no projeto e reunir requisitos para definir recursos e funções do software. |
| Planejamento | Criar um "mapa" (plano de projeto) descrevendo tarefas técnicas, riscos, recursos, produtos e um cronograma de trabalho. |
| Modelagem | Criar modelos (esboços) para entender melhor as necessidades do software e do projeto, permitindo uma visão do todo. |
| Construção | Combina a geração de código (manual ou automatizada) e a realização de testes para revelar erros na codificação. |
| Entrega | Envolve a entrega do software ao cliente e a subsequente avaliação por ele. |

### 5.2 Atividades de Apoio (Pressman)
- As atividades de apoio são transversais a todo o processo e garantem a qualidade e o gerenciamento do projeto.

| ATIVIDADE | DEFINIÇÃO |
|---|---|
| Controle e acompanhamento do projeto | Avaliar o progresso em relação ao plano e tomar medidas para cumprir o cronograma. |
| Administração de riscos | Avaliar riscos que possam afetar o resultado ou a qualidade do produto/projeto. |
| Garantia da qualidade | Definir e conduzir atividades que garantam a qualidade do software. |
| Revisões técnicas | Avaliar artefatos da engenharia de software para identificar e eliminar erros precocemente. |
| Medição | Definir e coletar medidas do processo, do projeto e do produto. |
| Gerenciamento da configuração de software | Gerir os efeitos das mudanças ao longo do processo. |
| Gerenciamento da capacidade de reutilização | Definir critérios e mecanismos para a reutilização de componentes de software. |
| Preparo e produção de artefatos de software | Atividades para criar artefatos como modelos, documentos, logos, formulários e listas. |

### 5.3 Detalhamento de Atividades de Apoio
- Controle e acompanhamento do projeto: essencial para qualquer processo, envolve avaliação contínua do progresso e cumprimento do cronograma, com elementos do gerenciamento de projetos (ex: PMBOK).
- Administração de riscos: análise recorrente durante o desenvolvimento, estruturada por normas como a ISO 27005 (segurança da informação) e ISO 31000 (riscos em geral).
- Garantia da qualidade e revisões técnicas: serão detalhadas em aulas específicas sobre qualidade de software.
- Medição: área de estudo que envolve a coleta e análise de métricas do processo, projeto e produto.
- Gerenciamento da configuração de software: foca no controle de versões e na gestão de mudanças, sendo amplamente utilizado na fase de construção.

> [!CAUTION] OBSERVAÇÃO:
> - A atividade de "Controle e acompanhamento do projeto" e "Administração de riscos" são fortemente influenciadas por práticas de gerenciamento de projetos e normas ISO, o que é um ponto de atenção para concursos que cobram conhecimentos interdisciplinares.

## 6. Atividades Fundamentais (Sommerville)
- Sommerville define quatro atividades fundamentais que são essenciais para o desenvolvimento de software.

| ATIVIDADE | DEFINIÇÃO |
|---|---|
| Especificação de software | Definir a funcionalidade do software e as restrições a seu funcionamento. |
| Projeto e implementação de software | Produzir o software para atender às especificações definidas. |
| Validação de software | Validar o software para garantir que atenda às demandas do cliente. |
| Evolução de software | Fazer o software evoluir para atender às necessidades de mudança dos clientes. |

- A especificação, projeto, implementação e evolução são atividades constantes, compreendidas por qualquer modelo de processo.
- A variedade de processos existe para atender à diversidade de tipos de software, adaptando-se ao produto em questão.
- A ideia de que um único processo se aplica a todas as situações era um erro comum que foi superado. Atualmente, entende-se que os processos precisam ser adaptados conforme a necessidade.

> [!TIP] DICAS:
> - Compare as atividades de Pressman e Sommerville para entender diferentes visões sobre o mesmo processo. Ambas são cobradas em concursos.
> - A especificação e a validação são atividades que garantem que o software certo está sendo construído e da maneira correta.