# CI/CD

## 1. Definição
- CI/CD refere-se a um conjunto de boas práticas empregadas no desenvolvimento de software que promovem a automação e agilidade nas entregas e integração de sistemas;
- O tema é um tópico recorrente em editais e frequentemente associado às práticas DevOps, embora não se limite a este contexto;
- Estabelece um ciclo contínuo e repetitivo essencial para garantir a entrega de software de forma concisa e segura ao cliente;
- O processo permite que os sistemas sejam atualizados frequentemente, garantindo que o cliente receba as atualizações de maneira confiável e organizada.

## 2. Integração Contínua (CI)
- Consiste na combinação de cada parte do código entregue sendo automaticamente construído e testado;
- Visa a detecção de falhas e vulnerabilidades de forma antecipada para contribuir com a robustez e confiabilidade do software;
- Requer a criação de versões incrementais do software em que os componentes são gradualmente combinados e testados;
- O merge ⟶ união de todas as partes do software para garantir a consistência do projeto.

## 3. Entrega e Implantação Contínua (CD)
- A entrega contínua (CD) é dependente da integração contínua e envolve a execução de novas checagens e disponibilização do software para uso;
- Utiliza um repositório automatizado de liberação para a entrega do software;
- O deployment ou implantação faz parte do pipeline e utiliza ferramentas automatizadas para garantir uma transição eficiente e minimamente manual.

> [!CAUTION] OBSERVAÇÃO: 
> - Não se deve confundir delivery (entrega da versão), release (liberação para produção) e deploy (implantação em um ambiente de produção).

## 4. Estrutura do Pipeline e do Ciclo de Desenvolvimento
- O pipeline é um mecanismo fundamental para o controle de atividades e ferramentas organizadas dentro de um fluxo ou processo de execução;
- É uma prática comum em áreas como big data e sistemas de suporte à decisão;
- A divisão do pipeline ocorre em camadas: integração, seguida pela entrega e, por fim, a implantação.

### 4.1 Etapas Estruturadas do Ciclo
- Planejamento;
- Codificação;
- Montagem da build;
- Testes contínuos;
- Liberação;
- Implantação;
- Monitoramento.

## 5. Ambientes e Validação de Qualidade
- O código é primeiramente integrado e testado pela equipe de desenvolvimento em um ambiente interno de testes;
- O staging é definido como um ambiente temporário onde o cliente pode realizar testes e homologações antes da disponibilidade para usuários finais;
- Testes de aceitação como beta e alfa ocorrem após a integração contínua para validar a funcionalidade em situações reais;
- É essencial realizar testes em partes menores do código antes de integrá-las em conjunto.

> [!TIP] DICAS: 
> - O teste é uma atividade necessária tanto na fase de integração quanto na fase de entrega para garantir a estabilidade do produto.

## 6. Ferramentas Utilizadas no Processo
- O suporte de sistemas específicos favorece o controle de versionamento automatizado e o fluxo contínuo de desenvolvimento.

| FERRAMENTA | FINALIDADE E ATUAÇÃO |
|---|---|
| Jenkins | Assegura critérios de qualidade, cria executáveis e trabalha na implementação; |
| Docker | Utilizado para desenvolvimento em contêineres e criação de ambientes isolados; |
| Openshift e Gitlab | Permitem o controle de versionamento automatizado do sistema; |
| Spinnaker | Projetada especificamente para entrega contínua em ambientes multi-cloud; |
| Concourse | Atua tanto na etapa de entrega quanto na de implantação (CI e CD); |
| Git | Sistema de controle de versão distribuído que integra as práticas de CI/CD. |

> [!CAUTION] OBSERVAÇÃO: 
> - A ferramenta Jenkins está relacionada tanto à criação de arquivos executáveis quanto à etapa de deploy (implantação).