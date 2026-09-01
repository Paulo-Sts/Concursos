# Engenharia de Software - Domain Driven Design

## 1. Fundamentos do Domain Driven Design
- O Domain Driven Design (DDD) é uma abordagem de projeto disciplinada que reúne conceitos e técnicas para a construção de softwares baseados em modelos de domínio.
- O domínio designa o campo de ação, conhecimento e influência de um determinado negócio que o software visa atender.
- Atua como um intermediário entre as metodologias ágeis e métodos tradicionais de engenharia de software.
- O foco central reside na disciplina do design do projeto para compreender completamente o negócio.
- Existe uma sinergia crucial entre o código e o processo de análise, onde mudanças no código devem resultar em mudanças no modelo.
- O uso do DDD é indicado especificamente para projetos que possuam um conjunto de regras de negócio complexas.

> [!TIP] DICAS: 
> - Para sistemas simples, o uso do DDD não é aconselhado devido à sua complexidade inerente ⟶ foque no DDD quando houver regras de negócio densas e complexas.

## 2. Linguagem Ubíqua
- Também conhecida como linguagem onipresente, busca garantir que todos os envolvidos no projeto falem a mesma língua.
- É um conceito fundamental para a comunicação eficaz entre equipes de desenvolvimento e especialistas do domínio.
- Utiliza termos bem definidos que integram o domínio do negócio e devem estar presentes tanto na linguagem falada quanto no código-fonte.
- Representa o jargão utilizado no domínio do projeto que deve ser entendido completamente por todas as áreas.

## 3. Arquitetura em Camadas e Camada de Domínio
- O DDD preconiza a separação das camadas para garantir uma estrutura organizada e de fácil manutenção.
- As camadas precisam ser independentes; se duas se misturam, perdem sua característica de camadas distintas.
- A camada de domínio é considerada o coração do sistema e a mais importante, pois contém as regras de negócio essenciais.
- O núcleo do domínio (core domain) é alcançado através de um processo chamado de destilação do domínio, focando no que é central para o negócio.

### 3.1 Contextos Delimitados
- Os contextos delimitados (bounded contexts) buscam dividir um domínio complexo em contextos baseados nas intenções do negócio.
- Permitem que o DDD lide com modelos grandes, dividindo-os e tratando melhor seus inter-relacionamentos.
- Cada contexto pode possuir uma modelagem específica para atender às suas regras de negócio exclusivas.
- A interação entre diferentes contextos é gerenciada por interfaces claras e traduções explícitas.

## 4. Integração com Sistemas Legados
- O DDD utiliza uma abordagem pragmática para lidar com sistemas de difícil manutenção ou códigos legados.

### 4.1 Camada Anticorrupção
- Atua como um intermediário técnico posicionado entre o novo sistema e um sistema legado.
- Tem a finalidade de traduzir informações entre os sistemas para preservar a integridade e a coerência dos dados.
- Evita que o sistema novo seja contaminado pelas deficiências estruturais do código legado.

### Resumo de Conceitos do Domain Driven Design
| CONCEITO | DEFINIÇÃO | FINALIDADE |
|---|---|---|
| Domínio | Campo de ação e conhecimento | Atender completamente o negócio. |
| Linguagem ubíqua | Terminologia compartilhada | Unificar a comunicação entre técnicos e especialistas. |
| Núcleo do domínio | Regras de negócio centrais | Concentrar os esforços no que é essencial. |
| Camada anticorrupção | Intermediário de tradução | Integrar sistemas legados sem contaminar o novo. |

> [!CAUTION] OBSERVAÇÃO: 
> - Diferente de algumas abordagens onde a modelagem e a implementação são independentes, no DDD elas são estritamente ligadas ⟶ o modelo de análise e o código devem estar sempre em total sinergia.