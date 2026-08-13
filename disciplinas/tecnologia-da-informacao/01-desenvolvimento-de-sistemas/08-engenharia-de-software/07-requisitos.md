# Engenharia de Software - Requisitos

## 1. Engenharia de Requisitos
- É o termo usado para descrever as atividades relacionadas à investigação e definição de escopo de um sistema de software.
- Trata-se de um processo sistemático de desenvolvimento de requisitos por meio de um processo cooperativo de análise, onde os resultados das observações são codificados em uma variedade de formatos e a acurácia das observações é constantemente verificada.
- Consiste no processo de descobrir, analisar, documentar e verificar as funções e restrições do sistema.
- As atividades do processo geram artefatos, como estudo de viabilidade, elicitação e análise de requisitos, especificações de requisitos e validação de requisitos.
- Não se trata de um processo linear, pois existem diversos percalços.
- Um dos problemas da engenharia de software é a falta de utilização dos elementos existentes, o que é agravado quando se eliminam etapas em ambientes que exigem formalismo.

> [!TIP] DICAS:
> - O termo "elicitação" remete à aparição de requisitos.

## 2. Verificação e Validação
- Barry Boehm expressou a diferença entre validação e verificação:
  - Validação: estamos construindo o produto certo?
  - Verificação: estamos construindo o produto da maneira certa?
- A verificação observa se o processo foi seguido, mas apenas seguir o processo não garante o software.
- A validação averigua se o produto a ser construído é o correto.

### 2.1 Verificação
- Examina a especificação do software para assegurar a definição sem ambiguidades, inconsistências ou omissões, detectando e corrigindo possíveis problemas ainda durante a fase de definição dos requisitos.
- O custo da correção de defeitos aumenta na medida em que o processo de desenvolvimento progride.
- Revisões de artefatos de software são uma abordagem eficiente e de baixo custo para encontrar defeitos.
- Modelos de maturidade de processo de software, como o CMMI e o MPS.BR, exigem a condução de revisões.

> [!TIP] DICAS:
> - O ideal é que seja feito um checklist dos requisitos para verificação.

### 2.2 Validação
- O aceite do usuário é negocial, ou seja, o usuário aceita se a funcionalidade atende o que ele procura.
- Se o software não executa as funcionalidades adequadamente, a culpa geralmente recai ao usuário.
- A validação representa a atividade em que se obtém o aceite do cliente sob determinado artefato.
- No cenário de engenharia de requisitos, essa atividade significa aprovar junto ao cliente os requisitos que foram especificados.

> [!CAUTION] OBSERVAÇÃO:
> - A validação está focada no "produto certo", enquanto a verificação está focada no "produto da maneira certa". A verificação não garante a validação.

## 3. Requisitos de Sistema/Software
- São descrições do que o sistema de software deve fazer, os serviços que ele oferece e as restrições do seu funcionamento.
- Demonstram as necessidades dos clientes que servem a uma finalidade determinada.

## 4. Níveis de Requisitos
- Declaração abstrata (alto nível) – requisito de usuário:
  - Linguagem natural (pode ser utilizado diagramas);
  - Descreve o que o sistema deve fornecer aos usuários;
  - Inclui restrições com as quais o sistema deve operar.
- Declaração detalhada (baixo nível) – requisito de sistema:
  - Também chamada de "especificação de requisitos";
  - Define exatamente o que deve ser implementado;
  - Serve para os desenvolvedores.

## 5. Requisitos Funcionais
- Tratam das funcionalidades do sistema, ou seja, o que o sistema deve fazer ou não fazer.
- Descrevem os serviços que devem ser fornecidos.
- Especificam como o sistema deve reagir a entradas específicas.
- Especificam como o sistema deve se comportar em determinadas situações.
- Incluem o que o sistema não deve fazer.

## 6. Requisitos Não Funcionais
- São restrições aos serviços ou funções do sistema.
- Incluem restrições de tempo e no processo.
- Geralmente, aplicam-se ao sistema como um todo.
- Relacionam-se ao uso da aplicação em termos de desempenho, usabilidade, confiabilidade, segurança, disponibilidade, manutenção e tecnologias envolvidas.

> [!CAUTION] OBSERVAÇÃO:
> - Confiabilidade é a confiança dada ao software, o que é diferente de confidencialidade, que está inserida na área da segurança da informação.

### 6.1 Tipos de Requisitos Não Funcionais
- Requisitos de produto: especificam o comportamento do produto.
  - Exemplo: incluem requisitos de desempenho (rapidez e uso de memória), confiabilidade (taxa aceitável de falhas), proteção e usabilidade.
- Requisitos organizacionais: derivados das políticas e procedimentos da organização do cliente e do desenvolvedor.
  - Exemplo: requisitos do processo de desenvolvimento (linguagem de programação, ambiente de desenvolvimento, normas de processo) e requisitos ambientais (ambiente operacional do sistema).
- Requisitos externos: abrangem tópicos advindos de fatores externos ao sistema.
  - Exemplo: requisitos de interoperabilidade, requisitos éticos e requisitos legais (para garantir que o sistema opere de acordo com a lei, como a aprovação por um regulador, ex. banco central).

> [!TIP] DICAS:
> - Um requisito legal pode ser funcional ou não funcional. Se o software executa uma ação que a lei manda, ele é funcional. Se o software opera conforme a lei como um todo, ele é não funcional.

## 7. Requisitos do Projeto
- Requisitos do negócio: descrevem em termos do negócio o que deve ser entregue ou conseguido para fornecer valor.
- Requisitos do produto: descrevem propriedades de um sistema ou produto, que pode ser uma das várias maneiras de satisfazer um conjunto de requisitos de negócio.
- Requisitos do processo: especificam as metodologias específicas que devem ser seguidas e as restrições a que a organização deve obedecer.