# Data Warehouse

## 1. Data Warehouse (DW)
- Repositório centralizado e integrado de dados estruturados, projetado para suportar análise e geração de relatórios.
- Fornece visão consolidada e histórica dos dados de uma organização.
- Os dados são organizados em modelo dimensional.
- Os usuários podem executar consultas ad hoc, criar relatórios personalizados, aplicar técnicas estatísticas e realizar análises avançadas para obter insights e tomar decisões informadas.
- Mantém histórico de dados, permitindo acesso a informações de períodos anteriores para identificação de tendências e padrões ao longo do tempo.

> [!TIP] DICAS:
> - O DW é um banco de dados utilizado no nível estratégico da organização (alta administração).
> - É otimizado para recuperação de dados, não para processamento rotineiro de transações.

> [!CAUTION] OBSERVAÇÃO:
> - O DW não substitui os bancos de dados operacionais; serve como repositório para análise.
> - O DW não é um dispositivo de armazenamento como HD ou processador; é um banco de dados.

## 2. Características Fundamentais do Data Warehouse
- O DW possui quatro características principais, segundo Inmon.

### 2.1 Orientado a Assunto
- Os dados são organizados por temas de interesse da organização (ex: vendas, clientes, produtos) e não por aplicações específicas.
- Foco no assunto de análise, não no processo de negócio.

> [!CAUTION] OBSERVAÇÃO:
> - Exemplo: em uma organização de arrecadação de impostos, os dados são organizados pelo imposto; o contribuinte é apenas uma dimensão.
> - O DW é orientado a assunto, enquanto os bancos transacionais são orientados a aplicações.

### 2.2 Integrado
- Os dados são provenientes de múltiplas fontes (internas e externas à organização).
- Passam pelo processo de ETL (Extrair, Transformar, Carregar) antes de serem armazenados.
- O DW pode fornecer um modelo de dados comum para diferentes áreas, independentemente da fonte.

> [!CAUTION] OBSERVAÇÃO:
> - A integração dificulta o trabalho do analista, pois exige lidar com redundância de informações.
> - Os dados não são inseridos em seu formato original; passam por transformação no ETL.

### 2.3 Não Volátil
- Após inseridos no DW, os dados não podem ser alterados ou removidos.
- Não há operações de atualização, alteração ou exclusão de registros específicos.
- Não há necessidade de bloqueio por concorrência de usuários ao acesso.

> [!TIP] DICAS:
> - "Não volátil" significa: uma vez inserido, o dado não muda. Isso facilita a diferenciação do DW em relação aos sistemas OLTP.
> - No DW, não se mexe nos dados após a carga.

### 2.4 Variável no Tempo
- O DW mantém dados históricos de longos períodos.
- Permite análises de série temporal e identificação de tendências.
- Os dados são armazenados com referência temporal (ex: data da transação).

> [!TIP] DICAS:
> - O DW é variável no tempo, mas NÃO é volátil (os dados históricos permanecem inalterados).
> - Suporta análises de evolução de valores ao longo de grande janela temporal.

> [!CAUTION] OBSERVAÇÃO:
> - Um data warehouse não mostra necessariamente o status atual; foca em dados históricos.

## 3. Níveis Organizacionais de Aplicação do DW
- Nível Estratégico (alta administração).
- Nível Gerencial (gestão de processos de negócio).
- O DW contém dados sumarizados para apoio à decisão nesses níveis.

> [!TIP] DICAS:
> - As ferramentas de BI que utilizam DW são adequadas para os níveis gerencial e estratégico.
> - O DW não é utilizado no nível operacional (uso diário da empresa).

> [!CAUTION] OBSERVAÇÃO:
> - Os dados no DW são sumarizados (não detalhados como nos sistemas transacionais).

## 4. Data Warehouse vs. Banco de Dados Transacional (OLTP)
| CARACTERÍSTICA | DATA WAREHOUSE | BANCO DE DADOS TRANSACIONAL (OLTP) |
|----------------|----------------|-------------------------------------|
| Finalidade | Orientado a assunto de análise | Orientado a aplicações de negócio |
| Volatilidade | Não volátil | Volátil (alterações constantes) |
| Temporalidade | Variável no tempo (histórico) | Dados atuais |
| Nível de uso | Estratégico e gerencial | Operacional |
| Tipo de dado | Sumarizados | Detalhados |
| Operações | Leitura/consulta | Inclusão, alteração, exclusão |
| Otimização | Recuperação de dados | Processamento de transações |

> [!TIP] DICAS:
> - A diferença funcional entre OLTP e DW: o transacional é orientado a aplicações de negócio; o DW é orientado a assuntos de análise.
> - No OLTP, os dados sofrem alterações (inclusão, alteração, exclusão); no DW, os dados são filtrados e limpos antes da carga.