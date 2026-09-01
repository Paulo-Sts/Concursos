# Engenharia de Software - Estágio de Teste 7

## 1. Teste de Integração
- Consiste em uma técnica sistemática para construir a arquitetura de software enquanto se conduzem testes para descobrir erros associados às interfaces dos componentes.
- O objetivo central é construir a estrutura do programa, determinada pelo projeto, a partir de componentes que já foram testados individualmente em unidade.

> [!CAUTION] OBSERVAÇÃO: 
> - A interface referenciada no teste de integração diz respeito à comunicação entre componentes técnicos e não à interface de usuário.

## 2. Abordagem Big Bang
- Caracteriza-se como uma integração não incremental onde todos os componentes são combinados antecipadamente.
- O programa inteiro é testado como um todo de uma única vez.
- Usualmente resulta em dificuldades de isolamento de erros, sendo frequentemente descrita como geradora de caos no processo de teste.

## 3. Integração Incremental
- Representa o oposto da abordagem big bang, onde o programa é construído e testado em pequenos incrementos.
- Permite que os erros sejam mais fáceis de isolar e corrigir durante o desenvolvimento.
- Aumenta a probabilidade de as interfaces serem testadas de forma completa.

### 3.1 Integração Descendente Top-down
- Estratégia em que o projeto de software segue a forma tradicional de desenvolvimento.
- Os componentes interagem a partir do topo da hierarquia para verificar como reagem entre si.
- Permite uma visão do todo do sistema enquanto os testes são realizados.

### 3.2 Integração Ascendente Bottom-up
- Estratégia de integração voltada para processos de desenvolvimento iterativos e ágeis.
- Os componentes são criados e testados individualmente à medida que surgem.
- Foca na construção de partes menores para depois observar o comportamento do sistema como um todo.

## 4. Contexto de Orientação a Objetos
- O teste de classe em software orientado a objetos (OO) é o equivalente ao teste de unidade para o software convencional.
- Diferente do software convencional, o foco não está apenas no detalhe algorítmico, mas nas operações encapsuladas e no estado de comportamento da classe.
- Estratégias tradicionais de hierarquia (top-down e bottom-up) possuem pouco significado em sistemas OO devido à ausência de uma estrutura óbvia de controle hierárquico.

### 4.1 Estratégias de Integração em Orientação a Objetos
- Teste baseado em sequência de execução (thread-based testing): integra o conjunto de classes necessárias para responder a uma entrada ou evento específico do sistema.
- Teste de agregado (cluster testing): etapa que exercita um grupo de classes colaboradoras através de casos de teste projetados para descobrir erros nas colaborações.

## 5. Teste de Regressão
- Realizado sempre que o software é corrigido ou quando ocorre alteração na configuração, documentação ou dados de suporte.
- Garante que as alterações realizadas não introduzam comportamentos indesejados ou novos erros em funcionalidades já existentes.
- Pode ser executado manualmente através de subconjuntos de casos de teste ou por ferramentas automáticas de captura e reexecução.

> [!TIP] DICAS: 
> - Em softwares com longo ciclo de vida, não é viável rodar todos os testes em cada alteração ⟶ é necessário eleger os testes prioritários para a regressão.

## 6. Teste Fumaça
- Abordagem de teste de integração frequente no desenvolvimento de produtos de software.
- Funciona como um mecanismo de marca-passo para projetos com prazos críticos, permitindo avaliações frequentes.
- Caracteriza-se como uma integração rolante, onde o software é recriado com novos componentes e testado diariamente.
- A finalidade principal é descobrir erros bloqueadores (showstoppers) que possuem alta probabilidade de atrasar o cronograma.

## 7. Teste de Validação
- Foca no nível de requisitos e em elementos que são imediatamente aparentes para o usuário final.
- Compreende a realização de testes alfa e beta para validar a entrega.

### 7.1 Revisão de Configuração
- Também chamada de auditoria, tem a finalidade de garantir que todos os elementos da configuração do software foram desenvolvidos e catalogados adequadamente.
- Assegura que existam detalhes necessários para amparar as atividades futuras de suporte ao software.

### Comparativo de Abordagens de Integração
| ABORDAGEM | MÉTODO | VANTAGEM |
|---|---|---|
| Big bang | Não incremental | Simplicidade teórica inicial. |
| Incremental | Pequenos incrementos | Facilidade no isolamento de erros. |
| Fumaça | Integração diária | Identificação rápida de impedimentos. |