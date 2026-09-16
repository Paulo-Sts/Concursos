# ISO/IEC 27002:2022 Controles Organizacionais 24

## 1. Proteção de Registros
- Controle: convém que os registros sejam protegidos contra perdas, destruição, falsificação, acesso não autorizado e liberação não autorizada.
- Propósito: assegurar o compliance dos requisitos legais, estatutários, regulamentares e contratuais, bem como expectativas comunitárias ou sociais relacionadas à proteção e disponibilidade de registros.
- Definição de registros: qualquer conjunto de informações, independentemente de sua estrutura ou forma, que documentam eventos, transações individuais, processos de trabalho, atividades ou funções.
- Abrangência: inclui informações na forma de documentos, coletas de dados ou outros tipos de informações digitais ou analógicas criadas e capturadas no decorrer dos negócios.

### 1.1 Atributos do Controle 5.33
| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade, integridade e disponibilidade | Identificar e proteger | Legal e compliance, gestão de ativos e proteção da informação | Defesa |

### 1.2 Orientações para Gestão de Registros
- Emissão de diretrizes: convém estabelecer normas sobre armazenamento, manuseio da cadeia de custódia e descarte de registros para prevenir a manipulação;
- Alinhamento de políticas: as diretrizes devem estar em conformidade com a política específica de gerenciamento de registros da organização;
- Cronograma de retenção: convém elaborar um documento definindo quais registros devem ser mantidos e por qual período de tempo;
- Identificação e sistema: o sistema de manuseio deve assegurar a identificação clara dos registros e seus respectivos prazos de retenção;
- Destruição adequada: convém que o sistema permita a eliminação segura dos registros após o fim do período de retenção, caso não sejam mais necessários;
- Classificação: a proteção de registros específicos deve considerar a classificação de segurança da informação correspondente no esquema da organização;
- Categorização por tipos: os registros podem ser divididos em contábeis, transações comerciais, pessoais ou legais.

### 1.3 Armazenamento e Tecnologia
- Recuperação de dados: os sistemas devem ser escolhidos para garantir que os registros sejam recuperados em tempo e formato aceitáveis;
- Acesso e legibilidade: convém estabelecer procedimentos para garantir o acesso ao formato e à mídia durante todo o período de retenção, protegendo contra obsolescência tecnológica;
- Chaves criptográficas: convém reter as chaves e programas associados a arquivos criptografados ou assinaturas digitais pelo mesmo tempo de retenção do registro original;
- Recomendações de fabricantes: os procedimentos de armazenamento devem seguir as orientações dos fabricantes das mídias para evitar a deterioração.

### 1.4 Metadados e Requisitos Legais
- Papel dos metadados: são componentes essenciais que descrevem o contexto, conteúdo e estrutura dos registros e sua gestão ao longo do tempo;
- Importância para auditoria: metadados são fundamentais para processos de verificação e auditoria;
- Primazia da lei: períodos de retenção definidos em leis ou regulamentos nacionais sobrepõem-se às decisões internas da organização para registros específicos.

> [!TIP] DICAS: 
> - Metadados ⟶ são dados sobre o dado, como data de criação, autor e local de armazenamento.
> - Meios de armazenamento ⟶ a escolha da mídia impacta a velocidade de recuperação; fitas magnéticas, por exemplo, possuem recuperação mais lenta que discos de gravação direta.

> [!CAUTION] OBSERVAÇÃO: 
> - Os registros devem ser protegidos simultaneamente nos três pilares: confidencialidade, integridade e disponibilidade.
> - Registros de órgãos públicos podem ser solicitados por qualquer cidadão via Lei de Acesso à Informação ou por autoridades em caso de investigações criminais.
> - Mídias físicas, como fitas magnéticas, exigem cuidados rigorosos com umidade e temperatura para evitar a perda definitiva de dados por deterioração.
> - É um erro comum em provas considerar metadados como irrelevantes; a norma os classifica como componentes essenciais do registro.