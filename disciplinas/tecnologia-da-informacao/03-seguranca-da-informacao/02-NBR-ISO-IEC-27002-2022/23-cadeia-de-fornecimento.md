# ISO/IEC 27002:2022 - Cadeia de Fornecimento de TIC

## 1. Contexto e Classificação do Controle
- O controle analisado pertence à norma ISO/IEC 27002:2022, dentro do grupo de controles organizacionais.
- O foco é a gestão da segurança da informação na cadeia de fornecimento de tecnologia da informação e comunicações.
- O controle é classificado como de natureza preventiva.
- As propriedades da segurança da informação aplicáveis são:
  - Confiabilidade;
  - Integridade;
  - Disponibilidade.
- Conceitos de segurança cibernética associados:
  - Identificar;
  - Segurança nas relações com fornecedores;
  - Governança e ecossistema;
  - Proteção.
- Capacidades operacionais mencionadas:
  - Segurança nas relações com fornecedores.
- Domínios de segurança abrangidos:
  - Governança e ecossistema;
  - Proteção.

| TIPO DE CONTROLE | PROPRIEDADE DA SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|------------------|-----------------------------------------|-------------------------------------|--------------------------|------------------------|
| Preventivo       | Confiabilidade; integridade; disponibilidade | Identificar | Segurança nas relações com fornecedores | Governança e ecossistema; proteção |

> [!TIP] DICAS:
> - Controle preventivo: age antes do incidente.
> - A tríade Confiabilidade, Integridade e Disponibilidade é a base da segurança da informação.
> - Os domínios e conceitos listados mostram que o controle vai além do fornecedor direto, envolvendo todo o ecossistema.

## 2. Controle
- Processos e procedimentos devem ser definidos e implementados para gerenciar riscos de segurança da informação associados à cadeia de fornecimento de produtos e serviços de TIC.
- A implementação deve considerar toda a cadeia, não apenas o fornecedor imediato.

> [!CAUTION] OBSERVAÇÃO:
> - A responsabilidade pela segurança da informação não pode ser centralizada apenas no fornecedor direto; a organização deve atuar ativamente na gestão dos riscos da cadeia.

## 3. Propósito
- Manter um nível acordado de segurança da informação nas relações com fornecedores.
- O propósito é garantir que a segurança pactuada seja mantida ao longo de todo o relacionamento com os fornecedores.

## 4. Orientações para Implementação
- Além dos requisitos gerais de segurança da informação para relações com fornecedores, os seguintes tópicos devem ser considerados:

### 4.1 Definição de Requisitos
- Definir requisitos de segurança da informação para aquisição de produtos ou serviços de TIC.
- Esses requisitos devem ser claros e aplicáveis desde o início do processo de compra.

### 4.2 Propagação de Requisitos na Cadeia
- Exigir que fornecedores de serviços de TIC propaguem os requisitos de segurança da organização por toda a cadeia de fornecimento, caso subcontratem partes do serviço prestado à organização.
- Exigir que fornecedores de produtos de TIC propaguem práticas de segurança adequadas por toda a cadeia de fornecimento, se os produtos incluírem componentes comprados de outros fornecedores ou entidades.
  - Exemplo: desenvolvedores de software subcontratados e provedores de componentes de hardware.

### 4.3 Transparência e Informações Técnicas
- Solicitar que fornecedores de produtos de TIC forneçam informações descrevendo:
  - Os componentes de software utilizados nos produtos;
  - As funções de segurança implementadas em seus produtos;
  - As configurações necessárias para a operação segura.

### 4.4 Monitoramento e Validação
- Implementar um processo de monitoramento e métodos aceitáveis para validação de produtos e serviços de TIC em conformidade com os requisitos de segurança declarados.
- Exemplos de métodos de revisão de fornecedores:
  - Testes de penetração;
  - Prova ou validação de atestados de terceiros para as operações de segurança do fornecedor.

### 4.5 Identificação e Gestão de Componentes Críticos
- Implementar um processo de identificação e documentação de componentes de produtos ou serviços que sejam fundamentais para a manutenção da funcionalidade.
- Esses componentes requerem maior atenção, escrutínio e acompanhamento, especialmente quando construídos fora da organização.
- Se o fornecedor terceirizar partes desses componentes para outros fornecedores, a atenção deve ser redobrada.

### 4.6 Rastreabilidade
- Obter garantia de que componentes críticos e sua origem podem ser rastreados em toda a cadeia de fornecimento.
- A rastreabilidade é fundamental para garantir a procedência e a integridade dos componentes.

