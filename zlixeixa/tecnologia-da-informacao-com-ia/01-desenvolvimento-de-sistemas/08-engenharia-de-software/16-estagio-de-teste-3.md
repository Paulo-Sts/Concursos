# Engenharia de Software - Estágio de Teste 3

## 1. Fundamentos do Teste de Release
- O teste de release é o processo de testar uma versão particular de um sistema destinada ao uso fora da equipe de desenvolvimento.
- Geralmente o release do sistema é voltado para o uso de clientes e usuários finais.
- Existem duas diferenças fundamentais entre o teste de release e o teste de sistema realizado no estágio de desenvolvimento:
- Uma equipe separada e independente do desenvolvimento, como uma equipe de homologação, deve ser responsável pela execução;
- O objetivo principal deixa de ser a descoberta de bugs (teste de defeitos) e passa a ser a verificação do atendimento aos requisitos para uso externo (teste de validação).

> [!TIP] DICAS: 
> - O teste de sistema foca em encontrar erros ⟶ o teste de release foca em validar o sistema para o cliente.

## 2. Estratégias de Teste: Caixa Preta e Caixa Branca
- Essas estratégias representam formas de realizar testes aplicáveis a qualquer nível do software.
- A estratégia de caixa preta foca exclusivamente nas saídas, sem observar o processamento interno ou detalhes de implementação.
- A estratégia de caixa branca busca verificar o comportamento interno e permite olhar o código para encontrar novos testes possíveis.
- O teste de release é predominantemente um processo de caixa preta, com testes derivados da especificação do sistema.
- O teste funcional é considerado uma estratégia de caixa preta pois o testador se preocupa apenas com a funcionalidade e não com a implementação.

> [!CAUTION] OBSERVAÇÃO: 
> - O teste unitário pode utilizar estratégia de caixa preta em casos de automação ou quando o foco é o teste de regressão.

## 3. Tipos de Teste no Estágio de Release
- O estágio de release compreende três abordagens principais conforme a estrutura de estágios abaixo:

| ESTÁGIO | TIPO | FINALIDADE |
|---|---|---|
| Desenvolvimento | Unitário, componentes e sistema | Foco em descobrir defeitos. |
| Release | Baseado em requisitos, cenário e desempenho | Foco em validar para uso externo. |
| Usuário | Alfa, beta e aceitação | Foco no gosto do usuário final. |

### 3.1 Testes Baseados em Requisitos
- Consistem em uma abordagem sistemática onde cada requisito do sistema gera um conjunto de testes correspondentes.
- Funcionam como uma validação para demonstrar que o sistema implementou adequadamente o que foi solicitado.
- Devem manter registros de rastreabilidade para ligar cada teste ao seu respectivo requisito.

### 3.2 Testes de Cenário
- Utilizam estórias que descrevem maneiras típicas e realistas de usar o sistema para desenvolver os casos de teste.
- O testador percorre o cenário observando como o software se comporta diante de diferentes entradas.
- Erros deliberados podem ser cometidos para verificar a reação do sistema a falhas, como o uso de chaves de criptografia incorretas.

### 3.3 Testes de Desempenho
- Avaliam propriedades emergentes do sistema totalmente integrado, focando em requisitos não funcionais como confiabilidade e velocidade.
- São projetados para assegurar que o sistema processe a carga de trabalho para a qual foi destinado.
- Ajudam a identificar problemas que podem levar o usuário a pular etapas de segurança caso o sistema seja muito lento.

#### 3.3.1 Diferença Entre Carga e Estresse
- Teste de carga: verifica o comportamento do software dentro dos limites estabelecidos nos requisitos não funcionais.
- Teste de estresse: também conhecido como teste de esforço, submete o sistema a demandas que ultrapassam os limites de projeto para observar sua reação.

> [!TIP] DICAS: 
> - Uma forma eficaz de descobrir defeitos é realizar o teste de estresse ⟶ testar os limites do sistema é mais importante que testar apenas o funcionamento normal.