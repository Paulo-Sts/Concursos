# Engenharia de Software - Conceitos Gerais 4

## 1. Definição de Processos
- Conjunto de atividades relacionadas que levam à produção de um produto de software.
- Cada modelo representa uma abordagem usada para a criação do software.
- Ter um bom processo não é garantia de geração de um bom produto final, embora o ideal seja melhorar o processo para melhorar o produto.

## 2. Processo Cascata (Waterfall)
- Modelo linear e sequencial.
- Muito difícil de ser implementado 100% na prática.
- Quando utilizado, nem sempre entrega produtos conforme o esperado pelos usuários.
- Aumenta o risco, pois não há feedbacks durante o processo.

## 3. Processo Incremental
- Passa pelas atividades (Comunicação, Planejamento, Modelagem, Construção e Emprego) e, posteriormente, entrega o incremento.
- Entrega o sistema por partes, o que se tornou mais comum porque os clientes não estão dispostos a esperar a entrega no final, especialmente em sistemas grandes.

## 4. Processo Iterativo
- Seleção do incremento a ser desenvolvido em uma iteração é feita com base em uma lista dos principais riscos.
- Cada iteração produz um executável testado, permitindo verificar a diminuição dos riscos.
- Riscos são diminuídos porque há feedbacks durante o processo, ao contrário do cascata.

> [!CAUTION] OBSERVAÇÃO:
> - O modelo iterativo não necessariamente é incremental. A diferença fundamental é que o iterativo foca na repetição de ciclos com refinamento contínuo, enquanto o incremental foca na entrega de partes funcionais do sistema.

## 5. Modelos Evolucionários
- Caracterizados por contínuas modificações, prazos muito apertados e ênfase na satisfação do cliente-usuário.
- Em muitos casos, o tempo de colocação de um produto no mercado é o requisito mais importante a ser gerenciado.
- Os mais conhecidos são Prototipação e Espiral.
- Desenvolvimento concorrente: define uma série de eventos que disparam transições de estado para cada atividade, ação ou tarefa da engenharia de software.

## 6. Modelo em V
- Variação do modelo cascata que enfatiza a estreita relação entre as atividades de teste e as demais fases do processo.
- Na análise e especificação de requisitos, realiza-se o teste de aceitação.
- No projeto do software (arquitetura), procede-se ao teste de sistema.
- No projeto detalhado, mais próximo da implementação, realizam-se testes de unidade e integração.
- Na implementação, são feitos testes de unidade e integração.

### 6.1 Níveis de Teste
- Teste de unidade: validar o método da classe.
- Teste de integração: avaliar o funcionamento dos componentes internos.
- Teste de sistema: avaliar a funcionalidade dos módulos no hardware.
- Teste de aceitação: envolve o produto como um todo.

> [!CAUTION] OBSERVAÇÃO:
> - Todos os autores utilizam os 4 níveis de teste: unidade, integração, sistema e aceitação.
> - Os processos convencionais têm custo de desenvolvimento maior; os processos ágeis são menores, com diminuição da entrega e rápida validação.

## 7. RAD (Rapid Application Development)
- Modelo incremental que enfatiza o ciclo de desenvolvimento extremamente curto.
- Diferença entre Agile e RAD: O RAD é um processo mais antigo, que lidava com técnicas de programação de 4ª geração (geração de códigos e componentes); o Agile transmite a ideia de rapidez para adaptações.
- Desvantagens: nem todos os tipos de aplicação são apropriados para uso de RAD; quando riscos técnicos são elevados, o RAD não é adequado.

### 7.1 Etapas do RAD
- Modelagem do negócio: fluxo de informação entre as funções do negócio é modelado.
- Modelagem dos dados: o fluxo de informação é refinado num conjunto de objetos.
- Modelagem do processo: os objetos de dados são transformados para conseguir o fluxo de informação necessário para implementar uma função de negócio.
- Geração da aplicação: considera o uso de técnicas de quarta geração (4GL); trabalha para reusar componentes ou criar programas reusáveis.
- Teste e entrega: os componentes novos devem ser testados e todas as interfaces exaustivamente exercitadas.

> [!CAUTION] OBSERVAÇÃO:
> - Riscos técnicos indicam incertezas na tecnologia.

## 8. Processo Unificado
- Modelo de processo genérico com 4 fases:
  - Concepção: atividades de comunicação e planejamento.
  - Elaboração: atividades de planejamento e modelagem.
  - Construção: atividades de construção.
  - Transição: atividades de emprego.

## 9. RUP (Rational Unified Process)
- Possui 6 disciplinas da engenharia de software:
  - Modelagem de negócios.
  - Requisitos.
  - Análise e design (projeto do software).
  - Implementação.
  - Teste.
  - Implantação.
- Possui 3 atividades de apoio:
  - Gerenciamento de configuração e mudança.
  - Gerenciamento de projeto.
  - Ambiente.

> [!TIP] DICAS:
> - As etapas de Iniciação, Elaboração, Construção e Transição são atividades do RUP, que foi derivado do processo unificado.
> - A modelagem de negócios, por exemplo, ocorre muito mais na fase de iniciação e elaboração; na construção diminui; na transição praticamente não acontece (gráfico de baleias).

## 10. Mais Alguns Modelos
- Desenvolvimento baseado em componentes: incorpora técnicas de tecnologias orientadas a objetos no modelo espiral.
- Modelo de métodos formais: conjunto de atividades que determinam uma especificação matemática; busca eliminar problemas de outros modelos com análise matemática, não de forma ad hoc.
- Técnicas de quarta geração: especificação em linguagem natural onde o código fonte é gerado automaticamente a partir dessas especificações.

## 11. Resumo dos Modelos de Processos
- Modelo cascata: linear.
- Modelo de prototipação.
- Modelo iterativo.
- Modelo incremental (RAD).
- Processo unificado (RUP).
- Modelos evolucionários (iterativo e incremental).

> [!CAUTION] OBSERVAÇÃO:
> - Os processos devem ser adaptados à realidade implementada.
> - Os modelos sequenciais pressupõem que o sistema é entregue completo, após a realização de todas as atividades de desenvolvimento.