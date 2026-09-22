# Engenharia de Software - Qualidade de Software 3

## 1. Arcabouço de Padrões ISO 9001
- A ISO 9001 aplica-se a padrões dentro da organização, sendo utilizada por organizações que prestam serviços ou entregam produtos.
- O conjunto internacional de padrões para sistemas de gerenciamento da qualidade em todos os setores é chamado de ISO 9000.
- A ISO 9001 é o mais geral desses padrões e aplica-se a organizações que projetam, desenvolvem e mantêm produtos, incluindo software.
- Foi desenvolvido originalmente em 1987.
- Não é um padrão específico para desenvolvimento de software, mas um arcabouço para o desenvolvimento de padrões de software.
- Estabelece princípios gerais de qualidade, descreve processos de qualidade em geral e define normas e procedimentos organizacionais que devem ser documentados em um manual de qualidade organizacional.

> [!CAUTION] OBSERVAÇÃO:
> - A ISO 9001 não define como fazer software de qualidade, apenas exige que a organização tenha procedimentos documentados e que os siga.

## 2. Certificação ISO 9001
- A certificação ISO 9001 concentra-se em assegurar que a organização tenha procedimentos de gerenciamento da qualidade e que siga esses procedimentos.
- Não há garantia de que empresas certificadas usem as melhores práticas de desenvolvimento de software ou que seus processos levem a software de alta qualidade.
- Algumas pessoas pensam erroneamente que a certificação ISO 9001 significa que a qualidade do software produzido por empresas certificadas será sempre melhor do que a de empresas não certificadas.

### 2.1 Críticas à Certificação ISO 9001
- A certificação define qualidade como conformidade aos padrões, não levando em conta a qualidade experimentada pelos usuários do software.
- Exemplo: Uma empresa poderia definir padrões de cobertura de teste especificando que todos os métodos devem ser chamados pelo menos uma vez. Esse padrão pode ser atendido por testes incompletos, que não incluem testes com diferentes parâmetros de método.
- Contanto que os procedimentos de teste definidos sejam seguidos e os registros sejam mantidos, a empresa poderá ser certificada ISO 9001.

> [!TIP] DICAS:
> - A certificação ISO 9001 = conformidade com procedimentos, não = qualidade do produto final.
> - A ISO 9001 não avalia a eficácia dos testes, apenas se os procedimentos definidos foram seguidos.

## 3. Revisões e Inspeções
- São atividades de garantia da qualidade que verificam a qualidade dos entregáveis do projeto.
- Envolvem verificação do software, documentação e registros de processo para descobrir erros, omissões e violações de padrões.
- A verificação do software refere-se à verificação do processo.
- As revisões de qualidade são baseadas em documentos produzidos durante o processo de desenvolvimento.
- Podem ser revisados: especificações de software, projetos (design), código, modelos de processo, planos de teste, procedimentos de gerenciamento de configuração, padrões de processo e manuais de usuário.
- A revisão deve verificar consistência e completude dos documentos ou código e, se padrões foram definidos, certificar-se de que foram seguidos.

### 3.1 Finalidade
- Melhorar a qualidade do software, não avaliar o desempenho das pessoas no time de desenvolvimento.
- É um processo público de detecção de erros, em comparação com o processo mais privado de teste dos componentes.
- Erros cometidos pelos indivíduos são revelados para todo o time.
- Visão oriental: melhorar o processo para diminuir o erro das pessoas; quanto menos procedimentos manuais, menor a chance de erro.
- Visão ocidental: achar culpados, o que não impede que outra pessoa cometa os mesmos erros.

> [!CAUTION] OBSERVAÇÃO:
> - Revisão não tem caráter punitivo; o foco é encontrar problemas e melhorar o processo.

### 3.2 Revisão de Qualidade vs. Revisão de Progresso
- Revisões de qualidade não são revisões gerenciais de progresso, embora a informação sobre qualidade possa ser usada para decisões gerenciais.
- Avaliações de progresso comparam o progresso real com o planejado; preocupam-se com prazos e orçamento.
- Revisões de qualidade focam em procurar problemas, melhorar o processo e estabelecer padrões para mitigar problemas.
- Revisões de progresso consideram fatores externos e mudanças de circunstâncias que podem tornar o software desnecessário ou exigir modificações radicais.

