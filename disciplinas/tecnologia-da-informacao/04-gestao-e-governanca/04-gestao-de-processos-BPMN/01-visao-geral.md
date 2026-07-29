# Visão Geral e Notações de Modelagem de Processos

## 1. Principais Notações de Modelagem de Processos

### 1.1 BPMN (Business Process Model and Notation)
- Padrão criado pela Business Process Management Initiative (BPMI), posteriormente incorporado ao Object Management Group (OMG).
- Padrão aberto e amplamente difundido.
- Conjunto robusto de símbolos para modelagem de diferentes aspectos de processos de negócio.
- Ícones organizados em conjuntos descritivos e analíticos para atender a diferentes necessidades.
- Permite indicação de eventos de início, intermediário e fim.
- Permite fluxo de atividades e mensagens.
- Permite comunicação intranegócio e colaboração internegócio.
- Utiliza raias (piscinas e raias) para dividir o modelo em linhas paralelas, onde cada raia define um papel desempenhado por um ator.
- O trabalho se move de atividade para atividade seguindo o caminho do fluxo.

### 1.2 Fluxograma
- Originalmente aprovado como padrão ANSI (American National Standards Institute).
- Inclui conjunto simples e limitado de símbolos não padronizados.
- Facilita entendimento rápido do fluxo de um processo.

### 1.3 EPC (Event-driven Process Chain)
- Desenvolvido como parte da estrutura de trabalho ARIS pelo Professor Wilhelm-August Scheer da Universidade de Saarland no início de 1990.
- Considera eventos como gatilhos para ou resultados de uma etapa do processo.
- Útil para modelar conjuntos complexos de processos.
- Pode ser usado para modelação, análise e redesenho de processos de negócio.
- Pode ser melhorado através de swim lanes verticais ou horizontais.
- Conjunto central simples de símbolos facilmente reconhecíveis, ampliado com objetos opcionais.
- Algumas ferramentas empregam sistema de filtros para controlar o subconjunto de notação a ser utilizado.

> [!TIP] DICAS:
> - O ARIS implementa o EPC.
> - O EPC trabalha na vertical.

### 1.4 UML (Unified Modeling Language)
- Mantido pelo Object Management Group (OMG).
- Consiste em um conjunto-padrão de notações técnicas de diagramação.
- Orientado à descrição de requisitos de sistemas de informação.

### 1.5 IDEF (Integrated Definition Language)
- Padrão da Federal Information Processing Standard dos EUA.
- Destaca entradas, saídas, mecanismos, controles de processo e relação dos níveis de detalhe do processo superior e inferior.
- Ponto de partida para uma visão corporativa da organização.

### 1.6 Value Stream Mapping
- Do Lean Manufacturing.
- Conjunto intuitivo de símbolos usado para mostrar a eficiência de processos.
- Por meio do mapeamento de uso de recursos e elementos de tempo.

### 1.7 DMN (Decision Model and Notation)
- Notação para modelagem de decisões.
- Complementa o BPMN, não o substitui.

> [!CAUTION] OBSERVAÇÃO:
> - DMN e BPMN convivem em harmonia e se complementam.
> - DMN não substitui BPMN.

## 2. BPMN em Detalhe

### 2.1 Quando Usar BPMN
- Para apresentar um modelo de processos para públicos-alvo diferentes.
- Para simular um processo de negócio com um motor de processo.
  - A simulação permite testar mudanças antes da implantação, evitando ruídos operacionais.
- Para gerar aplicações em BPMS a partir de modelos de processos.

### 2.2 Vantagens do BPMN
- Uso e entendimento difundido em muitas organizações.
- Versatilidade para modelar as diversas situações de um processo.
- Suportado por ferramentas BPMS mais difundidas.

### 2.3 Desvantagens do BPMN
- Exige treinamento e experiência para uso correto do conjunto completo de símbolos.
- Dificulta visualização do relacionamento entre vários níveis de um processo.
- Diferentes ferramentas podem ser necessárias para apoiar diferentes subconjuntos da notação.
- Origem na tecnologia da informação inibe seu uso por pessoal de negócio.

> [!CAUTION] OBSERVAÇÃO:
> - BPMN é um padrão, mas a forma como se utiliza deve ser guiada por padrões corporativos.
> - Padrões corporativos devem reger quando e como as raias são definidas, como as atividades são decompostas e que dados são coletados na modelagem.
> - A visão de longo prazo deve ser a construção de um modelo integrado de negócio da organização.

## 3. Resumo Comparativo das Notações

| NOTAÇÃO              | ORIGEM/CARACTERÍSTICA PRINCIPAL                        | APLICAÇÃO                                                                   |
|----------------------|--------------------------------------------------------|-----------------------------------------------------------------------------|
| BPMN                 | Padrão OMG, criado pela BPMI                           | Modelagem de processos para diferentes públicos, simulação, geração em BPMS |
| Fluxograma           | Padrão ANSI, símbolos simples                          | Entendimento rápido do fluxo                                                |
| EPC                  | ARIS, eventos como gatilhos ou resultados              | Modelagem de conjuntos complexos de processos                               |
| UML                  | Mantido pelo OMG                                       | Descrição de requisitos de sistemas de informação                           |
| IDEF                 | Padrão Federal Information Processing Standard dos EUA | Visão corporativa da organização                                            |
| Value Stream Mapping | Lean Manufacturing                                     | Eficiência de processos, recursos e tempo                                   |
| DMN                  | Modelagem de decisões                                  | Complemento ao BPMN                                                         |

> [!TIP] DICAS:
> - O software Bizagi Modeler utiliza o padrão BPMN.
> - Ferramentas mais atuais utilizam BPMN como padrão.
> - O padrão BPMN é recomendado pela Object Management Group (OMG).

## 4. Elementos do BPMN
- Piscinas e Raias
- Conectores
- Atividades
- Tipos de Tarefas
- Tipos de Subprocesso
- Marcadores de Atividades
- Gateways
- Eventos
- Artefatos