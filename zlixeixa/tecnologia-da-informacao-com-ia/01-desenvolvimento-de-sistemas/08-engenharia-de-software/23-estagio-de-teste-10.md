# Engenharia de Software - Estágio de Teste 10

## 1. Ciclo de Vida de um Defeito
- Consiste nos estágios por meio dos quais um defeito é identificado, resolvido e verificado até sua conclusão final.
- O processo inicia com a descoberta de um novo defeito (new status), seguido pela sua abertura (open) e atribuição a um responsável técnico (assigned).
- Se for confirmado como um problema real, o defeito segue para correção (fixed); caso contrário, pode ser rejeitado (rejected).
- Após a correção, o defeito deve ser verificado (to be verified) para garantir que foi devidamente sanado.
- Se a correção for validada com sucesso, o defeito é encerrado (verified/closed); caso o problema persista, ele deve ser reaberto (re-opened) para novo ciclo.

| ESTÁGIO | DESCRIÇÃO |
|---|---|
| New | Defeito recém-descoberto no sistema. |
| Open | O defeito foi aberto para análise. |
| Assigned | Um responsável foi designado para a correção. |
| Fixed | O erro foi corrigido pelo desenvolvedor. |
| To be verified | O defeito aguarda validação pela equipe de testes. |
| Verified/Closed | A correção foi confirmada e o item fechado. |

## 2. Definições de Erro, Defeito e Falha
- Erro (error): caracteriza-se pela diferença entre o resultado obtido e o resultado esperado, originado geralmente por falha humana.
- Defeito (fault): representa a manifestação física de um erro no código ou em um documento, podendo acarretar uma falha futura.
- Falha (failure): ocorre quando o software deixa de cumprir seu objetivo ou requisito, podendo ou não gerar uma exceção visível.

| CONCEITO | NATUREZA | CONSEQUÊNCIA |
|---|---|---|
| Erro | Humana ou sistêmica | Gera um defeito. |
| Defeito | Manifestação do erro | Pode acarretar uma falha. |
| Falha | Evento externo | Software não atende ao objetivo. |

> [!CAUTION] OBSERVAÇÃO: 
> - A regra 10 de myers estabelece que o custo para corrigir um defeito tende a aumentar progressivamente quanto mais tarde ele for encontrado no ciclo de vida.
> - Defeitos encontrados nas fases iniciais do projeto são significativamente mais baratos do que aqueles detectados em produção.

## 3. Estratégias de Teste
- As estratégias definem o momento e a forma como a equipe de qualidade será integrada ao fluxo de desenvolvimento de software.

### 3.1 Estratégia Reativa
- Caracteriza-se pelo envolvimento tardio da equipe de testes, geralmente após a conclusão da análise e do projeto do sistema.
- Exige que os testadores explorem as funcionalidades de forma livre devido à falta de envolvimento prévio no planejamento.
- Os testes exploratórios são o pilar desta estratégia, baseando-se na experiência dos testadores para executar diversas possibilidades de avaliação.

### 3.2 Estratégia Preventiva
- Ocorre quando a equipe de testes é envolvida desde o início do desenvolvimento do software.
- Envolve o planejamento precoce e a especificação de atividades de teste logo nas fases iniciais.
- Contribui para a redução de custos e retrabalho, pois identifica bugs de especificação e projeto antes da codificação.
- Aplica técnicas como revisão e análise estática para prevenir a ocorrência de defeitos em tempo de execução.

| ESTRATÉGIA | FOCO | RESULTADO |
|---|---|---|
| Reativa | Testes exploratórios tardios | Maior custo e risco de retrabalho. |
| Preventiva | Planejamento inicial e revisão | Otimização e redução de custos. |

## 4. Artefatos de Teste
- Representam o conjunto de documentos e registros necessários para a gestão da qualidade.
- Estratégia de testes: documento de alto nível que define objetivos, diretrizes, requisitos, responsabilidades, níveis de teste e riscos.
- Plano de teste: detalha o escopo futuro, a abordagem técnica, os recursos necessários e os critérios de saída para conclusão.
- Outros artefatos comuns incluem o cenário de teste, os casos de teste, a matriz de rastreamento e o relatório de testes.

## 5. Ferramenta Sonar
- Consiste em uma plataforma de código aberto voltada para a inspeção contínua da qualidade do código-fonte.
- Realiza revisões automáticas por meio de análise estática para detectar bugs, códigos cheiros (code smells) e vulnerabilidades.
- Gera relatórios dinâmicos que fornecem feedback imediato sobre a qualidade do produto produzido.

> [!TIP] DICAS: 
> - O sonar é uma ferramenta de análise estática ⟶ permite avaliar a qualidade do código sem a necessidade de executar o programa.