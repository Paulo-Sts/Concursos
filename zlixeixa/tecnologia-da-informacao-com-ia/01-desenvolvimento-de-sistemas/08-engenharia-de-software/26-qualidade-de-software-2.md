# Engenharia de Software - Qualidade de Software 2

## 1. Abordagem Tradicional da Qualidade de Software
- O gerenciamento da qualidade fornece uma verificação independente do processo de desenvolvimento de software.
- A equipe de qualidade verifica os resultados do projeto para garantir consistência com os padrões e metas organizacionais.
- A equipe verifica a documentação do processo, que registra as tarefas concluídas por cada time do projeto.
- A documentação permite verificar se tarefas importantes não foram esquecidas ou se houve suposições incorretas entre grupos.
- A qualidade de software não é uma atividade separada; ela funciona em conjunto com todo o processo de desenvolvimento.
- A equipe de qualidade gerencia os testes do software antes do lançamento para os clientes.
- Responsabilidades da equipe:
  - Verificar se os testes do sistema fornecem cobertura aos requisitos.
  - Manter registros apropriados do processo de teste.
- A equipe deve ser independente do grupo de desenvolvimento para garantir visão objetiva.
- A independência permite relatar a qualidade sem influência dos problemas de desenvolvimento.

> [!CAUTION] OBSERVAÇÃO: 
> - A independência da equipe de qualidade é fundamental para evitar conflitos de interesse, especialmente em situações de pressão por prazos.

## 2. Plano de Qualidade
- A equipe de gerenciamento da qualidade deve ter responsabilidade sobre toda a organização.
- Deve se reportar à gerência acima do nível do gerente de projeto.
- Exemplo: se o prazo for apertado, o gerente de projeto pode cortar testes; a equipe de qualidade deve verificar esse corte e reportar à alta gerência.
- Se a qualidade ficar sob responsabilidade do gerente de projetos, há tendência de pular etapas para cumprir prazos e orçamento.
- O plano de qualidade deve definir os atributos da qualidade mais importantes para o software em desenvolvimento.
- A qualidade é alcançada quando o plano e o processo são seguidos.

### 2.1 Tópicos para um Plano de Qualidade
- Introdução ao produto:
  - Descrição do produto.
  - Mercado pretendido.
  - Expectativas de qualidade.
- Planos do produto:
  - Datas críticas de lançamento.
  - Responsabilidades do produto.
  - Planos de distribuição e manutenção.
- Descrições dos processos:
  - Processos e padrões de desenvolvimento e serviço a serem utilizados.
- Metas de qualidade:
  - Identificação e justificativa dos atributos críticos de qualidade do produto.
- Riscos e gerenciamento dos riscos:
  - Principais riscos que afetam a qualidade.
  - Ações para resolver esses riscos.

## 3. Qualidade Baseada em Processos
- O gerenciamento tradicional da qualidade baseia-se na suposição de que a qualidade do software está diretamente relacionada à qualidade do processo de desenvolvimento.
- O software é projetado, não manufaturado, tornando a relação entre processo e produto mais complexa.
- Mesmo seguindo o processo, o produto pode não atender aos requisitos do usuário.
- São necessários: processo, produto, verificação e validação.

### 3.1 Fatores que Afetam a Qualidade Independentemente do Processo
- O projeto de software é um processo criativo; habilidades individuais e experiência têm influência significativa.
- Fatores externos:
  - Nova aplicação.
  - Pressão comercial para antecipação do lançamento.
- Quando algo é antecipado, algo é cortado, afetando a qualidade do produto.

> [!TIP] DICAS: 
> - A qualidade não depende apenas do processo; fatores humanos e externos também influenciam o resultado final.

### 3.2 Influência do Processo na Qualidade
- O processo de desenvolvimento tem influência significativa sobre a qualidade.
- Bons processos são mais propensos a levar a software de boa qualidade.
- O gerenciamento e a melhoria da qualidade podem resultar em menos defeitos.
- É difícil avaliar atributos como confiabilidade e manutenibilidade sem uso prolongado do software.
- Há métricas diretas, indiretas e subjetivas.

> [!CAUTION] OBSERVAÇÃO: 
> - A dificuldade de avaliação de atributos como confiabilidade e manutenibilidade sem uso prolongado é uma limitação importante dos modelos de qualidade baseados apenas em processo.

## 4. Padrões de Software
- Capturam a sabedoria organizacional baseada na melhor ou mais adequada prática.
- O conhecimento é adquirido após tentativa e erro; padronizar ajuda a reutilizar experiência e evitar erros.
- Padroniza-se o que já se sabe ser uma boa prática.
- Fornecem um quadro de referência para definir qualidade em um contexto específico.
- Ajudam a dar continuidade quando o trabalho é passado de uma pessoa para outra.
- Garantem que todos os engenheiros adotem as mesmas práticas.
- Reduzem o esforço de aprendizagem ao iniciar novos trabalhos.

> [!TIP] DICAS: 
> - Padrões são especialmente úteis em equipes com alta rotatividade, pois agilizam a adaptação de novos membros.

### 4.1 Padrões de Produto
- Aplicam-se ao produto de software que está sendo desenvolvido.
- Incluem:
  - Padrões de documento: estrutura de documentos de requisitos.
  - Padrões de documentação: cabeçalho de comentário padrão para definição de classe.
  - Padrões de codificação: definem como uma linguagem de programação deve ser usada.

### 4.2 Padrões de Processo
- Definem os processos a serem seguidos durante o desenvolvimento.
- Devem encapsular boas práticas de desenvolvimento.
- Incluem:
  - Definições de processos de especificação, projeto e validação.
  - Ferramentas de apoio a processos.
  - Descrições dos documentos a serem escritos durante os processos.

### 4.3 Exemplos de Padrões de Produto e Processo
| PADRÕES DE PRODUTO | PADRÕES DE PROCESSO |
|---|---|
| Formulário de revisão de projeto (design) | Conduta para revisão de projeto (design) |
| Estrutura de documentos de requisitos | Submissão de novo código para construção do sistema |
| Formato de cabeçalho de método | Processo de lançamento de versão (release) |
| Estilo de programação em Java | Processo de aprovação do plano de projeto |
| Formato de plano de projeto | Processo de controle de mudança (cvs) |
| Formulário de solicitação de mudança | Processo de registro de teste |

### 4.4 Adaptabilidade dos Padrões
- Diferentes tipos de software precisam de processos de desenvolvimento diferentes.
- Os padrões devem ser adaptáveis a cada projeto.
- Não há vantagem em prescrever uma maneira particular de trabalhar se for inapropriada.
- Estabelecer um padrão inadequado pode trazer desvantagens ou prejuízos.

> [!CAUTION] OBSERVAÇÃO: 
> - A rigidez excessiva na aplicação de padrões pode ser prejudicial; a adaptabilidade é essencial para atender às necessidades específicas de cada projeto.