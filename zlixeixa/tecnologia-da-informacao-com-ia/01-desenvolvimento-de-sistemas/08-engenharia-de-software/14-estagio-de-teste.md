# Engenharia de Software - Estágio de Teste

## 1. Conceitos Fundamentais de Testes de Software
- O teste de software é uma área ampla dentro da engenharia de software, com diversas nomenclaturas e abordagens segundo diferentes autores.
- Destina-se a demonstrar que um programa faz o que é proposto a fazer e a descobrir defeitos antes do uso.
- O processo de teste possui dois objetivos distintos:
  - Demonstrar ao desenvolvedor e ao cliente que o software atende a seus requisitos;
  - Descobrir situações em que o software se comporta de maneira incorreta, indesejável ou diferente das especificações.

### 1.1 Testes de Validação
- Baseiam-se no primeiro objetivo: demonstrar que o sistema atende aos requisitos.
- Utilizam casos de teste que refletem o uso esperado do sistema.
- Espera-se que o sistema execute corretamente durante esses testes.

### 1.2 Testes de Defeitos
- Baseiam-se no segundo objetivo: expor defeitos no sistema.
- Os casos de teste são projetados especificamente para encontrar falhas.
- Podem ser deliberadamente obscuros e não precisam refletir o uso comum do sistema.

> [!TIP] DICAS: 
> - Os limites entre testes de validação e defeitos não são rígidos; durante a validação podem ser encontrados defeitos, e nos testes de defeitos alguns testes podem mostrar conformidade com os requisitos.

> [!CAUTION] OBSERVAÇÃO: 
> - Deve-se definir um limite para testar, pois a empresa não pagará um testador para testar infinitamente.

## 2. Verificação e Validação (V&V)
- Verificação e validação são processos distintos, porém complementares, dentro do V&V.

### 2.1 Validação
- Processo mais geral que visa garantir que o software atenda às expectativas do cliente.
- Vai além da simples verificação de conformidade com as especificações.
- Busca demonstrar que o software faz o que o cliente espera que ele faça.
- Relaciona-se à pergunta: "estamos construindo o produto certo?".

### 2.2 Verificação
- Processo que checa se o software está sendo construído de acordo com o que foi especificado.
- Verifica se os requisitos funcionais e não funcionais estão sendo atendidos.
- Relaciona-se à pergunta: "estamos construindo o produto da maneira certa?".

## 3. Inspeções e Revisões
- Técnicas estáticas de V&V, pois não requerem a execução do software.
- Podem ser aplicadas a diversas representações do software, como:
  - Requisitos de sistema;
  - Modelos de projeto (ex.: UML, arquitetura de software);
  - Código-fonte do programa;
  - Esquemas de banco de dados;
  - Testes de sistema propostos.
- Atualmente, também podem incluir a inspeção de protótipos do sistema.
- Ferramenta comum utilizada em inspeções: Sonar.

### 3.1 Vantagens da Inspeção sobre os Testes Dinâmicos
- Durante o teste dinâmico, erros podem mascarar outros erros, dificultando a identificação da causa de anomalias; a inspeção, por ser estática, não sofre com essa interação e pode descobrir muitos erros em uma única sessão.
- Versões incompletas do sistema podem ser inspecionadas sem custos adicionais de desenvolvimento de dispositivos de teste especializados.
- Além de defeitos, a inspeção pode avaliar outros atributos de qualidade, como:
  - Conformidade com padrões;
  - Portabilidade;
  - Manutenibilidade;
  - Ineficiências e algoritmos inadequados;
  - Estilo de programação que dificulte a manutenção.

> [!TIP] DICAS: 
> - Fagan (1986) relatou que mais de 60% dos erros em um programa podem ser detectados por inspeções informais.
> - No processo Cleanroom, afirma-se que mais de 90% dos defeitos podem ser descobertos em inspeções.

> [!CAUTION] OBSERVAÇÃO: 
> - As inspeções não substituem os testes de software, pois não são eficazes para descobrir defeitos decorrentes de interações inesperadas entre partes do programa, problemas de timing ou de desempenho.
> - Deve-se utilizar uma estratégia conjunta de inspeções e testes.

## 4. Modelo de Entrada-Saída de Teste
- O modelo ilustra a relação entre entradas e saídas no processo de teste.
- Existem entradas que causam comportamentos anômalos dentro do conjunto de dados de teste.
- Entre as saídas do teste, algumas revelam defeitos no sistema.

## 5. Modelo V de Testes
- Modelo amplamente cobrado em concursos, que enfatiza a associação entre cada nível do processo de desenvolvimento e um nível de teste correspondente.
- Para cada atividade do processo, há um teste associado.

### 5.1 Estrutura do Modelo V
- Especificação de requisitos: plano de testes de aceitação.
- Especificação de sistema: plano de testes de integração de sistema.
- Projeto de sistema: plano de teste de integração do subsistema.

### 5.2 Níveis de Teste Mais Cobrados
- Teste de unidade: testa o método de uma classe.
- Teste de integração: testa como as classes conversam entre si.
- Teste de sistema: testa o funcionamento de todos os componentes juntamente com o hardware.
- Teste de aceitação: o usuário realiza a aceitação final, permitindo que o software entre em produção.

> [!TIP] DICAS: 
> - O Modelo V é um dos mais cobrados pelas bancas de concurso, assim como os quatro níveis de teste listados.

## 6. Atenção aos Conceitos de Verificação e Validação
- Verificação: foco em verificar se os processos foram seguidos e se os requisitos especificados foram implementados corretamente.
- Validação: processo mais geral para verificar se o software atende às expectativas do usuário, podendo, em alguns casos, estar em desacordo com a verificação (o cliente pode não aprovar mesmo que os processos tenham sido seguidos).

> [!CAUTION] OBSERVAÇÃO: 
> - Os testes podem mostrar apenas a presença de erros, e não sua ausência (Dijkstra et al. 1972).