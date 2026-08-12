# Iso/Iec 27002:2022 - Controles Tecnológicos 4

## 1. Autenticação Segura 8.5
- Convém que sejam implementados tecnologias e procedimentos de autenticação seguros com base em restrições de acesso à informação e na política específica de controle de acesso.
- Propósito: assegurar que um usuário ou uma entidade seja autenticada com segurança quando o acesso a sistemas, aplicações e serviços é concedido.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Orientação Para Técnicas de Autenticação
- Convém escolher uma técnica de autenticação adequada para comprovar a identidade alegada de usuários, softwares, mensagens e outras entidades.
- A força da autenticação deve ser adequada para a classificação das informações a serem acessadas.
- Quando for necessária autenticação forte, convém usar métodos alternativos a senhas, como certificados digitais, cartões inteligentes, tokens ou meios biométricos.
- Implementar a autenticação multifatorial (MFA) para sistemas críticos, combinando múltiplos fatores para reduzir as possibilidades de acessos não autorizados.
- Fatores de autenticação incluem o que você sabe (senhas), o que você tem (tokens ou cartões) e o que você é (biometria).
- Combinar o MFA com regras e padrões predefinidos baseados em circunstâncias específicas de acesso.
- Considerar o local de acesso como critério relevante, identificando acessos originados de localidades incomuns.
- Monitorar se o acesso é realizado a partir de um dispositivo não habitual ou endpoint atípico.
- Avaliar o momento do acesso, verificando conexões realizadas fora do intervalo padrão de horário da organização.

> [!CAUTION] OBSERVAÇÃO: 
> - A autenticação biométrica pode tornar-se indisponível devido a condições de uso como umidade, envelhecimento do indivíduo ou alterações na pele ⟶ convém que a biometria seja acompanhada de pelo menos uma técnica alternativa de autenticação.

### 1.2 Procedimentos de Log-on Seguro
- Projetar o procedimento de entrada para minimizar o risco de acesso não autorizado.
- Não exibir informações sensíveis do sistema ou aplicativo até que o processo de log-on tenha sido concluído com sucesso.
- Evitar fornecer qualquer assistência desnecessária a usuários não autorizados durante a autenticação.
- Exibir um aviso público indicando que o sistema só deve ser acessado por pessoas autorizadas.
- Não fornecer mensagens de ajuda durante o erro que indiquem qual parte dos dados (usuário ou senha) está correta ou incorreta.
- Validar as informações de log-on no sistema somente após a conclusão de todos os dados de entrada.
- Proteger contra tentativas de força bruta utilizando mecanismos como CAPTCHA, redefinição de senha ou bloqueio após limite de erros.
- Registrar todas as tentativas de acesso bem-sucedidas e malsucedidas para monitoramento.
- Criar eventos de segurança e enviar alertas para usuários e administradores caso detectadas violações de controle de acesso.
- Exibir em canal separado a data e hora do log-on anterior e detalhes de tentativas malsucedidas desde o último acesso.
- Ocultar a exibição da senha em texto claro durante a digitação para evitar a captura visual por terceiros.
- Não transmitir senhas em texto claro pela rede para evitar a captura por programas sniffer.
- Finalizar sessões inativas após período especificado de inatividade e restringir tempos de conexão para aplicações de alto risco.

> [!TIP] DICAS: 
> - O CAPTCHA é um mecanismo de verificação por imagem ou lógica que busca distinguir ações humanas de interações automatizadas realizadas por bots ⟶ garante segurança nos processos de acesso.

## 2. Gestão de Capacidade 8.6
- Convém que o uso dos recursos seja monitorado e ajustado de acordo com os requisitos atuais e esperados de capacidade.
- Propósito: assegurar a capacidade necessária dos recursos de tratamento de informações, recursos humanos, escritórios e outros serviços de infraestrutura.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo; Detectivo | Integridade; Disponibilidade | Identificar; Detectar; Proteger | Continuidade | Governança e ecossistema; Proteção |

### 2.1 Monitoramento e Planejamento
- Identificar requisitos de capacidade levando em conta a criticidade dos negócios e processos.
- Aplicar ajustes e monitoramento constante para assegurar a disponibilidade e eficiência dos sistemas.
- Realizar testes de estresse para confirmar se a capacidade atende aos requisitos de desempenho máximo.
- Utilizar controles detectivos para identificar falhas ou problemas de sobrecarga em tempo hábil.
- Projetar requisitos futuros considerando novos requisitos de negócios e tendências projetadas nos recursos de informação.
- Monitorar a utilização de recursos com prazos de aquisição longos ou custos elevados.
- Identificar e evitar limitações de recursos ou dependência de pessoas-chave que possam ameaçar a segurança.
- Planejar ações apropriadas para garantir a continuidade operacional diante da ausência de profissionais essenciais.
- Considerar um plano de gestão de capacidade documentado para sistemas de missão crítica.

> [!CAUTION] OBSERVAÇÃO: 
> - O teste de estresse submete a aplicação ao uso máximo de CPU e memória para verificar se a capacidade atribuída é suficiente para mantê-la operacional ⟶ se insuficiente, os recursos devem ser ajustados.

### 2.2 Estratégias Para Ajuste de Capacidade
- Aumentar a capacidade através da contratação de pessoal, obtenção de novas instalações ou aquisição de hardware mais potente.
- Utilizar a computação em nuvem devido às características de elasticidade e escalabilidade, permitindo expansão rápida sob demanda.
- Reduzir a demanda através da exclusão de dados obsoletos e descarte de registros impressos que cumpriram o período de retenção.
- Descomissionar aplicações, sistemas ou bancos de dados que não são mais necessários.
- Otimizar processos em lote, agendamentos, códigos de aplicativos e consultas de banco de dados.
- Restringir ou negar largura de banda para serviços não críticos com alto consumo de recursos, como streaming de vídeo.

> [!CAUTION] OBSERVAÇÃO: 
> - A gestão de capacidade aplica-se também aos recursos humanos; a saída de um administrador essencial sem substitutos previstos pode comprometer a continuidade ⟶ requer planejamento prévio para formação de equipe reserva.