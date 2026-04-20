# Ferramentas de Proteção

#### 🦠 Antivírus
- Detecta e remove malwares (vírus, worm, trojan, ransomware, spyware etc.).
- Funções principais: varredura, quarentena, remoção, atualização de vacinas, proteção em tempo real.
- Exemplo de antivírus: McAfee, Kaspersky, Norton, Avast, AVG.
- Quarentena: arquivo suspeito é isolado e criptografado.
- Não instalar mais de um antivírus no mesmo computador.

#### 👁️ Antispyware
- Detecta e remove spywares (malwares que espiam o usuário).
- Funções: proteção em tempo real, varredura e remoção.
- Pode ser usado junto com antivírus (sem conflito).

#### 📬 Antispam
- Bloqueia mensagens eletrônicas indesejadas (spam).
- Usa IA para classificar remetente, conteúdo e padrão de envio.
- No ambiente corporativo, bloqueia até envio de spam (ex: PC infectado).

#### 🔑 Senha forte
- Use: letras maiúsculas/minúsculas, números, caracteres especiais.
- Evite: dados pessoais, sequências simples (123456, aaaa).
- Quanto mais longa e variada, mais difícil de quebrar.
- Senhas iguais para usos diferentes são inseguras.

#### 🔐 Autenticação multifator (MFA)
- Usa mais de um fator: senha + código, biometria, token etc.
- Mesmo que a senha seja descoberta, há uma segunda etapa de verificação.
- Códigos podem ser enviados por app, e-mail, SMS.

#### 🪪 Certificado digital
- Documento eletrônico que identifica o usuário com segurança.
- Contém: chaves pública e privada, validade, autoridade certificadora (AC).
- Usado em: assinaturas digitais, autenticação, criptografia.
- Tipos:
  - Tipo A: autenticação/identificação (A1, A3)
    - A1: HD/pendrive/nuvem – 1 ano
    - A3: cartão/token/nuvem – até 5 anos
  - Tipo S: sigilo
  - Tipo T: carimbo do tempo
  - PIN: senha para acessar o certificado.  
  - PUK: desbloqueia o PIN.

#### 🔏 Criptografia
- Simétrica:
  - Mesma chave para criptografar e descriptografar.
  - Mais rápida, usada em softwares (Word, Excel, BitLocker).
- Assimétrica:
  - Usa duas chaves: pública (cifra) e privada (decifra).
  - Base da assinatura digital (hash criptografado com a chave privada).
  - Garante: autenticidade, integridade e não repúdio.

#### 🖊️ Assinatura digital
- Gera-se um hash do documento e cifra com a chave privada.
- Receptor usa a chave pública para decifrar.
- Comprova: autoria e integridade.

#### 🛡️ Firewall
- Barreira entre a rede interna e a internet.
- Pode ser software ou hardware.
- Filtra e bloqueia conexões com base em regras definidas.
- Não remove malwares, mas impede seu tráfego.

#### 🧠 IDS e IPS
- IDS (Intrusion Detection System): Monitora o tráfego e detecta anomalias.
- IPS (Intrusion Prevention System): Atua além do IDS, bloqueando ameaças em tempo real.
- IPS complementa o IDS.

#### 🏛️ ICP-Brasil (Infraestrutura de chaves públicas)
- Sistema oficial de certificação digital no Brasil.
- Autoridades:
  - ITI (AC-Raiz): coordena e fiscaliza.
  - AC 1º e 2º nível: emitem certificados.
  - AR (Autoridade de Registro): identifica o usuário, entrega certificados.


