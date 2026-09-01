# Itil 4 Práticas 3

## 1. Gerenciamento de Talento e Força de Trabalho
- O propósito desta prática é garantir que a organização possua as pessoas certas, com habilidades e conhecimentos adequados, ocupando os papéis corretos para suportar os objetivos de negócio.
- Abrange um conjunto amplo de atividades focadas no engajamento eficaz com os funcionários, incluindo:
  - Planejamento;
  - Recrutamento;
  - Integração (onboarding);
  - Aprendizado e desenvolvimento;
  - Medição de desempenho;
  - Planejamento de sucessão.
- A lógica central consiste em contratar e manter os profissionais alocados em atividades estritamente compatíveis com seu perfil profissional.

> [!CAUTION] OBSERVAÇÃO: 
> - O gerenciamento de talento e força de trabalho é classificado como uma prática geral de gerenciamento, e não como uma prática de gerenciamento técnico.

## 2. Gerenciamento de Disponibilidade
- Esta prática visa garantir que os serviços forneçam os níveis de disponibilidade acordados para atender às necessidades dos clientes e usuários.
- Disponibilidade é definida como a capacidade de um serviço de TI ou de outro item de configuração de desempenhar sua função acordada quando necessário.
- A disponibilidade de um serviço depende diretamente de dois fatores fundamentais:
  - Com que frequência o serviço falha;
  - Quão rapidamente o serviço se recupera após uma falha.

### 2.1 Indicadores de Disponibilidade
- Para verificar se a disponibilidade atende aos requisitos, utilizam-se indicadores de desempenho específicos.
- O MTBF não representa um tempo máximo de funcionamento, mas sim uma média aritmética das ocorrências em um período.
- O MTTR (ou MTRS) é calculado através da soma do tempo total utilizado nos reparos dividida pelo número de reparos realizados.
- Exemplo de cálculo de MTTR: se um equipamento teve 30 horas de manutenção em 5 falhas no período ⟶ MTTR de 6 horas.

| INDICADOR | SIGNIFICADO | DESCRIÇÃO |
|---|---|---|
| MTBF | Mean Time Between Failures | Tempo médio entre falhas que mede a frequência de interrupções |
| MTRS ou MTTR | Mean Time to Restore Service | Tempo médio para reparar ou restaurar o serviço após uma falha |

> [!CAUTION] OBSERVAÇÃO: 
> - Em provas, é comum a tentativa de inverter os conceitos: o MTBF mede a frequência de falhas, enquanto o MTTR mede a rapidez da restauração.

## 3. Análise de Negócio
- O propósito é analisar um negócio ou seus elementos, definir necessidades associadas e recomendar soluções para resolver problemas, facilitando a criação de valor.
- Existe uma relação estreita entre a análise de requisitos e a definição de soluções para as partes interessadas.
- Os requisitos são divididos em duas categorias principais:
  - Requisitos de utilidade: requisitos funcionais definidos pelo cliente e específicos para um produto;
  - Requisitos de garantia: geralmente são requisitos não funcionais coletados como entradas de stakeholders e outras práticas.

> [!CAUTION] OBSERVAÇÃO: 
> - A análise de negócios é uma prática específica da Itil 4, não devendo ser confundida com uma atividade genérica do modelo de quatro dimensões.

## 4. Gerenciamento de Capacidade e Desempenho
- Garante que os serviços alcancem o desempenho esperado, atendendo à demanda atual e futura de maneira eficiente em termos de custo.
- O desempenho é uma medida do que é entregue por um sistema, pessoa, equipe, prática ou serviço.
- A prática exige o dimensionamento adequado para evitar dois extremos negativos:
  - Desperdício de recursos por superdimensionamento imediato;
  - Incapacidade de atender ao crescimento projetado da demanda.
- O controle da entrega de capacidade deve considerar tanto o presente quanto o planejamento para o futuro.

> [!TIP] DICAS: 
> - A adoção de novas tecnologias, como soluções em nuvem, é uma estratégia desta prática para aprimorar o desempenho e atender níveis de capacidade exigidos de forma eficaz.

## 5. Controle de Mudança
- O objetivo é maximizar o número de mudanças bem-sucedidas em serviços e produtos através da avaliação de riscos e autorização de implementações.
- Mudança é definida como a adição, modificação ou remoção de qualquer coisa que possa ter efeito direto ou indireto sobre os serviços.
- Esta prática possui relação estreita com a gestão de riscos, gerenciamento de projetos e gerenciamento de configuração, não sendo realizada de forma isolada.

### 5.1 Tipos de Mudança
- No Itil 4, as mudanças são categorizadas em três tipos principais, cada uma com um modelo de gestão específico.
- O Change Advisory Board (CAB) atua como um comitê de controle que avalia as requisições de mudança (RFC) aceitas ou rejeitadas.

| TIPO DE MUDANÇA | CARACTERÍSTICAS | REQUISITO DE AUTORIZAÇÃO |
|---|---|---|
| Mudança Padrão | Baixo risco, bem documentada e repetitiva | Pré-autorizada, dispensa aprovações adicionais |
| Mudança Normal | Precisa ser agendada e avaliada formalmente | Requer autorização seguindo o processo formal |
| Mudança de Emergência | Implementada rapidamente para resolver incidentes críticos | Autorização imediata ou processo acelerado |

> [!CAUTION] OBSERVAÇÃO: 
> - As mudanças padrão são as únicas que dispensam autorizações adicionais para execução por já serem pré-aprovadas.