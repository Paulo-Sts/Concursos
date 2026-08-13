# Engenharia de Software - Requisitos 2

## 1. Engenharia de Requisitos
- É o processo de descobrir, analisar, documentar e verificar serviços e restrições do sistema.
- O termo "requisito" não é usado de forma consistente pela indústria de software.
- Essa inconsistência ocorre devido à diversidade de fontes e autores, já que a engenharia de software e a computação são campos recentes em comparação a outras disciplinas.
- A pluralidade de termos resulta da adoção de técnicas e métodos de diversas outras áreas.
- Em alguns casos, o requisito é apenas uma declaração abstrata de alto nível de um serviço ou restrição.
- No outro extremo, é uma definição detalhada e formal de uma função do sistema.

> [!CAUTION] OBSERVAÇÃO: 
> - Existem algumas classificações de requisitos.

### 1.1 Diferenças nos Níveis de Requisitos
- As diferenças existem porque, em projetos de grande porte com contrato, as necessidades devem ser definidas de forma abstrata para que a solução não seja predefinida.
- Requisitos abstratos permitem que vários contratantes concorram com diferentes soluções.
- Após a adjudicação do contrato, o contratante escreve uma definição mais detalhada para que o cliente entenda e valide o que o software fará.
- Ambos os documentos podem ser chamados de documentos de requisitos do sistema.

## 2. A Importância da Definição de Requisitos
- Segundo Frederick Brooks (responsável pelo OS/360 da IBM e autor de "The Mythical Man-Month"), a parte mais difícil na construção de um sistema de software é decidir o que construir.
- Nenhuma outra parte do trabalho conceitual é tão difícil quanto o estabelecimento dos requisitos técnicos detalhados.
- Nenhuma outra parte mutila o sistema resultante se for feita errada.
- Nenhuma outra parte é tão difícil de corrigir depois.

> [!CAUTION] OBSERVAÇÃO: 
> - Man-Month é uma métrica de esforço de software para desenvolvimento.

### 2.1 Consequências de uma Má Gestão de Requisitos
- A gestão de requisitos e a engenharia de requisitos trazem técnicas para evitar os problemas elencados por Brooks.
- Uma má gestão ou definição inadequada de requisitos pode acarretar custos elevados para o software.
- Isso ocorre pela falta de cumprimento das expectativas ou por problemas mais graves.

### 2.2 Custo da Correção de Bugs
- A maioria dos bugs ocorre devido a problemas na especificação de requisitos.
- Quanto mais tempo levar para identificar um erro ao longo do processo, maior será o custo para a correção.
- O custo para correção de um bug aumenta com o andar do projeto, além de aumentar a dificuldade.

> [!CAUTION] OBSERVAÇÃO: 
> - Trata-se de um gráfico empírico, embasado em estudos da engenharia de software fundamentados em experimentos.

## 3. Visão Tradicional de Requisitos
- Refere-se à visão tradicional, não à de processos ágeis.
- Em processos ágeis, não há um documento de requisitos formal.
- No desenvolvimento ágil, o documento pode se manifestar como histórias de usuário, guias ou um documento de arquitetura, geralmente mais conciso.
- Para sistemas de grande porte, ainda existe uma fase de engenharia de requisitos antes da implementação.
- O resultado é um documento de requisitos, que pode ser parte do contrato de desenvolvimento do sistema.
- Haverá mudanças nos requisitos, e os requisitos de usuário (alto nível) poderão ser ampliados em requisitos de sistema mais detalhados (baixo nível).

> [!CAUTION] OBSERVAÇÃO: 
> - Quando há um contrato com obrigações financeiras, não é viável adotar um processo ágil. A formalização se torna imperativa devido à natureza contratual do processo.

### 3.1 Classificação de Requisitos
- Requisitos de usuário: representam um nível mais elevado.
- Requisitos de sistema: representam um nível mais detalhado (baixo nível).

#### 3.1.1 Exemplo de Requisitos para o Sistema MHC-PMS
- Definição de requisitos de usuário:
  - O MHC-PMS deve gerar relatórios gerenciais mensais que mostrem o custo dos medicamentos prescritos por cada clínica durante aquele mês.
- Especificação de requisitos de sistema:
  - No último dia útil de cada mês deve ser gerado um resumo dos medicamentos prescritos, seus custos e as prescrições de cada clínica.
  - Após 17:30h do último dia útil do mês, o sistema deve gerar automaticamente o relatório para impressão.
  - Um relatório será criado para cada clínica, listando os nomes dos medicamentos, o número total de prescrições, o número de doses prescritas e o custo total dos medicamentos prescritos.
  - Se os medicamentos estão disponíveis em diferentes unidades de dosagem (ex.: 10 mg, 20 mg), devem ser criados relatórios separados para cada unidade.
  - O acesso aos relatórios de custos deve ser restrito a usuários autorizados por uma lista de controle de gerenciamento de acesso.

