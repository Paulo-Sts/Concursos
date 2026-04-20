# Ameaças, Ataques e Pragas Virtuais

## 1. Conceitos Fundamentais

> ### 🛑 Ameaça
- Fator externo que coloca em risco a segurança da informação.
- Pode afetar: confidencialidade, integridade, disponibilidade, autenticidade.

> ### ⚠️ Vulnerabilidade
- Fragilidade interna explorável por ameaças.
- Exemplos:
  - Sistema desatualizado
  - Senhas fracas
  - Software pirata
  - Antivírus vencido
  - Rede pública insegura
  - Falta de backup

> ### 🎲 Risco
- Fórmula: Ameaça + Vulnerabilidade = Risco
- Probabilidade de dano real a partir da exploração.

> ### 🧨 Incidente
- Evento adverso à segurança (ataque, falha, vazamento etc.).

> ### 💥 Dano
- Resultado negativo de um incidente (ex: perda de dados).

## 2. Tipos de ameaças e atacantes

> ### 👨‍💻 Hacker
- Expert em segurança digital.
- Pode ter intenções éticas ou curiosidade (não é crime por si só).
- Tipos:
  - White Hat: hackers do bem
  - Hacktivistas: ideologia política (ex: Anonymous)

> ### 💣 Cracker
- Usa conhecimento para crimes, fraudes e vandalismo.
- Tem o mesmo nível técnico do hacker, mas com **intenção maliciosa**.

> ### 📨 SPAM
- Mensagens eletrônicas não solicitadas em massa.
- Pode conter: golpes, fake news, propagandas e **malwares**.
- Spammer: quem envia.

> ### 🧠 Engenharia social
- Técnica que explora **emoções humanas** (ganância, medo, empatia) para enganar.
- Exemplos:
  - Phishing: link falso enviado por e-mail.
  - Smishing: phishing via SMS.
  - Pharming: redirecionamento do DNS para site falso.
  - Também pode ocorrer presencialmente (alguém se passando por técnico).

> ### 🍪 Cookies

| TIPO         | CARACTERÍSTICA                                         |
|--------------|--------------------------------------------------------|
| Sessão       | Temporário. Some ao fechar navegador.                  |
| Persistente  | Salvo no disco. Gera sugestões personalizadas.         |
| Risco        | **Cookies de terceiros** podem violar sua privacidade. |

## 3. Principais ataques

> ### 🔁 DoS / DDoS
- Negação de serviço: sobrecarrega servidor com requisições.
- DDoS: distribuído por botnets.
- Viola a disponibilidade.

> ### 🔓 Spraying de senhas
- Usa lista de senhas comuns para tentar acesso (ex: 123456).
- Diferente de **força bruta**, que testa combinações aleatórias.

> ### 💣 Força bruta
- Tenta descobrir senhas via tentativa e erro.
- Pode ser evitado com **MFA** (autenticação em 2 etapas).

> ### 🎭 Spoofing
- Falsifica identidade (IP, e-mail etc.).
- Exemplo: **IP Spoofing**, **E-mail Spoofing**.
- Conexão enganada pelo atacante → ataque "Homem-no-Meio".

> ### 🔍 Scan
- Varredura de rede procurando dispositivos ativos vulneráveis.

> ### 🕵️ Sniffing
- Interceção de tráfego de rede.
- Captura senhas, cartões, e-mails em conexões sem criptografia.

> ### 🎨 Defacement
- Invasor altera visual de um site (vandalismo).
- Viola a integridade.

## 4. 💀 Pragas virtuais (Malwares)

> ### 🦠 Vírus
- Se espalha por outros arquivos.
- Não é autônomo.
- Pode apagar, corromper e impedir inicialização.

| TIPO             | AÇÃO                                 |
|------------------|--------------------------------------|
| Boot             | Afeta a inicialização do SO          |
| Macro            | Infecta arquivos do Office com macro |
| Stealth          | Se esconde do antivírus              |
| Polimórfico      | Muda sua forma a cada infecção       |
| Bomba-Relógio    | Ativado por data/hora específica     |

> ### 🐴 Cavalo de Troia (Trojan)
- Parece legítimo, mas contém código malicioso.
- Não se replica, nem é autônomo.
- Serve de porta de entrada.

> ### 🪱 Worm
- Se autorreplica e se espalha pela rede.
- Autônomo, visa sobrecarga (DoS).
- Não corrompe arquivos diretamente.

> ### 🤖 Bot
- Worm com controle remoto (computador zumbi).
- Pode formar uma botnet para DDoS.

> ### 💸 Ransomware
- Criptografa dados e exige resgate (ransom).
- Nem sempre o atacante devolve a chave.
- Prevenção: backup.

> ### 🧰 Rootkit
- Dá privilégios de superusuário ao invasor.
- Fica oculto, se disfarça de programa legítimo.

> ### 🕵️ Spyware
- Espiona dados do usuário sem permissão.
- Tipos: 
  - Keylogger (grava tudo que você digita).
  - Screenlogger (tira prints da tela ao clicar).
  - Adware (exibe anúncios indesejados, pode se comportar como spyware).
  - Backdoor (cria uma porta de entrada oculta para o invasor retornar).

## 5. 🧠 Comparações importantes

| TERMO      | CARACTERÍSTICA PRINCIPAL                       |
|------------|------------------------------------------------|
| Spoofing   | Falsificação da identidade                     |
| Sniffing   | Interceptação e roubo de dados                 |
| Scan       | Varredura da rede em busca de vulnerabilidades |
| Phishing   | Golpe por link falso (e-mail, SMS)             |
| Pharming   | Golpe por redirecionamento DNS                 |
| DoS / DDoS | Ataque à disponibilidade do serviço            |
| Defacement | Vandalismo visual em sites                     |
| Ransomware | Criptografa e cobra resgate                    |
| Rootkit    | Esconde a presença do invasor                  |
| Worm       | Se espalha pela rede                           |
| Trojan     | Parece útil, mas é malicioso                   |
| Adware     | Exibe propaganda                               |
| Backdoor   | Deixa "porta aberta" para retorno do invasor   |