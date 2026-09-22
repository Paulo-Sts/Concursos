# Engenharia de Software - Requisitos 7

## 1. Conceitos Fundamentais de Requisitos
- Requisitos estabelecem o que o sistema deve fazer e definem as restrições sobre seu funcionamento e implementação.
- A engenharia de requisitos tem como objetivo fazer com que o cliente obtenha aquilo que pediu.
- Os requisitos podem se apresentar em inúmeras formas e classificações.
- Exemplo: em um sistema de controle de trem, o requisito de domínio deve levar em conta as características de frenagem em diferentes condições climáticas.

### 1.1 Classificação dos Requisitos
- Requisitos funcionais e não funcionais.
- Requisitos de usuário, de sistema e de QFD (Quality Function Deployment).
- Requisitos normais, esperados e fascinantes.
- Requisitos de projeto, de negócio, de produto, organizacionais e de levantamento.

### 1.2 Requisitos Funcionais
- São declarações dos serviços que o sistema deve fornecer.
- Descrevem como alguns processamentos devem ser efetuados.
- Representam as funcionalidades específicas que o sistema precisa executar.

### 1.3 Requisitos Não Funcionais
- Restringem o sistema que está sendo desenvolvido e o processo de desenvolvimento que está sendo usado.
- Classificam-se em:
  - Requisitos de produto;
  - Requisitos organizacionais;
  - Requisitos externos.
- Costumam se relacionar com as propriedades emergentes do sistema, aplicando-se ao sistema como um todo.
- São critérios de qualidade do sistema e do software.
- Requisitos não funcionais indefinidos prejudicam o software como um todo.
- É necessário ter requisitos não funcionais bem definidos.

### 1.4 Requisitos de Domínio
- Criados a partir das características do ambiente onde o sistema será inserido.
- Podem criar novos requisitos funcionais.
- Podem impor restrições sobre requisitos existentes.
- Podem definir cálculos específicos.
- Exemplo: sistema de controle de trem deve considerar as características de frenagem em diferentes condições climáticas.

> [!TIP] DICAS: 
> - Os requisitos de domínio são frequentemente cobrados em provas, especialmente quando se pede para identificar a origem de um requisito específico.
> - Lembre-se: o requisito de domínio sempre se relaciona com o contexto onde o sistema será aplicado.

## 2. Processo de Engenharia de Requisitos
- Inclui um estudo da viabilidade, elicitação e análise de requisitos, especificação de requisitos, validação e gerenciamento de requisitos.
- É um processo iterativo e contínuo.

> [!CAUTION] OBSERVAÇÃO: 
> - A engenharia de software se preocupa com o software, enquanto a engenharia de sistema é mais ampla, englobando o software.

### 2.1 Elicitação e Análise de Requisitos
- Processo iterativo em espiral composto por:
  - Descoberta de requisitos;
  - Classificação e organização de requisitos;
  - Negociação de requisitos;
  - Documentação de requisitos.

### 2.2 Técnicas de Levantamento
- As técnicas mais exigidas pelas bancas examinadoras são:
  - Etnografia;
  - Prototipação.
- O autor Sommerville também é amplamente cobrado em provas.

#### 2.2.1 Etnografia
- Técnica na qual se observa e anota o comportamento dos usuários no ambiente de trabalho.
- Pode revelar requisitos que não eram claros anteriormente.
- Útil para descobrir requisitos implícitos que os stakeholders não conseguem expressar formalmente.
- Exemplo: a etnografia pode exibir requisitos que, outrora, não eram tão claros, apesar da utilização prévia da prototipação.

> [!CAUTION] OBSERVAÇÃO: 
> - A etnografia não utiliza um conjunto predefinido de questões. Diferente de entrevistas estruturadas, a observação é o principal instrumento.

### 2.3 Validação de Requisitos
- Processo de verificação da validade, consistência, completude, realismo e verificabilidade dos requisitos.
- No processo de validação, deve-se verificar também a adaptabilidade.
- Exemplo: não existe um balanço com três assentos e, por isso, o crivo da validade é importante.

#### 2.3.1 Propriedades Verificadas na Validação
- Verificabilidade: a exigência é realmente testável.
- Compreensibilidade: o requisito é adequadamente compreendido.
- Rastreabilidade: a origem do requisito é clara.
- Adaptabilidade: o requisito pode ser alterado sem causar um grande impacto sobre outros requisitos.
- Completude: o requisito não pode ser excluído sem prejuízo ao sistema.

### 2.4 Especificação de Requisitos
- Documento de requisitos de software é uma declaração acordada dos requisitos do sistema.
- Deve ser organizado para que tanto os clientes do sistema quanto os desenvolvedores de software possam usá-lo.
- No final do processo de licitação, o documento de requisito do software é uma declaração acordada dos requisitos do sistema.

## 3. Gerenciamento de Requisitos
- Mudanças organizacionais, mudanças nos negócios e mudanças técnicas inevitavelmente geram mudanças nos requisitos para um sistema de software.
- O processo espiral pode ter alteração de requisitos com o tempo.

### 3.1 Planejamento do Gerenciamento de Requisitos
- O planejamento é o primeiro estágio essencial no processo de gerenciamento de requisitos.
- Determina o nível de detalhamento requerido no gerenciamento de requisitos.
- Estabelece a estabilidade necessária, as ferramentas a serem utilizadas e como será feito o gerenciamento.

> [!TIP] DICAS: 
> - O planejamento é o ponto de partida do gerenciamento de requisitos e determina o nível de detalhamento necessário.
> - Quando no processo de licitação, planeja-se o gerenciamento de requisitos.

## 4. Relação entre Requisitos e Teste de Software
- Requisitos devem ser testáveis, ou seja, escritos de modo que um teste possa ser projetado para eles.
- Testes baseados em requisitos são uma abordagem sistemática para projeto de casos de teste.
- Cada requisito é considerado para derivar um conjunto de testes para ele.
- A correção, a completude e a consistência do modelo de requisitos têm forte influência sobre a qualidade de todos os produtos seguintes do desenvolvimento de software.

> [!CAUTION] OBSERVAÇÃO: 
> - O que importa para o teste não é apenas o código-fonte. Os requisitos bem definidos são fundamentais para a qualidade do teste.

## 5. Usabilidade e Requisitos
- A usabilidade refere-se à facilidade com que os usuários podem interagir com o sistema.
- Falhas na especificação de requisitos podem prejudicar a usabilidade.
- Exemplo: falta de controle na entrada de dados (como endereços eletrônicos sem regra de formação) caracteriza falhas na especificação de requisitos de usabilidade.
- O ideal em sistemas é que o erro seja evitado, pois o custo de corrigi-lo depois é alto.