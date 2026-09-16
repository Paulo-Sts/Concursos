# PMBOK 7ª Edição: Domínio de Desempenho do Planejamento 3

## 1. Cronogramas
- Consistem em um modelo para a execução das atividades do projeto, incluindo durações, dependências e outras informações de planejamento.
- O planejamento do cronograma pode utilizar abordagens preditivas ou adaptativas.

## 2. Abordagem Preditiva
- Segue um fluxo estruturado de cinco passos para a construção do cronograma:
  - Passo 1 ⟶ Decompor o escopo do projeto em atividades;
  - Passo 2 ⟶ Sequenciar as atividades;
  - Passo 3 ⟶ Estimar esforço, duração, pessoas e recursos necessários;
  - Passo 4 ⟶ Alocar pessoas e recursos com base na disponibilidade;
  - Passo 5 ⟶ Ajustar a sequência, estimativas e recursos até alcançar um cronograma acordado.

> [!CAUTION] OBSERVAÇÃO: 
> - O planejamento é considerado um processo de refinamento constante.

## 3. Abordagem Adaptativa
- Utiliza o planejamento incremental baseado em iterações e liberações.
- É desenvolvido um plano de liberação de alto nível indicando características e funcionalidades básicas.
- Dentro de cada liberação ocorrem duas ou mais iterações.
- Utiliza janelas de tempo pré-determinado, conhecidas como timebox.

## 4. Diagrama de Rede do Cronograma
- Representação esquemática dos relacionamentos lógicos entre as atividades do cronograma.
- Permite a visualização da sequência de elementos terminais e suas dependências.
- Os números no diagrama representam a duração e as setas indicam as dependências.

## 5. Método do Caminho Crítico
- O Critical Path Method (CPM) é utilizado para estimar a duração mínima do projeto.
- Representa a sequência de atividades que compõe o caminho mais longo do diagrama de rede.
- Determina a menor duração possível para a conclusão do projeto.
- As atividades que compõem este caminho não podem sofrer atrasos, sob pena de comprometer o prazo final.

> [!CAUTION] OBSERVAÇÃO: 
> - A folga livre é a quantidade de atraso permitida sem prejudicar a data da entrega.
> - Em projetos adaptativos, o caminho crítico continua sendo o caminho do diagrama de rede, e não a sequência de maior valor para o cliente.
> - Diferente do PERT, o CPM possui uma abordagem determinística e não probabilística.

## 6. Dependências do Cronograma
- Obrigatórias ⟶ Exigidas legalmente, contratualmente ou inerentes à natureza da atividade;
- Arbitradas ⟶ Definidas pela equipe do projeto com base em experiências anteriores;
- Externas ⟶ Envolvem relações entre atividades do projeto e atividades fora dele, geralmente além do controle da equipe;
- Internas ⟶ Dependências de precedência entre atividades sob controle da equipe do projeto.

## 7. Técnicas de Estimativa e Simulação
- PERT (Program Evaluation Review Technique) ⟶ Descobre a duração baseando-se em três estimativas: otimista (O), pessimista (P) e mais provável (MP).
- É uma abordagem probabilística que utiliza a fórmula: PERT = (O + 4MP + P) / 6.
- Simulação de Monte Carlo ⟶ Ferramenta de simulação que permite calcular o percentual de probabilidade de um evento acontecer.

## 8. Compressão de Cronograma
- Técnicas utilizadas para reduzir o tempo total do projeto:
  - Compressão (Crashing) ⟶ Adição de recursos, o que implica em aumento de custos;
  - Paralelismo (Fast-track) ⟶ Realização simultânea de atividades antes planejadas como sequenciais, aumentando o risco de retrabalho.

### Tabela de Comparação de Técnicas
| TÉCNICA | CARACTERÍSTICA PRINCIPAL | IMPACTO PRIMÁRIO |
|---|---|---|
| Crashing | Adição de recursos | Aumento de custos |
| Fast-track | Execução paralela | Aumento de riscos |
| Pert | Média ponderada | Estimativa probabilística |
| Cpm | Caminho mais longo | Duração mínima do projeto |

> [!TIP] DICAS: 
> - O Crashing geralmente envolve aumentar o número de trabalhadores e máquinas para recuperar atrasos.
> - Em abordagens adaptativas, os itens do topo do backlog devem ser mais refinados para caberem no timebox da sprint.