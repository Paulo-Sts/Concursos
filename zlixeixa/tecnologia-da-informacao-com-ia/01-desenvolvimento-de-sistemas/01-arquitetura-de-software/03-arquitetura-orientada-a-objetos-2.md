# Arquitetura Orientada a Objetos 2

## 1. Polimorfismo
- Capacidade de um método ou entidade assumir muitas formas, onde diferentes classes são tratadas como instâncias de uma única classe base por meio de uma base comum.
- Existem três tipos fundamentais de polimorfismo utilizados no desenvolvimento orientado a objetos: de inclusão, paramétrico e por sobrecarga.

### 1.1 Polimorfismo de Inclusão
- Também chamado de subtipagem, é o tipo mais comum onde a subclasse sobrescreve um método da sua classe base.
- O objeto da subclasse é tratado como um objeto da classe base durante a execução.
- Exemplo: uma classe cão estendida de animal que sobrescreve o método emitirSom para imprimir latido em vez do som genérico da classe pai.

### 1.2 Polimorfismo Paramétrico
- Define funções ou tipos de dados de forma genérica, permitindo que operem com qualquer tipo de dado.
- Exemplo: uma função genérica de impressão que aceita um valor de qualquer tipo t.

### 1.3 Polimorfismo de Sobrecarga
- Conhecido como ad-hoc, ocorre quando várias funções possuem o mesmo nome, mas apresentam assinaturas diferentes, seja pelo tipo ou pelo número de parâmetros.
- Exemplo: a existência de duas funções somar, onde uma recebe parâmetros inteiros e a outra recebe parâmetros reais.

> [!TIP] DICAS: 
> - Lembre-se que na sobrecarga o que diferencia as funções é a assinatura (parâmetros), e não apenas o nome do método.

## 2. Princípios de Projeto
- Diretrizes que auxiliam desenvolvedores na criação de sistemas fáceis de manter, entender e expandir.
- Existem princípios gerais aplicáveis a qualquer arquitetura e princípios específicos para orientação a objetos.

### 2.1 Princípios Gerais
- DRY (Don’t Repeat Yourself) ⟶ orientação para não escrever mais de uma vez no código algo que poderia ser replicado ou herdado;
- YAGNI (You Ain’t Gonna Need It) ⟶ princípio de não adicionar elementos ou funcionalidades ao projeto que não sejam necessários no momento;
- KISS (Keep It Simple, Stupid) ⟶ diretriz para manter o sistema da forma mais simples possível.

> [!CAUTION] OBSERVAÇÃO: 
> - A decomposição de um sistema em objetos é diretamente influenciada por fatores como encapsulamento, granularidade e desempenho.

## 3. Princípios Solid
- Acrônimo que representa cinco princípios fundamentais para o design de software orientado a objetos.
- Single Responsibility Principle ⟶ uma classe deve possuir apenas uma única responsabilidade para garantir a modularidade;
- Open/Closed Principle ⟶ as entidades de software devem estar abertas para extensão, mas fechadas para modificação;
- Liskov Substitution Principle ⟶ objetos de um programa devem poder ser substituídos por instâncias de seus subtipos sem alterar a correção do sistema;
- Interface Segregation Principle ⟶ a utilização de muitas interfaces específicas é preferível ao uso de uma interface única e genérica;
- Dependency Inversion Principle ⟶ orientação para que o desenvolvedor dependa de abstrações e não de implementações concretas.

> [!CAUTION] OBSERVAÇÃO: 
> - No princípio de segregação de interface, o objetivo é evitar que a alteração em uma parte do código impacte diversas outras partes desnecessariamente.

## 4. Padrões de Projeto Comportamentais
- Categoria de padrões que lidam com a comunicação eficaz e a distribuição de responsabilidades entre os objetos do sistema.
- Observer ⟶ sistema de inscrição onde objetos reagem a eventos em outros objetos, como notificações em aplicativos;
- Strategy ⟶ permite a configuração de diferentes algoritmos intercambiáveis em um objeto, como diferentes cálculos de rotas;
- Command ⟶ transforma solicitações em objetos autônomos para permitir operações de enfileiramento e desfazer;
- State ⟶ permite que um objeto altere seu comportamento conforme seu estado interno muda, como em um gerenciador de downloads;
- Iterator ⟶ possibilita percorrer elementos de uma coleção (listas, pilhas, árvores) sem expor sua representação interna;
- Memento ⟶ permite salvar e restaurar o estado de um objeto em um momento posterior, como a função desfazer em editores.

## 5. Padrões Grasp
- General Responsibility Assignment Software Patterns ⟶ conjunto de princípios para atribuição de responsabilidades em modelos de software.
- Especialista em Informação ⟶ atribui responsabilidade à classe que possui as informações necessárias para realizar a tarefa;
- Criador ⟶ define que a classe que contém ou usa outra frequentemente deve ser responsável por criar suas instâncias;
- Controlador ⟶ centraliza o processamento de solicitações em uma classe que representa um caso de uso específico;
- Baixo Acoplamento ⟶ promove a independência entre as classes para aumentar a reutilização e flexibilidade;
- Alta Coesão ⟶ foca no design de classes com responsabilidades bem definidas e limitadas.

> [!CAUTION] OBSERVAÇÃO: 
> - Cuidado com pegadinhas de prova: os padrões grasp buscam sempre o baixo acoplamento e a alta coesão, e não o contrário.

## 6. Linguagem de Modelagem Unificada
- Conhecida como UML, é um modelo padronizado para descrever graficamente a estrutura e os comportamentos de sistemas orientados a objetos.
- Proporciona uma representação visual que facilita o entendimento da arquitetura de software.

### 6.1 Principais Diagramas UML
- Diagrama de Classes ⟶ demonstra a estrutura das classes, seus atributos, métodos e relações;
- Diagrama de Casos de Uso ⟶ descreve as funcionalidades do sistema e como elas interagem com os usuários;
- Diagrama de Sequência ⟶ representa a interação entre objetos durante a execução de um cenário específico ao longo do tempo;
- Diagrama de Atividades ⟶ ilustra o fluxo de operações e atividades dentro do sistema.

### Estrutura de Classe UML
| COMPONENTE | DEFINIÇÃO | EXEMPLO |
|---|---|---|
| Nome da classe | Identificador da entidade | Carro |
| Atributos | Características ou dados | Placa, numchassi |
| Métodos | Ações ou comportamentos | Acelerar(), frear() |

> [!TIP] DICAS: 
> - O diagrama de sequência é o mais indicado quando a questão de prova foca na interação entre objetos durante a execução de um cenário específico.