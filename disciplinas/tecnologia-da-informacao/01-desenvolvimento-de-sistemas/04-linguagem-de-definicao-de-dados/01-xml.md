# Tecnologias XML e Visão Geral

## 1. Introdução e Origem
- XML é a sigla para eXtensible Markup Language, traduzida como Linguagem de Marcação Extensível.
- Foi criada no final dos anos 90 pelo W3C (World Wide Web Consortium) como uma simplificação do SGML.
- O objetivo principal é o transporte e intercâmbio de informações de forma estruturada entre sistemas e linguagens de programação diferentes.
- Trata-se de uma tecnologia robusta e burocrática que perdeu espaço para linguagens mais simples como JSON, YAML e TOML.
- A complexidade e formalidade fazem com que o uso atual seja mais específico, especialmente em cenários que exigem maior segurança no intercâmbio de dados.

## 2. Características Principais
- Extensível: permite que os usuários definam suas próprias etiquetas (tags) e estruturas de dados ⟶ as regras de criação são definidas por documentos como DTD e XSD.
- Autodescritiva: os dados são acompanhados por etiquetas que explicam o significado do conteúdo.
- Independência: facilita o compartilhamento de dados na internet de forma padronizada.

## 3. Estrutura do Documento XML

### 3.1 Prólogo ou Declaração XML
- Especifica a versão da linguagem e a codificação de caracteres utilizada (exemplo: encoding="UTF-8").
- Serve para garantir que o documento seja interpretado corretamente por diferentes processadores.

### 3.2 Elemento Raiz
- Todo documento XML deve conter obrigatoriamente um único elemento raiz.
- Este elemento serve como um contêiner que encapsula todos os outros nós do documento.

### 3.3 Elementos e Tags
- Formam a estrutura hierárquica do arquivo.
- Devem possuir etiquetas de abertura e fechamento para serem considerados válidos.
- Podem conter texto puro, outros elementos aninhados ou uma mistura de ambos.

### 3.4 Atributos
- Fornecem informações adicionais e propriedades aos elementos.
- São comumente utilizados para identificar elementos de forma única.

### 3.5 Comentários
- Podem ser inseridos em qualquer local onde o conteúdo seja permitido.
- Sintaxe: <!-- conteúdo do comentário -->.
- São ignorados pelos processadores XML e servem apenas para documentação interna.

> [!TIP] DICAS: 
> - O prólogo é opcional ⟶ se omitido, o documento ainda pode ser processado (parciado), mas podem ocorrer falhas de validação.

> [!CAUTION] OBSERVAÇÃO: 
> - Regras rígidas de formatação ⟶ esquecer o fechamento de uma tag ou a barra de fechamento torna o documento mal formado e gera erros de processamento.
> - Atributos devem obrigatoriamente estar entre aspas.

#### Exemplo
```xml
<?xml version="1.0" encoding="UTF-8"?>
<pontos_turisticos>
  <ponto_turistico id="1">
    <nome>Catedral Metropolitana de Brasília</nome>
    <arquiteto>Oscar Niemeyer</arquiteto>
    <inauguracao>1970</inauguracao>
    <descricao>A Catedral de Brasília.</descricao>
  </ponto_turistico>
  <ponto_turistico id="2">
    <nome>Palácio da Alvorada</nome>
    <arquiteto>Oscar Niemeyer</arquiteto>
    <inauguracao>1958</inauguracao>
    <descricao>Residência oficial do Presidente da República.</descricao>
  </ponto_turistico>
  <ponto_turistico id="3">
    <nome>Palácio Itamaraty</nome>
    <arquiteto>Oscar Niemeyer</arquiteto>
    <inauguracao>1970</inauguracao>
    <descricao>Sede do Ministério das Relações Exteriores.</descricao>
  </ponto_turistico>
</pontos_turisticos>
```

## 4. Qualidade e Validação do Documento

### 4.1 Documento Bem Formado
- É aquele que segue estritamente as regras sintáticas básicas da linguagem.
- Regras básicas:
  - Possuir uma única raiz;
  - Tags fechadas e aninhadas corretamente;
  - Atributos entre aspas;
  - Prólogo, se houver, posicionado no início.

### 4.2 Documento Válido
- É um documento que, além de ser bem formado, respeita as regras de um esquema de definição.
- Os esquemas (DTD ou XSD) determinam quais tags são permitidas, sua ordem, obrigatoriedade e tipos de dados.

#### Exemplo 1
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogo>
  <produto id="1234">
    <nome>Caneta</nome>
    <preco>1.50</preco>
  </produto>
</catalogo>
```

#### Exemplo 2
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogo xmlns:xsi="[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)"
  xsi:noNamespaceSchemaLocation="catalogo.xsd">
  <produto id="1234">
    <nome>Caneta</nome>
    <preco>1.50</preco>
  </produto>
</catalogo>
```

## 5. Namespaces e Unicidade
- Método para qualificar nomes de elementos e atributos associando-os a nomes de domínios da internet.
- Finalidade: evitar conflitos de nomes quando se combinam documentos XML de fontes distintas.
- Associa um prefixo a um identificador único (URI) para distinguir elementos com nomes iguais em contextos diferentes.

> [!CAUTION] OBSERVAÇÃO: 
> - O identificador do namespace (URI) parece um site, mas funciona apenas como um nome único ⟶ o sistema não precisa acessar a internet para obter os dados.

#### Exemplo
```xml
<?xml version="1.0"?>
<informatica xmlns:hw="[http://www.exemplo-hardware.com/equipamentos](http://www.exemplo-hardware.com/equipamentos)">
  <hw:computador>
    <hw:tipo>Desktop</hw:tipo>
    <hw:processador>Intel i7</hw:processador>
    <hw:memoria>16GB RAM</hw:memoria>
  </hw:computador>
  <hw:monitor>
    <hw:polegadas>21,5</hw:polegadas>
    <hw:resolucao>1280x1090</hw:resolucao>
  </hw:monitor>
</informatica>
```

## 6. Ecossistema de Tecnologias XML

| TECNOLOGIA | DESCRIÇÃO | FUNÇÃO PRINCIPAL |
|---|---|---|
| XML | Linguagem de marcação extensível | Estruturação de dados de forma hierárquica e flexível |
| XML DOM | Document object model | Permite manipular e navegar pelos nós do XML via programação |
| DTD | Document type definition | Define regras básicas de validação e estrutura do documento |
| XSD | XML schema definition | Evolução do dtd com suporte a tipos de dados complexos e regex |
| XPATH | Linguagem de consulta | Seleciona nós específicos e extrai informações de forma eficiente |
| XQUERY | Linguagem de consulta poderosa | Realiza consultas complexas e constrói novos dados a partir de coleções xml |
| XSLT | Linguagem de folhas de estilo | Transforma documentos xml em outros formatos como html ou texto |

> [!TIP] DICAS: 
> - O XSD é considerado mais avançado e preciso que o DTD por suportar namespaces e definições detalhadas de tipos de dados.
> - XSLT é a ferramenta chave para apresentação ⟶ transforma o dado bruto (XML) em algo visual (HTML).