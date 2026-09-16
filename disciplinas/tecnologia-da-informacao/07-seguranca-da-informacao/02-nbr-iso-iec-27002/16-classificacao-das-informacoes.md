# ISO/IEC 27002:2022 - Classificação das Informações

## 1. Definição
- O controle de classificação das informações é um controle preventivo.
- Este controle está diretamente relacionado às propriedades de segurança da informação, conhecidas como tríade da segurança da informação.
- O controle está alinhado ao conceito de segurança cibernética de identificação das capacidades operacionais para proteção da informação.
- Nos domínios de segurança, a classificação das informações se enquadra em proteção e defesa.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|-----------------------------------------|------------------------------------|--------------------------|-----------------------|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Identificar | Proteção da informação | Proteção; Defesa |

## 2. Controle (Recomendação Central)
- As informações devem ser classificadas de acordo com as necessidades de segurança da informação da organização.
- A classificação deve ser baseada na confidencialidade, integridade, disponibilidade e requisitos relevantes das partes interessadas.
- Não existe um padrão uniforme de classificação; a abordagem é baseada nas necessidades e atributos específicos de cada organização.

## 3. Propósito
- Assegurar a identificação e o entendimento das necessidades de proteção das informações.
- A proteção deve ser proporcional à importância da informação para a organização.
- A classificação deve ser precedida pela compreensão de que nem todas as informações terão a mesma classificação, pois cada informação pode ter relevância distinta.

> [!CAUTION] OBSERVAÇÃO:
> - O propósito principal do controle é determinar o grau de importância de cada informação para a organização, direcionando as necessidades de proteção de forma individualizada.

## 4. Orientações para a Classificação

### 4.1 Política Específica
- A organização deve estabelecer uma política específica sobre classificação e comunicação de informações para todas as partes interessadas pertinentes.
- A política deve detalhar como a classificação e a comunicação das informações devem ser realizadas.
- É recomendado que as organizações disponham de políticas específicas por tema, sendo a classificação das informações uma delas.

### 4.2 Consideração dos Requisitos da Tríade
- O esquema de classificação deve considerar os requisitos de confidencialidade, integridade e disponibilidade.
- As classificações e os controles de proteção associados devem ser avaliados conforme orientado pela norma.

### 4.3 Necessidades do Negócio e Requisitos Legais
- A classificação deve considerar as necessidades do negócio para compartilhar ou restringir informações.
- Deve proteger a integridade das informações e assegurar a disponibilidade.
- Os requisitos legais relativos à confidencialidade, integridade ou disponibilidade devem ser incluídos no processo de classificação.

### 4.4 Classificação de Outros Ativos
- Outros ativos (que não sejam as informações) podem ser classificados em conformidade com a classificação das informações que são armazenadas, processadas, manuseadas ou protegidas por esses ativos.
- A classificação determinada para as informações pode ser aplicada a outros ativos associados.

### 4.5 Responsabilidade pela Classificação
- Os proprietários das informações são responsáveis por sua classificação.

> [!TIP] DICAS:
> - Em provas, a responsabilidade pela classificação das informações sempre será atribuída aos proprietários da informação, não a analistas de negócios ou de banco de dados, por exemplo.

### 4.6 Regime de Classificação e Critérios
- O regime de classificação deve incluir convenções para classificação e critérios para análise crítica da classificação ao longo do tempo.

### 4.7 Atualização da Classificação
- Os resultados da classificação devem ser atualizados de acordo com as alterações do valor, sensibilidade e criticidade das informações ao longo de seu ciclo de vida.
- Uma informação pode apresentar alto valor no início de seu ciclo de vida e perder valor ao final.
- A avaliação do valor, sensibilidade e criticidade deve ser contínua, considerando as mudanças durante todo o ciclo de vida da informação.

> [!CAUTION] OBSERVAÇÃO:
> - A classificação não é fixa; ela deve acompanhar as mudanças das informações ao longo do tempo. Superclassificação pode gerar gastos desnecessários, enquanto subclassificação pode levar a controles insuficientes.

### 4.8 Alinhamento com a Política de Controle de Acesso
- O esquema de classificação deve estar alinhado à política específica sobre controle de acesso (ver 5.1).
- Deve atender às necessidades específicas de negócios da organização.
- O controle de acesso determina quem pode acessar determinada informação conforme sua classificação.
- Exemplo: ao classificar uma informação como secreta, apenas pessoas autorizadas para esse nível têm permissão de acesso.

