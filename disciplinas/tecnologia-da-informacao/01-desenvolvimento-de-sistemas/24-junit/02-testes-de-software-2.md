# Testes de Software 2

## 1. Teste de Integração
- Tipo de teste que verifica as interfaces e interações entre diferentes módulos do sistema.
- Inclui dependências reais como banco de dados, arquivos ou APIs externas.
- Foca nos problemas associados ao projeto do software.
- Testa as interfaces entre os componentes ou interações de diferentes partes de um sistema.
- Contribui para a avaliação da existência de erros associados às interfaces do sistema após a realização dos testes unitários.

> [!TIP] DICAS:
> - O teste de integração é o responsável por verificar a comunicação entre módulos e dependências externas (banco de dados, APIs, arquivos).
> - É realizado após os testes unitários.

> [!CAUTION] OBSERVAÇÃO:
> - Diferente do teste unitário que testa partes isoladas, o teste de integração verifica a comunicação entre essas partes.
> - Os testes devem ser realizados primeiro nos componentes individuais (unitários) e depois no sistema como um todo (integração). A ordem inversa está errada.

## 2. Teste de Desempenho
- Visa assegurar que o software possa realizar seu processamento de acordo com a carga pretendida.
- O teste de carga é um tipo de teste de desempenho que determina como a aplicação responderá a várias condições de carga.

> [!TIP] DICAS:
> - O objetivo específico do teste de desempenho é verificar o comportamento do software sob determinada carga de processamento.
> - Teste de carga = verifica resposta da aplicação em diferentes condições de carga.

## 3. Teste Unitário
- Testes automatizados que verificam o comportamento de pequenas unidades do sistema (menores partes testáveis).
- Validam partes individuais do código-fonte isoladamente para assegurar que cada unidade funciona conforme o esperado.
- Verificam a integridade das funções e classes que compõem o software.
- Procuram aferir a corretude do código em sua menor fração.

### 3.1 Para que Servem os Testes Unitários
| OBJETIVO | DESCRIÇÃO |
|---|---|
| Verificar | Se pequenas partes do código funcionam corretamente |
| Identificar | Erros rapidamente |
| Evitar | Regressões |
| Documentar | O comportamento esperado do código |
| Facilitar | Refatorações |
| Aumentar | A segurança na manutenção |
| Reduzir | Testes manuais repetitivos |
| Melhorar | A qualidade do projeto |
| Apoiar práticas | Como Desenvolvimento Orientado a Testes (TDD) |

### 3.2 Características dos Testes Unitários
- Testam unidades individuais de código (métodos, classes, regras de negócio isoladas).
- Não provam que o sistema inteiro está correto.
- São executados de forma automatizada.

> [!TIP] DICAS:
> - Teste unitário = testa a menor parte do código individualmente.
> - É automatizado, rápido e deve ser executado frequentemente.
> - Não elimina a necessidade de outros testes (integração, sistema, aceitação).

> [!CAUTION] OBSERVAÇÃO:
> - Os testes unitários NÃO eliminam revisões de software e testes de aceitação em DevOps.
> - Testes unitários em DevOps garantem um código sempre livre de erros e com integração e deployment contínuos? ERRADO. Eles não eliminam revisões e testes de aceitação.

## 4. Teste de Regressão
- Testes executados novamente para verificar se a adição de novos módulos não provocou erros até então inexistentes.
- Realizados durante testes de integração de módulos de software.

> [!TIP] DICAS:
> - O teste de regressão verifica se mudanças no código introduziram novos defeitos em funcionalidades que já funcionavam.

## 5. Teste de Recuperação
- Consiste em forçar o software a falhar e verificar se a sua recuperação ocorre adequadamente.

> [!TIP] DICAS:
> - Teste de recuperação = simula falhas para verificar a capacidade de recuperação do sistema.