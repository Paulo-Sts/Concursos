# Arquitetura Tcp/Ip – Camada de Aplicação – Protocolo Https

## 1. Conceitos e Finalidade do Https
- O Protocolo de Transferência de Hipertexto Seguro (HTTPS) constitui a versão protegida do HTTP, sendo o principal meio para o envio seguro de dados entre navegadores e sites.
- Funciona como uma suíte que combina o protocolo HTTP da camada de aplicação com os protocolos SSL ou TLS da camada de transporte.
- Sua criação visou solucionar a vulnerabilidade do HTTP, que transmite informações em texto claro (ASCII) e sem criptografia.
- O uso do HTTPS garante a criptografia de toda a comunicação, impedindo que interceptadores (man-in-the-middle) acessem dados sensíveis como nomes de usuário e senhas.
- Navegadores modernos sinalizam como não seguros os sites que operam apenas com HTTP, muitas vezes exibindo um cadeado verde para indicar conexões HTTPS legítimas.

> [!CAUTION] OBSERVAÇÃO: 
> - Sites maliciosos podem simular o ícone de cadeado na barra de status por meio de imagens ou GIFs para enganar o usuário, embora o navegador aponte a falta de segurança na URL.

## 2. Identificadores Uri e Url
- O Uniform Resource Identifier (URI) é o identificador de um elemento ou objeto em um servidor.
- A Uniform Resource Location (URL) é um tipo específico de URI que fornece a localização exata do recurso na rede.
- Toda URL é obrigatoriamente uma URI, mas nem toda URI é uma URL, pois a URI pode ser apenas um nome ou identificador sem a localização.

> [!TIP] DICAS: 
> - URI ⟶ Identificação do recurso;
> - URL ⟶ Identificação somada à localização do recurso.

## 3. Mecanismos de Criptografia no Https
- O protocolo protege as comunicações utilizando uma infraestrutura de chave pública assimétrica.
- Chave privada: mantida exclusivamente pelo proprietário do site no servidor web para descriptografar as informações.
- Chave pública: distribuída livremente para todos os usuários que desejam interagir com o servidor de forma segura.
- Criptografia simétrica: utiliza uma chave compartilhada única para criptografar e descriptografar mensagens durante uma sessão específica.
- Chave de sessão: chave simétrica exclusiva gerada para cada conexão individual, possuindo validade por tempo limitado.

## 4. Comparativo entre Protocolos e Segurança
| PROTOCOLO | PORTA PADRÃO | SEGURANÇA | DESCRIÇÃO |
|---|---|---|---|
| Http | 80 | Sem criptografia | Comunicação em texto puro |
| Https | 443 | Criptografia + autenticação | Usa ssl (antigo) ou tls |

### 4.1 Diferenças Técnicas entre Ssl e Tls
| ASPECTO | SSL | TLS |
|---|---|---|
| Estado atual | Obsoleto e inseguro | Padrão atual (1.2 e 1.3) |
| Criptografia | Algoritmos antigos (md5, rc4) | Algoritmos modernos (aes, sha-256) |
| Handshake | Processo lento e com falhas | Handshake eficiente e seguro |
| Autenticação | Suporte limitado a certificados | Suporte completo a certificados x.509 |
| Negociação de versão | Enviada em texto claro | Protegida no handshake |
| Uso atual em https | Praticamente inexistente | Amplamente adotado |

> [!CAUTION] OBSERVAÇÃO: 
> - O SSL 3.0 é vulnerável ao ataque POODLE, que explora falhas no preenchimento (padding) de bits em rajadas de dados para decifrar comunicações por meio de tentativas de erro e acerto.

## 5. Processo de Handshake Tls 1.3
- O handshake é a negociação inicial entre o navegador do cliente e o servidor para estabelecer a conexão segura.
- ClientHello: o cliente inicia o contato enviando a lista de versões TLS suportadas e métodos de compressão.
- ServerHello: o servidor responde escolhendo a versão da cifra e enviando seu certificado digital X.509 junto à chave pública.
- Verificação do Certificado: o cliente atesta a validade do certificado e da assinatura digital do servidor junto a uma autoridade certificadora (CA).
- Geração da Chave de Sessão: cliente e servidor utilizam algoritmos como o Diffie-Hellman para combinar segredos e derivar uma chave simétrica única.
- Finalização (Finished): ambas as partes confirmam a integridade do processo e passam a utilizar a criptografia simétrica para a troca de dados.

## 6. Evolução para o Https sobre o Protocolo Quic
- O HTTP/3 utiliza o protocolo QUIC em vez do tradicional TCP para a camada de transporte.
- O QUIC é executado sobre o UDP e já possui o serviço TLS 1.3 integrado nativamente.

| ASPECTO | TCP | QUIC |
|---|---|---|
| Base | Protocolo próprio | Executado sobre udp |
| Handshake | 1-3 rtts | 1 rtt (round-trip time) |
| Handshake de reconexão | 1-3 rtts | 0 rtt (round-trip time) |
| Criptografia | Tls opcional | Tls 1.3 integrado |
| Mudança de rede | Reconexão necessária | Conexão mantida via connection id |

> [!TIP] DICAS: 
> - O TLS 1.3, lançado em 2018, é a versão mais rápida e segura disponível, reduzindo o número de etapas no handshake em comparação às versões anteriores.