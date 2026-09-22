# Banco de Dados - Mapeamento 2

## 1. Mapeamento Relacionamentos 1:N
- No modelo relacional, o relacionamento 1:N é implementado pela inclusão da chave estrangeira na tabela do lado N.
- O lado N (muitos) recebe uma coluna que referencia a chave primária do lado 1 (um).
- Exemplo: empregado trabalha em um departamento.
  - Cada empregado pertence a um único departamento;
  - Cada departamento pode ter vários empregados.
- Implementação:
  - Tabela DEPARTAMENTO (CodDep, Sigla, LocalDep);
  - Tabela EMPREGADO (CodEmp, Nome, CodDep).
- A coluna CodDep em EMPREGADO é uma chave estrangeira que referencia CodDep em DEPARTAMENTO.
- Restrição de integridade: o campo CodDep em EMPREGADO não pode ser nulo, pois todo empregado deve estar associado a um departamento.

### Tabela
| CODEMP | NOME | CODDEP |
|--------|------|--------|
| 1 | João | 10 |
| 2 | Antônio | 10 |
| 3 | Juliana | 20 |
| 4 | Priscila | 30 |
| 5 | Vinícius | 40 |

| CODDEP | SIGLA | LOCALDEP |
|--------|-------|----------|
| 10 | DTI | Recife |
| 20 | DENG | São Paulo |
| 30 | DIUR | Porto Alegre |
| 40 | DFIN | Brasília |
| 50 | DAUD | Vitória |

> [!CAUTION] OBSERVAÇÃO:
> - No exemplo apresentado, todos os empregados possuem departamento associado, ou seja, não há valores nulos na chave estrangeira.
> - A cardinalidade 1:N é a mais comum em modelos relacionais e cai com frequência em provas.

## 2. Mapeamento Relacionamentos N:M
- Relacionamentos muitos-para-muitos não podem ser implementados diretamente em um banco relacional.
- É obrigatória a criação de uma tabela de associação (tabela intermediária) para representar o relacionamento.
- A tabela de associação contém as chaves estrangeiras das duas tabelas participantes, formando uma chave primária composta.
- Exemplo: empregado trabalha em projeto.
  - Tabela EMPREGADO (CodEmp, Nome);
  - Tabela PROJETO (CodProj, Descricao);
  - Tabela associativa TRABALHA (CodEmp, CodProj).
- A chave primária de TRABALHA é composta por CodEmp + CodProj.
- Regra: o mesmo empregado não pode trabalhar no mesmo projeto mais de uma vez.

### Exemplo Clínica Médica
- Relacionamento N:M entre médico e paciente, com atributo Data da consulta.
- Tabelas:
  - MEDICO (CRM, Nome, Especialidade);
  - PACIENTE (CodPaciente, Nome, DataNasc);
  - CONSULTA (CRM, CodPaciente, Data).
- Chave primária de CONSULTA: composta por CRM + CodPaciente + Data.

### Tabela
| CRM | NOME | ESPECIALIDADE |
|-----|------|---------------|
| 1 | Mauro | Pediatria |
| 2 | Daniel | Ortopedia |
| 3 | Marcela | Ginecologia |
| 4 | Priscila | Hematologia |
| 5 | Vinícius | Oftalmologia |

| CRM | CODPACIENTE | DATA |
|-----|-------------|-------|
| 1 | 50 | 01.01.2011 |
| 2 | 30 | 05.02.2010 |
| 3 | 20 | 02.01.2007 |
| 4 | 40 | 10.10.2002 |
| 5 | 10 | 05.01.2004 |
| 2 | 20 | 10.05.2012 |
| 5 | 30 | 05.05.2005 |
| 5 | 30 | 10.10.2005 |

| CODPACIENTE | NOME | DATANASC |
|-------------|------|----------|
| 10 | João | 10/01/1980 |
| 20 | Maria | 05/01/1995 |
| 30 | Antônio | 10/10/1990 |
| 40 | Marta | 01/01/1994 |
| 50 | Juliana | 01/02/2005 |

> [!TIP] DICAS:
> - A chave primária da tabela de associação pode ser composta por todas as chaves estrangeiras envolvidas, acrescida de atributos que garantam unicidade.
> - A data frequentemente faz parte da chave primária para evitar duplicidade no mesmo dia.