### 4.7 Integridade e Funcionamento dos Produtos
- Obter garantia de que os produtos de TIC entregues estão funcionando como esperado, sem características inesperadas ou indesejadas.
- Implementar processos para garantir que os componentes dos fornecedores sejam genuínos e sem alteração de sua especificação.
- Medidas de exemplo para garantir a autenticidade:
  - Rótulos antiadulteração;
  - Verificações de hash;
  - Criptografia ou assinaturas digitais.
- O monitoramento para o desempenho fora da especificação pode ser um indicador de adulteração ou falsificações.
- A prevenção e a detecção de adulteração devem ser implementadas durante múltiplas etapas do ciclo de vida do desenvolvimento do sistema:
  - Projeto;
  - Desenvolvimento;
  - Integração;
  - Operações;
  - Manutenção.

### 4.8 Certificação e Avaliação de Segurança
- Obter garantia de que os produtos de TIC atingem níveis de segurança necessários.
- Exemplo: certificação formal ou um esquema de avaliação, como o Acordo de Reconhecimento de Critérios Comuns.

### 4.9 Compartilhamento de Informações
- Definir regras para o compartilhamento de informações sobre a cadeia de fornecimento e eventuais problemas e compromissos entre a organização e fornecedores.

### 4.10 Gestão do Ciclo de Vida dos Componentes
- Implementar processos específicos para a gestão do ciclo de vida dos componentes de TIC e disponibilidade e riscos de segurança associados.
- Isso inclui gerenciar os riscos de:
  - Os componentes não estarem mais disponíveis devido aos fornecedores não estarem mais no negócio;
  - Fornecedores não mais fornecerem esses componentes devido aos avanços tecnológicos.
- Deve ser considerada a identificação de um fornecedor alternativo e o processo de transferência de software e competência para o fornecedor alternativo.

> [!TIP] DICAS:
> - A orientação sobre fornecedor alternativo é crucial para a continuidade do negócio. A norma recomenda planejar a substituição do fornecedor em caso de falência, encerramento ou descontinuação de componentes.

> [!CAUTION] OBSERVAÇÃO:
> - A expressão “convém” indica uma recomendação, ou seja, uma boa prática a ser seguida, e não uma obrigação absoluta. No entanto, em concursos, costuma ser cobrada como a conduta esperada.

## 5. Outras Informações e Contexto
- As práticas específicas de gestão de riscos da cadeia de fornecimento de TIC são construídas em cima das práticas gerais de segurança da informação, qualidade, gerenciamento de projetos e engenharia de sistemas, mas não as substituem.
- As organizações são aconselhadas a trabalhar com fornecedores para entender a cadeia de fornecimento de TIC e quaisquer assuntos que tenham um efeito importante sobre os produtos e serviços que estão sendo prestados.
- A organização pode influenciar as práticas de segurança da informação na cadeia de fornecimento de TI ao explicitar, nos acordos com fornecedores, os temas que devem ser abordados por outros participantes dessa cadeia.
- Recomenda-se que tecnologias da informação e comunicações sejam adquiridas de fontes confiáveis.
- A confiabilidade de software e hardware é matéria de controle de qualidade.
- Embora nem sempre seja viável inspecionar os sistemas de qualidade dos fornecedores, é possível formular juízos consistentes com base na reputação e no histórico do fornecedor.
- No escopo deste controle, as cadeias de fornecimento de TI incluem serviços em nuvem.

### 5.1 Exemplos de Cadeias de Fornecimento de TI
- Provisão de serviços em nuvem:
  - O provedor depende de desenvolvedores de software, prestadores de serviços de telecomunicações e fabricantes de hardware.
- Internet das Coisas (IoT):
  - O serviço envolve fabricantes de dispositivos, provedores de serviços em nuvem (operadores de plataformas de IoT), desenvolvedores de aplicações móveis e web e fornecedores de bibliotecas de software.
- Serviços de hospedagem:
  - O provedor conta com service desks externos, incluindo primeiro, segundo e terceiro níveis de apoio.

> [!TIP] DICAS:
> - A inclusão de serviços em nuvem no escopo do controle é um ponto relevante, pois amplia a abrangência da gestão de riscos.
> - Os exemplos mostram como a cadeia de fornecimento de TIC pode ser complexa e envolver múltiplos atores, o que reforça a necessidade de uma gestão cuidadosa.

> [!CAUTION] OBSERVAÇÃO:
> - A confiabilidade do fornecedor (reputação e histórico) é um fator relevante, mas não é o único critério. A norma recomenda medidas complementares, como testes e validações, para garantir a segurança.