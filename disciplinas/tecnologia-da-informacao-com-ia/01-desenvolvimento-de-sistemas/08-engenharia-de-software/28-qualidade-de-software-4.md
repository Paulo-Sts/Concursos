# Engenharia de Software - Qualidade de Software 4

## 1. Métodos Ágeis e a Ênfase no Código
- Os métodos ágeis de engenharia de software concentram-se primordialmente no desenvolvimento do código-fonte.
- Minimizam a documentação e os processos que não estão diretamente relacionados com a criação do código.
- Enfatizam a importância das comunicações informais entre os membros da equipe em detrimento das comunicações baseadas em documentos de projeto formalizados.
- Alguns métodos ágeis chegam a afirmar que o código bem escrito é, por si só, a documentação do sistema.

> [!CAUTION] OBSERVAÇÃO:
> - Essa visão minimalista de documentação é um dos principais pontos de distinção entre as abordagens ágeis e as tradicionais, sendo frequentemente cobrado em provas que comparam metodologias.

## 2. Qualidade no Contexto Ágil
- A qualidade, no desenvolvimento ágil, está diretamente associada à qualidade do código produzido.
- Práticas como refatoração e Test-Driven Development (TDD) são empregadas para assegurar a produção de um código de alta qualidade.
- Um código de alta qualidade resulta em ganhos significativos de manutenibilidade e confiabilidade do software.

> [!TIP] DICAS:
> - Lembre-se: a qualidade ágil é focada no produto (código) e nas práticas de engenharia, e não em documentos formais ou processos burocráticos.

## 3. Qualidade e Agilidade: Visão da Comunidade Ágil
- A comunidade ágil posiciona-se de forma fundamentalmente oposta ao que considera uma sobrecarga burocrática.
- Essa sobrecarga é frequentemente associada a abordagens baseadas em padrões formais e processos de qualidade, como o estabelecido pela norma ISO 9001.
- No desenvolvimento ágil, o gerenciamento da qualidade baseia-se em boas práticas compartilhadas pela equipe, e não em documentação formal e processos prescritivos.

## 4. Boas Práticas de Extreme Programming (XP)
- O Extreme Programming (XP) introduz práticas específicas para garantir a qualidade do software, com foco em um código de alta qualidade.

### 4.1 Verificar Antes do Check-in
- Os programadores são responsáveis por organizar suas próprias revisões de código com outros membros da equipe.
- Essa verificação deve ocorrer antes de o código ser submetido (commit) ao sistema de construção (build) principal.
- Busca-se ter uma ampla cobertura de testes no código-fonte.
- A cobertura de testes permite que, em alterações futuras, seja possível verificar rapidamente se algo foi "quebrado" (regressão).

### 4.2 Nunca Quebrar a Construção
- É inaceitável que um membro da equipe submeta um código que faça com que o sistema como um todo falhe (quebre o build).
- Cada indivíduo deve testar suas mudanças contra todo o sistema e estar confiante de que o código funciona conforme o esperado.
- Se a construção for quebrada, espera-se que a pessoa responsável dê prioridade máxima para corrigir o problema imediatamente.

### 4.3 O Código Não Tem Dono
- O código do sistema pertence à equipe como um todo, e não a desenvolvedores individuais.
- Se um programador descobrir problemas ou trechos obscuros no código desenvolvido por outra pessoa, ele pode corrigi-los diretamente.
- Essa prática elimina a necessidade de encaminhar o problema de volta ao desenvolvedor original, agilizando a correção.

> [!TIP] DICAS:
> - O princípio "código não tem dono" é um conceito chave do XP e visa aumentar a colaboração e a responsabilidade coletiva, sendo frequentemente cobrado em provas.

## 5. Inspeção de Código e Programação em Pares
- As revisões de código podem ser implementadas de duas formas principais no XP.
- Responsabilidade individual com verificação antes do check-in.
- Programação em pares (Pair Programming).

