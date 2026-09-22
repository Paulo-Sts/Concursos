# Metadados

## 1. Conceito Fundamental de Metadados
- Metadados são dados que descrevem outros dados, fornecendo contexto e enriquecendo a informação original.
- O objetivo principal é registrar e organizar dados de forma estruturada, facilitando a padronização, indexação e recuperação eficiente das informações.

## 2. Exemplos Práticos de Metadados
- Pesquisa em biblioteca: autor, área de conhecimento e ano de publicação auxiliam na localização do livro.
- Questões para concursos: indexação por banca examinadora, disciplina e tipo de questão (certo/errado, múltipla escolha).
- Imagem JPEG: nome do arquivo, autor e data de criação.

### 2.1 Interpretação de Dados
- Um valor isolado (como 37,5) só faz sentido com metadados que indicam contexto (ex.: tabela de prontuário médico, coluna de temperatura do paciente).

> [!TIP] DICAS:
> - Metadados respondem à pergunta "o que representa este dado?".
> - Eles são essenciais para transformar dados brutos em informação útil.

## 3. Estrutura e Representação de Metadados

### 3.1 Dados Estruturados (Tabelas)
- Metadados incluem:
  - Nome da tabela;
  - Nome dos campos (colunas);
  - Tipo de dados (inteiro, string, etc.).

### 3.2 Dados Semiestruturados (XML e JSON)
- XML: metadados representados por tags.
- JSON: metadados representados por pares chave-valor.
- Exemplo JSON:
```json
{
  "Nome": "Victor",
  "Disciplinas": ["Banco de Dados", "Estruturas de Dados"]
}
```

### 3.3 Grafos
- Nós representam entidades (ex.: "Vitor").
- Metadados descrevem atributos do nó (ex.: nome, profissão).
- Arestas representam relações entre entidades.

### 3.4 Localização de Armazenamento
- Metadados podem indicar onde o dado está armazenado (URL, pasta, estante, etc.).

## 4. Funções e Aplicações dos Metadados

### 4.1 Funções Principais
- Identificar o recurso informacional.
- Descrever o conteúdo e as características do objeto.
- Facilitar a busca, localização, acesso e recuperação da informação.
- Auxiliar na gestão da informação (versão, acesso, localização).
- Tornar ferramentas de busca mais efetivas, especialmente em bibliotecas digitais.

### 4.2 Tipos de Informações Contidas nos Metadados
- Natureza bibliográfica do objeto (autor, título, assunto, ISBN).
- Localização física ou digital do objeto.
- Formato do arquivo e sistema necessário para acesso.
- Dados de preservação e armazenamento físico.
- Data de criação e de atualização do documento.

### 4.3 Padronização
- Metadados podem seguir padrões internacionais, como o Dublin Core.
- A padronização garante consistência na descrição de objetos (ex.: livro sempre descrito com autor, ano, volume, edição).

### 4.4 Autodescrição e Documentação
- Metadados podem fornecer documentação própria que subsidia o gerenciamento dos recursos informacionais.
- Permitem que o recurso permaneça acessível e compreensível no futuro.

> [!CAUTION] OBSERVAÇÃO:
> - Metadados não se limitam à descrição física de componentes; abrangem informações amplas sobre o recurso informacional.
> - Não são descrições longas e subjetivas; são específicas, objetivas e padronizadas para facilitar a organização e recuperação.

## 5. Armazenamento de Metadados
- Podem estar incorporados dentro do dado (ex.: tags HTML).
- Podem ser armazenados separadamente em arquivos de suporte.
- Independente da forma, permitem que os dados sejam organizados, pesquisados e utilizados de forma mais eficiente.

## 6. Importância em Bibliotecas Digitais
- São a principal forma de acesso às informações e diferentes conteúdos encontrados em documentos digitais.
- Essenciais para a criação, organização e manipulação de informações em sistemas online que armazenam documentos e livros em formato digital (ex.: PDFs).

> [!TIP] DICAS:
> - Em provas, metadados frequentemente aparecem associados à organização, recuperação e contexto da informação.
> - Cuidado com pegadinhas que confundem metadados com descrições subjetivas ou conteúdo completo do documento.