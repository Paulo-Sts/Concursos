# Testes de Software e JUnit 2

## 1. Conceitos Fundamentais de Testes

### 1.1 Cobertura de Testes
- É uma métrica utilizada para indicar quais partes do código foram executadas durante a execução dos testes automatizados.
- Mede o quanto do código-fonte foi exercitado pelos testes.
- Exemplo: se uma classe possui 100 linhas de código e os testes executam 80 dessas linhas, então há uma cobertura de 80% das linhas em tese.

> [!CAUTION] OBSERVAÇÃO: 
> - O JUnit, por si só, não mede cobertura de testes. Normalmente, utilizam-se ferramentas complementares para essa finalidade, como JaCoCo, Cobertura ou Emma.
> - Essa é uma pegadinha comum em provas: afirmar que o JUnit gera relatórios de cobertura sem ferramentas adicionais está ERRADO.

### 1.2 Teste Unitário
- É uma modalidade de testes que se concentra na verificação da menor unidade do projeto de software (geralmente métodos, funções ou classes).
- Foca em validar cada componente individualmente.
- É rápido de ser executado, pois testa partes isoladas do sistema.
- Geralmente é realizado pelos próprios desenvolvedores, não pelos usuários finais.
- Não verifica a interação entre diferentes módulos do software (isso é papel dos testes de integração).

> [!CAUTION] OBSERVAÇÃO: 
> - O teste unitário é conhecido como teste de "caixa branca", pois o desenvolvedor tem acesso ao código-fonte e conhece sua estrutura interna.
> - Não confunda com teste de integração (que verifica a interação entre módulos) nem com teste de sistema (que avalia o sistema como um todo).

### 1.3 Testes de Regressão
- São testes executados sempre que alguma modificação no código é feita.
- Ajudam a detectar quando partes do código que estavam funcionando passam a apresentar erros após o código ter sido modificado.
- Estão diretamente relacionados à prática de Test Driven Development (TDD) e integração contínua.
- JUnit pode ser estendido para se criar um ambiente de testes de regressão automatizado.

### 1.4 Test Driven Development (TDD)
- Prática essencial onde o desenvolvedor cria um ou mais testes para cada unidade do sistema (classe, função ou método) antes de escrever o código propriamente dito.
- Normalmente utiliza um pacote feito na mesma linguagem de programação do programa, como JUnit para Java.

## 2. Framework JUnit

### 2.1 Definição e Propósito
- JUnit é um framework open-source que facilita o desenvolvimento e execução de testes automatizados em Java.
- É um framework de teste de unidade que auxilia a criação e execução de testes sobre classes Java.
- Constitui um conjunto de classes em Java que o usuário estende para criar um ambiente de testes automatizado.
- Permite validar partes específicas do código de forma automatizada.
- Facilita a criação e manutenção do código para a automação de testes com apresentação dos resultados.

> [!TIP] DICAS: 
> - JUnit é especificamente para a linguagem Java. Frameworks similares existem para outras linguagens: PHPUnit (PHP), NUnit (.NET/C#), CUnit (C).
> - Não confunda JUnit com outras ferramentas: ele não é para testes de desempenho, carga, interface de usuário ou integração distribuída.

### 2.2 Características e Funcionalidades
- Possui integração com várias IDEs (Ambientes de Desenvolvimento Integrado) como Eclipse, IntelliJ IDEA e NetBeans.
- É largamente utilizado em equipes que adotam Extreme Programming (XP).
- Permite criar hierarquia de testes para testar todo ou apenas parte do sistema.
- Fornece suporte para execução de testes, geração de logs e verificação de resultados.
- Pode ser utilizado tanto para testes unitários quanto, em alguns contextos, para testes funcionais, embora seu propósito principal seja o teste de unidade.

### 2.3 Limitações Importantes
- JUnit não mede cobertura de testes.
- JUnit não gera automaticamente relatórios de cobertura de código.
- JUnit não é projetado especificamente para testar interfaces de usuário (como Java Swing).
- JUnit não é uma ferramenta para execução paralela de testes de integração distribuídos.
- JUnit não é um framework para testes de desempenho e carga.

> [!CAUTION] OBSERVAÇÃO: 
> - Para medir cobertura de testes com JUnit, é necessário utilizar ferramentas complementares como JaCoCo, Cobertura ou Emma.
> - Afirmar que o JUnit "permite a geração automática de relatórios de cobertura de código sem precisar de ferramentas adicionais" é uma pegadinha comum em concursos.

## 3. Comparação com Outros Frameworks e Ferramentas

### 3.1 Frameworks XUnit por Linguagem
| LINGUAGEM | FRAMEWORK DE TESTE |
|---|---|
| Java | JUnit |
| PHP | PHPUnit |
| .NET / C# | NUnit |
| C | CUnit |

### 3.2 Ferramentas de Integração Contínua
- Git: controle de versão.
- JUnit: testes automatizados.
- Hudson e Jenkins: deploys em ambientes de desenvolvimento e produção.
- Essas ferramentas, quando utilizadas em conjunto, reduzem a geração de erros de integração.

## 4. Níveis de Teste

### 4.1 Hierarquia de Testes
- Teste de Unidade: teste de unidades individuais do sistema (métodos, classes).
- Teste de Integração: verifica a interação entre diferentes módulos do software.
- Teste de Sistema: processo que envolve a integração de todas as unidades do sistema, verificando o desempenho como um todo.

### 4.2 Técnicas de Teste
- Teste Estrutural (ou Caixa Branca): recomendado para os níveis de testes de unidade e de integração.
- Para a execução dos testes unitários com técnica estrutural, faz-se uso do JUnit.

> [!CAUTION] OBSERVAÇÃO: 
> - O modelo V de desenvolvimento de software deriva planos de testes da especificação e do projeto de sistema.
> - No modelo V, a técnica de teste estrutural é recomendada para testes de unidade e integração.