# Engenharia de Software - Estágio de Teste 4

## 1. Teste de Usuário
- Estágio do processo de teste em que usuários ou clientes fornecem entradas e conselhos sobre o teste de sistema.
- Pode envolver um teste formal de um sistema aprovado por fornecedor externo ou um processo informal de experimentação.
- O objetivo é verificar se o software atende às necessidades dos usuários e se estes gostam do produto.
- É considerado um estágio essencial para validar as funcionalidades, mesmo quando testes de release já foram realizados.

### 1.1 Teste Alfa
- Tipo de teste em que os usuários trabalham com a equipe de desenvolvimento no local do desenvolvedor.
- Os usuários são considerados parte do time de desenvolvimento durante este processo.
- Utilizado com frequência no desenvolvimento de produtos vendidos como sistemas-pacote.
- Antecipa informações sobre novas características aos usuários e reduz riscos de mudanças inesperadas nos negócios.
- Métodos ágeis, como o XP, defendem que usuários devem desempenhar papel fundamental no projeto de testes.

### 1.2 Teste Beta
- Um release do software é disponibilizado para usuários experimentarem e levantarem problemas fora do ambiente de desenvolvimento.
- Atualmente é muito utilizado via internet e em aplicativos para celulares para reportar erros e propor melhorias.
- Pode envolver um grupo selecionado de clientes (early adopters) ou ser aberto a qualquer pessoa interessada.
- Essencial para descobrir problemas de interação entre o software e os diversos ambientes reais que os desenvolvedores não podem replicar.
- Funciona também como uma ferramenta de marketing para que os clientes aprendam sobre as capacidades do sistema.

### 1.3 Testes de Aceitação
- Tipo de teste de usuário no qual o cliente testa o sistema de forma formal.
- Serve para decidir se o sistema deve ser aceito pelo fornecedor ou se necessita de desenvolvimento adicional.
- Exemplo: um grupo de usuários finais simula operações de rotina para atestar se o comportamento do sistema está de acordo com as expectativas.

> [!TIP] DICAS: 
> - A sequência lógica para memorizar é: Alfa (interno/com desenvolvedor) ⟶ Beta (externo/ambiente real) ⟶ Aceitação (formal/decisão final).

## 2. Processos e Estratégias de Teste
- O processo de teste geralmente envolve uma combinação de abordagens manuais e automatizadas.

### 2.1 Teste Manual e Automatizado
- Teste manual: o testador executa o programa, compara os resultados com suas expectativas e reporta discrepâncias.
- Teste automatizado: os testes são codificados em programas executados repetidamente a cada nova versão do sistema.
- Testes automatizados são geralmente mais rápidos que os manuais, especialmente em estratégias de regressão.

### 2.2 Teste de Regressão
- Estratégia que consiste em executar novamente testes anteriores para verificar se alterações não introduziram novos bugs.
- Envolve a reexecução de testes unitários e de integração para garantir que nada quebrou após modificações.
- Deve ser realizado sempre que o sistema recebe uma nova funcionalidade ou alteração.

### 2.3 Outros Conceitos de Teste
- Teste Funcional: busca verificar se o sistema segue sua especificação e requisitos sem se preocupar com a estrutura interna.
- Teste de Integração: foca em testar as interfaces entre componentes ou as interações entre diferentes partes do sistema.
- Teste de Unidade: é o primeiro teste realizado na classe e não no módulo; no TDD, o teste é pensado antes da implementação.
- Cobertura de Teste: refere-se ao percentual de alcance dos testes sobre o código do programa.

> [!CAUTION] OBSERVAÇÃO: 
> - O teste funcional é considerado um sinônimo de estratégia caixa-preta por não olhar detalhes de implementação.
> - Testes de regressão não são realizados por clientes para checar funcionalidades, mas sim para validar a estabilidade após mudanças.

### Estágio de Teste de Usuário
| ESTÁGIO | TIPO | FINALIDADE |
|---|---|---|
| Usuário | Alfa, beta e aceitação | Validar funcionalidades e obter o aceite final do cliente. |