# Engenharia de Software - Estágio de Teste 9

## 1. Teste de Conteúdo
- Utilizado para identificar erros em conteúdos gerados de forma dinâmica a partir de bases de dados.
- Atua como um teste funcional focado em obter resultados específicos, como a consulta de uma lista de alunos.
- Cada nível da pirâmide de projeto possui seu próprio teste de conteúdo correspondente.

## 2. Teste de Base de Dados
- Aplicado em sistemas que interagem com gerenciadores de banco de dados para criar conteúdos dinâmicos em tempo real.
- A finalidade central é validar se o banco de dados está retornando as informações conforme o esperado via comandos SQL.

## 3. Teste de Usabilidade
- Avalia o software sob três prismas fundamentais de qualidade para o usuário.

| PRISMA | CARACTERÍSTICA | IMPACTO |
|---|---|---|
| Facilidade de uso | Nível de esforço para aprender e efetividade | Quanto maior a facilidade, melhor a experiência do usuário. |
| Facilidade de entendimento | Nível de clareza e informação | Uma usabilidade ruim pode ser considerada enganosa e induzir ao erro. |
| Previsibilidade | Nível de uniformidade | Busca garantir que o sistema se comporte de forma previsível. |

## 4. Ferramentas de Teste Estático
- Realizam a análise de artefatos sem a necessidade de executar o código-fonte do sistema.
- Embora não rodem o código analisado, a ferramenta executa seu próprio processamento interno de análise.

### 4.1 Tipos de Ferramentas Estáticas
- Baseadas em código: analisam o código-fonte para gerar casos de teste automaticamente, como o SonarQube.
- Linguagens especializadas: permitem a escrita de especificações detalhadas de logística de teste, como a linguagem ATLAS.
- Baseadas em requisitos: isolam requisitos do usuário para sugerir classes de testes que os exercitem.

## 5. Ferramentas de Teste Dinâmico
- Interagem diretamente com o programa em execução para verificar fluxos e valores de variáveis.
- Exemplos comuns em concursos incluem o JUnit, Selenium e JMeter.

### 5.1 Mockito e Objetos Fictícios
- Framework de código aberto utilizado para criar objetos fictícios (mocks) em testes de software.
- Objetos fictícios são implementações simuladas de interfaces ou classes que permitem definir saídas específicas para métodos.
- Simplificam a configuração de testes ao isolar classes de suas dependências externas.

### 5.2 Appium
- Ferramenta de automação para execução de scripts em aplicativos móveis nativos, web ou híbridos.
- Suporta plataformas Android e iOS utilizando o protocolo webdriver.

> [!TIP] DICAS: 
> - Junit, Selenium e JMeter são as ferramentas dinâmicas mais frequentes em provas ⟶ foque no estudo das funcionalidades específicas de cada uma.

> [!CAUTION] OBSERVAÇÃO: 
> - Análise estática ⟶ não executa o código do sistema.
> - Teste de unidade ⟶ é um teste dinâmico focado nas menores partes do programa, como funções e objetos.
> - Test-Driven Development (TDD) ⟶ utiliza frameworks como JUnit para automação de testes de unidade em Java.