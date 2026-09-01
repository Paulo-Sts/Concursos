# Desenvolvimento de Software: Programação Tradicional, Low-Code e No-Code

## 1. Programação Tradicional
- Processo de desenvolvimento de software que utiliza linguagens de programação formais, como Java, C, Python, C# e JavaScript, por meio da escrita manual de código-fonte estruturado.
- Exige que o desenvolvedor domine a sintaxe da linguagem, estruturas de controle, lógica, algoritmos e modelagem de arquiteturas como MVC ou microsserviços.
- É a abordagem mais poderosa e flexível, sendo a mais recomendada para sistemas robustos, com especificações complexas e requisitos críticos de segurança.
- Gerenciamento integral de bancos de dados, integrações e testes manuais.

### 1.1 Desvantagens da Programação Tradicional
- Requer conhecimento técnico aprofundado e experiência vasta da equipe;
- Projetos complexos demandam maior tempo de análise, codificação e manutenção;
- Envolve custos elevados com infraestrutura e equipes técnicas altamente especializadas.

## 2. Estratégias Low-Code e No-Code
- Surgem como alternativas para acelerar a criação de sistemas e aplicativos com menor ou nenhuma necessidade de programação manual.
- Estratégias fundamentais para:
  - Acelerar a transformação digital nas organizações;
  - Reduzir o backlog de TI ⟶ permite que a equipe técnica foque em processos críticos e sensíveis;
  - Democratizar o desenvolvimento de soluções.

## 3. Low-Code
- Abordagem de desenvolvimento que utiliza interfaces visuais e ferramentas gráficas para reduzir drasticamente a necessidade de escrita de código.
- Permite a personalização de áreas padronizadas através de pequenos trechos de código, como em operações matemáticas específicas.
- Público-alvo composto por programadores, analistas técnicos e times mistos entre TI e negócio.

### 3.1 Características e Funcionamento do Low-Code
- Uso de interfaces visuais do tipo drag-and-drop para construção de telas e fluxos;
- Suporte a scripts personalizados para regras de negócio e integrações complexas;
- Possui componentes reutilizáveis como widgets e templates;
- Modelagem visual onde cada ação é registrada como metadado (XML ou JSON) e convertida por um motor de renderização em código executável (HTML, JS, Java, SQL, etc.).

### 3.2 Vantagens e Desvantagens do Low-Code
- Vantagens:
  - Acelera o desenvolvimento de projetos e MVPs;
  - Facilita a integração com sistemas legados e APIs;
  - Escalável para ambientes corporativos em nuvem.
- Desvantagens:
  - Lock-in de fornecedor ⟶ dependência da plataforma e de suas licenças;
  - Riscos de segurança se houver implementação indevida ou falhas na própria plataforma;
  - Difícil migração ⟶ se o projeto crescer demais, pode ser necessário refazer do zero por impossibilidade de reaproveitamento do código.

## 4. No-Code
- Abordagem de desenvolvimento de aplicações que dispensa completamente o uso de linguagens de programação tradicionais.
- As aplicações são criadas exclusivamente por interfaces gráficas, com blocos visuais, menus de configuração e modelos prontos.
- Utiliza o conceito de desenvolvimento declarativo para a construção das soluções.
- Público-alvo composto por cidadãos desenvolvedores e colaboradores que não atuam diretamente com tecnologia da informação.
- Ferramentas acessíveis que não exigem nenhum conhecimento prévio de programação.
- Funcionamento estrito no sistema de clique e arraste.
- Características:
  - Customização mínima e limitada aos módulos pré-construídos;
  - Usuário deve se adaptar totalmente às regras da plataforma.

### 4.1 Citizen Developer
- Persona definida pela consultoria Gartner como um colaborador que cria funcionalidades de aplicativos para uso próprio ou de terceiros.
- Não representa um cargo formal ou função designada dentro da estrutura organizacional.
- O profissional está vinculado a uma unidade de negócio ou área funcional que não pertence ao setor de tecnologia da informação.
- Utiliza ferramentas que não são explicitamente proibidas pelas áreas de tecnologia da informação ou pelas unidades de negócio.

