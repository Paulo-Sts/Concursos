# Testes de Software

## 1. Conceituação de Testes de Software
- Teste de software é o processo de avaliar se o sistema faz o que deveria fazer.
- Essa avaliação deve ocorrer tanto nas condições esperadas quanto diante de situações inválidas ou inesperadas.
- Todo sistema de software está sujeito a erros, mesmo códigos aparentemente simples podem apresentar falhas quando recebem entradas inesperadas.
- Os testes tornam-se necessários quando:
  - Regras de negócio mudam;
  - Novas funcionalidades são adicionadas.

> [!TIP] DICAS: 
> - A definição central de teste é "avaliar se o sistema faz o que deveria fazer". Essa é a base para qualquer questão introdutória sobre o tema.

## 2. Por que Testar os Softwares
- Os softwares precisam ser testados porque estão sujeitos a erros em todas as fases do desenvolvimento.
- Testar envolve verificar o comportamento do sistema diante de entradas válidas e inválidas.
- O teste não se restringe a validar o funcionamento padrão, mas também a robustez do sistema em situações imprevistas.

### 2.1 Mudanças e Novas Funcionalidades
- Quando as regras de negócio mudam, é necessário testar para garantir que o sistema ainda atende aos novos requisitos.
- Quando novas funcionalidades são adicionadas, os testes verificam se a integração com o sistema existente ocorre sem falhas.
- Códigos aparentemente simples podem falhar ao receber entradas inesperadas, o que reforça a necessidade de testes abrangentes.

> [!CAUTION] OBSERVAÇÃO: 
> - A banca pode cobrar a ideia de que testar não é apenas verificar o que o sistema faz, mas também o que ele não deveria fazer. Fique atento a essa dualidade.

## 3. Objetivos do Processo de Teste
- O processo de teste possui dois objetivos principais, que são complementares e não excludentes.

### 3.1 Objetivo 1: Demonstrar Conformidade com os Requisitos
- Demonstrar ao desenvolvedor e ao cliente que o software atende a seus requisitos.
- Para softwares customizados: deve haver pelo menos um teste para cada requisito do documento de requisitos.
- Para softwares genéricos: deve haver testes para todas as características do sistema, além de suas combinações, que serão incorporadas ao release do produto.
- Esse objetivo está relacionado à validação e à verificação do sistema.

### 3.2 Objetivo 2: Descobrir Defeitos e Comportamentos Indesejáveis
- Descobrir situações em que o software se comporta de maneira incorreta, indesejável ou de forma diferente das especificações.
- Essas situações são consequências de defeitos de software.
- O teste de defeitos preocupa-se com a eliminação de comportamentos indesejáveis do sistema.
- Exemplos de comportamentos indesejáveis:
  - Panes (falhas graves);
  - Interações indesejáveis com outros sistemas;
  - Processamentos incorretos;
  - Corrupção de dados.

> [!TIP] DICAS: 
> - Os dois objetivos (demonstrar conformidade e descobrir defeitos) são frequentemente cobrados em provas. Lembre-se de que eles não se substituem; ambos são necessários.
> - O objetivo 2 é conhecido como "teste de defeitos" e foca em eliminar comportamentos ruins, não apenas em provar que o sistema funciona.

## 4. Estágios e Níveis de Granularidade dos Testes
- O material menciona a existência de três estágios de testes e três níveis de granularidade.
- Embora os slides não detalhem cada um, a estrutura hierárquica é um ponto importante para concursos.

### 4.1 Três Estágios de Testes
- Os estágios representam as fases do processo de teste ao longo do desenvolvimento.
- A divisão em estágios ajuda a organizar a execução dos testes desde as unidades menores até o sistema completo.

### 4.2 Três Níveis de Granularidade de Testes
- A granularidade refere-se ao tamanho e ao escopo do que está sendo testado.
- Quanto menor a granularidade, mais focado e isolado é o teste; quanto maior, mais integrado e abrangente.

| NÍVEL DE GRANULARIDADE | DESCRIÇÃO |
|---|---|
| Teste de unidade | Valida a menor unidade de código isolável, normalmente classes ou métodos; utiliza objetos simulados (mocks) para desvincular a lógica de negócio de dependências externas complexas. |
| Teste de integração | Explora funcionalidades de maior granularidade, envolvendo mais classes e, eventualmente, pacotes distintos; verifica a comunicação entre componentes. |
| Teste de interface (ou sistema) | Valida o fluxo de negócio de forma abrangente e real, testando o sistema como um todo; não substitui os testes de unidade e integração. |

> [!CAUTION] OBSERVAÇÃO: 
> - A pirâmide de testes recomenda que o volume de testes unitários seja superior ao de testes de integração e de interface, devido à sua rapidez e baixo custo. Esse princípio é cobrado com frequência.
> - Testes de interface não substituem os testes de unidade e integração, pois cada nível tem um propósito específico e complementar.

## 5. Etapas de Teste de Software
- O slide indica a existência de etapas, mas não as detalha no conteúdo fornecido.
- As etapas geralmente compreendem planejamento, projeto, execução e avaliação dos testes.
- A ausência de detalhamento no material sugere que o foco da aula foi a introdução e conceituação.

> [!TIP] DICAS: 
> - Em provas, é comum associar cada nível de teste a um objetivo específico. Por exemplo: testes unitários focam em lógica interna; testes de integração focam em comunicação entre componentes; testes de interface focam no fluxo de ponta a ponta.

## 6. Considerações Finais sobre os Conceitos
- Testes de software são essenciais para garantir a qualidade e a confiabilidade dos sistemas.
- O processo de teste deve equilibrar a verificação de conformidade com a busca por defeitos.
- A automação de testes é um componente fundamental para a qualidade contínua, permitindo a execução frequente de suítes de validação.
- Os diferentes níveis de teste (unidade, integração, interface) devem ser utilizados de forma complementar, respeitando a pirâmide de testes.