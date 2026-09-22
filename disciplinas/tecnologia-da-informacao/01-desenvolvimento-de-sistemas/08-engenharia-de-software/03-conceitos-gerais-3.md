# Engenharia de Software Conceitos Gerais 3

## 1. Modelo em Cascata
- O modelo em cascata é um processo sequencial, onde as atividades seguem uma ordem definida e preestabelecida.
- As atividades principais incluem: especificação, projeto, construção, teste e entrega.
- É um modelo linear, onde cada fase deve ser concluída antes do início da próxima.
- Sinônimos comuns cobrados em provas para essas atividades: levantamento de requisitos, modelagem, construção e entrega.
- Possui fases bem definidas e documentação extensa em cada etapa.
- Exemplo: em um projeto de sistema bancário, primeiro são levantados todos os requisitos, depois é feito o projeto da arquitetura, seguido da codificação, testes e finalmente a entrega do sistema completo.
- Explicação: a abordagem sequencial impede que se retorne a fases anteriores sem custos elevados, tornando o modelo rígido.

### 1.1 Características do Modelo Cascata
- Desenvolvimento sequencial e linear.
- Entrega do produto apenas ao final do processo.
- Dificuldade de voltar atrás e corrigir erros após uma fase concluída.
- Não permite que os usuários acompanhem o progresso gradualmente.
- Possui fase de análise de requisitos bem definida no início do projeto.

> [!TIP] DICAS: 
> - A banca pode utilizar sinônimos para as atividades do cascata, como "fecundação" (termo incorreto) ou "levantamento de requisitos" para "especificação". Fique atento às pegadinhas!
> - Modelo cascata NÃO é orientado a riscos e NÃO possui ciclos iterativos.

> [!CAUTION] OBSERVAÇÃO: 
> - No cascata, nada é desenvolvido em paralelo; todas as etapas são sequenciais.
> - O progresso não pode ser acompanhado gradualmente, pois a entrega ocorre apenas ao final.

## 2. Desenvolvimento Incremental
- Envolve atividades simultâneas e entregas parciais do software.
- O software é desenvolvido em incrementos, com cada versão adicionando novas funcionalidades.
- Permite que os usuários vejam o progresso gradualmente.
- Os incrementos são entregues em ciclos, agregando valor ao sistema progressivamente.
- Exemplo: um sistema de e-commerce pode ser entregue primeiro com funcionalidades básicas de catálogo, depois com carrinho de compras, e posteriormente com sistema de pagamento.
- Explicação: cada incremento é uma versão funcional do sistema, permitindo feedback contínuo dos usuários.

> [!CAUTION] OBSERVAÇÃO: 
> - O desenvolvimento incremental será explorado mais detalhadamente em blocos subsequentes da disciplina.

## 3. Engenharia de Software Orientada a Reúso
- Baseia-se no modelo "Baseado em Componentes", que explora a reutilização de software existente.
- O modelo é prescritivo e envolve forte ênfase no planejamento.
- Atividades do modelo: especificação de requisitos, análise de componentes, alterações nos requisitos, projeto do sistema com reuso, desenvolvimento, integração e validação do sistema.
- Possui duas fases distintas relacionadas à engenharia de requisitos, diferenciando-se de outros modelos.
- Enfatiza a criação de componentes genéricos para facilitar o desenvolvimento de sistemas.
- Exemplo: ao desenvolver um novo sistema de gestão, utiliza-se componentes já existentes para autenticação de usuários e geração de relatórios, adaptando-os às novas necessidades.
- Explicação: o reúso reduz custos e tempo de desenvolvimento, mas exige atenção aos trade-offs entre reuso e acoplamento.

### 3.1 Conceitos Relacionados
- Padrões de projeto (design patterns): soluções reutilizáveis para problemas comuns em engenharia de software.
- Frameworks: estruturas reutilizáveis que fornecem funcionalidades genéricas e podem ser estendidas para atender necessidades específicas.

> [!CAUTION] OBSERVAÇÃO: 
> - Os tópicos de padrões de projeto e frameworks normalmente são cobrados apenas quando especificamente mencionados nos editais dos concursos.
> - O modelo "Baseado em Componentes" é o único que possui duas fases distintas relacionadas à engenharia de requisitos.

## 4. Processos Iterativos x Processos Incrementais
- Na prática, muitos processos incorporam elementos de ambas as abordagens, sendo iterativos e incrementais ao mesmo tempo.
- Processo iterativo: envolve repetições (ciclos) para validar e reduzir riscos, permitindo refinar o produto a cada ciclo.
- Processo incremental: entrega partes funcionais do software (incrementos) ao longo do desenvolvimento.
- Analogia da Monalisa:
  - Processo iterativo: faria esboços para validar e reduzir riscos à medida que avança.
  - Processo incremental: entregaria partes da ideia (incrementos) até chegar à versão final.
- Processos modernos combinam iterações com entregas incrementais.
- A iteratividade permite que o desenvolvedor volte para etapas anteriores se necessário.
- Processos lineares (como o cascata) não permitem retorno após a conclusão de uma etapa.
- Práticas como prototipação e validação de requisitos são comuns em processos iterativos e incrementais.

### 4.1 Comparação entre Abordagens
| CARACTERÍSTICA | PROCESSO ITERATIVO | PROCESSO INCREMENTAL |
|---|---|---|
| Foco principal | Validação e redução de riscos | Entregas parciais do produto |
| Ciclos | Repetições para refinamento | Entregas de funcionalidades |
| Retorno a etapas anteriores | Permitido | Pode ocorrer, mas não é o foco |
| Visualização do progresso | Parcial, através de protótipos | Gradual, através de incrementos |
| Exemplo prático | Esboços da Monalisa | Partes da Monalisa entregues separadamente |

> [!TIP] DICAS: 
> - As bancas frequentemente perguntam sobre as características desses processos, especialmente a diferença entre iterativo e incremental.
> - Compreender a evolução da engenharia de software é fundamental para responder questões sobre modelos de ciclo de vida.

> [!CAUTION] OBSERVAÇÃO: 
> - Processos lineares (como cascata) não permitem retorno a etapas anteriores.
> - Modelos mais antigos ainda são cobrados em concursos, mesmo que não sejam amplamente utilizados atualmente.