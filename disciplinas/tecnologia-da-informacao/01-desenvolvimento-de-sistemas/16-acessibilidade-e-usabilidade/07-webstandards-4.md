# Webstandards (Acessibilidade XML) 4

## 1. Fundamentos de Acessibilidade e Padrões W3C
- A acessibilidade é um conceito de inclusão que afeta o desenvolvimento de sistemas, abrangendo design visual e interativo para garantir acesso a todas as pessoas.
- A arquitetura de acessibilidade do W3C fundamenta-se em três pilares principais: Web Content Accessibility Guidelines (WCAG), Authoring Tool Accessibility Guidelines (ATAG) e User Agent Accessibility Guidelines (UAAG).
- Princípios do WCAG: o conteúdo deve ser baseado no acrônimo PORC, que significa Perceptível, Operável, Compreensível e Robusto.
- Níveis de conformidade: as diretrizes de acessibilidade possuem três níveis de sucesso denominados A, AA e AAA.

### 1.1 Práticas de Acessibilidade em Interfaces
- Para usuários com deficiência visual, a acessibilidade deve ser garantida através de navegação facilitada por teclado e descrições textuais de elementos gráficos para leitura em áudio.
- O uso de alto contraste nas cores é uma diretriz recomendada para auxiliar o acesso de pessoas com daltonismo.
- No desenvolvimento de formulários, deve-se associar uma etiqueta (label) a cada controle para ajudar leitores de tela a identificar a entrada necessária.
- Para conteúdos em áudio, deve-se fornecer transcrição de texto para garantir o acesso de pessoas com deficiência auditiva.
- Dificuldades cognitivas: o design deve utilizar ícones, símbolos e termos familiares para facilitar o entendimento do conteúdo.

> [!CAUTION] OBSERVAÇÃO: 
> - O W3C não recomenda um formato gráfico específico (como JPG) para acessibilidade; a recomendação é que haja sempre uma alternativa em texto para qualquer conteúdo não textual.

## 2. XML (Linguagem de Marcação Extensível)
- XML é um formato de texto simples e flexível, derivado do SGML, utilizado para a formação de dados semiestruturados.
- Sua função principal é armazenar e transportar informações de maneira independente de hardware e software, facilitando a interoperabilidade entre sistemas.
- Diferente do HTML, que possui tags fixas para estrutura de páginas, o XML permite que o desenvolvedor crie suas próprias tags personalizadas conforme o escopo do projeto.
- Um documento XML é considerado bem formado quando respeita todas as regras sintáticas da linguagem.
- Um documento XML é considerado válido quando, além de bem formado, obedece a regras adicionais definidas por um DTD (Document Type Definition) ou esquema.

| CARACTERÍSTICA | EXPLICAÇÃO |
|---|---|
| Extensível | Permite a criação de tags personalizadas para cada necessidade |
| Estruturado | Organiza dados de forma hierárquica com elementos pai e filhos |
| Textual | Baseado em texto simples, o que garante portabilidade e suporte ao unicode |
| Independente | Pode ser operado em diferentes sistemas e linguagens de programação |
| Focado em dados | Serve prioritariamente para representar e transportar informações |
| Processável | Permite que programas consigam ler, validar e transformar os documentos |

### 2.1 Regras de Sintaxe e Formatação XML
- As tags XML são case sensitive, ou seja, diferenciam letras maiúsculas de minúsculas.
- Todos os elementos devem possuir tags de abertura e de fechamento correspondentes.
- Valores de atributos devem obrigatoriamente estar envolvidos por aspas.
- Elementos vazios podem ser representados de forma abreviada, como no exemplo: <foto/>.
- Caracteres especiais devem ser escapados para não causarem erros de processamento.

### 2.2 Regras para Nomeação de Elementos
- Pode começar com letras ou com o caractere underscore (_);
- É proibido começar nomes de elementos com números ou hífens;
- Não deve conter espaços em branco no nome do elemento;
- Pode conter hífens, pontos ou underscores no meio do nome.

> [!TIP] DICAS: 
> - Para concursos: Lembre-se que XML foca no que o dado é (significado), enquanto HTML foca em como o dado aparece na tela.

## 3. XSL (Linguagem Extensível de Folhas de Estilo)
- XSL é uma família de recomendações do W3C utilizada para a transformação e apresentação de documentos XML.
- Enquanto o XML provê a estrutura do dado, o XSL confere a estilização e a forma de apresentação.
- Diferença técnica: XSL não apenas formata (como o CSS faz com o HTML), mas também tem a capacidade de transformar o documento XML em outros formatos.

### 3.1 Componentes do XSL
- XSLT: linguagem utilizada para transformar documentos XML em outros formatos, como HTML, texto ou PDF;
- XPath: linguagem de navegação utilizada para localizar ou acessar partes específicas dentro de um documento XML;
- XSL-FO: vocabulário utilizado para definir a formatação visual, sendo muito aplicado na geração de documentos para impressão ou PDFs.

## 4. Tecnologias de Interoperabilidade e Dados
- Web Services: componentes de aplicações que permitem a comunicação e o uso de recursos através da web.
- WSDL (Web Services Description Language): linguagem baseada em XML recomendada pelo W3C para descrever as funcionalidades e detalhes técnicos de um Web Service.
- SOAP (Simple Object Access Protocol): protocolo leve baseado em XML utilizado para a troca de mensagens estruturadas em ambientes distribuídos.
- RDF (Resource Description Framework): modelo padrão para intercâmbio de dados na web que facilita a integração de informações através de triplas.

### 4.1 Estrutura de Triplas RDF
- O modelo RDF representa informações seguindo a lógica: Sujeito ⟶ Predicado ⟶ Objeto.

| PARTE DA TRIPLA | FUNÇÃO NA ESTRUTURA | EXEMPLO |
|---|---|---|
| Sujeito | Recurso sobre o qual se está falando | Brasília |
| Predicado | Relação ou propriedade que conecta os elementos | éCapitalDe |
| Objeto | Valor ou outro recurso relacionado ao sujeito | Brasil |

### 4.2 Interfaces de Processamento: DOM e SAX
- DOM (Document Object Model): carrega o documento XML inteiramente na memória, criando uma estrutura de árvore navegável.
- SAX (Simple API for XML): interface orientada a eventos que processa o documento parte por parte, sendo mais leve em termos de consumo de memória.

> [!CAUTION] OBSERVAÇÃO: 
> - Em provas de TI, é comum a comparação entre DOM e SAX. Grave que o DOM é baseado em árvore (memória total) e o SAX é baseado em eventos (processamento sequencial).