### 4.9 Critério de Impacto e Nomenclatura
- A classificação pode ser determinada pelo nível de impacto que seu comprometimento teria para a organização.
- Informações críticas exigem classificação de acordo com seu grau de impacto.
- A cada nível definido no esquema deve ser dado um nome que faça sentido no contexto da aplicação do regime de classificação.
- A nomenclatura pode seguir abordagem qualitativa (ex.: baixo, médio, alto).

### 4.10 Consistência em Toda a Organização
- O esquema de classificação deve ser consistente em toda a organização.
- Deve estar incluído nos procedimentos para que todos classifiquem as informações e apliquem outros ativos associados da mesma forma.
- Isso promove compreensão comum dos requisitos de proteção e aplicação adequada dessas medidas.

### 4.11 Diferenças entre Organizações
- O esquema de classificação de uma organização pode diferir daquele utilizado em outras instituições, mesmo que os nomes para níveis sejam semelhantes.
- Informações que transitam entre organizações podem receber classificações diferentes, conforme o contexto de cada instituição.
- Exemplo: uma informação pode ser considerada pública e de baixo impacto em uma organização, enquanto, em outra, pode ser classificada como secreta e de alto impacto.
- Acordos com outras organizações que incluem o compartilhamento de informações podem prever procedimentos para identificar a classificação dessas informações e interpretar os níveis de classificação de outras organizações.
- A correspondência entre diferentes esquemas pode ser determinada buscando equivalência nos métodos de manuseio e proteção associados.

### 4.12 Comunicação da Classificação
- A classificação fornece às pessoas que lidam com informações uma indicação concisa de como manuseá-las e protegê-las.
- O sistema de classificação deve ser compreensível, permitindo ao público interno identificar, apenas pelo nome atribuído, como as informações devem ser manuseadas e qual o grau de proteção necessário.
- O entendimento do nível de proteção e do procedimento adequado deve ser acessível a qualquer pessoa que tenha contato com as informações.

### 4.13 Agrupamento de Informações
- A norma orienta a criação de grupos de informações que possuam necessidades de proteção semelhantes.
- Devem ser especificados procedimentos de segurança da informação aplicáveis a todas as informações de cada grupo.
- Essa abordagem facilita a gestão, permitindo organizar as informações em grupos (ex.: públicas, confidenciais ou secretas) para que cada categoria receba medidas de proteção equivalentes.
- Reduz a necessidade de avaliações individualizadas de risco e customização de controles para cada caso.

### 4.14 Mudança de Sensibilidade ao Longo do Tempo
- As informações podem deixar de ser sensíveis ou críticas após um determinado período de tempo.
- Exemplo: quando as informações são tornadas públicas, elas não têm mais requisitos de confidencialidade, mas ainda podem requerer proteção para suas propriedades de integridade e disponibilidade.
- A superclassificação pode levar à implementação de controles desnecessários, resultando em despesas adicionais.
- A subclassificação pode levar a controles insuficientes para proteger as informações de comprometimento.

### 4.15 Exemplo de Esquema de Classificação
- A norma apresenta um exemplo de esquema de classificação de confidencialidade baseado em quatro níveis:
  - Nível 1: a divulgação não causa danos;
  - Nível 2: a divulgação causa pequenos danos à reputação ou pequenos impactos operacionais;
  - Nível 3: a divulgação tem um impacto significativo de curto prazo nas operações ou objetivos de negócios;
  - Nível 4: a divulgação tem um impacto sério em objetivos de negócios de longo prazo ou coloca a sobrevivência da organização em risco.

## 5. Diferenciação entre Recomendação e Requisito
- A ISO/IEC 27002 apresenta orientações e recomendações, não obrigações.
- O termo "convém que" é utilizado para indicar recomendações baseadas em melhores práticas reconhecidas internacionalmente.
- As recomendações não possuem caráter mandatório, diferindo dos requisitos, que são definidos em outras normas, como a ISO/IEC 27001.
- Os requisitos geralmente são expressos por termos como "deve".

> [!TIP] DICAS:
> - Identificar a diferença entre "convém que" (recomendação) e "deve" (requisito) é importante em provas, especialmente quando se comparam as normas ISO 27001 e ISO 27002.

## 6. Principais "Pegadinhas" Identificadas

### 6.1 Responsabilidade pela Classificação
- A responsabilidade é dos proprietários da informação, não de cargos específicos como analistas de negócios ou de banco de dados.

### 6.2 Classificação Fixa
- A classificação não é fixa; deve ser atualizada conforme mudanças em valor, sensibilidade ou criticidade ao longo do ciclo de vida da informação.

### 6.3 Padronização entre Organizações
- Não há obrigatoriedade de padronização do esquema de classificação com outras organizações.
- Cada instituição deve adotar um esquema que atenda ao seu próprio contexto organizacional.