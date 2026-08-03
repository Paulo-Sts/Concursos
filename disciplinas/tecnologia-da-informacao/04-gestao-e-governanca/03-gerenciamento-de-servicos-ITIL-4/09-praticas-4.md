# Itil 4 Práticas 4

## 1. Gerenciamento de Incidentes
- O propósito desta prática é minimizar o impacto negativo dos incidentes através do restabelecimento da operação normal do serviço o mais rapidamente possível.
- Um incidente é definido como uma interrupção não planejada de um serviço de TI ou uma redução na sua qualidade.
- Os incidentes possuem impacto direto nos usuários ou nos processos de negócio e exigem resolução célere para manter a atividade normal da organização.
- Exemplos de incidentes incluem:
  - Queda total de conexão que impede finalização de transações;
  - Degradação da qualidade do serviço (ex.: conexão lenta).

### 1.1 Swarming no Gerenciamento de Incidentes
- O swarming é uma técnica utilizada para auxiliar no gerenciamento de incidentes.
- Envolve diversos stakeholders trabalhando em conjunto inicialmente no incidente.
- O grupo colabora até que se identifique quem possui a melhor capacidade técnica para seguir com a resolução, permitindo que os demais retornem às suas tarefas habituais.

> [!CAUTION] OBSERVAÇÃO: 
> - O gerenciamento de incidentes não possui relação com a identificação da causa raiz. Seu foco é estritamente operacional e voltado para a restauração do serviço.

## 2. Gerenciamento de Problemas
- O objetivo desta prática é reduzir a probabilidade e o impacto de incidentes através da identificação de suas causas reais e potenciais.
- Os problemas são as causas subjacentes dos incidentes.
- Esta prática gerencia:
  - Erros conhecidos;
  - Soluções temporárias (workarounds).
- A gestão de problemas exige investigação e análise para identificar a causa raiz e recomendar soluções completas de longo prazo para evitar repetições.

### 2.1 Erro Conhecido e Workaround
- Erro conhecido (known error) é um problema que já foi analisado, mas que ainda não foi resolvido pela organização.
- Solução de contorno (workaround) é uma solução temporária e rápida.
- O papel principal do workaround é reduzir ou eliminar o impacto de um problema sem necessariamente resolver a causa raiz de forma imediata.

> [!TIP] DICAS: 
> - Um problema analisado que aguarda priorização para conserto é um erro conhecido. De tempos em tempos, a falha desse erro gerará novos incidentes até que a causa seja eliminada.

## 3. Definições e Diferenciações Técnicas
- Para o sucesso em provas, é fundamental distinguir os termos técnicos que compõem o fluxo de falhas de acordo com a Itil 4.
- A relação lógica segue este fluxo: o erro (defeito) se manifesta ⟶ ocorre uma falha (perda de habilidade) ⟶ gera-se um incidente (impacto no usuário).

| CONCEITO | DEFINIÇÃO |
|---|---|
| INCIDENTE | Interrupção não planejada ou redução da qualidade de um serviço de ti |
| PROBLEMA | Causa de um ou mais incidentes que exige investigação e análise |
| FALHA | Perda da habilidade de operar de acordo com a especificação ou resultado requerido |
| ERRO | Defeito ou vulnerabilidade que causa incidentes |

## 4. Fluxo de Tratamento de Incidentes e Problemas
- O gerenciamento de incidentes e o de problemas são práticas distintas e não foram unificados na Itil 4.
- No fluxo de tratamento, após um incidente ser resolvido com sucesso, a organização pode iniciar:
  - A revisão do incidente;
  - A investigação do problema associado.
- O diagnóstico do incidente busca identificar a melhor solução imediata, enquanto a abertura de chamados para mudanças permanentes é vinculada ao controle de mudanças e não ao diagnóstico em si.

> [!CAUTION] OBSERVAÇÃO: 
> - Não confunda as responsabilidades: o gerenciamento de incidentes restaura o serviço; o gerenciamento de problemas identifica e corrige a causa raiz.
> - A criação de alarmes de indisponibilidade não é função do gerenciamento de problemas, mas sim da prática de gerenciamento de eventos.