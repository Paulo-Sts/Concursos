# Microsoft SDL Security Development Lifecycle

## 1. Introdução ao Microsoft SDL
- Processo de garantia de segurança focado no desenvolvimento e operação de software seguro conhecido como DevSecOps;
- Integração das áreas de desenvolvimento, operação e segurança para que a responsabilidade por vulnerabilidades seja compartilhada;
- Fornecimento de requisitos de segurança detalhados e mensuráveis para reduzir o número e a gravidade de falhas em produtos e serviços.

## 2. Governança e Arquitetura Zero Trust
- Baseia-se no pressuposto da confiança zero onde todos devem caminhar conforme os requisitos de segurança na arquitetura e na governança;
- Implementação de gates entre as etapas do processo que apresentam listas de verificação obrigatórias para o avanço de fase;
- Exemplo: necessidade de análise estática do código para sair da etapa de design e codificação ⟶ realização de análise binária para entrar na fase de construção.

## 3. Práticas de Segurança e Testes
- Estabelecimento de padrões de segurança, métricas e governança corporativa;
- Realização de revisão de design de segurança e modelagem de ameaças para criar arquiteturas resistentes;
- Execução de monitoramento e resposta de segurança após o lançamento do produto;
- Treinamento contínuo em segurança da informação para atualização constante das equipes;
- SAST (Static Application Security Test) ⟶ identificação de vulnerabilidades no código-fonte por meio de análise estática sem necessidade de execução;
- DAST (Dynamic Application Security Test) ⟶ teste de segurança em aplicações dinâmicas em tempo de execução através das interfaces expostas;
- SCA (Software Composition Analysis) ⟶ análise da composição dos sistemas relacionada à segurança da cadeia de suprimentos.

### 3.1 Comparação de Testes de Segurança
| TESTE | SIGLA | CARACTERÍSTICA | EXECUÇÃO |
|---|---|---|---|
| Estático | Sast | Revisão direta do código-fonte | Sem execução ou compilação |
| Dinâmico | Dast | Teste de fora para dentro em interfaces | Em tempo de execução |

## 4. Componentes do Ciclo de Vida

### 4.1 Training
- Formação obrigatória em segurança e privacidade para todos os funcionários da Microsoft;
- Realização de treinamento inicial após a contratação e atualizações anuais obrigatórias para manter o conhecimento sobre tendências recentes.

### 4.2 Requirements
- Definição de requisitos baseada em dados processados, ameaças conhecidas, melhores práticas e lições aprendidas de incidentes anteriores;
- Documentação e controle contínuo dos requisitos para refletir alterações na funcionalidade e no panorama de ameaças.

### 4.3 Design
- Execução da modelagem de ameaças (threat modeling) para evitar que falhas passem pelo design do produto;
- O fluxo da modelagem segue a ordem: define ⟶ diagram ⟶ identify ⟶ mitigate ⟶ validate.

### 4.4 Implementation
- Fase de codificação utilizando ferramentas de desenvolvimento seguras, compiladores e ambientes com verificações incorporadas.

### 4.5 Verification
- Aplicação de análise de código estático, análise binária e scanner de credenciais para evitar exposição de segredos como senhas e urls;
- Realização de teste fuzz para observar o comportamento do sistema quando submetido a entradas nos limites de buffer;
- Governança de componentes para garantir a segurança dos itens integrados.

### 4.6 Release
- Lançamento estruturado em anéis de progressão:
  - Cadência 0 ⟶ equipe de desenvolvimento responsável;
  - Anel 1 ⟶ todos os funcionários da Microsoft;
  - Anel 2 ⟶ utilizadores externos específicos para testes direcionados;
  - Anel 3 ⟶ lançamento padrão mundial em subfases.

### 4.7 Response
- Monitoramento centralizado quase em tempo real para identificação e resposta a potenciais incidentes de segurança após o lançamento.

> [!TIP] DICAS: 
> - A cobrança em concursos foca em definir o que é o processo ou quais são as tarefas de cada etapa.
> - Lembre-se que SAST ocorre no código-fonte (estático) e DAST ocorre no software rodando (dinâmico).

> [!CAUTION] OBSERVAÇÃO: 
> - A modelagem de ameaças é realizada na fase de Design e não na fase de requisitos.
> - O conserto de vulnerabilidades via DAST costuma ser mais caro do que as descobertas no início do ciclo de desenvolvimento.
> - O roteiro do processo SDL é único, servindo tanto para novos sistemas quanto para manutenção de existentes.