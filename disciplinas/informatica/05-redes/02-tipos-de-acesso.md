# Resumo: Tipos de Acesso em Redes de Computadores

## 1. Acesso Local

### Com Fio (Ethernet - IEEE 802.3)
- Padrões Ethernet:
  - 10Base5: Coaxial grosso, 10 Mbps, 500m
  - 10Base2: Coaxial fino, 10 Mbps, 185m
  - 10BaseT: Par trançado, 10 Mbps, 100m
  - 10BaseF: Fibra ótica, 10 Mbps, 2000m
  - 100BaseTX: Par trançado, 100 Mbps, 100m
  - 100BaseFX: Fibra ótica, 100 Mbps, 2000m
  - 1000BaseT: Par trançado, 1 Gbps, 100m

- Categorias de Cabo (1000BaseT):
  - Cat 5e: 1 Gbps, 100m, 100 MHz
  - Cat 6: 1 Gbps, 100m, 250 MHz
  - Cat 6A: 10 Gbps, 100m, 500 MHz
  - Cat 7: 40 Gbps, 15m
  - Cat 7A: 100 Gbps, 15m, 1 GHz
  - Cat 8: 40 Gbps, 30m, 2 GHz

- Cabos:
  - UTP (não blindado)
  - STP (blindado)
  - Padrões de conectorização: T-568A e T-568B

### Sem Fio
- Wi-Fi (IEEE 802.11):
  - Rede local sem fio (WLAN)
  - Velocidades inferiores à Ethernet
  - Permite acesso à internet

- Bluetooth (IEEE 802.15):
  - Rede pessoal (PAN)
  - Baixo consumo de energia
  - Curta distância (até 100m)
  - Conexão entre dispositivos móveis

- NFC (Near Field Communication):
  - Comunicação por proximidade
  - Não requer pareamento
  - Aplicações: pagamentos, controle de acesso, transferência de dados

## 2. Banda Larga

### Com Fio
- ADSL (Linha Digital Assimétrica):
  - Usa infraestrutura de telefonia fixa
  - Download > Upload
  - Transmissão simultânea de voz e dados

- Cable Modem:
  - Usa infraestrutura de TV a cabo
  - Cabo coaxial
  - Transmissão simultânea de TV e dados

- PLC/BPL:
  - Power Line Communication
  - Usa rede elétrica para transmissão de dados
  - Transmissão simultânea de energia e dados

### Sem Fio
- Via Rádio:
  - Ondas de rádio
  - Antenas fixas
  - Sem mobilidade

- Banda Larga Móvel:
  - Tecnologias: 3G, 4G LTE, 5G
  - Usa telefonia móvel
  - Permite mobilidade entre células

- WiMAX:
  - Acesso sem fio de longa distância
  - Alcance de quilômetros

- Via Satélite:
  - Ideal para áreas rurais
  - Usado em aviões e locais remotos
  - Exemplo: Starlink

## 3. Equipamentos de Conexão

- Modem:
  - Modula e demodula sinais
  - Conecta usuário ao provedor

- Roteador:
  - Interconecta redes diferentes
  - Atua como gateway
  - Controla fluxo de dados

- Hub:
  - Conecta dispositivos na mesma rede
  - Topologia física estrela/lógica barramento
  - Transmite sinais para todas as portas

- Switch:
  - Conecta dispositivos na mesma rede
  - Topologia física estrela/lógica malha
  - Encaminha dados baseado no endereço MAC

## 4. Comparativo de Tecnologias

| Tecnologia | Alcance | Velocidade | Aplicação |
|------------|---------|------------|-----------|
| Ethernet | Até 100m | Até 100 Gbps | Redes locais |
| Wi-Fi | Até 100m | Até 1 Gbps | Redes sem fio locais |
| Bluetooth | Até 100m | Até 3 Mbps | Dispositivos pessoais |
| NFC | Até 10cm | Até 424 kbps | Pagamentos/transferência |
| ADSL | Km | Até 24 Mbps | Banda larga residencial |
| 4G/5G | Km | Até 1 Gbps | Banda larga móvel |
| Satélite | Global | Variável | Áreas remotas |

## 5. Dicas para Provas

- Ethernet: padrão IEEE 802.3
- Wi-Fi: padrão IEEE 802.11
- Bluetooth: padrão IEEE 802.15
- PAN: redes pessoais (Bluetooth)
- WLAN: redes locais sem fio (Wi-Fi)
- ADSL: assimetria (download > upload)
- PLC: usa rede elétrica para dados
- Hub: broadcast para todas as portas
- Switch: encaminhamento seletivo por MAC