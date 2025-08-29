# Tipos de Dados

## Dados estruturados
- Possuem estrutura rígida e bem definida.
- Armazenados em tabelas, com linhas e colunas.
- Esquema definido antes da existência dos dados.
- Organização semântica clara (atributos, tipos, domínios).
- Exemplos: bancos de dados relacionais (SQL), planilhas do Excel.
- Facilmente recuperáveis, manipuláveis e consultáveis.
- Representam cerca de 20% dos dados institucionais.

#### Características
- Estrutura independente dos dados.
- Esquema prescritivo (define o que os dados devem ser).
- Fáceis de proteger e gerenciar com ferramentas tradicionais.
- Menor consumo de espaço de armazenamento.

## Dados não estruturados
- Não possuem estrutura definida.
- Não seguem modelo pré-estabelecido.
- Exemplos: textos, PDFs, imagens, áudios, vídeos, e-mails.
- Podem usar metadados para organização externa.
- Representam cerca de 80% dos dados institucionais.
- Exigem maior espaço de armazenamento.

#### Características
- Difíceis de consultar e analisar automaticamente.
- Estrutura inexistente ou muito flexível.
- Dependem de metadados para classificação.

## Dados semiestruturados
- Possuem estrutura flexível e implícita.
- Estrutura definida durante ou após a criação dos dados.
- Auto-descritivos (a estrutura está nos próprios dados).
- Exemplos: JSON, XML, CSV.
- Podem ter partes estruturadas e não estruturadas.

#### Características
- Estrutura irregular e evolutiva.
- Não possuem esquema rígido.
- Facilmente adaptáveis a mudanças.
- Estrutura descritiva (não prescritiva).

## Comparativo
- Estruturados:
  - Esquema definido antes.
  - Rígidos e regulares.
  - Independentes dos dados.
  - Bidimensionais (tabelas).
- Semiestruturados:
  - Esquema definido durante/após.
  - Flexíveis e irregulares.
  - Estrutura implícita nos dados.
  - Podem ser hierárquicos (ex: XML, JSON).

## Metadados
- Dados que descrevem outros dados.
- Usados para classificar e organizar dados não estruturados.
- Armazenados em catálogos ou dicionários de dados.
- Exemplo: esquema de um banco de dados.

## Aplicação
- Dados estruturados: ideais para consultas rápidas e relatórios.
- Dados não estruturados: requerem processamento adicional (ex: mineração de texto).
- Dados semiestruturados: usados em integração de sistemas e APIs.

## Observação
- Dados semiestruturados são uma ponte entre os estruturados e não estruturados.
- Ferramentas como Excel e Access são comuns para dados estruturados.
- Formatos como JSON e XML são comuns para dados semiestruturados.