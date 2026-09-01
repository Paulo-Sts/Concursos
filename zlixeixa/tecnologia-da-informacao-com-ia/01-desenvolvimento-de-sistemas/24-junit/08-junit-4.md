# Testes Automatizados e Desenvolvimento Orientado a Testes 4

## 1. Contexto e Abordagens de Teste
- O teste de software é executado de maneira diferente dependendo do contexto e do modelo de desenvolvimento adotado.
- Em projetos ágeis, a abordagem de teste difere da utilizada em projetos de ciclo de vida sequencial.
- Produtos de trabalho da implementação de teste incluem trabalhos manuais como:
  - Procedimentos de teste e seu sequenciamento;
  - Elaboração das suítes de teste;
  - Cronograma de execução do teste.
- Em modelos de desenvolvimento incremental e iterativo, onde alterações de código estão em andamento, testes automatizados desempenham um papel fundamental.
- Os testes automatizados criam confiança de que as alterações não impactaram os componentes existentes.

> [!TIP] DICAS: 
> - Em projetos ágeis, a automatização de testes é ainda mais relevante devido à frequência de mudanças no código.
> - O foco principal dos testes automatizados em cenários iterativos é garantir que novas funcionalidades não quebrem as existentes.

### 1.1 Tipos de Testes e Automatização
- Entre os diferentes tipos de teste, o mais propenso a ser automatizado é o teste de regressão.
- O teste de regressão verifica se alterações no código não impactaram funcionalidades já existentes.
- Sua natureza repetitiva e a necessidade de execução frequente tornam a automatização altamente vantajosa.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora outros tipos de teste possam ser automatizados parcialmente, o teste de regressão é o que apresenta maior viabilidade e retorno sobre o investimento em automação.

## 2. Testes Automatizados
- Testes automatizados são executados pela máquina, diferentemente dos testes manuais.
- Possuem custo inicial de implementação, mas geram economia de tempo e recursos a longo prazo.
- Aumentam a confiabilidade do produto final quando implementados corretamente.
- Garantem que os procedimentos do software estejam de acordo com as especificações previstas no projeto.

## 3. Frameworks para Testes Automatizados
- Frameworks são ferramentas que fornecem estrutura e funcionalidades para criação e execução de testes automatizados.
- No ecossistema Java, o framework mais popular e amplamente utilizado é o JUnit.

### 3.1 JUnit
- É um framework open-source para criação de testes automatizados em Java.
- Permite escrever e executar testes de unidade de forma estruturada.
- Suporta a criação de baterias de testes automatizados baseados em modelos de testes padrão.
- Utilizado para:
  - Criar o teste antes da implementação;
  - Executar o teste e observar a falha;
  - Reexecutar o teste após a implementação para verificar se o teste passou;
  - Manter uma suíte de testes para futuras refatorações.
- É a ferramenta que materializa a prática de Test-Driven Development (TDD) em Java.

> [!TIP] DICAS: 
> - JUnit é o framework de testes mais cobrado em concursos para plataforma Java.
> - Associação direta: JUnit ⟶ testes de unidade; JUnit ⟶ TDD.

### 3.2 Cucumber
- Framework associado à técnica de Behavior-Driven Development (BDD).
- Diferencia-se do JUnit por focar na descrição do comportamento esperado em linguagem natural.

## 4. Test-Driven Development
- O TDD é um processo de desenvolvimento de software que visa garantir que o comportamento da aplicação está cumprindo o que é requerido.
- O processo funciona em ciclos pequenos, onde os requisitos são escritos como casos de teste.
- O código é desenvolvido de forma incremental, em conjunto com o teste para esse incremento.
- Só se passa para o próximo incremento quando o atual passar no teste.
- O feedback rápido é uma das principais características do TDD.

### 4.1 Ciclo do TDD
- O ciclo de desenvolvimento do TDD é composto por etapas curtas e repetitivas:
  - Escreve-se um teste automatizado para uma nova funcionalidade antes mesmo de o código da funcionalidade estar pronto.
  - Executa-se o teste e observa-se a falha.
  - Implementa-se o código mínimo necessário para fazer o teste passar.
  - Executa-se novamente o teste para verificar se o teste passou.
  - Refatora-se o código, se necessário, mantendo os testes passando.

