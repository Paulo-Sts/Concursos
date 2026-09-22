# Engenharia de Software - Estágio de Teste 5

## 1. Classificação Geral dos Estágios de Teste
- O processo de teste é segmentado em três grandes estágios fundamentais, cada um com justificativas e tipos específicos de execução.

| ESTÁGIO | JUSTIFICATIVA | TIPO | COMO FUNCIONA? |
|---|---|---|---|
| Desenvolvimento | Ocorre durante a construção para descobrir bugs e defeitos | Unitário, componentes e sistema | Teste de unidades individuais, interfaces de componentes e do sistema completo integrado. |
| Release | Equipe independente testa versão completa antes da liberação | Requisitos, cenário e desempenho | Valida requisitos, utiliza cenários de uso real e analisa consumo de recursos e tempo de resposta. |
| Usuário | Usuários ou potenciais usuários testam o sistema | Alfa, beta e aceitação | Testes no local do desenvolvedor, em ambiente real ou formalização de aceite pelo cliente. |

## 2. Estratégias de Caixa-preta e Caixa-branca
- As estratégias definem a forma como o testador interage com o software, podendo focar na lógica interna ou no comportamento externo.
- Teste de caixa-preta: foca em verificar se o sistema atende aos requisitos e é bom o suficiente para uso externo (teste de validação).
- Teste de caixa-branca: busca verificar o comportamento interno do software, analisando diretamente os elementos relacionados ao código-fonte.
- O teste funcional é predominantemente caixa-preta, pois se preocupa em validar a funcionalidade, entrada e saída sem olhar o código.

> [!TIP] DICAS: 
> - Teste funcional ⟶ foca na lógica de negócio descrita nos documentos de requisitos.
> - Teste de caixa-branca ⟶ foca na lógica interna de processamento e estruturas de dados dentro de um componente.

## 3. Teste de Regressão e Automação
- Consiste na reexecução de testes anteriores para verificar se alterações ou correções no programa não introduziram novos bugs em funcionalidades que já estavam prontas.
- Pode ser aplicado em cima de testes unitários ou de integração.
- Em testes automatizados, os casos de teste são codificados em programas executados a cada nova versão do sistema em desenvolvimento.

> [!CAUTION] OBSERVAÇÃO: 
> - O teste unitário nem sempre é executado pelo programador que escreveu o código; ele pode ser feito por testadores ou através de ferramentas automatizadas.

## 4. Teste de Release e Performance
- O teste de release visa demonstrar que o sistema implementou adequadamente seus requisitos para ser entregue ao cliente.
- Teste baseado em requisitos: considera cada requisito individualmente para derivar um conjunto de testes correspondente.
- Teste de cenário: cria situações típicas de uso real para desenvolver os casos de teste.
- Teste de desempenho (performance): analisa critérios ligados ao consumo de recursos de processamento, memória e tempo de resposta.

### 4.1 Diferenciação de Carga e Estresse
- Teste de carga: projetado para assegurar que o sistema processe a carga de trabalho prevista, como 300 usuários simultâneos.
- Teste de estresse: foca nos limites do sistema para demonstrar o atendimento aos requisitos e descobrir defeitos através da sobrecarga.

## 5. Teste de Usuário e Aceitação
- Envolve a participação direta dos usuários finais para validar se o sistema atende às suas necessidades reais de trabalho.
- Teste alfa: usuários trabalham com a equipe de desenvolvimento no local do desenvolvedor.
- Teste beta: release antecipado e por vezes inacabado disponibilizado para avaliação externa pelos usuários.
- Teste de aceitação: processo formal onde o cliente decide se o sistema deve ser aceito ou se exige desenvolvimento adicional.

> [!CAUTION] OBSERVAÇÃO: 
> - No teste de usuário, o cliente principal (ex.: um juiz federal) pode enviar um representante para realizar os testes caso não possua disponibilidade.
> - O teste de aceitação frequentemente avalia critérios de usabilidade.

## 6. Modelo V
- O modelo V é um processo derivado do modelo em cascata que estabelece uma relação direta entre as fases de desenvolvimento e os níveis de teste.

### 6.1 Relações de Validação no Modelo V
- Modelagem de requisitos ⟶ Validada pelo teste de aceitação.
- Projeto da arquitetura ⟶ Validado pelo teste do sistema.
- Projeto dos componentes ⟶ Validado pelo teste de integração.
- Geração de código ⟶ Validada pelo teste de unidades.

> [!TIP] DICAS: 
> - Um teste bem-sucedido é aquele que identifica defeitos no software.
> - Casos de teste são compostos pela especificação das entradas e pela saída esperada do sistema.