# Resumo: Classificação de Redes de Computadores

## 1. Classificação por Abrangência

### PAN (Personal Area Network)
- Rede pessoal de curta distância (poucos metros)
- Conecta dispositivos móveis entre si
- Exemplos: conexão Bluetooth entre smartphone e fones

### LAN (Local Area Network)
- Rede local restrita a uma instituição
- Alcance: dezenas de metros
- Pode ser com fio (Ethernet) ou sem fio (Wi-Fi)

### CAN (Campus Area Network)
- Conecta várias LANs em uma mesma instituição
- Alcance: centenas de metros
- Exemplo: rede universitária com múltiplos prédios

### MAN (Metropolitan Area Network)
- Rede metropolitana entre regiões ou cidades
- Alcance: dezenas de quilômetros
- Exemplo: rede de órgãos públicos em uma capital

### WAN (Wide Area Network)
- Rede de longa distância entre países/continentes
- Exemplo: Internet

## 2. Classificação por Funcionalidade

### Internet
- Rede pública mundial
- Arquiteturas: cliente/servidor e P2P
- Protocolos: TCP/IP

### Intranet
- Rede privada corporativa
- Acesso restrito a usuários autorizados
- Pode usar diferentes alcances (LAN, WAN)

### Extranet
- Disponibiliza recursos da Intranet via Internet
- Acesso controlado para parceiros/clientes
- Exemplo: portal do aluno

### VPN (Virtual Private Network)
- Conexão segura à rede privada via Internet
- Usa criptografia (IPSec)
- Diferente da Extranet: usuário acessa a rede

### Backbone
- Rede central de alto desempenho
- Espinha dorsal de comunicação
- Exemplo: rede de fibra ótica entre estados

## 3. Classificação por Topologia

### Estrela (Star)
- Equipamento central conecta todos dispositivos
- Vantagem: falha em nó não afeta outros
- Desvantagem: falha no central paralisa rede

### Anel (Ring)
- Dispositivos conectados em série
- Transmissão unidirecional com token
- Falha em um nó interrompe toda rede

### Barramento (Bus)
- Todos conectados a um cabo central
- Tecnologia obsoleta
- Falha em nó afeta toda rede

### Malha (Mesh)
- Todos dispositivos conectados entre si
- Full-mesh: cada nó conectado a todos
- Mais comum em topologia lógica

### Híbrida
- Combinação de duas ou mais topologias

## Dicas para Provas
- WAN: conecta países/continentes (Internet)
- LAN: rede local (escritórios, empresas)
- PAN: dispositivos pessoais (Bluetooth)
- Intranet: rede privada corporativa
- Extranet: Intranet disponibilizada parcialmente
- VPN: acesso seguro remoto à rede
- Topologia estrela: mais utilizada atualmente