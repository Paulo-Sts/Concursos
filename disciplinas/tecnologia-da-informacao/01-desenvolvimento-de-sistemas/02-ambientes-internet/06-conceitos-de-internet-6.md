# Conceitos de Internet e Intranet 6

## 1. Camadas do Modelo TCP/IP
- Representa a arquitetura técnica que permite a comunicação entre computadores na rede.
- Camada de aplicação: local onde residem os protocolos utilizados pelos programas e aplicativos para prestar serviços ao usuário.
- Camada de transporte: responsável por garantir a entrega correta e a ordenação dos dados transmitidos entre as máquinas.
- Camada de internet: executa as funções de roteamento e endereçamento dos pacotes de dados pela rede.
- Camada de acesso à rede: cuida da transmissão física dos bits através do meio de comunicação, como cabos ou sinal sem fio.

| CAMADA | EXEMPLOS DE PROTOCOLOS | FUNÇÃO PRINCIPAL |
|---|---|---|
| Aplicação | Http, ftp, smtp, dns | Interface com o usuário |
| Transporte | Tcp, udp | Controle da comunicação |
| Internet | Ip, icmp, arp | Endereçamento e roteamento |
| Acesso à rede | Ethernet, wi-fi, ppp | Transmissão física |

> [!TIP] DICAS: 
> - Protocolos ⟶ Linguagem padrão utilizada pelo computador para prestar um serviço específico.

## 2. Portas dos Protocolos
- Funcionam como portas lógicas que possibilitam a entrada e saída de comunicações específicas pela web.
- Cada serviço de rede possui um número de porta padronizado para facilitar a identificação pelo sistema.

| PROTOCOLO | PORTA PADRÃO |
|---|---|
| Ftp | 20 e 21 |
| Telnet | 23 |
| Smtp | 25 |
| Dns | 53 |
| Http | 80 |
| Pop3 | 110 |
| Imap | 143 |
| Https | 443 |
| Imaps | 993 |
| Pop3s | 995 |

> [!CAUTION] OBSERVAÇÃO: 
> - As portas com a letra s ao final (como 443, 993 e 995) indicam comunicações seguras que utilizam criptografia.

## 3. Camada de Internet e Endereçamento IP
- Protocolo IP: garante que os dados cheguem ao destino correto através da rede.
- Todo dispositivo conectado a uma rede internet ou intranet deve possuir um endereço ip único para identificação.
- IPv4: utiliza endereços compostos por 32 bits, permitindo cerca de 4,3 bilhões de combinações únicas.
- IPv6: utiliza endereços de 128 bits, criado para solucionar a escassez de endereços do padrão anterior.

### 3.1 Endereços Privados de Intranet
- Faixas de endereços reservadas para redes internas que não são visíveis diretamente na internet pública:
  - 10.0.0.0 até 10.255.255.255;
  - 172.16.0.0 até 172.31.255.255;
  - 192.168.0.0 até 192.168.255.255;
  - 169.254.0.0 até 169.254.255.255.

> [!CAUTION] OBSERVAÇÃO: 
> - O IPv6 possui capacidade de endereçamento praticamente ilimitada em comparação ao IPv4.

## 4. Protocolo ICMP
- Sigla para internet control message protocol, sendo um componente obrigatório do protocolo ip.
- Utilizado para fornecer relatórios de erros e informações de controle à fonte original dos dados.
- Tipos de mensagens icmp:
  - Destination unreachable: emitida quando o roteador não consegue localizar o destino do pacote;
  - Time exceeded: ocorre quando o pacote é descartado porque o seu tempo de vida (ttl) chegou a zero;
  - Parameter problem: detecta valores ilegais ou incorretos no cabeçalho do pacote;
  - Source quench: utilizado anteriormente para reduzir a velocidade de envio de hosts que sobrecarregavam a rede.

## 5. Camada de Transporte
- TCP (Transmission Control Protocol): protocolo orientado à conexão que garante a entrega de dados sem erros e na sequência correta.
- Controle de fluxo: mecanismo do tcp que impede que um emissor rápido sobrecarregue um receptor mais lento.
- UDP (User Datagram Protocol): protocolo sem conexão e não confiável, priorizando a velocidade em detrimento da verificação de erros.
- Aplicações do udp: ideal para transmissões de voz e vídeo em tempo real onde perdas ocasionais de dados são toleráveis.

| PROTOCOLO | ORIENTAÇÃO | CONFIABILIDADE | USO COMUM |
|---|---|---|---|
| Tcp | Com conexão | Alta (sem erros) | E-mail, web, arquivos |
| Udp | Sem conexão | Baixa (rápido) | Streaming, voip |

## 6. Camada de Aplicação
- Contém os protocolos de nível mais alto que definem como as informações de serviços específicos são trocadas.
- FTP: protocolo específico para a transferência de arquivos entre máquinas.
- Telnet: permite o acesso remoto a terminais virtuais.
- SSH (Secure Shell): oferece as mesmas funcionalidades do telnet, porém com a proteção adicional de criptografia.
- DNS (Domain Name System): sistema responsável por traduzir nomes de domínios em endereços ip numéricos.
- SNMP: facilita o gerenciamento de dispositivos de rede, permitindo monitorar o desempenho e resolver problemas técnicos.

> [!TIP] DICAS: 
> - O ssh é amplamente utilizado em vpns através da técnica de tunelamento para garantir segurança.

> [!CAUTION] OBSERVAÇÃO: 
> - O servidor dns é o computador responsável por controlar qual servidor um usuário alcançará ao digitar uma url no navegador.