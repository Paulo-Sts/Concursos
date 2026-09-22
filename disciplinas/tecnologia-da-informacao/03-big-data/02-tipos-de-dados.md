# Tipos de Dados em Big Data

## 1. Classificação dos Dados
- Os dados são classificados em três categorias principais conforme sua estrutura e organização.

### 1.1 Dados Estruturados
- Definição: informações organizadas em formato fixo e padronizado, armazenados em tabelas com linhas e colunas.
- Onde ficam: bancos de dados relacionais (SQL).
- Vantagens:
  - Fácil armazenamento, busca e consulta com linguagens como SQL;
  - Alta integridade e consistência dos dados.
- Exemplos: registros de vendas (data, produto, valor); cadastros de clientes (nome, CPF, endereço).
- São dados organizados em linhas e colunas, com esquema rígido e definido, incluindo campos, tipos de dados, restrições de integridade, chaves primárias e estrangeiras.
- Representam apenas 20% dos dados que circulam na internet, mas possuem alta relevância.

### 1.2 Dados Semiestruturados
- Definição: possuem alguma organização ou marcação, mas não seguem modelo fixo como os dados estruturados.
- Onde ficam: arquivos em formatos flexíveis ou bancos NoSQL.
- Características:
  - Possuem metadados (informações que descrevem o dado);
  - Estrutura flexível, adaptável a mudanças no formato.
- Utilizam marcações ou pares de chave-valor para organização.
- Não se utiliza SQL para consulta; utilizam-se bibliotecas nas linguagens de programação.
- São armazenados em bancos orientados a documentos (não relacionais).
- Exemplos:
  - Arquivos XML e JSON;
  - Registros de logs de sistemas;
  - Dados de sensores IoT enviados em formato de texto com chaves/valores.

#### 1.2.1 XML (Extensible Markup Language)
- Organização ocorre por meio de tags hierárquicas e aninhadas.
- Exemplo: `<PROFESSOR> <NOME>VITOR</NOME> <IDADE>46</IDADE> </PROFESSOR>`

#### 1.2.2 JSON (JavaScript Object Notation)
- Dados aparecem em pares de chave e valor delimitados por chaves.
- Exemplo: `{NOME: VITOR, IDADE: 46, DISCIPLINAS: IA, BIG DATA}`
- Estrutura flexível: permite que registros tenham campos diferentes.
  - Exemplo: um cadastro de professor pode ter CPF, enquanto outro professor (estrangeiro) não possui esse campo, e ambos são aceitos pela base.

### 1.3 Dados Não Estruturados
- Definição: não possuem formato fixo ou modelo predefinido, dificultando armazenamento e análise por sistemas tradicionais.
- Onde ficam: sistemas de arquivos distribuídos, data lakes e repositórios multimídia.
- Características:
  - Maior desafio para processamento e extração de informações;
  - Exigem técnicas como mineração de texto, processamento de linguagem natural (PLN) e visão computacional.
- Análise não é realizada por sistemas tradicionais de SQL, mas normalmente por inteligência artificial.
- Exemplos:
  - Imagens e vídeos (câmeras de vigilância, redes sociais);
  - Áudios (chamadas gravadas, podcasts);
  - Textos livres (e-mails, posts em redes sociais, documentos escaneados).
- Representam cerca de 80% dos dados que circulam na internet.

> [!TIP] DICAS:
> - Para identificar o tipo de dado, pergunte-se: "É uma tabela?" (estruturado), "Tem tags ou chave-valor?" (semiestruturado), "É imagem, áudio ou texto livre?" (não estruturado).
> - Metadados = dados que descrevem outros dados; característica marcante dos semiestruturados.

> [!CAUTION] OBSERVAÇÃO:
> - Bancos de dados relacionais modernos (Oracle, MySQL) permitem armazenar imagens em colunas, tecnicamente viabilizando dados não estruturados em SQL. No entanto, para arquiteturas de Big Data com grandes volumes, essa prática não é adequada. Em provas, o conceito tradicional prevalece: dados não estruturados não são armazenados em bancos relacionais.
> - O examinador pode usar sinônimos para dificultar a questão, como "estrutura não homogênea" em vez de "estrutura flexível" para dados semiestruturados. É necessário interpretar o que a banca está descrevendo.
> - Uma afirmação pode ser considerada incorreta se for incompleta, mesmo que a parte mencionada esteja correta. Atenção a termos como "apenas", "exclusivamente" e "todos".