> [!TIP] DICAS:
> - Qualidade é uma área de conhecimento do PMBOK.
> - Revisão de qualidade = foco no produto e no processo; revisão de progresso = foco no cronograma e orçamento.

### 3.3 Processo de Revisão
- A equipe de qualidade faz a revisão e pode marcar uma reunião para avaliação com o time.

### 3.4 Inspeções de Programa
- São revisões por pares em que os membros do time colaboram para encontrar bugs no programa em desenvolvimento.
- Podem fazer parte dos processos de verificação e validação de software.
- Complementam os testes porque não requerem a execução do programa.
- Versões incompletas do sistema podem ser verificadas.
- Frequentemente usa-se um checklist de erros comuns de programação para focalizar a pesquisa de defeitos.

#### 3.4.1 Checklist de Inspeção
| CLASSE DE DEFEITO | VERIFICAÇÃO DE INSPEÇÃO |
|---|---|
| Defeito de dados | Todas as variáveis de programa foram inicializadas antes de seus valores serem usados?; Todas as constantes têm nomes?; O limite superior dos vetores deve ser igual ao tamanho do vetor ou ao tamanho -1?; Se forem utilizadas cadeias de caracteres, um delimitador foi explicitamente atribuído?; Existe qualquer possibilidade de estouro de buffer? |
| Defeito de controle | Para cada comando condicional, a condição está correta?; É certo que cada laço termina?; Os comandos compostos estão corretamente agrupados?; Nos comandos case, todos os casos possíveis foram levados em conta?; Se for necessário um break após cada caso nos comandos case, ele foi incluído? |
| Defeito de entrada-saída | Todas as variáveis de entrada são utilizadas?; Todas as variáveis de saída receberam um valor antes de serem devolvidas?; Entradas inesperadas podem causar corrupção? |
| Defeito de interface | Todas as chamadas de função e métodos têm o número correto de parâmetros?; Os tipos de parâmetros formais e reais têm correspondência?; Os parâmetros estão na ordem certa?; Se os componentes acessarem a memória compartilhada, eles têm o mesmo modelo de estrutura de memória compartilhada? |
| Defeito de gerenciamento de armazenamento | Se uma estrutura ligada for modificada, todas as ligações foram corretamente reatribuídas?; Se for utilizada memória dinâmica, o espaço foi alocado corretamente?; O espaço foi explicitamente liberado após não ser mais necessário? |
| Defeito de gerenciamento de exceções | Todas as possíveis condições de erro foram levadas em conta? |

> [!TIP] DICAS:
> - O checklist de inspeção é uma ferramenta sistemática para encontrar defeitos, não uma lista exaustiva.
> - Inspeções são mais eficazes que testes unitários para detecção de defeitos, segundo estudos clássicos.

### 3.5 Inspeções e sua Relevância
- Estudo de Fagan (1986): mais de 60% dos erros em um programa foram detectados usando inspeções de programa informais.
- McConnell (2004): testes unitários têm taxa de detecção de defeitos de cerca de 25%, enquanto inspeções têm taxa de 60%.
- Essas comparações foram feitas antes da popularização dos testes automatizados, portanto não se sabe como as inspeções se comparam a essa abordagem.

> [!CAUTION] OBSERVAÇÃO:
> - Os dados de Fagan e McConnell são referências clássicas, mas anteriores à era dos testes automatizados, o que relativiza a comparação nos dias atuais.

## 4. Padrões de Produto e Padrões de Processo
- Padrões do produto e padrões do processo são definidos pela organização e são importantes para a qualidade final do software.
- O controle de qualidade inclui a revisão da qualidade da documentação e dos processos usados para a produção do software.

> [!TIP] DICAS:
> - Controle de qualidade não se limita ao produto final; abrange documentação e processos.

## 5. Qualidade e Ciclo de Vida do Software
- A qualidade não é inserida somente em etapas específicas do ciclo de vida.
- A inspeção pode ser feita durante todo o processo de desenvolvimento.
- O processo de qualidade está presente em todo o ciclo de vida do produto.
- A qualidade de software, teoricamente, deve satisfazer o usuário.
- A visão tradicional tem certa dificuldade em incorporar mudanças, enquanto no desenvolvimento ágil a mudança é bem aceita.

> [!CAUTION] OBSERVAÇÃO:
> - A qualidade é contínua e transversal, não uma fase isolada.
> - A visão tradicional e a visão ágil tratam a mudança de formas distintas: a primeira resiste, a segunda acolhe.