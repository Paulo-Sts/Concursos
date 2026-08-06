# Data Mart e OLAP

## 1. Data Mart
- Subconjunto de um Data Warehouse.
- Representa uma visão específica e segmentada dos dados para atender a uma área de negócio ou a uma equipe específica dentro de uma organização.
- Contém informações focadas em um determinado assunto, como vendas, marketing, finanças ou recursos humanos.

### 1.1 Abordagens para Criação
- Top-down: os Data Marts são derivados diretamente do Data Warehouse.
- Bottom-up: os Data Marts são criados separadamente e depois integrados em um Data Warehouse central.

### 1.2 Benefícios
- Foco em necessidades específicas.
- Melhor desempenho.
- Autonomia para as equipes.
- Flexibilidade.

### 1.3 Definição Técnica
- É um subconjunto de dados referentes a uma área específica, não normalizados e indexados para suportar pesquisas.

> [!TIP] DICAS:
> - Data Mart é uma subdivisão do Data Warehouse, criada para atender departamentos ou áreas específicas.
> - Não é uma cópia do Data Warehouse para alterações, nem uma versão carregada no computador do cliente.
> - Pode ser criado antes do Data Warehouse central (abordagem Bottom-up) ou a partir dele (abordagem Top-down).

> [!CAUTION] OBSERVAÇÃO:
> - Data Mart contém dados não normalizados e indexados para otimizar consultas analíticas.
> - Um projeto de Data Warehouse pode começar atendendo um subconjunto da organização por meio de Data Marts, dispensando grandes investimentos iniciais.

## 2. OLAP (Online Analytical Processing)
- Permite extrair as informações dos dados armazenados no modelo dimensional (no Data Warehouse).
- Abordagem e tecnologia usada para a análise interativa de dados multidimensionais.
- Projetado para fornecer respostas rápidas a consultas analíticas complexas, permitindo que os usuários explorem os dados de maneira flexível e intuitiva.
- É uma ferramenta para acesso à informação de um Data Warehouse que armazena dados históricos para tomadas de decisão empresariais.
- Organiza, consolida e permite o acesso a dados de múltiplas fontes para tomada de decisão.
- Programa que possibilita que os usuários explorem dados de diferentes perspectivas para conduzir à inteligência empresarial.

### 2.1 Características Chave
- Modelagem Multidimensional.
- Operações Analíticas.
- Desempenho Otimizado: otimiza o desempenho do modelo dimensional e várias tabelas dimensões em volta.
- Acesso Hierárquico: hierarquia para cada uma das dimensões (dimensão região, dimensão tempo etc.).
- Funcionalidades de Navegação.
- Visualização de Resultados.

### 2.2 Características Específicas
- Trabalha sobre histórico de dados com o objetivo de analisar informações.
- Usado para realizar análise de dados a fim de se obter informações desejadas.
- Disponibiliza relatórios de forma dinâmica para análise e tratamento.

> [!TIP] DICAS:
> - OLAP não opera com dados em tempo real.
> - OLAP não suporta operações cotidianas do processo operacional (essa é função do OLTP).

> [!CAUTION] OBSERVAÇÃO:
> - OLAP é um conceito de interface com o usuário que proporciona a capacidade de ter ideias sobre os dados, permitindo analisá-los profundamente em diversos ângulos.
> - Suas funções básicas são fornecer visualização multidimensional dos dados, exploração, rotação e diferentes modos de visualização.
> - É uma interface com o usuário e não uma forma de armazenamento de dados, porém usa o armazenamento para poder apresentar as informações.
> - OLTP (Online Transaction Processing) é a técnica de análise de dados que tem o propósito de desempenhar funções empresariais cotidianas.

### 2.3 Variações do OLAP

#### 2.3.1 MOLAP (OLAP Multidimensional)
- Forma clássica de OLAP (conhecido como OLAP).
- Armazena dados em um modelo de dados multidimensional.
- Pré-computação (cubo de dados) no MOLAP tradicional ou computação sobre demanda no MOLAP rápido.
- Dimensões do fato são as faces do cubo de dados.
- Em vez de guardar os dados em tabelas, os dados são armazenados em formato de cubo, auxiliando muito em operações OLAP.
- Características:
  - Consultas mais rápidas.
  - Precisa de menos espaço em disco.
  - Propensa à explosão de dados.

> [!CAUTION] OBSERVAÇÃO:
> - MOLAP não é um método utilizado para apresentar, fisicamente e em formato relacional, os dados em formato OLAP.
> - MOLAP é o resultado de um banco de dados OLAP implementado sobre um banco de dados tradicional existente.

#### 2.3.2 ROLAP (OLAP Relacional)
- Trabalham diretamente com bancos de dados relacionais.
- Não realizam pré-computação.
- Os dados são mantidos como tabelas relacionais.
- Características:
  - Cargas mais rápidas.
  - Mais escalável.
  - Tempo de desenvolvimento maior.

> [!TIP] DICAS:
> - ROLAP cria visões multidimensionais a partir de um banco de dados relacional existente.

#### 2.3.3 HOLAP (OLAP Híbrido)
- Permite armazenar dados em MOLAP e em ROLAP.
- Particionamento vertical:
  - Agregações em MOLAP.
  - Dados detalhados em ROLAP.
- Particionamento horizontal:
  - Dados mais novos em MOLAP.
  - Dados mais antigos em ROLAP.

> [!CAUTION] OBSERVAÇÃO:
> - HOLAP faz o tratamento de bancos híbridos, aqueles que têm parte relacional e parte multidimensional.

#### 2.3.4 WOLAP
- OLAP baseado em web.
- Análises e consultas baseadas em ambiente web.
- Navegação pelos dados de forma interativa.

#### 2.3.5 DOLAP
- Desktop OLAP.
- Dados acessados e analisados localmente.

#### 2.3.6 RTOLAP
- OLAP em tempo real.

#### 2.3.7 GOLAP
- OLAP gráfico.
- Utiliza gráficos e visualizações para auxiliar na análise e exploração dos dados.

### 2.4 Resumo das Variações OLAP
| VARIAÇÃO | ARMAZENAMENTO | CARACTERÍSTICA PRINCIPAL |
|----------|---------------|--------------------------|
| MOLAP    | Multidimensional | Dados em cubos; consultas rápidas; propenso à explosão de dados |
| ROLAP    | Relacional     | Trabalha com bancos de dados relacionais; não faz pré-computação |
| HOLAP    | Híbrido        | Combina MOLAP e ROLAP (partes em cada formato) |
| WOLAP    | Variado        | Baseado em web |
| DOLAP    | Local          | Desktop |
| RTOLAP   | Variado        | Tempo real |
| GOLAP    | Variado        | Foco em gráficos e visualizações |