> [!TIP] DICAS: 
> - A estratégia de escrever testes automatizados antes do código da funcionalidade estar pronto é chamada de Test-Driven Development.
> - O TDD é frequentemente associado ao Extreme Programming (XP), sendo uma de suas práticas centrais.

### 4.2 Princípios do Desenvolvimento Baseado em Testes
- Este processo requer que desenvolvedores criem unidades de teste para definir os requisitos que um determinado código deve conter.
- Os testes devem ser criados antes do código, e não após uma parte funcional estar disponível.
- Frequentemente são utilizados frameworks de teste pelos desenvolvedores, como o xUnit ou JUnit, para a criação de casos de teste automatizados.
- É importante que o código escrito seja apenas projetado para passar o teste específico.
- Nenhuma outra funcionalidade deve ser prevista ou permitida fora do escopo do teste em nenhum estágio do processo.

> [!CAUTION] OBSERVAÇÃO: 
> - Um erro comum é pensar que os testes são criados após o código estar pronto. No TDD, a criação do teste é o ponto de partida.
> - O princípio de escrever apenas o código necessário para passar no teste evita o desenvolvimento de funcionalidades desnecessárias (overengineering).

## 5. O Padrão AAA
- O padrão AAA (Arrange-Act-Assert), também conhecido como Triple A, é uma forma didática e organizada de escrever testes unitários.
- Divide o teste em três etapas distintas, com responsabilidades bem definidas.

### 5.1 Etapas do Padrão AAA
| ETAPA | DESCRIÇÃO | FINALIDADE |
|---|---|---|
| Arrange | Configura-se tudo o que é necessário para que o teste possa rodar | Preparação do cenário de teste |
| Act | Processa-se de fato o teste | Execução do comportamento a ser testado |
| Assert | Verifica-se se a operação realizada na etapa anterior surtiu o resultado esperado | Verificação do resultado |

#### 5.1.1 Arrange (Preparação)
- É a fase de montagem do cenário de teste.
- Momento de preparar tudo o que o teste precisa para ser executado.
- Nessa fase:
  - Criam-se objetos;
  - Inicializam-se variáveis;
  - Configuram-se dados de entrada;
  - Criam-se test doubles, como Mocks.
- Deixa-se o cenário pronto para a execução.

> [!TIP] DICAS: 
> - Exemplo de código na fase Arrange:
>   ```java
>   Calculadora calculadora = new Calculadora();
>   int a = 2;
>   int b = 3;
>   ```

#### 5.1.2 Act (Ação/Execução)
- É o momento em que se executa o comportamento que se quer testar.
- Chama-se o método da classe que está sendo testada.
- É a ação principal do teste.
- A execução é realizada para que o comportamento possa ser verificado na etapa seguinte.

> [!TIP] DICAS: 
> - Exemplo de código na fase Act:
>   ```java
>   int resultado = calculadora.somar(a, b);
>   ```

#### 5.1.3 Assert (Verificação)
- É o momento de verificar se o resultado obtido corresponde ao resultado esperado.
- No JUnit, essa verificação é feita por meio de métodos de asserção.
- Principais métodos de asserção do JUnit:
  - `assertEquals()`;
  - `assertTrue()`;
  - `assertFalse()`;
  - `assertNull()`;
  - `assertNotNull()`;
  - `assertThrows()`.

> [!TIP] DICAS: 
> - Exemplo de código na fase Assert:
>   ```java
>   assertEquals(5, resultado);
>   ```
> - O padrão AAA ajuda a deixar o teste mais organizado, legível, fácil de entender, fácil de manter e claro para identificar falhas.

### 5.2 SUT (System Under Test)
- SUT é o sistema, classe ou método que está sendo testado.
- Não se encontra apenas na etapa Assert.
- É preparado no Arrange, executado no Act e verificado no Assert.

> [!CAUTION] OBSERVAÇÃO: 
> - É incorreto afirmar que o SUT se encontra apenas na etapa Assert. Ele está presente em todas as etapas do teste: preparado (Arrange), executado (Act) e verificado (Assert).