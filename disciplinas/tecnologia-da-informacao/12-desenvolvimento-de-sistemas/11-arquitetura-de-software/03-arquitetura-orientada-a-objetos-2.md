# Arquitetura Orientada à Objetos 2

## 1. Polimorfismo

### 1.1 Definição
- Capacidade de um método ou entidade assumir muitas formas.
- Diferentes classes são tratadas como instâncias de uma única classe base, por meio de uma base comum.

### 1.2 Tipos de Polimorfismo

#### 1.2.1 Polimorfismo de Inclusão (Subtipagem)
- É o tipo mais comum.
- A subclasse sobrescreve um método da sua classe base.
- Um objeto da subclasse é tratado como objeto da classe base.
- Exemplo: classe "Animal" com método emitirSom() que imprime "Faz algum som"; classe "Cão" (extende Animal) com método emitirSom() que imprime "Latido".

#### 1.2.2 Polimorfismo Paramétrico
- Define funções ou tipos de dados de forma genérica, operando com qualquer tipo de dado.
- Exemplo: função genérica imprimir<T>(valor: T) que imprime o valor recebido.

#### 1.2.3 Polimorfismo por Sobrecarga (*Ad-Hoc*)
- Várias funções com o mesmo nome, mas diferentes assinaturas (tipo ou número de parâmetros).
- Exemplo: função somar(a: Inteiro, b: Inteiro) e função somar(a: Real, b: Real) - ambas com o mesmo nome, mas com tipos de parâmetros diferentes.

> [!CAUTION] OBSERVAÇÃO: 
> - O polimorfismo de inclusão é o mais comum e o mais cobrado em provas.

## 2. Princípios de Projeto (Design Principles)

### 2.1 Definição
- Princípios de projeto ou princípios de design de software são diretrizes que ajudam desenvolvedores a criar sistemas de software fáceis de manter, entender e expandir.
- São aplicáveis em qualquer tipo de arquitetura de software ou programação.

### 2.2 Princípios Gerais

#### 2.2.1 DRY (*Don't Repeat Yourself*)
- Princípio de não escrever mais de uma vez no código algo que poderia ser replicado.
- Exemplo: em vez de escrever os mesmos métodos da classe Animal para a classe Cachorro, esses métodos seriam simplesmente herdados, e corrigidos simultaneamente.

#### 2.2.2 YAGNI (*You Ain't Gonna Need It*)
- Não adicionar elementos no projeto que não são necessários no momento.

#### 2.2.3 KISS (*Keep It Simple, Stupid*)
- O sistema deve ser mantido da forma mais simples possível.

## 3. Princípios SOLID
- Acrônimo para cinco princípios de design orientado a objeto, específicos da arquitetura orientada a objetos.

### 3.1 S - *Single Responsibility Principle* (Princípio da Responsabilidade Única)
- Uma classe deve ter apenas uma responsabilidade.
- Do contrário, a modularidade seria comprometida.

### 3.2 O - *Open/Closed Principle* (Princípio Aberto/Fechado)
- Entidades de software devem estar abertas para extensão, mas fechadas para modificação.

### 3.3 L - *Liskov Substitution Principle* (Princípio da Substituição de Liskov)
- Objetos de um programa devem ser substituíveis por instâncias de seus subtipos sem alterar a correção do programa.
- As instâncias dos subtipos não devem alterar a correção de algum programa, no sentido de que eles funcionam de forma modular.

### 3.4 I - *Interface Segregation Principle* (Princípio da Segregação de Interface)
- Muitas interfaces específicas são melhores que uma interface única.
- Se todos os elementos fossem interligados, a alteração em uma parte do código implicaria outras partes do sistema.

> [!CAUTION] OBSERVAÇÃO: 
> - O princípio da segregação de interface NÃO define que uma classe deve possuir somente uma operação para ser executada. Ele defende que muitas interfaces específicas são melhores que uma interface única.

### 3.5 D - *Dependency Inversion Principle* (Princípio da Inversão de Dependência)
- Dependa de abstrações, não de implementações concretas.

## 4. Padrões de Projeto Comportamentais
- Categoria de padrões de design em programação orientada a objetos que lidam com a comunicação eficaz e a distribuição de responsabilidades entre objetos.

