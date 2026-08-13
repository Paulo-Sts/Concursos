# Engenharia de Software - Estágio de Teste 2

## 1. Estágios de Testes de Software
- O sistema de software comercial geralmente percorre três estágios fundamentais de teste antes de sua conclusão.
- Os estágios são divididos conforme o momento do ciclo de vida e o responsável pela execução.

| ESTÁGIO | TIPO | FINALIDADE |
|---|---|---|
| Desenvolvimento | Unitário, componentes e sistema | Ocorre durante a construção para descobrir bugs e defeitos. |
| Release | Baseado em requisitos, cenário e desempenho | Equipe independente testa versão completa antes da liberação. |
| Usuário | Alfa, beta e aceitação | Usuários testam o sistema em seu próprio ambiente. |

> [!TIP] DICAS: 
> - As bancas costumam cobrar testes de forma ampla, utilizando nomenclaturas variadas para o mesmo conceito ⟶ é essencial estudar o tema de maneira abrangente.

## 2. Teste em Desenvolvimento
- Realizado primordialmente pelo próprio programador do sistema.
- Pode ser executado através de programação em pares ou revisão em pares, especialmente em metodologias ágeis.
- Em sistemas críticos, o uso de equipes específicas para testes é recomendado.
- O objetivo central é o teste de defeitos para a descoberta de bugs.

### 2.1 Teste Unitário
- Foca no teste individual de unidades de programa ou classes de objetos.
- Deve centrar-se na funcionalidade específica dos objetos ou métodos.
- Representa o processo de testar a menor parte do código-fonte.
- Consiste em realizar chamadas para rotinas utilizando diferentes parâmetros de entrada.
- Exemplo: inserção de um dado incorreto em um validador de CPF para verificar a reação do sistema.

### 2.2 Teste de Componentes
- Ocorre quando várias unidades individuais são integradas para criar componentes compostos.
- O foco principal é o teste das interfaces dos componentes.
- Deve demonstrar que a interface do componente se comporta conforme sua especificação.
- Pressupõe que os testes unitários dos objetos individuais já foram concluídos.
- Identifica erros resultantes das interações entre os objetos, que não seriam detectáveis isoladamente.

### 2.3 Erros de Interface
- Mau uso: ocorre quando um componente chamador utiliza a interface de outro de forma errada, como inverter a ordem de parâmetros.
- Mau entendimento: o componente chamador não compreende a especificação da interface, esperando um comportamento divergente do real.
- Erros de timing: comuns em sistemas de tempo real com memória compartilhada, onde produtor e consumidor operam em velocidades distintas.

### 2.4 Teste de Sistema
- Envolve a integração de alguns ou todos os componentes para testar o sistema como um todo.
- Foca prioritariamente nas interações entre os componentes integrados.
- Segue o modelo tradicional de projetar casos de teste, preparar dados, executar o programa e comparar resultados para gerar relatórios.

> [!CAUTION] OBSERVAÇÃO: 
> - Teste de integração é frequentemente utilizado como sinônimo para teste de componentes pelas bancas de concurso.
> - No nível de desenvolvimento não ocorre o teste de aceitação, pois este exige a participação do usuário.