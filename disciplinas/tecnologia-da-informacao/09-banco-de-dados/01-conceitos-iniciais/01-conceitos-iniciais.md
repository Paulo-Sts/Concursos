# Banco de Dados – Conceitos Iniciais

## 1. Importância dos Bancos de Dados no Cotidiano
- Bancos de dados estão presentes em diversas atividades diárias, tais como:
  - Recuperação de informações na WWW (World Wide Web).
  - Operações com cartão de crédito.
  - Download de arquivos da Internet.
  - Compra de passagens aéreas.
  - Marcação de consultas médicas.
  - Reservas em hotéis.
  - Operações bancárias.
  - Renovação da Carteira Nacional de Habilitação (CNH).
  - Compras em supermercados.
  - Declaração do Imposto de Renda.

#### 1.1 Definição Ampla
- De forma geral, tudo o que guarda informações pode ser chamado de banco de dados.
- No contexto da computação, a definição é mais restrita e técnica.

## 2. Sistemas Tradicionais de Processamento de Arquivos
- Antes do surgimento dos Sistemas Gerenciadores de Banco de Dados (SGBDs), os dados eram armazenados em arquivos isolados.
- Cada programa de aplicação fazia seu próprio gerenciamento de dados – sistema altamente acoplado (dados e programas fortemente dependentes).

#### 2.1 Limitações dos Sistemas Tradicionais de Arquivos

| LIMITAÇÃO | DESCRIÇÃO |
|-----|-----|
| Complexidade no controle de segurança | Difícil implementar permissões granulares e consistentes em arquivos isolados. |
| Inconsistência | Mesmo dado pode estar armazenado em múltiplos arquivos com valores diferentes. |
| Problemas de atomicidade | Em caso de falha, pode ser impossível garantir que todas as operações relacionadas sejam concluídas ou revertidas. |
| Ausência de padronização | Cada programa pode usar formato próprio, dificultando integração. |
| Complexidade para acessar dados | Acesso a dados dispersos exige maior esforço de programação. |
| Redundância não controlada | O mesmo dado é repetido em vários arquivos, gerando desperdício de espaço e risco de inconsistência. |

## 3. Banco de Dados (Definição Formal)
- Coleção de dados relacionados (não qualquer conjunto de arquivos soltos).
- Conjunto de dados integrados que tem o intuito de atender a uma comunidade de usuários.
- Fatos conhecidos que podem ser registrados e possuem significado implícito.
- Coleção lógica e coerente de dados.

## 4. Minimundo (Universe of Discourse – UoD)
- Representa algum aspecto do mundo real que será modelado no banco de dados.
- Parte do mundo real sobre a qual será criado o banco de dados e sua aplicação.
- Pode ser manual ou informatizado.
- Complexidade variável e qualquer tamanho.
- O minimundo é a fonte dos dados.
- O banco de dados é uma representação (modelagem) do minimundo.

## 5. SGBD – Sistema de Gerenciador de Banco de Dados
- SGBD ou DBMS é o software que permite a criação, manipulação e administração de bancos de dados.
- É um software de propósito geral que possibilita a definição, construção e manipulação de bancos de dados.
- O SGBD é dependente de tecnologia (evolui conforme a tecnologia disponível).

#### 5.1 Principais Funções do SGBD
- Especificar os tipos de dados, estruturas e restrições para os dados armazenados. 
- Armazenar os dados em algum meio de armazenamento controlado pelo SGBD. 
- Recuperar e atualizar dados (consultas, inserções, exclusões, alterações). 
- A definição de estruturas e restrições busca resolver o problema da inconsistência presente nos sistemas tradicionais de arquivos.

#### 5.2 Exemplos de SGBDs

| SGBD | CARACTERÍSTICA |
|-----|-----|
| SQL Server | Microsoft, amplamente usado no ambiente corporativo Windows. |
| PostgreSQL | Open-source, avançado, suporte a JSON e tipos complexos. |
| MySQL | Open-source, muito popular em aplicações web. |
| MariaDB | Versão modificada (fork) do MySQL, também open-source. |
| Oracle | SGBD comercial de grande porte, muito usado em empresas. |

#### 5.3 Metadados
- Metadados são "dados sobre os dados".
- Informações que descrevem outros dados, permitindo que sejam:
  - Identificados;
  - Organizados;
  - Localizados;
  - Usados de forma mais eficiente.

#### 5.4 Exemplos de Metadados

| METADADO | DESCRIÇÃO |
|---|---|
| Nome da tabela | Identifica a estrutura de armazenamento. |
| Nome das colunas | Identifica os atributos de cada entidade. |
| Tipo de dado de uma coluna (ex.: INT, VARCHAR) | Define o formato e as operações possíveis. |
| Restrições (ex.: NOT NULL, PRIMARY KEY) | Define regras de integridade dos dados. |
| Índices | Acelera a localização de dados. |

#### 5.5 Esquema vs. Instância
- Esquema: a descrição estrutural do banco de dados (conjunto de metadados) – é relativamente estável.
- Instância: o conteúdo efetivo do banco de dados em um dado momento (os dados propriamente ditos) – muda frequentemente.

#### 5.6 Atomicidade
- Atomicidade é uma propriedade das transações em bancos de dados.
- Garante que todas as etapas de uma transação sejam concluídas ou revertidas integralmente (tudo ou nada).
- Exemplo: transferência bancária – o débito em uma conta e o crédito em outra devem ocorrer juntos ou nenhum deve ocorrer.