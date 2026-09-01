# Conceitos Fundamentais de Dados

## 1. Definições de Dados, Informação e Conhecimento
- Dados são representações simbólicas de informações que requerem interpretação para que seu significado seja extraído,.
- Informação surge a partir do processamento e análise de dados para atribuir-lhes um sentido prático,.
- Conhecimento resulta da reunião de diversas informações em um contexto específico permitindo a identificação de padrões,.
- Sabedoria constitui a consolidação de conhecimentos que orientam a tomada de decisão em uma organização,.
- Exemplo: o valor 37,5 isoladamente é um dado; afirmar que representa a temperatura corporal é informação; saber que indica ausência de febre é conhecimento.

| CONCEITO | DEFINIÇÃO |
|---|---|
| Dado | Representação simbólica bruta |
| Informação | Dado processado com significado |
| Conhecimento | Informação aplicada em contexto |
| Sabedoria | Conhecimento consolidado para decisão |

> [!TIP] DICAS: 
> - A sequência evolutiva para a tomada de decisão é: Dado ⟶ Informação ⟶ Conhecimento ⟶ Sabedoria.

> [!CAUTION] OBSERVAÇÃO: 
> - Tradicionalmente a informação exige participação humana para estruturação e busca de significado, enquanto dados são mais facilmente obtidos por máquinas,.

## 2. Processos Geradores de Dados
- Referem-se a qualquer sistema ou mecanismo que cria ou coleta dados de forma manual ou automatizada.
- Sensores iot: dispositivos que capturam dados do ambiente físico como temperatura e pressão.
- Transações financeiras: sistemas de pagamento e compras que registram informações transacionais,.
- Redes sociais: interações humanas que geram conteúdos como postagens, curtidas e comentários.
- Sistemas corporativos: ferramentas como erp e crm que geram dados a partir de operações empresariais,.

> [!CAUTION] OBSERVAÇÃO: 
> - Processos automatizados não exigem participação humana direta na geração dos dados, ao contrário dos processos manuais.

## 3. Classificação dos Dados por Natureza
- Dados quantitativos: representam valores que podem ser medidos e expressos numericamente.
- Dados contínuos: pertencem ao conjunto dos números reais e apresentam um intervalo infinito de possibilidades como peso e altura.
- Dados discretos: representam valores inteiros e contáveis como a quantidade de filhos por casal,.
- Dados qualitativos: descrições que não possuem uma representação numérica direta.
- Dados nominais: categorias que não apresentam qualquer relação de ordem entre si como cor dos olhos ou bairro de residência,.
- Dados ordinais: categorias que possuem uma ordem implícita como nível de escolaridade ou níveis de satisfação,.

| TIPO | SUBDIVISÃO | EXEMPLO |
|---|---|---|
| Quantitativo | Contínuo | Temperatura e altura |
| Quantitativo | Discreto | Número de filhos |
| Qualitativo | Nominal | Sexo e cor dos olhos |
| Qualitativo | Ordinal | Escolaridade e classificação |

> [!TIP] DICAS: 
> - Dados discretos ⟶ Números inteiros.
> - Dados contínuos ⟶ Números decimais (reais).

## 4. Estrutura dos Dados
- Dados estruturados: organizados em tabelas com linhas e colunas possuindo um esquema definido previamente,.
- Dados semiestruturados: possuem uma estrutura flexível que não segue uma tabela rígida mas utiliza marcações para organização,.
- Exemplos de semiestruturados: arquivos nos formatos xml, json e bson,.
- Dados não estruturados: informações armazenadas em formato livre e bruto sem estrutura pré-definida,.
- Exemplos de não estruturados: textos livres, imagens, vídeos e áudios,.

| ESTRUTURA | CARACTERÍSTICA | FORMATO COMUM |
|---|---|---|
| Estruturado | Rígido e tabular | Bancos sql e planilhas |
| Semiestruturado | Tags e flexibilidade | Xml e json |
| Não estruturado | Formato bruto | Vídeos e imagens |

> [!CAUTION] OBSERVAÇÃO: 
> - O simples armazenamento de dados não estruturados em uma tabela de banco de dados relacional não os torna estruturados.