### 4.1 Observer
- Utilizado para criar um sistema onde objetos se inscrevem para observar e reagir a eventos em outros objetos.
- Exemplo: aplicativo de notícias com opção de inscrição para receber notificações.

### 4.2 Strategy
- Permite a configuração de diferentes algoritmos para serem usados em um objeto, tornando-os intercambiáveis.
- Exemplo: aplicativo de navegação que pode calcular diferentes rotas.

### 4.3 Command
- Transforma uma solicitação em um objeto autônomo, permitindo operações como enfileiramento e desfazer ações.
- Exemplo: controle que envia comandos para aparelhos eletrônicos.

### 4.4 State
- Permite que um objeto mude seu comportamento quando seu estado interno muda, parecendo alterar sua classe.
- Exemplo: gerenciador de download (pode pausar ou cancelar quando está em andamento).

### 4.5 Iterator
- Permite percorrer elementos de uma coleção sem expor sua representação subjacente.
- Exemplo: listas, pilhas, árvores.

### 4.6 Memento
- Permite que o estado de um objeto seja salvo e restaurado em um momento posterior.
- Exemplo: comando "desfazer" em editores de texto.

> [!TIP] DICAS: 
> - Os padrões comportamentais mais cobrados são: *iterator*, *memento* e *observer*.

## 5. Padrões GRASP (*General Responsibility Assignment Software Patterns*)

### 5.1 Definição
- Conjunto de princípios na programação orientada a objetos que solucionam problemas comuns de atribuição de responsabilidades em modelos de software.

### 5.2 Especialista em Informação (*Information Expert*)
- Atribui responsabilidades à classe que detém as informações necessárias para realizar uma tarefa específica.
- Exemplo: para calcular a média de um aluno, a classe que possui os dados das notas deve ser a responsável pelo cálculo.

### 5.3 Criador (*Creator*)
- Determina que uma classe que contém ou usa frequentemente outra deve ser responsável por criar instâncias dessa outra classe.

### 5.4 Controlador (*Controller*)
- Centraliza o processamento de solicitações, atribuindo a responsabilidade a uma classe que representa um caso de uso específico.

### 5.5 Baixo Acoplamento (*Low Coupling*)
- Promove independência entre classes para aumentar a reutilização e a flexibilidade do código.

### 5.6 Alta Coesão (*High Cohesion*)
- Encoraja o design de classes com responsabilidades bem definidas e focadas, melhorando a compreensibilidade e reduzindo erros.

> [!CAUTION] OBSERVAÇÃO: 
> - Entre os padrões GRASP, destacam-se baixo acoplamento e alta coesão. A banca pode tentar confundir com "baixa coesão e alto acoplamento" - fique atento!

### 5.7 Polimorfismo como Princípio GRASP
- O polimorfismo é um princípio orientador para atribuir responsabilidades a classes abstratas que representem o comportamento de classes concretas para permitir ao sistema lidar com vários tipos de maneira homogênea.

## 6. UML (*Unified Modeling Language*)

### 6.1 Definição
- Linguagem criada como um modelo padronizado para descrever uma abordagem de programação orientada a objeto.
- Facilita o entendimento da arquitetura de software, pois proporciona representação gráfica das estruturas e dos comportamentos do sistema.
- Diagramas de classes são componentes básicos da UML.

### 6.2 Tipos de Diagramas

#### 6.2.1 Diagrama de Classes
- Mostra a estrutura das classes e suas relações.

#### 6.2.2 Diagrama de Casos de Uso
- Descreve as funcionalidades do sistema e suas interações com os usuários.
- Exemplo: clínica médica - relacionamento do paciente com o secretário e com o médico.

#### 6.2.3 Diagrama de Sequência
- Representa a interação entre objetos durante a execução de um cenário específico.
- Exemplo: cliente realiza cadastro incluindo dados cadastrais; validação para verificar se o cliente existe; dados do cliente são inseridos no banco de dados.

#### 6.2.4 Diagrama de Atividades
- Ilustra o fluxo de operações.

> [!TIP] DICAS: 
> - O diagrama de sequência é comumente usado para representar a interação entre objetos durante a execução de um cenário específico.