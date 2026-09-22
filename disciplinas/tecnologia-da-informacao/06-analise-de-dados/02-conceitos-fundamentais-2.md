# Conceitos Fundamentais de Dados 2

## 1. Formatos Comuns de Arquivos de Dados
- TXT (Texto Puro): contém dados em formato de texto simples sem estruturação formal além de quebras de linha.
- Características do TXT: apresenta facilidade de abertura, porém demonstra ineficiência para o gerenciamento de grandes volumes de dados ou metadados.
- CSV (Comma-Separated Values): armazena dados tabulares em texto simples onde os valores são separados por vírgulas ou outros delimitadores.
- Limitações do CSV: não possui bom desempenho com dados complexos, hierárquicos ou não estruturados.
- XLSX (Excel): formato binário proprietário da microsoft utilizado para o armazenamento de planilhas.
- Funcionalidades do XLSX: permite a aplicação de formatação rica, macros e fórmulas, exigindo bibliotecas específicas para manipulação automatizada.

| FORMATO | NATUREZA | CARACTERÍSTICA PRINCIPAL |
|---|---|---|
| Txt | Texto simples | Ineficiente para grandes volumes |
| Csv | Texto simples | Armazenamento tabular em linha |
| Xlsx | Binário | Suporte a fórmulas e macros |

> [!CAUTION] OBSERVAÇÃO: 
> - O processamento de um arquivo CSV exige a leitura integral de cada linha pelo sistema, mesmo que apenas algumas colunas sejam necessárias.
> - Metadados em arquivos de texto puro geralmente exigem uma estrutura de chave e valor que é mais adequada a formatos como JSON ou XML.

## 2. Dados Semiestruturados e Hierárquicos
- XML (Extensible Markup Language): empregado para armazenar dados de forma estruturada e hierárquica por meio de marcações conhecidas como tags.
- Aplicação do XML: amplamente utilizado para o intercâmbio de dados entre sistemas, embora possa ser verboso em grandes volumes.
- JSON (JavaScript Object Notation): formato leve e legível para humanos frequentemente utilizado em apis para a troca de informações.
- Estrutura do JSON: baseia-se em pares de chave e valor e suporta estruturas hierárquicas de forma mais eficiente que o XML.

| FORMATO | CLASSIFICAÇÃO | ESTRUTURA |
|---|---|---|
| Xml | Semiestruturado | Marcações e tags hierárquicas |
| Json | Semiestruturado | Pares de chave e valor |

> [!CAUTION] OBSERVAÇÃO: 
> - Diferente do que algumas bancas podem sugerir, arquivos XML e JSON são classificados tecnicamente como dados semiestruturados.

## 3. Apache Parquet
- Formato de armazenamento de dados em colunas open-source otimizado para leitura e escrita eficiente.
- Contexto de uso: voltado para ambientes de big data e sistemas analíticos distribuídos como hadoop, spark e amazon s3.
- Mecanismo de operação: as operações são realizadas em um subconjunto de colunas sem a necessidade de carregar o arquivo inteiro na memória.
- Vantagem de desempenho: permite que atualizações em uma coluna ocorram diretamente nela sem percorrer todo o conjunto de dados linha a linha.

| CARACTERÍSTICA | CSV | JSON | PARQUET |
|---|---|---|---|
| Estrutura | Linha | Hierárquico | Colunar |
| Compactação | Nenhuma (grande) | Opcional | Alta |
| Leitura seletiva | Não | Não | Sim (colunas) |
| Suporte a big data | Limitado | Limitado | Otimizado |
| Desempenho de leitura | Lento | Médio | Rápido |

> [!TIP] DICAS: 
> - O formato Parquet é a escolha principal em ciência de dados e inteligência artificial para o armazenamento de grandes datasets.

### 3.1 Tipos de Dados Suportados
- Boolean ⟶ booleano de 1 bit para verdadeiro ou falso;
- Int32 e Int64 ⟶ inteiros com sinal de 32 e 64 bits;
- Int96 ⟶ utilizado principalmente para o armazenamento de timestamps;
- Float e Double ⟶ valores de ponto flutuante em formato ieee;
- Byte_array ⟶ cadeias de bytes de comprimento arbitrário;
- Fixed_len_byte_array ⟶ arrays de bytes com comprimento fixo.

### 3.2 Metadados e Organização
- Metadados globais: descrevem a versão do formato, o esquema das colunas, o número total de linhas e os tipos de compressão aplicados.
- Metadados de bloco: referem-se à segmentação do arquivo (sharding) e contêm estatísticas como valores mínimos, máximos e contagem de nulos por bloco.
- Metadados de coluna: incluem o nome, tipo de dado, estatísticas específicas e os métodos de codificação e compressão daquela coluna.

> [!CAUTION] OBSERVAÇÃO: 
> - O uso de estatísticas nos metadados permite otimizações importantes como a eliminação de blocos inteiros que não contenham os valores buscados pelo usuário.