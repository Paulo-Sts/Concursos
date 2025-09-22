# Ferramentas Multimídia

## 1. O que é Multimídia?
- Recursos e dispositivos usados para criar, editar, transmitir e reproduzir conteúdo que combina diferentes meios de comunicação.
- Tipos:
  - Texto;
  - Imagem;
  - Áudio;
  - Vídeo;
  - Animação;
  - Interatividade.

> ### 1.1 Aplicações da Multimídia
- Educação: apresentações interativas, cursos online, treinamentos corporativos.
- Entretenimento: filmes, jogos, realidade virtual e aumentada.
- Negócios: videoconferências, apresentações de produtos, e-commerce.
- Informação: jornais online, sites de notícias, blogs, redes sociais.

> ### 1.2 Tipos de Mídia
- Multimídia: combinação de diferentes tipos de mídia.
- Mídia discreta: elementos estáticos (texto, imagem).
- Mídia contínua: elementos em movimento (vídeo, áudio).

## 2. Áudio Digital

#### 2.1 Características do Áudio Digital
- Frequência: altura do som (graves/agudos).
- Amplitude: intensidade (volume).
- Taxa de amostragem: qualidade da digitalização.
- Profundidade de bits: resolução do som.

#### 2.2 Formatos de Áudio

| FORMATO | TIPO             | USO PRINCIPAL                        |
|---------|------------------|--------------------------------------|
| MP3     | Com perdas       | Streaming, dispositivos portáteis    |
| WAV     | Sem perdas       | Edição profissional, alta fidelidade |
| FLAC    | Sem perdas       | Arquivos de alta qualidade           |
| AAC     | Com perdas       | Streaming (Apple Music, Spotify)     |
| OGG     | Livre/sem perdas | Alternativa ao MP3                   |
| WMA     | Com perdas       | Windows Media Player                 |
| AIFF    | Sem perdas       | Sistemas Apple                       |
| DSD     | Alta resolução   | Audiófilos                           |
| M4A     | Com perdas       | Apple (iTunes, iOS)                  |
| Opus    | Código aberto    | VoIP, videoconferências              |

## 3. Vídeo Digital

#### 3.1 Características do Vídeo Digital
- Resolução: qualidade da imagem (pixels).
- Quadros por segundo (FPS): fluidez do movimento.
- Proporção da tela: relação largura/altura (ex: 16:9).
- Taxa de bits: quantidade de dados por segundo.

#### 3.2 Formatos de Vídeo

| FORMATO | TIPO         | USO PRINCIPAL                     |
|---------|--------------|-----------------------------------|
| MP4     | Mais popular | Streaming, dispositivos portáteis |
| AVI     | Sem perdas   | Edição profissional               |
| MOV     | Apple        | QuickTime, Final Cut Pro          |
| WMV     | Microsoft    | Windows Media Player              |
| FLV     | Streaming    | YouTube, Vimeo                    |
| MKV     | Versátil     | Arquivos com múltiplos codecs     |
| WebM    | Livre        | Streaming em navegadores          |
| H.264   | Codec        | MP4, MOV, MKV                     |
| H.265   | Codec        | Sucessor do H.264                 |
| ProRes  | Profissional | Edição de vídeo profissional      |

## 4. Formatos de Imagem
- JPEG, PNG, GIF, BMP, TIFF, SVG, WEBP
- Observação:  
  - GIF suporta múltiplos frames (animação).  
  - Cuidado com TIFF: pode conter vírus.

## 5. Compactação
- Compressão com perdas: reduz tamanho sem perda significativa de qualidade.
- Compressão sem perdas: mantém qualidade original, mas arquivos maiores.

## 6. Implicações Legais
- Direitos autorais: autorização necessária para uso.
- Licenças Creative Commons: uso legal com restrições.
- Pirataria: reprodução/distribuição ilegal.

## 7. Ferramentas de Reprodução e Edição

#### 7.1 Reprodutores
- Windows Media Player, VLC, iTunes, QuickTime, AIMP, Foobar2000, PotPlayer, Media Player Classic.

### 7.2 Editores
- Imagem: Photoshop, GIMP, Canva, Inkscape
- Áudio: Audacity, Adobe Audition, FL Studio
- Vídeo: Premiere Pro, Final Cut Pro, DaVinci Resolve

## 7.3 Codec
- Dispositivo ou software que codifica/decodifica dados digitais.  
- Exemplos: 
  - H.264;
  - H.265;
  - AAC;
  - MP3.

## 7.4 Aplicativos Multimídia
- Streaming: YouTube, Netflix, Globoplay.  
- Mensagens: WhatsApp (usa XMPP nas portas 5222/5223).  

## 8. Protocolos de Transmissão

#### 8.1 Funcionalidades
- Controle de fluxo
- Sincronização áudio/vídeo
- Qualidade de serviço (QoS)
- Segurança

#### 8.2 Tipos de Protocolos
- Streaming: transmissão em tempo real (ex: RTMP, RTSP, HLS, MPEG-DASH)
- Download progressivo: transmissão em blocos (ex: HTTP, FTP, BitTorrent)

| PROTOCOLO | FUNÇÃO                              | PORTA         |  
|-----------|-------------------------------------|---------------|  
| RTSP      | Controle de streaming (vídeo/áudio) | 554 (TCP/UDP) |  
| RTP       | Transmissão em tempo real (VoIP)    | 5004/5005     |  
| SIP       | Chamadas VoIP                       | 5060          |  

## 9. Acesso Remoto  
- Capacidade de acessar um computador/dispositivo de qualquer local via rede (LAN/WAN).  
- Ferramentas principais:  
  - Windows: 
    - Área de Trabalho Remota (RDP): Porta 3389 (necessita configuração).  
    - Conexão de RemoteApp.  
  - TeamViewer/AnyDesk: Conexão via ID e senha.  
  - VNC (Virtual Network Computing): Acesso por IP (popular em Linux).  

#### 9.1 Protocolos

| PROTOCOLO | FUNÇÃO                          | PORTA | SEGURANÇA                |  
|-----------|---------------------------------|-------|--------------------------|  
| Telnet    | Acesso remoto sem criptografia  | 23    | Não(substituído por SSH) |  
| SSH       | Acesso remoto criptografado     | 22    | Sim                      |  
| RDP       | Controle remoto (Windows)       | 3389  | Sim (com configuração)   |  

## 10. VPN (Rede privada virtual) 
- Tem como objetivo criar conexão segura através de tunelamento na internet.  
- Modos de Operação:  
  - Transporte: Criptografa apenas a mensagem (sem cabeçalho).  
  - Tunelamento: Criptografa pacote completo (com cabeçalho).  
- Uso: Acesso remoto a redes corporativas com segurança.  