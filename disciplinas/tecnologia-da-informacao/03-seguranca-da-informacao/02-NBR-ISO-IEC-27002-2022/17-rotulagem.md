# ISO/IEC 27002:2022 - Rotulagem de Informações

## 1. Definição
- O controle é do tipo preventivo.
- As propriedades de segurança envolvidas são a tríade (confidencialidade, integridade e disponibilidade).
- Os conceitos de segurança cibernética abrangem a proteção.
- As capacidades operacionais são voltadas à proteção da informação.
- O domínio de segurança contempla defesa e proteção.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|------------------------------------------|-------------------------------------|--------------------------|-----------------------|
| Preventivo       | Confidencialidade; Integridade; Disponibilidade | Proteger | Proteção da informação | Defesa; Proteção |

### 1.1 Controle
- Um conjunto adequado de procedimentos para rotulagem de informações deve ser desenvolvido e implementado.
- Os procedimentos devem estar de acordo com o esquema de classificação de informações adotado pela organização.
- A rotulagem deve estar alinhada ao que foi desenvolvido e implementado no esquema de classificação de informações.

> [!CAUTION] OBSERVAÇÃO: 
> - A rotulagem depende diretamente do esquema de classificação de informações abordado em tópico anterior (5.12). Sem classificação definida, não há como rotular adequadamente.

### 1.2 Propósito
- Facilitar a comunicação da classificação das informações.
- Apoiar a automação da gestão e tratamento das informações.

## 2. Orientação

### 2.1 Abrangência dos Procedimentos
- Os procedimentos para rotulagem de informações devem abranger informações e outros ativos associados em todos os formatos.
- A rotulagem deve refletir o regime de classificação estabelecido em 5.12.
- Os rótulos devem ser facilmente reconhecíveis.

### 2.2 Dependência do Tipo de Mídia
- Os procedimentos devem orientar onde e como as etiquetas são anexadas.
- A forma de rotulagem depende de como as informações são acessadas ou os ativos são tratados.
- A rotulagem varia conforme os tipos de mídia de armazenamento utilizados.

> [!CAUTION] OBSERVAÇÃO: 
> - Mídias como fitas de backup constituem um tipo de mídia.
> - HDs internos de máquinas, servidores, endpoints e equipamentos de usuários constituem outro tipo de mídia.
> - Há dependência do procedimento em relação à mídia utilizada.

### 2.3 Definições dos Procedimentos
- Os procedimentos podem definir:

  - Casos em que a rotulagem é omitida (por exemplo, rotulagem de informações não confidenciais para reduzir cargas de trabalho).

  > [!TIP] DICAS: 
  > - Sendo público, não possui rótulo, pois não há classificação que exija a rotulagem.
  > - Diminui-se a carga de trabalho ao não rotular o que não é necessário.

  - Como rotular informações enviadas ou armazenadas em meios eletrônicos ou físicos ou qualquer outro formato.
  - Como lidar com casos em que a rotulagem não é possível (por exemplo, devido a restrições técnicas).

### 2.4 Técnicas de Rotulagem
- Exemplos de técnicas de rotulagem incluem:
  - Rótulos físicos;
  - Cabeçalhos e rodapés;
  - Metadados;
  - Marca d'água;
  - Carimbos de borracha.

### 2.5 Metadados
- Informações digitais devem utilizar metadados para identificar, gerenciar e controlar as informações.
- Os metadados são especialmente importantes no que diz respeito à confidencialidade.
- Os metadados também permitem a busca eficiente e correta das informações.
- Os metadados facilitam os sistemas para interagir e tomar decisões com base nos rótulos de classificação anexados.
- Os procedimentos devem descrever:
  - Como anexar metadados às informações;
  - Quais rótulos usar;
  - Como os dados sejam tratados, de acordo com o modelo de informações da organização e a arquitetura de TIC.
- Metadados adicionais relevantes devem ser incorporados pelos sistemas quando eles tratam informações dependendo de suas propriedades de segurança da informação.

> [!CAUTION] OBSERVAÇÃO: 
> - Metadados são dados sobre os dados, como data de criação, autor, localidade e dispositivo utilizado.
> - Não constituem o conteúdo da informação, mas dados relacionados a ela.
> - Servem para identificá-la, gerenciá-la e controlá-la, especialmente no que diz respeito à confidencialidade.

### 2.6 Conscientização e Treinamento
- O pessoal e outras partes interessadas devem estar cientes dos procedimentos de rotulagem.
- Todo o pessoal deve ter treinamento necessário para assegurar que as informações sejam corretamente rotuladas e tratadas adequadamente.

### 2.7 Saída de Sistemas
- A saída de sistemas que contenham informações classificadas como sensíveis ou críticas deve conter um rótulo de classificação adequado.

## 3. Outras Informações

### 3.1 Requisito Fundamental
- A rotulagem de informações classificadas é um requisito fundamental para o compartilhamento de informações.

### 3.2 Metadado Adicional
- Outro metadado útil que pode ser anexado às informações é qual processo organizacional criou as informações e em que momento.

### 3.3 Efeitos Negativos da Rotulagem
- A rotulagem de informações e outros ativos associados às vezes pode ter efeitos negativos.
- Ativos classificados podem ser mais fáceis de identificar por pessoas mal intencionadas, para potencial uso indevido.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora a rotulagem permita o manuseio adequado e a devida proteção, também pode facilitar a identificação para atividades maliciosas, conforme indicado pela norma.
> - Este é um ponto de atenção relevante para provas.

### 3.4 Sistemas sem Rotulagem Individual
- Alguns sistemas não rotulam arquivos individuais ou registros de banco de dados com sua classificação.
- Nesses casos, protegem todas as informações no mais alto nível de classificação de qualquer uma das informações que contém ou são permitidas para conter.
- É comum nesses sistemas determinar e, em seguida, rotular informações quando são exportadas.

> [!TIP] DICAS: 
> - Distinção fundamental: classificação identifica e entende as necessidades de proteção de acordo com a importância da informação; rotulagem facilita a comunicação dessa classificação.
> - A rotulagem apoia a automação do processamento e gerenciamento das informações.
> - Cuidado com a pegadinha em prova: a alternativa que menciona "identificação e entendimento das necessidades de proteção" refere-se à classificação, não à rotulagem.