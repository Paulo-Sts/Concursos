# Iso/Iec 27002:2022 - Controles Tecnológicos 3

## 1. Restrição de Acesso à Informação
- Convém que o acesso às informações e outros ativos associados seja restrito de acordo com a política específica por tema sobre controle de acesso.
- Propósito: assegurar apenas o acesso autorizado e impedir o acesso não autorizado a informações e a outros ativos associados.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| PREVENTIVO | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de identidade e acesso | Proteção |

### 1.1 Diretrizes para Restrição de Acesso
- Não permitir acesso a informações confidenciais por identidades de usuários desconhecidos ou anonimamente.
- Fornecer mecanismos de configuração para controlar o acesso à informação em sistemas, aplicações e serviços.
- Controlar quais dados podem ser acessados por um determinado usuário e quais identidades ou grupos possuem permissões específicas (como ler, escrever, excluir e executar).
- Prover controles de acesso físico ou lógico para garantir o isolamento de aplicações, dados ou sistemas sensíveis.
- Considerar o uso de técnicas e processos dinâmicos de gestão de acesso para proteger informações confidenciais de alto valor organizacional.
- Garantir que as técnicas dinâmicas de gestão protejam a informação durante todo o seu ciclo de vida, incluindo criação, tratamento, armazenamento, transmissão e descarte.

### 1.2 Gestão Dinâmica de Acesso
- Estabelecer regras de gestão baseadas em casos específicos de uso para conceder permissões conforme a identidade, o dispositivo, a localização ou a aplicação utilizada.
- Utilizar o esquema de classificação da organização para identificar quais informações demandam técnicas dinâmicas de gerenciamento.
- Exigir o uso de autenticação robusta, credenciais apropriadas ou certificados digitais para permitir o acesso.
- Implementar restrições temporais de acesso, definindo prazos específicos para a validade das permissões.
- Empregar criptografia como método de proteção das informações tratadas.
- Determinar permissões granulares, como a capacidade de impressão de documentos, e registrar detalhadamente quem acessou e como a informação foi utilizada.
- Configurar o disparo de alertas automáticos caso sejam detectadas tentativas de uso indevido das informações.
- Manter a capacidade de modificar ou revogar permissões em tempo real, o que serve de apoio fundamental para os processos de resposta a incidentes.

> [!CAUTION] OBSERVAÇÃO: 
> - O acesso público ou anônimo é uma exceção e só deve ser concedido a locais de armazenamento que comprovadamente não contenham informações confidenciais.
> - A gestão dinâmica é especialmente útil para compartilhar informações com pessoas fora da organização, mantendo o controle sobre o acesso mesmo onde as listas de controle de acesso (ACL) tradicionais não alcançam.
> - Existe a possibilidade de aplicar o modelo ABAC (Attribute-Based Access Control), onde a autorização é concedida considerando múltiplos atributos além do perfil do usuário, como o dispositivo e a localização geográfica ⟶ controle de acesso contextual.

## 2. Acesso ao Código-Fonte
- Convém que os acessos de leitura e escrita ao código-fonte, ferramentas de desenvolvimento e bibliotecas de software sejam adequadamente gerenciados.
- Propósito: evitar a introdução de funcionalidades não autorizadas, prevenir mudanças não intencionais ou maliciosas e manter a confidencialidade de propriedade intelectual valiosa.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| PREVENTIVO | Confidencialidade; Integridade; Disponibilidade | Proteger | Gestão de identidade e acesso; Segurança de aplicação; Segurança de configuração | Proteção |

### 2.1 Orientação para Acesso ao Código
- Controlar estritamente o acesso ao código-fonte e itens associados, como projetos, especificações e planos de verificação.
- Gerenciar o acesso às ferramentas de desenvolvimento, incluindo compiladores, ferramentas de integração e plataformas de teste.
- Armazenar o código de preferência em um sistema de gerenciamento de código-fonte centralizado.
- Diferenciar os direitos de acesso conforme o papel: o acesso de leitura pode ser fornecido amplamente na organização para colaboração, mas a escrita deve ser restrita a pessoas privilegiadas ou proprietários designados.
- Aplicar procedimentos formais de controle de mudança antes de executar qualquer atualização ou alteração no código-fonte.
- Manter as listagens dos programas em ambientes seguros e garantir a existência de uma trilha de auditoria para todos os acessos e modificações realizadas.
- Adotar controles adicionais de integridade, como assinaturas digitais, caso o código-fonte seja destinado à publicação externa.

> [!CAUTION] OBSERVAÇÃO: 
> - É terminantemente recomendado que os desenvolvedores não possuam acesso direto ao repositório central de código-fonte; o acesso deve ser mediado por ferramentas de desenvolvimento que registrem e controlem as autorizações e atividades.
> - A fragilidade no controle de acesso ao código pode expor dados críticos do ambiente de desenvolvimento, como segredos de configuração ou cópias de dados de produção, para pessoas não autorizadas.