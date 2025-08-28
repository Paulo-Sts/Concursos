# Resumo: Equipamentos de Rede e Arquiteturas TCP/IP e OSI

## 1. Equipamentos de Rede e Suas Funções

### Gateway
- Portal de entrada/saída entre redes distintas
- Exemplo: Roteador atuando como gateway

### Bridge
- Subdivide uma rede em sub-redes
- Reduz tráfego de dados na mesma rede
- Roteador pode exercer função de bridge

### Switch
- Distribui pacotes entre dispositivos da mesma rede
- Encaminha dados baseado no endereço MAC
- Topologia física estrela/lógica malha

### Hub
- Concentrador que promove conexão física
- Transmite sinais para todas as portas (broadcast)
- Topologia física estrela/lógica barramento

### Repetidor
- Amplifica sinal elétrico
- Não interpreta dados

### Modem
- Modula e demodula sinais
- Conecta usuário ao provedor (ISP)

## 2. Arquiteturas de Rede

### TCP/IP (4 Camadas)
1. **Aplicação**: HTTP, FTP, DNS, SMTP, POP3, IMAP
2. **Transporte**: TCP, UDP, SSL, TLS
3. **Internet/Rede**: IP, ARP, RARP, NAT, ICMP
4. **Acesso à Rede**: IEEE 802.3, 802.11, 802.15

### OSI/ISO (7 Camadas)
1. **Física**: Bits
2. **Enlace**: Frames
3. **Rede**: Pacotes
4. **Transporte**: Segmentos
5. **Sessão**: Dados
6. **Apresentação**: Dados
7. **Aplicação**: Dados

### Relação entre Arquiteturas
- TCP/IP Aplicação = OSI Aplicação + Apresentação + Sessão
- TCP/IP Acesso à Rede = OSI Enlace + Física

## 3. Protocolos por Camada

### Camada de Aplicação
- **HTTP/HTTPS**: Páginas web (porta 80/443)
- **FTP**: Transferência de arquivos (porta 20/21)
- **SSH**: Conexão remota segura
- **Telnet**: Conexão remota não segura (porta 23)
- **DNS**: Tradução nome↔IP
- **DHCP**: Atribuição dinâmica de IP
- **SMTP**: Envio de email (porta 587)
- **POP3**: Recebimento de email (porta 110)
- **IMAP**: Acesso a email no servidor (porta 143)

### Camada de Transporte
- **TCP**: Orientado à conexão, confiável
- **UDP**: Não orientado à conexão, rápido
- **SSL/TLS**: Criptografia e segurança

### Camada de Internet/Rede
- **IP**: Endereçamento (IPv4/IPv6)
- **ARP**: Resolução IP→MAC
- **RARP**: Resolução MAC→IP
- **NAT**: Tradução de endereços
- **ICMP**: Controle e mensagens (ping)

### Camada de Acesso à Rede
- **IEEE 802.3**: Ethernet
- **IEEE 802.5**: Token Ring
- **IEEE 802.11**: Wi-Fi
- **IEEE 802.15**: Bluetooth
- **IEEE 802.16**: WiMAX

## 4. Endereçamento IP

### IPv4
- 32 bits, 4 octetos (0-255)
- Exemplo: 192.168.0.1
- Classes:
  - A: 0.0.0.1 - 126.255.255.255
  - B: 128.0.0.0 - 191.255.255.255
  - C: 192.0.0.0 - 223.255.255.255
  - D: Multicast
  - E: Experimental

### IPv6
- 128 bits, 8 grupos hexadecimais
- Exemplo: FE80::C500:12F9:0:2F8E
- Representação simplificada com "::"

### IPs Privados
- Classe A: 10.0.0.0 - 10.255.255.255
- Classe B: 172.16.0.0 - 172.31.255.255
- Classe C: 192.168.0.0 - 192.168.255.255
- Localhost: 127.0.0.1

## 5. Comandos Úteis
- **ipconfig** (Windows): Configuração de rede
- **ifconfig** (Linux): Configuração de rede
- **ping**: Teste de conectividade (ICMP)

## 6. Dicas para Provas
- Roteador: Interliga redes distintas
- Switch: Encaminhamento por MAC
- Hub: Broadcast para todas as portas
- TCP: Conexão confiável (3-way handshake)
- UDP: Conexão não confiável mas rápida
- HTTP: Porta 80, HTTPS: Porta 443
- FTP: Porta 20/21
- SMTP: Porta 587
- POP3: Porta 110
- IMAP: Porta 143