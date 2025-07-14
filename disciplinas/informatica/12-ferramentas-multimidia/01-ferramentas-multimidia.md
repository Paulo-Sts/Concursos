# Ferramentas Multimídia

## Acesso remoto  
- Capacidade de acessar um computador/dispositivo de qualquer local via rede (LAN/WAN).  

### Ferramentas principais:  
- **Windows:**  
  - **Área de Trabalho Remota (RDP):** Porta **3389** (necessita configuração).  
  - **Conexão de RemoteApp.**  
- **TeamViewer/AnyDesk:** Conexão via ID e senha.  
- **VNC (Virtual Network Computing):** Acesso por IP (popular em Linux).  

### Protocolos

| PROTOCOLO | FUNÇÃO                          | PORTA | SEGURANÇA                |  
|-----------|---------------------------------|-------|--------------------------|  
| Telnet    | Acesso remoto sem criptografia  | 23    | Não(substituído por SSH) |  
| SSH       | Acesso remoto criptografado     | 22    | Sim                      |  
| RDP       | Controle remoto (Windows)       | 3389  | Sim (com configuração)   |  

## VPN (Rede privada virtual) 
- Tem como objetivo criar conexão segura através de tunelamento na internet.  
- **Modos de Operação:**  
  - **Transporte:** Criptografa apenas a mensagem (sem cabeçalho).  
  - **Tunelamento:** Criptografa pacote completo (com cabeçalho).  
- **Uso:** Acesso remoto a redes corporativas com segurança.  

## Transferência de arquivos multimídia  

### Formatos comuns

| TIPO        | EXTENSÕES              |  
|-------------|------------------------|  
| Imagens     | .BMP, .PNG, .JPG, .GIF |  
| Áudio       | .MP3, .WMA, .AAC       |  
| Vídeo       | .MP4, .AVI, .WMV, .MOV |  
| Compactados | .ZIP, .RAR             |  

### Conceitos-chave  
- **Streaming:** Transmissão contínua sem download (ex.: Netflix, YouTube).  
- **Codec:** Codifica/decodifica dados multimídia (ex.: H.264 para vídeos).  
- **Mídias:**  
  - **Estática:** Texto, imagens (independentes do tempo).  
  - **Dinâmica:** Áudio, vídeo (dependentes do tempo).  

### Protocolos multimídia  
| PROTOCOLO | FUNÇÃO                              | PORTA         |  
|-----------|-------------------------------------|---------------|  
| RTSP      | Controle de streaming (vídeo/áudio) | 554 (TCP/UDP) |  
| RTP       | Transmissão em tempo real (VoIP)    | 5004/5005     |  
| SIP       | Chamadas VoIP                       | 5060          |  

## Aplicativos multimídia
- **Reprodutores:** VLC, Windows Media Player, RealPlayer.  
- **Streaming:** YouTube, Netflix, Globoplay.  
- **Mensagens:** WhatsApp (usa XMPP nas portas 5222/5223).  

### Destaques para concursos 
- Diferenciar **Telnet (inseguro)** vs **SSH (seguro)**.  
- Portas de protocolos (**RDP:3389, SSH:22, SIP:5060**).  
- VPN é essencial para **acesso remoto seguro**.  
- **Streaming não salva arquivos localmente**.  