### 4.2 Características Técnicas do No-Code
- Processo de construção 100% visual abrangendo interface de usuário, lógica, banco de dados e automações.
- Inexistência de código-fonte visível para o usuário, sem necessidade ou opção de digitação manual de código tradicional.
- Comandos de lógica, fluxos e integrações encapsulados em componentes prontos para uso.
- Disponibilidade de modelos reutilizáveis e templates configuráveis para sistemas comuns como crm, cadastros ou controles.
- Presença de conectores nativos para integração com planilhas, apis rest/soap e ferramentas de produtividade como Google Workspace.

### 4.3 Análise de Vantagens e Limitações
- Desenvolvimento extremamente ágil permitindo a criação de aplicações em minutos ou poucas horas.
- Autonomia do setor de negócio ⟶ libera a equipe de tecnologia da informação de demandas menos complexas.
- Compatibilidade nativa com diversas plataformas e dispositivos, facilitando a criação de aplicações acessíveis e responsivas.
- Redução do tempo de entrega de soluções para responder rapidamente às necessidades do negócio sem depender exclusivamente da equipe técnica.

### 4.4 Desvantagens e Riscos Associados
- Baixa flexibilidade e customização restrita aos blocos e modelos disponíveis na plataforma escolhida.
- Risco de shadow it caracterizado pelo surgimento de soluções paralelas sem validação técnica ou governança pela equipe de tecnologia da informação.
- Forte dependência do fornecedor dificultando migrações futuras para outras ferramentas.
- Dificuldade de escalabilidade em sistemas que envolvem alto volume de dados ou requisitos críticos e complexos.
- Permanência de riscos de segurança relacionados a vulnerabilidades inerentes à plataforma utilizada.

### 4.5 Aplicações Recomendadas e Contraindicadas
| TIPO DE SISTEMA | ABORDAGEM RECOMENDADA | JUSTIFICATIVA DIDÁTICA |
|---|---|---|
| Gestão de férias e folgas | No-code ou low-code | Automação de processos internos simples |
| Coleta de dados por questionários | No-code ou low-code | Foco na agilidade e facilidade de uso |
| Assistentes virtuais e chatbots | No-code ou low-code | Uso de componentes pré-construídos e fluxos simples |
| Migração de sistemas legados | Desenvolvimento tradicional | Exigência de controle sobre desempenho e segurança |
| Controle de carro autônomo | Desenvolvimento tradicional | Alta complexidade que exige desenvolvimento especializado |
| Internet banking | Desenvolvimento tradicional | Requisito de alta segurança e personalização profunda |

> [!TIP] DICAS: 
> - Embora o usuário não precise escrever código manualmente, a aplicação gerada depende de código para ser executada pelo computador.
> - O lançamento mais rápido de protótipos e de produtos mínimos viáveis (mvps) é uma das maiores vantagens sobre o desenvolvimento tradicional.

> [!CAUTION] OBSERVAÇÃO: 
> - A implementação de uma governança de tecnologia da informação é essencial para realizar revisões de segurança e conformidade.
> - Sistemas críticos exigem algum nível de envolvimento do time de tecnologia da informação mesmo quando se trabalha com abordagens low-code ou no-code.

## 5. Comparativo entre Abordagens
| CATEGORIA | PROGRAMAÇÃO TRADICIONAL | LOW-CODE | NO-CODE |
|---|---|---|---|
| Conhecimento técnico | Alto e especializado | Noções básicas | Nenhum conhecimento |
| Método de criação | Escrita manual de código | Interface visual e scripts | Clique e arraste |
| Flexibilidade | Máxima e total | Alta com limitações | Mínima e padronizada |
| Uso recomendado | Sistemas hipercríticos | Aplicativos corporativos | Sistemas simples e internos |

> [!TIP] DICAS: 
> - O low-code não descarta as linguagens de programação; ele as automatiza através de soluções genéricas para ganhar velocidade.

> [!CAUTION] OBSERVAÇÃO: 
> - A principal diferença entre low-code e no-code para fins de prova é o nível de conhecimento de codificação exigido do usuário.
> - Sistemas hipercríticos de bancos, saúde ou segurança ainda dependem da programação tradicional pela necessidade de controle total.