## 4. Leitores de Diferentes Tipos de Especificação de Requisitos

### 4.1 Leitores de Requisitos de Usuário
- Gerentes clientes;
- Usuários finais do sistema;
- Engenheiros clientes;
- Gerentes contratantes;
- Arquitetos de sistema.

### 4.2 Leitores de Requisitos de Sistema
- Usuários finais do sistema;
- Engenheiros clientes;
- Arquitetos de sistema;
- Desenvolvedores de software.

> [!CAUTION] OBSERVAÇÃO: 
> - Na prática, essas classificações não são rígidas. Um requisito do usuário pode ser tanto funcional quanto não funcional.
> - O usuário tende a pensar apenas nas funcionalidades, enquanto os requisitos não funcionais (disponibilidade, usuários simultâneos) geralmente não são especificados por ele.
> - O engenheiro de software é crucial para garantir que todos os requisitos sejam identificados durante a elicitação.

## 5. Tipos de Requisitos

### 5.1 Requisitos Funcionais (RF) versus Requisitos Não Funcionais (RNF)
- Na prática, no documento de requisitos, é difícil separar os requisitos funcionais dos não funcionais.
- Se apresentados separadamente, os relacionamentos entre eles podem ficar difíceis de entender.
- O custo de verificar RNF pode ser muito elevado, e os clientes podem não achar que os custos sejam justificados.

> [!CAUTION] OBSERVAÇÃO: 
> - Os requisitos não funcionais aplicam-se ao software como um todo.

## 6. Métricas de Requisitos Não Funcionais (RNF)
| PROPRIEDADE | MEDIDA |
|---|---|
| Velocidade | Transações processadas/segundo; Tempo de resposta de usuário/evento; Tempo de atualização de tela |
| Tamanho | Megabytes; Número de chips de memória ROM |
| Facilidade de uso | Tempo de treinamento; Número de frames de ajuda |
| Confiabilidade | Tempo médio para falha; Probabilidade de indisponibilidade; Taxa de ocorrência de falhas |
| Disponibilidade | (medida relacionada à confiabilidade) |
| Robustez | Tempo de reinício após falha; Percentual de eventos que causam falhas; Probabilidade de corrupção de dados em caso de falha |
| Portabilidade | Percentual de declarações dependentes do sistema-alvo; Número de sistemas-alvo |

> [!CAUTION] OBSERVAÇÃO: 
> - A propriedade de facilidade de uso é uma métrica complexa relacionada à usabilidade e constitui uma medida indireta.
> - A usabilidade pode variar conforme o usuário e é bastante subjetiva.

## 7. Documento de Requisitos
- Também chamado de Especificação de Requisitos de Software (SRS, do inglês Software Requirements Specification).
- É uma declaração oficial do que os desenvolvedores do sistema devem implementar.
- Deve incluir tanto os requisitos de usuário quanto uma especificação detalhada dos requisitos de sistema.
- Em alguns casos, os requisitos de usuário e de sistema são integrados em uma única descrição.

> [!TIP] DICAS: 
> - Documentos de requisitos são essenciais quando um contratante externo está desenvolvendo o sistema de software.

### 7.1 Visão dos Métodos Ágeis sobre o Documento de Requisitos
- Métodos ágeis pregam que requisitos mudam tão rapidamente que um documento de requisitos já está ultrapassado assim que termina de ser escrito.
- O esforço é considerado desperdiçado.
- Em vez de um documento formal, abordagens como a Extreme Programming (XP) coletam os requisitos de usuário em cartões como estórias de usuário.
- O usuário prioriza os requisitos, sendo uma boa abordagem para sistemas de negócio com requisitos instáveis.
- Deve ser avaliado se ainda é útil escrever um pequeno documento de apoio com os requisitos de negócio e de confiança (RNF).

> [!CAUTION] OBSERVAÇÃO: 
> - O método ágil utiliza o backlog e histórias de usuário, implementando funcionalidades de forma incremental.
> - Requisitos do Negócio descrevem, em termos do negócio, o que deve ser entregue ou conseguido para fornecer valor.
> - Quando o foco está nos requisitos funcionais dos próximos releases, é fácil esquecer os RNF, que se aplicam ao sistema como um todo.

### 7.2 Usuários de um Documento de Engenharia de Requisitos
- Clientes do sistema: especificam e leem os requisitos para verificar se satisfazem suas necessidades; também especificam alterações.
- Gerentes: usam o documento para planejar uma proposta para o sistema e o processo de desenvolvimento.
- Engenheiros de sistema: usam os requisitos para entender o sistema que será desenvolvido.
- Engenheiros de teste de sistema: usam os requisitos para desenvolver testes de validação do sistema.
- Engenheiros de manutenção de sistema: usam os requisitos para entender o sistema e os relacionamentos entre suas partes.