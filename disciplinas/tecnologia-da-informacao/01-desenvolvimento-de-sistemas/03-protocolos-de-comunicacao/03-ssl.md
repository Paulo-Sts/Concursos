# Segurança da Informação – Ssl e Tls

## 1. Protocolos Ssl e Tls
- O Secure Sockets Layer (SSL) e o Transport Layer Security (TLS) são protocolos criptográficos destinados a proteger a comunicação entre dispositivos em uma rede.
- Estes protocolos garantem os princípios fundamentais de confidencialidade, integridade e autenticidade dos dados trocados.
- São amplamente aplicados na internet para assegurar conexões HTTPS, além de serviços de e-mail e mensagens instantâneas.
- Funcionam estabelecendo uma conexão segura entre cliente e servidor, sendo essenciais para o tráfego de dados sensíveis como senhas e números de cartões de crédito.

## 2. História e Evolução do Ssl
- O SSL foi o precursor do TLS e teve diversas versões ao longo de sua história.
- SSL 1.0 ⟶ Nunca foi lançado publicamente devido a graves problemas de segurança.
- SSL 2.0 (1995) ⟶ Lançado pela Netscape, mas apresentava vulnerabilidades que comprometiam a segurança.
- SSL 3.0 (1996) ⟶ Representou uma reformulação significativa para tornar o protocolo mais seguro, introduzindo novos recursos criptográficos.

> [!CAUTION] OBSERVAÇÃO: 
> - O SSL 3.0 é vulnerável ao ataque POODLE, que explora falhas no preenchimento de dados (padding) em criptografias de bloco para inferir informações trafegadas.

## 3. Protocolo Tls – Transport Layer Security
- O TLS é o sucessor oficial do SSL, projetado especificamente para corrigir as deficiências de seu antecessor e fornecer uma solução mais robusta.
- Devido às vulnerabilidades descobertas nas versões antigas, o SSL foi descontinuado e substituído pelo TLS.

### 3.1 Versões do Tls
- TLS 1.0 (1999) ⟶ Primeiro padrão baseado no SSL 3.0, com melhorias iniciais de segurança.
- TLS 1.1 (2006) ⟶ Introduziu proteções contra ataques de repetição e de reflexão (interceptação de comunicação).
- TLS 1.2 (2008) ⟶ Ofereceu grande avanço na criptografia, permitindo o uso de algoritmos modernos como o AES e maior flexibilidade na escolha de cifras.
- TLS 1.3 (2018) ⟶ Versão atual mais recomendada, que eliminou algoritmos inseguros e reduziu a latência para tornar as conexões mais rápidas.

## 4. O Processo de Handshake
- O handshake SSL/TLS é o procedimento de inicialização que estabelece a comunicação segura entre as partes.
- Início da conexão: o cliente envia uma mensagem Hello informando ao servidor as versões de protocolo e os algoritmos de criptografia que suporta.
- Negociação: o servidor responde com seu próprio Hello, selecionando a versão mais alta compatível e enviando seu certificado digital X.509.
- Verificação: o cliente atesta a validade do certificado do servidor junto a uma autoridade certificadora confiável.
- Troca de chaves: as partes acordam uma chave secreta compartilhada, utilizando métodos como o Diffie-Hellman efêmero nas versões mais recentes.
- Conexão estabelecida: após a troca, todos os dados futuros são protegidos por criptografia simétrica utilizando a chave de sessão gerada.

> [!TIP] DICAS: 
> - O TLS introduziu uma mensagem de alerta chamada fechar notificação (close notify), que indica formalmente o encerramento da conexão para evitar o envio de dados residuais.

## 5. Algoritmos de Criptografia Simétrica
- São utilizados para a proteção dos dados transmitidos após o término do handshake.
- Utilizam uma única chave compartilhada para as operações de criptografia e descriptografia.
- Destacam-se por serem rápidos e eficientes, sendo ideais para o processamento de grandes volumes de informações.
- O AES (Advanced Encryption Standard) é o algoritmo mais proeminente no TLS, suportando chaves de 128, 192 e 256 bits.

> [!CAUTION] OBSERVAÇÃO: 
> - Embora chaves maiores (como 256 bits) ofereçam segurança superior, elas demandam maior poder de processamento do servidor, o que pode impactar o rendimento da conexão.

## 6. Integridade e Algoritmos de Hash
- Estes algoritmos garantem que as informações não foram alteradas ou corrompidas durante o trânsito na rede.
- Funcionam criando um resumo matemático (hash) único para os dados enviados.
- Qualquer modificação nos dados originais resulta em um hash completamente diferente, alertando sobre a quebra de integridade.
- O TLS utiliza funções de hash resistentes a colisões, como o SHA-256 e o SHA-384.
- O HMAC (Hash-based Message Authentication Code) é empregado para adicionar uma camada de autenticação ao processo de hash utilizando uma chave secreta.

## 7. Mecanismos de Troca de Chaves
- Esta etapa é crucial para que as partes concordem com a chave secreta de sessão de forma segura.

| MODO | CARACTERÍSTICA | SEGURANÇA |
|---|---|---|
| Rsa static | Usa a chave pública do servidor para proteger a chave de sessão | Removido no tls 1.3 por não oferecer sigilo direto |
| Diffie-hellman efêmero (dhe) | Gera chaves temporárias exclusivas para cada sessão individual | Recomendado por oferecer sigilo direto e melhor desempenho |

> [!CAUTION] OBSERVAÇÃO: 
> - O conceito de sigilo direto (Perfect Forward Secrecy - PFS) assegura que, mesmo que uma chave mestra seja comprometida no futuro, as comunicações de sessões passadas permaneçam protegidas.