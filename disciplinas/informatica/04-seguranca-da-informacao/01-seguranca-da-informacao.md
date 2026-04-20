# Segurança da Informação

## 1. Princípios da Segurança da Informação

#### 1.1 Confidencialidade
- Acesso restrito à informação apenas por pessoas autorizadas.
- ⚠️ Violada quando terceiros não autorizados acessam os dados.
- 📌 Ferramentas:
  - Criptografia;
  - Certificado digital.

#### 1.2 Integridade
- Garante que a informação esteja completa e sem alterações indevidas.
- ⚠️ Alterações só podem ser feitas por usuários autorizados.
- 📌 Ferramentas:
  - Backup;
  - Assinatura digital.

#### 1.3 Disponibilidade
- Informação deve estar acessível sempre que necessário.
- ⚠️ Ataques como DDoS afetam este princípio.
- 📌 Ferramentas:
  - Nobreak;
  - Firewall;
  - Backup;
  - Equipamentos redundantes.

#### 1.4 Autenticidade
- Confirma que a informação é de quem diz ser (autor legítimo).
- Inclui o não repúdio (irretratabilidade).
- 📌 Ferramentas:
  - Assinatura digital;
  - Certificado digital;
  - Biometria;
  - MFA (autenticação multifator).

## 2. Princípios Adicionais

#### 2.1 Irretratabilidade (Não Repúdio)
- Garante que o autor **não pode negar** a autoria da ação digital.
- ✔️ Assinatura digital e certificado digital garantem esse princípio.
- Duas vertentes:
  - Irretratabilidade de origem: garante o autor.
  - Irretratabilidade de destino: garante o recebimento.

#### 2.2 Legalidade/Conformidade
- Adequação às leis de proteção de dados, como a LGPD no Brasil. 
- Garante que dados sensíveis sejam gerenciados segundo leis (como a LGPD) e normas técnicas. Isso envolve proteger a confidencialidade, integridade e disponibilidade das informações, evitando vazamentos e sanções jurídicas. Práticas essenciais incluem auditorias, gestão de riscos, criptografia e controle de acesso, assegurando a autenticidade e o não repúdio. 

#### 2.3 Identificação
- É quando o usuário **informa sua identidade** (ex: login, e-mail, CPF).
- Etapa anterior à autenticação.

#### 2.4 Autenticação
- Confirma que a identidade informada é verdadeira.
- 📌 Métodos: senha, token, biometria, chave, MFA.

#### 2.5 Autorização
- Define **o que o usuário pode fazer** após ser autenticado.
- Exemplos: acessar, editar, excluir ou apenas visualizar dados.

#### 2.6 Confiabilidade
- Garante que o sistema **cumpre sua função sem falhas**.
- ⚠️ Não confundir com confidencialidade.