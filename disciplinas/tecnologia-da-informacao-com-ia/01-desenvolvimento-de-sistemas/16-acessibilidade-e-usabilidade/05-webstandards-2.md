# Webstandards (HTML) 2

## 1. Linguagem de Ontologia Web (OWL)
- OWL é uma linguagem da Web Semântica criada para representar conhecimento rico e complexo sobre coisas, grupos de coisas e relações entre elas.
- Permite que programas de computador processem esse conhecimento para verificar consistência ou tornar explícitas informações que estavam implícitas.
- Documentos OWL são chamados de ontologias e podem ser publicados na rede, referenciando outras ontologias.
- OWL faz parte da pilha de tecnologias da Web Semântica, juntamente com RDF, RDFS e SPARQL.

| ELEMENTO | SIGNIFICADO | EXEMPLO |
|---|---|---|
| CLASSE | Categoria ou tipo de coisa | Pessoa, veiculo, investigador |
| INDIVÍDUO | Um objeto concreto pertencente a uma classe | Joao, carro123, delegacianorte |
| PROPRIEDADE DE OBJETO | Relação entre dois indivíduos | Investiga, possuiveiculo, lotadoem |
| PROPRIEDADE DE DADO | Relação entre indivíduo e valor literal | Nome, idade, placa, datanascimento |
| AXIOMAS/RESTRIÇÕES | Regras lógicas sobre o domínio | Todo investigador é uma pessoa |

> [!CAUTION] OBSERVAÇÃO: 
> - OWL não é utilizado para montar telas ou para estilização; sua função exclusiva é conferir significado aos dados.

## 2. Sinergia entre WHATWG e W3C
- Em 2019, o Memorando de Entendimento (MOU) definiu que o WHATWG manteria os padrões vivos (Living Standards) de HTML e DOM.
- O W3C encerrou a publicação de especificações concorrentes, focando em acessibilidade, internacionalização, privacidade e segurança.
- O desenvolvimento técnico acelerado no WHATWG é validado por critérios sociais e técnicos do W3C antes de se tornar uma Recomendação oficial.

## 3. Estrutura Semântica e Filosofia da Marcação
- A marcação não deve ser vista como ferramenta de apresentação visual, mas como meio de descrever a função e a natureza da informação.
- HTML representa a estrutura (esqueleto), o CSS a apresentação (aparência) e o JavaScript o comportamento (dinamismo).
- A organização moderna organiza elementos em categorias que determinam quais elementos podem ser filhos de outros no Document Object Model (DOM).
- O elemento raiz <html> delimita o início e fim; <head> contém meta-informações e título; <body> contém o conteúdo visível.

> [!TIP] DICAS: 
> - Utilize apenas um único h1 por página para o título principal, seguindo uma hierarquia lógica (h2, h3) sem pular níveis para garantir a acessibilidade.

## 4. Práticas de Sintaxe e Validação
- O uso de sintaxe rigorosa (estilo XHTML) é recomendado para manter a consistência e evitar falhas de interpretação pelos navegadores.
- Recomendações principais incluem o fechamento explícito de todas as tags e o uso de letras minúsculas para elementos e atributos.
- Valores de atributos devem ser sempre envolvidos por aspas e apresentados em sua forma completa.
- A declaração <!DOCTYPE html> no início do arquivo garante que o navegador utilize o modo de padrões (standards mode).

## 5. Componentes e Acessibilidade
- Tabelas devem representar estritamente dados tabulares com mais de uma dimensão e nunca serem usadas para organizar o layout da página.
- O atributo alt em elementos de imagem é obrigatório para fornecer conteúdo equivalente quando a imagem não carrega ou para leitores de tela.
- O atributo lang no elemento raiz ajuda ferramentas de síntese de voz e tradução a processarem corretamente o idioma do documento.

## 6. Formulários
- Use o elemento <label> para identificar campos e sinalize campos obrigatórios visualmente e no código com o atributo required.
- Agrupe campos relacionados, como opções de múltipla escolha ou blocos de endereço, utilizando <fieldset> e <legend>.
- Prefira tipos de entrada adequados como email, url, number ou date, que auxiliam na validação nativa e ajustam teclados em dispositivos móveis.
- O sistema deve validar a entrada, notificar a conclusão bem-sucedida de tarefas ou exibir alertas contextuais claros em caso de erro.

## 7. Linked Open Data (LOD)
- Para ser considerado Linked Data, o dado deve seguir quatro regras: usar URIs como nomes, usar HTTP URIs para busca, fornecer informações úteis (RDF/SPARQL) e incluir links para outras URIs.
- Linked Open Data permite que pessoas e sistemas encontrem, combinem e reutilizem informações de forma padronizada e conectada.

| CONCEITO | IDEIA CENTRAL |
|---|---|
| OPEN DATA | Dados abertos, disponíveis para acesso e reutilização |
| LINKED DATA | Dados estruturados e conectados por links semânticos |
| LINKED OPEN DATA | Dados abertos + estruturados + conectados na web |

## 8. Sistema de 5 Estrelas do Open Data
- Criado por Tim Berners-Lee para medir a qualidade da abertura dos dados em uma organização.

| ESTRELAS | O QUE SIGNIFICA NA PRÁTICA? | EXEMPLO |
|---|---|---|
| 1 ESTRELA | Dados disponíveis na web sob uma licença aberta | Um pdf com uma tabela de salários |
| 2 ESTRELAS | Dados disponíveis como dados estruturados (formato proprietário) | A mesma tabela em arquivo excel (.xlsx) |
| 3 ESTRELAS | Dados em formato estruturado e não-proprietário | A mesma tabela exportada em formato .csv |
| 4 ESTRELAS | Uso de uris do w3c para identificar coisas | Dados publicados usando rdf e json-ld |
| 5 ESTRELAS | Inclui links para dados de terceiros para dar contexto | Sistema que linka id de cidade ao id do ibge |