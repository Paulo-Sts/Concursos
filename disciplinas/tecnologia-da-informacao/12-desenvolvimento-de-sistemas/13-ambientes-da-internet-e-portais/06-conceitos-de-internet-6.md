# Protocolos e Camadas de Rede

## 1. Fundamentos de Protocolos e Portas
- Protocolo é definido como a linguagem utilizada pelo computador para a prestação de um determinado serviço.
- O modelo de camadas organiza as funções de rede em diferentes níveis de abstração.
- As quatro camadas principais são:
  - Camada de aplicação: local onde residem os protocolos utilizados pelos aplicativos;
  - Camada de transporte: responsável por garantir a entrega correta e ordenada dos dados;
  - Camada de internet: executa o roteamento e o endereçamento dos pacotes de dados;
  - Camada de acesso à rede: responsável pela transmissão física das informações.

### 1.1 Portas de Comunicação
- As portas são elementos que possibilitam a comunicação pela web através dos protocolos TCP e UDP.

| PROTOCOLO | PORTA PADRÃO |
|---|---|
| Ftp | 20 |
| Telnet | 23 |
| Smtp | 25 |
| Dns | 53 |
| Http | 80 |
| Pop3 | 110 |
| Imap | 143 |
| Imap3 | 220 |
| Https | 443 |
| Imaps | 993 |
| Pop3s | 995 |

> [!TIP] DICAS: 
> - A porta 8080 também é comumente utilizada em servidores específicos para o protocolo http.

## 2. Camada de Internet e Endereçamento
- O protocolo ip (internet protocol) garante que os dados cheguem ao destino correto através de endereços únicos.
- Cada dispositivo conectado em uma rede, seja ela internet ou intranet, deve possuir um endereço ip exclusivo.

### 2.1 Versões do Protocolo Ip
- Ipv4: utiliza endereços de 32 bits (ex: 192.0.2.1) e possui uma limitação de aproximadamente 4,3 bilhões de endereços.
- Ipv6: utiliza endereços de 128 bits (ex: 2001:0db8::1) e oferece uma quantidade de endereços praticamente ilimitada.

### 2.2 Endereçamento Ip para Intranet
- Existem faixas específicas de endereços ip reservadas exclusivamente para o uso em redes internas (intranets).

| TIPO DE REDE | GAMA DE ENDEREÇOS RESERVADOS |
|---|---|
| Intranet classe a | 10.0.0.0 até 10.255.255.255 |
| Intranet classe b | 172.16.0.0 até 172.31.255.255 |
| Intranet classe c | 192.168.0.0 até 192.168.255.255 |
| Link-local | 169.254.0.0 até 169.254.255.255 |

> [!CAUTION] OBSERVAÇÃO: 
> - O ipv6 foi desenvolvido como sucessor do ipv4 para suprir a escassez de endereços e inclui suporte nativo a funcionalidades de segurança e mobilidade.

### 2.3 Protocolo Icmp
- Icmp (internet control message protocol) é um protocolo integrante do ip, definido pela rfc 792, utilizado para fornecer relatórios de erros à fonte original.
- As principais mensagens geradas pelo icmp incluem:
  - Destination unreachable: quando o roteador não localiza o destino;
  - Time exceeded: quando o pacote é descartado porque o contador ttl (time to live) chegou a zero;
  - Parameter problem: detecção de valor ilegal no cabeçalho do pacote;
  - Source quench: utilizado anteriormente para restringir hosts que enviavam pacotes em excesso.

## 3. Camada de Transporte
- Esta camada cuida da comunicação fim a fim entre os dispositivos.

### 3.1 Protocolo Tcp
- Tcp (transmission control protocol) é orientado à conexão e considerado confiável.
- Garante a entrega de um fluxo de bytes sem erros entre computadores.
- Gerencia o controle de fluxo para evitar que um transmissor rápido sobrecarregue um receptor lento.

### 3.2 Protocolo Udp
- Udp (user datagram protocol) é um protocolo sem conexões e não confiável.
- Não oferece sequenciação ou controle de fluxo nativo.
- Indicado para aplicações que priorizam a velocidade e possuem controle próprio, como transmissões de voz e vídeo.

## 4. Camada de Aplicação
- Contém os protocolos de nível mais alto que interagem diretamente com os softwares e usuários.

### 4.1 Principais Protocolos de Aplicação
- Ftp: protocolo específico para a transferência de arquivos.
- Smtp: protocolo utilizado para o envio de mensagens de correio eletrônico.
- Pop3: recebimento de e-mail com a realização de download da mensagem para o dispositivo local.
- Imap: recebimento de e-mail com foco na sincronização entre diferentes dispositivos.
- Telnet: protocolo para acesso via terminal virtual.
- Ssh (secure shell): oferece as mesmas funcionalidades do telnet, mas com a proteção adicional de criptografia.
- Dns (domain name system): realiza a resolução de nomes, traduzindo domínios em endereços ip.
- Snmp: facilita o intercâmbio de informações de gerenciamento entre dispositivos de rede como switches e placas.

> [!TIP] DICAS: 
> - O ssh é amplamente utilizado em vpns através da técnica de tunelamento (tunneling) para garantir a segurança da transmissão.
> - O dns é o serviço que permite que você digite um nome de site no navegador e seja direcionado ao servidor correto.