# Testes de Software 4

## 1. Test Driven Development (TDD)
- Metodologia de desenvolvimento de software que propõe escrever casos de testes automatizados baseados nos requisitos do software antes de desenvolver o código de produção (SOMMERVILLE, 2011).
- É uma prática de desenvolvimento em que o programador escreve o teste antes de escrever a implementação da funcionalidade (PRESSMAN, 2021).
- O processo funciona em ciclos pequenos, onde os requisitos são escritos como casos de teste.
- O feedback rápido e a garantia de que o comportamento da aplicação está cumprindo o que é requerido são objetivos centrais do TDD.
- Em vez de começar pelo código de produção, o desenvolvedor começa definindo o comportamento esperado por meio de um teste automatizado (PRESSMAN, 2021).

### 1.1 Ciclo de Desenvolvimento do TDD (Red-Green-Refactor)
- O ciclo de desenvolvimento do TDD é composto por três etapas principais que se repetem continuamente.

#### 1.1.1 Red (Escrever um teste que falha)
- Etapa inicial onde se escreve um teste automatizado para uma nova funcionalidade que ainda não foi implementada.
- O teste é executado e falha (daí o nome "Red"), pois a funcionalidade ainda não existe no código de produção.
- O teste deve ser simples e específico para uma única funcionalidade.

#### 1.1.2 Green (Implementar código para fazer o teste passar)
- Adiciona-se uma nova funcionalidade ao sistema para fazer o teste passar (PRESSMAN, 2021).
- O desenvolvedor escreve o código mínimo necessário para que o teste seja aprovado.
- O foco nesta etapa é fazer o teste passar, sem se preocupar com a qualidade ou otimização do código.

#### 1.1.3 Refactor (Refatorar o código)
- Eliminar códigos redundantes, remover acoplamentos e identificar pontos de melhoria no código (PRESSMAN, 2021).
- O código da nova funcionalidade deve ser refatorado para melhorar a estrutura interna sem alterar seu comportamento externo.
- Nesta etapa, aperfeiçoa-se a estrutura interna do código e a legibilidade dos testes, eliminando redundâncias.
- O sistema de software deverá ser modificado para melhorar a estrutura interna do código sem alterar seu comportamento funcional externo.
- Após a refatoração, todos os testes devem continuar passando.

### 1.2 Ferramentas para TDD (JUnit)
- JUnit é uma das ferramentas usadas para aplicar o TDD em Java (PRESSMAN, 2021).
- Permite escrever e executar os testes automatizados em Java.
- Suas funcionalidades incluem:
  - Criar o teste antes da implementação;
  - Executar o teste para observar a falha;
  - Reexecutar o teste após implementar o código para verificar se passou;
  - Manter uma suíte de testes para futuras refatorações.

### 1.3 Benefícios do TDD
- O código fica mais modular e com menos defeitos.
- Ajuda o desenvolvedor a escrever código de qualidade.
- Garante que os requisitos do sistema sejam atendidos.
- Torna os testes de regressão mais eficientes.

> [!TIP] DICAS: 
> - No TDD, o desenvolvedor escreve o teste antes de escrever o código de produção.
> - O ciclo TDD sempre segue a ordem: Red (teste falha) ⟶ Green (teste passa) ⟶ Refactor (melhoria do código).
> - A etapa "Refactor" não altera o comportamento funcional do sistema.

> [!CAUTION] OBSERVAÇÃO: 
> - Não se deve escrever testes automatizados apenas para os módulos críticos; no TDD, todos os códigos devem ser guiados por testes.
> - O TDD não é utilizado somente em refactoring de métodos com mais de 256 linhas de código; é uma prática aplicada continuamente.
> - Não é verdade que o TDD torna os testes de regressão mais demorados, pois os testes são automatizados.
> - O TDD não propõe que os testes sejam escritos após a implementação completa do sistema; a prática é exatamente o oposto.

## 2. Mock Objects
- Objetos utilizados no TDD para simular o comportamento de objetos reais durante a realização de um teste de software (PRESSMAN, 2021).
- São objetos "falsos" que apenas simulam o comportamento de um objeto ou classe real para focar o teste no objeto a ser validado (SOMMERVILLE, 2011).
- Possuem a mesma interface que os objetos externos usados para simular sua funcionalidade.
- Podem ser usados para simular operações anormais ou eventos raros.
- Auxiliam os testes unitários, pois são objetos com a mesma interface que os objetos externos.

### 2.1 Finalidade dos Mock Objects em Testes
- Substituir dependências externas que podem não ter sido escritas ou que atrasam o processo de teste (SOMMERVILLE, 2011).
- Exemplo: se o objeto chama um banco de dados, isso pode implicar um processo lento de instalação antes que possa ser usado.
- Isolar a unidade de código em teste, eliminando dependências externas e não-determinísticas (PRESSMAN, 2021).
- Evitar a poluição do código em produção com elementos de testes propriamente ditos.

### 2.2 Mock Objects vs. Objetos Reais
- Mock objects não são objetos genéricos que atendem a todas as necessidades de testes; eles são específicos para simular comportamentos particulares.
- Ao contrário do que alguns afirmam, não é inviável utilizar Mock Objects em testes unitários; eles são amplamente utilizados para isolar o código em teste.

> [!TIP] DICAS: 
> - Mock objects são utilizados para isolar o código em teste, substituindo dependências externas como bancos de dados, APIs e serviços.
> - Em provas, lembre-se: mock objects são usados para testes unitários, não para testes de integração.

> [!CAUTION] OBSERVAÇÃO: 
> - Mock objects não são objetos genéricos que atendem a todas as necessidades de testes (CESPE/CEBRASPE, 2025 - Item ERRADO).
> - Mock objects podem ser usados em testes unitários; não é verdade que lidam com mais de um objeto ao mesmo tempo (CESPE/CEBRASPE, 2015 - Item ERRADO).
> - Em testes automatizados, para diminuir problemas de lentidão ao se acessar um banco de dados no teste de funcionalidade, pode-se substituir o banco de dados por mock objects (CESPE/CEBRASPE, 2020 - Item CERTO).

## 3. Testes Unitários
- Processo em que se testam os componentes do programa, que podem ser procedures, métodos ou classes (PRESSMAN, 2021).
- Verificam o comportamento isolado de unidades de código, utilizando técnicas como mocks e stubs para simular dependências externas.
- O objetivo é garantir que cada unidade de código funcione corretamente de forma isolada.

### 3.1 Relação entre Testes Unitários e Mock Objects
- Mock objects são ferramentas essenciais para testes unitários, pois permitem isolar a unidade em teste.
- Substituem dependências externas que poderiam introduzir comportamentos não-determinísticos ou lentidão.
- Facilitam a criação de testes focados exclusivamente na lógica da unidade sendo testada.

> [!CAUTION] OBSERVAÇÃO: 
> - Testes unitários são mais eficazes quando escritos antes da implementação (TDD), não após a implementação completa do sistema (CONSULPAM, 2025 - Item D - sentença 1 falsa, sentença 2 verdadeira).
> - Em testes unitários, para garantir o isolamento da unidade de código, eliminam-se dependências externas e não-determinísticas usando Mock Objects (FGV, 2025 - Alternativa B correta).