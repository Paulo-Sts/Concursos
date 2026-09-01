# Engenharia de Software - Pontos de Função 2

## 1. Nesma (Netherlands Software Metrics Users Association)
- Associação fundada em 12 de maio de 1989 na Holanda, originalmente chamada de NEFPUG (Netherlands Function Point Users Group).
- Em 1995, passou a se chamar NESMA (Netherlands Software Metrics Users Association).
- É um dos maiores grupos de usuários de pontos por função da Europa.
- Utiliza filosofia, conceitos, termos e regras muito parecidos com os do IFPUG, mas com algumas diretrizes diferentes.
- Possui seu próprio manual de contagem desde 1990 (atualmente na versão 2.2.1), com forma de contagem bem próxima à do manual do IFPUG.
- Usa a classificação de complexidades do IFPUG (baixa, média e alta).

> [!CAUTION] OBSERVAÇÃO: 
> - A NESMA reconhece três tipos de contagem de pontos de função (detalhada, estimativa e indicativa), sendo esse seu grande diferencial.

## 2. Os Três Tipos de Contagem de Pontos de Função da Nesma

### 2.1 Contagem Detalhada
- É a contagem usual de pontos de função.
- Realizada da seguinte forma:
  - Determina-se todas as funções de todos os tipos (ALI, AIE, EE, SE, CE);
  - Determina-se a complexidade de cada função (baixa, média, alta);
  - Calcula-se o total de pontos de função não ajustados.

### 2.2 Contagem Estimativa
- Realizada em uma etapa na qual o software ainda não está totalmente finalizado.
- Determina-se todas as funções de todos os tipos (ALI, AIE, EE, SE, CE).
- Toda função do tipo dado (ALI, AIE) tem sua complexidade funcional avaliada como baixa.
- Toda função transacional (EE, SE, CE) é avaliada como de complexidade média.
- Isso ocorre porque ainda não existem os requisitos detalhados.
- Com dados empíricos, estima-se que sua precisão é bem razoável, cerca de 40%.
- Calcula-se o total de pontos de função não ajustados.
- A única diferença em relação à contagem usual é que a complexidade funcional não é determinada individualmente para cada função, mas pré-definida para todas elas.

> [!TIP] DICAS: 
> - Na contagem estimativa, as funções de dados (ALI e AIE) são sempre consideradas de complexidade BAIXA.
> - As funções transacionais (EE, SE e CE) são sempre consideradas de complexidade MÉDIA.
> - A precisão estimada é de cerca de 40%.

### 2.3 Contagem Indicativa
- É usada no início do projeto, quando os requisitos ainda estão pouco claros.
- Determina-se apenas a quantidade das funções do tipo dado (ALIs e AIEs).
- Calcula-se o total de pontos de função não ajustados da aplicação da seguinte forma:
  - Tamanho indicativo (PF) = 35 x Número de ALIs + 15 x Número de AIEs.
- Esta estimativa é baseada somente na quantidade de arquivos lógicos existentes (ALIs e AIEs).
- Baseia-se na premissa de que existem aproximadamente:
  - 3 EEs (para adicionar, alterar e excluir dados do ALI);
  - 2 SEs;
  - 1 CE na média para cada ALI.
  - Aproximadamente 1 SE e 1 CE para cada AIE.
- A contagem indicativa pode ser feita apenas com uma especificação superficial.
- Por isso, apenas as funções de dados são contadas.

> [!TIP] DICAS: 
> - A contagem indicativa da NESMA é também conhecida no mundo como "método holandês".
> - Fórmula: PF = 35 x ALI + 15 x AIE.
> - Para realizar uma contagem estimativa, são necessárias informações a respeito das funções transacionais, portanto, requisitos do usuário mais detalhados.

## 3. Em Que Fase Utilizar Cada Tipo de Contagem?
- As contagens indicativa e estimada foram idealizadas pela NESMA para serem utilizadas em etapas iniciais do ciclo de vida de desenvolvimento do sistema, onde ainda não existem definições detalhadas dos requisitos da aplicação.
- A contagem detalhada de pontos de função é mais exata que a contagem estimativa e indicativa, mas consome mais tempo e necessita de especificações mais detalhadas.

> [!CAUTION] OBSERVAÇÃO: 
> - A NESMA reconhece os três tipos de contagem (detalhada, estimativa e indicativa), e não apenas a estimativa e a indicativa, como alguns podem pensar.

## 4. Tabela de Complexidades e Pesos (IFPUG)
| PARÂMETRO DE MEDIÇÃO | SIMPLES | MÉDIO | COMPLEXO |
|---|---|---|---|
| Entradas do usuário | 3 | 4 | 6 |
| Saídas do usuário | 4 | 5 | 7 |
| Consultas do usuário | 3 | 4 | 6 |
| Número de arquivos | 7 | 10 | 15 |
| Interfaces externas | 5 | 7 | 10 |

> [!TIP] DICAS: 
> - Os pesos da tabela acima são utilizados para calcular a Contagem_Total (soma dos pontos de função não ajustados).
> - A fórmula geral para o cálculo de pontos de função é: FP = Contagem_Total x [0,65 + 0,01 x Σ(Fi)], onde Σ(Fi) é a soma dos 14 fatores de ajuste de complexidade.