# Modelos De Dados

## 1. Definição
- Representação abstrata que organiza elementos de dados.
- Existem diferentes modelos para atender a diversas necessidades e tipos de dados.

### 1.1 Principais Tipos de Modelos
- Modelo relacional:
  - Os dados são organizados em tabelas inter-relacionadas por meio de chaves primárias e estrangeiras.
  - Limitação: lentidão ao lidar com grandes volumes de dados.
- Modelo dimensional:
  - Os dados são organizados em tabelas fato e descritos por dimensões.
  - Vantagem: reduz os níveis de junção a apenas um.
- Modelo de documentos:
  - Criado para lidar com dados não estruturados e semiestruturados.
  - Oferece uma estrutura flexível, como a do JSON, permitindo aninhamento de documentos.
  - Exemplo de aplicação: bancos de dados como o MongoDB.

## 2. Avaliação de Modelos de Dados
- Atividade objetiva que deve ser realizada por alguém que não participou da construção do modelo.
- A avaliação, por si só, não garante a qualidade do modelo, que vai além dessa verificação.

### 2.1 Ciclo Pdca na Avaliação
- O ciclo PDCA (Planejar, Executar, Checar, Agir) é uma ferramenta para a melhoria contínua da qualidade.
- Aplicação no contexto de modelos de dados:
  - Planejar: definição de como será feita a avaliação.
  - Executar (Do): avaliação efetiva do modelo.
  - Checar (Check): verificação dos resultados da avaliação para identificar melhorias.
  - Agir (Act): implementação das correções necessárias no modelo de dados.

> [!CAUTION] OBSERVAÇÃO:
> - O ciclo PDCA implica que a qualidade é planejada e continuamente melhorada, não apenas controlada. Esta é uma pegadinha clássica em provas.

## 3. Aspectos Principais da Avaliação
- A avaliação verifica diversos aspectos para garantir a robustez do modelo.

| ASPECTO | DESCRIÇÃO |
|---------|-----------|
| Correção | Identificação de erros no modelo. |
| Consistência | Uniformidade na formatação dos dados em diferentes tabelas que representam o mesmo tipo de informação. |
| Completude | Verificação da presença de todos os dados essenciais. |
| Normalização | Garantia de que os dados estão todos na mesma escala. |
| Extensibilidade | Flexibilidade e capacidade de expansão do modelo. |
| Conformidade com padrões | Verificação se o modelo segue um padrão de codificação definido pela organização. |
| Validação da integridade dos dados | Garantia da integridade referencial e de domínio. |
| Documentação do modelo | Serve como base para a avaliação; uma boa documentação facilita o processo. |

## 4. Técnicas e Ferramentas
- Diversas técnicas e ferramentas são empregadas para avaliar modelos de dados.

### 4.1 Ferramentas
- Ferramentas de modelagem de dados.
- Ferramentas de análise de dados.

### 4.2 Técnicas
- Revisão por pares: outra pessoa revisa o modelo.
- Simulação: utilização de dados irreais para preencher as tabelas e verificar possíveis inconsistências.
- Validação com dados reais.

> [!TIP] DICAS:
> - A revisão por pares e a simulação são técnicas importantes para identificar erros que o modelador pode não ter percebido.
> - A avaliação de modelos de dados é uma atividade formal e essencial, mesmo em processos ágeis. Ela não se torna dispensável pela agilidade do desenvolvimento.