# Engenharia de Software - Estágio de Teste 6

## 1. Modelo V de Teste de Software
- Fornece uma forma de visualizar como as ações de verificação e validação são aplicadas ao trabalho de engenharia anterior.
- Descreve a relação entre ações de garantia da qualidade e as atividades de comunicação, modelagem e construção.
- À medida que a equipe desce o lado esquerdo do v, os requisitos básicos do problema são refinados em representações detalhadas e técnicas.
- Ao gerar o código, a equipe se desloca para cima no lado direito, realizando testes que validam cada um dos modelos criados anteriormente.
- O modelo estabelece associações diretas entre os níveis de teste e as fases de desenvolvimento:

| NÍVEL DE TESTE | ATIVIDADE ASSOCIADA | CARACTERÍSTICA |
|---|---|---|
| Unidade | Geração de código | Foca na menor unidade, métodos, funções ou componentes simples. |
| Integração | Projeto dos componentes | Analisa a interação entre componentes à medida que o sistema é construído. |
| Sistema | Projeto da arquitetura | Avalia se os requisitos foram atendidos para o sistema completo ou incremento. |
| Aceitação | Modelagem de requisitos | Conduzido pelo cliente para empregar todos os fatores e funções requisitados. |

## 2. Teste de Unidade
- Avalia o software em relação à sua implementação detalhada para detectar falhas de codificação, algoritmos ou estruturas de dados incorretas.
- O teste é simplificado quando um componente é projetado com alta coesão e implementa apenas uma função.
- Áreas fundamentais examinadas no ambiente de teste de unidade:
- Interface do módulo;
- Estruturas de dados locais;
- Condições de fronteira;
- Caminhos independentes;
- Caminhos de manipulação de erro.
- A interface é testada para assegurar que as informações fluam corretamente para dentro e para fora da unidade de programa.
- Estruturas de dados locais são verificadas para garantir que dados temporários mantenham a integridade durante a execução do algoritmo.
- O uso de caminhos independentes assegura que todas as instruções do módulo sejam executadas pelo menos uma vez.

### 2.1 Manipulação de Erros no Teste Unitário
- Casos de teste devem ser projetados para descobrir falhas devido a computações errôneas, comparações incorretas ou fluxo de controle inadequado.
- Erros potenciais avaliados na manipulação de erro:
- Descrição confusa do erro;
- Incompatibilidade entre o erro apontado e o erro encontrado;
- Intervenção do sistema antes da manipulação do erro;
- Processamento incorreto de condição de exceção;
- Informações insuficientes para localizar a causa da falha.

## 3. Ambiente de Teste de Unidade
- Como componentes não são programas independentes, o teste exige o desenvolvimento de estruturas de suporte.
- Pseudocontrolador (driver): funciona como um programa principal que aceita dados de casos de teste, os passa para o componente e imprime resultados relevantes.
- Pseudocontrolado (stub): representa o módulo ou componente que deve ser testado ou simulado para permitir a execução.

> [!TIP] DICAS: 
> - O teste de unidade não é considerado um teste funcional porque não realiza a implementação de todos os componentes do sistema ⟶ foca exclusivamente nos detalhes técnicos internos.
> - Um teste de unidade bem-sucedido é aquele que consegue identificar defeitos no software.

> [!CAUTION] OBSERVAÇÃO: 
> - Não confunda interface de componente com interface de usuário ⟶ a interface de usuário é a tela de interação, enquanto a de componente permite a comunicação técnica entre módulos.
> - O teste de regressão é a aplicação de testes à versão mais recente para garantir que novos defeitos não surjam em partes já testadas ⟶ o teste de unidade atenta estritamente aos detalhes da unidade individual.
> - De acordo com pressman, o teste nunca termina de fato ⟶ o encargo passa do engenheiro para o usuário final ou o processo acaba quando o tempo ou o dinheiro terminam.