# Engenharia de Software - Estágio de Teste 8

## 1. Teste de Sistema
- Consiste em uma série de diferentes testes cuja finalidade primária é exercitar totalmente o sistema.
- Funciona no sentido de verificar se todos os elementos do sistema foram bem integrados e se executam as funções a eles alocadas.
- Diferencia-se do teste de integração pois este valida o projeto dos componentes, enquanto o teste de sistema foca no projeto da arquitetura e no software como um todo.
- Corresponde à última camada de testes possíveis dentro da engenharia de sistemas.
- No modelo V clássico, o teste de sistema ocorre após a fase de validação.

### 1.1 Tipos de Testes de Sistema
| TIPO | FINALIDADE | FUNCIONAMENTO |
|---|---|---|
| Recuperação | Verificar a correção do retorno após falhas | Força o software a falhar e avalia a reinicialização automática ou o tempo médio de reparo humano (mttr). |
| Segurança | Proteger contra acesso indevido | Verifica se os mecanismos de proteção tornam o custo da invasão maior do que o valor das informações obtidas. |
| Esforço | Colocar o programa em situações anormais | Questiona até que ponto o sistema pode ser forçado até que ocorra uma falha; também conhecido como teste de estresse. |
| Desempenho | Medir conformidade com requisitos não funcionais | Essencial para sistemas em tempo real e embutidos para medir a utilização precisa de recursos como ciclos de processador. |
| Disponibilização | Examinar procedimentos de entrega | Avalia os instaladores que serão usados pelos clientes e toda a documentação de suporte para o usuário final. |

> [!CAUTION] OBSERVAÇÃO: 
> - O teste de segurança não se limita ao software, abrangendo também os equipamentos de infraestrutura que garantem a proteção do ambiente.
> - Em sistemas embutidos ou embarcados, o desempenho é crítico devido à memória limitada e ambientes complexos, tornando inviável o aumento de recursos.

## 2. Processo de Depuração
- Tem como objetivo primordial encontrar e corrigir a causa de um erro ou defeito de software.
- Pode ocorrer de forma automática através de ambientes integrados de desenvolvimento (ide) que capturam erros predeterminados específicos da linguagem.
- Utiliza táticas como a força bruta ou o rastreamento.
- O rastreamento é destinado a depurações automáticas que auxiliam na visualização do código para localizar falhas.

> [!TIP] DICAS: 
> - Para memorizar as camadas de teste e seus focos: unidade ⟶ código; integração ⟶ projeto; validação ⟶ requisitos; sistema ⟶ engenharia de sistemas.

## 3. Estratégias de Teste Caixa-branca
- Também chamado de teste estrutural, foca na lógica interna e na estrutura de controle do programa.
- Inclui métodos específicos para exercitar o fluxo de dados e os caminhos lógicos.

### 3.1 Métodos de Caixa-branca
| MÉTODO | DESCRIÇÃO |
|---|---|
| Caminho básico | Cria casos de teste para exercitar o conjunto básico e garantir que todas as instruções sejam executadas pelo menos uma vez. |
| Condição | Exercita as condições lógicas (variáveis booleanas ou expressões relacionais) contidas em um módulo. |
| Fluxo de dados | Seleciona caminhos de acordo com a localização das definições e dos usos das variáveis no programa. |
| Ciclo | Focaliza exclusivamente a validade das construções de loopings (ciclos simples, aninhados ou conectados). |

> [!CAUTION] OBSERVAÇÃO: 
> - É irreal supor que o teste de fluxo de dados seja usado extensivamente em grandes sistemas; ele deve ser aplicado especificamente em áreas suspeitas do software.
> - A técnica de caminho básico pode ser representada por meio de grafos de fluxos (nós e arestas) ou matrizes de grafos.

## 4. Estratégias de Teste Caixa-preta
- Também conhecido como teste funcional, foca nas funcionalidades, entradas e saídas sem considerar o código interno.

### 4.1 Métodos de Caixa-preta
| MÉTODO | DESCRIÇÃO |
|---|---|
| Baseado em grafo | Cria um grafo de objetos e suas relações para garantir que cada elemento seja exercitado e os erros descobertos. |
| Particionamento de equivalência | Divide o domínio de entrada em classes de dados para reduzir o número total de casos de teste necessários. |

> [!TIP] DICAS: 
> - O particionamento de equivalência divide o domínio de entrada em estados válidos ou inválidos ⟶ a técnica busca definir um caso de teste que descubra classes de erros para aumentar a eficácia.
> - Em vez de testar cada valor individual, selecionam-se alguns valores dentro de cada partição para validar o comportamento do programa.