# Lei n. 13.709/2018 – LGPD IX (Anonimização, Pseudonimização e Saúde Pública – Arts. 12 e 13)

## 1. Anonimização – conceito (art. 12)

### 1.1 Regra geral
**Art. 12.** Os dados anonimizados não serão considerados dados pessoais para os fins desta lei, salvo quando o processo de anonimização ao qual foram submetidos for revertido, utilizando exclusivamente meios próprios, ou quando, com esforços razoáveis, puder ser revertido.
- A partir do momento em que não se consegue mais identificar o titular do dado, não há que se falar em aplicação da LGPD.
- Na reversão (reidentificação), o dado volta a ser pessoal e a LGPD se aplica.

> [!CAUTION] OBSERVAÇÃO: 
> - Regra de ouro: se puder ser revertido, ainda é dado pessoal.

### 1.2 Teste de reversibilidade
- O processo de anonimização pode ser revertido?

| RESULTADO | CLASSIFICAÇÃO | APLICAÇÃO DA LGPD |
|-----------|---------------|-------------------|
| Sim, com esforços razoáveis ou meios próprios | Dado pessoal | LGPD se aplica |
| Não, impossível de reverter | Dado anonimizado | LGPD NÃO se aplica |

### 1.3 Esforço razoável – § 1º
**Art. 12, § 1º** A determinação do que seja razoável deve levar em consideração fatores objetivos, tais como custo e tempo necessários para reverter o processo de anonimização, de acordo com as tecnologias disponíveis, e a utilização exclusiva de meios próprios.

| FATOR | EXPLICAÇÃO |
|-------|------------|
| Custo | É financeiramente viável quebrar a criptografia? Recurso computacional é caro |
| Tempo | Levaria dias ou milênios para reverter? Se levar milênios, não é razoável |
| Tecnologia | Há capacidade computacional disponível hoje para isso? |

> [!TIP] DICAS: 
> - Exemplo de anonimização que NÃO é válida: realizar um mascaramento simples, trocar o nome do titular por "Paciente X", mas manter uma planilha secreta ligando esse código ao nome real. Isso é pseudonimização, não anonimização.

## 2. Perfilamento comportamental e padrões da ANPD

### 2.1 Perfis comportamentais – § 2º
**Art. 12, § 2º** Poderão ser igualmente considerados como dados pessoais, para os fins desta lei, aqueles utilizados para a formação do perfil comportamental de determinada pessoa natural, se vier a ser identificada.
- Dados aparentemente anônimos se tornam dados pessoais se permitirem singularizar uma pessoa.
- Exemplo: um aplicativo que rastreia horários de sono e localização. Se a junção desses dados inferir que o usuário "anônimo" é o João da Silva, o perfil torna-se protegido pela LGPD.

### 2.2 Papel da ANPD – § 3º
**Art. 12, § 3º** A autoridade nacional poderá dispor sobre padrões e técnicas utilizados em processos de anonimização e realizar verificações acerca de sua segurança, ouvido o Conselho Nacional de Proteção de Dados Pessoais.
- A ANPD define padrões de anonimização e fiscaliza a segurança, ouvindo sempre o Conselho Nacional.

## 3. Pesquisa em saúde pública (art. 13)

### 3.1 Regra geral
**Art. 13.** Na realização de estudos de saúde pública, os órgãos de pesquisa poderão ter acesso a bases de dados pessoais que serão tratados exclusivamente dentro do órgão e estritamente para a finalidade de realização de estudos e pesquisas, e mantidos em ambiente controlado e seguro, conforme práticas de segurança previstas em regulamento específico e que incluam, sempre que possível, a anonimização ou a pseudonimização dos dados, bem como considerem os devidos padrões éticos relacionados a estudos de pesquisa.

### 3.2 Requisitos obrigatórios para acesso a dados em pesquisa de saúde

| REQUISITO | EXPLICAÇÃO |
|-----------|------------|
| Finalidade estrita | Acesso aos dados apenas para estudos e pesquisas |
| Tratamento exclusivo dentro do órgão | Não pode ser feito em local diverso |
| Ambiente controlado e seguro | Segurança da informação garantida |
| Anonimização ou pseudonimização | Uma das técnicas deve ser aplicada (sempre que possível) |
| Respeito a padrões técnicos e éticos | Cumprir regulamentações específicas |

> [!TIP] DICAS: 
> - Exemplo prático: a Fiocruz ou o Instituto Butantan acessando dados do SUS para mapear uma epidemia. O tratamento deve ser feito estritamente nos servidores do próprio instituto, com as técnicas de proteção apropriadas.

## 4. Vedações em pesquisas de saúde

### 4.1 Divulgação de resultados – § 1º
**Art. 13, § 1º** A divulgação dos resultados de qualquer excerto do estudo ou da pesquisa, em nenhuma hipótese, poderá revelar dados pessoais.

| PERMITIDO | PROIBIDO |
|-----------|----------|
| Publicar estatísticas gerais agregadas | Publicar qualquer trecho que identifique o paciente |
| Exemplo: "40% dos pacientes apresentaram melhora" | Exemplo: "o paciente X, morador do bairro Y, teve piora" |

### 4.2 Repasse de dados
- Regra do repasse: a transferência de dados brutos para terceiros é terminantemente proibida em qualquer circunstância.
- Exemplo: um instituto público não pode vender ou ceder a base de dados para uma farmacêutica privada.

### 4.3 Regulamentação – § 3º
**Art. 13, § 3º** O acesso aos dados de que trata este artigo será objeto de regulamentação por parte da Autoridade Nacional e das autoridades da área de saúde e sanitárias, no âmbito de suas competências.

## 5. Pseudonimização – conceito (§ 4º)
**Art. 13, § 4º** Para os efeitos deste artigo, pseudonimização é o tratamento por meio do qual um dado perde a possibilidade de associação direta ou indireta a um indivíduo, se não pelo uso de informação adicional, mantida separadamente pelo controlador em ambiente controlado e seguro.

### 5.1 Anonimização x Pseudonimização

| CARACTERÍSTICA | ANONIMIZAÇÃO | PSEUDONIMIZAÇÃO |
|----------------|--------------|-----------------|
| Reversibilidade | Irreversível | Reversível (com chave) |
| Identificação do titular | Impossível | Possível com informação adicional |
| Aplica-se a LGPD? | NÃO (dado anonimizado) | SIM (ainda é dado pessoal) |
| Exemplo | Estatísticas agregadas sem identificação | CPF trocado por código "#A892" com tabela de conversão separada |

> [!CAUTION] OBSERVAÇÃO: 
> - Na anonimização, o processo é irreversível e o dado deixa de ser pessoal. Na pseudonimização, a chave para reidentificar o titular existe e é guardada separadamente; o dado continua sendo pessoal e sujeito à LGPD.