### 5.1 Programação em Pares (Pair Programming)
- Duas pessoas são responsáveis pelo desenvolvimento do código e trabalham em conjunto para alcançá-lo.
- O código desenvolvido por um indivíduo é constantemente examinado e analisado por outro membro da equipe durante o processo de criação.
- Ambas as pessoas examinam cada linha de código, realizando uma verificação contínua antes de a solução ser aceita.

### 5.2 Benefícios da Programação em Pares
- A programação em pares leva a um conhecimento profundo do programa, pois ambos os programadores precisam compreendê-lo em detalhes para continuar o desenvolvimento.
- Essa profundidade de conhecimento pode ser difícil de alcançar em outros processos de inspeção formal.
- A revisão contínua pode encontrar defeitos que talvez não fossem descobertos em inspeções formais, devido à constante atenção sobre o código.

### 5.3 Possíveis Problemas da Programação em Pares
- Apesar dos benefícios, a programação em pares apresenta desafios, pois as duas pessoas envolvidas são donas do trabalho e podem não ser tão objetivas quanto uma equipe de inspeção externa.

#### 5.3.1 Mal-entendidos Mútuos
- Ambos os membros do par podem cometer o mesmo erro na compreensão dos requisitos do sistema.
- As discussões entre a dupla podem reforçar esses erros em vez de corrigi-los, criando um "ponto cego" comum.

#### 5.3.2 Reputação dos Pares
- Os pares podem estar relutantes em procurar e apontar erros no trabalho um do outro.
- Essa relutância pode ser motivada pelo receio de retardar o andamento do projeto ou de prejudicar a relação profissional.

#### 5.3.3 Relações de Trabalho
- A capacidade do par para descobrir defeitos pode ser comprometida pela estreita relação profissional.
- A proximidade muitas vezes leva à relutância em criticar colegas de trabalho, mesmo quando a crítica é construtiva e necessária para a qualidade.

> [!CAUTION] OBSERVAÇÃO:
> - Estudos acadêmicos indicam que, para a programação em pares funcionar de forma mais eficaz, é recomendável ter um programador júnior e outro mais experiente.
> - Se os dois membros forem do mesmo nível de senioridade, podem ocorrer conflitos ou a dinâmica de revisão pode ser menos produtiva.

## 6. Limitações da Abordagem Ágil e a Necessidade de Documentação
- A abordagem informal para o gerenciamento da qualidade é eficaz em certos contextos, mas pode se tornar impraticável em outros.
- A abordagem ágil funciona bem para produtos de software onde a empresa que desenvolve também controla a especificação, sem a necessidade de reportar qualidade a um cliente externo.

### 6.1 Cenários Onde a Abordagem Ágil Pode Ser Impraticável
- Cliente com processos próprios de qualidade: Se o cliente for uma grande empresa, ele pode ter seus próprios processos de gerenciamento da qualidade e exigir que a desenvolvedora divulgue o progresso de forma compatível. O time pode ter de produzir um plano de qualidade formal e relatórios.
- Equipes distribuídas geograficamente: Em projetos com vários times distribuídos (talvez de empresas diferentes), as comunicações informais são impraticáveis. Diferentes empresas podem ter abordagens distintas, exigindo documentação formal para alinhamento.
- Sistemas de longa vida útil: O time de desenvolvimento mudará com o tempo. Sem documentação, novos membros podem achar impossível entender decisões de desenvolvimento tomadas no passado.

## 7. Adaptação da Qualidade em Métodos Ágeis
- A qualidade em métodos ágeis pode precisar ser adaptada para incorporar documentação e processos formais de qualidade.
- Geralmente, essa adaptação é integrada ao processo de desenvolvimento iterativo.
- Todas as práticas ágeis buscam trazer qualidade ao software, mas a ISO de qualidade se preocupa mais com manuais formais, podendo perder o foco no envolvimento do usuário.
- Para controlar processos, são necessárias medições, e as métricas apoiam a busca por um software que atenda às necessidades do usuário e a diversos requisitos (funcionais e não funcionais).

> [!CAUTION] OBSERVAÇÃO:
> - O manifesto ágil não ordena a abolição da documentação. A ênfase é na colaboração, mas a documentação pode ser necessária em projetos complexos ou com clientes externos, como destacado.