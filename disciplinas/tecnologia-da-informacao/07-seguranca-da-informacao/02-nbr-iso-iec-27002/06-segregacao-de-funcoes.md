# ISO/IEC 27002:2022 - Segregação de Funções

## 1. Atributos e Propósito do Controle
- O controle de segregação de funções é classificado como preventivo e visa atuar antes da ocorrência de incidentes.
- Atribuição dos atributos conforme a norma:

| ATRIBUTO | VALOR DO ATRIBUTO |
|---|---|
| TIPO DE CONTROLE | Preventivo |
| PROPRIEDADES DE SEGURANÇA | Confidencialidade, integridade e disponibilidade |
| CONCEITOS DE SEGURANÇA CIBERNÉTICA | Proteger |
| CAPACIDADES OPERACIONAIS | Governança e gestão de identidade e acesso |
| DOMÍNIOS DE SEGURANÇA | Governança e ecossistema |

- O propósito principal é reduzir o risco de fraude, erro e desvio de controles de segurança da informação.
- Propósito ⟶ separar funções conflitantes entre diferentes indivíduos para evitar que alguém execute tarefas incompatíveis sozinho.
- A concentração de funções em uma única pessoa aumenta a probabilidade de erros por falta de verificação cruzada.

## 2. Orientações para Implementação e Exemplos Práticos
- A organização deve determinar quais funções e áreas de responsabilidade precisam ser segregadas.
- Funções conflitantes não devem ser desempenhadas pela mesma pessoa para permitir o controle e revisão das atividades.
- Exemplos de atividades que exigem segregação:
  - Iniciar, aprovar e executar uma mudança;
  - Solicitar, aprovar e implementar direitos de acesso;
  - Projetar, implementar e revisar códigos;
  - Desenvolver software e administrar sistemas de produção;
  - Utilizar e administrar aplicações;
  - Utilizar aplicações e administrar bancos de dados;
  - Projetar, auditar e garantir os controles de segurança da informação.

### 2.1 Gestão de Riscos e Controle de Acesso
- A possibilidade de conluio deve ser considerada no desenho dos controles.
- Conluio ⟶ associação de indivíduos para agir em benefício próprio contrariando os interesses da organização.
- No modelo de controle de acesso baseado em papéis (RBAC), deve-se garantir que papéis conflitantes não sejam concedidos ao mesmo pessoal.
- Ferramentas automatizadas podem ser usadas para identificar conflitos, mas a supervisão humana permanece indispensável.
- Os papéis devem ser provisionados com cuidado para minimizar problemas caso um papel seja removido ou redesignado.

## 3. Aplicação em Pequenas Organizações
- Pequenas organizações podem encontrar dificuldades práticas para alcançar a segregação total de funções.
- Nestes casos, o princípio da segregação deve ser aplicado na medida do possível e praticável.
- Quando a segregação é difícil, convém considerar controles compensatórios:
  - Monitoramento de atividades;
  - Trilhas de auditoria para registro detalhado das ações;
  - Supervisão direta pela alta direção.

> [!TIP] DICAS: 
> - Guarde os três pilares do propósito: reduzir Fraude, Erro e Desvio (FED).
> - Em desenvolvimento de software, quem codifica não deve ser a mesma pessoa que revisa o código para garantir a confiabilidade.

> [!CAUTION] OBSERVAÇÃO: 
> - Pegadinha de prova: as bancas afirmam que funções conflitantes devem ser agregadas. Incorreto. O termo técnico obrigatório é segregação ou separação.
> - A responsabilidade por definir a segregação é da própria organização, adaptando a norma à sua realidade e maturidade técnica.