# Itil 4 Práticas 5

## 1. Gerenciamento de Ativos de TI
- O propósito desta prática é planejar e gerenciar o ciclo de vida completo de todos os ativos de tecnologia da informação.
- Objetivos principais incluem a maximização do valor, o controle de custos e o gerenciamento de riscos associados aos ativos.
- Apoia a tomada de decisão sobre a compra, reutilização, aposentadoria e descarte de ativos.
- Garante o atendimento a requisitos regulamentares e contratuais da organização.
- Ativo de TI é definido como qualquer componente de valor financeiro que possa contribuir para a entrega de um produto ou serviço.
- A classificação dos ativos de informação envolve a identificação e categorização com base no nível de sensibilidade, criticidade e valor para a organização.

> [!CAUTION] OBSERVAÇÃO: 
> - A palavra-chave desta prática é ciclo de vida, pois os artigos tornam-se obsoletos e exigem atualizações ou substituições constantes para manter o controle de custos.

## 2. Monitoramento e Gerenciamento de Eventos
- Esta prática foca em observar sistematicamente os serviços e seus componentes para registrar e relatar mudanças de estado.
- Identifica e prioriza eventos relacionados à infraestrutura, serviços, processos de negócio e segurança da informação.
- Evento é qualquer mudança de estado que tenha significância para o gerenciamento de um serviço ou item de configuração (IC).
- Permite reagir a condições que podem levar a falhas ou incidentes antes que o impacto ocorra.
- As notificações de eventos são geralmente geradas por ferramentas de monitoramento, itens de configuração ou pelo próprio serviço de TI.

## 3. Gerenciamento de Liberação e Versão
- O propósito é disponibilizar novos serviços, funcionalidades ou serviços alterados para o uso dos consumidores.
- Uma versão (release) pode ser composta por um único item de configuração ou um conjunto deles.
- Em ambientes ágeis, esta prática foca em entregas pequenas, rápidas e com ciclos curtos de desenvolvimento.

> [!TIP] DICAS: 
> - A palavra-chave para identificar esta prática em provas é disponibilizar.

## 4. Gerenciamento de Catálogo de Serviços
- Fornece uma fonte única de informação coerente sobre todos os serviços e ofertas de serviços da organização.
- Garante que essas informações estejam disponíveis para o público relevante de forma clara e acessível.

> [!TIP] DICAS: 
> - A expressão fonte única é o principal indicativo desta prática em questões de concurso.

## 5. Gerenciamento de Configuração de Serviço
- Garante que informações precisas e confiáveis sobre a configuração dos serviços e seus itens de configuração (ICs) estejam disponíveis.
- Item de Configuração (IC) é qualquer componente que precisa ser gerenciado para entregar um serviço de TI.
- A prática mantém informações sobre como os ICs são configurados e as relações existentes entre eles.
- Utiliza o Sistema de Gerenciamento de Configuração (CMS), que é um conjunto de ferramentas e dados para suportar a prática.

> [!CAUTION] OBSERVAÇÃO: 
> - A responsabilidade por manter o sistema de gerenciamento de configuração não é exclusiva de um gerente de mudanças, podendo ser compartilhada ou atribuída a outros papéis.

## 6. Gerenciamento de Continuidade de Serviço
- O propósito é garantir que a disponibilidade e o desempenho de um serviço sejam mantidos em níveis suficientes em caso de desastre.
- Fornece uma estrutura para a construção de resiliência organizacional e resposta eficaz para salvaguardar os interesses das partes interessadas.
- Planos de Recuperação de Desastres (DRP) definem como a organização retornará à condição anterior ao desastre considerando as quatro dimensões do gerenciamento de serviços.

### 6.1 Indicadores e Análise de Continuidade
- A Análise de Impacto nos Negócios (BIA) identifica as funções críticas de negócios (VBFs) e suas dependências.
- Define os requisitos de recuperação através de indicadores específicos apresentados na tabela abaixo.

| INDICADOR | SIGNIFICADO | DESCRIÇÃO |
|---|---|---|
| RTO | Recovery Time Objective | Período máximo aceitável de tempo após uma interrupção antes de afetar severamente o negócio |
| RPO | Recovery Point Objective | Ponto no tempo ao qual as informações devem ser restauradas para que a atividade opere na retomada |

> [!CAUTION] OBSERVAÇÃO: 
> - O foco da continuidade de negócio é manter níveis mínimos de operação estritamente em caso de desastre.

## 7. Design de Serviço
- Esta prática visa projetar produtos e serviços adequados para a finalidade (fit for purpose) e para o uso (fit for use).
- Inclui o planejamento de pessoas, parceiros, fornecedores, informação, tecnologia e processos.
- Considera a interação entre a organização e seus clientes para novos requisitos ou alterações.
- O Pacote de Design de Serviço (SDP) define todos os aspectos de um serviço e seus requisitos em cada estágio do ciclo de vida.

### 7.1 Técnicas de Design
- A prática utiliza abordagens modernas para garantir a qualidade do projeto e a experiência do interessado.

| TÉCNICA | APLICAÇÃO |
|---|---|
| Design Thinking | Ferramenta colaborativa para resolver problemas complexos e encontrar soluções práticas |
| CX e UX | Foco na experiência do cliente e do usuário para melhorar as interações funcionais e emocionais |

> [!TIP] DICAS: 
> - O Design Thinking é frequentemente citado como a técnica colaborativa ideal para elicitação de requisitos com equipes multidisciplinares.