### 2.1 Exemplo com Três Entidades (Fornecedor, Projeto, Material)
- Relacionamento N:M com três entidades participantes.
- Tabela associativa FORNECE contém as chaves estrangeiras de FORNECEDOR, PROJETO e MATERIAL.
- Atributo adicional: Quantidade (exclusivo da associação).
- Chave primária: composta pelas três chaves estrangeiras.
- A quantidade não é chave, portanto pode se repetir.
- Regra: não pode haver repetição da combinação das três chaves simultaneamente.

> [!CAUTION] OBSERVAÇÃO:
> - A nomenclatura das tabelas e colunas com sufixos (ex: F, M, P) é utilizada para facilitar consultas e evitar conflitos em relatórios.
> - O nome de uma coluna não precisa ser único na tabela, mas a chave primária sim.

## 3. Caso Especial: Fusão de Tabelas (Relacionamento 1:1)
- A fusão de tabelas ocorre apenas em relacionamentos 1:1.
- É um caso raro, mas pode ser cobrado em provas.
- Exemplo: país e constituição.
  - Cada país possui uma constituição;
  - Cada constituição pertence a um país.
- Implementação: pode-se criar uma única tabela contendo os atributos de ambas as entidades, ou manter duas tabelas com chave estrangeira compartilhada.

> [!CAUTION] OBSERVAÇÃO:
> - A fusão de tabelas não é utilizada para relacionamentos 1:N ou N:M.
> - O Cespe/CEBRASPE costuma cobrar esse detalhe em questões.

## 4. Caso Especial: Disjunção (Generalização/Especialização)
- Corresponde a situações em que uma entidade pode ser de um tipo ou de outro, de forma exclusiva.
- Exemplo: empregado pode ser advogado, médico ou engenheiro.
- Não há participação total obrigatória.
- Em modelo relacional, a implementação é mais complexa, exigindo restrições robustas para garantir que um empregado não pertença a mais de um tipo simultaneamente.
- Estratégias comuns:
  - Criar uma tabela base com atributos comuns e tabelas específicas para cada subtipo;
  - Utilizar restrições de integridade (CHECK ou triggers) para impedir duplicidade de tipos.

## 5. Regras Gerais de Mapeamento
- Relacionamentos 1:N: chave estrangeira no lado N.
- Relacionamentos N:M: criação de tabela associativa.
- Relacionamentos 1:1: fusão de tabelas ou chave estrangeira com restrição de unicidade.
- Em qualquer caso, a chave primária deve garantir a unicidade das tuplas.

> [!TIP] DICAS:
> - Sempre verifique se a chave estrangeira pode ser nula, conforme a participação da entidade no relacionamento.
> - Em provas de concurso, a banca costuma explorar a diferença entre modelo conceitual e modelo relacional.

## 6. Análise de Questões Comentadas (Conceitos Teóricos)

### 6.1 Modelo Lógico Produto x TipoDeProduto
- Um tipo de produto se relaciona com vários produtos (1:N).
- A chave estrangeira CodigoTipoProduto em Produto referencia TipoDeProduto.
- O modelo lógico já apresenta a visão de implementação e armazenamento, enquanto o modelo conceitual é voltado para o cliente.

### 6.2 Fusão de Tabelas no Modelo ER
- A fusão de tabelas só é obrigatória em relacionamentos 1:1.
- Em relacionamentos 1:N ou N:M, não se fundem tabelas; adicionam-se chaves estrangeiras ou tabelas associativas.

### 6.3 Nomenclatura de Chaves
- Chaves primárias podem ter nomes iguais em entidades distintas, desde que cada tabela mantenha sua própria unicidade.
- O nome da coluna não precisa ser único globalmente, apenas dentro da tabela.

> [!CAUTION] OBSERVAÇÃO:
> - As bancas cobram detalhes sobre nomenclatura e regras de mapeamento.
> - Fique atento ao que é permitido em modelo conceitual versus modelo relacional.

### 6.4 Cardinalidade N:M (Juiz x Assistente)
- Relacionamento N:M exige tabela de ligação (associação).
- A tabela de ligação gera dois relacionamentos 1:N com as tabelas originais.
- Não se cria uma tabela com chave composta exclusiva apenas com IDs; a tabela de ligação deve existir fisicamente.
- Alternativas incorretas:
  - Transformar chaves estrangeiras entre as tabelas originais;
  - Manter relacionamento bidirecional 1:1;
  - Usar chave composta nas tabelas originais.

> [!TIP] DICAS:
> - Questões sobre cardinalidade N:M sempre exigem a criação de uma tabela de ligação.
> - A tabela de ligação é conhecida como tabela própria ou tabela associativa.