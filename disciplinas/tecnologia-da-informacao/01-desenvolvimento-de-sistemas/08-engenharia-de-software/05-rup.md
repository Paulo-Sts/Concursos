# Engenharia de Software - Rup

## 1. Processo Unificado
- Processo de software dirigido a casos práticos, centrado na arquitetura, iterativo e incremental.
- Desenvolvido como uma metodologia para os métodos e ferramentas da UML.
- Ao compreender o conteúdo de UML, será possível projetar o software adequadamente.
- O Processo Unificado é, algumas vezes, chamado de Processo Unificado Racional - RUP em homenagem à Rational Corporation (posteriormente adquirida pela IBM).

> [!TIP] DICAS: 
> - O RUP é um processo voltado à entrega de software.
> - O desenvolvimento ágil não é centrado na arquitetura, e sim em resolver MVP.

## 2. Características
- Usa orientação a objetos em sua concepção.
- Projetado e documentado utilizando a notação UML.
- A UML corresponde a uma linguagem de modelagem que é independente de linguagem de programação e de processos.
- Processo considerado pesado e preferencialmente aplicável a grandes equipes.
- Pelo fato de ser amplamente customizável, torna possível que seja adaptado para projetos de qualquer escala.
- Modular e automatizado.
- Apoiado por ferramentas de desenvolvimento integradas da IBM.

## 3. Métodos Concorrentes do RUP
- Cleanroom (considerado pesado): corresponde à ideia de separar as equipes, cabendo destacar que uma equipe não podia saber do que a outra fazia.
- Métodos Ágeis (leves): Programação Extrema (XP), Scrum, FDD e outros.

## 4. Linhas Mestras
- Gestão de requisitos.
- Uso de arquitetura baseada em componentes.
- Uso de software de modelos visuais.
- Verificação da qualidade do software.
- Gestão e controle de mudanças do software.

> [!CAUTION] OBSERVAÇÃO: 
> - Verificação ≠ Validação.
> - A verificação está relacionada ao processo.
> - A validação está relacionada ao produto.

## 5. Fases
- Linhas mestras são gerais a serem utilizadas ao percorrer o ciclo de vida de um projeto.
- As fases indicam a ênfase que é dada no projeto em um dado instante.
- Para capturar a dimensão do tempo de um projeto, o RUP divide o projeto em quatro fases diferentes.

| FASE | ÊNFASE |
|---|---|
| Iniciação ou Concepção | Escopo do sistema |
| Elaboração | Arquitetura |
| Construção | Desenvolvimento |
| Transição | Implantação |

- Observações sobre as fases:
  - Inception pode ser entendido como Iniciação ou Concepção.
  - Algumas questões fazem essa confusão para tentar levar o candidato ao erro.
  - Seis disciplinas de engenharia de software e três de apoio/suporte.

### 5.1 Gráfico de Baleias
- Responsável por demonstrar a intensidade de uma determinada disciplina.
- Design = projeto.

## 6. Disciplinas de Engenharia de Software
- Modelagem de Negócios.
- Requisitos.
- Análise e Projeto (Design).
- Implementação.
- Teste.
- Implantação.

> [!TIP] DICAS: 
> - A disciplina de teste é executada na fase de elaboração.
> - No processo unificado, requisitos não são a disciplina que demanda maior esforço nas fases de elaboração e construção.

## 7. Disciplinas de Apoio/Suporte
- Configuração e Gerência de Mudança.
- Gerência de Projeto.
- Ambiente.

## 8. Os 4 Ps
- Funcionamento do RUP:
  - As fases são compostas de iterações.
  - As iterações são janelas de tempo.
  - As iterações possuem prazo definido enquanto as fases são objetivas.
  - Todas as fases geram artefatos que serão utilizados nas próximas fases e documentam o projeto, além de permitir melhor acompanhamento.

## 9. Princípios e Melhores Práticas
- Desenvolvimento de software iterativo.
- Gerenciamento de requisitos.
- Uso de arquitetura baseada em componente.
- Modelagem visual de software.
- Verificação da qualidade do software.
- Controle de alteração no software.

## 10. Iterativo e Incremental
- A integração é feita passo a passo durante o processo de desenvolvimento.
- Cada passo limita-se a poucos elementos.
- A integração é menos complexa, reduzindo seu custo e aumentando sua eficiência.
- Partes separadas de projeto e/ou implementação podem ser facilmente identificadas para posterior reuso.
- Mudanças de requisitos são registradas e podem ser acomodadas.
- Os riscos são abordados no início do desenvolvimento.
- Cada iteração permite a verificação de riscos já percebidos, bem como a identificação de novos.
- A arquitetura de software é melhorada através de um exame repetitivo dos artefatos.